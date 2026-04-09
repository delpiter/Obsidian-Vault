## Basi Facili per le Forme Bilineari
---
>[!question] È possibile trovare una base $v_{1},\dots,v_{n}$ di $V$ tale che la matrice di $\beta$ in tale base sia diagonale?

>[!abstract] Osservazione

Se $\beta$ è ***antisimmetrica***, sicuramente no
- L'unica ***matrice antisimmetrica diagonale*** è la matrice nulla

Se $\beta$ è ***simmetrica*** è sempre diagonalizzabile
- Una base diagonalizzabile si può ***sempre trovare***

### Teorema
>[!info] Diagonalizzazione delle Forme Bilineari
>Sia $V$ uno [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Spazio Vettoriale|spazio vettoriale]] su $\mathbb{K}$ e $\beta$ una [[1 - Forme Bilineari#Forma Bilineare|forma bilineare]] ***simmetrica***
><u>Allora</u>
>$\exists$ una base $v_{1},\dots,v_{n}$ di $V$ tale che $\beta$ in tale base è [[../Applicazioni/9 - Matrici Diagonali#Matrice Diagonale|diagonale]]
>>[!done] In altre Parole
>>Sia $A$ una ***matrice simmetrica***, $\exists$ una matrice diagonale congruente ad $A$

#### Dimostrazione
>*Cominciamo con una base qualsiasi si $V$: $w_{1},\dots,w_{n}$*

>[!abstract] Passo 1

Nella base $w_{1},\dots,w_{n}$, ho la matrice:
$$
\begin{pmatrix}
w_{1},w_{1} & w_{1},w_{2} & w_{1},w_{3} & \dots \\
w_{2},w_{1} & w_{2},w_{2} & w_{2},w_{3} & \dots\\
w_{3},w_{1} & w_{3},w_{2} & w_{3},w_{3}& \dots \\
\dots& \dots& \dots& \dots
\end{pmatrix}
$$
###### Caso 1
Se $\beta(w_{1},w_{1})\neq 0$, vai al ***passo 2***

###### Caso 2
Se $\beta(w_{1},w_{1})=0$ ma esiste $i$ tale che $\beta(w_{i},w_{i})\neq 0$
- Scambia $w_{1}$ con $w_{i}$ e vai al ***passo 2***

###### Caso 3
Se $\beta(w_{i},w_{i})=0$ $\forall i=1,\dots,n$ allora cerco $i,j:\beta(w_{i},w_{j})\neq0$ e scambio:
- $w_{1} \leftarrow w_{i}+w_{j}$, $\quad w_{2} \leftarrow w_{j}$, $\quad w_{i}\leftarrow w_{1}$, $\quad w_{j}\leftarrow w_{2}$
- Così che $\beta(w_{i}+w_{j},w_{i}+w_{j})=\underbrace{ \beta(w_{i},w_{i}) }_{ =0 }+\underbrace{ \beta(w_{j},w_{j}) }_{ =0 }+\underbrace{ 2\beta(w_{i},w_{j}) }_{ \neq 0 }$
- E vado al ***passo 2***

>[!abstract] Passo 2

Per quanto fatto al ***passo 1*** $\beta(w_{1},w_{1})\neq 0$
Definiamo una nuova base $w_{1}',\dots,w_{n}'$
- $w_{1}'=w_{1}$ 
- $w_{i}'=w_{i}-\displaystyle{\frac{\beta(w_{1},w_{i})}{\beta(w_{1},w_{1})}}w_{1} \qquad \forall i=2,\dots,n$

La definiamo così affinché:
$$
\beta(w_{1}',w_{i}')=\beta\left( w_{1},w_{i}-\underbrace{ \displaystyle{\frac{\beta(w_{1},w_{i})}{\beta(w_{1},w_{1})}} }_{ a }w_{1} \right) 
$$
Utilizzando la ***proprietà della linearità***:
$$
\beta(w_{1},w_{i})-\displaystyle{\frac{\beta(w_{1},w_{i})}{\cancel{ \beta(w_{1},w_{1}) }}}\cancel{ \beta(w_{1},w_{1}) }=
$$
$$
=\beta(w_{1},w_{i})-\beta(w_{1},w_{i})=0
$$
Cioè nella nuova base, la matrice di $\beta$ è:
$$
\begin{pmatrix}
*  & 0 & 0 & \dots & 0 \\
0 \\
0 \\
\dots \\
0
\end{pmatrix}
$$
Ora $w_{1}'$ non lo tocco più e riapplico il ***passo 1*** e il ***passo 2*** a $w_{2}',\dots,w_{n'}$
- Ottengo una ***nuova base*** $w_{1}'',w_{2}'',\dots,w_{n}''$ in cui la matrice di $\beta$ è:

$$
\begin{pmatrix}
*  & 0 & 0 & \dots & 0 \\
0  & * & 0 & \dots & 0\\
0  & 0\\
\dots  & \dots\\
0 & 0
\end{pmatrix}
$$

>[!caution] E così via

Dopo $n-1$ iterazioni dei $2$ passi, ho ottenuto una base $u_{1},\dots,u_{n}$ tale che la matrice di $\beta$ in questa base è diagonale
$$
\begin{pmatrix}
*  & 0 & 0 & \dots & 0 \\
0  & * & 0 & \dots & 0\\
0  & 0 & \dots & \dots & \dots\\
\dots  & \dots & \dots & \dots & 0\\
0 & 0 & \dots & 0 & *
\end{pmatrix}
$$

#### Esempio
>*Sia $A$ la matrice $3\times 3$ che rappresenta la forma bilineare simmetrica $\beta$ nella base $e_{1},e_{2},e_{3}$*

$$
A=\begin{pmatrix}
0 & -1 & 2 \\
-1 & 1 &  0 \\
2 & 0 & 2
\end{pmatrix}
$$
- $\beta(e_{1},e_{1})=0$
- $\beta(e_{1},e_{2})=-1$
- $\beta(e_{2},e_{2})=1$
- $\beta(e_{1},e_{3})=2$
- $\beta(e_{2},e_{3})=0$
- $\beta(e_{3},e_{3})=2$

>[!caution] Iterazione 1

>[!abstract] Passo 1

$\beta(e_{1},e_{1})=0$
- Quindi devo ***invertire*** i primi due vettori

- $w_{1}=e_{2},\quad w_{2}=e_{1},\quad w_{3}=e_{3}$

In tale base la nuova matrice di $\beta$ è:
$$
\begin{pmatrix}
1 & -1 & 0 \\
-1 & 0 & 2  \\
0 & 2 & 2
\end{pmatrix}
$$
>[!abstract] Passo 2

- $w_{1}'=w_{1}=e_{2}$
- $w_{2}'=w_{2}-\displaystyle{\frac{\beta(w_{1},w_{2})}{\beta(w_{1},w_{1})}}w_{1}=w_{2}-\displaystyle{\frac{(-1)}{1}}w_{1}=w_{2}+w_{1}=e_{1}+e_{2}$
- $w_{3}'=w_{3}-\displaystyle{\frac{\beta(w_{1},w_{3})}{\beta(w_{1},w_{1})}}w_{1}=w_{3}-\displaystyle{\frac{0}{1}}w_{1}=w_{3}=e_{3}$

Ora controlliamo che la *prima riga* e la *prima colonna* ***si siano azzerate***

- $\beta(w_{1}',w_{2}')=\beta(w_{1},w_{1})+\beta(w_{1},w_{2})=0$
- $\beta(w_{1}',w_{3}')=\beta(w_{1},w_{3})=0$

Nella nuova base ($e_{2},\ e_{1}+e_{2},\ e_{3}$) la matrice è:
$$
\begin{pmatrix}
1 & 0 & 0  \\
0 & -1 & 2 \\
0 & 2 & 2
\end{pmatrix}
$$
***Poiché***:
$\beta(w_{2}',w_{2}')=\beta(w_{1}+w_{2},w_{1}+w_{2})=\beta(w_{1},w_{1})+\beta(w_{2},w_{2})+2\beta(w_{1},w_{2})=1+0+2(-1)=-1$
$\beta(w_{2}',w_{3}')=\beta(w_{1}+w_{2},w_{3})=\beta(w_{1},w_{3})+\beta(w_{2},w_{3})=0+2=2$

E ***infine***
$\beta(w_{3}',w_{3}')=\beta(w_{3},w_{3})=2$

>[!caution] Iterazione 2

Ora applico l'algoritmo alla matrice $\begin{pmatrix}-1 & 2 \\ 2 & 2 \end{pmatrix}$
>[!abstract] Passo 1

Osservo che $\beta(w_{2}',w_{2}')\neq0$

>[!abstract] Passo 2

Cerco la nuova ***base***:
- $u_{1}=w_{1}'=e_{1}$
- $u_{2}=w_{2}'=e_{1}+e_{2}$
- $u_{3}=w_{3}'-\displaystyle{\frac{\beta(w_{2}',w_{3}')}{\beta(w_{2}',w_{2}')}}w_{2}'=w_{3}'-\frac{2}{-1}w_{2}=w_{3}'+2w_{2}=2e_{1}+2e_{2}+e_{3}$

Controllo che si sia azzerato quello che volevo si azzerasse
- $\beta(u_{2},u_{3})=\beta(w_{2}',w_{3}')+2\beta(w_{2}',w_{2}')=2+2(-1)=0$

>[!done] Quindi la mia base di *matrice diagonale* è
>$$u_{1}=e_{1},u_{2}=e_{1}+e_{2},u_{3}=2e_{1}+2e_{2}+e_{3}$$

Calcolo l'ultimo elemento della matrice: $\beta(u_{3},u_{3})$:
$$
\begin{array}
\ \beta(u_{3},u_{3})=\beta(w_{3}'+2w_{2}',w_{3}'+2w_{2}')=\beta(w_{3}',w_{3}'+2w_{2})+2\beta(w_{2}',w_{3}'+2w_{2}')= \\
=\beta(w_{3}',w_{3}')+4\beta(w_{2}',w_{2}')+4\beta(w_{2}',w_{3}')= 2+4(-1)+4(2)=6
\end{array}
$$
Di conseguenza la ***matrice in questa base*** è:
$$
\begin{pmatrix}
1 & 0 & 0 \\
0 & -1 & 0 \\
0 & 0 & 6
\end{pmatrix}
$$

## Matrici ancora più Facili
---
>*Abbiamo visto che data una forma bilineare si $V$ ($V$ [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Spazio Vettoriale|spazio vettoriale]] su $\mathbb{K}$) si può trovare una base di $V$ tale che la matrice di $\beta$ sia* ***diagonale***

>[!question] Si può fare di meglio?

#### Esempio
>*Sia $\beta$ una [[1 - Forme Bilineari#Forma Bilineare|forma bilineare]] su $\mathbb{R}^4$ e supponiamo di aver trovato una base $v_{1},v_{2},v_{3},v_{4}$:*
- $\beta(v_{1},v_{1})=4$
- $\beta(v_{2},v_{2})=3$
- $\beta(v_{3},v_{3})=-5$
- $\beta(v_{4},v_{4})=0$
- $\beta(v_{i},v_{j})=0 \quad \forall i\neq j$

$$
D=
\begin{pmatrix}
4 & 0 & 0 & 0 \\
0 & 3 & 0 & 0 \\
0 & 0 & -5 & 0 \\
0 & 0 & 0 & 0
\end{pmatrix}
$$
Ora consideriamo una nuova base $u_{1},u_{2},u_{3},u_{4}$
- $u_{1}=\frac{1}{2}v_{1}\implies \beta(u_{1},u_{1})=\beta\left( \frac{1}{2}v_{1},\frac{1}{2}v_{1} \right)=\frac{1}{4}\beta(v_{1},v_{1})=\frac{1}{4}\cdot 4=1$
- $u_{2}=\frac{1}{\sqrt{ 3 }}v_{2}\implies \beta(u_{2},u_{2})=\frac{1}{\sqrt{ 3 }}\cdot \frac{1}{\sqrt{ 3 }}\cdot 3=1$
- $u_{3}=\frac{1}{\sqrt{ 5 }}v_{3}\implies\beta(u_{3},u_{3})=\frac{1}{\sqrt{ 5 }}\cdot\frac{1}{\sqrt{ 5 }}\cdot (-5)=-1$
- $u_{4}=v_{4}$

>[!abstract] La nuova matrice sarà

$$
D_{new}=
\begin{pmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & -1 & 0 \\
0 & 0 & 0 & 0
\end{pmatrix}

$$
>[!done] Risposta: Dipende dal campo $\mathbb{K}$

##### Osservazione
Se invece che $\mathbb{R}$ fossi stato su $\mathbb{C}$, cioè $V=\mathbb{C}^4$
- Invece che $u_{3}=\frac{1}{\sqrt{ 5 }}v_{3}$ avrei potuto prendere $u_{3}=\frac{1}{\sqrt{ -5 }}v_{3}=\frac{i\sqrt{ 5 }}{5}v_{3}$
- Così che $\beta(u_{3},u_{3})=1$

E quindi la matrice di $\beta$ sarebbe stata:
$$
D_{new}=
\begin{pmatrix}
1 & 0 & 0 & 0 \\
0 & 1 & 0 & 0 \\
0 & 0 & 1 & 0 \\
0 & 0 & 0 & 0
\end{pmatrix}
$$
### Teorema di Sylvester
>[!info] Sylvester
>Dato uno [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Spazio Vettoriale|spazio vettoriale]] $V$ su $\mathbb{R}$ e data una [[1 - Forme Bilineari#Forma Bilineare|forma bilineare]] *simmetrica* $\beta$ su $V$
>$\exists$ una ***base*** $u_{1},\dots,u_{n}$ di $V$ tale che in tale base la ***matrice*** di $\beta$ è una ***matrice*** fatta così:
>>[!abstract] ‎ 
>$$\begin{pmatrix}I_{p} & 0 & 0 \\ 0 & -I_{r-p} & 0 \\ 0 & 0 & 0 \end{pmatrix}=\begin{pmatrix} 1 \\  & \underbrace{ \dots }_{ p } \\  &  & 1 \\  &  &  & -1 \\  &  &  &  & \underbrace{ \dots }_{ r-p } \\  &  &  &  &  & -1 \\  &  &  &  &  &  & 0 \\  &  &  &  &  &  &  & \underbrace{ \dots }_{ n-r } \\  &  &  &  &  &  &  &  & 0 \end{pmatrix}$$

>[!summary] Segnatura
>I numeri $p$ e $r-p$  ($r$ è il [[../Applicazioni/6 - Cambiamenti di Base#Rango di una Matrice|rango]] della *matrice*) *dipendono* solo da $\beta$ e *non dalla base scelta* e sono detti ***segnatura*** di $\beta$

Nell'esempio precedente la ***segnatura*** è: $(2,1)$
#### Dimostrazione
Per il [[#Teorema|teorema di diagonalizzazione]], esiste una base $v_{1},\dots,v_{n}$ di $V$ tale che la matrice di $\beta$ è ***diagonale***

A meno di ***riordinare questi elementi***, possiamo supporre che:
- $\beta(v_{i},v_{i})>0 \quad \forall i=1,\dots,p$
- $\beta(v_{j},v_{j})<0 \quad \forall j=p+1,\dots,r$
- $\beta(v_{h},v_{h})=0 \quad \forall h=r+1,\dots, n$

Consideriamo ora la ***base***:
$$
u_{i}=\begin{cases}
\displaystyle{\frac{1}{\sqrt{ \mid\beta(v_{i},v_{i}) \mid}}v_{i}} \quad \text{ se } i\leq r \\
v_{i} \qquad \qquad \qquad \quad \text{ se } i>r
\end{cases}
$$

Così che:
$$
\beta(u_{i},u_{i})=\begin{cases}
1 \qquad \text{ se }i=1,\dots,p \\
-1 \ \quad \text{ se }i=p+1,\dots,r \\
0 \qquad \text{ se }i=r+1,\dots,n
\end{cases}
$$

>*Omettiamo la dimostrazione della seconda parte*
>- *La segnatura non dipende dalla base scelta*

### Teorema di Sylvester su $\mathbb{C}$
>[!info] Sylvester su $\mathbb{C}$
>Dato uno [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Spazio Vettoriale|spazio vettoriale]] $V$ su $\mathbb{C}$ e data una [[1 - Forme Bilineari#Forma Bilineare|forma bilineare]] *simmetrica* $\beta$ su $V$
>$\exists$ una ***base*** $u_{1},\dots,u_{n}$ di $V$ tale che in tale base la ***matrice*** di $\beta$ è una ***matrice*** fatta così:
>>[!abstract] ‎ 
>$$\begin{pmatrix}I_{r} & 0  \\ 0 & 0  \end{pmatrix}=\begin{pmatrix} 1 \\  & \ \underbrace{ \dots }_{r  } \\  &  & 1 \\   &  &  & 0 \\    &  &  &  & \underbrace{ \dots }_{ n-r } \\    &  &  &  &  & 0 \end{pmatrix}$$
#### Dimostrazione
>*Procediamo come nella* ***dimostrazione precedente***

Per il [[#Teorema|teorema di diagonalizzazione]], esiste una base $v_{1},\dots,v_{n}$ di $V$ tale che la matrice di $\beta$ è ***diagonale***

Salvo che:
- $\forall i=1,\dots,r$
Definiamo
$$
u_{i}=
\displaystyle{\frac{1}{\sqrt{ \beta(v_{i},v_{i}) }}v_{i}} 
$$

Così che:
$$
\beta(u_{i},u_{i})=\begin{cases}
\displaystyle{\frac{1}{\sqrt{ \beta(v_{i},v_{i}) }}v_{i}} \qquad \text{ se }i=p+1,\dots,r \\
0 \qquad \qquad \quad \qquad \text{ se }i=r+1,\dots,n
\end{cases}
$$

### Corollario
>[!info] Matrici Congruenti
>Due matrici [[1 - Forme Bilineari#Matrici Simmetriche e Antisimmetriche|simmetriche]] sono [[1 - Forme Bilineari#Matrici Congruenti|congruenti]] su $\mathbb{R}\iff$ hanno la stessa ***segnatura*** 
>Due matrici [[1 - Forme Bilineari#Matrici Simmetriche e Antisimmetriche|simmetriche]] sono [[1 - Forme Bilineari#Matrici Congruenti|congruenti]] su $\mathbb{C}\iff$ hanno lo stesso [[../Applicazioni/6 - Cambiamenti di Base#Rango di una Matrice|rango]]

#### Esempio
>*Siano $A=\begin{pmatrix}2&0 \\ 0 &3\end{pmatrix}$ e $M=\begin{pmatrix}2&0 \\ 0 &-3\end{pmatrix}$*

***Sono congruenti*** su $\mathbb{C}\implies$ Hanno entrambe $r=2$
***Non sono congruenti*** in $\mathbb{R}\implies A$ ha 2 numeri positivi (*segnatura* $(2,0)$) e $M$ ha un numero negativo e uno positivo (*segnatura* $(1,1)$)

In effetti $\exists B:M=B^TAB$
Dove $B=\begin{pmatrix}1 &0 \\ 0 & i\end{pmatrix}$

$$
\begin{pmatrix}
1 & 0 \\
0 & i
\end{pmatrix}\begin{pmatrix}
2 & 0 \\
0 & 3
\end{pmatrix}\begin{pmatrix}
1 & 0 \\
0 & i
\end{pmatrix}=\begin{pmatrix}
2 & 0 \\
0 & -3
\end{pmatrix}
$$
