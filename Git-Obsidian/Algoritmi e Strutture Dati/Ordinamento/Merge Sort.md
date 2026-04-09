## Pseudocodice
---
```pseudo
	\begin{algorithm}
	\caption{Merge Sort}
	\begin{algorithmic}
\Procedure{MergeSort}{$ A[],p,r $}
\If{$ p<r  $}
  \State $ q=(p+r)/2 $
  \State \Call{MergeSort}{$A[],p,q$}
  \State \Call{MergeSort}{$A[],q+1,r$}
  \State \Call{Merge}{$A[],p,q,r$}
 \EndIf
 \EndProcedure



 \Procedure{Merge}{$ A[],p,q,r $}
\State $ i=p,j=q+1,k=0 $
\While{$i \leq q \text{ and } j \leq r$}
\If{$ A[i]<A[j]  $}
  \State $ B[k]=A[i] $
  \State $ i=i+1 $
  \Else 
 \State $ B[k]=A[j] $
 \State $ j=j+1 $
 \EndIf
 \State $ k=k+1 $
\EndWhile
\While{$i \leq q$}
  \State $ B[k]=A[i] $
  \State $ i=i+1 $
  \State $ k=k+1 $
\EndWhile
\While{$j \leq r$}
  \State $ B[k]=A[j] $
  \State $ i=i+1 $
  \State $ k=k+1 $
\EndWhile

\For{$ k=p\to r $}
  \State $ A[k]=B[k-p] $
 \EndFor
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```
![[youtube.com)](https://www.youtube.com/watch?v=ZRPoEKHXTJg|Merge Sort (youtube.com)]]
## Concetto
---
> Algoritmo di ordinamento basato sulla tecnica [[../Divide et Impera]]

Ideato da *John Von Neumann* nel 1945
- Implementato come algoritmo di *ordinamento standard* nelle librerie di alcuni linguaggi
- Algoritmo di tipo [[../../Programmazione/Funzioni/Recursive Functions|ricorsivo]]

>[!info] Dividi

Se $S$ contiene almeno due elementi (un solo elemento è banalmente già ordinato)
- Rimuovi tutti gli elementi da $S$ e inseriscili in due vettori $S_{1},S_{2}$
- Ognuno dei quali contiene circa la metà degli elementi di $S$

>[!tip] Risolvi

Ordina gli elementi in $S_{1},S_{2}$ utilizzando il metodo `MergeSort` (ricorsione)
- Considerando l'*Istanza Banale* una istanza di uno o due elementi

>[!done] Combina

Metti insieme gli elementi di $S_{1},S_{2}$ ottenendo un unico vettore $S$ *ordinato*

![[attachements/MergeSort.png]]

### Operazione di Merge
> L'operazione di Merge è quella che effettivamente va a ordinare i singoli elementi

Si controllano i numeri coppia a coppia nei due sottovettori
- Il più piccolo fra i due viene "*spostato*" dal **sottovettore**, all'**vettore ordinato**
- Continua fino a che i due sottovettori sono svuotati

## Costo Computazionale
---
$$
T(n)=2T(n/2)+\Theta(n) = \Theta(nlog(n))
$$
La *complessità* del **Merge Sort** non dipende dalla *configurazione iniziale* dell'array
- Di conseguenza la complessità è la stessa nei casi *ottimo*, *pessimo* e *medio*

> *Caso speciale dell'[[../../Programmazione/Funzioni/Recursive Functions#Albero della Ricorsione|albero della ricorsione]]*

![[attachements/MergeSortProof.png]]