## Metodo di Gauss
---
>*Algoritmo semplice ed efficiente per risolvere sistemi lineari*
>*Funziona anche per sistemi dove il numero di equazioni è diverso dal numero di incognite*

>[!tip] Vediamo un esempio

$$
\begin{matrix}
1^a \\
2^a \\
3^a \\
4^a
\end{matrix}
\begin{cases}
2x_{1}-x_{2}+x_{3}+2x_{4}=1 \\
4x_{1}-x_{2}-3x_{3}-x_{4}=-1 \\
-2x_{1}-x_{2}+x_{3}+x_{4} = 1 \\
x_{1}+x_{2}+x_{3}+x_{4} = 2
\end{cases}
$$
>[!example] Primo Step

*Non tocco la prima equazione*
Sommo a ciascuna equazione, dalla $2^a$ in poi, un *multiplo* della $1^a$ equazione
- In modo tale che il *coefficiente* di $x_{1}$ **si annulli**

$$
\begin{matrix}
1^a \\
2^a-2\cdot1^a \\
3^a+ 1^a \\
4^a-\frac{1}{2}\cdot 1^a
\end{matrix}
\begin{cases}
2x_{1}-x_{2}+x_{3}+2x_{4}=1 \\
0x_{1}+x_{2}-5x_{3}-5x_{4}=-3 \\
0x_{1}-2x_{2}+2x_{3}+3x_{4} = 2 \\
0x_{1}+\frac{3}{2}x_{2}+\frac{1}{2}x_{3}+0x_{4} = 2
\end{cases}
$$
>[!example] Secondo Step

*Non tocco più la prima e la seconda equazione*.
Sommo a ciascuna equazione, dalla $3^a$ in poi, un *multiplo* dilla $2^a$ equazione
- In modo tale che il *coefficiente* di $x_{2}$ **si annulli**
$$
\begin{matrix}
1^a \\
2^a \\
3^a+2\cdot2^a \\
4^a-\frac{3}{2}2^a
\end{matrix}
\begin{cases}
2x_{1}-x_{2}+x_{3}+2x_{4}=1 \\
0x_{1}+x_{2}-5x_{3}-5x_{4}=-3 \\
0x_{1}-0x_{2}-8x_{3}-7x_{4} = -4 \\
0x_{1}+0x_{2}+8x_{3}+\frac{15}{2}x_{4} = 6
\end{cases}
$$
>[!example] Terzo Step

*Non tocco più la prima, la seconda e la terza equazione*.
Sommo a ciascuna equazione, dalla $4^a$ in poi, un *multiplo* della $3^a$ equazione
- In modo tale che il *coefficiente* di $x_{3}$ **si annulli**
$$
\begin{matrix}
1^a \\
2^a \\
3^a \\
4^a+3^a
\end{matrix}
\begin{cases}
2x_{1}-x_{2}+x_{3}+2x_{4}=1 \\
0x_{1}+x_{2}-5x_{3}-5x_{4}=-3 \\
0x_{1}-0x_{2}-8x_{3}-7x_{4} = -4 \\
0x_{1}+0x_{2}+0x_{3}+\frac{1}{2}x_{4} = 2
\end{cases}
$$

>[!done] Step Finale

