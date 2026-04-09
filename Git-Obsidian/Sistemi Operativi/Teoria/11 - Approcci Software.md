>L'implementazione di algoritmi per risolvere la concorrenza sono [[10 - Sezioni Critiche#Approcci|approcci software]]

## Algoritmo di Dekker
---
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
## Dimostrazioni
---
### Mutua Esclusione
>[[9 - Condivisione di Risorse#Mutua Esclusione|Mutua Esclusione]]
>Assumiamo per ***assurdo*** che $P$ e $Q$ siano in una [[10 - Sezioni Critiche|sezione critica]] contemporaneamente

>Poiché gli accessi in memoria sono esclusivi
- Per entrare devono almeno aggiornare/valutare entrambe le variabili: $needp$ e $needq$

Uno dei due entra per *primo*
- Supponiamo sia $Q$

>$needq$ sarà `true` fino a quando $Q$ non uscirà dal ciclo

Poiché $P$ entra nella ***critical section*** mentre $Q$ è nella ***critical section*** significa che esiste un istante temporale in cui $needq=false$ e $Q$ è in una ***critical section***


>[!danger] Assurdo
### Assenza di Deadlock
>[[9 - Condivisione di Risorse#Deadlock|Deadlock]]
>Assumiamo per ***assurdo*** che né $P$ né $Q$ possano entrare in una ***critical section***

>$P$ e $Q$ devono essere bloccati nel primo `while`

Esiste un istante $t$ dopo di che $needp$ e $needq$ sono sempre `true`
- Supponiamo che all'istante $t$, $turn = Q$
- L'unica modifica a $turn$ può avvenire solo quando $Q$ entra nella ***critical section***
- Dopo $t$, $turn$ resterà sempre uguale a $Q$
- $P$ entra nel primo ciclo e mette $needp=false$

>[!danger] Assurdo

### Assenza di Ritardi non Necessari
>[!abstract] Dimostrazione di assenza di Ritardi non necessari
>Se $Q$ sta eseguendo codice non critico, allora $needq=false$
><u>Allora</u>
>$P$ può entrare nella ***critical section***

### Assenza di Starvation
>[[9 - Condivisione di Risorse#Starvation|Starvation]]
>Se $Q$ richiede di accedere alla ***critical section***
>- $needq=true$

>Se $P$ sta eseguendo codice non critico
- $Q$ entra

>Se $P$ sta eseguendo il resto del codice
- Prima o poi ne uscirà e metterà il turno a $Q$
- $Q$ potrà quindi entrare

## Algoritmo di Peterson
---
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

