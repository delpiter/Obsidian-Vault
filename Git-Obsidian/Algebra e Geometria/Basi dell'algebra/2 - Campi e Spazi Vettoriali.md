## Campo
---
>[!info] Definizione
>Un **campo** è un insieme con due operazioni $+$ e $\cdot$ **commutative** e **associative** 
>Con **elementi neutri** $s,p$, tali che $a+s=a\quad ap=a$
>Con un **opposto** di ogni elemento $a+b = 0$
>Con **inverso** di ogni elemento non nullo $ab = 1$

Quasi tutte le cose fatte in questo corso valgono per un campo qualsiasi
- $\mathbb{Q}$ e $\mathbb{R}$ sono dei campi
- $\mathbb{N}$ e $\mathbb{Z}$ non lo sono

>[!question] $\mathbb{C}$ è un campo?
- Si!
$$
(a+ib)-(a-ib) = a^2\cancel{+ aib }\cancel{ -aib }-i^2b^2 = a^2+b^2
$$
$$(a+ib)^{-1}=\displaystyle{\frac{a-ib}{a^2+b^2}} =1$$

### Classi
>[!info] Definizione
>Dato $n\in\mathbb{N}, n\geq 2$, e dato $a\in\mathbb{Z}$, definiamo
>$$\overline{a}= \{ b\in\mathbb{Z}  : b\equiv a (n) \}$$

- Definiamo due operazioni $+,\cdot$ su $\mathbb{Z}_{n}$ come
	- $\overline{a}+\overline{b} = \overline{a+b}$
	- $\overline{a}\cdot \overline{b} = \overline{a\cdot b}$

#### Es
In $\mathbb{Z}_{3}$
- $\overline{1}+\overline{2} = \overline{0}$
- $1+2 =3 \equiv 0 (3)$

In $\mathbb{Z}_{5}$
- $\overline{3}\cdot \overline{4} = \overline{2}$ perchè $3\cdot4=12\equiv 2(5)$

#### Osservazione
$\mathbb{Z}_{n}$ è un campo $\Leftrightarrow n$ è **primo**

## Spazio Vettoriale
---
>[!info] Definizione
>Sia $\mathbb{K}$ un campo
>Uno **Spazio Vettoriale** su $\mathbb{K}$ è un insieme $V$ con 2 operazioni
>>[!tip] Somma di Vettori ($+$)
>>Associa due elementi di $V$ ad un altro elemento di $V$
>>>$v_{1},v_{2}\in V$ associa $v_{1}+v_{2}\in V$
>>
>>Soddisfa le seguenti **proprietà**:
>>- Commutativa
>>- Associativa
>>- Ha un numero neutro $\underline{0}$ e opposti
>
>>[!tip] Prodotto per scalare ($\cdot$)
>>Operazione che a $a \in \mathbb{K}, v\in V$ associa $a\cdot v\in V$
>>Soddisfa le seguenti **proprietà**
>>- Associativa
>>- Distributiva rispetto alla somma 
>>- Ha un elemento neutro

### Proprietà Somma
1. Proprietà Commutativa$$v_{1}+v_{2} = v_{2}+v_{1}, \forall v_{1},v_{2} \in V$$
2. Proprietà Associativa$$(v_{1}+v_{2})+v_{3}=v_{1}+(v_{2}+v_{3}),\forall v_{1},v_{2},v_{3}\in V$$
3. Elemento Neutro $$\exists \underline{0}\in V (\text{"vettore nullo"}):\underline{0}+v = v \ \forall v \in V$$
4. Elementi Opposti $$\forall v\in V, \exists -v\in V : v+(-v)=\underline{0}$$
### Proprietà Prodotto
$\forall\ v,v_{1},v_{2} \in V, \forall a,b \in \mathbb{K}$
5. Proprietà Associativa $$a(bv)=(ab)v$$
6. Proprietà Distributiva 
$$
\begin{array}
\ (a+b)v = av +bv \\
a(v_{1}+v_{2}) = av_{1}+av_{2}
\end{array}
$$
7. Elemento Neutro $$1v=v$$

