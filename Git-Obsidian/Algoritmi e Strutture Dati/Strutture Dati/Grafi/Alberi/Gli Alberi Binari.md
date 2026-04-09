## Albero Binario
---
>[!info] Definizione
>In un *albero binario* ogni nodo ha **zero**, **uno** o due **successori** ordinati
>
>>[!tip] Albero Binario **Completo**
>>Tutte le foglie hanno la stessa profondità e tutte le profondità sono completamente piene
>
>>[!tip] Albero Binario ***Quasi*** **Completo**
>>Albero Binario completo tranne che per il livello inferiore che è pieno da sinistra verso destra solo parzialmente

### Alberi Binari Quasi Completi
> *Si consideri un albero binario quasi completo di altezza* $h$

>[!example] Se il livello inferiore contiene **1 elemento**

Il numero di elementi $n$:
$$
n=(1+2+4+\dots+2^{h-1})+1 = \displaystyle{\frac{2^{h}-1}{2-1}}+1= (2^h-1)+1 = 2^h
$$
>[!example] Se il livello inferiore è pieno

Il numero di elementi $n$:
$$
n=1+2+4+\dots+2^h = \displaystyle{\frac{2^{h+1}-1}{2-1}} = 2^{h+1}-1
$$

>[!done] Range del numero di Elementi

In ogni caso il numero di elementi sarà:
$$
2^h\leq n<2^{h+1}-1
$$
Di conseguenza:
$$
\begin{array}
\ h\leq log(n)< h+1 \\
log(n)-1 < h \leq log(n) \\
h = \lceil log(n) \rceil 
\end{array}
$$
>[!question] Perchè $\lceil log(n) \rceil$?

Prendiamo $n$ come numero di nodi $+1$ di un albero binario
- $log(n)=$ altezza dell'albero completo
- L'altezza di un albero *quasi completo* è la stessa
	- Di conseguenza $log(n)$ di un albero *quasi completo* si otterrebbe un numero decimale, inferiore a quello del vero valore del livello
	- Quindi per ottenere il vero livello dell'albero si dovrà ***arrotondare il numero*** per *eccesso*

## Alberi Binari di Ricerca
---
>[!info] Definizione
>Un ***binary search tree*** (**BST**) è una *struttura dati* ad *albero binario* con delle particolari proprietà
>Le chiavi in un *binary search tree* sono sempre salvate in modo da soddisfare queste proprietà
>>[!abstract] Proprietà
>>Sia $x$ un nodo in un *binary search tree*
>>Se $y$ è un nodo del ***sotto albero di sinistra***
>><u>Allora</u>
>>Deve valere la relazione:
>>$$x.key\geq y.key$$
>>Sia $x$ un nodo in un *binary search tree*
>>Se $y$ è un nodo del ***sotto albero di destra***
>><u>Allora</u>
>>Deve valere la relazione:
>>$$x.key\leq y.key$$
 
>[!question] Quanti *binary search tree* esistono con $n$ nodi?

