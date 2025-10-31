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
