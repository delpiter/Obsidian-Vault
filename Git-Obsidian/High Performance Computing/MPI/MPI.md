## Message Passing Interface
---
>[!info] Message Passing
>Il [[14 - Message Passing|message passing]] è il modello di programmazione predominante per [[Git-Obsidian/Architettura degli Elaboratori/Architetture a Confronto/Architetture Parallele#Multicomputer|supercomputer e cluster]].

>[!tldr] `MPI`
>`MPI` è una libreria usata nei linguaggi sequenziali convenzionali `{c icon} C`, `{fortran icon} fortran`, `{cpp icon} C++`.

È basata sul paradigma [[Git-Obsidian/Architettura degli Elaboratori/Architetture a Confronto/Architetture Parallele#Classificazione di sistemi Paralleli|SPMD]] (***S***ingle ***P***rogram ***M***ultiple ***D***ata).
- Lo stesso programma è eseguito da `P` processi.
- Ogni processo potrebbe seguire un **percorso di esecuzione diverso** in base al suo `ID` (*rank*).

> Avviene una ***isolazione di spazi di indirizzi separati***.
- Non ci sono [[8 - Concorrenza#Race Condition|race condition]].
- Sono possibili ***errori di comunicazione***.

### Comunicazione
> Tutte le operazioni di sincronizzazione e comunicazione richiedono delle *chiamate a subroutine*.

>[!warning] Non ci sono variabili condivise

> Ci sono 3 tipologie di subroutine:

#### Communication
>[!caution] Comunicazione

- A **coppie** o Point-to-Point.
- Collettiva comprendendo processi multipli.

#### Synchronization
>[!summary] Sincronizzazione

- **Barriere**.
- **Non** ci sono lock perché non ci sono variabili condivise da proteggere.

#### Queries
>[!question] Queries

- **Quanti** processori ci sono?
- **Quale** processore sono?
- Ci sono dei messaggi in attesa?

#### Funzioni di Base
> Ci sono due funzioni importanti frequentemente usate in un programma parallelo.

>[!quote] `{c icon} MPI_Comm_size()`

- Ritorna il ***numero di processi***.

>[!quote] `{c icon} MPI_Comm_rank()`

- Ritorna il ***rank***, un numero tra $0$ e $size-1$, che identifica il *processo chiamante*.


> Altre funzioni necessarie per *programmi semplici* sono:

>[!quote] `{c icon} MPI_Init()`

>[!quote] `{c icon} MPI_Finalize()`

>[!quote] `{c icon} MPI_Send()`
- Blocking Send

>[!quote] `{c icon} MPI_Recv()`
- Blocking Receive.

>[!quote] `{c icon} MPI_Abort()`
- Abort the computation.

## Concetti di Base
---
### Organizzazione dei Processi
>[!summary] Communicator
>I ***processi*** possono essere raggruppati in *gruppi*.
>- Un *gruppo* è "identificato" dal **communicator**.

Un *processo* è identificato dal suo **rank** nel gruppo associato con un *communicator*.
- Il communicator di default è `MPI_COMM_WORLD` il cui gruppo contiene ***tutti i processi***.

### Data Types
>[!tldr] Idea
>I dati ***inviati*** o ***ricevuti*** sono descritti da una *tripla*.
>- `address`, `count`, `datatype`.

I **tipi di dati** sono:
- Tipi *predefiniti*, gli equivalenti di `MPI` dei tipi di dato base del linguaggio (`MPI_INT`, `MPI_DOUBLE`, etc...).
- Un *array di blocchi contigui* di tipi `MPI`.
- E altre strutture più complicate che richiedono la definizione di ***custom datatype***.

Ci sono funzioni `MPI` per definire tipi di dato personalizzati.

### Tags
>[!info]
>I messaggi sono inviati con un ***tag*** intero definito dall'utente, per aiutare il processo ricevente ad *identificare il messaggio*.

I messaggi possono essere filtrarti dal ricevente ***specificando un tag***.
- Il tag `MPI_ANY_TAG` accetta ***qualsiasi tag***.

Se il ricevente riceve un messaggio con un tag diverso da quello specificato nella `{c icon} MPI_Recv()`.
- Il messaggio viene ***mantenuto in attesa*** di una `{c icon} MPI_Recv()` con il tag corretto.

### Status
>[!failure] Stato
>Lo ***stato*** è una *struttura dati* con parametri, tra cui:
>- `{c} int MPI_SOURCE`
>- `{c} int MPI_TAG`
>- `{c} int MPI_ERROR`
>- etc...

Se un processo [[Send e Receive#Blocking Receive|ricevente]] utilizza `MPI_ANY_TAG` o `MPI_ANY_SOURCE`, attraverso lo stato è in grado di sapere queste informazioni.
- Da chi è arrivato.
- Il tag del messaggio.
- etc...
