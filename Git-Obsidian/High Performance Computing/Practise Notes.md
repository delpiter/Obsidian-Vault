## Pattern Comuni
```c title:"array division"
my_start = (my_id * n)/p;
my_end = ((my_id + 1) * n)/p;
```

```c title:"cyclic ghost area"
a[i] = b[(i + n - 1) % n] + b[(i + 1) % n];
```

```c title:"loop aligning"
// a[0] = 0;
// for (i=1; i<n; i++) {
// 	a[i] = b[i-1] * c[i];
// 	d[i] = a[i-1] + 2;
// }
=>
a[0] = 0;
d[1] = a[0] + 2;
for(i = 1; i < n-1; i++)
{
	a[i] = b[i - 1] * c[i];
	d[i-1] = a[i] + 2;
}
a[n-1] = b[n - 2] * c[n - 1];
```
## OMP

```c title:"OMP primitives"
int my_rank = omp_get_thread_num();
/* returns the id of the thread executing the code */
int thread_count = omp_get_num_threads();
/* returns the number of threads in the currently active team */
int x = omp_get_max_threads()
/* returns the default dimension of the thread team */
omp_set_num_threads(4);
/* Sets the number of threads in the team */
```

>[!hint] Scope
> Una variabile visibile prima del blocco parallelo è condivisa dai thread, sono private altrimenti.

>Per alterare il comportamento di default:

`{c icon} shared(x)`
- Tutti i thread hanno accesso alla stessa area di memoria.

`{c icon} private(x)`
- Ogni thread ha la propria copia della variabile, **NON** inizializzata.

`{c icon} firstprivate(x)`
- Ogni thread ha la propria copia della variabile inizializzata con il valore corrente di $x$.

`{c icon} default(shared) default(none)`
- Ha effetto su tutte le variabili non specificate nelle altre clausole.

>[!failure] Pragmas

`{c icon} #pragma omp parallel`
- Crea il team di thread paralleli.

`{c icon} #pragma omp parallel for`
- Usata in un loop, le iterazioni verranno assegnate automaticamente ai thread del team corrente.

`{c icon} #pragma omp parallel reduction(+: result)`
- Accumula i risultati parziali in maniera atomica.
- Ciascun thread crea una copia privata di `result` e la inizializza con il valore neutro dell'operatore.
- Quando i thread finiscono viene applicato l'operatore con l'ultimo valore di ogni riduzione locale e il valore che la variabile aveva prima della regione parallela.

`{c icon} #pragma omp parallel for collapse(2)`
- Specifica quanti loop in un loop innestato possono essere collassati in un unico loop.

`{c icon} #pragma omp parallel for schedule(type, chunksize)`
- Si aggiunge al costrutto `for` e consente di definire come le iterazioni vengono assegnate ai thread.
	- Le iterazioni sono divise in chunk di `chunksize` iterazioni consecutive
- Il tipo può essere:
	- `static`: le iterazioni sono assegnate ciclicamente
		- `chunksize=ceil(n_iteration/n_thread)` se non specificato.
	- `dynamic/guided`: Le iterazioni sono assegnate secondo il master worker paradigm.
		- `chunksize` di default è $1$.
	- `auto`: il compilatore determina lo schedule.
	- `runtime`: lo schedule è determinato usando la variabile d'ambiente `{sh icon} OMP_SCHEDULE`

`{c icon} #pragma omp barrier`
- Tutti i thread nel team attivo devono raggiungere il punto prima di continuare.

`{c icon} #pragma omp master`
- La regione parallela deve essere eseguita solo dal processo master `rank=0`.
- **Non** c'è una barriera implicita.

`{c icon} #pragma omp single`
- Indica che la regione parallela deve essere eseguita una sola volta dal primo thread che entra.
- C'è una barriera implicita.

>[!todo] Task
>Un task è una unità di lavoro indipendente, composta da codice da eseguire e dati da elaborare.

`{c icon} #pragma omp task`

Al termine della regione parallela tutti i task sono stati eseguiti.
- ***GARANZIA***.

I task vengono eseguiti in ordine "casuale" (non in ordine di creazione).

Fondamentale il `{c icon} #pragma omp single` per non creare un task per thread.

> Scoping
- `shared`: La variabile fa riferimento alla locazione di memoria condivisa con quel nome, al punto dove il task era stato incontrato.
- `private`: Fa riferimento a una nuova porzione di memoria non inizializzata, creata all'esecuzione del task.
- `firstprivate`: Fa riferimento a una nuova porzione di memoria inizializzata con il valore della variabile esistente, creata alla creazione del task.

