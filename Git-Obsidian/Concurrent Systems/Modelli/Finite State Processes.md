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

#### Indexed Processes and Action
> [!tldr] Idea
> In `FSP` sia i processi locali che le action label possono essere ***indicizzate***, modellando processi e azioni che **possono assumere valori multipli**.

> Esempio: *Buffer*

$\text{BUFF}=(in[i:0..3]\to out[i]\to BUFF)$

È equivalente a scrivere:
$$
\begin{align}
\text{BUFF}=(in[0]\to out[0]\to BUFF  \\
\mid in[1]\to out[1]\to BUFF  \\
\mid in[2]\to out[2]\to BUFF \\
\mid in[3]\to out[3]\to BUFF)
\end{align}
$$
#### Variabili
> [!caution] Range
> Si può specificare un ***range*** riutilizzabile in più punti.

```
range T = 0..3
BUFF = (in[i:T]-> STORE[i]),
STORE[i:T] = (out[i] -> BUFF)
```

> [!abstract] Costanti
>

$\text{const } N=3$
#### Guarded Action
> [!tldr] Idea
> È spesso necessario definire alcune azioni in **base allo stato corrente della macchina**.
> Si possono usare delle *espressioni booleane* (**guards**) per indicare che una azione specifica può essere selezionata ***solo se l'espressione è vera***.

La scelta $(\text{when } B \ x\to P | y\to Q)$ significa che quando l'espressione $B$ è vera allora entrambe le azioni $x$ e $y$ possono essere scelte, altrimenti solo $y$ può essere scelta.
```example
COUNT (N=3) = COUNT[0],
COUNT[i:0..N] = ( when(i<N) inc->COUNT[i+1]
				| when(i>0) dec->COUNT[i-1]).
```

#### Process Alphabet
> [!abstract] Definizione 
> L'***alfabeto di un processo*** è l'insieme delle azioni in cui può trovarsi.

Per esempio l'alfabeto del processo count down descritto di seguito
```
COUNTDOWN (N=3) = (start-> COUNTDOWN[N]), 
COUNTDOWN[i:0..N] = (when(i>0) tick-> COUNTDOWN[i-1]
					|when(i==0) beep-> STOP
					|stop-> STOP ).
```

è $\{ \text{start}, \text{stop}, \text{tick}, \text{beep} \}$.

Un processo può compiere azioni ***contenute nel suo alfabeto***.

### Modellare la concorrenza
> [!summary] Parallel composition
> In `FPS` un ***sistema concorrente*** può essere modellato come una *composizione* di processi usando l'operatore parallelo $\mid\mid$.

Se $P$ e $Q$ sono processi, allora $(P \mid\mid Q)$ rappresenta l'esecuzione concorrente di $P$ e $Q$.

