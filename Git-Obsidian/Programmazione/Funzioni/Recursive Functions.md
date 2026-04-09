[[.md|Recursive Functions]]
## Ricorsione
---
>[!info] Definizione
>La ***ricorsione*** è l'applicazione all'*informatica* del [[../../Analisi/Tipologie di Dimostrazioni#Principio di induzione|principio di induzione]] della matematica
>$$\text{Ricorsione}:\text{Informatica}=\text{Principio di Induzione}:\text{Matematica}$$
>>[!tip] In altre parole
>>La **ricorsione** è un metodo risolutivo per un problema in ***base a se stesso richiamato*** su *istanze più piccole* del problema
>>- Istanze *più piccole* $\to$ Istanze che si avvicinano ai *casi base*
>
>
>>[!done] Ricorsione Corretta: ***Regole***
>> I casi base devono essere *risolti correttamente*
>> - Essi devono essere ***ben definiti***
>> 
>>Qualunque sia l'input, le *catene di ricorsione* devono essere ***ben fondate***
>>- Da *qualunque input* io parta devo finire in uno dei *casi base*
>>
>>***Assumendo corretti*** i risultati delle chiamate ricorsive (*Passo induttivo*)
>>- Il *passo ricorsivo* deve produrre una ***soluzione corretta***

#### Esempio
```pseudo
	\begin{algorithm}
	\caption{Factorial}
	\begin{algorithmic}
\Procedure{Factorial}{$ n $}
\If{$ n==1  $}
\Comment{Base Case}
  \Return $ 1 $
  \Else 
 \Return \Call{ Factorial }{$ n-1 $}$*n$
 \State \Comment{Recursive Chain}
 \EndIf
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```
### Un Algoritmo Ricorsivo: Ricerca Binaria
>*Solitamente le funzioni iterative sono più lente rispetto a quelle ricorsive*

![[../../Algoritmi e Strutture Dati/Confronto fra Algoritmi/Complessità di Algoritmi#^7830b9]]

>[!example] Nuovi Parametri e Condizioni
>L'array $v[]$ deve essere un ***array ordinato***
> $i$ e $j$ rappresentano rispettivamente l'*indice* di *inizio* e *fine* del ***sub-array che stiamo considerando***
 
```pseudo
	\begin{algorithm}
	\caption{Binary Search}
	\begin{algorithmic}
\Procedure{Binary-Search}{$ k,v[],i,j $}
\If{$ i>j  $}
  \Return $ -1 $
  \Else 
 \State $ m=(i+j)/2 $
 \Comment{Search the middle element}
 \If{$ v[m]== val  $}
  \Return $ m $
  \Else 
 \If{$ v[m]>val  $}
  \Return \Call{ Binary-Search }{$ val,v,i,m-1 $}
  \Else 
 \Return \Call{ Binary-Search }{$ val,v,m+1,j $}
 \EndIf
 \EndIf
 \EndIf
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```
#### Analisi Complessità
>*Sia $T(n)$ il tempo di esecuzione della funzione $\text{BinarySearch}$ su un vettore di $n=j-i+1$ elementi*

In generale $T(n)$ dipende non solo dal numero di elementi su cui fare la ricerca, ma anche dalla posizione dell'elemento cercato

>[!done] Caso Ottimo
>Nell'*ipotesi più favorevole* l'elemento cercato è proprio quello che ***occupa la posizione centrale***, in tal caso
>$$T(n)=O(1)$$

>[!fail] Caso Pessimo
>Nel caso *meno favorevole* l'elemento cercato ***non esiste***
>>[!question] Quanto vale $T(n)$ in questa situazione?

##### Analisi Caso Pessimo
>*Possiamo definire $T(n)$ per ricorrenza, come segue:*

$$
T(n)=\begin{cases}
c_{1} \qquad \qquad\qquad \text{ se }n=1 \\
T\left( \left\lfloor  \displaystyle{\frac{n}{2}}  \right\rfloor \right)+c_{2}\ \  \text{ se } n>1
\end{cases}
$$
- La ***complessità è costante*** se l'array ha una *sola cella* 
- Se il vettore ha più di una cella, si richiama la funzione con un ***argomento più piccolo***
	- Per come sono definite le funzioni ricorsive, ***prima o poi finiremo nel caso base***

$$
k\text{ chiamate ricorsive}\begin{cases}
T\left( \frac{n}{2} \right) \qquad\qquad +c_{2} \\
T\left( \frac{n}{4} \right) \quad\quad +c_{2}+c_{2} \\
\quad\vdots  \\
T\left( \frac{n}{n} \right)+ c_{2}+\dots+c_{2} \\
\end{cases}
$$
Quindi all'ultima chiamata:
$$
\underbrace{ c_{1}+c_{2}+\dots+c_{2} }_{ k }
$$
>[!tldr] Ci fermiamo quando $2^k=n$

$$
2^k=n \iff log_{2}(2^k)=log_{2}(n) \iff k=log_{2}(n)
$$
### Albero della Ricorsione

![[attachements/Recursion Tree.png]]