## Soluzione: Algoritmi
---
> Analizziamo inizialmente il problema considerando $2$ processi $P$ e $Q$ che condividono alcune variabili globali.

I protocolli potrebbero richiedere variabili locali o globali per il funzionamento.
- Assumiamo che le variabili usate nelle sezioni critiche e non critiche ***NON*** sono usate nei protocolli
### Primo tentativo
> Definiamo una variabile globale `turn`

Definiamo i due processi:
![[attachements/FirstAttempt.png]]

L'istruzione `await turn=1` è una notazione per un'istruzione che aspetta che la condizione `turn=1` sia vera
- Potrebbe essere implementata con un ***loop busy-waiting*** che non fa nulla fino a che la condizione è vera.

#### Controllare la correttezza
> [!hint] Osservazione
> Per dimostrare la correttezza della soluzione costruiamo il diagramma degli stati del programma concorrente

Sono da controllare solo l'insieme degli stati raggiungibili e le transizioni tra di essi.
- Gli stati sono triple $<p_{i},q_{j},turn>$
- La proprietà di correttezza della mutua esclusione è rispettate se l'insieme di tutti gli stati non contiene uno stato nella forma: $<p_{3}, q_{3}, \_>$

Definiamo le proprietà in [[Analizzare i Sistemi#Linear Temporal Logic|LTL]]
- $\Box \neg (p_{3} \wedge q_{3})$ mutua esclusione

Per controllare la correttezza, dobbiamo controllare le tre proprietà

> [!done] Mutua esclusione
> Non ci sono scenari che includono stati del tipo $<p_{3}, q_{3}, \_>$

> [!done] Assenza di deadlock
> Se un processo vuole entrare nella sezione critica, uno prima o poi ci riuscirà

> [!fail] Assenza di starvation
> Uno dei due processi potrebbe avere un loop infinito ***fuori dalla sezione critica***.

Questo caso è *ammesso secondo le regole*, ma causerebbe una ***starvation***
- un processo è bloccato nel loop infinito e il secondo processo attende che il primo entri nella sezione critica, esca e gli passi il turno.

### Secondo tentativo
> [!tldr] Idea
> Introduciamo delle variabili condivise che indicano quando un processo è nella sezione critica.

![[attachements/SecondAttempt.png]]

#### Correttezza
> Costruendo il diagramma degli stati:

Si può notare che la mutua esclusione non è rispettata.
- Esiste uno stato raggiungibile $<p_{4},q_{4}, true, true>$

> [!important] Osservazione
> Il problema deriva dalla ***non-atomicità*** del pre e post protocollo.

### Terzo Tentativo
> [!tldr] Idea
> Il problema del secondo tentativo si risolve considerando l'istruzione `await` come *parte della sezione critica*, ***muovendo l'assegnazione*** prima di `await`.

![[attachements/ThirdAttempt.png]]

#### Correttezza
> Risolto il problema della mutua esclusione


> [!fail] Deadlock
> Viene però introdotto un ***possibile deadlock***.

Deve essere anche rispettata la progress property (*no starvation*).
- $\Box((p_{3}\to \diamond p_{4})\wedge (q_{3} \to \diamond q_{4}))$

### Quarto tentativo
> [!tldr] Idea
> Possiamo risolvere il problema richiedendo ai processi di ***rinunciare alla sua intenzione di entrare nella sezione critica***, se scopre che sta *contendendo* con l'altro processo.

![[attachements/FourthAttempt.png]]

### Algoritmi Finali
#### Algoritmo di Dekker
```pseudo
	\begin{algorithm}
	\caption{Dekker's Algorithm}
	\begin{algorithmic}
	\State $ \text{shared int }turn\  =P $
	\State $ \text{shared boolean }needp\  =false $
	\State $ \text{shared boolean }needq\  =false $
	\State $\text{Cobegin } P \ \ Q \text{ Coend}$

	\Procedure{P}{}
	\While{true}
	\State $ needp = true $
	\While{needq}
	\If{$ turn == Q  $}
  \State $ needp= false $
  \While{turn == Q}
  \State $\text{/* Do nothing */}$
  \EndWhile
  \State $ needp=true $
 \EndIf
 \State $ \text{Critical Section} $
 \State $ needp = false $
 \State $ turn = Q $
 \State $  \text{Non-Critical Section} $
    \EndWhile
    \EndWhile
    \EndProcedure
	
	\end{algorithmic}
	\end{algorithm}
```

```pseudo
	\begin{algorithm}
	\begin{algorithmic}
\Procedure{Q}{}
	\While{true}
	\State $ needq = true $
	\While{needp}
	\If{$ turn == P  $}
  \State $ needq= false $
  \While{turn == P}
  \State $\text{/* Do nothing */}$
  \EndWhile
  \State $ needq=true $
 \EndIf
 \State $ \text{Critical Section} $
 \State $ needq = false $
 \State $ turn = P $
 \State $  \text{Non-Critical Section} $
    \EndWhile
    \EndWhile
    \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```
##### Dimostrazioni
###### Mutua Esclusione
>[!hint] [[9 - Condivisione di Risorse#Mutua Esclusione|Mutua Esclusione]]
>Assumiamo per ***assurdo*** che $P$ e $Q$ siano in una [[10 - Sezioni Critiche|sezione critica]] contemporaneamente

>Poiché gli accessi in memoria sono esclusivi
- Per entrare devono almeno aggiornare/valutare entrambe le variabili: $needp$ e $needq$

Uno dei due entra per *primo*
- Supponiamo sia $Q$

>$needq$ sarà `true` fino a quando $Q$ non uscirà dal ciclo

Poiché $P$ entra nella ***critical section*** mentre $Q$ è nella ***critical section*** significa che esiste un istante temporale in cui $needq=false$ e $Q$ è in una ***critical section***


>[!danger] Assurdo
##### Assenza di Deadlock
>[!info] [[9 - Condivisione di Risorse#Deadlock|Deadlock]]
>Assumiamo per ***assurdo*** che né $P$ né $Q$ possano entrare in una ***critical section***

>$P$ e $Q$ devono essere bloccati nel primo `while`

Esiste un istante $t$ dopo di che $needp$ e $needq$ sono sempre `true`
- Supponiamo che all'istante $t$, $turn = Q$
- L'unica modifica a $turn$ può avvenire solo quando $Q$ entra nella ***critical section***
- Dopo $t$, $turn$ resterà sempre uguale a $Q$
- $P$ entra nel primo ciclo e mette $needp=false$

>[!danger] Assurdo

##### Assenza di Ritardi non Necessari
>[!abstract] Dimostrazione di assenza di Ritardi non necessari
>Se $Q$ sta eseguendo codice non critico, allora $needq=false$
><u>Allora</u>
>$P$ può entrare nella ***critical section***

##### Assenza di Starvation
>[!help] [[9 - Condivisione di Risorse#Starvation|Starvation]]
>Se $Q$ richiede di accedere alla ***critical section***
>- $needq=true$

>Se $P$ sta eseguendo codice non critico
- $Q$ entra

>Se $P$ sta eseguendo il resto del codice
- Prima o poi ne uscirà e metterà il turno a $Q$
- $Q$ potrà quindi entrare

### Algoritmo di Peterson
```pseudo
	\begin{algorithm}
	\caption{Peterson's Algorithm}
	\begin{algorithmic}
	\State $ \text{shared int }turn$
	\State $ \text{shared boolean }needp\  =false $
	\State $ \text{shared boolean }needq\  =false $
	\State $\text{Cobegin } P \ \ Q \text{ Coend}$

	\Procedure{P}{}
	\While{true}
	\State $ needp = true $
	\State $ turn =Q $
	\While{$needq \text{ AND } turn != P$}
	  \State $\text{/* Do nothing */}$
	\EndWhile
 \State $ \text{Critical Section} $
 \State $ needp = false $
 \State $  \text{Non-Critical Section} $
    \EndWhile
    \EndProcedure
	
	\end{algorithmic}
	\end{algorithm}
```

```pseudo
	\begin{algorithm}
	\begin{algorithmic}
	\Procedure{Q}{}
	\While{true}
	\State $ needq = true $
	\State $ turn =P $
	\While{$needp \text{ AND } turn != Q$}
	  \State $\text{/* Do nothing */}$
	\EndWhile
 \State $ \text{Critical Section} $
 \State $ needq = false $
 \State $  \text{Non-Critical Section} $
    \EndWhile
    \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```

>[!definizione] Facile
>L'algoritmo di *Peterson* è più semplice e lineare di quello di *Dekker*
>È inoltre più facilmente generalizzabile al caso di ***processi multipli***


>[[9 - Condivisione di Risorse#Azioni Atomiche|Istruzioni atomiche]] le operazioni di ***load*** e ***store***

### Bakery Algorithm
> [!info] 
> Soluzione alternativa al problema della sezione critica per $N$ processi che tiene conto dell'*ordine di arrivo* del processo, tramite l'introduzione del concetto di ***ticket***.

![[attachements/BakeryAlgorithm.png]]