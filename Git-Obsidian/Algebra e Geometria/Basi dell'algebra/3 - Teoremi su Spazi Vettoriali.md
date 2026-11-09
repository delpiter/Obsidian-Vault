## Teorema delle Coordinate
---
>[!info] Enunciato
>Un insieme di vettori $v_{1},\dots,v_{n}$ è una [[2 - Campi e Spazi Vettoriali#Base|base]] di $V\Leftrightarrow$ Ogni $v\in V$ si scrive in modo unico come [[2 - Campi e Spazi Vettoriali#Combinazioni Lineari|combinazione lineare]]
>Cioè:
>$$\forall v\in V\quad \exists!(a_{1},\dots,a_{n}),a_{i}\in \mathbb{K}:v=a_{1}v_{1}+\dots+a_{n}v_{n} $$
>In tal caso $a_{1},\dots,a_{n}$ sono dette le **coordinate del vettore** $v$ nella base $v_{1},\dots,v_{n}$

### Dimostrazione
> $\implies$

Siano $v_{1},\dots,v_{n}$ una base di $V$, cioè *generano* $V$ e sono *linearmente indipendenti*
- Dunque $\forall v\in V, \exists a_{1},\dots,a_{n}:v=a_{1}v_{1}+\dots+a_{n}v_{n}$

>[!tip] Vediamo perchè $a_{1},\dots,a_{n}$ sono unici

Supponiamo che esistano anche $b_{1},\dots,b_{n} \in \mathbb{K}:v=b_{1}v_{1}+\dots+b_{n}v_{n}$
- Oltre a $v=a_{1}v_{1}+\dots+a_{n}b_{n}$
$$\underline{0}=v-v=(a_{1}-b_{1})v_{1}+\dots+(a_{n}-b_{n})v_{n}$$
Ma poichè $v_{1},\dots,v_{n}$ sono linearmente indipendenti, ciò implica che 
$$a_{1}-b_{1}=0,\dots,a_{n}-b_{n}=0$$
- L'unica combinazione che da il vettore nullo è mettere tutti i coefficienti a $0$
Quindi:
- $a_{1}=b_{1},\dots,a_{n}=b_{n}$

>$\impliedby$

Siano $v_{1},\dots,v_{n}$ tali che $\forall v\in V,\exists! a_{1},\dots,a_{n}\in \mathbb{K}:v=a_{1}v_{1}+\dots+a_{n}v_{n}$
- Dunque $v_{1},\dots,v_{n}$ *generano* $V$ 
- Poichè dato $\underline{0}\in V$ gli unici  $a_{1},\dots,a_{n}\in\mathbb{K}:a_{1}v_{1}+\dots+a_{n}v_{n}=\underline{0}$ sono $a_{1}=0,\dots,a_{n}=0$

$v_{1},\dots,v_{n}$ sono *linearmente indipendenti* dunque sono una **base**

### Esempi
>[!tip] Siano $v_{1}=(-1,0),v_{2}=(2,0)\in V=\mathbb{R}^2$

Non sono nè generatori ne linearmente indipendenti
- In effetti in $\mathbb{R}^2$ ci sono *vettori* che non sono combinazione lineare di $v_{1},v_{2}$ ad esempio:
	- $u =(2,3)$
- E ci sono vettori che sono combinazione lineare di $v_{1},v_{2}$ in infiniti modi, ad esempio:
	- $w_{1}=(4,0)=2v_{2}=v_{2}-2v_{1}=-4v_{1}=\dots$

>[!tip] Siano $v_{1}=(2,1),v_{2}=(1,-1)\in V = \mathbb{R}^2$

>[!question] È vero che ogni $v\in\mathbb{R}^2$ è loro combinazione lineare?

Cioè che:
$$
\forall v=(x,y)\in\mathbb{R}^2,\ \exists !a_{1},a_{2}\in\mathbb{R}:a_{1}v_{1}+a_{2}v_{2}=v 
$$
- $(2a_{1}+a_{2},a_{1}-a_{2})=(x,y)$
$$
\begin{cases}
2a_{1}+a_{2} = x \\
a_{1}-a_{2} = y
\end{cases}
\Leftrightarrow
\begin{cases}
3a_{1}=x+y \\
3a_{2}=x-2y
\end{cases}
\Leftrightarrow\begin{cases}
a_{1}=\displaystyle{\frac{x+y}{3}} \\
a_{2}=\displaystyle{\frac{x-2y}{3}}
\end{cases}
$$
>[!done] Si, è vero

$\forall v\in V$ gli scalari $a_{1},a_{2}$ esistono e sono unici
- $v_{1},v_{2}$ è una base

>[!tip] $v_{1}=(1,1),v_{2}=(2,2)$

>[!question] È vero che $\forall v = (x,y)\in \mathbb{R}^2, \exists !a_{1},a_{2}\in\mathbb{R}:v=a_{1},a_{1}+a_{2}v_{2}$?

$$
(x,y)=(a_{1}+2a_{2},a_{1}+2a_{2})
$$
$$
\begin{cases}
a_{1}+2a_{2} =x \\
a_{1}+2a_{2} =y
\end{cases}
\begin{cases}
a_{1}=x-2a_{2} \\
0=x-y
\end{cases}
$$
>[!danger] Non ho soluzione per tutti i vettori $(x,y)$

Ma solo per quelli che hanno le due coordinate uguali
- $v_{1},v_{2}$ non generano $\mathbb{R}^2$


## Teorema della Dimensione
---
>[!info] Enunciato
>Sia $V$ uno [[2 - Campi e Spazi Vettoriali#Spazio Vettoriale|spazio vettoriale]] su $\mathbb{K}$ tutte le [[2 - Campi e Spazi Vettoriali#Base|basi]] di $V$ hanno lo stesso numero di elementi
>>[!done] Definizione
>>Tale numero è detto la **dimensione** di $V$

>[!tip] Siano $v_{1}=(2,1),v_{2}=(1,-1)\in V = \mathbb{R}^2$

Abbiamo visto che $v_{1}=(2,1),v_{2}=(1,-1)$ è una base di $\mathbb{R}^2$
- Quindi ogni base di $\mathbb{R}^2$ è composta da 2 vettori e diciamo che la dimensione $\mathbb{R}^2$ è $2$
- Scriviamo $\text{dim}(\mathbb{R}^2)=2$

### Base Canonica
>[!info] Intro
>Sia $\mathbb{K}$ un campo
>$V=\mathbb{K}^n=\{ (x_{1},\dots,x_{n}),x_{i}\in \mathbb{K} \}$ è uno spazio vettoriale su $\mathbb{K}$ di dimensione $n$, perchè una sua base è:
>- $e_{1}=(1,0,\dots,0),e_{2}=(0,1,0,\dots,0),\dots,e_{n}=(0,\dots,0,1)$

Questa è una base perchè
$$
\begin{array}{}
\forall v=(x_{1},\dots,x_{n})\in V \\
v=x_{1}e_{1}+x_{2}e_{2}+\dots+x_{n}e_{n}
\end{array}
$$
E $x_{1},\dots,x_{n}$ sono gli unici scalari che danno $v$ come combinazione lineare di $v_{1},\dots,v_{n}$

>[!done] Definizione
>$e_{1},\dots,e_{n}$ sono detti la Base Canonica di $\mathbb{K}^n$

#### Esempi
> $V=\mathbb{R}^3, e_{1}=(1,0,0),e_{2}=(0,1,0),e_{3}=(0,0,1)$

- $v = \left( \frac{3}{2},7,-4 \right) = \frac{3}{2}e_{1}+7e_{2}-4e_{3}$

>[!tip] Sia $V=\mathbb{K[x]}=\{ \text{ polinomi a coefficienti in }\mathbb{K} \}$

- Una base di $V$ è data dai monomi:
$$
1,x,x^2,x^3,x^4,\dots
$$
- Quindi la dimensione di $\mathbb{K}[x]=\infty$

>[!example] Considero il sottospazio di $\mathbb{K}[x]$
>$W=\mathbb{K}[x]_{\leq n}=\{ \text{polinomi di grado} \leq n \}$

$\mathbb{K}[x]_{\leq n}= \{ a_{0}+a_{1}x+a_{2}x^2+\dots+a_{n}x^n,a_{i}\in \mathbb{K} \}$

- Quindi $1,x,x^2,\dots,x^n$ è una base di $\mathbb{K}[x]_{\leq n}$ (anche detta **base canonica** di $\mathbb{K}[x]_{\leq n}$)
	- $\mathbb{K}[x]_{\leq n}$ ha dimensione $n+1$

##### Esempio
>$\mathbb{R}[x]_{\leq 2}=\{ p(x)=a_{2}x^2+a_{1}x+a_{0}, a_{0},a_{1},a_{2} \in \mathbb{R} \}$

Lo spazio vettoriale ha per base $1,x,x^2$

>[!question] Controllare se $p_{1}(x)=x^2+1,p_{2}(x)=x-1,p_{3}(x)=x^2-x$ è una base di $\mathbb{R}[x]_{\leq 2}$

$$
a_{1}p_{1}+a_{2}p_{2}+a_{3}p_{3} = (a_{1}+a_{3})x^2+(a_{2}-a_{3})x+(a_{1}-a_{2})
$$
- È vero che per ogni $p(x)=ax^2+bx+c, \exists!a_{1},a_{2},a_{3}:p=a_{1}p_{1}+a_{2}p_{2}+a_{3}p_{3}$?

$$
\begin{cases}
a_{1}+a_{3}=a \\
a_{2}-a_{3}=b \\
a_{1}-a_{2}=c
\end{cases}
\Leftrightarrow
\begin{cases}
a_{1}=\displaystyle{\frac{a+b+c}{2}} \\
a_{3} = a-a_{1} = \displaystyle{\frac{a-b-c}{2}} \\
a_{2}=a_{1}-c=\displaystyle{\frac{a+b-c}{2}}
\end{cases}
$$
>[!done] Trovata una unica soluzione

- Si, $\forall p(x)\in\mathbb{K}[x]_{\leq 2} \exists! a_{1},a_{2},a_{3} :p_{0}a_{1}p_{1}+a_{2}p_{2}+a_{3}p_{3}$
	- Ne consegue il fatto che $p_{1},p_{2},p_{3}$ sono una base


>[!tip] Osservazione
>Uno spazio vettoriale ha tante basi diverse.
>Le coordinate dello **stesso** vettore $v$, in **basi diverse** saranno **diverse**
