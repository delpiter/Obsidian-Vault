## Collective Communication Operation
---
>Le operazioni [[Send e Receive]] sono raramente utilizzate in pratica.

Molte applicazioni utilizzano il ***pattern bulk synchronous***.

>[!help] Collective Communication
>Le ***operazioni di comunicazione collettiva*** sono eseguite da tutti i processi in un gruppo, per *calcolare* e *condividere* un risultato globale.

>[!done] Efficienza
>Le operazioni di comunicazione collettiva sono ***più efficienti*** rispetto a operazioni point-to-point.

>[!hint] Informazione

Per ogni *operazione di comunicazione collettiva* è presente una funzione sia ***sincrona*** che ***asincrona***.
### Barrier
```c title:syntax
int MPI_Barrier(MPI_Comm comm);
```

>[!info]
> Esegue una ***sincronizzazione a barriera*** in un gruppo di processi.

Il processo si ***blocca*** fino a quando tutti gli altri processi nel gruppo raggiungono la stessa funzione.

### Broadcast
```c title:syntax
int MPI_Bcast(void *buffer, int count, 
			  MPI_Datatype datatype, int root, MPI_Comm comm);
```

>[!info]
>Invia un ***messaggio*** [[Reti IP#Broadcast|broadcast]] a tutti gli altri processi del gruppo.
>>[!warning] Tutti i processi eseguono la funzione

>[!abstract] Parametri

> `{c icon} *buffer`
- Buffer da **spedire** o da **ricevere**.
	- Se sono *ricevente*, **ricevo**, se sono *mittente*, **spedisco**.

> `{c icon} root`
- Indica il sorgente del *messaggio broadcast*.
	- Internamente ci sarà un `if` che controlla se il processo corrente è mittente o destinatario.
### Scatter
```c title:syntax
int MPI_Scatter(const void *sendbuf, int sendcount, 
				MPI_Datatype sendtype,void *recvbuf, int recvcount, 
				MPI_Datatype recvtype, int root ,MPI_Comm comm);
```

![[Scatter.png]]

>[!info]
>***Distribuisce dati*** a gli altri processi nel gruppo.

>[!abstract] Parametri

> `{c icon} *sendbuf`
- Buffer di invio, per i ricevitori può essere impostato a `NULL`.

> `{c icon} sendcount`
- Numero di ***elementi da spedire*** a ciascun processo (dimensione del singolo blocco).

> `{c icon} *recvbuf`
- Buffer di ricezione.
>[!warning] Deve essere allocato anche dal mittente

> `{c icon} recvcount`
- Numero di ***elementi da ricevere*** dal processo mittente, quasi sempre sarà uguale a `sendcount`.

>[!question] A che cosa serve?
> Serve nel caso si utilizzino i tipi di dato ***definiti*** dall'utente.
>>[!example] Esempio
>>Un array con dei *blocchi vuoti*.
>
>Stesso discorso con il ***tipo di dato***.

> `{c icon} root`
- **Id** del processo *mittente*.

Produce lo stesso risultato se il processo mittente esegue una serie di `{c icon} MPI_Send()`.
- Con tutti gli altri processi in ascolto.

### Gather
```c title:syntax
int MPI_Gather(const void *sendbuf, int sendcount,
			   MPI_Datatype sendtype, void *recvbuf, int recvcount, 
			   MPI_Datatype recvtype, int root, MPI_Comm comm);
```

>[!info]
>***Raccoglie dati*** da altri processi.

>[!abstract] Parametri

> Parametri uguali alla funzione `scatter`
- Il send buffer **deve** essere definito da tutti i processi.
- Il buffer di ricezione deve essere definito ***solo dal ricevitore***.
#### All Gather
```c title:syntax
int MPI_Allgather(const void *sendbuf, int  sendcount,
             MPI_Datatype sendtype, void *recvbuf, int recvcount,
             MPI_Datatype recvtype, MPI_Comm comm);
```

>[!info]
>***Raccoglie dati*** dagli altri processi e poi ***distribuiti*** a tutti i processi.
>Equivalente a `gather()` seguito da un `scatter()`.

Possiamo assumere sia più efficiente delle due funzioni singole.
![[Pasted image 20260116171635.png]]

### Scatterv e Gatherv
>[!tldr] Idea
>Risultato delle operazioni uguali a `MPI_Scatter()` e `MPI_Gather()`, con qualche specifica in più.

- Degli ***spazi*** sono *permessi* in mezzo ai messaggi nel **buffer sorgente**.
- Messaggi di ***dimensione irregolari*** sono permessi.
- I dati possono essere distribuiti ai processi in ***qualsiasi ordine***.

```c title:syntax
int MPI_Scatterv(const void *sendbuf, const int sendcounts[], 
				 const int displs[], MPI_Datatype sendtype, 
				 void *recvbuf, int recvcount, MPI_Datatype recvtype, 
				 int root, MPI_Comm comm);
```

![[Scatterv.png]]

>[!abstract] Parametri

> `{c icon} displs[]`
- Indica, per ciascun processo, ***quanti elementi ci sono prima che inizi il blocco*** interessato.
- L'***indice dell'array*** corrisponde all'*Id del processo*.

>`{c icon} sendcounts[]`
- Indica, per ciascun processo, ***quanti elementi ci sono nel blocco*** di interesse.

> `{c icon} *sendbuf`
- È il buffer del processo `root` contenente i dati da inviare, i riceventi non accedono a questo buffer.
### Reduce
```c title:syntax
int MPI_Reduce(const void *sendbuf, void *recvbuf, int count,
			   MPI_Datatype datatype, MPI_Op op, int root,
			   MPI_Comm comm);
```

>[!info]
>Esegue una [[Reduce|riduzione]] e mette il risultato in un processo.

> `{c icon} MPI_Op op`
- È l'***operazione da eseguire*** come riduzione (somma, sottrazione, max, min, etc...).

> `{c icon} count`
- Se `count>1`, `{c} recvbuf[i]` è la riduzione di tutti gli elementi in `{c} sendbuf[i]` nei vari processi.

![[MPIReduce.png]]

| Operation      | Value                           |
| -------------- | ------------------------------- |
| `MPI_MAX()`    | Maximum                         |
| `MPI_MIN()`    | Minimum                         |
| `MPI_SUM()`    | Sum                             |
| `MPI_PROD()`   | Product                         |
| `MPI_LAND()`   | Logical AND                     |
| `MPI_BAND()`   | Bitwise AND                     |
| `MPI_LOR()`    | Logical OR                      |
| `MPI_BOR()`    | Bitwise OR                      |
| `MPI_LXOR()`   | Logical exclusive OR            |
| `MPI_BXOR()`   | Bitwise exclusive OR            |
| `MPI_MAXLOC()` | Maximum and location of maximum |
| `MPI_MINLOC()` | Minimum and location of minimum |
>[!hint] Min e Max Loc
>Gli operatori `MPI_MAXLOC()` e `MPI_MINLOC()` non ritornano l'elemento calcolato dalla riduzione, ma una coppia di elementi $(\text{value}, \text{index})$

```c title:"Min/Max"
struct {double val; int idx} in, out;
dst = 1; /* result will be placed in process 1 */
MPI_Reduce(&in, &out, 1, MPI_DOUBLE_INT, MPI_MINLOC,
		   dst, MPI_COMM_WORLD);
```

#### All Reduce
```c title:syntax
int MPI_Allreduce(const void *sendbuf, void *recvbuf, int count,
				  MPI_Datatype datatype, MPI_Op op, MPI_Comm comm);
```

>[!info]
> Esegue una ***riduzione*** e propaga il risultato in *tutti i processi*.

### All to All
```c title:syntax
int MPI_Alltoall(const void *sendbuf, int sendcount,
				MPI_Datatype sendtype, void *recvbuf, int recvcount,
				MPI_Datatype recvtype, MPI_Comm comm);
```

>[!info]
>Ogni processo esegue una ***operazione di scatter***.

>[!abstract] Parametri

> `{c icon} sendcount` e `{c icon} recvcount`
- Sono rispettivamente il numero di elementi mandati e ricevuti da ogni processo.

Il buffer di ricezione conterrà `recvcount` elementi ***ricevuti da ciascun processo***.

### Scan
```c title:syntax
int MPI_Scan(const void *sendbuf, void *recvbuf, int count,
			 MPI_Datatype datatype, MPI_Op op, MPI_Comm comm);
```

>[!info]
>Esegue una [[Scan]] ***inclusiva*** sugli elementi, in maniera simile alla *reduce*.

> `{c icon} count`
- Se `count>1`, `{c} recvbuf[i]` è la scan di tutti gli elementi in `{c} sendbuf[i]` nei vari processi.