### Esempi
1. Vettori **Geometrici**
![[attachements/Pasted image 20240219172214.png]]

2. Dato un campo $\mathbb{K}$, $n\geq 1$
$$
V=\mathbb{K}^n = \{ (x_{1},x_{2},\dots,x_{n}), x_{i}\in k, \forall i=1,2,3,\dots,n \}
$$
- È uno **spazio vettoriale** su $\mathbb{K}$ rispetto alle operazioni:
$$
\begin{array}
\ v_{1}=(x_{1},x_{2},\dots,x_{n}),v_{2}=(y_{1},y_{2},\dots,y_{n}) \\
v_{1}+v_{2} = (x_{1}+y_{1},x_{2}+y_{2},\dots,x_{n}+y_{n}) \\
av_{1}=(ax_{1},ax_{2},\dots,ax_{n})
\end{array}
$$
- Vettore "vuoto" $\underline{0}=(0,0,0,\dots,0)$

3. Polinomio
$\mathbb{K}[x]={\text{ polinomi a coefficientni in } \mathbb{K}}$

###### Es
$p(x)=2x^2-1, q(x)=x^3-3x+2 \in\mathbb{R}[x]$
$(p+q)(x)=x^3+2x^2-3x+1$
$\left(  \frac{5}{2} p\right )(x)=5x^2- \frac{5}{2}$

4. Funzioni
Sia $X$ un insieme
$V=\{ \text{funzioni }X\to \mathbb{K}\}$
- È uno spazio vettoriale rispetto alle operazioni:
	- $(f+g)(x)=f(x)+g(x)$
	- $(af)(x) = af(x)$

5. $\mathbb{C}$ è uno spazio vettoriale sul campo $\mathbb{R}$
Se $z_{1}=a+ib,z_{2}=c+id \in\mathbb{C}$
- $z_{1}+z_{2}= (a+c)+i(b+d)\in \mathbb{C}$

Sia $h\in\mathbb{R}, hz_{1}=ha+ihb$

### Riassunto
Dato uno spazio vettoriale $V$ su un campo $\mathbb{K}$ chiamiamo *scalari* gli elementi del campo $\mathbb{K}$

Chiamiamo invece *vettori* gli elementi dello spazio vettoriale $V$

#### Riepilogo esempi
- Nell'esempio `1` un vettore è una **freccia**
- Nell'esempio `2` un vettore è una **$n$-upla di numeri**
- Nell'esempio `3` un vettore è un **polinomio**
- Nell'esempio `4` un vettore è una **funzione**
- Nell'esempio `5` un vettore è un **numero complesso**

## Sottospazio Vettoriale
---
>[!info] Definizione
>Sia $\mathbb{K}$ un *campo* e sia $V$ uno *spazio vettoriale* su $\mathbb{K}$
>Un **Sottospazio Vettoriale** di $V$ è un sottoinsieme $U$ di $V$ non vuoto che è chiuso rispetto a tali operazioni
>$$U\subseteq V:\ \forall v_{1},v_{2}\in U,v_{1}+v_{2}\in U$$
>e
>$$\forall a \in\mathbb{K}, \forall v\in U, av\in U$$
>>[!done] In Breve
>>I risultati delle operazioni $+$ e $\cdot$ sono anche essi interni al sottoinsieme di $V$

### Esempi
#### Esempio 1
>Sia $\mathbb{K}=\mathbb{R}, V=\mathbb{R}^2=\{ (x,y):x,y\in\mathbb{R} \}$
>$U=\{ (x,y)\in\mathbb{R}^2 :y =2x\}$

>[!question] $U$ è un sottospazio vettoriale??

