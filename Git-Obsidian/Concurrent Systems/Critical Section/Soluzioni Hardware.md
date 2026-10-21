## Soluzione: Meccanismi
---
> L'[[Soluzioni Software#Algoritmo di Dekker|algoritmo di Dekker]] funziona in una qualsiasi architettura che fornisce le istruzioni di load e store come atomiche.

> [!tldr] Idea
> I problemi della sezione critica e mutua esclusione possono essere semplificati usando ***istruzioni atomiche più complesse***.

> Alcuni esempi di istruzioni sono le seguenti:
- ***Test and set***
- ***Exchange***
- ***Fetch and add***
- ***Compare and Swap***
- etc...
### Test e Set
>[!abstract] Istruzioni Speciali
>Sono istruzioni che realizzano due azioni in modo ***atomico***
>>[!example] Come
>>- Lettura e Scrittura
>>- Test e Scrittura
>
>`TS(x,y):= < y = x; x = 1 >`
>>[!done] A parole
>>Assegna in `y` il valore precedente di `x`, e successivamente assegna `1` ad `x`

###### Esempio di Utilizzo di Test&Set
```pseudo
	\begin{algorithm}
	\begin{algorithmic}
	\State $ \text{shared }lock\  =0 $
	\State $\text{Cobegin } P \ \ Q \text{ Coend}$
	\Procedure{P}{$  $}
\State $ \text{int }vp  $
\While{$true$}
\Repeat
\State \Call{TS}{$ lock,vp $}
\Until{$vp$}
 \State $ \text{Critical Section} $
 \State $ lock = 0 $
 \State $  \text{Non-Critical Section} $
\EndWhile
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```

```pseudo
	\begin{algorithm}
	\begin{algorithmic}
\Procedure{Q}{$  $}
\State $ \text{int }vq  $
\While{$true$}
\Repeat
\State \Call{TS}{$ lock,vq $}
\Until{$vq$}
 \State $ \text{Critical Section} $
 \State $ lock = 0 $
 \State $  \text{Non-Critical Section} $
\EndWhile
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```

>[!done] Mutua Esclusione
>Entra solo chi riesce a settare per primo il lock

>[!done] No deadlock
>Il primo che esegue `TS` entra senza problemi

>[!done] No Delay non necessari
>Un processo fuori dalla ***critical section*** non blocca gli altri

> [!warning] Attenzione
> Con più di 2 processi non c'è la garanzia dell'***assenza di starvation***.

### Locks
> [!todo] Lock
> Sfruttando queste istruzioni atomiche possiamo realizzare in maniera semplice un meccanismo basilare di ***lock***.

Il lock è una facile soluzione per il problema della sezione critica, *protegge delle sezioni critiche di codice*.

> Due sezioni:
- *Acquisire* il ***lock***
- *Rilasciare* il ***lock***

[[Meccanismi per la Coordinazione|Ulteriori meccanismi e astrazioni sono]]:
- Semafori
- Monitor