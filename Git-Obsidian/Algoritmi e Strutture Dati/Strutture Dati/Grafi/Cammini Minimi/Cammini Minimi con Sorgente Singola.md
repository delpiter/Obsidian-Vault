## Shortest Path Single Source
---
>[!info] Problema
>È un [[../../../../Definizioni/Definizioni_Algoritmi#Problema di Ottimizzazione|problema di ottimizzazione]], chiede di trovare il ***percorso minimo*** fra *due nodi* in un grafo
>>[!abstract] Input
>>Un [[../I Grafi|Grafo]] orientato o non orientato $G=(V,E,W)$ con ***funzione di peso***: $w:E\to\mathbb{R}$
>>E un vertice di tale grafo $s\in V$
>
>>[!caution] Output
>>Per ogni vertice $v\in V$, trovare il cammino di peso minimo da $s$ a $v$
>
>>[!example] Altri casi
>>- Trovare il cammino minimo fra una *coppia di vertici* $u$ e $v$
>>- Trovare i cammini minimi fra *tutte le coppie di vertici*

>[!done] Ipotesi Importante
>Nel grafo $G$ non possono essere presenti ***cicli di peso negativo***


### Cammini Minimi
>[!info] Definizione
>Sia $G=(V,E)$ un grafo orientato ai cui archi è associato un costo $W(u,v)$
>Il ***costo di un cammino*** $p=(v_{0},v_{1},\dots,v_{k})$ è la ***somma dei costi degli archi*** che lo costituiscono
>$$W(p)=\sum_{i=1}^k W(v_{i-1},v_{i})$$

Il costo di un cammino minimo da un vertice $u$ ad un vertice $v$ è definito come:
$$
\delta(u,v)=\begin{cases}
min(W(p))\quad \text{se }\exists\  W(p) \text{ da }u \text{ a } v \\
\infty \qquad \qquad\ \ \text{ altrimenti} 
\end{cases}
$$

>[!done] Cammino Minimo
>Un cammino minimo da $u$ a $v$ è un cammino $p$ da $u$ a $v$ di costo:
>$W(p)=\delta(u,w)$

#### Rappresentazione di Cammini Minimi
>*I cammini minimi vengono rappresentati analogamente agli alberi [[../Algoritmi di Ricerca su Grafo#Breadth First Search|BFS]]*

>[!abstract] Albero dei Cammini Minimi
>Per ogni vertice $v\in V$ si mantiene un ***predecessore*** $\pi(v)$
>I valori di $\pi$ inducono un *sottografo dei predecessori* $G_{\pi}=(V_{\pi},E_{\pi})$
>$G_{\pi}$ risulterà essere un ***albero di cammini minimi***, cioè:
>- $V_{\pi}$ è l'insieme dei ***vertici raggiungibili*** da $s$ in $G$
>- $G_{\pi}$ forma un ***albero con radice*** in $s$
>- Per ogni $v\in V_{\pi}$ l'unico ***cammino semplice*** da $s$ a $v$ in $G_{\pi}$ è un ***cammino minimo*** da $s$ a $v$ in $G$

### Sottostruttura Ottima
>*"Se da Cesena a Bologna il percorso migliore passa da Faenza, da Cesena a Faenza il percorso migliore è lo stesso"*

>[!abstract] Concetto
>Gli *algoritmi di ricerca di cammini minimi* si basano sulla proprietà che un cammino minimo tra due vertici ***contiene altri cammini minimi*** al suo interno

>[!info] Teorema
>Se il cammino $p=(v_{0},v_{1},\dots,v_{k})$ è minimo
><u>Allora</u>
>Sono minimi anche ***tutti i sottocammini*** $p_{ij}=(v_{i},\dots,v_{j})$

#### Dimostrazione
>*Sia $p=(v_{0},\dots,v_{k})$ un cammino minimo*

Se esistesse un cammino $q$ da $v_{i}$ a $v_{j}$, ($v,j\in[0,k]$) ***minore*** di $p_{ij}$
Allora:
- Sostituendo nel cammino $p$ il sotto cammino $p_{ij}$ con il cammino $q$ si otterrebbe un cammino da $v_{0}$ a $v_{k}$ di costo minore di $p$

>[!fail] Contraddizione: $p$ è un cammino minimo

Quindi
- Se $p$ è un cammino minimo da $s$ ad un vertice $v$ diverso da $s$
- Se $u$ è il vertice che precede $v$ nel cammino

<u>Allora</u>

$$
\delta(s,v)=\delta(s,u)+W(u,v)
$$

#### Archi Negativi
>*Il costo degli archi èuò essere negativo*

Questo *può non creare problemi* nella ricerca dei cammini minimi da una sorgente $s$
- A meno che vi siano ***cicli di costo negativo*** raggiungibili da $s$

>[!abstract] Concetto
>Se $u$ è un vertice raggiungibile da $s$ con un cammino $p$ passante per un vertice $v$ di un ciclo negativo
><u>Allora</u>
> Esistono cammini da $s$ a $u$ di ***costi sempre minori***, il costo di cammino minimo $\delta(s,u)$ ***non è definito***
>>[!caution] In questo caso poniamo $\delta(s,u)=-\infty$

![[attachements/Negative Weight Edges.png]]

>[[Algoritmo di Dijkstra|!warning]] non si accettano archi di costo negativo