$$
\begin{array}
\ v_{1}=(x,2x)\ \ \ \ v_{2}=(x',2x') \in U \\
v_{1}+v_{2} = (x+x', 2(x+x'))\in U \\
av_{1} = a(x,2x) = (ax,2ax)\in U
\end{array}
$$
>[!done] Si, $U$ è un sottospazio vettoriale di $V$

#### Esempio 2
> $\mathbb{K}=\mathbb{R}, V = \mathbb{R}^2, S = \{ (x,y)\in\mathbb{R}^2 :xy\geq0\}$

>[!question] $S$ è un sottospazio vettoriale??

$$
\begin{array}
v_{1}=(1,2),v_{2}=(-2,-1)\in S \\
v_{1}+v_{2} = (-1,1) \cancel{ \in }S
\end{array}
$$

![[attachements/Pasted image 20240220175558.png]]
>[!error] No, $S$ non è un sottospazio vettoriale di $V$

#### Esempio 3
>Sia $V=\mathbb{R}[x]=\{ \text{polinomi a coefficienti in } \mathbb{R}\}$
>Sia $U=\{ \text{ polinomi di grado }2 \}$

>[!question] $U$ è un sottospazio vettoriale??

$$
p_{1}(x)=x^2-3x+4 \in U, p_{2}(x) = -x^2 +2x-3 \in U
(p_{1}+p_{2})(x) = -x+1 \cancel{ \in } U
$$
>[!error] No, $U$ non è un sottospazio vettoriale di $V$

> Sia invece $W=\{ \text{ polinomi di grado }\leq 2 \}=\{ a,b,c\in\mathbb{R} :ax^2+bx+c\}$

