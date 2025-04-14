## Metodi Diretti
---
>[!info]
>In *assenza* di [[Errore di Rappresentazione|errori di arrotondamento]] conducono alla *soluzione esatta* in un numero ***finito di passi***.
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

>[[Complessità di Algoritmi|Complessità Algoritmo]] $O(n^3)\implies O(n^2)$

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


Utilizza il [[Risoluzione di Sistemi#Metodo di Gauss|metodo di Gauss]] per costruire $U$.
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
>Effettuare $P\cdot A$ equivale a scambiare le stesse due righe della matrice $A$

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
##### Metodo di Cholesky
> Associato alla fattorizzazione $A=LL^T$ o $A=R^TR$

*Dove*:
- $L$ è [[#Matrici Triangolari|triangolare]] inferiore con elementi diagonali positivi.
- $R$ triangolare superiore con elementi diagonali positivi.

>[!warning] Solo per matrici simmetriche e [[3 - Forme Quadratiche#Tipi di Forme Quadratiche|definita positiva]].

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

*Dove*:
- $Q$ è [[1 - Introduzione Isometrie#Matrice Ortogonale|ortogonale]] e $R$ è triangolare superiore.

>[!warning] La fattorizzazione è **sempre** possibile ma **non** unica.

###### Fattorizzazione $QR$
>[!check] Teorema
>Sia $A\in\mathbb{R}^{m\times n}$, con $m\geq n$ e $\text{rank}(A)=n$ (Le colonne sono [[2 - Campi e Spazi Vettoriali#Dipendenza Lineare|linearmente indipendenti]]).
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
