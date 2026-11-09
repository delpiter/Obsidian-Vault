## Matrici Nilpotenti
---
>[!info] Definizione
>Un [[4 - Isomorfismo#Endomorfismo|endomorfismo]] di $V$ è ***nilpotente*** se:
>$$\exists n>0,n\in \mathbb{N}:f^n = 0$$
>Dove $f^n=(\underbrace{ f_{o}f_{o}\dots_{o}f(v) }_{ n \text{ volte} }), \forall v \in V$
>>[!done] In altre parole
>>Diciamo che $f$ e la sua matrice $A$ sono "***nilpotenti***" se una *potenza* di $A$ o $f$ porterà prima o poi al ***vettore nullo***

#### Esempio
>*Sia $f:\mathbb{R}^4\to \mathbb{R}^4, f(x,y,z,w)=(y,z,w,0)$*

>[!abstract] Scriviamo la matrice di $f$ nella base canonica

- $f(e_{1})=\underline{0}$
- $f(e_{2})=e_{1}$
- $f(e_{3})=e_{2}$
- $f(e_{4})=e_{3}$

$$
A=\begin{pmatrix}
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 1 \\
0 & 0 & 0 & 0
\end{pmatrix}
$$
>[!abstract] Troviamo gli autovalori

$$
p(\lambda)=\det\begin{pmatrix}
-\lambda & 1 & 0 & 0 \\
0 & -\lambda & 1 & 0 \\
0 & 0 & -\lambda & 1 \\
0 & 0 & 0 & -\lambda
\end{pmatrix}=-\lambda\det\begin{pmatrix}
-\lambda & 1 & 0 \\
0 & \lambda & 1 \\
0 & 0 & -\lambda
\end{pmatrix}=(-\lambda)^2\det\begin{pmatrix}
-\lambda & 1 \\
0 & -\lambda
\end{pmatrix} = \lambda^4
$$
>[!done] C'è solo un autovalore

- $\lambda_{1}=0,ma(\lambda_{1})=4$

$$
f(x,y,z,w)=0(x,y,z,w)
$$
$$
\begin{cases}
y=0 \\
z=0 \\
w=0 \\
0=0
\end{cases}\implies V\lambda_{1}=\{ (x,0,0,0),x \in\mathbb{R} \}
$$
Base di $V\lambda_{1}=\{ e_{1} \}\implies mg(\lambda_{1})=1$

>[!fail] $f$ non si diagonalizza, $ma(\lambda_{1})\neq mg(\lambda_{1})$

##### Vediamolo in una Prospettiva Diversa
$$
\begin{array}{}
f^2(x,y,z,w)=f_{o}f(x,y,z,w)=f(y,z,w,0)=(z,w,0,0)\\
f^3(x,y,z,w)=f(z,w,0,0)=(w,0,0,0) \\
f^4(x,y,z,w)=f(w,0,0,0)=(0,0,0,0)
\end{array}
$$

>[!done] $f=0$ Dunque è chiaro che $f^4$ ha come unico autovalore $0$

###### Osservazione
Ora se $\lambda$ è un autovalore di $f$ e $v$ un suo autovettore
$$
f(v)=\lambda v
$$
- E
$$
f^4(v)=\lambda f^3(v)=\lambda^2 f^2(v)=\dots=\lambda^4 v
$$
- $\lambda^4=0 \implies\lambda=0$

In ***termini di matrici***
$$
A=\begin{pmatrix}
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 1 \\
0 & 0 & 0 & 0
\end{pmatrix}\implies A^2=\begin{pmatrix}
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 1 \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0
\end{pmatrix}
\implies\dots\implies
A^4=\begin{pmatrix}
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0
\end{pmatrix}
$$
### Teorema Matrici Nilpotenti
>[!info] Definizione
>Una matrice è ***nilpotente*** se $A^n=0$ (***matrice nulla***) con $n\in \mathbb{N}$

>[!Teorema]
>Se una [[1 - Applicazioni Lineari#Applicazione Lineare|applicazione lineare]] non nulla è ***nilpotente***
><u>Allora</u>
>Non è ***diagonalizzabile***

#### Dimostrazione
>*Sia $\lambda$ un autovalore per $f$ e $v$ un suo autovalore*

Poiché $f$ è nilpotente $\exists n>0:f^n=0$
- In particolare $f^n(v)=0$

D'altra parte $f^n(v)=f^{n-1}(\lambda v)=\lambda f^{n-1}(v)=\dots=\lambda^n v$

Poiché $v$ è diverso da $0$ per [[9 - Matrici Diagonali#Autovettore e Autovalore|definizione]]

Per forza $\lambda^n=0\implies\lambda=0$

Quindi $f$ ha come unico autovalore $0$

>[!fail] Se fosse diagonalizzabile avrebbe come matrice la matrice nulla. *Contraddizione*

### Blocco di Jordan
>[!info] Definizione
>Definiamo il "***blocco di Jordan***" $J_{\lambda i,n}$ come la matrice $n\times n$:
>$$J_{\lambda i,n}=\begin{pmatrix}\lambda_{i} & 1 & \dots & 0 \\0 & \lambda_{i} & \dots & 0 \\ \dots & \dots & \dots & \dots \\0 & 0 & \dots & 1 \\ 0 & 0 & \dots & \lambda_{i}\end{pmatrix}
\times\begin{pmatrix} x_{1} \\ x_{2} \\ \dots \\ x_{n-1} \\ x_{n}\end{pmatrix}=\begin{pmatrix} \lambda_{i}x_{1}+x_{2} \\ \lambda_{i}x_{2}+x_{3} \\ \dots \\ \lambda_{i}x_{n-1}+x_{n} \\ \lambda_{i}x_{n}\end{pmatrix}$$

$$
p(\lambda)=(\lambda_{i}-\lambda)\det(J_{\lambda i,n-1})=\dots=(\lambda i-\lambda)^n
$$
L'unico autovalore è $\lambda_{i}$ e $ma(\lambda_{i})=n$

$$
\begin{cases}
\lambda_{i}x_{1}+x_{2}=\lambda_{i}x_{1} \\
\dots \\
\lambda_{i}x_{n-1}+x_{n}=\lambda_{i}x_{n-1} \\
\lambda_{i}x_{n}=\lambda_{i}x_{n}
\end{cases} \iff \begin{cases}
x_{2}=0 \\
x_{3}=0 \\
\dots \\
x_{n}=0 \\
0=0
\end{cases}
$$
- $V\lambda_{i}=(x_{1},0,0,0,\dots,0)\implies mg(\lambda_{i})=1$

>[!tldr] $J_{\lambda i,n}$ non è diagonalizzabile

Quindi $\forall n>1$ $J\lambda i,n$ è somma di una matrice [[9 - Matrici Diagonali#Matrice Diagonale|diagonale]] e una [[#Matrici Nilpotenti|nilpotente]]

### Decomposizione Canonica di Jordan
>[!Teorema]
>Sia $f$ un [[4 - Isomorfismo#Endomorfismo|endomorfismo]] di $V$ e siano $\lambda_{1},\dots,\lambda_{t}\in\mathbb{K}$ i suoi [[9 - Matrici Diagonali#Autovettore e Autovalore|autovalori]]
><u>Allora</u>
>1. $f$ è somma di una applicazione diagonalizzabile $f_{d}$ e di una applicazione nilpotente $f_{n}$
>Tale decomposizione è ***unica***
>$$f=f_{d}+f_{n}$$
>2. Esiste una base di $V$ in cui la matrice ha la seguente forma, detta "***forma canonica di Jordan***"
>$$\begin{pmatrix} J_{\lambda_{1},n_{1}} & 0 & 0 & 0 & 0 & 0 \\ 0 & \dots & 0 & 0 & 0 & 0  \\ 0 & 0 & J_{\lambda_{1},n_{i}} & 0 & 0 & 0 \\ 0 & 0 & 0 & J_{\lambda_{2},n_{2}} & 0 & 0 \\ 0 & 0 & 0 & 0 & \dots & 0 \\ 0 & 0 & 0 & 0 & 0 & J_{\lambda_{t},n_{t}} \end{pmatrix}$$
>Dove per ciascun $\lambda_{i}$ ci sono $mg(\lambda_{i})$ ***blocchi di Jordan*** la cui somma delle dimensioni è $ma(\lambda_{i})$

#### Esempio
>*Supponiamo di avere $f:\mathbb{R}^6\to\mathbb{R}^6$ e aver trovato gli autovalori $\lambda_{1}=7,\lambda_{2}=3,\lambda_{3}=-2$ con $ma(7)=3,ma(3)=2,ma(-2)=1$*

Supponiamo di avere calcolato le molteplicità geometriche
- $mg=1 ,\forall\lambda$
Esiste una base di $\mathbb{R}^6$ in cui la matrice di $f$ è:
$$
\begin{pmatrix}
J_{7,3} & 0 & 0 \\
0 & J_{3,2} & 0 \\
0 & 0 & J_{-2,1}
\end{pmatrix}=
\begin{pmatrix}
7 & 1 & 0 & 0 & 0 & 0 \\
0 & 7 & 1 & 0 & 0 & 0 \\
0 & 0 & 7 & 0 & 0 & 0 \\
0 & 0 & 0 & 3 & 1 & 0 \\
0 & 0 & 0 & 0 & 3 & 0 \\
0 & 0 & 0 & 0 & 0 & -2
\end{pmatrix}=
$$
$$
=\begin{pmatrix}
7 & 0 & 0 & 0 & 0 & 0 \\
0 & 7 & 0 & 0 & 0 & 0 \\
0 & 0 & 7 & 0 & 0 & 0 \\
0 & 0 & 0 & 3 & 0 & 0 \\
0 & 0 & 0 & 0 & 3 & 0 \\
0 & 0 & 0 & 0 & 0 & -2
\end{pmatrix}+\begin{pmatrix}
0 & 1 & 0 & 0 & 0 & 0 \\
0 & 0 & 1 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 & 1 & 0 \\
0 & 0 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 & 0 & 0
\end{pmatrix}
$$

#### Esempio
>*Sia $f:\mathbb{R}^5\to\mathbb{R}^5$ e supponiamo di sapere che $f$ ha solo due autovalori $\lambda_{1}=6,\lambda_{2}=4$ con $ma(6)=4,ma(4)=1,mg(6)=2,mg(4)=1$*

Quindi ci sono $2$ ***blocchi di Jordan*** di autovalore $6$ e uno di autovalore $4$
- La decomposizione potrebbe essre:
$$
\begin{pmatrix}
J_{6,2} & 0 & 0 \\
0 & J_{6,2} & 0 \\
0 & 0 & J_{4,1}
\end{pmatrix}=\begin{pmatrix}
6 & 1 & 0 & 0 & 0 \\
0 & 6 & 0 & 0 & 0 \\
0 & 0 & 6 & 1 & 0 \\
0 & 0 & 0 & 6 & 0 \\
0 & 0 & 0 & 0 & 4
\end{pmatrix}
$$
Oppure
$$
\begin{pmatrix}
J_{6,3} & 0 & 0 \\
0 & J_{6,1} & 0 \\
0 & 0 & J_{4,1}
\end{pmatrix}=\begin{pmatrix}
6 & 1 & 0 & 0 & 0 \\
0 & 6 & 1 & 0 & 0 \\
0 & 0 & 6 & 0 & 0 \\
0 & 0 & 0 & 6 & 0 \\
0 & 0 & 0 & 0 & 4
\end{pmatrix}
$$