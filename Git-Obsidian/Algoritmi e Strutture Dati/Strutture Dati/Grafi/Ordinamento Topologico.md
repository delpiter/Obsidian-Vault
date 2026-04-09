## Grafo Diretto Aciclico
---
>[!info] Definizione
>Un ***Direct Acyclic Graph***, `DAG`, è un grafo diretto che *non contiene* ***cicli*** diretti

- Spesso utilizzato per rappresentare precedenze fra eventi
	- Specificando che un evento $a$ accada prima di un evento $b$

L'induzione di un ordine totale può essere fatta per mezzo dell'***ordinamento topologico***

### Ordinamento Topologico DAG
>[!info]
>L'*ordinamento topologico* di un `DAG` è un ***ordinamento lineare*** di tutti i suoi vertici
>tale che per ogni arco $(u,v)$ nel `DAG`, $u$ appare prima di $v$ nell'ordinamento

#### Pseudocodice
>[!tldr] Idea
>L'algoritmo chiama [[Algoritmi di Ricerca su Grafo#Depth First Search|DFS]] per calcolare i ***tempi di fine visita*** per ogni vertice $v$
>Appena la visita di un vertice è *finita*, si ***inserisce in testa ad una lista***
>***Ritorna*** la lista

```pseudo
	\begin{algorithm}
	\caption{DAG Topological Sort}
	\begin{algorithmic}
\Procedure{Topological-Sort}{$ G $}
\State \Call{ DFS }{$ G $}
\State \Comment{As each vertex is finished, insert it onto the front of a linked list}
\Return $ list $
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```

La ***linked list*** contiene l'***ordinamento***

#### Teorema
>[!check] Teorema `DAG`
>Un grafo diretto $G$ è aciclico $\iff$ Una ricerca `DFS` si $G$ non produce [[Algoritmi di Ricerca su Grafo#Back Edges|Back Edges]] 

##### Dimostrazione
>*Dimostrazione per assurdo* $\implies$

Sia $G$ un ***grafo diretto aciclico***

Si supponga che ci sia un arco all'indietro $(u,v)$
- $v$ è un antenato di $u$ nella foresta `DFS`

Quindi c'è un cammino da $v$ a $u$ in $G$ e $(u,v)$ chiude il ***ciclo***

>[!fail] Contraddizione, $G$ è aciclico

>*Dimostrazione per assurdo* $\impliedby$

Sia $G$ un grafo senza ***back edges***

Si supponga che $G$ contenga un ciclo $c$
- Sia $v$ il primo vertice in $c$ ad essere *scoperto* e sia $u$ un predecessore di $v$ in $c$

Al tempo $d[v]$ il ciclo da $v$ a $u$ è ***bianco***
- Bisogna visitare tutti i nodi raggiungibili su questo cammino prima di tornare alla $DFS-Visit(v)$
	- $u$ diventa un discendente di $v$

>[!fail] Contraddizione, $(u,v)$ è un *back edge*

#### Costo Computazionale
- Ricerca `DFS`: $O(V+E)$
- Inserimento di ciascuno dei $\mid V\mid$ vertici in testa alla lista: $O(1)$

>[!done] Tempo Totale
>$$O(V+E)$$

#### Esempio
![[attachements/Pasted image 20240414175958.png]]

- L'***Ordinamento Topologico*** ritorna la lista:

![[attachements/Pasted image 20240414180041.png]]


#### Correttezza dell'Ordinamento
>[!Tesi]
>Dato un `DAG`, un arco $(u,v)\in E \implies f[v]<f[u]$

##### Dimostrazione
>*Quando $(u,v)$ viene percorso, $u$ è **grigio**, ci sono 3 casi*

>[!abstract] $v$ è *grigio*

- $(u,v)$ è un Back Edge $\implies$ ciclo, *contraddizione*

>[!abstract] $v$ è *bianco*

-  $v$ diventa discendente di $u$
- $v$ sarà finito prima di $u$
- $f[v]<f[u]$

>[!abstract] $v$ è *nero*

- $v$ è già *finito*
- $f[v]<f[u]$
