## Il problema della sezione critica
---
> Introdotto inizialmente da [[../Algoritmi e Strutture Dati/Strutture Dati/Grafi/Cammini Minimi/Algoritmo di Dijkstra|Dijkstra]] nel $1965$.

Il problema della sezione critica può essere considerato uno dei problemi della programmazione concorrente più importanti e più studiati. 

> [!cite] Definizione
> $N$ processi, ciascuno esegue in un loop infinito una sequenza di istruzioni che possono essere divisi in due sottosezioni:
> - La ***sezione critica*** (`CS`)
> - e la ***sezione non critica*** (`NCS`)

```
P[1..n]:
loop {
	<non-critical section>
	entry protocol
	<critical section>
	exit protocol
	<non-critical section>
}
```

I protocolli garantiscono rispettivamente:
- Che un processo prima o poi entrerà nella sezione critica
- Che il processo dentro la sezione critica esca.

Ogni sezione critica tipicamente è una sequenza di statement che possono accedere ad un oggetto condiviso.

![[../Sistemi Operativi/Teoria/10 - Sezioni Critiche#Requisiti]]

Una qualsiasi soluzione deve soddisfare la [[Modelli/Finite State Processes#Check delle proprietà del sistema|progress property]] per la sezione critica.
- Una volta iniziata l'esecuzione di una sezione critica deve prima o poi finire.

La sezione non critica *non deve necessariamente soddisfare questa proprietà*.

### Soluzioni: algoritmi vs meccanismi
>[!caution] Meccanismi
> Il problema della sezione critica può essere risolto usando meccanismi basici come i semafori o i lock #addLink che devono essere forniti dalla macchina concorrente.

> [!tl;dr] Algoritmi
> Il problema può essere risolto anche attraverso algoritmi  specifici, senza l'utilizzo di meccanismi hardware.
#### Soluzioni
> Analizziamo inizialmente il problema considerando $2$ processi $P$ e $Q$ che condividono alcune variabili globali.

I protocolli potrebbero richiedere variabili locali o globali per il funzionamento.
- Assumiamo che le variabili usate nelle sezioni critiche e non critiche ***NON*** sono usate nei protocolli

##### Primo tentativo
Definiamo una variabile globale `integer turn <- 1`

Definiamo i due processi
```pseudo
	\begin{algorithm}
	\begin{algorithmic}
	\Procedure{Q}{}
	\While{true}
	\State $ \text{Non-critical section} $
	\State $ await \text{ turn}=1 $
	\State $ \text{Critical Section} $
	\State $ \text{turn} \leftarrow 2 $
    \EndWhile
    \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```

```pseudo
	\begin{algorithm}
	\begin{algorithmic}
	\Procedure{P}{}
	\While{true}
	\State $ \text{Non-critical section} $
	\State $ await \text{ turn}=2 $
	\State $ \text{Critical Section} $
	\State $ \text{turn} \leftarrow 1 $
    \EndWhile
    \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```

L'istruzione `await turn=1` è una notazione per un'istruzione che aspetta che la condizione `turn=1` sia vera
- Potrebbe essere implementata con un ***loop busy-waiting*** che non fa nulla fino a che la condizione è vera.

> [!warning] Attenzione
> Uno dei due processi potrebbe avere un loop infinito ***fuori dalla sezione critica***.

Questo caso è *ammesso secondo le regole*, ma causerebbe un ***deadlock***
- un processo è bloccato nel loop infinito e il secondo processo attende che il primo entri nella sezione critica, esca e gli passi il turno.
