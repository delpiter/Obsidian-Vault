>*Sia $f$ un [[4 - Isomorfismo#Endomorfismo|endomorfismo]] abbiamo visto che data una base $v_{1},\dots,v_{n}$ di $V$ possiamo associare ad $f$ una matrice $n\times n$ che dipende dalla base scelta*

>[!question] Possiamo scegliere la base di $V$ in modo che la matrice di $f$ sia particolarmente semplice?

## Matrice Diagonale
---
>[!info] Definizione
>Una *matrice* $D_{n\times n}$ è ***diagonale*** se:
>$$d_{ij}=0,\quad \forall i\neq j$$

$$
D=\begin{pmatrix}
d_{1} & 0 & \dots & 0 & 0 \\
0 & d_{2} & \dots & 0 & 0 \\
0 & 0 & \dots & 0 & 0 \\
\dots  & \dots & \dots & \dots & \dots \\
0 & 0 & \dots & d_{n-1} & 0 \\
0 & 0 & \dots & 0 & d_{n}
\end{pmatrix}
$$

>[!tldr] Osservazione
>Due *matrici diagonali* sono semplici da moltiplicare tra loro!

Infatti, se:
$$
D=\begin{pmatrix}
d_{1} & 0 & \dots & 0 & 0 \\
0 & d_{2} & \dots & 0 & 0 \\
0 & 0 & \dots & 0 & 0 \\
\dots  & \dots & \dots & \dots & \dots \\
0 & 0 & \dots & d_{n-1} & 0 \\
0 & 0 & \dots & 0 & d_{n}
\end{pmatrix},
E=\begin{pmatrix}
e_{1} & 0 & \dots & 0 & 0 \\
0 & e_{2} & \dots & 0 & 0 \\
0 & 0 & \dots & 0 & 0 \\
\dots  & \dots & \dots & \dots & \dots \\
0 & 0 & \dots & e_{n-1} & 0 \\
0 & 0 & \dots & 0 & e_{n}
\end{pmatrix}
$$
$$
D\times E=\begin{pmatrix}
d_{1}e_{1} & 0 & \dots & 0 & 0 \\
0 & d_{2}e_{2} & \dots & 0 & 0 \\
0 & 0 & \dots & 0 & 0 \\
\dots  & \dots & \dots & \dots & \dots \\
0 & 0 & \dots & d_{n-1}e_{n-1} & 0 \\
0 & 0 & \dots & 0 & d_{n}e_{n}
\end{pmatrix}
$$
>[!done] Ottengo una *matrice diagonale*

>***Inoltre***, $\forall m\in \mathbb{Z}$


$$
D^m=\begin{pmatrix}
d_{1}^m & 0 & \dots & 0 & 0 \\
0 & d_{2}^m & \dots & 0 & 0 \\
0 & 0 & \dots & 0 & 0 \\
\dots  & \dots & \dots & \dots & \dots \\
0 & 0 & \dots & d_{n-1}^m & 0 \\
0 & 0 & \dots & 0 & d_{n}^m
\end{pmatrix}
$$

>[!tldr] Osservazione
>Calcolare il [[7 - Determinante di una Matrice#Determinante|determinante]] è *estremamente banale*

$$
\det(D)=d_{1}\cdot d_{2}\cdot ...\cdot d_{n}
$$
>[!tldr] Osservazione
>Se il $\det(D)\neq 0$, la ***matrice inversa*** è *estremamente banale* da calcolare

$$
D^{-1}=\begin{pmatrix}
d_{1}^{-1} & 0 & \dots & 0 & 0 \\
0 & d_{2}^{-1} & \dots & 0 & 0 \\
0 & 0 & \dots & 0 & 0 \\
\dots  & \dots & \dots & \dots & \dots \\
0 & 0 & \dots & d_{n-1}^{-1} & 0 \\
0 & 0 & \dots & 0 & d_{n}^{-1}
\end{pmatrix}
$$
>***Inoltre***

$$
D\begin{pmatrix}
d_{1} & 0 & \dots & 0 & 0 \\
0 & d_{2} & \dots & 0 & 0 \\
0 & 0 & \dots & 0 & 0 \\
\dots  & \dots & \dots & \dots & \dots \\
0 & 0 & \dots & d_{n-1} & 0 \\
0 & 0 & \dots & 0 & d_{n}
\end{pmatrix}
\times
D^{-1}\begin{pmatrix}
d_{1}^{-1} & 0 & \dots & 0 & 0 \\
0 & d_{2}^{-1} & \dots & 0 & 0 \\
0 & 0 & \dots & 0 & 0 \\
\dots  & \dots & \dots & \dots & \dots \\
0 & 0 & \dots & d_{n-1}^{-1} & 0 \\
0 & 0 & \dots & 0 & d_{n}^{-1}
\end{pmatrix}=
I_{n}
$$

>[!done] Le matrici diagonali sono *MERAVIGLIOSE*

## Autovettore e Autovalore
---
>[!info] Definizioni
>Sia $f:V\to V$ un [[4 - Isomorfismo#Endomorfismo|endomorfismo]]
>>[!abstract] Autovettore
>>Un ***autovettore*** è un vettore
>>$$v\in V, v\neq 0:\exists \lambda \in \mathbb{K}:f(v)=\lambda v$$
>
>>[!abstract] Autovalore
>>Un numero $\lambda\in\mathbb{K}$ è detto ***autovalore*** se
>>$$\exists v\in V,v\neq 0:f(v)=\lambda v$$

#### Esempio
>*Sia $f:\mathbb{R}^2\to \mathbb{R}^2:f(x,y)=(2y,2x)$*

- $e_{1}$ non è un *autovettore* $\implies f(e_{1})=2e_{2}$
- $e_{2}$ non è un *autovettore* $\implies f(e_{2})=2e_{1}$

$v_{1}=(1,1)$ è un *autovettore* di *autovalore* $2$
- $f(v_{1})=(2,2)=2v_{1}$

$v_{2}=(1,-1)$ è un *autovettore* di *autovalore* $-2$
- $f(v_{2})=(-2,2)=-2v_{2}$

>[!abstract] Matrici di $f$ nelle *due basi*

$$
M(e_{1},e_{2})=\begin{pmatrix}
0 & 2 \\
2 & 0
\end{pmatrix},
A(v_{1},v_{2})=\begin{pmatrix}
2 & 0 \\
0 & -2
\end{pmatrix}
$$

>[!tldr] Osservazione
>Se $f$ è un ***endomorfismo*** e $v_{1},\dots,v_{n}$ è una [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Base|base]] di $V$ composta da ***autovettori*** 
><u>Allora</u>
>- $f(v_{1})=\lambda_{1}v_{1}+0v_{2}+\dots+0v_{n}$
>- $f(v_{2})=0v_{1}+\lambda_{2}v_{2}+\dots+0v_{n}$
>- $\dots$
>- $f(v_{n})=0v_{1}+0v_{2}+\dots+\lambda_{n}v_{n}$
>>[!done] La matrice è una *matrice diagonale*

$$
\begin{pmatrix}
\lambda_{1} & 0  & \dots & 0 \\
0 & \lambda_{2}  & \dots & 0  \\
\dots & \dots & \dots & \dots\\
0 & 0  & \dots & \lambda_{n}
\end{pmatrix}
$$

## Diagonalizzare un'applicazione
---
>[!question] Si può diagonalizzare un'applicazione $f$?
>$\to$ Si può trovare una *base* di $V$ in cui la matrice di $f$ sia ***diagonale***?
>$\to$ Esiste una base di $V$ composta da *autovettori* di $f$?


>[!info] Procedimento per Passi
>1. Trovare gli [[#Autovettore e Autovalore|autovalori]] di $f$, *se esistono*
>2. Per ciascun *autovalore*, trovare gli [[#Autovettore e Autovalore|autovettori]]

### Trovare gli Autovalori
>[!info] Polinomio caratteristico
>Il ***polinomio caratteristico*** di $f$
>$$p(\lambda)=\det(f-\lambda id)$$

>[!Teorema]
>$\lambda_{i}$ è un ***autovalore*** di $f\iff p(\lambda_{i})=0$

#### Dimostrazione
$\lambda_{i}$ è un *autovalore* di $f\iff\exists v\in V,v\neq 0:f(v)=\lambda_{i}v$
- $\iff f(v)-\lambda_{i}id(v)=\underline{0}$
- $\iff \exists v\in V,v\neq 0:(f-\lambda_{i}id)(v)=\underline{0}$
- $\iff \exists v\neq 0,v\in \mathrm{ker}(f-\lambda_{i}id)$
- $\iff \mathrm{ker}(f-\lambda_{i}id)\neq \{ \underline{0} \}$
- $\iff f-\lambda_{i}id$ non è una ***funzione iniettiva***, quindi non è ***invertibile***
- $\iff \det(f-\lambda_{i}id)=0\iff p(\lambda_{i})=0$

##### Esempio
>$f:\mathbb{R}^2\to\mathbb{R}^2$ $f(x,y)=(2y,2x)$

>[!esempio] Scrivo la matrice di $f$ in una base qualsiasi, ad esempio la canonica

- $f(e_{1})=2e_{2}, f(e_{2})=2e_{1}$

$$
A=\begin{pmatrix}
0 & 2 \\
2 & 0
\end{pmatrix}
$$
>[!abstract] Cerco gli *autovalori*

$$
p(\lambda)=\det(A-\lambda I_{2})=\det\begin{pmatrix}
-\lambda  & 2 \\
2 & -\lambda
\end{pmatrix}=\lambda^2-4=0\iff\lambda=2,-2
$$
- Gli autovalori di $f$ sono $\lambda_{1}=2,\lambda_{2}=-2$

>[!question] Chi sono gli autovettori corrispondenti?

Per definizione, $v_{1}(x,y)\in \mathbb{R}^2$ è un ***autovettore*** di ***autovalore*** $\lambda_{1}=2$ se:
- $f(v_{1})=2v_{1}$, cioè se $(2y,2x)=f(x,y)=(2x,2y)$
$$
\begin{cases}
2y=2x \\
2x=2y
\end{cases}
$$
- $x=y$ è l'insieme degli *autovettori* validi con *autovalore* $\lambda_{1}=2$
	- Per esempio $v_{1}=(1,1)$, ma anche $v_{1}=(42,42)$

<u>Analogamente</u>
$v_{2}=(x,y)\in \mathbb{R}^2$ è un ***autovettore*** di ***autovalore*** $\lambda_{2}=-2$ se:
- $f(v_{2})=-2v_{2}$, cioè se $(2y,2x)=f(x,y)=(-2x,-2y)$

$$
\begin{cases}
2y=-2x \\
2x=-2y
\end{cases}
$$
- $x=-y$ è l'insieme degli *autovettori* validi con *autovalore* $\lambda_{2}=-2$
	- Per esempio $v_{2}=(1,-1)$, ma anche $v_{2}=(24,-24)$

##### Esempio
>$f:\mathbb{R}^3\to \mathbb{R}^3$, $f(x,y,z)=(2x,-4x-2y-8z,-4z)$

>[!teor] Nella base canonica, la matrice di $f$:

- $f(e_{1})=2e_{2}-4e_{2}$
- $f(e_{2})=-2e_{2}$
- $f(e_{3})=-8e_{2}-4e_{3}$

$$
A=\begin{pmatrix}2 & 0 & 0 \\-4 & -2 & -8 \\0 & 0 & -4\end{pmatrix}
$$
>[!abstract] Cerco gli *autovalori*

- $p(\lambda)=\det(A-\lambda I_{3})=\det\begin{pmatrix}2-\lambda & 0 & 0 \\-4 & -2-\lambda & -8 \\0 & 0 & -4-\lambda\end{pmatrix}=$
- $(2-\lambda)\det\begin{pmatrix}-2-\lambda & -8 \\ 0  & -4-\lambda\end{pmatrix}$
	- $(2-\lambda)(-2-\lambda)(-4-\lambda)=0\iff \lambda=2,-2,-4$

>[!question] Chi sono gli autovettori corrispondenti?

>[!abstract] $\lambda_{1}=2$
- $f(v_{1})=2v_{1}\implies 2v_{1}=(2x,2y,2z)$

$$
\begin{cases}
2x=2x \\
2y=-4x-2y-8z \\
2z=-4z
\end{cases}\iff\begin{cases}
4y=-4x \\
z=0
\end{cases}
$$
- Una soluzione è $v_{1}=(1,-1,0)$

>[!abstract] $\lambda_{2}=-2$
- $f(v_{2})=-2v_{2}$

$$
\begin{cases}
-2x=2x \\
-2y=-4x-2y-8z \\
-2z=-4z
\end{cases}\iff \begin{cases}
x=0 \\
z=0
\end{cases}
$$
- Una soluzione è $v_{2}=(0,1,0)$

>[!abstract] $\lambda_{3}=-4$
- $f(v_{3})=-4v_{3}$
$$
\begin{cases}
-4x=2x \\
-4y=-4x-2y-8z \\
-4z=-4z
\end{cases}\iff\begin{cases}
x=0 \\
y=4z
\end{cases}
$$
- Una soluzione è $v_{3}=(0,4,1)$

>[!done] Possiamo verificare che $v_{1},v_{2},v_{3}$ formano una base di $\mathbb{R}^3$
- Già sappiamo che in tale ***base*** la *matrice* di $f$ è:

- $f(v_{1})=2v_{1}$
- $f(v_{2})=-2v_{2}$
- $f(v_{3})=-4v_{3}$
$$
D=\begin{pmatrix}
2 & 0 & 0 \\
0 & -2 & 0 \\
0 & 0 & -4
\end{pmatrix}
$$

>[!tldr] Tutto questo funziona se $p(x)$ che è un polinomio a coefficienti in $\mathbb{K}$ ha i suoi zeri in $\mathbb{K}$

#### Esempio
>$f:\mathbb{R}^2\to\mathbb{R}^2,\ f(x,y)=(y,-x)$

>[!teor] Nella base *canonica* la matrice di $f$:

- $f(e_{1})=-e_{2}$
- $f(e_{2})=e_{1}$

$$
A=\begin{pmatrix}
0 & 1 \\
-1 & 0
\end{pmatrix}
$$
$$
A-\lambda I_{2}=\begin{pmatrix}
-\lambda & 1 \\
-1 & -\lambda
\end{pmatrix}
$$
- $\det(A-\lambda I_{2})=\lambda^2+1=0\implies \cancel{ \exists } \lambda\in\mathbb{R}$

>[!fail] $f$ non si *diagonalizza* su $\mathbb{R}$

Ma $\lambda^2+1=0$ ha soluzioni in $\mathbb{C}\to \lambda_{1}=i,\lambda_{2}=-i$

>[!abstract] Troviamo gli *autovettori*

$v_{1}=(x,y)\to f(v_{1})=iv_{1}$
- $(y,-x)=f(x,y)=(ix,iy)$

$$
\begin{cases}
y=ix \\
-x=iy
\end{cases}\underset{ \text{*i} }{ \implies }
$$
Una soluzione è $v_{1}=(1,i)$

Analogamente

$v_{2}=(x,y)\to f(v_{2})=-i$
- $(y,-x)=f(x,y)=(-ix,-iy)$

$$
\begin{cases}
y=-ix \\
-x=-iy
\end{cases}
$$
Una soluzione è $v_{2}=(1,-i)$

>[!done] $f$ ha per *matrice*

$$
D=\begin{pmatrix}
i & 0  \\
0 & i
\end{pmatrix}
$$

$f$ si diagonalizza come applicazione $\mathbb{C}^2\to\mathbb{C}^2$, ma non come applicazione $\mathbb{R}^2\to\mathbb{R}^2$

### Conclusione Diagonalizzazione
>Per $\mathbb{K}=\mathbb{Q},\mathbb{R},\mathbb{Z}_{p}$ esistono polinomi a coefficienti in $\mathbb{K}$ che non hanno i loro zeri in $\mathbb{K}$

Come abbiamo visto in precedenza:
- "***Il teorema fondamentale dell'algebra***"
	- Ogni polinomio a coefficienti in $\mathbb{C}$ ha soluzioni in $\mathbb{C}$


>[!done] Gli autovalori si possono sempre trovare a condizione di mettersi in un campo più grande

## Autospazio
---
>[!info] Definizione
>Sia $V$ uno [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Spazio Vettoriale|spazio vettoriale]] su $\mathbb{K}$, sia $f$ un [[4 - Isomorfismo#Endomorfismo|endomorfismo]] e sia $\lambda_{i}$ un suo autovalore
>L'***autospazio*** relativo a $\lambda_{i}$ è
>$$V\lambda_{i}=\{ v\in V:f(v)=\lambda_{i}v \}=\{ \text{tutti gli autovettori }\cup\{ \underline{0} \} \}$$

>[!abstract] Proprietà
>1. $V\lambda_{i}$ è un ***sottospazio vettoriale*** di $V$
>2. Se $\lambda_{i}\neq\lambda_{j},V\lambda_{i}\cap V\lambda_{j}=\{ \underline{0} \}$

### Dimostrazione
>*1)*

Se $v,u$ sono ***autovettori*** $\in V\lambda_{i}$, cioè
- $f(v)=\lambda_{i}v$
- $f(u)=\lambda_{i}u$
<u>Allora</u>

$$
f(v+u)=f(v)+f(u)=\lambda_{i}v+\lambda_{i}u=\lambda_{i}(u+v)\implies v+u\in V\lambda_{i}
$$
- Analogamente se:
$$
a\in\mathbb{K}, f(av)=af(v)=\lambda_{i}av\implies av\in V\lambda_{i}
$$

>*2)*

Sia $v\in V\lambda_{i}\cap V\lambda_{j}$ con $\lambda_{i}\neq \lambda_{j}$

<u>Allora</u>
$$
\lambda_{i}v=f(v)=\lambda_{j}v
$$
- Cioè
$$
\lambda_{i}v-\lambda_{j}v=\underline{0}
$$
- Cioè
$$
(\underbrace{ \lambda_{i}-\lambda_{j} }_{ \neq 0 })(v)=\underline{0}\implies v=\underline{0}
$$
## Molteplicità
---
>[!info] Molteplicità Geometrica
>La ***molteplicità geometrica*** è la *dimensione* dell'[[#Autospazio]]
>$$mg(\lambda_{i})=\text{dim} (V\lambda_{i})$$

>[!info] Molteplicità Algebrica
>La ***molteplicità algebrica*** di $\lambda_{i}$ ($ma(\lambda_{i})$) è la sua molteplicità come soluzione dell'equazione $p(\lambda)=0$

#### Esempio
>*Sia $p(\lambda)=(\lambda-2)^5(\lambda+3)^2(\lambda-7)$*

- $\lambda_{1}=2 \ \ \ \ \ ma(\lambda_{1})=5$
- $\lambda_{2}=-3 \ \ \ \ \ ma(\lambda_{2})=2$
- $\lambda_{3}=7 \ \ \ \ \ ma(\lambda_{3})=1$

### Proposizione sulla Molteplicità
>[!Proposizione]
>Sia $\lambda_{i}$ un ***autovalore*** di $f$
><u>Allora</u>
>$$1\leq mg(\lambda_{i})\leq ma(\lambda_{i})$$

#### Dimostrazione
>$mg(\lambda_{i})\geq1$

- Perché se fosse $mg(\lambda_{i})=0$
	- Cioè $\text{dim}(V\lambda_{i})=0\implies V\lambda_{i}=\{ \underline{0} \}$

Avremmo che ***non ci sono vettori non nulli*** tali che:
- $\exists v\in V, v\neq0:f(v)=\lambda_{i}v$

- Contraddicendo la [[#Autovettore e Autovalore|definizione di autovalore]]

>*Sia ora* $h=mg(\lambda_{i})=\text{dim}(V\lambda_{i})$ *e mostriamo che $ma(\lambda_{i})\geq h$*

Prendiamo una base $v_{1},\dots,v_{h}$ di $V\lambda_{i}$
- Completiamola ad una base di $V$, aggiungendo $v_{h+1},\dots,v_{n}$

>[!abstract] Scriviamo la matrice di $f$ in *tale base*

- $f(v_{1})=\lambda_{i}v_{1}$
- $f(v_{2})=\lambda_{i}v_{2}$
- $\dots$
- $f(v_{h})=\lambda_{i}v_{h}$
- $\dots$
- $f(v_{h+1})=?$
- $\dots$
- $f(v_{n})=?$

La matrice sarà di *questo tipo*:
$$
A=\begin{pmatrix}
\lambda_{i} & 0 & \dots & 0  & ?\\
0 & \lambda_{i} & \dots & 0  & ?\\
\dots & \dots & \dots & \dots  & ?\\
0 & 0 & \dots & \lambda_{i} & ? \\
0 & 0 & \dots & 0 & ?
\end{pmatrix}
$$
Siamo a conoscenza di $h$ ***colonne della matrice***

Cerchiamo gli ***autovalori***:
$$
A-id=\begin{pmatrix}
\lambda_{i}-\lambda & 0 & \dots & 0  & ?\\
0 & \lambda_{i}-\lambda & \dots & 0  & ?\\
\dots & \dots & \dots & \dots  & ?\\
0 & 0 & \dots & \lambda_{i}-\lambda & ? \\
0 & 0 & \dots & 0 & ?
\end{pmatrix}
$$

- $p(\lambda)=\det(A-\lambda id)=(\lambda_{i}-\lambda)^h\cdot q(\lambda)$

>[!done] Il fattore $\lambda_{i}-\lambda$ compare almeno $h$ volte in $p(\lambda)$
>Potrebbe esserci anche in $q(\lambda)$ oppure no

Quindi:
$$
ma(\lambda_{i})\geq h
$$
##### Esempio
>*Sia* $f:\mathbb{R}^2\to\mathbb{R}^2, f(x,y)=(2x+5y,2y)$

>[!abstract] Cerco gli autovalori sulla base canonica

$$
p(\lambda)=\det\begin{pmatrix}
2-\lambda & 5 \\
0 &  2-\lambda
\end{pmatrix}=(2-\lambda)^2
$$
- L'unico autovalore è $\lambda_{1}=2$ con $ma(\lambda_{1})=2$

$$
f(x,y)=2(x,y)\iff\begin{cases}
2x+5y=2x \\
2y=2y
\end{cases}\iff y=0
$$

- $V\lambda_{1}=\{ (x,0),x\in\mathbb{R} \}\implies mg(\lambda_{1})=1$

Prendiamo un vettore di $V\lambda_{1}$, $v_{1}=(1,0)$

>[!question] Possiamo prendere un altro vettore e completare a una base di $V$?

- Se prendo $v_{2}\in V\lambda_{1}$

>[!fail] Non riesco a completare una base, $v_{2}$ è linearmente dipendente da $v_{1}$

- Se prendo $v_{2}\cancel{ \in } V\lambda_{1}$

>[!fail] $v_{2}$ non è un *autovettore*