Il comportamento voluto solitamente è `firstprivate`:
- Le variabili `private` sono `firstprivate` di default nei task.

`{c icon} #pragma omp taskwait`
- Barriera esplicita per i task
## MPI
>[!info]
>Modello per programmazione di computer a memoria distribuita.

>[!help] Organizzazione

> Communicator
- I processi sono raggruppati in gruppi, ciascun gruppo è identificato dal **communicator**.
- `MPI_COMM_WORLD` è il communicator di default.

> Tag
- I messaggi sono inviati con un tag intero definito dall'utente.
- I messaggi possono essere filtrati dal ricevente specificando un tag.
	- `MPI_ANY_TAG` accetta qualsiasi tag.

>[!abstract] Funzioni di Base

`{c icon} MPI_Comm_size()`
- Ritorna il numero di processi.

`{c icon} MPI_Comm_rank()`
- Ritorna il rank, un numero tra $0$ e $size-1$ che identifica il processo chiamante.

`{c icon} MPI_Init()` e `{c icon} MPI_Finalize()`
- Usati per iniziare e chiudere una sezione `MPI`.

`{c icon} MPI_Abort()`
- Termina la computazione.

>[!caution] Send e Receive

```c
int MPI_Send(
	const void *buf,       /*Puntatore all'area di memoria da inviare*/
	int count,             /*Numero di elementi inviati*/
	MPI_Datatype datatype, /*Tipo mpi che viene inviato*/
	int dest,              /*Rank del ricevente*/
	int tag,               /*Tag del messaggio*/
	MPI_Comm comm          /*Communicator*/
);
```

```c
int MPI_Recv(
	void *buf,             /*Puntatore a dove deve essere salvato il msg*/
	int count,             /*Numero massimo di elementi da ricevere*/
	MPI_Datatype datatype, /*Tipo mpi che viene ricevuto*/
	int dest,              /*Rank del mittente*/
	int tag,               /*Tag del messaggio*/
	MPI_Comm comm          /*Communicator*/
);
```

Il processo si sblocca quando il sottosistema `MPI` del nodo locale prende in carico il messaggio.
- Entrambi hanno la versione **asincrona**, con in aggiunta il parametro `{c icon} MPI_Request *request`
	- Parametro che permette di esaminare lo stato delle operazioni.

```c
/* 
 * Esegue una send e una receive bloccanti in una singola chiamata.
 * I parametri sono i parametri di una send seguiti da quelli di una   
 * recv
 */
int MPI_Sendrecv(
	const void *sendbuf,
	int sendcount, 
	MPI_Datatype sendtype,
	int dest,
	int sendtag,
	void *recvbuf,
	int recvcount,
	MPI_Datatype recvtype,
	int source,
	int recvtag,
	MPI_Comm comm,
	MPI_Status *status
);
```

- È possibile specificare un ricevitore nullo.

>[!hint] Collective Communication

```c
/* Invia un messaggio a tutti i processi del comm */
int MPI_Bcast(
	void *buffer,          /* Messaggio da spedire o ricevere */
	int count,             /* Numero di elementi da recv/inv */
	MPI_Datatype datatype, /* Tipo di dato da spedire */
	int root,              /* Rank del mittente */
	MPI_Comm comm          /* Communicator */
	);
```

```c
/* Distribuisce dati a gli altri processi nel gruppo */
int MPI_Scatter(
	const void *sendbuf,   /* Buffer di invio (ricevitore nullo) */
	int sendcount,         /* N.elementi da spedire a ciascun proc */
	MPI_Datatype sendtype, /* Tipo da inviare */
	void *recvbuf,         /* Buffer di ricezione(allocato da tutti) */
	int recvcount,         /* Numero di elementi da ricevere */
	MPI_Datatype recvtype, /* Tipo del dato */
	int root,              /* Rank del processo mittente */
	MPI_Comm comm          /* Communicator */
	);
```

```c
/* Raggruppa i dati provenienti da tutti i processi in uno solo */
int MPI_Gather(
	const void *sendbuf,    /* Buffer di invio (allocato da tutti) */
	int sendcount,          /* N.elementi da spedire */
	MPI_Datatype sendtype,  /* Tipo elemento */
	void *recvbuf,          /* Buffer di ricezione(solo ricevitore) */
	int recvcount,          /* Numero di elementi ricevuti */
	MPI_Datatype recvtype,  /* Tipo di ricezione */
	int root, MPI_Comm comm /* Communicator */
	);
```