$$
p_{1}=ax^2+bx+c ,p_{2}=a'x^2+b'x+c
p_{1}+p_{2}=(a+a')x^2+(b+b')x+(c+c')
$$
- E analogamente l'altra operazione
>[!done] Si, $W$ è un sottospazio vettoriale di $V$

#### Esempio 4
>$\mathbb{K}=\mathbb{R},V=\{ \text{ funzioni }f:\mathbb{R}\to\mathbb{R} \}$
>$U=\{ \text{ funzioni continue } f:\mathbb{R}\to\mathbb{R} \}$

>[!done] $U$ è un sottospazio vettoriale di $V$ poichè somma e prodotto di funzioni continue è essa stessa una funzione continua

### Proprietà
>[!info] Definizione
>$U$ è un **sottospazio vettoriale** di $V \Leftrightarrow \forall v_{1},v_{2}\in U,\forall a_{1},a_{2}\in \mathbb{K}, a_{1}v_{1}+a_{2}v_{2}\in U$ 

>[!tip] Dimostrazione

>$\implies$

Siano $v_{1},v_{2} \in U$ e $a_{1},a_{2} \in \mathbb{K}$
- Poichè $U$ è un *sottospazio vettoriale*, $a_{1}v_{1},a_{2}v_{2} \in U \implies a_{1}v_{1}+a_{2}v_{2}\in U$

>$\impliedby$

Siano $v_{1},v_{2}\in U$ poichè $a_{1}v_{1}+a_{2}v_{2}\in U \forall a_{1},a_{2} \in \mathbb{K}$
- Scegliendo $a_{1}=1,a_{2}=1$ ho che $v_{1}+v_{2}\in U$
- Scegliendo $a_{2}=0$ ho che $a_{1}v_{1}\in U \forall a_{1}\in\mathbb{K}$

### Sottospazio Affine
>[!info] Definizione
>Un sottoinsieme $S$ di $\mathbb{K}^n$ è un ***sottospazio affine*** di dimensione $d$ di $\mathbb{K}^n$ se è ottenuto traslando un sottospazio vettoriale $U$ di dimensione $d$
>>[!done] In Altre Parole
>>$S$ è un ***sottospazio affine*** se 
>>$$\exists p\in \mathbb{K}^n, \text{ e un SSV } U\subseteq \mathbb{K}^n: S=\{ u+p,u\in U \}$$

#### Esempio
>*Consideriamo in $\mathbb{R}^2$*

- $U=\{ (x,y)\in\mathbb{R}^2|x+y=0 \}=\{ (t,-t),t\in\mathbb{R} \}$
- $S=\{ (x,y)\in\mathbb{R}^2|x+y=2 \}$


```functionplot
---
title: Sottospazio Affine
xLabel: 
yLabel: 
bounds: [-10,10,-10,10]
disableZoom: true
grid: true
---
f(x)=-x
g(x)=-x +2
```


$U$ è un ***sottospazio vettoriale***
$S$ ***non*** è un ***sottospazio vettoriale***
- $S$ è un ***sottospazio affine*** di $\mathbb{R}^2$ di dimensione $1$, ottenuto traslando $U$ con il vettore $(1,1)$
- $S=\{ (t,-t)+(1,1),t\in\mathbb{R} \}$

>[!tldr] Osservazione
>Il vettore $p=(1,1)$ ***non è unico***

Potrei prendere $p'=(2,0)$ o $p''=(0,2)$ o infinite altre scelte, ottenendo:
- $S=\{ u+p,u\in U \}=\{ u+p',u\in U \}=\{ u+p'',u\in U \}$

>[!done] Ottengo $S$ sommando agli $u\in U$ *qualunque* $p\in S$


### Combinazioni Lineari
>[!info] Definizione
>Sia $V$ uno *spazio vettoriale* e siano $v_{1},v_{2},\dots,v_{n}\in V$
>Diciamo che $\mathrm{v}\in V$ è **combinazione lineare** di $v_{1},v_{2},\dots,v_{n}$ se $\exists a_{1},a_{2},\dots,a_{n}\in \mathbb{K}:\mathrm{v}=a_{1}v_{1}+a_{2}v_{2}+\dots+a_{n}v_{n}$
>
>>[!done] In Breve
>>Se esistono una serie di valori del campo che moltiplicati per i corrispettivi vettori e, successivamente sommati fra di loro danno come risultato il vettore $\mathrm{v}$

#### Esempi
>Siano $\mathbb{K}=\mathbb{R}, V= \mathbb{R}^2$
>Siano $v_{1}=(2,0),v_{2}=(0,-1)$

>[!question] $\mathrm{v}=(1,3)$ è **combinazione lineare** di $v_{1},v_{2}$?

$$
\frac{1}{2}v_{1}+(-3)v_{2} = (1,0)+(0,3) = (1,3) = \mathrm{v}
$$
Se non si vede ad occhio:
$$
a_{1}v_{1}+a_{2}v_{2} = (2a_{1},0)+(0,-a_{2})=(2a_{1},-a_{2})
$$
- Imposto di conseguenza il sistema
$$
\begin{cases}
2a_{1} = 1 \\
-a_{2} = 3
\end{cases}
\Leftrightarrow
\begin{cases}
a_{1}=\frac{1}{2} \\
a_{2}=-3
\end{cases}
$$
#### Esempio di non combinazione
>$u_{1}=(2,0),u_{2}=(-1,0)$
>$\mathrm{u} =(1,3)$

>[!question] $\mathrm{u}$ è una combinazione lineare di $u_{1},u_{2}$?? 

$$
\begin{array}
\ \forall a_{1}, a_{2}\in\mathbb{R},a_{1}u_{1}+a_{2}u_{2}= \\
(2a_{1},0)+(-a_{2},0)=(2a_{1}-a_{2},0) = (1,3)
\end{array}
$$
- Imposto il sistema
$$
\begin{cases}
2a_{1}-2a_{2}=1 \\
\cancel{ 0=3 }
\end{cases}
$$
E poichè il sistema non ha soluzione, qualsiasi siano $a_{1}$ e $a_{2}$
>[!danger] $\mathrm{u}$ NON è una combinazione lineare di $u_{1},u_{2}$

### Span
>[!info] Definizione
>Diciamo che un *sottospazio vettoriale* $U$ di $V$ è **generato** da $v_{1},\dots,v_{n}$ se ogni $u\in U$ è combinazione lineare di $v_{1},\dots, v_{n}$
>In questo caso diciamo che $U$ è lo **span** di $v_{1},\dots,v_{n}$ e scriviamo
>$$U=<v_{1},\dots,v_{n}>$$
><u>Oppure</u>
>
>Dati $n$ vettori $v_{1},v_{2},\dots,v_{n}$ di uno spazio vettoriale $V$ su un campo $\mathbb{K}$ si definisce **Span** l'insieme di tutti i vettori che si possono scrivere come *combinazione lineare* di $v_{1},v_{2},\dots,v_{n}$


>Lo **span** è un sottospazio vettoriale di $V$ ed è anche chiamato il **sottospazio vettoriale generato** da $v_{1},v_{2},\dots,v_{n}$

#### Esempio
>$V = \mathbb{R}^4=\{ (x_{1},x_{2},x_{3},x_{4}),x_{i}\in \mathbb{R} \}$
>$v_{1}=(2,0,0,0),v_{2}=(0,-1,1,0)$

$<v_{1},v_{2}>=\{ a_{1}v_{1}+a_{2}v_{2}, \ a_{1},a_{2}\in \mathbb{R} \}$

$$
\begin{array}
\ =\{ (2a_{1},0,0,0)+(0,a_{2},-a_{2},0) ,\ a_{1},a_{2} \in \mathbb{R}\} \\
=\{ (2a_{1},a_{2},-a_{2},0) ,\ a_{1},a_{2} \in \mathbb{R}\} \\
=\{ (x_{1},x_{2},x_{3},x_{4})\in \mathbb{R}^4 :\begin{cases}
x_{2}+x_{3} = 0 \\
x_{4} = 0
\end{cases}\}
\end{array}
$$
### Dipendenza Lineare
>[!info] Linearmente Indipendente
>Un insieme di vettori $v_{1},\dots,v_{n}$ è **linearmente indipendente** se nessuno di loro è combinazione lineare degli altri
> <u>Oppure</u>
> Un insieme di vettori $v_{1},\dots,v_{n}$ è **linearmente indipendente** se gli unici $a_{1},\dots,a_{n} \in \mathbb{K}$ tali che $a_{1}v_{1}+\dots+a_{n}v_{n}=\underline{0}$ è $a_{1}=0,\dots,a_{n}=0$

>[!info] Linearmente Dipendenti
>Un insieme di vettori $v_{1},\dots,v_{n}$ è **linearmente dipendente** se non è linearmente indipendente
>>[!done] In Breve
>>Esiste almeno un vettore che è combinazione lineare degli altri

#### Esempio
>$v_{1}=(2,0), v_{2}=(-1,0)$

Sono *linearmente dipendenti* perchè $v_{1} =-2v_{2}$
- $v_{1}$ è combinazione lineare di $v_{2}$
	- Ovvero: $\exists a_{1}=1,a_{2}=2$ tali che $a_{1}v_{1}+a_{2}v_{2}=1(2,0)+2(-1,0) = (0,0)=\underline{0}$

>$u_{1=}(2,0), u_{2}=(0,-1)$

 Sono *linearmente indipendenti* perchè $a_{1}u_{1}\neq u_{2}$
 - Ovvero $a_{1}u_{1}+a_{1}u_{2}=\underline{0}\Leftrightarrow a_{1}=0,a_{2}=0$

### Base
>[!info] Definizione
>Un insieme $v_{1},\dots v_{n}\in V$ è una **base** di $V$ se $v_{1},\dots v_{n}$ sono linearmente indipendenti e generano $V$

#### Esempi
>$V=\mathbb{R}^2\ v_{1}=(1,0),v_{2}=(0,1),v_{3}=(2,1)$

I vettori generano $V$ ma non sono *linearmente indipendenti*
- Quindi non sono una base
- $v_{3}=2v_{1}+v_{2}$

$v_{1},v_{2}$ generano e sono linearmente indipendenti $\to$ sono una *base*

>$V=\mathbb{R}^3 \ u_{1}=(1,0,0),u_{2} =(0,1,1)$

I vettori sono linearmente indipendenti ma non generano $\mathbb{R}^3$
- $<u_{1},u_{2}> =\{ a_{1}u_{1}+a_{2}u_{2} \}=\{(a_{1},a_{2},a_{2}), a_{1},a_{2}\in\mathbb{R}\}$
- $\{ (x,y,z)\in \mathbb{R}^3:y=z \}$ 
	- $u_{1},u_{2}$ non è una base

>[!question] $v_{1}=(1,1,0),v_{2}=(0,1,1),v_{3}=(1,0,1)$ è una base di $\mathbb{R}^3$?

$$
\begin{array}
a_{1}(1,1,0)+a_{2}(0,1,1)+a_{3}(1,0,1) = (a_{1}+a_{3},a_{1}+a_{2},a_{2}+a_{3}) \\
\begin{cases}
a_{1}+a_{3}=0 \\
a_{1}+a_{2}=0 \\
a_{2}+a_{3}=0 \\

\end{cases} \\
\begin{cases}
a_{1}=0 \\
a_{2}=0 \\
a_{3}=0
\end{cases}
\end{array}
$$
$v_{1},v_{2},v_{3}$ è linearmente indipendente

>[!question] $v_{1},v_{2},v_{3}$ generano $\mathbb{R}^3$?

È vero che ogni vettore $(x,y,z)\in \mathbb{R}^3$ si scrive come $a_{1}v_{1}+a_{2}v_{2}+a_{3}v_{3}$ per qualche $a_{1},a_{2},a_{3}\in\mathbb{R}$?
- $(a_{1}+a_{3},a_{1}+a_{2},a_{2}+a_{3}) = (x,y,z)$
$$
\begin{cases}
a_{1}+a_{3}=x \\
a_{1}+a_{2}=y \\
a_{2}+a_{3}=z \\
\end{cases}\Leftrightarrow
\begin{cases}
a_{1}-a_{2} = x-z \\
a_{1}+a_{2}=y \\
a_{3}=z-a_{2} \\
\end{cases}\Leftrightarrow
\begin{cases}
2a_{1}=x+y-z \\
-2a_{2} = x-y-z \\
a_{3}=z+\displaystyle{\frac{x-y-z}{2}}
\end{cases}
$$
ESISTE una soluzione
- $v_{1},v_{2},v_{3}$ generano $\mathbb{R}^3$, quindi sono una *base*

### Completare la Base
Se ho vettori linearmente indipendenti che non generano $V$, posso "*completarli a una base*"
- Cioè aggiungere vettori fino a ottenere una base
>$v_{1}=(1,0,0),v_{2}=(0,1,0)$ non sono una base di $\mathbb{R}^3$

- $<v_{1},v_{2}> =\{ (x,y,z):z=0 \}$
Ma $v_{1},v_{2},v_{3} = (0,0,1)$ è una base di $\mathbb{R}^3$
- Andrebbe bene un qualunque vettore con $z\neq 0$

Se ho vettori che generano $V$, posso "*estrarre una base di $V$*"
- Cioè scartare vettori linearmente dipendenti fino ad ottenere una base
>$V=\mathbb{R}^2,v_{1}=(1,0),v_{2}=(2,0),v_{3}=(0,1),v_{4}=(2,5)$

Generano $\mathbb{R}^2$, ma non sono linearmente indipendenti
- $v_{1},v_{3}$ è una base
- $v_{1},v_{2}$ non è una base

