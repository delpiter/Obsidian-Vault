## Grafo: Definizione
---
I *Grafi* sono la struttura fondamentale negli [[../../Problemi e Algoritmi#Algoritmo|algoritmi]]
>[!info] Definizione
>Un ***grafo*** è una coppia di insiemi $(V,E)$ dove
>- $V$ è un insieme di *vertici*
>- $E \subset V \times V$ è un insieme di coppie di elementi
> 
>>[!tip] Edge
>>L'*edge* è l'insieme di coppie non ordinate che connettono i vertici
>>$$\{ a,b \}=\{ b,a \}$$
>
>>[!tip] Arch
>>L'*arch* p l'insieme di coppie ordinate
>>$$(a,b)\neq (b,a)$$

>[!example] Grafo non Ordinato

$$
\begin{array}
\ V=\{ a,b,c,d,e \} \\
E=\{ \{ a,b \},\{ a,c \},\{ a,d \},\{ b,e \},\{ c,d \},\{ c,e \}, \{ d,e \} \}
\end{array}
$$
![[attachements/graph 3.png]]
>[!example] Grafo Diretto (Orientato)
>Se ogni coppia del grafo $(u,v)$ è ordinata allora il Grafo si dice *diretto o ordinato*

$$
\begin{array}
\ V=\{ a,b,c,d,e \} \\
E=\{ ( a,b ),( a,c ),( a,d ),( b,e ),( c,d ),( c,e ), ( d,e ) \}
\end{array}
$$
![[1)](attachements/graph (1|graph (1)]].png)
## Terminologia
---
### Vertici Adiacenti
>[!info] Definizione
>Due *vertici* si dicono ***adiacenti*** se sono *connessi da un arco*
>>[!tip] In un Grafo non Orientato
>>$u,v$ sono adiacenti se $\{ u,v \}\in E$
>
>>[!tip] In un Grafo Orientato
>>Se $(u,v)\in A \implies v$ adiacente a $u$ e $(u,v)$ è incidente in $v$
>>

### Grado di un Vertice
>[!info] Definizione
>In un *vertice* il ***grado*** è il numero di vertici adiacenti

### Cammino
>[!info] Definizione
>Una sequenza di *vertici* $v_{1},v_{2},\dots,v_{k}$ tale per cui ogni coppia di vertici consecutivi $v_{i},v_{i+1}$ è adiacente, è chiamata cammino
>- In un grafo orientato è detto *catena*
>>[!tip] Cammino Elementare
>>Un *cammino* si dice elementare quando non ci sono vertici ripetuti

 ![[attachements/image-removebg-preview.png]]
*Grafo 1: Cammino non Elementare, Grafi 2-3: Cammini Elementari*

>[!example] Ciclo
>Un *ciclo* è un cammino elementare con il primo vertice che coincide con l'ultimo
>>[!tip] Grafo Orientato
>>In un Grafo Orientato è detto *circuito*

^e45e8d

*Nell'immagine precedente, l'insieme di vertici: $\{ d,c,e,d \}$ è un ciclo*

### Grafo Connesso
>[!info] Definizione
>Un grafo si dice *connesso* quando qualsiasi coppia di vertici è unita da almeno un cammino

![[attachements/grafo connesso.png]]
*Grafo 1: Grafo connesso - Grafo 2: Grafo non Connesso*

### Grafo Completo
>[!info] Definizione
>Un *grafo completo* ha un arco fra ogni coppia di nodi

![[attachements/graphedges.png]]

### Componente Connessa e Sottografo
>[!info] Sottografo
>Un *sottografo* è un sottoinsieme di vertici e archi di un grafo dato

>[!tip] Componente Connessa
>Una *componente connessa* è un sottografo connesso massimale
>>[!done] Definizione Massimale
>>Non posso prendere altri elementi del grafo senza perdere la proprietà di connessione

![[attachements/Componente connessa.png]]

### Grafo Trasposto
>[!info] Definizione
>Un grafo *orientato* $G^T=(V;E^T)$ è detto trasposto di $G=(V,E)$ se
>$$E^T=\{ (u,v):(v,u)\in E \}$$
>$G$ e $G^T$ hanno le stesse componenti fortemente connesse

![[attachements/grafotrasposto.png]]
### Grafo Pesato
>[!info] Definizione
>Gli *archi* possono avere un *peso* associato
>Il peso può essere determinato da una funzione  $p:V\times V \to\mathbb{R}$
>Se non è specificato un peso su un arco, lo si assume infinito
>>[!tip] Cardinalità 
>>L'insieme dei *pesi* ha la cardinalità uguale all'insieme degli *archi*

![[attachements/grafo Pesato.png]]
