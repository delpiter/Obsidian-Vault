## Vettori nel Piano e nello Spazio
---
>[!tldr] Vettore
>Un vettore $\vec{V}$ è individuato da $3$ elementi:
>1) La **_Lunghezza_**, rappresentata da un numero $x\in\mathbb{R} : x\geq0$, anche chiamata modulo del vettore
>2) Una _**Direzione**_, rappresentata da una retta o da qualsiasi sua parallela.
>3) Un _**Verso**_

![[vettoreGeometrico.png]]
### Rappresentazione Cartesiana
Fissato un sistema di riferimento con origine $o(0,0)$:
- È possibile assegneare ad ogni punto $A=(x,y)$ il vettore $\vec{V}$ che unisce $o$ e $A$ orientato da $o$ ad $A$
![[vettoreCartesiano.png]]

#### Vettori Speciali
Esistono per convenzione vettori "_particolari_":
- Vettori di lunghezza $1$
![[versori.png]]

- Chiamati **versori**, sempre per convenzione denominati come $i$ e $j$
### Somma tra Vettori
>[!info] Definizione
>Dati due vettori $\vec{V} = \vec{oA}$ e $\vec{W} = \vec{oB}$
>La somma fra di essi si definisce in questo modo:
>Si applica ad $A$ il vettore $W$, cioè scrivo $W=\vec{AC}$
><u>Allora</u>
>Ottengo un nuovo vettore: $\vec{V}+\vec{W} = \vec{oC}$

![[sommaVettori.png]]

### Vettore inverso
>[!info] Definizione
>Sia $\vec{V}$ un vettore di lunghezza $x$ e direzione di equazione $ax +c$:
>Il vettore inverso sarà un vettore di ***lunghezza e direzione uguale***, ma con il verso invertito.

![[vettoreInverso.png]]

### Prodotto di Vettore per uno Scalare
Considerando uno "scalare" come un qualsiasi numero $t\in\mathbb{R}$
>[!info] Definizione
>Sia $V$ un vettore del piano $(V\in\mathbb{R}^2)$, sia $t\in\mathbb{R}$
>Definiamo il vettore $tV$ come il vettore $W$:
>1) $|W| = |t|\cdot|V|$
>2) Direzione di $W$ uguale alla direzione di $V$
>3) Verso di $W=\begin{cases}\text{ verso di } V \text{ se }t>0 \\\text{ verso di } -V \text{ se }t<0\end{cases}$


## Vettori in $\mathbb{R}^3$
---
>[!tldr] Vettore
>La definizione di vettore in $\mathbb{R}^3$ è uguale al vettore in $\mathbb{R}^2$:
>1) La **_Lunghezza_**, rappresentata da un numero $x\in\mathbb{R} : x\geq0$, anche chiamata modulo del vettore
>2) Una _**Direzione**_, rappresentata da una retta o da qualsiasi sua parallela.
>3) Un _**Verso**_
>>[!done] Osservazione
>>Posso identificare un punto $P\in\mathbb{R}^3 = (x,y,z)$ con il vettore che unsice $o$ a $P$ orientato da $o$ a $P$

![[versoriR3.png]]
- In $\mathbb{R}^3$ si aggiunge un ***versore***, denominato $k$
	- $i=(1,0,0),j=(0,1,0),k=(0,0,1)$
	- Di conseguenza un vettore si può rappresentare come:
		- $V=(x,y,z)=ix+jy+kz$
### Modulo, Somma e Moltiplicazione per Scalare
Le operazioni sono analoghe per qualsiasi numero di dimensioni che prendiamo
#### Modulo
- Si applica due volte il teorema di Pitagora
$$
|V|=\sqrt{ x_{p}^2+y^2_{p}+z^2_{p} }
$$
![[moduloVettore.png]]
#### Somma di Vettori e Prodotto Scalare
- Analoghi ad $\mathbb{R}^2$

### Prodotto Scalare fra Vettori
>[!info] Definizione
>Definiamo il prodotto scalare tra $V$ e $W$ come:
>$$V\cdot W = |V| |W| cos(\alpha)$$
>Dove $\alpha$ è l'angolo tra $V$ e $W$ compreso tra $0$ e $\pi$


### Prodotto Scalare in Coordinate
#### $\mathbb{R}^2$
- Analogo in $\mathbb{R}^3$
>[!info] Definizione
>Sia $V=(x_{1},y_{1})=x_{1}i+y_{1}j$
>Sia $W=(x_{2},y_{2})=x_{2}i+y_{2}j$
>$$\begin{array}
,V\cdot W = (x_{1}i+y_{1}j)\cdot(x_{2}i+y_{2}j)= \\
=x_{1}i\cdot x_{2}i + \cancel{ x_{1}i\cdot y_{2}j } +\cancel{ y_{1}j\cdot x_{1}i  }+y_{1}j\cdot y_{2}j = \\
=x_{1}\cdot x_{2} +y_{1} \cdot y_{2}
\end{array}
>$$