Ora partendo dall'ultima equazione e salendo troviamo:
$$
\begin{cases}
\frac{1}{2}x_{4} = 2 \implies x_{4}=4 \\
8x_{3}=-4+7x_{4}=-24 \implies x_{3}=-3 \\
x_{2} = 5x_{3}+5x_{4}-3=2 \\
2x_{1} = 1+x_{2}-x_{3}-2x_{4} = -2 \implies x_{1}=-1
\end{cases}
$$
### $\infty$ soluzioni
>Quando ci sono $\infty$ soluzioni, il metodo di gauss mi aiuta a esprimerle in [[Basi dell'algebra/4 - Forme Parametriche e Cartesiane#Forme per Descrivere un Sottospazio Vettoriale|forma parametrica]]
#### Esempio
$$
\begin{cases}
x_{1}+x_{2}-3x_{3}+2x_{4}+13x_{5}-8x_{6}=0 \\
0x_{1}+0x_{2}-x_{3}+2x_{4}+x_{5}+x_{6} =0 \\
0x_{1}+0x_{2}+x_{3}-2x_{4}+2x_{5}+11x_{6}=0 \\
0x_{1}+0x_{2}+0x_{3}+0x_{4}+x_{5}+x_{6} =0 \\
0x_{1}+0x_{2}+0x_{3}+0x_{4}-3x_{5}+x_{6}=0 \\
0x_{1}+0x_{2}+0x_{3}+0x_{4}+0x_{5}+7x_{6} =0
\end{cases}
$$

$$
\begin{cases}
x_{1}+x_{2}-3x_{3}+2x_{4}+13x_{5}-8x_{6}=0 \implies x_{1}=s-4t\\
0x_{1}+0x_{2}\cancel{ -x_{3} }+\cancel{ 2x_{4} }+x_{5}+x_{6} =0 x_{2}=s\in\mathbb{R}\\
0x_{1}+0x_{2}+x_{3}-2x_{4}+2x_{5}+11x_{6}=0 \implies x_{3}-2t =0 \implies x_{3}=2t\\
0x_{1}+0x_{2}+0x_{3}+0x_{4}+x_{5}+x_{6} =0 \implies x_{4} = t\in\mathbb{R}\\
0x_{1}+0x_{2}+0x_{3}+0x_{4}-3x_{5}+x_{6}=0 \implies x_{5}=0\\
0x_{1}+0x_{2}+0x_{3}+0x_{4}+0x_{5}+7x_{6} =0 \implies x_{6}=0
\end{cases}
$$
L'insieme delle soluzioni è:
$$
\{ (4t-s,s,2t,t,0,0 ), t,s \in\mathbb{R}\}
$$

### Gauss Con Matrici
>*È possibile usare una matrice nella risoluzione di un sistema con il metodo di Gauss*

Basta affiancare la matrice $A$ dei ***coefficienti delle incognite*** con $b$, il vettore dei ***termini noti***
Ottenendo:
- $A|b$
Procedendo nello stessa maniera di un ***normale sistema***

Dopo $m-1$ passi ottengo una matrice a ***scala***
$$
A^{m-1}|b^{m-1}=\begin{pmatrix}
* & *  & \dots  & * & \mid & * \\
0 & *  & \dots  & * & \mid & * \\
0 & 0  & \dots  & * &  \mid & * \\
\dots  & \dots  & \dots &  ... & \mid  & \dots \\
0 & 0  & \dots  & 0& \mid & *
\end{pmatrix}
$$
Dove  $rk(A^{m-1})=rk(A)$ e le soluzioni di $A^{m-1}x=b^m-1$ ***sono le stesse*** di $Ax=b$

Possiamo fare un ulteriore passaggio
- ***Moltiplichiamo*** ogni riga ***non nulla*** di $A^{m-1}\mid b^{m-1}$  per l'inverso del suo ***primo elemento non nullo***, in modo da ottenere:

$$
\overline{A}\mid\overline{b}=\begin{pmatrix}
1 & *  & \dots  & * & \mid & * \\
0 & 1  & \dots  & * & \mid & * \\
0 & 0  & \dots  & 1 &  \mid & * \\
\dots  & \dots  & \dots &  ... & \mid  & \dots \\
0 & 0  & \dots  & 0& \mid & *
\end{pmatrix}
$$
- Chiamiamo ***pivot*** il *primo* elemento ***non nullo*** di ogni riga ***non nulla***

>[!tldr] Osservazione
>$\overline{A}\mid\overline{b}$ ha le stesse soluzioni di $Ax=b$

>[!tldr] Osservazione
>$rk(A)=rk(\overline{A})$ *massimo numero di colonne* di $A$ tra lori **linearmente indipendenti**
>E in $\overline{A}$ si vede facilmente che il numero massimo di *colonne linearmente indipendenti* è ***uguale*** al numero *massimo di righe linearmente* indipendenti
>Quindi $rk(A)=$ numero massimo di righe linearmente indipendenti

- Si vede facilmente che $rk(\overline{A})=$ numero di ***pivot*** $=$ numero di righe *linearmente indipendenti*

#### Esempio
>*Trovare le soluzioni del seguente sistema*

$$
\begin{cases}
x+2y-z=1 \\
2x+7y-5z=1 \\
-x+y-2z=-2
\end{cases}
$$
Possiamo vedere il sistema come $A\underline{x}=b$ con $\underline{x}=\begin{pmatrix}x \\y \\z\end{pmatrix}$:
$$
(A|b)=\begin{pmatrix}
1 & 2 & -1  & | & 1 \\
2 & 7 & -5 & | & 1 \\
-1 & 1 & -2 & | & -2 
\end{pmatrix}\implies A'|b'=\begin{pmatrix}
1 & 2 & -1  & | & 1 \\
0 & 3 & -3 & | & -1 \\
0 & 3 & -3 & | & -1
\end{pmatrix}
$$
$$
\implies A''|b''
\begin{pmatrix}
1 & 2 & -1  & | & 1 \\
0 & 3 & -3 & | & -1 \\
0 & 0 & 0 & | & 0
\end{pmatrix}\implies \overline{A}|\overline{b}\implies A''|b''
\begin{pmatrix}
1 & 2 & -1  & | & 1 \\
0 & 1 & -1 & | & -\frac{1}{3} \\
0 & 0 & 0 & | & 0
\end{pmatrix}
$$

Ora basta risolvere un sistema più semplice di quello di prima
$$
\begin{cases}
x+2y-z=1 \\
y-z=-\frac{1}{3} \\
0=0
\end{cases}\iff \begin{cases}
x=1+z-2y=1+t-2t+\frac{2}{3} \\
y=-\frac{1}{3}+z=t-\frac{1}{3} \\
z=t
\end{cases}
$$


## Risoluzione con Matrici
---

>[!abstract] Consideriamo un sistema a $m$ equazioni lineari in $n$ incognite

$$
\begin{cases}
a_{11}x_{1}+a_{12}x_{2}+\dots+a_{1n}x_{n}=b_{1} \\
a_{21}x_{1}+a_{22}x_{2}+\dots+a_{2n}x_{n}=b_{2} \\
\dots \\
a_{m1}x_{1}+a_{m2}x_{2}+\dots+a_{mn}x_{n}=b_{m}
\end{cases}
$$

Dove:
- $(b_{1},b_{2},\dots,b_{m})$ sono i ***termini noti***
- $a_{ij}$ sono i ***coefficienti delle equazioni***

>[!done] Posso scrivere questo sistema nella forma
>$$Ax=b$$
>Dove:
>$A=$ matrice dei ***coefficienti***
>$x=$ vettore delle ***incognite***
>$b=$ vettore dei ***termini noti***

Consideriamo ora un altro metodo di risoluzione
### Metodo di Cramer
>[!Proposizione]
>Sia $Ax=b$ un sistema di $n$ equazioni in $n$ variabili
>- $A\in\mathcal{M}_{n\times n}$
><u>Allora</u>
>- Se $\det(A)=0$ la **soluzione** *non esiste* o *non è unica*
>- Se $\det(A)\neq 0$ la **soluzione** *esiste* ed è *unica* ed è data da:
>$$x=A^{-1}b=\det(A)^{-1}\text{cof}(A)^Tb$$

#### Dimostrazione
>Se $\det(A)=0$, $A$ non è ***invertibile***

- L'applicazione $x\mapsto Ax$ non è ***biunivoca***

Se non è ***biunivoca***:

>[!abstract] Non è suriettiva
>Non esiste $x:Ax=b$
><u>Ovvero</u>
>La soluzione ***non esiste***

*Oppure*

>[!abstract] Non è iniettiva
>Per qualche $b$ esistono $x,x':Ax=b=Ax'$
><u>Ovvero</u>
>La soluzione ***non è unica***

>Se $\det(A)\neq 0$

- $A$ è ***invertibile***, $A^{-1}=\det(A)^{-1}\text{cof}(A)^T$

$$
Ax=b\implies x=A^{-1}b
$$
È l'***unica soluzione*** del *sistema lineare*

>[!warning] Limiti

Questo metodo funziona solamente quando il ***numero di incognite*** è uguale al ***numero di equazioni***
- In oltre è molto costoso in ***termini computazionali***
##### Esercizio 1
$$
\begin{cases}
x-2y=3 \\
-2x+4y = 7
\end{cases}\implies\det\begin{pmatrix}
1 & -2 \\
-2 & 4
\end{pmatrix}=0
$$
- Il sistema *non ha soluzione* poiché la prima equazione equivale a:
	- $-2(x-2y)=-2\cdot3=-6\neq 7$

##### Esercizio 2
$$
\begin{cases}
x-2y=3 \\
-2x+4y =-6
\end{cases}\implies\det\begin{pmatrix}
1 & -2 \\
-2 & 4
\end{pmatrix}=0
$$
- Il sistema ha *infinite soluzioni*
	- Tutti gli $(x,y):x=3+2y$

##### Esercizio 3
[[Applicazioni/8 - Matrici Invertibili#Esercizio|Riprendendo Questo esercizio]]

$$
\begin{cases}
3x+5y = 2 \\
2x+4y =-1
\end{cases}
$$
$$
\det\begin{pmatrix}
3 & 5 \\
2 & 4
\end{pmatrix}=2 \neq 0
$$
- La *soluzione* ***esiste ed è unica*** per ogni $b$
$$
A^{-1}=\begin{pmatrix}
2 & -\frac{5}{2} \\
1 & \frac{3}{2}
\end{pmatrix}
$$
Quindi per trovare le soluzioni:
$$
\begin{pmatrix}
x \\
y
\end{pmatrix}
=A^{-1}b=\begin{pmatrix}
2 & -\displaystyle\frac{5}{2} \\
1 &  \displaystyle\frac{3}{2}
\end{pmatrix}\times \begin{pmatrix}
2 \\
-1
\end{pmatrix}=\begin{pmatrix}
\displaystyle\frac{13}{2} \\
-\displaystyle\frac{7}{2}
\end{pmatrix}$$

### Ruchè-Capelli

>[!check] Teorema di Rouchè-Capelli
>Sia $Ax=b$ un sistema di $m$ equazioni in $n$ incognite
>Sia $A|b$ la matrice ottenuta *affiancando il vettore dei termini noti* alla matrice $A$
>Il sistema $Ax=b$ ammette almeno una soluzione $\iff rg(A|b)=rg(A)$.
>>[!quote] A Parole
>>La matrice ammette soluzioni se  $A$ e $A|b$ hanno lo stesso [[Applicazioni/2 - Teorema del Rango|rango]].

#### Dimostrazione
>*Se il* $rg(A|b)=rg(A)$

Vuol dire che $b$ è ***combinazione lineare*** dei vettori colonna $v_{1},\dots,v_{n}$ di $A$, cioè:
$$
\exists x_{1},\dots,x_{n}\in\mathbb{K}:b=x_{1}v_{1}+\dots+x_{n}v_{n}
$$

Ma allora:
$$
A\times\begin{pmatrix}
x_{1} \\
\dots \\
x_{n}
\end{pmatrix}=\begin{pmatrix}
b_{1} \\
\dots \\
b_{n}
\end{pmatrix}
$$
- Cioè
$$
x=\begin{pmatrix}
x_{1} \\
\dots \\
x_{n}
\end{pmatrix}
$$

>[!done] Il sistema ha una ***unica soluzione***

>*Se invece $rg(A|b)>rg(A)$*

Vuol dire che $b$ non è ***combinazione lineare*** dei vettori colonna di $A$
- Non esistono gli $x_{1},\dots,x_{n}$ suddetti
	- Non esiste $x:Ax=b$

>[!fail] Il sistema *non ha soluzione*

## Insieme delle Soluzioni
---
>[!info] Teorema
>Sia $Ax=b$ un sistema lineare
>Consideriamo il sistema lineare omogeneo associato $Ax=\underline{0}$
><u>Allora</u>
>1. L'insieme $U$ delle soluzioni di $Ax=\underline{0}$ è un [[Basi dell'algebra/2 - Campi e Spazi Vettoriali#Sottospazio Vettoriale|sottospazio vettoriale]] di $\mathbb{K}^n$ di dimensioni $n-rk(A)$
>2. L'insieme $S$ delle soluzioni di $Ax=b$, ***se non è vuoto***, è un [[Basi dell'algebra/2 - Campi e Spazi Vettoriali#Sottospazio Affine|sottospazio affine]] di $\mathbb{K}^n$ ottenuto traslando $U$ con un qualsiasi $p \in S$, di dimensioni $n-rk(A)$, cioè:
>$$S=\{ u+p,u\in U \}$$

>[!done] In Breve
>L'*insieme delle soluzioni* di un sistema lineare  $Ax=b$, se non è vuoto, è un ***sottospazio affine***, ovvero è ottenuto ***traslando*** l'insieme delle soluzioni del sistema lineare omogeneo $Ax=\underline{0}$
>Questi sottospazi hanno dimensione $n-rk(A)$, dove $n$ è il ***numero di incognite***

### Dimostrazione
>*Dimostrazione punto $1$*

Siano $u_{1},u_{2}\in U$, dunque $Au_{1}=\underline{0},Au_{2}=\underline{0}$
- Quindi $A(u_{1}+u_{2})=Au_{1}+Au_{2}=\underline{0}+\underline{0}=\underline{0}$

>[!done] $u_{1}+u_{2}\in U$

Analogamente, se $u\in U,a \in\mathbb{K}$
- $A(au)=aAu=a\underline{0}=\underline{0}$

>[!done] $au\in U$


Quindi $U$ è un sottospazio vettoriale di $\mathbb{K}^n$

>[!abstract] D'altra Parte

$U$ è il nucleo dell'[[Applicazioni/1 - Applicazioni Lineari#Applicazione Lineare|applicazione lineare]]:
$$
f:\mathbb{K}^n\to\mathbb{K}^m,f(x)=Ax
$$

Per il [[Applicazioni/2 - Teorema del Rango]], $U$ ha dimensione:
$$
\text{dim}(\mathrm{ker}f)=\text{dim}(\mathbb{K}^n)-\text{dim}(\mathrm{Im}f)=n-rk(A)
$$


>*Dimostrazione punto $2$*

Da dimostrare una ***doppia implicazione***

Sia $u\in U$, cioè $Au=\underline{0}$ e sia $p \in S$, cioè $Ap=b$
- Allora $u+p \in S$ perché $A(u+p)=Au+Ap=\underline{0}+b=b$

*Quindi*:
$$
\{ u+p, u \in U \}\subseteq S
$$

Siano $p,p' \in S$, cioè $Ap=b,Ap'=b$
- Allora $p'-p \in U$ perché $A(p'-p)=Ap'-Ap=b-b=\underline{0}$

*Quindi* $p'=p+u$ dove $u \in U$

Cioè:
$$
S \subseteq \{ u+p,u\in U \}
$$

>[!done] $S=\{ u+p,u\in U \}$


