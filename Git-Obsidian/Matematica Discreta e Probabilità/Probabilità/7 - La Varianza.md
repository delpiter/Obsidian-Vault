>Molto simile alla [[../Statistica Descrittiva/3 - Varianza|Varianza]] in ***statistica***

## Varianza
---
>[!definizione] Definizione
>La ***varianza*** da una misura della *dispersione* di valori di $X$, tenendo conto delle rispettive ***probabilità***
>$$Var(X)=E[(X-E[X])^2]$$
>Come in *statistica*, la varianza ***non*** si calcola usando la *definizione*
>>[!example] Formula
>>$$Var(X)=E[X^2]-E[X]^2$$

##### Dimostrazione
$$
E[(X-E[X])^2]=E[X^2-2E[X]X+E[X]^2]
$$
- Ora sfrutto la proprietà della [[6 - Valore Atteso#Corollario|somma del valore atteso]]

$$
E[X^2]-2E[X]E[X]+E[X]^2=E[X^2]-E[X]^2
$$

#### Esempi
>$X\sim B(1,p)$

>[!question] $Var(X)?$

- $Var(X)=E[X^2]-E[X]^2=\underbrace{ E[X] }_{ p }-p^2=p(1-p)$

###### Esempio 2
>$X\sim B(2,p)$

- $\displaystyle d_{X}(k)=\binom{2}{k}p^k(1-p)^{2-k}\quad k=0,1,2$

$$
E[X^2]=0^2\cdot  d_{X}(0)+1^2\cdot  d_{X}(1)+2^2\cdot  d_{X}(2)=0+2p(1-p)+4p^2
$$
$$
Var(X)=2p+2p^2-4p^2=2p(1-p)
$$
>[!question] È vero che se $X\sim B(n,p)$ allora $Var(X)=np(1-p)$?

#### Somma di Varianze
>[!definizione] Proprietà
>Se $X$ e $X$ sono ***variabili aleatorie*** *indipendenti*
><u>Allora</u>
>$$Var(X+Y)=Var(X)+Var(Y)$$

###### Dimostrazione
$$
\begin{array}
\ Var(X+Y)=E[(X+Y)^2]-E[(X+Y)]^2= \\
=E[X^2+2XY+Y^2]-(E[X]+E[Y])^2= \\
=E[X^2]+2E[XY]+E[Y^2]-E[X]^2-2E[X]E[Y]-E[Y]^2=
\end{array}
$$
E poiché [[6 - Valore Atteso#Prodotto di Valori Attesi|le variabili sono indipendenti]]
$$
\begin{array}
\ E[X^2]\cancel{ +2E[XY]}+E[Y^2] -E[X]^2-\cancel{ 2E[X]E[Y] }-E[Y]^2= \\
=\underbrace{ E[X^2]-E[X]^2 }_{ Var(X) }+\underbrace{ E[Y^2]-E[Y]^2 }_{ Var(Y) }=Var(X)+Var(Y)
\end{array}
$$

>[!tl;dr] Corollario
>Sia $X\sim B(n,p)$
><U>Allora </U>
>$$Var(X)=np(1-p)$$

###### Dimostrazione
>Sappiamo che $X=X_{1}+\dots X_{n}$

- $X_{i}\sim B(1,p)$

$$
Var(X)=Var(X_{1}+X_{2}+\dots+ X_{n})=Var(X_{1})+Var(X_{2})+\dots+Var(X_{n})=
$$
$$
\underbrace{ p(1-p)+p(1-p)+\dots p(1-p) }_{ n \text{ volte} }=np(1-p)
$$

>[!hint] Osservazione
>$Var(aX)=a^2Var(X)\quad a\in\mathbb{R}$ 

>Infatti

$$
Var(aX)=E[(aX)^2]-E[aX]^2=a^2E[X^2]-a^2E[X]^2=a^2(E[X^2]-E[X]^2)
$$
Quindi:
$$
a^2Var(X)
$$

>[!hint] Osservazione 2
>Se $X$ e $Y$ sono *indipendenti*
>$$Var(X-Y)=Var(X)+Var(Y)$$
>>[!note] Poiché
>>$$Var(X+(-Y))=Var(X)+Var(-Y)=Var(X)+(-1)^2Var(Y)$$

#### Varianza di Variabili di Poisson
>[[3 - Variabili Aleatorie#Variabili di Poisson|Variabili di Poisson]]

Se $X\sim P(\lambda)$ sappiamo che $X$ ***approssima*** una $B\left( n, \frac{\lambda}{n} \right)$ con $n$ *grande*

>[!caution] Quindi:

$$
Var(X)=\cancel{ n }\cdot \frac{\lambda}{\cancel{ n }}\underbrace{ \left( 1- \frac{\lambda}{n} \right)}_{ \to 1 }=\lambda
$$
>[!done] Conclusione
>Sia $X\sim P(\lambda)$ 
><u>Allora</u>
>$$E[X]=\lambda\quad Var(X)=\lambda$$

#### Esercizio
>$X\sim H(b,r;2)$

>[!question] $Var(X)$?

$Var(X)=E[X^2]-E[X]^2$

$$
d_{X}(k)=\begin{cases}
\displaystyle{\frac{\binom{r}{2}}{\binom{b+r}{2}}}\qquad k=0 \\
\displaystyle{\frac{\binom{r}{1}\binom{b}{1}}{\binom{b+r}{2}}}\ \ \quad k=1 \\
\displaystyle{\frac{\binom{b}{2}}{\binom{b+r}{2}}}\qquad k=2 \\
0 \qquad\qquad \text{ altrimenti}
\end{cases}
$$

- $E[X]=2 \displaystyle{\frac{b}{b+r}}$
- $E[X^2]=1\cdot \displaystyle{\frac{2br}{(b+r)(b+r-1)}}+4 \displaystyle{\frac{\displaystyle{\frac{b(b-1)}{\cancel{ 2 }}}}{\displaystyle{\frac{(b+r)(b+r-1)}{\cancel{ 2 }}}}}=\displaystyle{\frac{2br+4b^2-ab}{(b+r)(b+r-1)}}$

$$Var(X)=E[X^2]-E[X]^2$$
$$\displaystyle{\frac{2br+4b^2-ab}{(b+r)(b+r-1)}}-\left( \frac{2b}{b+r} \right)^2$$

>[!note] Troppo complessa