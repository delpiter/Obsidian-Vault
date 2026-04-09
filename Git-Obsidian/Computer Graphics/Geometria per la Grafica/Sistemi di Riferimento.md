>[[../../Algebra e Geometria/Basi dell'algebra/2 - Campi e Spazi Vettoriali#Base|base]] non basta per definire la posizione di un punto

Occorre definire un punto di riferimento.
- L'***origine del sistema di riferimento***.

## Frame
---
> Si estende il concetto di base a quello di *frame* in uno spazio affine.

>[!definizione]
>Dato un riferimento $F=(e_{1},e_{2},e_{3},P_{0})$, i punti ed i vettori dello spazio saranno esprimibili nel seguente modo:
>$$\begin{array}\ P=P_{0}+v=P_{0}+v_{1}e_{1}+v_{2}e_{2}+v_{3}e_{3} \\v=v_{1}e_{1}+v_{2}e_{2}+v_{3}e_{3}\end{array}$$

Gli scalari ($v_{1},v_{2},v_{3}$) sono le coordinate del punto $P$ nel ***sistema di riferimento*** $F=(e_{1},e_{2},e_{3},P_{0})$

###### Esempio
> Sistema di riferimento cartesiano in $\mathbb{R}^{2}$

$$
\mathbb{R}^{2}=(e_{1},e_{2},P_{0}),\qquad e_{1}\equiv(1,0),e_{2}\equiv(0,1),P_{0}=(0,0)
$$
Un punto $P$ di coordinate $x,y$ nel sistema di riferimento cartesiano $(e_{1},e_{2},P_{0})$ si esprime come:
$$
P=xe_{1}+ye_{2}+P_{0}=x(1,0)y(0,1)+(0,0)
$$

> Dato il sistema di riferimento:

$$
\mathbb{R}^{2}=(e_{1},e_{2},P_{0}),\qquad e_{1}\equiv(1,0),e_{2}\equiv(0,1),P_{0}=(4,4)
$$
Un punto $P$ di coordinate $(2,2)$ nel sistema di riferimento cartesiano $(e_{1},e_{2},P_{0})$ si esprime come:
$$
P=2(1,0)2(0,1)+(4,4)=(6,6)
$$
### Coordinate Omogenee
> Rappresentare sia i vettori che i punti usano tre scalari è ambiguo.

Vogliamo trovare un sistema di coordinate che porti ad una ***rappresentazione univoca***.

<u>Assunzione</u>

$$
1\cdot P=P\quad 0\cdot P=0
$$
>[!hint] Sistema Unificato

Sotto questa ipotesi, un vettore è allora dato da:
$$
v=v_{1}e_{1}+v_{2}e_{2}+v_{3}e_{3}+0P_{0}
$$
Un punto invece è dato da:
$$
v=v_{1}e_{1}+v_{2}e_{2}+v_{3}e_{3}+1P_{0}
$$

>[!tldr] Idea
>L'idea è quella di ***aggiungere una dimensione extra***.
>Ogni punto/vettore è definito da 4 coordinate.
>- Coordinate del *Punto*
>
>$$(v_{1},v_{2},v_{3},1)^{T}$$
>- Coordinate del *Vettore*
>
>$$(v_{1},v_{2},v_{3},0)^{T}$$

Quindi:
$$
P=[v_{1},v_{2},v_{3},1]\begin{bmatrix}
e_{1} \\
e_{2} \\
e_{3} \\
P_{0}
\end{bmatrix}
$$
E
$$
v=[v_{1},v_{2},v_{3},0]\begin{bmatrix}
e_{1} \\
e_{2} \\
e_{3} \\
P_{0}
\end{bmatrix}
$$
### Cambio di Sistema di Riferimento
>[!info] Concetto
>Consiste nel *cambio delle coordinate* di un vettore/punto da un ***sistema ad un altro***.

> Siano $F_{1}=(x,y,O)$ ed $F_{2}=(u,v,e)$ due [[#Frame]] di uno stesso spazio.

![[attachements/ReferenceSystemChange.png]]

Supponiamo di conoscere le coordinate del punto $P$ nel frame $F_{2}$ e vogliamo vedere quali sono le sue coordinate nel frame $F_{1}$

>[!failure] Procedura
 
Esprimiamo i vettori e origine di $F_{2}$ in termini di vettori e origine di $F_{1}$:
$$
\begin{array}
\ u=x_{u}x+y_{u}y+0\cdot O \\
v=x_{v}x+y_{v}y+0\cdot O \\
e=x_{e}x+y_{e}y+1\cdot O
\end{array}
$$
- In forma matriciale:
$$
\begin{bmatrix}
u \\
v \\
e
\end{bmatrix}=\begin{bmatrix}
x_{u} & y_{u} & 0 \\
x_{v} & y_{v} & 0 \\
x_{e} & y_{e} & 1
\end{bmatrix}\begin{bmatrix}
x \\
y \\
O
\end{bmatrix}
$$
La matrice $M=\begin{bmatrix}x_{u} & y_{u} & 0 \\x_{v} & y_{v} & 0 \\x_{e} & y_{e} & 1\end{bmatrix}$ rappresenta il [[../../Algebra e Geometria/Applicazioni/6 - Cambiamenti di Base|cambiamento del sistema di riferimento]] da $F_{1}$ ad $F_{2}$.

Il punto $P$ nel frame $F_{1}$ avrà coordinate omogenee $a^{T}=[x_p, y_{p},1]$
Il punto $P$ nel frame $F_{2}$ avrà coordinate omogenee $b^{T}=[u_p,v_{p}, 1]$

In forme matriciali:
$$
P=a^{T}\begin{bmatrix}
x \\
y \\
O
\end{bmatrix}\qquad P=b^{T}\begin{bmatrix}
u \\
v \\
e
\end{bmatrix}
$$
>[!question] Ora vogliamo che le due rappresentazioni forniscano lo stesso punto

$$
a^{T}\begin{bmatrix}
x \\
y \\
O
\end{bmatrix}=b^{T}\begin{bmatrix}
u \\
v \\
e
\end{bmatrix}
$$
Ma sappiamo che:
$$
\begin{bmatrix}
u \\
v \\
e
\end{bmatrix}=M\begin{bmatrix}
x \\
y \\
O
\end{bmatrix}
$$
> Quindi segue che:

$$
a^{T}\begin{bmatrix}
x \\
y \\
O
\end{bmatrix}=bM^{T}\begin{bmatrix}
x \\
y \\
O
\end{bmatrix}
$$
Segue quindi:
- $a^{T}=b^{T}M \implies a=M^{T}b,\ b=(M^{T})^{-1}a$

$$
\begin{bmatrix}
x_{p} \\
y_{p} \\
1
\end{bmatrix}=\begin{bmatrix}
x_{u} & x_{v} & x_{e} \\
y_{u} & y_{v} & y_{e} \\
0 & 0 & 1
\end{bmatrix}\begin{bmatrix}
u_{p} \\
v_{p} \\
1
\end{bmatrix}\implies \begin{bmatrix}
u_{p} \\
v_{p} \\
1
\end{bmatrix}=\begin{bmatrix}
x_{u} & x_{v} & x_{e} \\
y_{u} & y_{v} & y_{e} \\
0 & 0 & 1
\end{bmatrix}^{-1}\begin{bmatrix}
x_{p} \\
y_{p} \\
1
\end{bmatrix}
$$

## Trasformazioni Geometriche
---
>[!definizione] Trasformazioni Affini
>Le ***trasformazioni geometriche*** sono lo strumento che consente di *manipolare* punti e vettori all'interno del mondo dell'applicazione grafica.

Sono funzioni che mappano un punto in un altro punto.
- Permettono di traslare, ruotare, scalare o deformare oggetti, permettendo di istanziarli con attributi diversi nello *spazio di coordinate del mondo*.

>[!important] Una trasformazione geometrica affine è una trasformazione lineare

$$
f(aP+bQ)=af(P)+bf(Q)
$$
- Note le trasformazioni dei vertici, si possono ottenere le trasformazioni di combinazioni lineari dei vertici combinando linearmente le trasformazioni dei vertici.
	- **Non** è necessario ricalcolare le trasformazioni per *ogni combinazione*.

>Le trasformazioni affini preservano:

***Collinearità***
- I punti di una linea giacciono ancora su di una linea dopo la trasformazione.

***Rapporto tra le distanze***
- Il punto medio di un segmento *rimane il punto medio* anche dopo la trasformazione.

>[!info]
>Ogni trasformazione geometrica complessa può essere decomposta in una concatenazione di ***trasformazioni geometriche elementari***:
>- *Traslazione*, *Scala* e *Rotazione*
>
> Altre trasformazioni sono possibili ma **derivabili dalle precedenti**.
> - Riflessione rispetto ad un *asse*/*punto*, *deformazione*. 

Queste trasformazioni modificano le coordinate di un oggetto per ottenerne un altro simile, ma differente per ***posizione***, ***orientamento*** e ***dimensione***.

Le trasformazioni sono usate per:
- *Posizionare* gli oggetti nella scena
- Cambiarne la *forma*
- Creare *copie* degli oggetti
- *Animazioni*

### Traslazione
>[!definizione]
> Traslare una primitiva geometrica nel piano significa muovere ogni suo punto $P(x,y)$ di $d_{x}$ unità lungo l'asse $x$ e di $d_{y}$ unità lungo l'asse $y$, fino a raggiungere la nuova posizione $P'(x',y')$ dove:
> $$x'=x+d_{x}\qquad y'=y+d_{y}$$

In ***notazione matriciale***:
$$
P=\begin{bmatrix}
x \\
y
\end{bmatrix}\qquad P'=\begin{bmatrix}
x' \\
y'
\end{bmatrix}\qquad T=\begin{bmatrix}
d_{x} \\
d_{y}
\end{bmatrix}
$$
$$
P'=P+T
$$
- Ma questa operazione è *diversa* rispetto alla **rotazione** e alla **scalatura** (somma vs. prodotto).
	- Questo causa problemi all'interno della [[../Rendering Pipeline/Rendering Graphics Pipeline]].

Per risolvere questo problema si sfruttano le *coordinate omogenee*.
- Nella notazione in ***coordinate omogenee*** possiamo riscrivere la traslazione come:
$$
\begin{bmatrix}
x' \\
y' \\
1
\end{bmatrix}=\begin{bmatrix}
1 & 0 & d_{x} \\
0 & 1 & d_{y} \\
0 & 0 & 1
\end{bmatrix}\begin{bmatrix}
x \\
y \\
1
\end{bmatrix}
$$
> Esempio

![[attachements/TranslationExample.png]]


> Siano $F_{1}=(x,y,O)$ e $F_{2}=(u,v,e)$

![[attachements/Translation.png]]

Il punto $P$ ha coordinate omogenee $a^{T}=(x_{p},y_{p},1)$ in $F_{1}$ e $b^{T}=(u_{p},v_{p},1)$ in $F_{1}$

Esprimiamo i vettori *base* di $F_{2}$ con i vettori di $F_{1}$.
$$
\begin{cases}
u=x+0\cdot y+0\cdot O \\
v=0\cdot x +y+0\cdot O \\
e=x_{e}x+y_{e}y+1\cdot O
\end{cases}
$$
In ***forma matriciale***:
$$
M=\begin{bmatrix}
1 & 0 & 0 \\
0 & 1 & 0 \\
x_{e} & y_{e} & 1
\end{bmatrix}
$$

>[!done] Traslazione
>La matrice $M$ rappresenta il ***cambiamento del sistema di riferimento*** da $F_{1}$ a $F_{2}$.

### Scalatura
>[!definizione]
>Scelto un punto $C$ (fisso) di riferimento, ***scalare*** una primitiva geometrica, significa *riposizionare* rispetto a $C$ tutti i suoi punti in accordo ai *fattori di scala* ($s_{x}$ e $s_{y}$) scelti.

Se il punto fisso è l'origine degli assi, la trasformazione di $P$ in $P'$ si ottiene con:
$$
x'=s_{x}\cdot x\qquad y'=s_{y}\cdot y
$$
In ***notazione matriciale***:
$$
P=\begin{bmatrix}
x \\
y 
\end{bmatrix}\qquad P'=\begin{bmatrix}
x' \\
y'
\end{bmatrix}\qquad S=\begin{bmatrix}
s_{x} & 0 \\
0 & s_{y}
\end{bmatrix}
$$
$$
P'=S\cdot P
$$

> Esempio

![[attachements/ScaleExample.png]]

>[!hint] Osservazioni
>- Fattori di scala $<1$ avvicinano l'oggetto al punto di riferimento, $>1$ lo allontanano.
>- Se $s_{x}\neq s_{y}$ le proporzioni dell'oggetto ***non sono mantenute***.


Nella notazione in ***coordinate omogenee*** possiamo riscrivere la traslazione come:
$$
\begin{bmatrix}
x' \\
y' \\
1
\end{bmatrix}=\begin{bmatrix}
s_{x} & 0 & 0 \\
0 & s_{y} & 0 \\
0 & 0 & 1
\end{bmatrix}\begin{bmatrix}
x \\
y \\
1
\end{bmatrix}
$$
### Rotazione
>[!definizione]
>Fissato un punto $C$ di riferimento ed un *verso di rotazione*, ***ruotare*** una primitiva geometrica attorno a $C$ significa muovere tutti i suoi punti nel verso assegnato in maniera che **si conservi la distanza** da $C$.

Una rotazione di $\theta$ attorno all'origine degli assi è definita come:
$$
x'=x\cos\theta-y\sin\theta\qquad y'=x\sin\theta+y\cos\theta
$$
In ***termini matriciali***:
$$
\begin{bmatrix}
x' \\
y' \\
1 
\end{bmatrix}=\begin{bmatrix}
\cos\theta & -\sin\theta & 0 \\
\sin\theta & \cos\theta & 0 \\
0 & 0 & 1
\end{bmatrix}\begin{bmatrix}
x \\
y \\
1
\end{bmatrix}
$$
> Esempio

![[attachements/RotationExample.png]]

>[!hint] Osservazioni
>- Gli angoli sono considerati positivi quando misurati in senso orario.

> Siano $F_{1}=(x,y,O)$ e $F_{2}=(u,v,e)$

![[attachements/Rotation.png]]

Il punto $P$ ha coordinate omogenee $a^{T}=(x_{p},y_{p},1)$ in $F_{1}$ e $b^{T}=(u_{p},v_{p},1)$ in $F_{1}$

### Altre Trasformazioni
>[!tl;dr] Riflessione

> Rispetto all'asse $x$

$$
\begin{bmatrix}
x' \\
y' \\
1
\end{bmatrix}=\begin{bmatrix}
1 & 0 & 0 \\
0 & -1 & 0 \\
0 & 0 & 1
\end{bmatrix}\begin{bmatrix}
x \\
y \\
1
\end{bmatrix}
$$

> Rispetto all'asse $y$

$$
\begin{bmatrix}
x' \\
y' \\
1
\end{bmatrix}=\begin{bmatrix}
-1 & 0 & 0 \\
0 & 1 & 0 \\
0 & 0 & 1
\end{bmatrix}\begin{bmatrix}
x \\
y \\
1
\end{bmatrix}
$$
> Rispetto all'origine

$$
\begin{bmatrix}
x' \\
y' \\
1
\end{bmatrix}=\begin{bmatrix}
-1 & 0 & 0 \\
0 & -1 & 0 \\
0 & 0 & 1
\end{bmatrix}\begin{bmatrix}
x \\
y \\
1
\end{bmatrix}
$$

>[!tl;dr] Deformazione o shear

> Rispetto all'asse $x$

$$
\begin{bmatrix}
x' \\
y' \\
1
\end{bmatrix}=\begin{bmatrix}
1 & a & 0 \\
0 & 1 & 0 \\
0 & 0 & 1
\end{bmatrix}\begin{bmatrix}
x \\
y \\
1
\end{bmatrix}
$$

> Rispetto all'asse $y$

$$
\begin{bmatrix}
x' \\
y' \\
1
\end{bmatrix}=\begin{bmatrix}
1 & 0 & 0 \\
b & 1 & 0 \\
0 & 0 & 1
\end{bmatrix}\begin{bmatrix}
x \\
y \\
1
\end{bmatrix}
$$
> Rispetto all'origine

$$
\begin{bmatrix}
x' \\
y' \\
1
\end{bmatrix}=\begin{bmatrix}
1 & a & 0 \\
b & 1 & 0 \\
0 & 0 & 1
\end{bmatrix}\begin{bmatrix}
x \\
y \\
1
\end{bmatrix}
$$

### Composizione di Trasformazioni
> La rappresentazione in coordinate omogenee permette la ***concatenazione di trasformazioni***.

>[!warning] Ordine di Concatenazione
>L'*ordine di concatenazione* è importante poiché le trasformazioni geometriche sono associative ma ***non sono in generale commutative***.

La matrice della prima trasformazione che si vuole fare, deve essere l'***ultima ad essere moltiplicata***.
- La corretta sequenza delle trasformazioni $T_{1}$, $T_{2}$, $T_{3}$, $T_{4}$ è: 
$$
T=T_{4}\cdot T_{3}\cdot T_{2}\cdot T_{1}
$$

>[!hint] Non Commutatività

Una traslazione seguita da rotazione attorno all'origine (*sinistra*), una rotazione intorno all'origine seguita da una traslazione (*destra*).

![[attachements/NonCommutative.png]]

> Esempio

Rotazione oraria di un angolo $\theta$ attorno ad un punto $P$ generico.
1. **Traslazione** che muove $P$ nell'origine degli assi.
2. **Rotazione** attorno all'origine.
3. **Traslazione** opposta alla precedente che riporta $P$ nella sua posizione originale.

$$
R_{g}=\begin{bmatrix}
1 & 0 & P_{x} \\
0 & 1 & P_{y} \\
0 & 0 & 1
\end{bmatrix}\cdot\begin{bmatrix}
\cos\theta & -\sin\theta & 0 \\
\sin\theta & \cos\theta & 0  \\
0 & 0 & 1
\end{bmatrix}\cdot\begin{bmatrix}
1 & 0 & -P_{x} \\
0 & 1 & -P_{y} \\
0 & 0 & 1
\end{bmatrix}
$$

### Invertibilità delle Trasformazioni
>Sia $M$ una trasformazione tra quelle fondamentali.

Poiché $M$ non è [[../../Metodi Numerici per L'Intelligenza Artificiale/Equazioni Lineari/Sistemi Lineari#Matrici Singolari|singolare]], allora esiste la matrice inversa $M^{-1}$ tale che:
$$
MM^{-1}=I
$$
>[!check] Teorema
>Applicare ad un punto $P'$, trasformato di $P$ mediante $M$, la ***matrice inversa della matrice di trasformazione*** $M$ equivale a riottenere $P$.
>$$P'=MP\implies P=M^{-1}P'$$

Per le trasformazioni viste le matrici inverse sono *particolarmente semplici da calcolare*.

> Inversa della **Rotazione**: Rotazione di un angolo $-\theta$

$$
R(-\theta)=R^{T}(\theta)=R^{-1}(\theta)
$$
> Inversa della **Traslazione**

$$
T^{-1}(t)=T(-t)
$$
> Inversa della **Scala**

$$
S^{-1}(s)=S\left( \frac{1}{s_{x}}, \frac{1}{s_{y}} \right)
$$
### Trasformazioni 3D
>[!info]
>Se tutte le *trasformazioni nel piano* possono essere rappresentate da matrici $3\times3$ le ***trasformazioni nello spazio*** possono essere rappresentate da matrici $4\times4$.

#### Traslazione
> Una semplice estensione della matrice `2D`

$$
T(d_{x},d_{y},d_{z})=\begin{bmatrix}
1 & 0 & 0 & d_{x} \\
0 & 1 & 0 & d_{y} \\
0 & 0 & 1 & d_{z} \\
0 & 0 & 0 & 1
\end{bmatrix}
$$
#### Scalatura
> Una semplice estensione della matrice `2D`

$$
S(s_{x},s_{y},s_{z})=\begin{bmatrix}
s_{x} & 0 & 0 & 0 \\
0 & s_{y} & 0 & 0 \\
0 & 0 & s_{z} & 0 \\
0 & 0 & 0 & 1
\end{bmatrix}
$$

#### Rotazione
> La matrice di rotazione generica nello spazio è molto più complessa.

>[!hint] Proprietà
>Una qualunque rotazione `3D` si può ottenere come composizione di 3 rotazioni ***attorno gli assi coordinati***.

##### Attorno all'Asse x
>*Pitch*

$$
R_{x}(\theta)=\begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & \cos\theta & -\sin\theta & 0 \\
0 & \sin\theta & \cos\theta & 0  \\
0 & 0 & 0 & 1
\end{bmatrix}
$$

##### Attorno all'Asse y
>*Yaw*

$$
R_{y}(\theta)=\begin{bmatrix}
\cos\theta & 0 & \sin\theta & 0 \\
0 & 1 & 0 & 0 \\
-\sin\theta & 0 & \cos\theta & 0  \\
0 & 0 & 0 & 1
\end{bmatrix}
$$
##### Attorno all'Asse z
>*Roll*

$$
R_{z}(\theta)=\begin{bmatrix}
\cos\theta & -\sin\theta & 0 & 0 \\
\sin\theta & \cos\theta & 0  & 0\\
0 & 0 & 1 & 0  \\
0 & 0 & 0 & 1
\end{bmatrix}
$$


##### Attorno ad un Asse Generico
> Sia $\omega$ il versore di un generico asse di rotazione $\omega=(\omega_{x},\omega_{y},\omega_{z})$ e $\theta$ un angolo di rotazione.

>[!check] Formule di Rodrigues

$$
\begin{bmatrix}
\cos\theta+\omega^{2}_{x}(1-\cos\theta) & \omega_{x}\omega_{y}(1-\cos\theta)-\omega_{z}\sin\theta & \omega_{y}\sin\theta+\omega_{x}
\omega_{z}(1-\cos\theta) \\
\omega_{z}\sin\theta+\omega_{x}\omega_{y}(1-\cos\theta) & \cos\theta+\omega_{y}^{2}(1-\cos\theta) & -\omega_{x}\sin\theta+\omega_{y}
\omega_{z}(1-\cos\theta) \\
-\omega_{y}\sin\theta+\omega_{x}\omega_{z}(1-\cos\theta) & \omega_{x}\sin\theta+\omega_{y}\omega_{z}(1-\cos\theta) & \cos\theta+\omega_{z}^{2}(1-\cos\theta)
\end{bmatrix}
$$
