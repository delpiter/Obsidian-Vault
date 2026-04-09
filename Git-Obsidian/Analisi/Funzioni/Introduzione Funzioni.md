>[!info] Definizione
>Siano $A$ e $B \neq \varnothing$  chiamiamo funzione da $A$ a $B$ una legge che ad ogni elemento di $A$ associa uno ed un solo elemento di $B$ 
$$f:A\rightarrow B$$
- Dove $A$ rappresenta il dominio della funzione e $B$ il codominio
$$\forall x \in A, \exists y \in B : y = f(x)$$
## Dominio e Codominio e Immagine
---
>[!info] Dominio
>L'insieme dei valori possibili che la variabile $x$ può assumere
>>[!done] In Breve
>>L'insieme su cui è definita la funzione.

>[!info] Codominio
>È l'insieme dove sono contenute tutte le immagini della funzione

>[!info] Immagine
>Il sottoinsieme di $y$ costituito dai valori effettivamente assunti dalla funzione $f$ è invece detto immagine
$$f(A)=\{y\in B\;|\;\exists x\in A:f(x)=y\}$$
## Grafico di una Funzione
- - -
>Siano $A$ e $B \neq \varnothing$, sia $f: A \rightarrow B$ chiamiamo grafico di $f$, l'insieme 
$$y_f =\{(a,b) \in A\times B \; | b=f(a)\}$$



```functionplot
---
title: Piano Cartesiano
xLabel: 
yLabel: 
bounds: [-10,10,-10,10]
disableZoom: true
grid: true
---

```

#### Iniettività e surriettività
##### Funzione Surriettiva
>[!info] Surriettività $[f\;su]$
>Diciamo che $f$ è surriettiva se $f(A)=B$
>>[!done] In Breve
>>Se per ogni elemento del codominio, c'è almeno un elemento del domino associato
>
>Sia $f:A\to B$
>$$\forall y \in B, \exists \; x \in A | f(x)=y$$
- Tutte le funzioni possono essere surriettive
	- Basta restringere il codominio

##### Funzione Iniettiva
>[!info] Iniettività $[f\;1-1]$
>Diciamo che $f$ è iniettiva se:
>$$\forall y \in f(A), \exists! \;x \in A | f(x)=y$$
>>[!done] In Breve
>>Ogni elemento del dominio ha una immagine distinta

- Oppure se $f(x_1) = f(x_2) \Rightarrow x_1=x_2$

##### Funzione Biunivoca
>[!info] Funzione invertibile
>Diciamo che $f$ è invertibile (Biettiva o Biunivoca) se è sia iniettiva che surriettiva

##### Funzione inversa
>[!info] Definizione
>Sia $f:A\rightarrow B$ invertibile chiamiamo funzione inversa di $f$ la funzione $$f^-1:B\rightarrow A$$
>>[!done] In Breve
>>$\forall y\in B,f^-1(y)$ è l'unica soluzione dell'equazione $f(x)=y$

## Composizione
---
>[!info] Definizione
>Siano $f:A\rightarrow B, \;g:C\rightarrow D$
>Supponiamo che $f(A)\subseteq C$ (se $f(x)$ esce dal dominio di $g$ non è possibile)
>chiamiamo funzione composta
>$$g_of \;A\rightarrow D$$
>La funzione:
$$(g_of)(x)=g(f(x))$$
- Importante l'ordine con cui si compongono
	- Non è sempre detto sia possibile farlo in entrambi i versi ($g_of$ e $f_og$)
	- E anche se fosse possibile in generale $g_of\neq f_og$

## Funzione Identità
---
>La funzione identità è una particolare funzione che associa ad ogni $x$ la $x$ stessa
$$Id_a: A\rightarrow A$$
$$x\mapsto x$$

```functionplot
---
title: Funzione Identità
xLabel: 
yLabel: 
bounds: [-10,10,-10,10]
disableZoom: true
grid: true
---
y=x
```

###### Osservazione
- Sia $f$ una funzione invertibile, $f:A\to B$
	- Allora
$$(f_of^{-1})(x) = x \;\; \forall x \in B$$
$$(f^{-1}_of)(x) = x \;\; \forall x \in A$$

