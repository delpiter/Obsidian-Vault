## Send
---
### Blocking Send

```c title:Syntax
int MPI_Send(const void *buf, int count, MPI_Datatype datatype,
			 int dest, int tag, MPI_Comm comm);
```

>[!abstract] Parametri

> `{c icon} *buf`
- ***Puntatore*** all'area di memoria dove è salvato il dato.

> `{c icon} count`
- Indica il numero di ***elementi inviati***
>[!warning] Non il numero di `byte`

>`{c icon} datatype`
- Indica il [[MPI#Data Types|tipo di dato]] [[MPI]] che viene inviato.

> `{c icon} dest`
- Indica il *rank* del processo target ricevente.
- Se `{c icon} dest=MPI_PROC_NULL` l'operazione **non ha effetti**.

> `{c icon} tag`
- Indica il [[MPI#Tags|tag]] del messaggio.

>`{c icon} comm`
- Indica il [[MPI#Concetti di Base|communicator]] del messaggio.

>[!attention] Nota bene
> Non è la classica [[14 - Message Passing#Tassonomia|send bloccante]], il processo si sblocca quando il sottosistema `MPI` del nodo locale *prende in carico il messaggio*.
>>[!danger] **NON** quando il messaggio è arrivato al destinatario.

>[!bug] Attenzione
>Utilizzando `send` e `receive` ***bloccanti*** è possibile che accada un [[9 - Condivisione di Risorse#Deadlock|deadlock]].

Per evitare i ***deadlock*** si può:
- Riordinare le *operazioni*.
- Utilizzare comunicazioni ***non bloccanti***.

### Non Blocking Send
```c
int MPI_Isend(const void *buf, int count, MPI_Datatype datatype, 
			int dest, int tag, MPI_Comm comm, MPI_Request *request);
```

>[!note] Nota
>È possibile utilizzare **funzioni bloccanti** con con **funzioni non bloccanti**. 

>[!abstract] Parametri

I parametri sono gli stessi della `send` bloccante, a meno del parametro `{c} MPI_Request *request`.
- Parametro che permette di esaminare lo **stato delle operazioni** ([[Interfacciamento di Periferiche#Polling|polling]]) tramite delle funzioni.
#### Controllo dello Stato
```c title:Test
int MPI_Test(MPI_Request *request, int *flag, MPI_Status *status);
```

- ***Controlla lo stato*** di una *send* o *receive* bloccante specificata.
- L'intero `flag` indica se l'operazione è completata o no (`1` = **completata**).
- Per il controllo di multiple operazioni, si possono usare `{c} MPI_Testany()`, `{c} MPI_Testall()` e `{c} MPI_Testsome()`.
- Serve per fare ***polling***.
- Vedi il [[Comandi#^617056|manuale]] per i dettagli.

```c title:Wait
int MPI_Wait(MPI_Request *request, MPI_Status *status);
```
- ***Blocca l'esecuzione*** fino a che una send o receive specificata termina.
- Per il controllo di multiple operazioni, si possono usare `{c} MPI_Waitany()`, `{c} MPI_Waitall()` e `{c} MPI_Waitsome()`.
## Receive
---
### Blocking Receive
```c title:"Syntax"
int MPI_Recv(void *buf, int count, MPI_Datatype datatype,
			 int source, int tag, MPI_Comm comm, MPI_Status *status);
```

>[!abstract] Parametri

> `{c icon} *buf`
- ***Puntatore*** all'area di memoria dove verrà salvato il dato.

> `{c icon} count`
- Indica il *massimo numero di elementi* che il ricevente è disposto a ricevere.
	- È un ***upper bound***

>[!fail] Se il mittente riceve più di quanto si aspetta viene lanciato l'errore `MPI_ERR_TRUNCATE`

>`{c icon} datatype`
- Indica il [[MPI#Data Types|tipo di dato]] [[MPI]] che viene ricevuto.

> `{c icon} source`
- Indica il *rank* del processo mittente nel ***communicator*** specificato in`comm`.
	- Se `{c icon} source=MPI_ANY_SOURCE` può ricevere da *qualsiasi processo*.

> `{c icon} tag`
- Indica il [[MPI#Tags|tag]] del messaggio.

>`{c icon} comm`
- Indica il [[MPI#Concetti di Base|communicator]] del messaggio.

>`{c icon} status`
- Lo [[MPI#Status|status]] contiene informazioni aggiuntive.
- Si usa `MPI_STATUS_IGNORE` se nessuna informazione aggiuntiva è necessaria.

Per sapere quanti elementi sono stati effettivamente ricevuti si usa la funzione:
```c
int MPI_Get_count(const MPI_Status *status, MPI_Datatype datatype,
            int *count);
```

### Non Blocking Receive
```c
int MPI_Irecv(void *buf, int count, MPI_Datatype datatype,
		    int source, int tag, MPI_Comm comm, MPI_Request *request);
```

>[!abstract] Parametri

I parametri sono gli stessi della `receive` bloccante, a meno del parametro `{c} MPI_Request *request`.
- Parametro che permette di esaminare lo **stato delle operazioni** ([[Interfacciamento di Periferiche#Polling|polling]]).

## Abortire L'operazione
---
```c
int MPI_Abort(MPI_Comm comm, int errorcode);
```

>[!danger] Attenzione
>Per ***abortire*** una computazione **non** usare `exit()` o `abort()`.

Utilizzare la funzione `{c} MPI_Abort()`
- Interrompe "*con grazia*" l'esecuzione di tutti i processi `MPI` nel ***communicator*** `comm`.
- Ritorna l'errore con il codice `errorcode`.

## SendRecv
```c title:"syntax"
int MPI_Sendrecv(const void *sendbuf, int sendcount, 
			MPI_Datatype sendtype, int dest, int sendtag,
			void *recvbuf, int recvcount,
            MPI_Datatype recvtype, int source, int recvtag,
            MPI_Comm comm, MPI_Status *status);
```

>[!info]
>Esegue una ***send e una receive bloccanti*** in una singola chiamata.
>- `MPI` [[7 - Scheduler|schedula]] la comunicazione in modo che non possa verificarsi il [[9 - Condivisione di Risorse#Deadlock|deadlock]].

>[!abstract] Parametri

> I parametri della routine sono tutti i parametri di una `{c}MPI_Send()` seguiti dai parametri di una `{c} MPI_Recv()`.

È possibile che uno dei processi che chiamano la *routine* non debba inviare alcun dato.
- È possibile specificare, in questo caso un ***ricevitore nullo***.

```c
next = (my_rank < comm_sz - 1 ? my_rank + 1 : MPI_PROC_NULL);
next = (my_rank > 0 ? my_rank - 1 : MPI_PROC_NULL);
```