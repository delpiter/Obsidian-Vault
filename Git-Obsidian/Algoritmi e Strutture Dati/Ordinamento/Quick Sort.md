## Pseudocodice
---
```pseudo
	\begin{algorithm}
	\caption{Quick Sort}
	\begin{algorithmic}
	\Procedure{QuickSort}{$ A[],p,r $}
	\If{$ p<r  $}
	\State \Comment{Partition The subarray around the Pivot}
	  \State $q=$\Call{Partition}{$A[],p,r$}
	  \State \Call{QuickSort}{$A[],p,q-1$}
	  \State \Call{QuickSort}{$A[],q+1,r$}
 \EndIf

 \EndProcedure
 \State \Comment{}

 \Procedure{Partition}{$ A[],p,r $}
 \State $ x = A[r] $
	\Comment{The pivot}
 \State $ i=p-1 $
 
 \For{$ j=p \to r-1 $}
 \If{$ A[j]\leq x  $} 
 \Comment{Does this element belong on the low side?}
 \State $ i=i+1 $
 \State $ \text{exchange }A[i]\text{ with }A[j] $
 \EndIf
 \EndFor
 \State $ \text{exchange }A[i+1] \text{ with }A[r] $
 \Comment{The Pivot goes to the right of the low side}
 \Return $ i+1 $
 \Comment{Return the index of the pivot}
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```
![[LR pointers) (youtube.com)](https://www.youtube.com/watch?v=8hEyhs3OV1w|Quick Sort (LR pointers) (youtube.com)]]

## Concetto
---
>Algoritmo di ordinamento basato sulla tecnica [[../Divide et Impera]]

Ideato da *Tony Hoare* nel 1960, come studente presso la *Moscow State University*
- Implementato come *algoritmo di ordinamento standard* nella libreria `C` di Unix (**`qsort()`**)
A differenza del [[Merge Sort]] il *quick sort* esegue comparazioni prima della ricorsione.

### Partition
La funzione di *partition* è la parte cruciale dell'algoritmo
Per trovare le partizioni:
- Imposto $i$ come indice del primo elemento
- Imposto $j$ come indice dell'ultimo elemento

1. Sposto $i$ a destra (`i++`) finché non trovo un elemento che è $\geq$ del *pivot*
2. Sposto $j$ a sinistra (`j--`) finché non trovo un elemento che è $<$ del *pivot*
3. Inverto gli elementi in posizione $i$ e $j$
4. Ripeto il processo fino a quando `j<i`

Quando noto che `j<i` ho separato con successo il vettore in due sottovettori 
- Il sottovettore di sinistra contenente solo valori $\leq$ *pivot*
- Il sottovettore di destra contenente solo valori $>$ *pivot*

![[attachements/QuickSortExample.png]]

## Costo Computazionale
---
### Caso Ottimo
>[!done] Partizioni Bilanciate

Come *pivot* viene scelto sempre l'elemento mediano
- Di conseguenza la complessità computazionale sarà uguale a quella del [[Merge Sort]]
$$
T(n)=2T(n/2) +\Theta(n)
$$
- Quindi $T(n)=\Theta(nlog(n))$

### Caso Pessimo
>[!danger] Partizioni Sbilanciate

Come *pivot* viene scelto sempre il valore *min/max* del vettore
- Ogni divisione rimuove solamente un elemento

$$
T(n)=T(n-1)+\Theta(n)
$$
- Quindi $T(n) =\Theta(n^2)$

### Caso Medio
>[!question] Partizioni Sproporzionate

Analizzando, noteremo che il caso medio dell'algoritmo *quick sort* è molto più vicino al caso ottimo rispetto al caso pessimo.

>Supponiamo che ogni partizione produce una separazione proporzionale $9-to-1$
>Ad una prima occhiata sembra abbastanza sbilanciato

Otteniamo la seguente equazione ricorsiva
$$
T(n) = T(n/10)+T(9n/10)+\Theta(n)
$$
![[attachements/QuickSortProof.png]]
*Albero della ricorsione del quick sort*

Possiamo notare come la parte sinistra dell'albero si concluda con una altezza di solo:
- $log_{10}n$
La ricorsione, però si conclude solo quando il lato destro dell'albero ha raggiunto la fine
$$
\begin{array}
\ \frac{n}{\left( \frac{10}{9} \right)^k}=1 \implies n=\left( \frac{10}{9} \right)^k \\
log_{\frac{10}{9}}n=k
\end{array}
$$
- La ricorsione quindi si conclude al livello $log_{\frac{10}{9}}n$ che in termini di costo computazionale è $\Theta(log(n))$

 Di conseguenza, nel caso medio, il *quick sort* ha un costo computazionale di $\Theta(n log(n))$

## Distribuzione dell'input
---
Abbiamo assunto implicitamente che tutte le sequenze di numeri da ordinare fossero equiparabili. 
- Se ciò non fosse vero potremmo avere dei costi computazionali diversi per input diversi

>[!done] Soluzione

### RQS
> Il *randomized quick sort* usa una versione randomizzata della procedura ***partition***

Ad ogni chiamata il *pivot* viene scelto in maniera casuale
- Un algoritmo randomizzato non ha un input pessimo, ma ha una sequenza di scelte pessime di *pivot*

### Conclusione
La probabilità del caso pessimo del *quick sort* è incredibilmente ridicola
- Possiamo dire quindi che l'efficienza del *quick sort* è simile a quella del [[Merge Sort]]