Il numero di *binary search tree* possibili con $n$ nodi è rappresentato con la seguente funzione dei ***Numeri di Catalan***
- [[../../../../Definizioni/Definizioni_Analisi#Coefficiente Binomiale|Coefficiente binomiale]]
$$
C_{n}=\displaystyle{\frac{1}{n+1}}\binom{2n}{n}
$$

### Operazioni
>[!example] Operazioni in un **BST**
>Un *binary search tree* ha a disposizione un set di operazioni:
>1. Search
>2. Minimum
>3. Maximum
>4. Predecessor
>5. Successor
>6. Insert
>7. Delete

>[!warning] Nota Bene

Un albero di ricerca binaria non è sempre ***ben bilanciato***:
![[attatchements/Pasted image 20240323114207.png]]
- Potrebbe accadere che i nodi siano *prevalentemente* da un *lato dell'albero*
![[attatchements/Pasted image 20240323114233.png]]
- In questo caso il [[../../../Confronto fra Algoritmi/Complessità di Algoritmi#Analisi di Complessità|costo computazionale]] delle *operazioni è più alto*


### Rappresentazione con Array
>[!info] Convenzione
>Anche gli alberi binari come lo [[../../Heap|Heap]] possono essere rappresentati con un vettore.
>Con la convenzione sugli **indici dei figli**.
>I *binary search tree* non sono alberi binari *quasi* completi
>- Ciò porta ad avere delle ***celle vuote*** all'interno dell'*array*

### Ordinamento
#### Inorder Tree Walk
```pseudo
	\begin{algorithm}
	\caption{Inorder Tree Walk}
	\begin{algorithmic}
\Procedure{Inorder-Tree-Walk}{$ x $}
\If{$ x\neq \text{ NULL }  $}
  \State \Call{Inorder-TreeWalk}{$left[x]$}
  \State \Print key[x]
  \State \Call{Inorder-TreeWalk}{$right[x]$}
 \EndIf
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```

#### Preorder Tree Walk
```pseudo
	\begin{algorithm}
	\caption{Preorder Tree Walk}
	\begin{algorithmic}
\Procedure{Preorder-Tree-Walk}{$ x $}
\If{$ x\neq \text{ NULL }  $}
\State \Print key[x]
  \State \Call{Preorder-TreeWalk}{$left[x]$}
  
  \State \Call{Preorder-TreeWalk}{$right[x]$}
 \EndIf
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```

#### Postorder Tree Walk
```pseudo
	\begin{algorithm}
	\caption{Postorder Tree Walk}
	\begin{algorithmic}
\Procedure{Postorder-Tree-Walk}{$ x $}
\If{$ x\neq \text{ NULL }  $}
  \State \Call{Postorder-TreeWalk}{$left[x]$}
  \State \Call{Postorder-TreeWalk}{$right[x]$}
  \State \Print key[x]
 \EndIf
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```

### Ricerca
```pseudo
	\begin{algorithm}
	\caption{Tree Search}
	\begin{algorithmic}
	\Procedure{TreeSearch}{$ x,k $}
	\If{$ x=\text{NULL OR } k=key[x] $}
  \Return $ x $
 \EndIf
 \If{$ k<key[x]  $}
  \Return \Call{TreeSearch}{$left[x],k$}
  \Else 
 \Return \Call{TreeSearch}{$right[x],k$}
 \EndIf
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```

### Successore e Predecessore
#### Successore
>[!info] Come Trovare il Successore di un Nodo
>Per trovare il ***successore*** di un *nodo* specificato ci sono *due casi di ricerca*
>>[!abstract] Il nodo ha il ***figlio destro***
>>Se il nodo ha il *figlio destro* **scendo** a quel nodo, sia $x$ il nodo
>>A quel punto devo trovare il ***più piccolo figlio*** del nuovo nodo
>>- Scendo al *figlio di sinistra* finché non ne trovo uno ***senza figlio di sinistra***
>
>>[!abstract] Il nodo ***non*** ha il ***figlio destro***
>>Se il nodo ***non*** ha il *figlio destro* mi devo spostare verso l'alto
>>Devo trovare il più basso antenato di $x$ il cui figlio sinistro è antenato di $x$

#### Predecessore
>[!info] Come trovare il Predecessore di un Nodo
>Analogamente al Successore, il predecessore ha *due casi di ricerca*
>>[!abstract] Il nodo ha il *figlio sinistro*
>>Se il nodo $x$ ha il *figlio sinistro*, **scendo** a quel nodo
>>A quel punto devo trovare il ***più grande figlio*** del nuovo nodo
>>- Scendo al *figlio di destra* finché non ne trovo uno senza ***figlio di destra***
>
>>[!abstract] Il nodo *non* ha il *figlio sinistro*
>>Se il nodo ***non*** ha il *figlio sinistro* mi devo spostare verso l'alto
>>Devo trovare il più alto antenato di $x$ il cui figlio destro è antenato di $x$

### Minimo e Massimo
#### Minimo
>*Per trovare il minimo sarà sufficiente scendere al nodo più a **sinistra***
```pseudo
	\begin{algorithm}
	\caption{Tree Minimum}
	\begin{algorithmic}
\Procedure{TreeMinimum}{$ x $}
	\While{$left(x) \neq \text{ NULL}$}
	\State $ x = left(x) $
    \EndWhile
    \Return $ x $
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```

#### Massimo
>*Per trovare il massimo sarà sufficiente scendere al nodo più a **destra***

```pseudo
	\begin{algorithm}
	\caption{Tree Maximum}
	\begin{algorithmic}
\Procedure{TreeMaximum}{$ x $}
	\While{$right(x) \neq \text{ NULL}$}
	\State $ x = right(x) $
    \EndWhile
    \Return $ x $
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```

#### Cancellazione
>*La cancellazione ha 3 casi:*

>[!abstract] Il nodo $z$ *non ha figli*

- Elimina $z$

>[!abstract] Il nodo $z$ ha un *solo figlio*
- Si collega l'unico *nodo figlio* con il *nodo padre*
	- Una specie di "***cortocircuito***" o "***transplant***" in *inglese*

![[attatchements/Pasted image 20240324172622.png]]

>[!abstract] Il nodo $z$ ha *due figli*

Per la cancellazione di un nodo $z$ con *due figli*:
1. Sia $y$ successore di $z$
	- $y$ ha al ***massimo*** un solo figlio
2. Sostituisci $z$ con $y$
3. Rimuovi $z$

![[attatchements/Pasted image 20240324172647.png]]

##### Pseudocodice

>[!example] Parametri
>$T\to$ ***Binary Search Tree Structure***
>$u\to$ Nodo da ***eliminare***
>$v\to$ Nodo da ***sostituire*** con $u$

```pseudo
	\begin{algorithm}
	\caption{Transplant}
	\begin{algorithmic}
\Procedure{Transplant}{$ T,u,v $}
\If{$ p(u)=\text{NULL}  $}
  \State $ root(T)=v $
  \Else \If{$ u=left(p(u))  $}
  \State $ left(p(u))=v $
  \Else 
 \State $ right(p(u))=v $
 \EndIf
 
 \EndIf
 \If{$ v \neq \text{NULL} $}
 \State $ p(v)=p(u) $
  
 \EndIf
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```

```pseudo
	\begin{algorithm}
	\caption{BST Delete}
	\begin{algorithmic}
\Procedure{TreeDelete}{$ T,z $}
\If{$ left(z)=\text{NULL}  $}
  \State \Call{Transplant}{$T,z, right(z) $}
  \Else 
 \If{$ right(z)=\text{NULL}  $}
  \State \Call{Transplant}{$T,z,left(z)$}
  \Else 
 \State $ y= $ \Call{TreeMinimum}{$z.right(z)$}
 \If{$ y\neq right(z) $}
  \State \Call{Transplant}{$T,y,right(y) $}
  \State $ right(y)=right(z) $
  \State $ p(right(y))=y $
 \EndIf
 \State \Call{Transplant}{$T,z,y$}
 \State $ left(y)=left(z) $
 \State $ p(left(y))=y $
 \EndIf
 \EndIf
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```