## Rette e Piani in $\mathbb{R}^3$
---
Una retta in $\mathbb{R}^3$ può essere rappresentata in $3$ modi:
>[!info] Rappresentazione
>Una retta in $\mathbb{R}^3$ è individuata da:
>1) Un punto e una direzione
>2) Da due Punti
>3) Da due Piani, non paralleli

### 1.
- Sia $P_{0}=(x_{0},y_{0},z_{0})$ e sia $V=(a,b,c)\neq 0$
>[!done] In breve
>Un qualsiasi punto $P$ appartenente alla retta $r$ passante per $P_{0}$ e di direzione $V$
>È della forma
>$$P = P_{0}+tV\,\,\, , t\in\mathbb{R}$$

![[rettaR3.png]]
- Il generico punto $P=(x,y,z)$ deve soddisfare le seguenti condizioni
$$
\begin{cases}
x=x_{p0}+ta \\
y=y_{p0}+tb \\
z=z_{p0}+tc
\end{cases}
$$
- Chiamate equazioni Parametriche di una retta in $\mathbb{R}$
	- Sono vere se $a,b,c\neq 0$
	- Es con una coordinata che si annulla

$$
\begin{cases}
x=x_{p0} \\
y=y_{p0}+tb \\
z=z_{p0}+tc
\end{cases}
$$
- Da qui possiamo ricavare l'Equazione cartesiana della retta
$$
\begin{cases}
\displaystyle{\frac{x-x_{0}}{a}} = \displaystyle{\frac{y-y_{0}}{b}} \\
\displaystyle{\frac{y-y_{0}}{b}} = \displaystyle{\frac{z-z_{0}}{c}}
\end{cases}
$$
### 2.
Dati due punti $P_{0}(x_{0},y_{0},z_{0})$ e $P_{1}(x_{1},y_{1},z_{1})$
>[!done] In Breve
>La retta passante per $P_{0}$ e $P_{1}$ non è altro che la retta passante per $P_{0}$ con direzione $V=P_{1}-P_{0}$

![[rettaPassante2Punti.png]]

## Piano in $\mathbb{R}^3$
---
Un piano in $\mathbb{R}^3$ può essere rappresentato in $3$ modi:
>[!info] Rappresentazione
>Un piano in $\mathbb{R}^3$ è individuato da:
>1) Un punto e un vettore ortogonale al piano
>2) Tre punti
>3) Due rette non [[Definizioni_Analisi#Rette Sghembe|sghembe]]

### Punto e vettore Ortogonale
>[!tip] 1
>Dato $P_{0}=(x_{0},y_{0},z_{0}),\,\,V\in(a,b,c)$
>Un generico punto $P=(x_{1},y_{1},z_{1})$ appartenente al piano deve soddisfare che:
>1) $(P-P_{0})\perp V \Leftrightarrow(P-P_{0})\cdot V = 0$
#### Equazione del piano
>[!info] Definizione
>Sia $P_{0}(x_{0},y_{0},z_{0})$
>Sia $V=(a,b,c)$
>L'equazione passante per $P_{0}$ e $\perp$ a $V$ è:
>$$a(x-x_{0})+b(y-y_{0})+c(z-z_{0})$$

### Piani Particolari
- $x=0\implies$ Piano $y-z$
- $y=0\implies$ Piano $x-z$
- $z=0\implies$ Piano $x-y$
#### Osservazione
Siano $\pi$ e $\pi'$
- $\pi:ax+bx+cz+d=0$
- $\pi':a'x+b'x+c'z+d'=0$
>[!tip] Oss
>$\pi$ e $\pi'$ sono $\parallel\Leftrightarrow(a,b,c)\parallel (a',b',c')$
>$\pi$ e $\pi'$ sono $\perp\Leftrightarrow(a,b,c)\perp (a',b',c')$


## Insiemi Aperti e Chiusi
---
>[!info] Definizioni
>>[!example] Aperto
>>Sia $A\subseteq\mathbb{R}^2$, diciamo che $A$ è **Aperto** se
>>$\forall(x_{0},y_{0})\in A,\ \ \exists$ un intorno $\mathrm{U}_{(x_{0},y_{0})}:$
>>$$\mathrm{U}_{(x_{0},y_{0})}\subset A$$ 
>
>>[!example] Chiuso
>>Sia $A\subseteq\mathbb{R}^2$, diciamo che $A$ è **Chiuso** se
>>$$\mathbb{R}^2 \setminus A$$
>>È aperto

