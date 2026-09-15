## Modellazione di un Sistema usando LTS e FSP
---
> [!info] LTS
> Gli [[Modellazione di Sistemi Concorrenti#Approcci di modellazione|LTS]] sono simili alle [[../../Internet of Things/Architetture/Finite State Machines|Finite State Machines]].
> Hanno delle proprietà matematiche ben definite che facilitano l'*analisi formale* e il *controllo meccanico*.

In questa forma di macchina a stati le transizioni sono etichettate con i nomi delle azioni.

Gli `LTS` sono usati per rappresentare il comportamento usando diagrammi.


> [!hint]
> Rappresentare le macchine a stati graficamente può limitare la complessità dei problemi che possono essere affrontati.

Per descrivere i modelli, si usano delle notazioni testuali, chiamate `FSP`
- `FSP` è un modo di ***descrivere il comportamento di un sistema*** usando l'*algebra* e *costrutti matematici*.
### Processo di Modellazione
> In un programma concorrente, con il termine processo, si intende l'esecuzione di un programma sequenziale.


> [!help] Stato
> Lo ***stato*** di un processo in un qualsiasi momento nel tempo consiste nell'insieme dei valori delle variabili dichiarate dal programmatore e da variabili implicite come il [[../../Architettura degli Elaboratori/Architettura del Calcolatore/La CPU#Registri|program counter]] e i contenuti dei registri.

Come il processo viene eseguito, ***trasforma il proprio stato*** eseguendo le istruzioni.
- Ogni istruzione consiste in una sequenza di una o più azioni atomiche che fanno cambi di stato indivisibili.

Con un *numero finito di stati* si possono rappresentare una ***quantità infinita di comportamenti***.
- Ogni azione causa una transizione dallo stato corrente allo stato successivo.
- L'ordine con cui le azioni possono accadere è determinato da un ***grafo delle transizioni***, una rappresentazione astratta del programma.

### Linguaggio Formale

> [!tl;dr] Transition System
> Formalmente un transition system è una coppia $(S, T)$ dove:
> - $S$ è l'insieme degli stati e $T$ è un sottoinsieme di $S\times S$

Diciamo che esiste una transizione dallo stato $p$ allo stato $q$ se $(p,q)\in T$ e viene etichettato come $p\to q$


> [!cite] Labelled Transition System
> Un `LTS` è una tupla $(S,\wedge,T)$ dove:
> - $\wedge$ è l'insieme delle label e $T$ è sottoinsieme di $S\times \wedge \times S$

Diciamo che esiste una transizione da $p$ a $q$ con label $\alpha$ se e solo se $(p, \alpha, q)\in T$ e lo denotiamo come $p\xrightarrow{\alpha}q$

## Finite State Process
---
> [!info] FSP
> `FSP` è una ***semplice notazione algebrica*** per descrivere i modelli di processo.

Ogni descrizione `FSP` ha una corrispondente descrizione `LTS`.

#### Sintassi
> Terminatore
- Come terminatore viene utilizzato il "$.$"

> Definizione di multipli processi
- Si usa "$,$" per la definizione di più processi.

L'operatore "$=$" significa "è definito come".
### Operatori
#### Action Prefix
> [!tldr] Idea
> Un ***action prefix*** è un modo per specificare che un processo sta eseguendo una azione e che terminerà in un novo processo.

Se $x$ è una azione e $P$ un processo, allora l'action prefix $(x\to P)$ descrive il processo che esegue l'azione $x$ e poi ***si comporta esattamente come descritto*** da $P$.

La definizione di un nuovo processo si fa con la seguente notazione:
$$Q = (x \to P).$$
- Il processo può essere definito in termini di altri processi attraverso l'utilizzo di operatori.

Alla fine un processo è una sequenza di azioni.

I processi che non finiscono sono specificati attraverso definizioni ricorsive.
- $P = (x\to P)$


> [!example] Interruttore della luce

- $SWITCH = OFF$
- $OFF = (on \to ON)$
- $ON = (off \to OFF)$

Una descrizione equivalente si ottiene applicando le sostituzioni:
$SWITCH = (on\to off \to SWITCH)$

#### Choice Construct
> [!tldr] Idea
> In `FSP` il choice construct è usato per modellare una ***scelta***.

Dato uno stato, ci potrebbero essere più possibili transizioni, a seconda degli eventi o gli stati interni.

Se $x$ e $y$ sono azioni allora $(x \to P | y \to Q)$ descrive un processo che inizialmente ingaggia in una tra le azioni $x$ o $y$.
- Dopo che l'azione è accaduta, il comportamento successivo è descritto da $P$ se l'azione era $x$ e $Q$ se l'azione era $y$.


> [!help] Scelta non deterministica
> 

Il processo $(x \to P | x \to Q)$ si dice non deterministico poiché dopo l'azione $x$, si potrebbe comportare sia come $Q$ che come $P$.

> Esempio

`COIN = (toss->heads->COIN | toss -> tails -> COIN).`