La ***macchina a stati*** che rappresenta la *composizione*, genera *tutti i possibili percorsi* in [[../../Sistemi Operativi/Teoria/8 - Concorrenza#Multiprogramming|interleaving]] dei processi costituenti.

> **Esempio**
- Il processo `ITCH=(scratch->STOP).` ha una singola esecuzione che consiste nell'azione `scratch`.
- Il processo `CONVERSE = (think->talk->STOP).` ha una singola esecuzione possibile `think->talk`.

Il ***processo combinato*** `||CONVERSE_ITCH = (ITCH || CONVERSE).` ha le seguenti possibili esecuzioni:
- $think\to talk\to scratch$
- $think\to scratch\to talk$
- $scratch\to think\to talk$

> Esempio radio e orologio.

```
CLOCK = (tick->CLOCK).
RADIO = (on->off->RADIO).
||CLOCK_RADIO = (CLOCK || RADIO).
```

![[attachements/ClockRadio.png]]

##### Modellare la concorrenza attraverso l'interleaving
> L'[[../Sistemi Concorrenti#Terminologia|esecuzione di un sistema concorrente]] consiste di multipli processi attivi allo stesso tempo.

> [!question] Dobbiamo modellare la velocità con cui un processo esegue in relazione all'altro?

La *velocità di esecuzione di un processo* in realtà dipende da **diversi fattori** come il numero di processori, la strategia di scheduling e il sistema operativo.

Un programma concorrente deve funzionare correttamente indipendentemente dai fattori esterni come il [[../../Sistemi Operativi/Teoria/3 - Livelli del Sistema Operativo#Introduzione|SO]] o il numero/qualità dei processori.

Scegliamo allora di ***non modellare una velocità relativa*** ma semplicemente i processi *vengono eseguiti ad una velocità arbitraria relativa*.
- Astrazione che ci allontana dal **tempo di esecuzione**.


> [!fail] Svantaggio

Non si possono specificare le *proprietà real-time* di un programma


> [!done] Vantaggio
> 

Si possono *verificare altre proprietà* di una particolare configurazione del computer.

L'indipendenza è molto importante per la ***portabilità*** dei programmi concorrenti.

#### Interaction
> L'interazione tra processi è modellata attraverso *azioni condivise tra i processi*.

Gli esempi precedenti sono tutte *composizioni di processi* con ***alfabeti distinti***.
- Se una composizione ha delle azioni in comune queste azioni si dicono condivise (*shared*).

>[!todo] Le azioni condivise sono il modo con cui l'interazioni tra processi è modellata
>

```
BILL = (play -> meet -> STOP).
BEN = (work -> meet -> STOP).
||BILL_BEN = (BILL || BEN).
```

Le possibili *tracce di esecuzione* sono le seguenti:
- $\text{play}\to \text{work}\to \text{meet}$
- $\text{work}\to \text{play}\to \text{meet}$

L'**interazione** tra processi ***riduce sempre le combinazioni possibili*** di transizioni di due processi concorrenti.

> Esempio:

```
MAKER = (make->ready->MAKER).
USER = (ready->use->USER).

||MAKER_USER = (MAKER || USER).
```

Una officina crea **un** item e segnala che l'oggetto è pronto all'uso.

![[../attachements/FSPSyncronization.png]]

Però in questo caso **due item possono essere creati** prima che il primo venga *utilizzato*.
- Supponendo che questo è un **comportamento non voluto**, possiamo modificare il modello in moto tale che l'utente indica che l'item è stato utilizzato.

```
MAKERv2 = (make->ready->used->MAKERv2).
USERv2 = (ready->use->used->USERv2).
||MAKER_USERv2 = (MAKERv2 || USERv2).
```

Multipli processi possono partecipare in una azione condivisa.
```
MAKE_A = (makeA->ready->used->MAKE_A).
MAKE_B = (makeB->ready->used->MAKE_B).
ASSEMBLE = (ready->assemble->used->ASSEMBLE).
||FACTORY = (MAKE_A || MAKE_B || ASSEMBLE).
```

##### Composizione di processi composti
> Siccome una **composizione parallela** di un processo è esso stesso un *processo*, può essere usata nella definizione di ulteriori composizioni.

```
MAKE_A = (makeA->ready->used->MAKE_A).
MAKE_B = (makeB->ready->used->MAKE_B).
||MAKERS = (MAKE_A || MAKE_B).

ASSEMBLE = (ready->assemble->used->ASSEMBLE).
||FACTORY = (MAKERS || ASSEMBLE).
```

#### Composizione Parallela di istanze multiple
> Data la definizione di un processo, spesso si vuole usare più di una copia di quel processo in un modello di sistema.

Data la definizione di ***switch***
- `SWITCH = (on -> off -> SWITCH).`

>[!fail]  La composizione è indistinguibile da un singolo switch, dato che due switch si sincronizzano sulle proprie azioni condivise on e off.

##### Process Labelling
> [!tldr] Idea
> Il process labelling $a:P$ è un costrutto con cui si ***assegna un prefisso*** ad ogni *action label* di un alfabeto $P$ on la label $a$.

> Data la definizione di switch:

$\mid\mid\text{TWO\_SWITCH} = (a:\text{SWITCH} \mid \mid b:\text{SWITCH}).$

I due alfabeti dei processi sono ora ***disgiunti***:
- $\{  a.on, a.off \}$ e $\{ b.on, b.off \}$

Processi composti possono essere parametrizzati usando il costrutto `forall`.
- `forall [i:1..N] P(i)`

La composizione parallela *equivalente* è:
`(P(1)||…||P(N))`

##### Set of prefix labels
> [!abstract] Idea
> Il labelling può essere fatto usando un insieme di ***prefix labels***: $\{ a_{1},a_{2},\dots,a_{x} \}::P$

Rimpiazza *ogni action label* $n$ nell'alfabeto di $P$ con le label $\{ a_{1}.n, \dots, a_{x}.n \}$
- Ogni azione $(n\to Q)$ nella definizione di $P$ è **rimpiazzata** con una delle transizioni: $(\{ a_{1}.n, \dots, a_{x}.n \}\to Q)$

Utile quando abbiamo multipli processi che interagiscono con uno stesso processo.

> Esempio

Spesso utilizzato per modellare un meccanismo di [[../../Sistemi Operativi/Teoria/13 - Semafori|Lock]] in una risorsa.
- Una singola risorsa che permette due azioni una $a.\text{aquire}$ e $b.\text{aquire}$
```
RESOURCE = (acquire->release->RESOURCE).
USER = (acquire->use->release->USER).
||RESOURCE_SHARE = (a:USER || b:USER || {a,b}::RESOURCE).
```

#### Relabelling
> [!tldr] Idea
> Ciascun processo può essere progettato con il ***proprio alfabeto***.

Quando si creano composite processes unendo processi indipendenti, bisogna creare una ***corrispondenza tra le azioni di sincronizzazione***.

Funzioni di *relabelling* sono applicate ai processi per ***cambiare i nomi delle action labels***:
- $\{ newLabel_{1}/oldLabel_{1}, \dots, newLabel_{n} / oldLabel_{n} \}$

```
CLIENT = (call->wait->continue->CLIENT).
SERVER = (request->service->reply->SERVER).
||CLIENT_SERVER = (CLIENT || SERVER) /{call/request, reply/wait}
```

#### Hiding and Silent Action
> [!tldr] Idea
> Può essere utile impostare alcune azioni di un processo come "***Private***", che *non possono essere usate per interagire* con altri processi.

In `FSP` questo può essere fatto attraverso l'uso dell'***hiding operator*** : $\backslash \{ a_{1}\dots a_{x} \}$
- Quando applicate ad un processo $P$ l'hiding operator **rimuove** i nomi delle azioni dall'alfabeto di $P$ e rende queste azioni "*silenziose*" (esecuzione non visibile dall'esterno).

Le **azioni silenziose** sono rappresentate dal simbolo $\tau$.

Operatore duale ( #todo ricerca operativa), ***interface operator*** $@ \{ a_{1} \dots a_{x} \}$
- Quando applicato al processo $P$ *nasconde* tutte le azioni nel'alfabeto $P$ *non **indicate*** nell'insieme.

#### Minimizzazione
> [!summary] Equivalenza
> Due sistemi sono ***equivalenti*** se le tracce dei due sistemi sono *uguali*.

Per capire il comportamento di un processo che sta per essere composto con altri processi, le *azioni nascoste* possono essere **rimosse**, minimizzando il processo.
- Il comportamento osservabile come l'insieme dei percorsi possibili è preservato.

Nascondere è essenziale per la *riduzione della complessità* di un sistema molto grande, con l'obbiettivo di analisi.

### Check delle proprietà del sistema
> Per controllare le proprietà di un sistema in `FSP` ci sono due possibili approcci.

#### Safety
> [!abstract] [[../Analizzare i Sistemi#Proprietà dei sistemi concorrenti|Safety]]
> Le ***safety property*** sono specificate tramite *property processes*.

Sintatticamente sono semplicemente processi `FSP` con la keywork `property`.

```
property POLITE = (knock->enter->POLITE).
```

Azioni che ***non*** sono parte del comportamento permesso dalla *safety property* sono transizioni che portano allo ***stato di errore***.


> [!cite] Definizione
> Una ***safety property*** $P$ definisce un *processo deterministico* che asserisce che una qualsiasi *trace* che include azioni nell'alfabeto di $P$, è accettato da $P$.

Se $P$ è composto con $S$ allora le tracce delle azioni che sono nell'alfabeto di $S$ e nell'alfabeto di $P$, devono essere tracce valide anche di $P$ altrimenti un errore è raggiungibile.

#### Liveness
> [!abstract] [[../Analizzare i Sistemi#Proprietà dei sistemi concorrenti|Safety]]
> Le ***liveness properties*** sono specificate tramite le *progress properties*.

Una progress property asserisce che qualsiasi sia lo stato di un sistema, è sempre assicurato che una azione specifica verrà prima o poi eseguita.

`progress P = {a1,a2..an}.`

La proprietà ***afferma*** che in una *esecuzione infinita* del sistema target in un qualsiasi stage dell'esecuzione ognuna delle azioni nel processo verranno eseguite.


> [!example] Esempio

```example
COIN = (toss->heads->COIN | toss->tails->COIN).
progress HEADS = {heads}
progress TAILS = {tails}
```

Il sistema `COIN` soddisfa le proprietà
- Un sistema con una ***moneta truccata*** (solo testa) non lo soddisfa.

### Applicare gli LTL
> Per applicare la [[../Analizzare i Sistemi#Linear Temporal Logic|linear temporal logic]] bisogna avere un modo di descrivere gli stati astratti coinvolti negli scenari, ottenuti dalle **tracce di azioni**.

A questo scopo si introducono i ***fluent***.
#### Fluent
> [!abstract] Definizione
> Un **fluent** è una condizione logica che può ***cambiare nel tempo***.

Sintassi:

```
fluent FL = <{s1,...,sn},{e1,...,en}> initially B
```

- $FL$ è inizialmente **vero** se l'espressione $B$ è vera, **falso** se $B$ è falsa.
- $FL$ diventa **vero** quando avviene una qualunque delle **azioni iniziatrici** $\{s_1,\dots,s_n\}$.
- $FL$ diventa **falso** quando avviene una qualunque delle **azioni terminatrici** $\{e_1,\dots,e_n\}$.

> [!example] Esempio: interruttore della luce

```
const False = 0
const True = 1
fluent LIGHT = <{on}, {off, power_cut}> initially False
```

> Il fluent cattura lo stato della luce: quando la luce è accesa `LIGHT` è vero, quando è spenta `LIGHT` è falso.

> [!danger] Rilevazione, non prevenzione
> Questa sintassi serve a **rilevare** i casi di errore, **non a prevenirli**.

##### Action fluent
> [!abstract] Definizione
> Gli **action fluent** sono fluent definiti direttamente a partire dalle azioni e rappresentano la condizione: *"l'azione è appena stata eseguita"*.

##### Espressioni di fluent
I fluent si possono combinare con i normali operatori logici.

> [!help] Operatori logici

| Operatore         | Significato                                                     |
| ----------------- | --------------------------------------------------------------- |
| $\&\&$            | congiunzione (and)                                              |
| $\mid\mid$        | disgiunzione (or)                                               |
| $!$               | negazione (not)                                                 |
| $\to$             | implicazione: $(A\to B) \equiv (!A\mid \mid B)$                 |
| $\leftrightarrow$ | equivalenza: $(A\leftrightarrow B) \equiv (A\to B)\&\&(B\to A)$ |

##### Fluent con gli operatori temporali
> [!tldr] Idea
> I *fluent* permettono di esprimere proprietà sullo **stato astratto** del sistema in un dato istante. Tale stato dipende dalla **traccia di azioni** avvenute fino a quel momento.

Sintassi:

- *always* ($\Box$): `[] F`
- *eventually* ($\Diamond$): `<> F`
#### Altri operatori della logica temporale lineare sui fluent

##### Until ($\text{U}$)
> [!abstract] Definizione
> La formula $p \text{ U } q$ è vera **se e solo se** $q$ è vera nell'istante corrente, oppure $q$ diventa vera in un istante futuro e $p$ è vera **fino a** quell'istante.

>[!done] In breve
- **Finché $q$ è falso, $p$ deve essere vero** (e $q$ deve prima o poi diventare vero).

> Esempio: precondizione
- Non si può entrare finché non busso alla porta.

##### Weak Until ($\text{W}$)
> [!abstract] Definizione
> La formula $p \text{ W } q$ è vera **se e solo se** $p$ è vera **indefinitamente**, oppure vale $p \text{ U } q$.

> [!tip] Differenza tra U e W
> - $p \text{ U } q$ **richiede** che $q$ avvenga prima o poi.
> - $p \text{ W } q$ **non lo richiede**: se $q$ non avviene mai, basta che $p$ resti sempre vera.
>
> Per questo l'esempio della porta è più preciso con $\text{W}$: se nessuno entra mai, la proprietà "non si entra finché non si bussa" deve comunque essere rispettata.