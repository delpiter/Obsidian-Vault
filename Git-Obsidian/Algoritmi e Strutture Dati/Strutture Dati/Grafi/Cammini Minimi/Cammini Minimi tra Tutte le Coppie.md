## All Pair Shortest Paths
---
>[!info] Problema
>Dato un [[../I Grafi|grafo]] ***orientato o non orientato e pesato***, trovare per ogni coppia di vertici $u,v\in V$ il ***minimo peso di un cammino*** da $u$ a $v$
>>[!abstract] Input
>>Un grafo orientato o non orientato $G=(V,E,W)$, con *funzione di peso* $w: E\to\mathbb{R}$ di cui si vogliono trovare i [[Cammini Minimi con Sorgente Singola#Cammini Minimi|cammini minimi]] fra ogni coppia di vertici $u,v$
>
>>[!caution] Output
>>Una struttura che indica il cammino minimo da un qualsiasi nodo $u$ ad un qualsiasi nodo $v$
>>Verrà calcolata una ***matrice di predecessori*** $\Pi(\pi_{uv})$ dove $\pi_{uv}$ è $NULL$ se $u=v$ o se non c'è ***nessun cammino*** da $u$ a $v$, altrimenti è un ***predecessore*** di $v$ su di un *cammino minimo* da $u$

Il sottografo indotto dall'$i$-esima riga della matrice $\Pi$ sarà un ***albero di cammini minimi*** con ***radice*** in $i$

### Algoritmo di Floyd-Warshall
>[!info] Floyd-Warshall
>È un [[../../../Programmazione Dinamica/Algoritmi di Programmazione Dinamica|algoritmo di programmazione dinamica]], può gestire ***archi di peso negativo***, ma si assume che ***non ci siano cicli negativi***
>>[!tldr] Idea
>>$d_{s,t}(i)$: cammino minimo da $s$ a $t$ contenente solo i vertici intermeti $v_{1},\dots,v_{i}$
>>- $d_{s,t}(0)=w(s,t)$
>>$$d_{s,t}(k)=\begin{cases}w(s,t) \qquad \qquad \qquad \qquad\qquad\qquad\qquad\qquad\text{ se }k=0 \\ min\{ d_{s,t}(k-1),d_{s,k}(k-1)+d_{k,t}(k-1) \} \quad \text{ se }k>0\end{cases}$$
>>
>>>[!question] È più corto lasciare il percorso attuale o *aggiungere un nodo intermedio*?

#### Determinazione $\Pi$
>*$\Pi$ è ottenibile da $D$ in $O(n^3)$*

>[!abstract] Oppure "*on-line*", mentre si aggiorna la $D$

$$
\pi_{ij}(0)=\begin{cases}
NULL\qquad \text{ se } i=j \text{ o } w_{ij}=\infty \\
i \qquad \qquad \quad \text{se } i\neq j \text{ e } w_{ij}<\infty  
\end{cases}
$$
- ***successivamente***
$$
\pi_{ij}(k)=\begin{cases}
\pi_{ij}(k-1) \qquad \text{ se } d_{ij}(k-1)\leq d_{ik}(k-1)+d_{kj}(k-1)\\
\pi_{kj}(k-1)\qquad \text{ se } d_{ij}(k-1)> d_{ik}(k-1)+d_{kj}(k-1)
\end{cases}
$$

#### Pseudocodice
```pseudo
	\begin{algorithm}
	\caption{Floyd-Warshall's Algorithm}
	\begin{algorithmic}
\Procedure{Floyd-Warshall}{$ W,n $}
\State $ D^{(0)}=W $
\For{$ k=1\to n $}
\State \Comment{Recursion Loop}
  \For{$ i=1 \to n $}
  \State \Comment{For each origin}
  \For{$ j=1 \to n $}
  \State \Comment{For each destination}
\State $ d_{ij}(k)=min \{d_{ij}(k-1),d_{ik}(k-1)+d_{kj}(k-1)\} $  
 \EndFor
 \EndFor
 \EndFor
 \Return $ D(n) $
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```
#### Complessità
>*La complessità è determinata dai tre cicli for*

Ogni esecuzione dell'istruzione interna è $O(1)$, quindi 

>[!done] Complessità Floyd-Warshall
>$$T(V,E)=\Theta(n^3)=\Theta(V^3)$$

#### Stampa dei cammini minimi
```pseudo
	\begin{algorithm}
	\caption{Shortest Path Print}
	\begin{algorithmic}
\Procedure{Print-All-Pairs-Shortest-Path}{$ n,i,j $}
\If{$ i=j  $}
  \State \Call{ Print }{$ i $}
  \Else 
 \If{$ \pi_{ij} = NULL  $}
  \State \Call{ Print }{$ \text{"Path does not Exists"} $}
  \Else 
 \State \Call{ Print-All-Pairs-Shortest-Path }{$ n,i,\pi_{ij} $}
 \State \Call{ Print }{$ j $}
 \EndIf
 \EndIf

 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```

