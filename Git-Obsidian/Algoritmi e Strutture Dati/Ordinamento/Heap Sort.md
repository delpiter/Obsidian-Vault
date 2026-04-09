## Pseudocodice
---
```pseudo
	\begin{algorithm}
	\caption{Heap Sort}
	\begin{algorithmic}
\Procedure{HeapSort}{$ A[] $}
\State \Call{BuildHeap}{$A$}

\For{$ i = \text{length}(A) \to 2 $}
  \State \Call{Exchange}{A[1],A[i]}
  \State $ \text{Heap-Size}(A) = \text{Heap-Size}(A)-1 $
  \State \Call{Heapify}{$A,1$}
 \EndFor
\EndProcedure
	\end{algorithmic}
	\end{algorithm}
```
![[../Strutture Dati/Heap#Pseudocodice Heapify]]
![[../Strutture Dati/Heap#Pseudocodice Build Heap]]

![[youtube.com)](https://www.youtube.com/watch?v=_bkow6IykGM|Heap Sort (youtube.com)]]

## Concetto
---
>[!tldr] L'idea
>Per ordinare in senso ***cresente***:
>Prima Parte
>- Si trasforma l'*array* in input in una [[../Strutture Dati/Heap|max-heap]] (una *heap* con il valore più ***grande alla radice***)
>Seconda Parte
>- Si scambia il **dato** nella *radice* con il **dato** dell'*ultimo nodo*
>- Si *esclude* l'ultimo nodo dalla **heap**
>- Si ricostruisce la ***heap***

![[attachements/heap-removebg-preview.png]]

## Complessità
---
>[!danger] Caso Pessimo

La **complessità** **computazionale** dell'*heap-sort* nel caso pessimo:
- $\text{BuildHeap}$ ripete $O(n)$ volte il ciclo interno
- Si fanno $n-1$ chiamate a $\text{Heapify}$
- Ogni chiamata costa $O(log(n))$

>[!done] Quindi $\text{Heapsort}$ è$$O(n\cdot log(n))$$
