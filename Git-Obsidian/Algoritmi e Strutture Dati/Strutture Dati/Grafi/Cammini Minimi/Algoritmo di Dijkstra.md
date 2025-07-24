## Dijkstra
---
>[!info] Informazioni
>Algoritmo di ricerca di [[Cammini Minimi con Sorgente Singola|cammini minimi]] di tipo [[Gli Algoritmi Greedy|Greedy]]
>L'algoritmo di basa su un *rilassamento*
>>[!caution] Struttura della soluzione
>>Ogni nodo $v$ nel grafo $G$ contiene:
>>$d[v]\to$ Il ***costo*** del cammino minimo dalla sorgente $s$ a $v$
>>$p[v]\to$ Il predecessore del vertice $v$ nel ***cammino minimo***

### Inizializzazione delle Strutture
>[!abstract] Initialize
>Per ogni nodo $v\in G$ imposto la ***distanza dalla sorgente*** $s$ a $\infty$ e il ***predecessore nullo***
>Successivamente imposto la ***distanza dalla sorgente del nodo sorgente*** a $0$

```pseudo
	\begin{algorithm}
	\caption{Dijkstra Initialize}
	\begin{algorithmic}
\Procedure{Initialize-Single-Source}{$ G,s $}
\ForAll{$v \in G$}
\State $ d[v] = \infty$
\State $ p[v]=0 $
\EndFor
\State $ d[s]=0 $
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```

### Relax
>[!question] È possibile migliorare il cammino passando da un altro cammino?

>[!info] Funzione *Relax*
>Il rilassamento di un arco $(u,v)$ verifica se è possibile migliorare il cammino per $v$ passante per $u$, trovato fino a quel momento
>Se si, si aggiornano $d[v]$ e $p[v]$
>>[!done] A parole
>>Ad ogni momento dell'espansione confronto un ***cammino che già conosco*** e un altro cammino

```pseudo
	\begin{algorithm}
	\caption{Dijkstra Relax}
	\begin{algorithmic}
\Procedure{Relax}{$ u,v,w $}
\If{$ d[v]>d[u]+w(u,v)  $}
  \State $ d[v]=d[u]+w(u,v) $
  \State $ p[v]=u $
 \EndIf
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```

#### Effetto del rilassamento

>[!abstract] Relax Effect
>Dopo avere eseguito $\text{Relax(G,u,v)}$, vale la disuguaglianza:
>$$d[v]\leq d[u]+W(u,v)$$

##### Dimostrazione
Se $d[v]>d[u]+W(u,v)$ *prima del rilassamento*
- Viene posto $d[v]=d[u]+W(u,v)$

Se $d[v]\leq d[u]+W(u,v)$ *prima del rilassamento*
- Non viene fatto nulla e quindi è ***vero anche dopo***

### Algoritmo di Dijkstra
>[!info] Strutture‎ 
>L'algoritmo mantiene un insieme $S$ che contiene i vertici $v$ *il cui peso* del cammino minimo da $s$, $\delta(s,v)$, è già *stato determinato*
>In oltre, l'algoritmo utilizza una [[Queue|coda di priorità]] contenente tutti i nodi in ***ordine di distanza dalla sorgente***, il cui *cammino minimo* non è ancora stato identificato

>[!warning] Attenzione
>L'algoritmo non ***assicura una soluzione ottima*** se il grafo contiene degli ***archi negativi***
#### Pseudocodice
```pseudo
	\begin{algorithm}
	\caption{Dijkstra's Algorithm}
	\begin{algorithmic}
	\Procedure{Dijkstra}{$ G,w,s $}
\ForAll{$v \in V[G]$}
\State $ d[v] = \infty$
\State $ p[v]=0 $
\EndFor
\State $ d[s]=0 $
\State $ S=\varnothing $
\State $ Q=V[G] $
\While{$Q\neq 0$}
\State $ u= $\Call{ Extract-Min }{$ Q $}
\State $ S=S\cup\{u\} $
\ForAll{$v \in Adj[u]$}
\If{$ d[v]>d[u]+w(u,v)  $}
  \State $ d[v]=d[u]+w(u,v) $
  \State $ p[v]=u $
 \EndIf
\EndFor
\EndWhile
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```

##### Esempio
![[Dijkstra Example.png]]

### Correttezza
>[!Teorema] 
>Se si esegue l'algoritmo di ***Dijkstra*** su di un grafo $G=(V,E,W)$ con funzione di peso non negativa $W$ e sorgente $s$
><u>Allora</u>
>Al termine si ha $d[v]=\delta(s,v)$ per ogni vertice $v\in V_{\pi}$

#### Dimostrazione
>*Si vuole provare che quando in nodo $u$ viene scoperto, $d[u]=\delta(s,u)$*

>[!abstract] Dimostrazione per Induzione

>[!todo] *Passo* "$0$"

Per la sorgente $s$ si ha $d(s)=0=\delta(s,s)$

>[!caution] Passo Induttivo

Alla iterazione $k$ si estrae da $Q$ il vertice $u$ tale per cui:
$$
d(u)=\underset{ v\in Q }{ \text{min} }\ d(v)\qquad d(p(u))=\delta(s,p(u))
$$

Gli archi del grafo hanno tutti lunghezza $w(i,j)\geq0$
- Per cui, ogni cammino $P(v,u)$ con $v,u\in Q$ ha lunghezza $d_{P}\geq 0$

Quindi $d(u)\leq d(v)+d_{P}\qquad \forall v\in Q$ 

>[!done] Quindi $d(u)$ è la distanza minima da $s$ a $u$, $\delta(s,u)$

### Complessità
>*Molto simile alla complessità dell'algoritmo di [[Minimum Spanning Tree#Algoritmo di Prim|Prim]]*

>[!info] Initialize Single Source

$$
T_{I}(V,E)=O(V)
$$
>[!caution] Relax

$$
T_{R}(V,E)=O(1)
$$

>[!abstract] Dijkstra con *coda come array*

$$
T(V,E)=T_{I}(V,E)+O(V^2)+E\cdot T_{R}(V,E)=O(V^2+E)=O(V^2)
$$
