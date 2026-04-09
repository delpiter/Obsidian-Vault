## Knapsack
---

>[!info] Problema
>>[!abstract] Knapsack 0-1
>>Un ladro che sta rapinando un negozio vuole prendere "***carico con più valore***" caricato in uno zaino capace di trasportare un peso di $W$.
>>Il ladro può scegliere di prendere un ***qualsiasi sottoinsieme*** di $n$ oggetti nel negozio.
>>- L'oggetto $i$-esimo vale $v_{i}$ e pesa $w_{i}$, dove $v_{i}$ e $w_{i}$ sono interi
>>
>>>[!caution] 0-1 poiché il ladro può o prendere o lasciare l'oggetto, non può prenderne una parte frazionaria
>
>>[!tldr] Fractional Knapsack
>>La situazione è la stessa del *Knapsack 0-1*, ma il ladro è in grado di prendere una parte frazionaria degli oggetti
>>>[!caution] Knapsack è una generalizzazione di *Knapsack 0-1*

>[!question] Quali oggetti deve rubare per massimizzare il guadagno?

### Sottostruttura del Problema
>*Entrambi i problemi soddisfano la proprietà di [[../../Definizioni/Definizioni_Algoritmi#Sottostruttura Ottimale|sottostruttura ottima]]*

Supponiamo che il ladro *possa rubare* un peso totale di $W'$ non maggiore di $W$ e di valore massimo $V$
Se togliamo dallo zaino l'oggetto $j$ otteniamo la ***soluzione ottima*** del sotto problema in cui lo zaino può ***contenere al massimo*** $W-w_{j}$ ottenuti mettendo insieme oggetti da un insieme di $n-1$
- È stato tolto l'oggetto $j$-esimo



![[attachements/knapsack-Ottimalità.png]]
>*Supponendo per assurdo che non valga la proprietà*
### Soluzione Greedy
>*Il knapsack frazionario si può risolvere tramite [[Gli Algoritmi Greedy|algoritmi Greedy]]*

>[!Idea]
>Il ladro prende la *quantità più grande possibile* dell'oggetto $i$ tale per cui $v_{i}/w_{j}$ (valore per unità di peso) è ***massimo***
>Se c'è *ancora posto* nello zaino, ***ripeti l'operazione***

![[attachements/knapsack Example.png]]

>[!done] Soluzione

![[attachements/knapsack Solution.png]]

>[!fail] Il knapsack 0-1 non è risolvibile tramite un *algoritmo greedy*

### Knapsack 0-1 Soluzione Dinamica
Il ***knapsack 0-1*** può essere risolto efficientemente da un algoritmo di [[../Programmazione Dinamica/Algoritmi di Programmazione Dinamica#Programmazione Dinamica|programmazione dinamica]]

>Il problema può essere ridotto in ***sottoproblemi*** più piccoli
> - *Riducendo la capacità* del ***knapsack***
> - *Riducendo l'insieme di alternative* (***oggetti***) fra cui scegliere

>[!info] $Knap(S,W)$
>Partendo dal problema iniziale i sottoproblemi possibili sono:
>>[!abstract] $Knap(S_{i},W)$
>>Scelgo fra i ***primi $i$ elementi*** dell'insieme $S$, valore ottimo: $f[S_{i},W]$
>
>>[!caution] $Knap(S,q)$
>>Scelgo fra tutti gli elementi di $S$ ma con ***ridotta capacità del knapsack*** ($q<W$), valore ottimo: $f[S,q]$
>
>Mettendo insieme i due sottoproblemi:
>>[!done] $Knap(S_{i},q)$
>>Scelgo fra i primi $i$ elementi dell'insieme $S$ e con ridotta capacità del knapsack, valore ottimo: $f[S_{i},q]$

#### Idea per l'Algoritmo
>[!tldr] Idea di Ricorsione
>$S_{i}$ contiene gli elementi $1,\dots,i$
>$f[i,q]$ contiene il valore della migliore selezione da $S_{i}$ con peso totale $q$
>>[!question] Come trovo $f[i,q]$?
>
>1. Se il peso dell'oggetto $i$-*esimo* $w_{i}$ è ***maggiore della capacità massima***, non è possibile prendere $w_{i}$, di conseguenza si mantiene la migliore soluzione con elementi fino a $i-1$
>>[!done] $f[i,q]=f[i-1,q]$
>
>2. Se il peso dell'oggetto $i$-*esimo* $w_{i}$ è ***minore o uguale della capacità massima***, posso aggiungere l'elemento $w_{i}$ alla migliore soluzione che lascia abbastanza spazio ($q-w_{i}$) e la confronto con la migliore soluzione senza l'oggetto $i$-*esimo*
>>[!done] $f[i,q]=max\{ f[i-1,q],f[i-1,q-w_{i}]+v_{i} \}$

>[!abstract] Inizializzazione

$f_{0}(q)=0 \qquad\forall q$

>[!question] Ci sta il primo elemento?

$$
f_{1}(q)=\begin{cases}
0 \qquad \qquad \qquad  q<w_{1} \\
max\{ 0,w_{1} \}\ \ \ \ \ \  q\geq w_{1}
\end{cases}
$$

>[!summary] Step $i$

$$
f_{i}(q)=\begin{cases}
f_{i-1}(q) \qquad \qquad \qquad \qquad \qquad \qquad q<w_{i} \\
max\{ f_{i-1}(q),f_{i-1}(q-w_{i})+v_{i} \} \ \ \ \ \ \  q\geq w_{i}
\end{cases}
$$
#### Pseudocodice
>[!Dati]
>$S$ consiste di $n$ ***elementi***
>Ogni elemento $i$ ha un *peso* $w_{i}$ e un *valore* $v_{i}$
>$W$ è il peso totale del ***knapsack***


```pseudo
	\begin{algorithm}
	\caption{Knapsack Programmazione Dinamica}
	\begin{algorithmic}
\Procedure{Knapsack01}{$ S,W $}
\State $ \text{new }f[0\dots n, 0 \dots W] $
\For{$ q=0 \to W $}
  \State $ f[0,q]=0 $
  \Comment{No item to select}
 \EndFor
 \For{$ i=1 \to n $}
  \State $ f[i,0]=0 $
  \Comment{No item can fit in a 0 capacity bag}
 \EndFor

\For{$ q=1 \to W $}
  \For{$ i=1 \to n $}
  \If{$ w[i]\leq q  $}
  \State $ f[i,q]=max\{f[i-1,q],f[i-1,q-w[i]]+v[i] \} $
  \Else 
 \State $ f[i,q]=f[i-1,q] $
 \EndIf
 \EndFor
 \EndFor
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```

>[!caution] Complessità

La complessità di questo algoritmo è ***pseudopolinomiale***
- È necessario riempire una tabella di dimensioni: ***numero di oggetti*** $\times$ ***peso della sacca***

>*In realtà la tabella è più grande ma la prima riga e la prima colonna vengono riempite in tempo lineare*
$$
\Theta(nW)
$$


##### Esempio
>*$3$ Oggetti totali*

1. Item $1$:
	- Peso $w_{1}=3$
	- Valore $v_{1}=9$

2. Item $2$:
	- Peso $w_{2}=2$
	- Valore $v_{2}=5$

3. Item $3$:
	- Peso $w_{3}=2$
	- Valore $v_{3}=5$

>Peso massimo della sacca $W=4$

