## Varianza di un Carattere
---
>[!Definizione]
>La ***varianza di un carattere*** è un *indice di dispersione*.
>Da una misura della lontananza dei dati tra di loro
>>[!done] ‎ 
>>La varianza è la media dei quadrati delle distanze rispetto a $‎\overline{x}$ e si indica con $\sigma^2_{x}$
>>Sia $\micro$ la media dei valori $x_{1},\dots,x_{n}$
>>$$\sigma^2_{x}= \displaystyle{\frac{\displaystyle\sum_{i=1}^n(x_{i}-\micro)}{n}}$$
>


##### Esempio
>$x=-1,-2,3$
>$y=-50,-70,-120$

La media di $x$ e $y$ è entrambe $0$

$$
\sigma^2_{x}=\displaystyle{\frac{(-1-0)^2+(-2-0)^2+(3-0)^2}{3}}=\frac{14}{3}
$$
$$
\sigma^2_{y}=\displaystyle{\frac{(-50-0)^2+(-70-0)^2+(120-0)^2}{3}}=\text{ numero grande}
$$

### Varianza
>[!example] Formula
> $$\sigma^2_{x}=\overline{x^2}-\overline{x}^2$$

#### Dimostrazione

$$
\sigma^2_{x}=\frac{1}{n}\sum_{i=1}^n(x_{i}-\overline{x})^2=\frac{1}{n}\sum_{i=1}^n(x_{i}^2-2\overline{x}x_{i}+\overline{x}^2)=
$$
$$
=\underbrace{ \frac{1}{n}\sum_{i=1}^n x_{i}^2 }_{ \overline{x^2} }-\underbrace{ \frac{2\overline{x}}{n}\sum_{i=1}^nx_{i} }_{ -2\overline{x}\cdot\overline{x} }+\frac{1}{\cancel{ n } }\cdot \cancel{ n }\overline{x}^2
$$
$$
\overline{x^2}-2\overline{x}^2+\overline{x}^2=\overline{x^2}-\overline{x}^2
$$

>[!abstract] Proprietà
>$y=x+a\implies \sigma^2_{y}=\sigma^2_{x}$

##### Dimostrazione
$$
\begin{array}{}
\sigma^2_{y}=\overline{y^2}-\overline{y}^2=\overline{x^2+2ax+a^2}-(\overline{x}^2+2a\overline{x}+a^2) =\\=\overline{x^2}+\cancel{ 2a\overline{x} }+\cancel{ a^2 }-(\overline{x}^2+\cancel{ 2a\overline{x} }+\cancel{ a^2 })= \\
=\overline{x^2}-\overline{x}^2
\end{array}
$$
>[!abstract] Proprietà
>$y=ax\implies \sigma^2_{y}=a^2\sigma^2_{x}$

##### Dimostrazione
$$
\begin{array}{}
\sigma^2_{y}=\overline{y^2}-\overline{y}^2= \\
\overline{(ax)^2}-\overline{ax}^2= \\
=a^2(\overline{x^2}-\overline{x}^2)= \\
=a^2\sigma^2_{x}
\end{array}
$$

>[!example] Mettendo insieme le formule
>$$y=ax+b\implies \sigma^2_{y}=a^2\sigma^2_{x}$$


### Covarianza
>[!info] Definizione
>Siano $x,y$ due [[1 - Indagine Statistica#Carattere|caratteri]] definiti sulla stessa [[1 - Indagine Statistica#Popolazione|popolazione]]
>$$\sigma_{x,y}=\frac{1}{n}\sum_{i=1}^n(x_{i}-\overline{x})(y_{i}-\overline{y})$$
>A differenza della *varianza*, la ***covarianza*** può assumere valori negativi


>[!question] Che cosa rappresenta??

>Correlazione dei concetti:

Se la ***varianza è positiva***
- Ci aspettiamo che se un carattere assume un valore "*qualunque*" l'altro valore avrà lo ***stesso segno***

#### Esempio
>$x =$ altezza
>$y=$ peso

>[!tip] Sono positivamente correlate
>

>$x=$ ore di corsa
>$y=$ peso

>[!example] Sono negativamente correlate

#### Formula per la Covarianza
>$\sigma_{x,y}=\overline{xy}-\overline{x}\overline{y}$

##### Dimostrazione
$$
\begin{array}{}
\sigma_{x,y}=\displaystyle\frac{1}{n} \sum_{i=1}^n(x_{i}-\overline{x})(y_{i}-\overline{y}) =\\
=\displaystyle\underbrace{ \frac{1}{n}\sum_{i=1}^nx_{i}y_{i} }_{ \overline{xy} }-\underbrace{ \frac{1}{n}\sum^n_{i=1}x_{i-\overline{y}} }_{ \overline{x}\overline{y} }-\underbrace{ \frac{1}{n}\sum_{i=1}^n\overline{x}y_{i}U }_{ \overline{x}\overline{y} }+\frac{1}{n}\underbrace{ \sum_{i=1}^n\overline{x}\overline{y} }_{ \overline{x}\overline{y} }= \\
=\overline{xy}-\overline{x}\overline{y}-\cancel{ \overline{x}\overline{y} }+\cancel{ n\cdot \frac{1}{n}\overline{x}\overline{y} }= \\
=\overline{xy}-\overline{x}\overline{y}
\end{array}
$$

### Retta ai minimi quadrati
>[!info] Definizione
>La ***retta ai minimi quadrati*** è quella che minimizza la somma dei quadrati della lunghezza dei segmenti creati dalla ***proiezione*** dei punti sulla retta

#### Esempio
>Campione di $7$ studenti
>$x=$ Ore di studio
>$y=$ Voto

| $x$ | $y$ |
| --- | --- |
| 10  | 10  |
| 60  | 28  |
| 50  | 30  |
| 40  | 25  |
| 40  | 20  |
| 30  | 21  |
| 25  | 18  |
_Vogliamo stimare la $y$ con la retta_

>[!example] Equazione della retta

$$
\begin{cases}
m= \displaystyle{\frac{\sigma_{x,y}}{\sigma_{x}^2}} \\
q=\overline{y}- \displaystyle{\frac{\sigma_{x,y}}{\sigma_{x}^2}}\overline{x}
\end{cases}
$$