## Intervallo
- - -
>[!info] Definizione
>Diciamo che $I \subseteq \mathbb{R}$ è un intervallo se $\forall x,y \in I$ ($x>y$) e $\forall z \in \mathbb{R}: x<z<y$
>si ha $z \in I$
>
>>[!done] In Breve
>>Presi due numeri $x\; e \;y$ all'interno dell'insieme si dice intervallo se qualsiasi $z$ preso fra $x$ e $y$, anche $z$ è interno all'insieme
###### Es
- È un intervallo:
$$
I=\{x \in \mathbb{R} | 1<x<52\}
$$
- Non è un intervallo
$$
A=\{x \in \mathbb{R} | x<1 \vee x > 7\}
$$
### Notazioni
> Dati $a,b \in \mathbb{R}$
- $]a,b[ = \{x \in \mathbb{R} | a<x<b\}$
- $[a,b] = \{x \in \mathbb{R} | a\leq x\leq b\}$
	- Intervallo chiuso
- È possibile mischiare le notazioni
- $]a,b] = \{x \in \mathbb{R} | a<x\leq b\}$
- $+ \infty$ non è un numero reale è solo una notazioni
	- Per convenzione quindi è escluso dalla notazione
	- $[a,+\infty[ = \{x \in \mathbb{R} | x\geq a\}$
## Intervallo Forato
---
>[!info] Definizione
>Diciamo che $J\subseteq\mathbb{R}$ è un intervallo forato se:
>$$\exists c\in\mathbb{R}\setminus J:J\cup\{ c \}$$
>È un intervallo
#### Es
- $J=(0,1)\cup(1,2)$
	- L'insieme $J$ è un intervallo forato in $1$

## Continuità
---
>[!info] Definizione
>Sia $\mathrm{I}$ intervallo di $\mathbb{R},f:\mathrm{I}\to \mathbb{R}$
>Sia $c\in\mathrm{I}$
>Diciamo che $f$ è continua in $c$ se esiste il [[../Limiti/Limiti#Definizione Limite|limite]] e vale $f(c)$
>$$\exists\lim\limits_{x\to c}f(x) = f(c)$$
>Diciamo che $f$ è continua in $\mathrm{I}$ se è continua in ogni suo punto
>>[!bug] Errore
>>Non è vero che una funzione è continua se per disegnarla basta non staccare mai la penna

### Es
$$
f(x)=\begin{cases}
1 \text{ se } x>0 \\
0 \text{ se }x \leq 0
\end{cases}
$$
- La funzione è continua in $\mathbb{R}\setminus\{0\}$
$$
f:\mathbb{R}\setminus\{0\}\to\mathbb{R}, f(x)=\frac{1}{x}
$$
- La funzione è continua nel dominio
### Teorema
>[!info] Teorema
>Siano $f,g:I\to\mathbb{R}$ funzioni continue
><u>Allora</u>
>$$
\begin{cases}
f+g \text{ è continua} \\
f\cdot g \text{ è continua} \\
\displaystyle{\frac{f}{g}} \text{ è continua, }g\neq0 
\end{cases}
>$$
- Inoltre 
	- $f:I\to\mathbb{R},g:J\to\mathbb{R}$
		- Se $f(I)\subset J$ e se $f$ è continua su $I$ e $g$ è continua su $J$
		- Allora $g_{o}f$ è continua su $I$
	- $f:I\to f(I)$  
		- Se $f$ è invertibile e continua
		- Allora $f^-1$ è continua
## Limitazioni
- - -
>[!info] Definizione
>Siano $A \subseteq \mathbb{R}, \;f:A\to\mathbb{R}$ diciamo che $f$ è limitata superiormente o inferiormente se lo è $f(A)$ (l'immagine)
###### Es
$$
\begin{array}
/f:\mathbb{R}\to\mathbb{R}, f(x)=x^2 \\
f(\mathbb{R})=\mathbb{R}^+=\{x \in \mathbb{R}|x\geq 0\}
\end{array}
$$

```functionplot
---
title: 
xLabel: 
yLabel: 
bounds: [-10,10,-10,10]
disableZoom: true
grid: true
---
f(x)=x^2
```

- $f$ è limitata inferiormente ma non superiormente
### Estremi superiori e inferiori
- Nelle funzioni esistono e sono sempre unici gli estremi superiori e inferiori
	- A differenza dei punti di minimo e di massimo
##### Superiore
>Definiamo l'estremo superiore come
$$
\sup\limits_{A}f:=supf(A)
$$
##### Inferiore
>Definiamo l'estremo inferiore come
$$
\inf\limits_{A}f:=inff(A)
$$
### Massimo e minimo
- Non è sempre possibile che ci sia un punto di massimo o di minimo
>Diciamo che $f$ ammette un massimo, se $f(A)$ ammette il massimo
$$
\max\limits_{A}f:=maxf(A)
$$
>Analogamente diciamo che $f$ ammette un minimo, se $f(A)$ ammette il minimo
$$
\min\limits_{A}f:=minf(A)
$$
###### Es
$$
\begin{array}
/f:\mathbb{R}\to\mathbb{R} \\
x \mapsto (x-2)^2
\end{array}
$$

```functionplot
---
title: 
xLabel: 
yLabel: 
bounds: [-2,5,-2,5]
disableZoom: true
grid: true
---
f(x)=(x-2)^2
```
$$
\begin{array} \\

\sup\limits_{\mathbb{R}}f:=+\infty \\
\inf\limits_{\mathbb{R}}f:=0 \\
x=2\text{ Punto di minimo di }f
\end{array}
$$
## Teorema di Weierstruss
---
>[!info] Teorema
>Sia $f:[[.md#Continuità|continua]]
><u>Allora</u>
>$f$ ammette massimo e minimo

È possibile dimostrarlo utilizzando il metodo di bisezione
### Esempi
- Alcuni esempi del perchè servono tutte le condizioni
#### Dominio chiuso
$f:(0,5)\to\mathbb{R}$
$x\mapsto \displaystyle{\frac{1}{x}}$
>[!done] In breve
>$f$ non ha ne $MAX$ ne $min$
>Non ha il $MAX$ perchè a $0$ la funzione assume il valore $+\infty$
>Non ha il $min$ perchè il valore $5$ dovrebbe essere il minimo della funzione ma è escluso dal dominio
#### Continuità
$f:(-1,1)\setminus\{0\}\to\mathbb{R}$
$x\mapsto x^2$
>[!done] In breve
>$f$ non ha il $min$ poichè la funzione non è definita nel suo valore minimo
## Funzioni Monotone
- - -
- Sia $A \subseteq \mathbb{R},\; f:A \to \mathbb{R}$
### Crescente
>[!info] Definizione
>Diciamo che $f$ è una funzione **crescente** se 
>$\forall x_1,x_2 \in A$ con $x_{1}\leq x_{2}$ si ha che:
>$$
f(x_{1})\leq f(x_{2})
>$$

- Si indica con una freccia verso l'alto: $\nearrow$
- Si dice che $f$ è **strettamente crescente** se
	- $\forall x_{1},x_{2} \in A, \;x_{1}<x_{2},\; \text{si ha }f(x_{1})<f(x_{2})$
### Decrescente
>[!info] Definizione
>Diciamo che $f$ è una funzione **decrescente** se $\forall x_1,x_2 \in A$ con $x_{1}\leq x_{2}$ si ha che
>$$
f(x_{1})\geq f(x_{2})
>$$

- Si indica con una freccia verso il basso: $\searrow$
- Si dice che $f$ è **strettamente crescente** se
	- $\forall x_{1},x_{2} \in A, \;x_{1}<x_{2},\; \text{si ha }f(x_{1})>f(x_{2})$
###### Es
- Mi chiedo quando $f$ è crescente $\nearrow$
- È vero che $\forall x_{1},x_{2}$ con $x_{1}\leq x_{2}$ si ha $f(x_{1})\leq f(x_{2})$?
$$
\begin{array}
/f(x)=mx+q \\
mx_{1}+q \leq mx_{2}+q \\
mx_{1}+\cancel{q} \leq mx_{2}+\cancel{q} \\
m(x_{1}-x_{2})\leq 0 \\
(x_{1}-x_{2}) \leq 0 \;\forall x \in \mathbb{R} \\
\text{Quindi: }\begin{cases}
f \text{ è } \nearrow \;\Leftrightarrow\;m\geq 0 \\
f \text{ è } \searrow \;\Leftrightarrow\;m\leq 0
\end{cases} 
\end{array}
$$
### Monotonia funzioni composte
>Siano $f:A\to \mathbb{R}, g:B\to \mathbb{R} \ \ \ \ \ \ f(A) \subseteq B$
>se $f$ e $g$ sono monotone allora anche la composizione ($g_{o}f$) è monotona
- In particolare
	- $f_{o}g$ è $\nearrow$ se $f$ e $g$ hanno la stessa monotonia
	- $f_{o}g$ è $\searrow$ se $f$ e $g$ hanno monotonia contraria

### Proprietà monotonia
- Sia $f:A \to \mathbb{R}$
>Se $f$ è strettamente monotona allora $f$ è [[.md#Iniettività $[f ;1-1]$|iniettiva]] e $f^{-1}:f(A)\to A$ sono strettamente monotone della stessa monotonia
#### Dimostrazione
- Voglio dimostrare che se $f(x_{1})=f(x_{2}) \implies x_{1}=x_{2}$
	- Ciò è vero infatti:
	- supponiamo $f$ sia strettamente crescente

## Funzioni Pari e Dispari
---
>Sia $A \subseteq \mathbb{R}$ simmetrico rispetto all'oirgine (cioè se $x \in A \implies -x \in A$)
>	Sia $f:A\to\mathbb{R}$, diciamo che $f$ è **pari** se $\forall x \in A, f(x)=f(-x)$
>	Sia $f:A\to\mathbb{R}$, diciamo che $f$ è **dispari** se $\forall x \in A, f(x)=-f(-x)$
### Graficamente
$$
f(x) = x^2
$$

```functionplot
---
title: 
xLabel: 
yLabel: 
bounds: [-5,5,-1,9]
disableZoom: true
grid: true
---
f(x)=x^2
```
- Funzione pari
	- Simmetrica rispetto all'asse delle y
	- $f(2) = f(-2)$

$$
f(x)=x
$$

```functionplot
---
title: 
xLabel: 
yLabel: 
bounds: [-5,5,-5,5]
disableZoom: true
grid: true
---
f(x) = x
```
- Funzione dispari
	- Simmetrica rispetto all'origine
	- $f(2)=-f(-2)$

## Funzione Periodica
- - -
### Definizione Periodo
>[!info] Periodo
>Sia $T\in\mathbb{R}^+ \setminus \{0\},$ diciamo che $A\subseteq \mathbb{R}$ è T-periodica se $\forall x \in A, \forall k \in \mathbb{Z}$ si ha che $x + kT\in A$
>>[!done] In Breve
>>Ogni $T$ volte il valore della $x$ si ripete

### Definizione funzione periodica
>Sia $A\subseteq\mathbb{R}$ T-Periodico, $f:a\to\mathbb{R}$ diciamo che f è T-periodico se $\forall x \in A:f(x)=f(x+T)$

## Operazioni sul grafico
- - -
><font color="CornflowerBlue">$f(x) = x^2$ </font>
><font color="red">$f(x)+k = (x^2)+2$ </font>
><font color="green">$f(x)-k= (x^2)-2$</font>

```functionplot
---
title: 
xLabel: 
yLabel: 
bounds: [-5,5,-3,7]
disableZoom: true
grid: true
--- 
f(x)=x^2
g(x)=(x^2)+2
c(x)=(x^2)-2
```
><font color="CornflowerBlue">$f(x) = x^2$</font>
><font color="red">$f(x+k) = (x+2)^2$</font>
><font color="green">$f(x-k)= (x-2)^2$</font>

```functionplot
---
title: 
xLabel: 
yLabel: 
bounds: [-5,5,-1,9]
disableZoom: true
grid: true
---
f(x) = x^2
f(x+k) = (x+2)^2
f(x-k)= (x-2)^2
```
>[[../Breve ripasso#Valore assoluto|Valore Assoluto]]
><font color="CornflowerBlue">$f(x) = (x-2)^2-2$</font>
><font color="red">$f(|x|) = (|x|-2)^2-2$</font>


```functionplot
---
title: 
xLabel: 
yLabel: 
bounds: [-5,5,-3,7]
disableZoom: true
grid: true
---
f(x) = (x-2)^2-2
g(x)=(abs(x)-2)^2-2
```
><font color="CornflowerBlue">$f(x) = x^2-2$</font>
><font color="red">$|f(x)| = |x^2-2|$</font>

```functionplot
---
title: 
xLabel: 
yLabel: 
bounds: [-5,5,-3,7]
disableZoom: true
grid: true
---
f(x) = x^2-2
g(x) = abs(x^2-2)
```