```c
/* Equivalente a una gather seguita da una scatter */
int MPI_Allgather(
	const void *sendbuf,
	int  sendcount,
	MPI_Datatype sendtype,
	void *recvbuf,
	int recvcount,
	MPI_Datatype recvtype,
	MPI_Comm comm
);
```

![[AllGather.png]]

```c
/* Come scatter ma permette:
 * Spazi vuoti in mezzo ai messaggi
 * Dimensione irregolare
 * Ordine qualsiasi
 */
int MPI_Scatterv(
	const void *sendbuf,   /*Buffer di invio del processo root */
	const int sendcounts[],
		/* Per ciascun processo il numero di elementi da inviare */ 
	const int displs[],
		/* Per ciascun processo il numero di elementi prima
		   dell'inizio del blocco */
	MPI_Datatype sendtype, /* Tipo di dato */
	void *recvbuf,         /* Buffer di ricezione */
	int recvcount,         /* Numero di elementi da ricevere */
	MPI_Datatype recvtype, /* Tipo di dato da ricevere */
	int root,              /* Rank mittente */
	MPI_Comm comm          /* Communicator */
 	);
```

![[Scatterv.png]]

```c
int MPI_Reduce(
	const void *sendbuf,   /* Buffer del mittente */
	void *recvbuf,         /* Buffer del ricevente */
	int count,             /* N.elementi del buffer */
	MPI_Datatype datatype, /* Tipo del dato */
	MPI_Op op,             /* Operazione da eseguire */
	int root,              /* Rank del ricevente */
	MPI_Comm comm          /* Communicator */
);
```

![[MPIReduce.png]]
- $\text{count}=3$

```c
int MPI_Scan(
	const void *sendbuf,   /* buffer di invio dei processori */
	void *recvbuf,         /* buffer di ricezione (solo ricevitore) */
	int count,             /* N.elementi del buffer */
	MPI_Datatype datatype, /* Tipo di dato */
	MPI_Op op,             /* Operatore da applicare */
	MPI_Comm comm          /* Communicator */
	);
```
## CUDA
>[!info] Device Code

Per scrivere device code serve definire una funzione "speciale".
```c
__global__ void funcName()
{...}
```

>[!help] Esecuzione

Per eseguire del device code.
```c
#define BLKDIM 1024
int main()
{
	funcName<<<bB, nT>>>();
	// nB -> Numero di blocchi
	// nT -> Numero di thread per blocco
	
	/* Con un array di dimensioni N */
	const size_t SIZE = N * sizeof(int);
	funcName<<<(N + BLKDIM - 1)/BLKDIM, BLKDIM>>>();
	/* Ogni thread esegue una cella dell'array */
}
```

>[!tip] Blocchi Multidimensionali

```c
int main()
{
	dim3 grid1(3);
	// Defines a variable "grid" representing a 3x1x1 block.
	dim3 grid2(3,4);
	// Defines a variable "grid2" representing a 3x4x1 block.
	dim3 blk(3,4,7);
	// Defines a variable "blk" representing a 3x4x7 block.
	
	dim block(16);
	myKernel<<<grid1,block>>>();
	// Lanch 3 blocks, 16 threads per block (1D)
	
	myKernel<<<grid2, blk>>>();
	// Launch 3x4 blocks (3x4x7) threads per block (3D)
}
```

>[!warning] Attenzione
>Il blocco può contenere un massimo numero di thread (in base alla `GPU`), solitamente $1024$.
>Si possono, quindi, avere:
>- Array da $1024$.
>- Matrici $32\times 32$.
>- "Cubi" $8\times 8\times 16$

Ogni thread ha accesso alle seguenti variabili per riconoscere la sua posizione:
- `blockIdx​`: indica in quale blocco il thread si trova (`x`, `y` o `z`).
- `threadIdx​`: indica in quale indice del blocco il thread si trova (`x`, `y` o `z`).

>[!abstract] Indicizzazione di Array

```c
/* 1 Dimensione */
int index = threadIdx.x + blockIdx.x * blockDim.x;

/* 2 Dimensioni */
int i = threadIdx.y + blockIdx.y * blockDim.y;
int j = threadIdx.x + blockIdx.x * blockDim.x;
```
