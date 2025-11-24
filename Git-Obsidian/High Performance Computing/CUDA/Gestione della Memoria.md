>[!info]
>Le memorie di ***device*** e di ***host*** sono entità *completamente separate*.

Puntatori alla *memoria di device* possono essere passati da/a **codice host**.
>[!fail] I puntatori alla **memoria device** ***non*** possono essere dereferenziati dal codice host

[[CUDA]] mette a disposizione delle `API` per la gestione della ***device memory***:
- `{c icon} cudaMalloc()`, `{c icon} cudaFree()`, `{c icon} cudaMemcpy()`.
- Sono simili agli equivalenti di `{C icon} C`: `{c icon} Malloc()`, `{c icon} free()`, `{c icon} memcpy()`.
- Le chiamate sono bloccanti ma sono presenti delle ***routine asincrone***.
	- Per la sincronizzazione dopo l'uso di una funzione asincrona:
		- `cudaDeviceSynchronize()`.

```c title:"CUDA memory Management"
int *buffer, *d_buffer;
const int SIZE = n * sizeof(buffer);

buffer = (int *) malloc(SIZE);
cudaMalloc((void **)&d_buffer, SIZE);

cudaMemcpy(buffer, d_buffer, SIZE, cudaMemcpyHostToDevice);

/* Computations */

cudaMemcpy(d_buffer, buffer, SIZE, cudaMemcpyDeviceToHost);

cudaFree(d_buffer);

/* Elaborate Output */

free(buffer);
```

## Specifiche dei Thread
---
>[!question] Perché aggiungere la complessità dei thread?

Al contrario dei *blocchi paralleli* i threads hanno dei meccanismi in più:

>[!done] Meccanismi di sincronizzazione e condivisione di informazioni
- Meccanismi che servono principalmente a ***ridurre la pressione esercitata sulla memoria globale*** (molto lenta rispetto ai core).
#### Esempio
> Consideriamo una applicazione di uno [[Stencil]] ad un array `1D` di elementi.

>[!abstract] Consideriamo un raggio dello stencil di $3$.
>Ogni elemento in output è la somma di $7$ *elementi in input*.
>- Per semplicità non verranno calcolati i primi e gli ultimi *radius* elementi.

Ogni thread processa un elemento dell'**output**.
- In questo modo ogni elemento in input viene letto $7$ ***volte*** ($2R + 1$).

>[!danger] Gli accessi alla memoria globale sono causa di bottleneck
- A causa della ***bandwidth limitata***.

### Condivisione della Memoria
>[!info]
> All'interno di un *blocco* i thread possono condividere i dati attraverso la ***memoria condivisa***.

La memoria del blocco è ***estremamente veloce*** e *gestita dall'utente*.
- Tipo una [[Cache]] ma gestita dal programmatore.

> `{c} __shared__`
- Le variabili vengono dichiarate tramite il costrutto `{c} __shared__ int var[1024];`
- Queste variabili non saranno visibili ai ***thread*** in altri ***blocchi***.

```c title:"stencil"
__shared__ int temp[BLKDIM + 2 * RADIUS];
const int gindex = threadIdx.x + blockIdx.x * blockDim.x + RADIUS;
const int lindex = threadIdx.x + RADIUS;
/* ... */
temp[lindex] = in[gindex]; /* Copies blockDim.x elements in one line */
if(threadIdx.x < RADIUS){
	/* Copies the ghost area  */
	temp[lindex - RADIUS] = in[gindex - RADIUS];
	temp[lindex + BLKDIM] = in[gindex + BLKDIM];
}

/* Computation */
```

>[!danger] Attenzione
>Potrebbe succedere che alcuni thread inizino la computazione prima che altri abbiano copiato il proprio valore nella ***memoria condivisa***.

> Soluzione: `{c icon} __syncthreads()`
- Sincronizza tutti i thread di un [[CUDA#Anatomia di una GPU|blocco]].

`{c icon} cudaDeviceSynchronize()` aspetta la fine dell'esecuzione del ***kernel***.

```c title:"Device Synchronization"
mykernel<<<X, Y>>>( );   /* kernel invocation */
cudaDeviceSynchronize(); /* Wait operation */
```

### Pattern di Accesso alla Memoria
>[!summary] Accessi alla Memoria
>Si può accedere alla memoria globale attraverso ***transazioni*** di $32,64,128$ `byte`.

I trasferimenti avvengono a partire da indirizzi multipli di $32,64,128$.
- L'hardware riesce a "*impacchettare*" assieme gli accessi ad uno stesso [[Scheduling in CUDA|warp]].
#### Caching Load
> Gli indirizzi sono allineati in una *cache line*.
- Il **warp** ha bisogno di $128$ `bytes`.
- $128$ `byte` vengono mossi nel `BUS`.
	- Utilizzo del `BUS`: $100\%$
	- Transazioni: $1$

![[CachingLoad.png]]

> Warp richiede $32$ parole di $4$ `byte` permutati in una *linea di cache*.
- Il **warp** ha bisogno di $128$ `bytes`.
- $128$ `byte` vengono mossi nel `BUS`.
	- Utilizzo del `BUS`: $100\%$
	- Transazioni: $1$

![[CachingLoad2.png]]

> Warp richiede $32$ parole di $4$ `byte` non allineati in una *linea di cache*.
- Il **warp** ha bisogno di $128$ `bytes`.
- $256$ `byte` vengono mossi nel `BUS`.
	- Utilizzo del `BUS`: $50\%$
	- Transazioni: $2$

![[CachingLoad3.png]]

> Tutti i thread richiedono la stessa parola da $4$ `byte`.
- Il **warp** ha bisogno di $4$ `bytes`.
- $128$ `byte` vengono mossi nel `BUS`.
	- Utilizzo del `BUS`: $3.125\%$
	- Transazioni: $1$

![[CachingLoad4.png]]

> Warp richiede $32$ parole di $4$ `byte` posizionate casualmente.
- Il **warp** ha bisogno di $128$ `bytes`.
- $N\times128$ `byte` vengono mossi nel `BUS`.
	- Utilizzo del `BUS`: $\displaystyle\frac{128}{N\times128}\%$

![[CachingLoad5.png]]

