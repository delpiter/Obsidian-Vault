## Metodi Diretti
---
>[!info]
>In *assenza* di [[../Numeri Finiti/Errore di Rappresentazione|errori di arrotondamento]] conducono alla *soluzione esatta* in un numero ***finito di passi***.
>Adatti per la soluzione di sistemi con matrice dei coefficienti **densa** e di **moderate dimensioni**.

>[!caution] Matrice Densa
>Una matrice si dice ***densa*** se il numero di elementi $\neq 0$ è maggiore del $33\%$ di tutti gli elementi, altrimenti si dice ***sparsa***.

^6e46d3

I metodi diretti trasformano un *sistema lineare generico* in un *sistema lineare equivalente* dotato di una ***struttura che ne semplifica la risoluzione***.

### Fattorizzazione
>[!abstract] Obbiettivo
>L'obbiettivo della ***fattorizzazione*** $A=BC$ è quello di trasformare il sistema lineare $Ax=b$ in un sistema lineare *equivalente*.
>$$BCx=b$$
>Si può spezzare in due problemi:
>$$\begin{cases}By=b \\ Cx=y\end{cases}$$

>[[../../Algoritmi e Strutture Dati/Confronto fra Algoritmi/Complessità di Algoritmi|Complessità Algoritmo]] $O(n^3)\implies O(n^2)$

#### Metodi di Risoluzione
##### Metodo di Eliminazione Gaussiana
> Associato alla fattorizzazione $A=LU$

*Dove*:
- $L$ è triangolare inferiore con elementi diagonali $1$.
- $U$ triangolare superiore.

