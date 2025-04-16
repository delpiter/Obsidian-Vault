>[!info] Numeri Complessi
>Un numero complesso si può definire come una coppia ordinata di numeri reali $(a,b)$
>>L'insieme dei numeri complessi è perciò definito come il piano cartesiano
>>$$
\begin{array}
\ \mathbb{C}=\mathbb{R}\times\mathbb{R}=\mathbb{R}^2 \\
\{(a,b)|a\in\mathbb{R},b\in\mathbb{R}\}
\end{array}
>>$$

#### Osservazione
- $\mathbb{R}$ è un sottoinsieme di $\mathbb{C}$ in quanto $(a,0)\to\mathbb{R}$
## Operazioni
- - -
>I numeri complessi sono dotati delle seguenti operazioni
### Somma di numeri complessi
$$
(a,b)+(c,d):=(a+c,b+d)
$$
- Elemento neutro: $(0,0)$
- Operazione opposta: $(-a,-b)$
### Prodotto di numeri complessi
$$
(a,b)\cdot(c,d):=(ac-db,ad+bc)
$$
- Elemento neutro: $(1,0)$
- Operazione opposta: $\left( \displaystyle{\frac{a}{a^2+b^2}},-\displaystyle{\frac{b}{a^2+b^2}} \right)$
#### Osservazione
$(0,1)\cdot(0,1)=(0\cdot0-1\cdot1,0\cdot1+1\cdot0) = (-1,0)$
- Quindi $(0,1)^2=-1$
	- Chiamo $(0,1)$ l'unità immaginaria e la indico con $i$

## Forma Algebrica
- - -
$$
\begin{array}
\ z\in\mathbb{C} \\
z=(a,b)=a(1,0)+b(0,1)=a+ib
\end{array}
$$
- Dove $a$ è la parte reale ($\mathbb{R}ez$)
- e b è la parte immaginaria ($Imz$)
#### Osservazione
- Osserviamo che
##### Somma
$$
\begin{array}
\ (a+ib)+(c+id)=a+c+i(b+d) \\
(a,b)+(c,d)=(a+c,b+d)
\end{array}
$$
##### Prodotto
$$
\begin{array}
\ (a+ib)\cdot(c+id)=ac-bd+i(bc+ad) \\
(a,b)\cdot(c,d)=(ac-db,ad+bc)
\end{array}
$$
## Coniugato
- - -
>[!info] Definizione
>Il numero complesso $a-ib$ si dice il _complesso coniugato_ di $z=a+ib$ e si indica con $\overline{z}$

- Si può osservare
$$
\begin{array}
\ \mathbb{R}e(z)=\displaystyle{\frac{z+\overline{z}}{2}}=a \\
Im(z)=\displaystyle{\frac{z-\overline{z}}{2i}}=b
\end{array}
$$
### Proprietà
$$
\begin{array}
\ \overline{z_{1}}+\overline{z_{2}}=\overline{z_{1}+z_{2}}\\
\overline{z_{1}}\cdot\overline{z_{2}}=\overline{z_{1}\cdot z_{2}}
\end{array}
$$

## Modulo
- - -
>[!info] Definizione
>Si chiama _modulo_ di $z=a+ib$ il numero reale non negativo $\sqrt{ a^2+b^2 }$ che si indica con $\mid z\mid$
>> [!done] In breve
>>Può essere visto come la distanza di un punto dall'origine del piano
### Proprietà
1. $\mid z\mid \geq 0$ e $\mid z\mid = 0 \Leftrightarrow z=0$
2. $\mid z\mid = \mid \overline{z}\mid$
3. $|z_{1}+z_{2}| \leq |z_{1}| + |z_{2}|$
4. $|z_{1}-z_{2}| \geq ||z_{1}| - |z_{2}||$

## Forma Trigonometrica
- - -
>[!info] Coordinate polari
>I punti del piano possono essere individuati, oltre che dalle loro _coordinate cartesiane_, anche dalle loro _coordinate polari_
>>[!tldr] \
>>$\rho$ Raggio polare, distanza del punto dall'origine
>>$\theta$ Angolo polare, l'angolo che la retta congiungente il punto con l'origine forma con l'asse delle ascisse positive con $\rho \in [0,2\pi]$

- Dato un numero complesso $z$ il suo modulo $|z|$ coincide con il raggio polare del punto
- Chiamiamo _argomento_ di $z$ ($arg(z)$) l'angolo $\theta$ relativo al punto $z$

>Dato il numero $z=a+ib$, dalla trigonometria ricaviamo immediatamente le relazioni tra le coordinate cartesiane $a,b$ e le coordinate polari $\rho,\theta$
$$
\begin{array} \\
a=\rho(cos\theta) \\
b=\rho(sin\theta)
\end{array}
$$
- Di conseguenza il numero complesso $z$ può essere scritto nella forma
$$
z=\rho(cos(\theta)+isin(\theta))
$$
- Che è detta *forma trigonometrica* dei numeri complessi
#### Formule inverse
1. $\rho = \sqrt{ a^2+b^2 }$
2. $cos(\theta)=\displaystyle{\frac{a}{\sqrt{ a^2+b^2 }}}$
3. $sin(\theta)=\displaystyle{\frac{b}{\sqrt{ a^2+b^2 }}}$
4. $tan(\theta)=\displaystyle{\frac{b}{a}}$
## Formule di De Moivre
- - -
>La forma trigonometrica è comoda per esprimere prodotti e quozienti di numeri complessi:
$$
z_{1}=\rho_{1}(cos(\theta_{1})+isin(\theta_{1})),\ \ \ z_{2}=\rho_{2}(cos(\theta_{2})+isin(\theta_{2}))
$$
- Otteniamo infatti
$$
\begin{array}\
z_{1}z_{2}=\rho_{1}\rho_{2}[cos(\theta_{1})cos(\theta_{2})sin(\theta_{1})sin(\theta_{2})+i(sin(\theta_{1})cos(\theta_{2})+cos(\theta_{1})sin(\theta_{2}))]= \\
=\rho_{1}\rho_{2}(cos(\theta_{1}+\theta_{2})+isin(\theta_{1}+\theta_{2}))
\end{array}
$$
## Radci N-esime
- - -
- Dato un numero complesso $w$, diremo che $z$ è una radice $n-esima$ di $w$ se risulta $z^n=w$
>[!info] Teorema Fondamentale dell'Algebra
>Sia $w\in\mathbb{C}, w\neq0$ e $n\in\mathbb{N}$, esistono precisamente n radici n-esime complesse di $w$

[[Definizioni_Analisi#Notazione numeri complessi in forma goniometrica|Notazione]]
- Voglio risolvere $z^n=w$
	- Sia $w=r(cos(\rho)+isin(\rho))=re^{i\rho}$
	- Sia $z=\rho e^{i\theta} \implies z^n=\rho^ne^{in\theta}$
- Devo imporre
$$
z_{k}
\begin{cases}
\rho^n=r \\
n\theta_{k}=\rho+2k\pi,\ \ k\in{0,1,2,\dots,n-1}
\end{cases}
$$
$$
z_{k}
\begin{cases}
\rho^n=r \\
\theta_{k}=\displaystyle{\frac{\rho+2k\pi}{n}}
\end{cases}
$$
### Osservazione
> Vale sempre vche le radici $n$-esime di $w$ sono i vertici di un poligono regolare di $n$ lati inscritto in una circonferenza di raggio $\sqrt[n]{\mid w \mid}$