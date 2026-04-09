>[!info] Definizione
>Un *Heap* è un [[Grafi/Alberi/Gli Alberi Binari#Alberi Binari Quasi Completi|albero binario quasi completo]]
>Quasi, significa che *possono mancare* alcune foglie *consecutive* a partire dall'ultima foglia di destra
>Per ogni nodo deve valere:
>$$value(i)\leq value(parent(i))$$
>>[!tip] Nota 1
>>Il massimo si trova nella radice
>
>>[!tip] Nota 2
>>Non c'è ***nessuna relazione*** tra il *valore di un nodo* e quello di un **suo fratello**

### Heap in un Vettore
>È possibile immaginarsi un heap come una struttura: ***vettore***

Considerando la radice dell'albero come la posizione 1
- Per ogni nodo in posizione $i$
	- $\text{left-child}(i) =$ posizione $2i$
	- $\text{right-child}(i) =$ posizione $2i+1$
- $\text{parent}(i)=\lfloor \frac{i}{2}\rfloor$
### Heapify
>[!info] Definizione
>***Heapify*** è il processo di creazione di una struttura dati heap partendo da due strutture *heap* e aggiungendo un elemento iniziale

1. Provo ad inserirlo nella *posizione* più *alta*
2. Se dopo questo inserimento la struttura **non** è più un ***heap***
	1. **Scambio** il valore appena inserito con il figlio con il valore più *alto*
3. ***Itero*** il procedimento fino a quando non ottengo nuovamente una struttura ***heap***

#### Pseudocodice Heapify

```pseudo
	\begin{algorithm}
	\caption{Heapify}
	\begin{algorithmic}
	\Procedure{Heapify}{$ A[],i $}
\State $l =$\Call{left}{i}
\State $r =$\Call{right}{i}
\If{$ l\leq  $ \Call{HeapSize}{A}$\text{ And } A[l]>A[i]$}
\State $ largest=l $
\Else 
 \State $ largest = i $
 \EndIf
 \If{$ r\leq  $ \Call{HeapSize}{A}$\text{ And } A[r]>A[largest]$}
\State $ largest=r $
 \EndIf
 \If{$ largest \neq i  $}
  \State \Call{Swap}{A[i],A[largest]}
  \State \Call{Heapify}{A,largest}
 \EndIf
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```

#### Costo Computazionale

>[!danger] Caso Pessimo

Nel caso pessimo il nodo si sposta fino ad *arrivare alle foglie*
- Di conseguenza esegue al massimo $height(i)$ aggiustamenti dove $height(i)=O(log(n))$


### Build Heap
>[!info] Idea
>Si trasforma in un *heap* un albero binario con radice in posizione $i$
>Si assume che gli ***alberi binari*** con radice in $2i$ e $2i+1$ siano già delle strutture *heap*

Si può assumere che **metà** del vettore è ***già un heap*** corretto (da *destra* a *sinistra*)
- Poiché elementi singoli possono essere considerati come *heap*
- La metà dei nodi in un *albero binario quasi completo* sono **foglie**

#### Pseudocodice Build Heap
```pseudo
	\begin{algorithm}
	\caption{Build Heap}
	\begin{algorithmic}
\Procedure{BuildHeap}{$ A[] $}
\State \Call{HeapSize}{A} $=$ \Call{length}{A}
\For{$ i= \lfloor $\Call{length}{A}/2 $\rfloor \to 1$}
  \State \Call{Heapify}{A,i}
 \EndFor
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```

## Priority Queue
---
>[!info] Struttura 
>>[!tip] Dati
>>Un insieme di *elementi*, ognuno dei quali ha una ***chiave*** (per esempio un intero)
>
>>[!tip] Operazioni
>>- Inserimento
>>- Trova il Massimo
>>- Estrazione del Massimo
>
>>[!done] Applicazioni
>>- *Job Scheduling*
>>- *Event Driven Simulations*


### Implementazione con Vettore
>Soluzione con *Vettore Ordinato*

- Ricerca Massimo: $\Theta(1)$ operazioni
- Estrazione Massimo: $\Theta(1)$ operazioni
- Inserimento: $\Theta(n)$ operazioni

>Soluzione con *Vettore non Ordinato*


- Ricerca Massimo: $\Theta(n)$ operazioni
- Estrazione Massimo: $\Theta(n)$ operazioni
- Inserimento: $\Theta(1)$ operazioni

### Implementazione con Heap
>[!example] *Heap PQ*
>- Ricerca Massimo: $\Theta(1)$ operazioni
>- Estrazione Massimo: $\Theta(log(n))$ operazioni
>- Inserimento: $\Theta(log(n))$ operazioni

>[!question] È Vantaggioso?

In termini algoritmici
- Sostituire una funzione costante ($\Theta(1)$) con una funzione logaritmica ($\Theta(log(n))$)
- Sostituire una funzione lineare ($\Theta(n)$) con una funzione logaritmica ($\Theta(log(n))$)

>[!done] *È vantaggioso* 

