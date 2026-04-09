## $h(x)$
---
>[!info] Descrizione
>La *funzione di hash* è il gestore della posizione della [[Hash Table]]
>La funzione hash $h$ prende in `input` una ***chiave*** e *restituisce* un valore compreso tra $0$ e $m-1$
>Si utilizza un vettore $T$ di *puntatori* con $m$ posizioni indicizzate
>L'elemento $x$ con chiave $x.key$ viene *memorizzato* in $T$ in posizione $h(x.key)$
![[attachements/Screenshot_2024-03-17_164254-removebg-preview.png]]

- Nelle [[Hash Table#Direct Address Table|direct access table]] la funzione di hash è semplicemente la [[../../../Analisi/Funzioni/Introduzione Funzioni#Funzione Identità|funzione identità]]
	- $h(x) = x$

### Collisioni
>[!info] Definizione
>Siano $x$ e $y$ due valori da passare alla funzione *hash* $h$
>$x$ e $y$ generano una ***collisione*** se
>$$x\neq y \text{ e } h(x) = h(y)$$ 

La funzione di hash deve cercare di minimizzare le collisioni

>[!abstract] Obbiettivi contrastanti

La *funzione hash* ha due obbiettivi contrastanti:
1. Comportarsi come una ***funzione casuale***
	- *Minimizza le collisioni*, quando inevitabile, appaiono in maniera *omogenea*
2. Essere ***deterministica***
	- Il processo di **hashing** deve essere *ripetibile*
	- Stesso `input` $\to$ stesso `output`

#### Frequenza delle collisioni
>[!tip] Sia $T$ una tabella di dimensione $m$ e $p$ il numero di elementi da inserire

La *funzione hash* ha $m^p$ diverse possibilità di allocazione dei $p$ elementi
- Con $p=8$ e $m=10$ ci sono $10^8$ possibili allocazioni diverse

Ci sono $\displaystyle{\frac{m!}{(m-p)!}}$ **possibilità** di un *hashing senza collisioni*

La probabilità di collisione *cresce in modo sorprendente*

## Tecniche di Gestione di Collisioni
---
### Chaining
>[!info] Risoluzione di collisioni con "***chaining***"
>Si crea una [[../Linked Lists|lista]] per ogni cella della tabella (valori assumibili dalla funzione $h$)
>Si collegano i *record* afferenti a una *stessa cella* nella sua lista
>Le celle della tabella sono le *teste delle liste* (`NULL` se liste vuote)

![[attachements/Pasted image 20240317170426.png]]
#### Analisi della Complessità
>[!info] Load Factor
>Il *Load Factor* è una misura di quanto la tabella è piena
>- $n$ Numero di elementi memorizzati nella tabella
>- $m$ Dimensione della tabella
>$$\text{ Load Factor }\to \alpha = \frac{n}{m}$$
>

>[!fail] Caso Pessimo
>>Tutte le $n$ *chiavi* finiscono nella **stessa posizione**
>>- Ricerca: $\Theta(n)$


>[!caution] Caso Medio
>>***Simple Uniform Hashing***
>>La funzione di hash $h$ *suggerisce* una cella del vettore con una ***stessa probabilità*** di un'altra

##### Simple Uniform Hashing
>[!info] Definizione
>Sia $n$ una *funzione hash*
>Diciamo che $h$ è uniforme se per ogni chiave $k$ e per ogni coppia di indici $i,j$ della tabella $T$ vale la relazione:
>$$(\text{Probabilita}[h(k)=i])=(\text{Probabilita}[h(k)=j])$$

>[!tip] $h$ Semplice Uniforme
>Una *funzione hash* si dice ***semplice uniforme*** quando rende **uniforme** il *riempimento* della tabella

###### Complessità SUH
>[!check]
>Siano le collisioni ***gestite con chaining***
>Sia la funzione di hash ***Semplice Uniforme***
><u>Allora</u>
>Una ricerca ha [[../../Confronto fra Algoritmi/Complessità di Algoritmi#Analisi di Complessità|costo computazionale]] di $\Theta(1+\alpha)$
>Dove $1$ è il costo della funzione $h$ e $\alpha$ è il ***load factor***

>[!hint] Dimostrazione
>Caso di ricerca ***senza Successo***

Il *Load Factor* $\alpha$ è la lunghezza media di una *catena*
- In una ricerca **senza successo** il numero di *elementi esaminati* è uguale alla ***lunghezza media*** delle catene
$$
\frac{n}{m}=\alpha
$$
Dato che calcolare $h()$ costa $\Theta(1)$

La ricerca costerà
$$
\Theta(1)+\Theta(\alpha) = \Theta(1+\alpha)
$$

>[!hint] Dimostrazione
>Caso di ricerca ***con Successo***

Assumiamo di inserire elementi in *coda alla catena*
- Per ipotesi il numero medio di elementi in una catena dopo $i$ inserimenti è
$$
\frac{i}{m}
$$
L'elemento $i$ verrà inserito *mediamente* nella posizione $1+\displaystyle{\frac{(i-1)}{m}}$ all'interno di una catena

Un elemento generico finirà in media nella posizione data dalla formula:
$$
\frac{1}{n}\sum_{i=1}^n \left( 1+\displaystyle{\frac{(i-1)}{m}} \right)
$$
Scomponiamo la sommatoria:
$$
\begin{array}
\ \underbrace{ \displaystyle\sum_{i=1}^n 1 }_{ n } + \displaystyle\sum_{i=1}^n \frac{i}{m} - \underbrace{ \displaystyle\sum_{i=1}^n \frac{1}{m} }_{ \frac{n}{m} } \\
n+\displaystyle\frac{1}{m}\displaystyle\sum_{i=1}^ni - \frac{n}{m} \\
n+\displaystyle\frac{1}{m}\cdot \displaystyle{\frac{n(n+1)}{2}} - \frac{n}{m} 
\end{array}
$$

Ora torniamo alla funzione originale
$$
\frac{1}{n}\left( n+\displaystyle{\frac{n(n+1)}{2m}}-\frac{n}{m} \right)=
$$
$$
1+\displaystyle{\frac{(n+1)}{2m}}-\displaystyle{\frac{2}{2m}}=
$$
$$
1+\displaystyle{\frac{n-1}{2m}}=
$$
$$
1+\underbrace{ \frac{n}{2m} }_{ \alpha/2 }-\frac{1}{2m}=\Theta(1+\alpha)
$$
>[!done] Conclusione

Supponiamo che $n=O(m)$
- Ovvero che il numero di **elementi** inseriti nella tabella sia *proporzionale alla dimensione* della tabella stessa
$$
\alpha = \frac{n}{m} =\frac{O(m)}{m} = O(1)
$$
In questo caso la ricerca impiega ***tempo costante***!

Se usiamo le [[../Linked Lists#Doubly Linked List|doubly linked lists]] per le catene e se inseriamo in testa alle liste i nuovi elementi abbiamo che:
- Ricerca
- Cancellazione
- Inserimento
Fanno in media $O(1)$ operazioni

###### Progettazioni Funzioni Hash
>[!hint] Progettazione
>Siano $Pr(k)=$ Probabilità della chiave $k$
>$S_{j}=\{ k\in U :h(k)=j\}$
>Vogliamo ***uniform hashing*** ovvero:
>$$\sum_{k\in S_{i}}Pr(k)=\frac{1}{m}$$
>Con $m =$ Dimensione della tabella

Se $Pr()$ è sconosciuta:
- Si utilizzano [[../../../Definizioni/Definizioni_Algoritmi#Algoritmi Euristici|Algoritmi Euristici]]

>[!abstract] Metodo della Divisione
>$$h(k)=k mod(m)$$

>[!abstract] Metodo della Moltiplicazione
>$$h(k)=\lfloor m(kA mod1)\rfloor$$
>Passaggi:
>1. Scegli una costante $A$ con $0<A<1$
>2. Calcola $k\cdot A$
>3. Prendi la parte frazionaria: $k\cdot A-\lfloor k\cdot A\rfloor$
>4. Moltiplica il risultato per $m$
>5. Prendi la parte intera
>La chiave $k$ è mappata in $\lfloor(m\cdot(k\cdot A-\lfloor k\cdot A\rfloor))\rfloor$

Costante $A$ ottimale:
- $(5^{\frac{1}{2}}-1)/2 = 0.618\dots$

### Open Addressing
>[!info] Risoluzione di Collisioni con Open Addressing
>Nell'***open addressing*** la tabella è *dimensionata* in accordo con il numero di dati da inserire
>A contrario del *chaining* è possibile **finire lo spazio** a disposizione
>L'hash function $h$ è più complessa, prende come parametri la *chiave* e il ***numero di collisioni già avvenute***

#### Uniform Hashing
>[!info] Funzione Hash
>La gestione di collisioni con il metodo ***open addressing*** richiede che per ogni chiave $k$, la sequenza di [[../../../Definizioni/Definizioni_Algoritmi#Probe|probe]] $<h(k,0),\dots,h(k,m-1)>$ deve essere una permutazione degli indici $<1,\dots,m>$ tali che ogni posizione della ***tabella hash*** è **prima o poi** considerata come uno *slot per una nuova chiave*

#### Open Addressing - Ricerca
>[!check]
>Sia $n$ il numero di celle occupate e $m$ il numero totale di celle
>Data una *hash table* con *open addressing* e load factor $\alpha=\displaystyle\frac{n}{m}<1$
>La lunghezza **media** di una [[../../../Definizioni/Definizioni_Algoritmi#Probe|probe]] in una *ricerca senza successo* è di $\displaystyle{\frac{1}{(1-\alpha)}}$
>- Assumendo una ***permutazione uniforme di indici***

##### Dimostrazione
>*Sia* $x$ *il numero di accessi necessari prima di trovare una cella vuota (probe)*

Dobbiamo valutare $E[x]$, la media di tutte le possibili $x$

Posso calcolare la *media* di valori facendo:
-  La somma di ***valori assumibili*** moltiplicata per la ***probabilità*** con cui viene *assunto* il valore
$$
\begin{array}
\ A=\{ 3,6,1,3,9,6,8,5,5 \} \\
\text{ Average }=1\cdot \frac{1}{9} + 2\cdot0+2\cdot \frac{2}{9}+4\cdot0+5\cdot \frac{2}{9}+6\cdot \frac{2}{9} +7\cdot 0+8\cdot\frac{1}{9} +9\cdot \frac{1}{9}= \\
\displaystyle\sum_{i=0}^{+\infty}i\cdot p_{i}
\end{array}
$$
- $p_{i} \to$ *probabilità* di assunzione del valore
- $i\to$ *numero* di *accessi*
$$
x=\begin{cases}
0\to p_{0} \\
1\to p_{1} \\
\dots \\
i\to p_{i} \\
\dots
\end{cases}
$$ 
>[!warning] Nota
>$$p_{i}=0,\forall i>n$$
>La probabilità che un numero ***fuori dall'insieme*** venga estratto è uguale a $0$

$$
\begin{array}
\ \displaystyle\sum_{i=0}^{+\infty}i\cdot p_{i}=\displaystyle\sum_{i=0}^{+\infty}i\cdot p(x=i)= \\
\end{array}
$$
- Posso sostituire la *probabilità* che venga assunto un valore $=i$ con:
	- La *differenza fra la probabilità* che venga assunto un valore $\geq i$ e la *probabilità* che venga assunto un valore $\geq i+1$

$$
\begin{array}
\ \displaystyle\sum_{i=0}^{+\infty} i(p(x\geq i)-p(x\geq i+1)) = 1P_{1}\underbrace{ -1P_{2}+2P_{2} }_{ +P_{2} }\underbrace{ -2P_{3}+3P_{3} }_{ +P_{3} }+\dots= \\
\displaystyle\sum_{i=1}^{+\infty} p(x\geq i)

\end{array}
$$
Notare che ora la sommatoria non ha più il *fattore $i$ moltiplicato*
- Ora basta ricondursi a una delle [[../../Confronto fra Algoritmi/Confronto e Pseudocodice#Sommatorie utilizzate|sommatorie conosciute]]

Sappiamo che la ***probabilità di fare almeno un accesso*** è:
$$
p_{1}=\frac{n}{m}
$$
Quindi, di *conseguenza*:
$$
\begin{array}
\ p_{2}(\text{1 cella occupata}) = \displaystyle\frac{n}{m}\cdot \displaystyle{\frac{n-1}{m-1}}< \left( \frac{n}{m} \right)^2 \\
\dots \\
p_{i}(\text{i-1 celle occupate})=\displaystyle\frac{n}{m}\cdot ... \cdot \displaystyle{\frac{n-(i-1)}{m-(i-1)}} < \left( \frac{n}{m} \right)^i
\end{array}
$$

- Ci siamo ricondotti a una ***sommatoria conosciuta***:
$$
E[x]=\sum_{i=1}^{+\infty}p(x\geq i)\leq\sum_{i=1}^{+\infty}\left( \frac{n}{m} \right)^i=\sum_{i=1}^{+\infty}\alpha^i
$$

>[!done] Conclusione

Il costo per la ricerca *senza successo* sarà:
- Il valore appena calcolato $+1$ 
	- Che rappresenta ***l'accesso necessario*** per trovare una *cella vuota*

$$
1+E [x]\leq \displaystyle{\frac{1}{1-\alpha}}
$$

#### Open Addressing - Inserimento
>[!check]
>Data una *hash table* con *open addressing* e **load factor** $\alpha=\frac{n}{m}<1$
>La lunghezza media di una [[../../../Definizioni/Definizioni_Algoritmi#Probe|probe]] è $\frac{1}{1-\alpha}$
>- Assumendo una ***permutazione uniforme degli indici***

##### Dimostrazione
Per inserire un elemento abbiamo bisogno di *determinare la posizione* nella tabella ***dove inserirlo***
- *Costo della ricerca*: $\displaystyle{\frac{1}{1-\alpha}}$


#### Pseudocodici
```pseudo
	\begin{algorithm}
	\caption{Insert}
	\begin{algorithmic}
\Procedure{HashInsert}{$ T,k $}
\State $ i=0 $
\Repeat
	
\State $ j= $\Call{h}{k,i} 
	\If{$ T[j]=null \text{ OR } T[j]='d' $}
  \State $ T[j]=k $
  \Return $ j $
  \Else 
 \State $ i=i+1 $
 \EndIf
\Until{i=m}
\State $ \text{"error hash table overflow"} $	
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```

```pseudo
	\begin{algorithm}
	\caption{Search}
	\begin{algorithmic}
\Procedure{HashSearch}{$ T,k $}
\State $ i=0 $
\Repeat
\State $ j= $	\Call{h}{$k,i$}
	\If{$ T[j]=k  $}
	\Return $ j $
	\Else 
 \State $ i=i+1 $
  
 \EndIf
\Until{$T[j]==null \text{ OR } i==m$}
	\Return $ null $
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```

```pseudo
	\begin{algorithm}
	\caption{Delete}
	\begin{algorithmic}
\Procedure{HashDelete}{$ T,k $}
\State $ i= $ \Call{HashSearch}{T,k}
\If{$ i\neq null  $}
  \State $ T[i]='d' $
 \EndIf
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```

#### Linear Probing
>[!info] Descrizione
>Il ***linear probing*** è un caso speciale di *double hashing*.
>È l'approccio ***open-addressing*** più semplice di risolvere le *collisioni*
>>[!abstract] Funzionamento
>>Nel caso del ***linear probing*** una funzione di hash ausiliaria $h_{1}$ determina la prima posizione della **[[../../../Definizioni/Definizioni_Algoritmi#Probe|probe]]** $h_{1}(k)$ per l'inserimento di un elemento.
>>Se lo slot $T[h_{1}(k)]$ è già *occupato*, la prossima posizione da controllare sarà: $T[h_{1}(k)+1]$
>>Continua il processo fino a che non si ***trova una cella libera***

>[!done] Funzione di hash $h$
$$
h(k,i)=(k_{1}(k)+i)\text{ mod }m
$$
##### Analisi del linear probing
>Il *linear probing* è spesso implementato, ma esibisce un fenomeno chiamato ***primary clustering***

>[!info] Primary Clustering
>Il **primary clustering** è una lunga sequenza di slot occupati, che ***aumentano il tempo medio di ricerca***

- Questo accade perché uno *slot vuoto* **preceduto** da $i$ *slot pieni* viene successivamente riempito con una ***probabilità*** di $\frac{i+1}{m}$ 
- Una lunga *sequenza di slot occupati* tende a diventare ***sempre più lunga***

![[attachements/primary clustering.png]]
###### Semi-Soluzione
>[!info] Quadratic Probing
>Ad ogni *collisione* l'indice $i$ si altera in ***maniera quadratica***
>$$h(k,i)=(h_{1}(k)+c_{1}i+c_{2}i^2)\text{ mod }m$$


![[attachements/Screenshot 2024-03-22 163714.png]]
>[!fail] Il problema persiste

Due chiavi che vanno in collisione con $h_{1}(k,0)$ andranno in *collisione* ad ogni ***passaggio/iterazione***

#### Double Hashing
>[!info] Descrizione
>Nel double hashing **accodo** alla ***prima funzione*** di *hash semplice* $h_{1}$ una ***seconda funzione*** di *hash semplice* $h_{2}$ diversa in modo di *abbassare* drasticamente le ***collisioni in catena***

>[!done] Funzione di double hashing $h$

$$
h(k,i)=(h_{1}(k)+ih_{2}(k))\text{ mod }m
$$