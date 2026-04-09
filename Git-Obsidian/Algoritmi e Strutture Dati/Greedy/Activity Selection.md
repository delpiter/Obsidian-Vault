## Selezione di Attività
---
>*Esempio di Problema risolvibile con [[Gli Algoritmi Greedy|algoritmi greedy]]*

>[!info] Problema
>Selezionare un sottoinsieme di attività ***mutualmente compatibili***
>>[!caution] Input
>>Un insieme $S=(1,\dots,n)$ di attività.
>>Ogni attività ha un tempo di inizio $s_{i}$ e un tempo di fine $f_{i}$
>>Per ogni attività vale: $f_{i}>s_{i}$
>
>>[!done] Output
>>Un sottoinsieme $S'$ ***massimale di attività compatibili***:
>>- Se $i$ e $j$ appartengono ad $S'$ allora $s_{i}\geq f_{j}$ oppure $s_{j}\geq f_{i}$
>>- La cardinalità di $S'$ è ***massima***


![[attachements/Activity Selection Table.png]]
>*Esempio di input*

![[attachements/Activity Selection Table Solution.png]]
>*Esempio di output*
### Pseudocodice
```pseudo
	\begin{algorithm}
	\caption{Greedy Activity Selection}
	\begin{algorithmic}
\Procedure{Greedy-Activity-Selector}{$ s,f,n $}
\State $ A=\{a_{1}\} $
\State $ k=1 $
\For{$ m=2 \to n $}
  \If{$ s[m] \geq f[k] $}
  \Comment{If the activity is compatible}
  \State $ A = A \cup \{a_{m}\} $
  \Comment{Add the activity}
  \State $ k=m $
  \Comment{Update the compatibility condition}
 \EndIf
 \EndFor
 \Return $ A $
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```
### Dimostrazione di Correttezza
>*Assumiamo che le attività siano ordinate per* ***tempi di fine crescenti***

>[!abstract] Voglio mostrare che *esiste una soluzione ottima* $S'$ che contiene l'attività 1 (***scelta greedy iniziale***)

Siano:
- $S'=\{ 1,\dots,a_{n} \}$ costruita con l'***algoritmo greedy***
- $S''=\{ a_{k},\dots,a_{j} \}, a_{k}\neq 1$
Due ***soluzioni ottimali***

Supponiamo per assurdo che la soluzione $S''$ sia migliore di $S'$

Posso sostituire $a_{k}$ con $1$ e ottenere ***un'altra soluzione valida***
$$
T=S''-\{ a_{k} \}\cup\{ 1 \}
$$
- $T$ è la migliore soluzione possibile e contiene l'attività $1$

Adesso eliminiamo da $S$ tutte le attività incompatibili con $1$ e ***ripetiamo la dimostrazione***