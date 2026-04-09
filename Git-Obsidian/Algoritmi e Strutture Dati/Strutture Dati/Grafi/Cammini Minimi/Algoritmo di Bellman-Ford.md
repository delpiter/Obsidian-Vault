## Bellman-Ford
---
>[!informazioni]
>Algoritmo di ricerca di [[Cammini Minimi con Sorgente Singola|cammini minimi]] tramite [[../../../Programmazione Dinamica/Algoritmi di Programmazione Dinamica|programmazione dinamica]]
>Risolve lo stesso problema dell'algoritmo di [[Algoritmo di Dijkstra|Dijkstra]]
>>[!caution] Basato sulla seguente Equazione Ricorsiva
>>$$d^k[v]=\begin{cases} v=s\ ?\ 0:\infty \qquad \qquad \qquad k=0\\ min\{ d^{k-1}[u]+w(u,v) \}\ \ \ \  1\leq k\leq n \end{cases}$$
>>Dove $k$ indica il numero di archi intermedi che il cammino può utilizzare
>>- $d^k[v]\to$ è la ***distanza minima*** per andare da una *sorgente* a una *destinazione* passando $k$ ***nodi intermedi***

A differenza di Dijkstra:

>[!done] L'algoritmo di *Bellman-Ford* accetta anche *archi con peso negativo*

>[!abstract] Valore Restituito
>Restituisce un booleano che dice ***se esiste un ciclo di peso negativo*** (*nessuna soluzione*)
>Oppure produce l'***albero dei cammini minimi***

![[Algoritmo di Dijkstra#Inizializzazione delle Strutture]]

>*Anche Bellman-Ford utilizza la stessa funzione di relax di Dijkstra*

![[Algoritmo di Dijkstra#Relax]]

#### Pseudocodice
>[!info] Struttura Pseudocodice
>L'algoritmo si divide in due parti
>>[!abstract] Ricerca Cammini Minimi
>>La prima parte esegue l'effettivo algoritmo di programmazione dinamica per la ***ricerca dei cammini minimi*** da una sorgente $s$ a un nodo $v \in V[G]$
>
>>[!caution] Ricerca Cicli Negativi
>>La seconda parte non fa altro che ***ripetere un ciclo dell'algoritmo*** per vedere se ci possono essere *miglioramenti dei percorsi*
>>Se almeno uno dei percorsi viene migliorato vuol dire che è ***presente un ciclo negativo***

```pseudo
	\begin{algorithm}
	\caption{Bellman-Ford's Algorithm}
	\begin{algorithmic}
\Procedure{BellmanFord}{$ G,w,s $}
\State \Call{ Initialize-Single-Source }{$ G,s $}
\For{$ k=1 \to |V[G]-1| $}
  \For{$ (u,v)\in E[G] $}
\State \Call{ Relax }{$ u,v,w $}
 \EndFor
 \EndFor
 \State $  $
 \Comment{At this point all the Shortest Path are found}
 \State $  $
 \Comment{Do another loop to identify negative loops}
 \For{$ (u,v)\in E[G] $}
	\If{$ d[v]>d[u]+w(u,v)  $}
  \Return $ \text{False} $
 \EndIf
 \EndFor
	 \Return $ \text{True} $
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```

##### Esempio
![[attachements/Bellman-Ford Example.png]]
### Correttezza
>[!Teorema]
>Si esegua *Bellman-Ford* su un grafo orientato e pesato $G=(V,E)$ con sorgente $s$ e funzione di peso $w:E\to\mathbb{R}$
>- Se $G$ ***non contiene cicli di peso negativo*** l'algoritmo restituisce `True` e si ha che: $d[v]=\delta(s,v)$ per tutti i vertici $v\in V$ e che il sottografo dei predecessori è un albero di cammini minimi radicato in $s$
>- Se $G$ ***ha un ciclo di peso negativo***, l'algoritmo restituisce `False`

### Complessità
>[!info] Initialize Single Source

$$
T_{I}(V,E)=O(V)
$$
>[!caution] Relax

$$
T_{R}(V,E)=O(1)
$$

>[!abstract] Bellman-Ford

$$
T(V,E)=T_{I}(V,E)+O(V^2)+V\cdot E\cdot T_{R}(V,E)+E=O(V)+V\cdot E\cdot O(1)+E=O(V\cdot E)
$$

## Cammini minimi in DAG
---
>*Rilassando gli archi di un grafo pesato $G=(V,E)$ secondo un ordine topologico, si possono calcolare i cammini minimi da una singola sorgente in tempo $O(V+E)$*

```pseudo
	\begin{algorithm}
	\caption{DAG Shortest-Path}
	\begin{algorithmic}
	\Procedure{DAG-Shortest-Path}{$ G,w,s $}
\Comment{Topologically sort the vertices of G}
\State\Call{ Initialize-Single-Source }{$G,s  $}
\ForAll{$u\in V[G] \text{ taken in topologically sorted order}$}
\ForAll{$v \in Adj[u]$}
\State \Call{ Relax }{$ u,v,w $}
\EndFor
\EndFor
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```

#### Esempio
![[attachements/DAG Shortest Path.png]]

### Complessità
$$
T(V,E)=\underset{ sort }{ \Theta(V+E) }+\underset{ Initialize }{ \Theta(V) }+\underset{ Relax }{ E\Theta(1) }=\Theta(V+E)
$$