###### Fattorizzazione $LU$
>[!check] Teorema
>Data $A\in\mathbb{R}^{n\times n}$ sia $A_{k}$ la sottomatrice principale di testa di $A$ considerando le prime $k$ righe e colonne di $A$.
>Se $A_{k}$ [[Sistemi Lineari#Matrici Singolari|non è singolare]] per ogni $k=1,\dots,n-1$ allora esiste ed è unica la fattorizzazione $LU$ di $A$, dove:
>- $L$ è triangolare inferiore con elementi diagonali $1$.
>- $U$ triangolare superiore.


Utilizza il [[../../Algebra e Geometria/Risoluzione di Sistemi#Metodo di Gauss|metodo di Gauss]] per costruire $U$.
- La matrice $L$ si inizializza all'identità.

Per calcolare $L$
$$
k=1,\dots,n-1
\quad \begin{cases}
l_{ik}=\displaystyle\frac{a_{ik}}{a_{kk}} \quad i=k+1,\dots,n \\
a_{ij}=a_{ij}-l_{ik}a_{kj}
\end{cases}$$
>[!quote] A parole
>Ogni fattore usato nel metodo di gauss viene inserito come valore della matrice $L$.

>[!definizione] Matrice di Permutazione
>Matrice ottenuta dalla *matrice identità* **scambiando** due righe tra di loro.
>Effettuare $P\cdot A$ equivale a scambiare le stesse due righe della matrice $A$.

>[!check] Teorema
>Data una qualunque matrice $A$ non singolare, esiste una matrice di permutazione $P$ non singolare t.c. $PA=LU$

Dal punto di vista algoritmico porta all'algoritmo di ***Gauss con Pivotaggio***.
- Al passo $k$, prima di calcolare $l_{ik}$, se $a_{kk}=0$ si cerca dalla colonna $k$-*esima* a partire dalla riga $k$-*esima*, la posizione di riga $s$ in cui si trova il ***primo elemento diverso da zero***.

Sfruttando questo teorema la soluzione del sistema diventa:
$$
\begin{cases}
Ly=P\cdot b \\
Ux=y
\end{cases}
$$

###### Calcolo del Determinante con la Fattorizzazione
> Sia $PA=LU$ con $L$ matrice triangolare inferiore con elementi diagonali uguali a $1$:

$$
\det(PA)=\det(LU)=\underbrace{ \det(L) }_{ 1 }\det(U)=\det(U)=\prod_{i=1,\dots,n}u_{ii}
$$
Possiamo dire quindi:
$$
\det(PA)=\det(P)\det(A)=\prod_{i=1,\dots,n}u_{ii}
$$
***Ma sappiamo che***:
$$
\det(P)=(-1)^{s}
$$
- Dove $s$ è il numero di scambi effettuati.

>[!done] Conclusione
>Quindi $\det(A)=(-1)^{s}\prod_{i=1,\dots,n}u_{ii}$
##### Metodo di Cholesky
> Associato alla fattorizzazione $A=LL^T$ o $A=R^TR$

*Dove*:
- $L$ è [[#Matrici Triangolari|triangolare]] inferiore con elementi diagonali positivi.
- $R$ triangolare superiore con elementi diagonali positivi.

>[[../../Algebra e Geometria/Frome Bilineari e Prodotti Scalari/3 - Forme Quadratiche#Tipi di Forme Quadratiche|Definita positiva]].

###### Fattorizzazione di Cholesky
>[!check] Teorema di Cholesky
>Sia $A$ una matrice di ordine $n$ simmetrica e definita positiva.
><u>Allora</u>
>Esiste una matrice triangolare inferiore $L$ con elementi *diagonali positivi*. ($l_{ii}>0,i=1,\dots,n$) tale che:
>$$A=L\cdot L^T$$

Usando questo teorema la soluzione si riduce a:
$$
\begin{cases}
Ly=b \\
L^Tx=y
\end{cases}
$$

##### Metodo di Householder
> Associato alla fattorizzazione $QR$

>[!warning] La fattorizzazione è **sempre** possibile ma **non** unica.

###### Fattorizzazione $QR$
>[!check] Teorema
>Sia $A\in\mathbb{R}^{m\times n}$, con $m\geq n$ e $\text{rank}(A)=n$ (Le colonne sono [[../../Algebra e Geometria/Basi dell'algebra/2 - Campi e Spazi Vettoriali#Dipendenza Lineare|linearmente indipendenti]]).
><u>Allora</u>
>Esistono una matrice $Q\in\mathbb{R}^{m\times m}$ **ortogonale** e una matrice $R=\begin{pmatrix}R_{1} \\ 0\end{pmatrix}\in \mathbb{R}^{(m-n)\times n}$ dove $R_{1}\in\mathbb{R}^{n\times n}$, è una matrice triangolare superiore ***non singolare***, e $0\in \mathbb{R}^{(m-n)\times n}$ è una matrice di zeri tali che $A=QR$ 

Usando questo teorema la soluzione si riduce a:
$$
\begin{cases}
Qy=b \implies y=Q^Tb\\
Rx=y
\end{cases}
$$
#### Stabilità di un Algoritmo di Fattorizzazione
> Consideriamo la fattorizzazione $A=BC$

Consideriamo:
- $\mathcal{B}=B+\delta B$
- $\mathcal{C}=C+\delta C$

>I fattori $\mathcal{B},\mathcal{C}$ possono essere pensati come fattorizzazione esatta di una *matrice perturbata*.

$$
A+\delta A=\mathcal{B}\cdot\mathcal{C}
$$
Quindi
$$
A+\delta A=\underbrace{ (B+\delta B)\cdot(C+\delta C) }_{ BC+B\delta C+\delta BC+\delta B\delta C }
$$
>[!hint]
>La relazione evidenzia che la perturbazione $\delta A$ ***non dipende solo dalle perturbazioni*** $\delta B, \delta C$ ma è tanto più grande quanto sono più grandi gli elementi dei fattori $B$ e $C$.

>[!check] Stabilità di un Algoritmo di Fattorizzazione
>Data una matrice $A$ i cui elementi sono tutti minori o uguali a $1$, si dice che un *algoritmo di fattorizzazione* è ***numericamente stabile in senso forte***, se esistono delle costanti positive $a$ e $b$ indipendenti dall'ordine e dagli elementi di $A$ tali che:
>$$\mid b_{ij}\mid\leq a\quad \mid c_{ij}\mid\leq b$$

Se le costanti $a,b$ dipendono dall'ordine di $A$ si dice che la fattorizzazione è ***stabile in senso debole***.

- *Fattorizzazione di Gauss* -> Stabile in senso **debole** ($\mid u_{ij}\mid\leq 2^{n-1}\max\mid a_{ij}\mid$)
- *Fattorizzazione di Cholesky* -> Stabile in senso **forte** ($\max\limits_{ij}\mid l_{ij}\mid\leq\sqrt{ \max\limits_{ij}\mid a_{ij}\mid }$)
- *Fattorizzazione* $QR$ -> Stabile in senso **debole** ($\mid q_{ij}\mid\leq_{1} \mid r-_{ij}\mid\leq \sqrt{ n }\max\limits_{ij}\mid a_{ij}\mid$)
#### Matrici Triangolari
>Siano $L$ e $U$ matrici triangolari *inferiore* e *superiore*.

>[!check] Forward Substitution
>Soluzione del *sistema* $Lx=b$.

```pseudo
	\begin{algorithm}
	\caption{Forward Substitution}
	\begin{algorithmic}
	\For{$ i=1,2,\dots,n $}
  \State $ x_i=b_i $
  \For{$ j=1,2,1dots,i-1 $}
  \State $ x_i=x_i-l_{ij}\cdot x_j $
 \EndFor
 \State $ x_i=\displaystyle\frac{x_i}{l_{ii}} $
 \EndFor
	\end{algorithmic}
	\end{algorithm}
```

>[!abstract] Backwards Substitution
>Soluzione del *sistema* $Ux=b$.

```pseudo
	\begin{algorithm}
	\caption{Backwards Substitution}
	\begin{algorithmic}
	\For{$ i=n,n-1,\dots,1 $}
  \State $ x_i=b_i $
  \For{$ j=i+1,\dots,n $}
  \State $ x_i=x_i-u_{ij}\cdot x_j $
 \EndFor
 \State $ x_i=\displaystyle\frac{x_i}{u_{ii}} $
 \EndFor
	\end{algorithmic}
	\end{algorithm}
```

>[!summary] Complessità
> La complessità computazionale in termini di *operazioni moltiplicative* è:
> $$\sum_{i=1}^n i=\frac{n(n+1)}{2}\implies O(n^2)$$


## Metodi Iterativi
---
>[!info]
>Metodi che generano una successione di soluzioni che sotto opportune ipotesi, ***convergono alla soluzione***.
>Adatti per la soluzione di sistemi con matrice dei coefficienti di **grandi dimensioni** e [[#^6e46d3|sparsa]].

Si basano su una decomposizione della matrice $A$ e presentano una [[../../Algoritmi e Strutture Dati/Confronto fra Algoritmi/Complessità di Algoritmi|complessità]] di $O(kn^2)$, dove $k$ è il numero di iterazioni.

### Basati sulla Decomposizione
>[!check] Decomposizione
>Sia $A$ una matrice di ordine $n$ e sia dato il sistema $Ax=b$ con $\det A\neq 0$.
>Una famiglia di *metodi iterativi* per la soluzione del sistema lineare si ottiene utilizzando una ***decomposizione della matrice*** $A$ nella forma:
>$$A=M-N,\qquad \det M \neq 0$$
>In tal modo il sistema diventa
>$$(M-N)x=b\implies Mx=Nx +b$$
>>[!done] $x=M^{-1}Nx+M^{-1}b$

Questa formulazione suggerisce di considerare metodi iterativi le cui iterazioni siano fornite dalle iterazioni successive:
$$
x^{(k)}=M^{-1}Nx^{(k-1)}+M^{-1}b\quad k=1,2,\dots
$$
> Si parte da un vettore $x^{(0)}$ iniziale **arbitrario**, *stima iniziale della soluzione* del sistema.
- Si costruisce una successione di iterati $x^{(k)}$ *mediante il procedimento*.

$$
x^{(k)}=Tx^{(k-1)}+q\qquad k=1,2,\dots
$$
>Dove 
- $T=M^{-1}N$ è detta ***matrice di iterazione*** del metodo iterativo.
- $q=M^{-1}b$

>[!hint]
>I metodi di questa forma sono detti ***iterativi stazionari*** perché $T$ e $q$ non dipendono dall'indice di iterazione $k$

#### Esempi
>[!example] Metodi
>1. ***Metodo di Jacobi*** (Metodo degli spostamenti simultanei)
>2. ***Metodo di Gauss-Seidel*** (Metodo degli spostamenti successivi)

In entrambi i metodi si considera la matrice $A$ del sistema decomposta come somma di 3 matrici:
$$
A=D+E+F
$$
Con:
$$
D=\begin{bmatrix}
a_{11} &  \\
 & \ddots \\
&  & a_{nn}
\end{bmatrix},
E=\begin{bmatrix}
0 & 0 & \dots & 0 & 0 \\
a_{21} & 0  & \dots & 0 & 0\\
a_{31} &  a_{32} &  \ddots & 0 & 0 \\
\vdots  & \vdots & \ddots & \ddots & \vdots\\
a_{n1} & a_{n2} &  \dots& a_{nn-1} & 0
\end{bmatrix},
F=\begin{bmatrix}
0 & a_{12} & a_{13} & \dots & a_{1n} \\
0 & 0 & a_{23} & \dots & a_{2n} \\
\vdots & \vdots & \ddots & \ddots & \vdots \\
0 & 0 & 0 & \ddots & a_{n-1n} \\
0 & 0 & 0 & \dots & 0
\end{bmatrix}
$$

E si suppone che $a_{ii}\neq 0\quad i=1,2,\dots,n$

##### Metodo di Jacobi
>[!tldr] Idea
>Nel ***metodo di Jacobi*** la decomposizione di $A$ nella forma $A=M-N$ si ottiene scegliendo $M=D$ e $N=-(E+F)$

Il procedimento iterativo diventa:
$$
x^{(k)}=-D^{-1}(E+F)x^{(k-1)}+D^{-1}b_{1}\quad k=1,2,\dots
$$

> In termini di componenti l'equazione equivale a calcolare la $i$-esima componente dell'iterato $k$-esimo:

$$
x_{i}^{(k)}=\displaystyle{\frac{-\displaystyle\sum^n_{j=1,\ j\neq i}a_{ij}x^{(k-1)}_{j}+b_{i}}{a_{ii}}},\quad i=1,2,\dots,n
$$

Dato che la matrice $D^{-1}$ è una [[../../Algebra e Geometria/Applicazioni/9 - Matrici Diagonali|matrice diagonale]]:
- La ***matrice di iterazione*** del metodo di *Jacobi* è data da:

$$
T_{J}=M^{-1}N=-D^{-1}(E+F)
$$

>[!hint] Osservazioni
>1. L'algoritmo di Jacobi è definito se gli elementi diagonali di $A$ sono diversi da $0$
>
>In caso contrario (Sotto l'ipotesi che $A$ non sia [[Sistemi Lineari#Matrici Singolari|singolare]]) si possono ***riordinare*** le equazioni e le incognite del sistema in modo da rendere il metodo definito.
>
>2. Nel metodo ogni elemento dell'iterato $(k)$ è ***indipendente dagli altri***.
>
>Il metodo è programmabile in ***forma parallela***.

##### Metodo di Gauss-Seidel
>[!tldr] Idea
>Nel ***metodo di Gauss-Seidel*** la *decomposizione* di $A$ si ottiene scegliendo $M=E+D$ e $N=-F$
>La matrice di iterazione del metodo è data da:
>$$T_{G}=M^{-1}N=-(E+D)^{-1}F$$

La soluzione al passo $k$ si ottiene come:
$$
x^{(k)}=-(E+D)^{-1}Fx^{(k-1)}+(E+D)^{-1}b\quad k=1,2,\dots
$$
> Per esprimere la soluzione in termini di componenti partiamo da:

$$Mx^{(k)}=Nx^{(k-1)}+b$$

Sostituendo ad $M$ la matrice $E+D$ e ad $N$ la matrice $-F$, otteniamo:
$$
\begin{array}
\ (E + D)\,x^{(k)} = -F\,x^{(k-1)} + b \qquad k = 1, 2, \dots \\
D\,x^{(k)} = -E\,x^{(k)} - F\,x^{(k-1)} + b \\
x^{(k)} = D^{-1}(-E\,x^{(k)} - F\,x^{(k-1)} + b) \\
\end{array}
$$
E in termini di componenti:
$$
x_i^{(k)} = \frac{\displaystyle-\sum_{j=1}^{i-1} a_{ij} x_j^{(k)} 
- \sum_{j=i+1}^{n} a_{ij} x_j^{(k-1)} + b_i}{a_{ii}}
\quad \text{per } i = 1, 2, \ldots, n
$$


>[!caution] Caratteristica
>Usa, per calcolare la ***nuova componente*** $i$-esima di un *iterato* le *componenti già calcolate* dell'iterato stesso.

>[!hint] Osservazione
>Il metodo non si presta ad essere [[../../Architettura degli Elaboratori/Architetture a Confronto/Architetture Parallele|parallelizzato]] in quanto ogni nuovo componente dell'iterato *dipende* da tutte le nuove componenti appena calcolate.

Il metodo suggerisce che la **soluzione** al passo $k$ si *ottiene*:
- Risolvendo il sistema ***triangolare inferiore*** avente $(D+E)$ come matrici dei coefficienti e termine noto $b-Fx^{(k-1)}$.

#### Convergenza
>[!definizione]
>Un procedimento iterativo si dice [[../../Analisi/Successioni/Limiti di Successioni#Definizioni|convergente]] se, per ogni vettore iniziale $x_{0}$ la successione $\{ x_{k} \}$ converge ad un vettore limite $y$
>$$\lim\limits_{k\to \infty }x_{k}=y$$

>[!check] Teorema
>Il sistema $Ax=b$ con $\det A\neq 0$ ammette un'unica soluzione $x$ e se il processo iterativo è ***convergente***, allora il valore limite $y$ **coincide** con la soluzione $x$.

##### Dimostrazione
>Partendo da:

Consideriamo il limite $k\to \infty$ di entrambi i membri.
$$
\lim\limits_{k\to \infty}Mx^{(k)}=\lim\limits_{k\to \infty}(Nx^{(k-1)}+b)
$$
Poiché $x^{(k)}$ è per ipotesi una successione convergente a $y$ segue che
$$
My=Ny+b
$$
- Da cui si ottiene $(M-N)y=b$

Essendo $M-N=A$, si ha $Ay=b$ e quindi $y=x$
- Per ipotesi $Ax=b$ ha un'unica soluzione $x$.

##### Convergenza dei metodi Iterativi
> Consideriamo la matrice di iterazione $T$

**Definiamo**:
- L'errore commesso al passo $k$ come il vettore $e^{(k)}=x^{(k)}-x$
- Il vettore residuo al passo $k$: $r^{(k)}=Ax^{(k)}-b$

>[!hint] Osservazione
>Si osservi che queste quantità sono legate dalla relazione:
>$$r^{(k)}=Ax^{(k)}-b=Ax^{(k)}-Ax=A(x^{(k)}-x)=Ae^{(k)}$$

Consideriamo la relazione relativa al valore esatto $x$: $Mx=Nx+b$ e la relazione analoga al passo $k:$ $Mx^{(k)}=Nx^{(k-1)}+b$

> Sottraendo la prima dalla seconda otteniamo: $Me^{(k)}=Ne^{(k-1)}$ da cui:

$$
e^{(k)}=M^{-1}Ne^{(k-1)}=Te^{(k-1)}=T^2e^{(k-2)}=\dots=T^k
e^{(0)}$$

>[!done] Metodo convergente
>Affinché il *procedimento sia convergente* si deve avere che, qualunque sia $x^{(0)}$ ciascuna componente del vettore $e^{(k)}$ tenda a $0$ per $k\to \infty$

#### Teorema di Convergenza
>[!check] Condizione Necessaria e Sufficiente alla convergenza
>Sia $A=M-N$ una matrice di ordine $n$, con $\det A\neq 0$, e $T=M^{-1}N$ la [[#Basati sulla Decomposizione|matrice di iterazione]] del procedimento *iterativo*.
>La condizione ***necessaria e sufficiente*** per la *convergenza* del procedimento iterativo, comunque si scelga il vettore iniziale $x^{(0)}$, al vettore soluzione $x$ del sistema $Ax=b$ , è che:
>$$\rho(T)<1$$
>>[!quote] A parole
>>Il [[../Norma#Norme Indotte dalle Norme più Comuni|raggio spettrale]] della matrice di iterazione $T$ sia minore di $1$.

> Consideriamo ora condizioni più restrittive.

>[!check] Teorema Condizione sufficiente alla Convergenza
>Se per una qualche [[../Norma|norma]] risulta $\| T\| < 1$, allora il *processo iterativo*:
>$$x^{(k)}=Tx^{(k-1)}+M^{-1}b\qquad k=1,2,\dots$$
>È convergente per ogni $x^{(0)}$.
##### Dimostrazione
> Dalla definizione di [[../../Algebra e Geometria/Applicazioni/9 - Matrici Diagonali#Autovettore e Autovalore|autovalore]] di una matrice si ha $Tx=\lambda x$, con $x\neq 0$.

Da cui si può ottenere $|\lambda| \|x\| =\|Tx\|\leq\|T\|\|x\|$
- Quindi $\mid\lambda\mid\leq \|T\|$

>[!quote] Cioè
> Il modulo di ogni ***autovalore*** della matrice $T$ è minore o uguale della ***norma*** della matrice $T$.

Per ipotesi si ha $\|T\|\leq1$
Quindi:
$$
|\lambda|\leq\|T\|<1
$$
Da cui: $\rho(T)<1$ e, per il teorema precedente il ***procedimento iterativo è convergente***.

> Seguono due teoremi che garantiscono la convergenza per classi particolari di matrici

>[!check] Teorema
>Se la matrice $A$ è ***diagonale strettamente dominante***:
>$$\mid a_{ii}\mid>\sum_{k=1, \ k\neq i}^n|a_{ik}| \qquad i=1,2,\dots,n$$
>>[!quote] Cioè
>>Ciascun elemento nella diagonale è *maggiore* della **somma dei restanti elementi** della riga.
>
>Allora sia il metodo di *Jacobi* che quello di *Gauss-Seidel* convergono e si ha 
>$$\|T_{G}\|\leq\|T_{J}\|< 1$$

>[!tip] Teorema
>Se la matrice $A$ è simmetrica e definita positiva il *metodo di Gauss-Seidel* è convergente.
#### Velocità di Convergenza
> Abbiamo visto che $e^{(k)}=T^ke^{(0)}$

Quindi $\|e^{(k)}\|\leq \|T\|^k\| e^{(0)}\|$

>[!cite] Si può dimostrare che:
>Per $k$ grande:
>$$\|e^{(k)}\|\approx C\rho(T)^k \cdot \|e^{(0)}\|$$
>Dove $C$ è una opportuna costante maggiore di zero.
>Da cui segue:
>$$\displaystyle{\frac{\|e^{(k+1)}\| }{\|e^{(k)}\|}} \approx \rho(T)$$

Si tratta di ***metodi iterativi a convergenza lineare*** e $\rho(T)$ è il *fattore costante* che descrive quanto l’errore si riduce se $\rho(T)<1$ (o *cresce* in caso contrario) a ogni passo, quando il metodo si stabilizza (per $k$ grande).

>[!abstract] Osservazione
>Un metodo tanto è ***più velocemente convergente*** quanto più *piccolo* è l'***autovalore di modulo massimo*** della matrice di iterazione $T$.


##### Mal Condizionamento
> Il condizionamento di $A$ è responsabile del rallentamento o perdita della convergenza nei *metodi iterativi*.

Essendo la matrice di iterazione $T$ calcolata a partire da una ***matrice mal condizionata*** $T$ può avere autovalore massimo molto vicino a $1$ o $>1$.

#### Accelerazione di un Metodo Iterativo
>[!help] Metodo di Rilassamento
>Poiché la ***velocità di convergenza*** di un metodo *iterativo* dipende dal **raggio spettrale** della matrice di iterazione $T$, un modo per *accelerare la convergenza* è quello di far dipendere la matrice di iterazione da un **parametro**, detto ***parametro di rilassamento***, e di scegliere tale parametro in modo tale che la matrice abbia *minimo raggio spettrale*.

>Vediamo come generare un metodo di rilassamento a partire dal [[#Metodo di Gauss-Seidel]].

$$
x^{(k)} = -D^{-1}(E\,x^{(k)} + F\,x^{(k-1)} - b)
$$
Può essere riscritto nella forma:
- $x^{(k)}=x^{(k-1)}+r^{(k)}$

*Dove* (1)
$$
r^{(k)}=x^{(k)}-x^{(k-1)}=-D^{-1}[Ex^{(k)}+Fx^{(k-1)}-b]-x^{(k-1)}
$$
Modificando il *metodo di Gauss-Seidel* come (2):
$$
x^{(k)}=x^{(k-1)}+\omega r^{(k)}
$$
>[!hint]
>Scegliendo opportunamente il parametro $\omega>0$ si può ***accelerare la convergenza in modo significativo***.

> A seconda di come viene scelto tale parametro si distinguono i metodi di rilassamento.

>[!abstract] Under-Relaxation
>Con $0<\omega<1$.
>I metodi di ***under-relaxation*** possono essere usati per *ottenere convergenza* su certi sistemi per cui **non** si ha convergenza con il metodo di *Gauss-Seidel*.

>[!tip] Over-Relaxation
>Con $\omega>1$.
>I metodi di ***over-relaxation*** possono essere usati per *accelerare la convergenza* in sistemi in cui il metodo di *Gauss-Seidel* converge ma **lentamente**.

Questi metodi vengono chiamati metodi di ***Successive Over-Relaxation*** e vengono impiegati per risolvere sistemi lineari.

Il metodo **SOR** si ottiene sostituendo (1) con (2):
$$
x^{(k)} = (1 - \omega)x^{(k-1)} - \omega D^{-1}[E x^{(k)} + F x^{(k-1)} - b]
$$
Da cui si ricava:
$$
x^{(k)} = (1 - \omega)x^{(k-1)} + \omega[-D^{-1}[E x^{(k)} + F x^{(k-1)} - b]]
$$

> In termini di componenti si ha che la componente $i$-esima della soluzione al passo $k$, $x_{i}^{(k)}$ diventa:

$$
x_i^{(k)} = (1 - \omega)x_i^{(k-1)} + \frac{\omega}{a_{ii}} \left[
b_i - \sum_{j=1}^{i-1} a_{ij} x_j^{(k)} - \sum_{j=i+1}^{n} a_{ij} x_j^{(k-1)}
\right] \qquad i = 1, 2, \dots, n
$$
Questa variante dipende dal parametro $\omega$ ed è detta metodo di ***Gauss-Seidel Estrapolato***.
$$
\begin{cases}
\displaystyle \tilde{x}_i^{(k)} = \frac{1}{a_{ii}} \left[
b_i - \sum_{j=1}^{i-1} a_{ij} x_j^{(k)} - \sum_{j=i+1}^{n} a_{ij} x_j^{(k-1)}
\right] \\
\displaystyle x_i^{(k)} = (1 - \omega)x_i^{(k-1)} + \omega \tilde{x}_i^{(k)}
\end{cases}
$$

>La matrice di iterazione del metodo è:

$$
T_\omega = (D + \omega E)^{-1} \left[(1 - \omega)D - \omega F \right].
$$
È noto che per matrici simmetriche definite positive e per $0<\omega<2$ il valore di $\rho(T_{\omega})$ si mantiene $<1$.
- Ma c'è un punto in cui è minimo

![[attachements/RelaxationMethods.png]]

>[!caution] Calcolo
>Il calcolo di $\omega_{\text{ottimo}}$ è molto complesso, per cui si suole andare per ***tentativi***.

#### Criterio d'Arresto
>Occorre individuare dei [[../Equazioni non Lineari/Criteri di Arresto|criteri di arresto]] del procedimento.

I criteri più comunemente usati, che consistono nel fissare una tolleranza $\varepsilon$ che tiene conto della ***precisione*** utilizzata nei calcoli, sono i seguenti:
$$
\|x^{(k)}-x^{(k-1)}\|\leq\varepsilon
$$
Oppure:
$$
\displaystyle{\frac{\|x^{(k)}-x^{(k-1)}\|}{\|x^{(k)}\|}}\leq \varepsilon
$$
La scelta della tolleranza $\varepsilon$ nel ***criterio d’arresto*** viene fatta considerando la *percentuale d’errore* da cui sono affetti i *dati iniziali*.
La scelta del tipo di [[../Norma|norma]], dipende dallo specifico problema in esame; 
- *Norme comunemente usate* sono la norma $\infty$ e la norma $2$.


