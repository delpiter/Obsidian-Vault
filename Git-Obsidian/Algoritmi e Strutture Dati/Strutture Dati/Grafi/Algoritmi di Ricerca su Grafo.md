>*Negli algoritmi di seguito si assume una rappresentazione a [[Rappresentazione di Grafi#Liste di Adiacenza|liste di adiacenza]]*

## Attraversamento di un Grafo
---
>[!info] Definizione del Problema
>***Graph Traversal***
>Dato un grafo $G=(V,E)$ ed un vertice $r\in V$ detto sorgente si richiede:
>- ***Visitare*** ogni vertice raggiungibile nel grafo dal vertice $r$
>- Ogni nodo deve essere ***visitato*** *una volta sola*
>
>>[!tldr] *Breadth Firsth Search*
>>`BFS`
>>Visita i nodi espandendo una frontiera fra ***nodi scoperti/da scoprire*** cercando di restare il più possibile ***vicini alla radice***
>
>>[!tldr] *Depth First  Search*
>>`BFS`
>>Visita i nodi andando subito il più ***lontano possibile dalla radice***

### Breadth First Search
>[!info] Descrizione
>Una ricerca per ampiezza percorre una [[I Grafi#Componente Connessa e Sottografo|componente connessa]] di un grafo e facendolo definisce un [[Alberi/Gli Alberi#Alberi Definizione|albero]] di copertura con molte proprietà utili

Dato un **vertice** ***sorgente*** $s$, `BFS` calcola la distanza (*minimo numero di archi*) da $s$ a ogni vertice *raggiungibile*
- Al vertice $s$ viene associata una distanza di $0$

>[!tldr] Color Code
>Ogni vertice ha un ***colore associato***:
>- ***Bianco*** $\to$ Non *Scoperto*
>- ***Grigio*** $\to$ *Scoperto* ma non *Espanso*
>- ***Nero*** $\to$ *Espanso*
>
>>[!done] Vertice Espanso
>>Un vertice si dice ***espanso*** quando ciascuno dei suoi ***vertici adiacenti*** è stato *scoperto*

Nella prima mossa vengono ***scoperti*** tutti i nodi raggiungibili dall'origine percorrendo ***un solo arco***
- Viene assegnata a questi nodi una distanza di $1$

Al passo successivo vengono ***scoperti*** tutti i nodi raggiungibili dall'origine percorrendo ***due archi***
- Viene assegnata a questi nodi una distanza di $2$
>[!abstract] Loop
>Si continua così fino a che non è associato ***un livello*** ad ***ogni vertice***
 
Ogni vertice $v$
- Viene etichettato con la lunghezza $d$ del cammino più breve da $s$ a $v$
- Viene etichettato con l'id $\pi(v)$ del ***vertice predecessore*** da cui proveniva quando si è scoperto $v$

>[!warning] I vertici scoperti ma non espansi sono mantenuti in una coda $Q$

#### Pseudocodice
>*All'inizio tutti i nodi sono bianchi e distanti $\infty$ fra di loro*

>[!info] Descrizione
>Algoritmo diviso in ***3 sezioni***
>1. *Inizializzazione* di tutti i vertici
>2. *Inizializzazione* algoritmo con $s$
>3. *Scoperta* di tutti i nodi

>[!abstract] Parametri
>- $V[G]\to$ *Grafo*
>- $s\to$ *Nodo Sorgente*
>- $color[u]\to$ *Stato di colore* del nodo $u$
>- $d[u]\to$ *Distanza dalla sorgente* del nodo $u$ 
>- $\pi[u]\to$ Vertice predecessore di $u$
>- $Q\to$ *Coda* 
>- $Adj[u]\to$ Lista di *vertici adiacenti* di $u$

```pseudo
	\begin{algorithm}
	\caption{Breadth First Search}
	\begin{algorithmic}
\Procedure{BFS}{$ V[G],s $}
\State \Comment{First Section}
\ForAll{$u \in V[G]-\{s\} $}
\State $ color[u]=white $
\State $ d[u]=\infty $
\State $ \pi[u]=\text{NULL} $
\EndFor
\State $ ‎  $
\State \Comment{Second Section}
\State $ color[s]= grey $
\State $ d[s]=0 $
\State $ \pi[s]=\text{NULL} $
\State $ Q=\{s\} $
\State $ ‎  $
\State \Comment{Third Section}
\While{$Q\neq 0$}
\State $ u = head[Q] $
\ForAll{$v \in Adj[u]$}
\If{$ color[v] == white  $}
  \State $ color[v] = grey $
  \State $ d[v] = d[u]+1 $
  \State $ \pi[v] = u $
  \State \Call{ Enqueue }{$ Q,v $}
 \EndIf
\EndFor
\State \Call{ Dequeue }{$ Q $}
\State $ color[u]=black $
\EndWhile
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```
#### Esempio
![[attachements/BFS-1.png]]
![[attachements/BFS-2.png]]

#### Analisi della Complessità
>*Dato un grafo* $G=(V,E)$

>[!abstract] Sezione 1
>L'*inizializzazione* dell'algoritmo richiede $O(V)$

>[!attention] Sezione 2
>La sezione 2 si conclude sempre in un ***tempo costante*** $=O(1)$

>[!info] Sezione 3
>I vertici vengono *accodati* se il loro ***colore è bianco***
>- Assumendo che un accodamento/rimozione richieda tempo costante, il costo totale di questa operazione è $O(V)$
>
>La *lista di adiacenze* di un vertice **viene percorsa** quando il vertice viene ***rimosso dalla lista***
>- La *somma delle lunghezze* di tutte le liste è $\Theta(E)$ quindi è richiesto $O(E)$ per *percorrerle tutte*

>[!done] Tempo totale di `CPU` è $O=(V+E)$

Cioè lineare nella dimensione della rappresentazione del grafo con [[Rappresentazione di Grafi#Liste di Adiacenza|liste di adiacenza]]

#### Proprietà
>[!example] Proprietà  `BFS`
>- Dato un grafo $G=(V,E)$, la `BFS` scopre tutti i vertici ***raggiungibili*** da un vertice origine $s$
>- *Calcola* la ***distanza minima*** per ogni vertice raggiungibile
>- *Calcola* un albero ***breadth first*** contenente tutti i vertici raggiungibili
>- Per ogni vertice $v$ raggiungibile da $s$, il cammino nell'albero ***breadth first*** da $s$ a $v$ corrisponde ad un cammino minimo in $G$

##### Alberi BFS
>*Sottografo dei predecessori di $G$*

$$
\begin{array}
\ G_{\pi}=(V_{\pi},E_{\pi}) \\
V_{\pi}=\{ v\in V:\pi[v]\neq \text{NULL} \}\cup\{ s \} \\
E_{\pi}=\{ (\pi[v],v)\in E :v\in V_{\pi} -\{ s \}\}
\end{array}
$$
Se applicata ad un grafo $G$ la `BFS` costruisce $\pi$ in modo tale che il sottografo dei predecessori $G_{\pi}$ è un albero ***breadth first***
- $V_{\pi}$ consiste di tutti i ***vertici raggiungibili*** da $s$
- Per ogni $v\in V_{\pi}$ c'è un unico ***cammino elementare*** in $G_{\pi}$ da $s$ a $v$ ed è anche il ***cammino minimo***

### Depth First Search
>[!info] Descrizione
>La ***ricerca in profondità*** visita la [[I Grafi#Componente Connessa e Sottografo|componente connessa]] raggiungibile da un nodo $u$ esplorando i nodi in ***maniera ricorsiva***

>[!abstract] Schema di Funzionamento
>La ***ricerca in profondità*** in un grafo non diretto $G$ si basa sullo schema seguente
>- Si inizia da un vertice $u$ qualsiasi, etichettandolo "***scoperto***", si etichetta $u$ come vertice corrente
>- Si percorre uno qualsiasi degli archi adiacenti al nodo. $(u,v),v\in Adj[u]$
>- Se l'arco $(u,v)$ porta ad un vertice $v$ già visitato, si ritorna in $u$
>- Se il vertice $v$ **non** è ancora stato ***visitato***, diventa il *vertice corrente*, lo si etichetta "***scoperto***" e si ripete il passo precedente
>In questo modo si visita la ***componente connessa*** raggiungibile da $u$

Prima o poi si arriva ad un punto in cui tutti gli archi incidenti su $u$ portano a vertici visitati.

Allora si attua un ***backtrack*** ritornando al vertice $v$ visitato prima di $u$.
- Il vertice $v$ diventa il *vertice corrente* e si ripetono i passi precedenti

 Quando anche tutti i vertici incidenti su $v$ portano a vertici visitati si effettua un altro ***backtrack***
 - Si continua ad effettuare ***backtrack*** lungo il cammino percorso
 - Esplorando archi che portano a ***vertici inesplorati*** e ripetendo la procedure

#### Pseudocodice

>[!info] Algoritmo `DFS`
>1. ***Inizializza*** $\to$ colora di *bianco* tutti i vertici
>2. Visita ogni vertice bianco usando $DFS-Visit$
>3. Ogni chiamata a $DFS-Visit(u)$ inizializza un ***nuovo albero*** con radice in $u$
>4. Quando $DFS-Visit$ finisce, ogni vertice $u$ ha associato:
>	1. Un tempo di ***inizio visita*** $d[u]$
>	2. Un tempo di ***fine visita*** $f[u]$
>5. Quando un vertice $v$ viene ***scoperto***, gli si associa in $\pi(v)$ l'id del ***predecessore***

Algoritmo ricorsivo diviso in due funzioni

>*Inizializza tutti i vertici*
```pseudo
	\begin{algorithm}
	\caption{Depth First Search}
	\begin{algorithmic}
	\Procedure{DFS}{$ G $}
\ForAll{$u \in V[G] $}
\State $ color[u]=white $
\State $ \pi[u]=\text{NULL} $
\EndFor
\State $ time = 0 $
\ForAll{$u \in V[G]$}
\If{$ color[u] == white  $}
 \State \Call{DFS-Visit}{$u$}
 \EndIf
\EndFor
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```

>*Visita ricorsivamente tutti i figli*

```pseudo
	\begin{algorithm}
	\caption{Depth First Search}
	\begin{algorithmic}
\Procedure{DFS-Visit}{$ u $}
\State $ color[u]=gray $
\State $ time++ $
\State $ d[u]=time $
\ForAll{$v \in Adj[u]$}
\If{$ color[v] == white $}
  \State $ \pi[v] = u $
  \State \Call{ DFS-Visit }{$ v $}
 \EndIf
\EndFor
\State $ color[u]=black $
\State $ time++ $
\State $ f[u]=time $
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```

#### Esempio
![[attachements/DFS-1.png]]
![[attachements/DFS-2.png]]
#### Complessità Computazionale
>[!tldr] Tempo di `CPU`
>Il ciclo in $DFS$ richiede un tempo $\Theta(V)$, *escludendo* il tempo per eseguire $DFS-Visit$ 
>$DFS-Visit$ è chiamata una volta ***per ogni vertice***
>- È chiamata ***solo*** per i vertici ***bianchi***
>- Etichetta *immediatamente* il vertice col ***grigio***
>Per ogni $DFS-Visit$ un ciclo percorre tutta $Adj[v]$
>Il costo totale per $DFS-Visit$ è $\Theta(E)$
>$$\sum_{v\in V}\mid Adj[v] \mid=\Theta(E)$$
>>[!done] Complessità
>>Il tempo di `CPU` di $DFS$ è $\Theta(V+E)$

#### Sottografo dei Predecessori
>*Definito in modo leggermente diverso dalla `BFS`*

$$
\begin{array}
\ G_{\pi}=(V, E_{\pi}) \\
E_{\pi}=\{ (\pi[v],v)\in E:v\in V \text{ and } \pi[v]\neq \text{NULL}\}
\end{array}
$$

- Il sottografo in questo caso forma una [[Alberi/Gli Alberi#Definizioni sugli Alberi|foresta]] ***depth-first*** composta da vari *alberi* ***depth-first***

#### Tempi di Visita
>*L'algoritmo `DFS` mantiene un orologio globale su:*
>- *Tempo di inizio visita $d[u]$*
>- *Tempo di fine visita $f[u]$*

>[!check] Per ogni vertice $u$ è verificata la disuguaglianza
>$$d[u]<f[u]$$

##### Stato dei Vertici
>[!tldr] Stato del vertice in base al Tempo
>Sia $u$ un vertice del grafo
>Il vertice $u$ è:
>- ***Bianco*** prima del tempo $d[u]$
>- ***Grigio*** fra il tempo $d[u]$ e $f[u]$
>- **Nero** dopo il tempo $f[u]$

- Ad uno stesso tempo $t$ i vertici ***grigi*** formano una catena lineare

##### Teorema delle Parentesi
>[!Ipotesi]
>I ***tempi di visita*** hanno una struttura a parentesi
>- Rappresentando il ***tempo di inizio visita*** di $u$ con una ***parentesi aperta***: $(u$
>- Rappresentando il ***tempo di fine visita*** di $u$ con una ***parentesi chiusa***: $u)$
>
>La storia di inizi e fine visita definisce una espressione ben formata
>- Le parentesi sono *annidate correttamente*

>[!abstract] Teorema
>In ogni `DFS` di un grafo $G=(V,E)$, per ogni coppia di vertici $u$ e $v$, ***una e una sola*** delle seguenti condizioni è ***soddisfatta***
>- Gli intervalli $[[../../../Analisi/Insiemi/Insiemi Numerici#Insiemi Separati|disgiunti]]
>	- Ne $u$ è *discendente* di $v$, ne $v$ è *discendente* di $u$
>- L'intervallo $[d[u],f[u]]$ è ***contenuto interamente*** in $[d[v],f[v]]$
>	- $u$ è un *discendente* di $v$ nell'albero `DFS`
>- L'intervallo $[d[v],f[v]]$ è ***contenuto interamente*** in $[d[u],f[u]]$
>	- $v$ è un *discendente* di $u$ nell'albero `DFS`

![[attachements/Pasted image 20240413185236.png]]

![[attachements/Pasted image 20240413185322.png]]

###### Corollario
>[!abstract] Annidamento di nodi discendenti
>Un vertice $v$ è un ***discendente*** di un vertice $u$ in una *foresta depth-first* di un grafo $G\iff d[u]<d[v]<f[v]<f[u]$ 

>[!done] Dimostrazione Immediata dal teorema delle parentesi

##### Teorema del Cammino Bianco
>[!Teorema]
>In una *foresta* `DFS` di un grafo $G=(V,E)$, un vertice $v$ è un discendente di un vertice $u\iff$ al tempo $d[u]$ il vertice $v$ è raggiungibile da $u$ con un cammino contenente ***esclusivamente nodi bianchi***

#### Classificazione degli Archi
>*È possibile utilizzare la visita per classificare gli archi $(u,v)$ del grafo di input*

>[!done] Teorema
>In una `DFS` di un ***grafo non orientato*** $G$
>- Ogni arco di $G$ è un ***tree edge*** *oppure* un ***backwards edge***
##### Tree Edges
>[!info] Definizione
>$(u,v)$ è un ***tree edge*** se $v$ è stato *scoperto* esplorando l'arco $(u,v)$

##### Back Edges
>[!abstract] Definizione
>$(u,v)$ è un ***back edge*** se connette $u$ ad un antenato $v$ di un albero `DFS`
>>[!done] In termini di Colori
>>Se $color[v]=gray \implies$ $(u,v)$ è un ***Back Edge***  

##### Forward Edges
>[!tip] Definizione
>Un ***non-tree-edge*** $(u,v)$ che connette $u$ ad un discendente $v$
>- Visto anche come una "***shortcut***" nel cammino
>
>>[!done] In breve
>>Se $color[v]=black$ e $d[u]<f[v]\implies(u,v)$ è un ***Forward Edge***

##### Cross Edges
>[!tldr] Definizione
>***Tutti gli altri nodi*** che collegano o due `DFS` *tree* oppure due nodi che ***non sono antenati*** l'un l'altro
>>[!done] In breve
>>Se $color[v]=black$ e $d[u]>f[v]\implies (u,v)$ è un ***Cross Edge***