## Insiemi Limitati
---
>[!info] Definizione
>Sia $A\subseteq\mathbb{R}^2$ diciamo che $A$ è limitato se:
>$$\exists B_{R(x_{0},y_{0})}: A \subset B_{R(x_{0},y_{0})}$$
>>[!done] In Breve
>>$A$ è limitato se esiste un cerchio di raggio $R$ e centro in $(x_{0},y_{0})$ che contenga interamente l'insieme $A$

## Matrici su $\mathbb{R}$ di tipo $(m,n)$
---
>[!info] Definizione
>Una Matrice è una tabella di $m\cdot n$ numeri reali disposti su $m$ righe e $n$ colonne
>>[!example] Esempio
>>$$
A=\begin{pmatrix}
2 & 3 & 1 \\
\pi & 0 & 7 \\
\frac{7}{5}  & 5  & 23
\end{pmatrix}
>>$$

### In generale
$$
A=\begin{pmatrix}
a_{11} & a_{12}  & \dots  & a_{1n} \\
a_{21} & a_{22}  & \dots  & a_{2n} \\
\dots & \dots & \dots & \dots \\
a_{m1} & a_{m2}  & \dots  & a_{mn}
\end{pmatrix}
$$
### Operazioni fra Matrici
#### Tra Matrici dello stesso tipo
- Posso definire:
##### Somma
$$
A=\begin{pmatrix}
a_{11} & a_{12}  & \dots  & a_{1n} \\
a_{21} & a_{22}  & \dots  & a_{2n} \\
\dots & \dots & \dots & \dots \\
a_{m1} & a_{m2}  & \dots  & a_{mn}
\end{pmatrix}
B=\begin{pmatrix}
b_{11} & b_{12}  & \dots  & b_{1n} \\
b_{21} & b_{22}  & \dots  & b_{2n} \\
\dots & \dots & \dots & \dots \\
b_{m1} & b_{m2}  & \dots  & b_{mn}
\end{pmatrix}
$$
$$
A+B=\begin{pmatrix}
a_{11}+b_{11} & a_{12}+b_{12}  & \dots  & a_{1n}+b_{1n} \\
a_{21}+b_{21} & a_{22}+b_{22}  & \dots  & a_{2n}+b_{2n} \\
\dots & \dots & \dots & \dots \\
a_{m1}+b_{m1} & a_{m2}+b_{m2}  & \dots  & a_{mn}+b_{mn} \\
\end{pmatrix}
$$

##### Prodotto per Scalare
- Dato $t\in\mathbb{R}$
$$
A=\begin{pmatrix}
a_{11} & a_{12}  & \dots  & a_{1n} \\
a_{21} & a_{22}  & \dots  & a_{2n} \\
\dots & \dots & \dots & \dots \\
a_{m1} & a_{m2}  & \dots  & a_{mn}
\end{pmatrix}
tA=\begin{pmatrix}
ta_{11} & ta_{12}  & \dots  & ta_{1n} \\
ta_{21} & ta_{22}  & \dots  & ta_{2n} \\
\dots & \dots & \dots & \dots \\
ta_{m1} & ta_{m2}  & \dots  & ta_{mn}
\end{pmatrix}
$$

#### Prodotto tra Matrici (Riga $\times$ Colonna)
>[!info] Definizione
>Siano $A=\text{matrice}(m,n)$ e $B=\text{matrice}(n,P)$
>Posso dire $C = A\cdot B$
>>[!done] Descrizione elementi
>>L'elemento $C_{i,j}$, di posto colonna $i$ e riga $j$ è dato dal prodotto scalare tra la $i-$esima riga della matrice $A$ e la $j-$esima colonna della matrice $B$

##### Esempio
- $C=A\cdot B =\text{matrice}(m,P)$
$$
A=\begin{pmatrix}
1 & 2 \\
3 & 1
\end{pmatrix}
\ \ \ \ \ \ 
B=\begin{pmatrix}
2 & 0 & 1 \\
1 & 1 & 3
\end{pmatrix}
$$
$$
C=\begin{pmatrix}
1\cdot 2+2\cdot 1  & 1\cdot 0+2\cdot 1  & 1\cdot 1 +2\cdot 3 \\
3\cdot 2+1\cdot 1  & 3\cdot 0 +1\cdot1  & 3\cdot1 +1\cdot 3
\end{pmatrix}=
\begin{pmatrix}
4 & 2 & 7 \\
7 & 1 & 6
\end{pmatrix}
$$
### Determinante di una Matrice $(2,2)$
$$
A=\begin{pmatrix}
a_{11}  & a_{12} \\
a_{21}  & a_{22}
\end{pmatrix}
$$
- $detA = a_{11}\cdot a_{22} -a_{12}\cdot a_{21}$
