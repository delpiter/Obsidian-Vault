## Definizione Integrale
---
>[!info] Definizione
>Sia $f:[a,b]\to\mathbb{R}$ una funzione e tale che $f(x)\geq0,\forall x \in[a,b]$
>Chiamiamo sottografico di $f$, l'insieme:
>$$ \large \Gamma f = \{ (x,y) \in \mathbb{R} \times \mathbb{R} \mid x \in [a,b], y \in [0, f(x)] \} $$

![[attachements/Pasted image 20231115133900.png]]

### Osservazione
$$
(b-a)\cdot \inf\limits_{[a,b]}f\leq Area(\Gamma_{f})\leq (b-a)\cdot \sup\limits_{[a,b]}f
$$
![[attachements/ossSottografo.png]]

Analogamente, se suddivido $[a,b]$ in $n$ parti uguali $[x_{i-1},x_{i}]$, posso dire che:
$$
\sum^n_{i=1}(x_{i}-x_{i-1})\cdot \inf\limits_{[x_{i-1},x_{i}]}f\leq Area(\Gamma_{f})\leq \sum^n_{i=1}(x_{i}-x_{i-1})\cdot \sup\limits_{[x_{i-1},x_{i}]}f
$$
![[attachements/limSottografo.png]]
## Integrale di Funzioni Continue
---
>[!info] Definizione
>Sia $f:[[../Funzioni/Introduzione Funzioni#Continuità|continua]]
>Suddivido $[a,b]$ in $n$ intervalli della forma $[x_{i-1},x_{i}]$ dove:
>$$
\begin{cases}
x_{0} = a  \\
x_{n}=b \\
x_{i}-x_{i-1} = \displaystyle{\frac{b-a}{n}}
\end{cases}
>$$

### Somma di RIEMANN di $f$
>[!info] Definizione
>Sia $c_{i}\in[x_{i-1},x_{i}] \forall i =1,2,3,\dots,n$
>Chiamiamo somma di RIEMANN di $f$
>$$S_{R}(f,c_{1},c_{2},\dots,c_{n})=\sum^n_{i=1}f(c_{i})\cdot \displaystyle{\frac{b-a}{n}}$$

>[!info] Teorema
>Sia $f:[[../Funzioni/Introduzione Funzioni#Continuità|continua]]
><u>Allora</u>
>$$\exists \lim\limits_{n\to +\infty}S_{R}(f,c_{1},c_{2},\dots,c_{n})\in\mathbb{R}$$
>E non dipende dalla scelta di $c_{i}$
>
>>[!tldr] Definizione
>>Chiamiamo tale limite **integrale** di $f$ in $[a,b]$ e lo indichiamo con:
>>$$ \large \int_{a}^{b} f(x) dx$$

## Significato dell'integrale per $f$ che cambia segno
---
>[!info] Introduzione
>Sia $f^+(x) \implies maxf\{ 0,f(x) \}$
>e sia $f^-(x) \implies maxf\{ 0,-f(x) \}$
> Allora vale che:
> $f(x) = f^+(x)-f^-(x)$

- Quindi si ha
$$
\int _{a}^b f(x)\, dx = \int _{a}^b f^+(x)\, dx - \int _{a}^b f^-(x)\, dx 
$$
### Dimostrazione Grafica
![[attachements/integraleNegativo.jpg]]
## Teorema della Media Integrale
---
>[!info] Teorema
>Sia $f\in C([a,b],\mathbb{R})$
><u>Allora</u>
>1)
>$$\min\limits_{[a,b]} \leq \underbrace{ \displaystyle{\frac{1}{b-a}} \int _{a}^b f(x)\, dx }_{ \text{Media Integrale} } \leq \max\limits_{[a,b]}$$
>2)
>$$\exists c\in[a,b]:\displaystyle{\frac{1}{b-a}} \int _{a}^b f(x)\, dx = f(c)$$
>
>>[!done] In Breve
>>C'è un punto $c$ tale che $f(c)$ è l'altezza di un rettangolo di base $b-a$ la cui area è uguale all'area del sottografico.
>>$c$ può essere considerato come "altezza media" della funzione

### Dimostrazione
Il $\max\limits_{[[../Funzioni/Introduzione Funzioni#Teorema di Weierstruss|teorema di Weierstruss]]
- Si ha:
$$
\min\limits_{[a,b]}\leq f(x) \leq \max\limits_{[a,b]}, \forall x \in[a,b]
$$
- Integro in $[a,b]$, e ottengo:
$$
\int _{a}^b \min\limits_{[a,b]}\, dx \leq \int _{a}^b f(x)\, dx \leq \int _{a}^b \max\limits_{[a,b]}\, dx
$$
- Per definizione di integrale si ha:
$$
\min\limits_{[a,b]}(b-a) \leq \int _{a}^b f(x)\, dx \leq \max\limits_{[a,b]}(b-a)$$
- Divido entrambi i membri per $(b-a)$ e ottengo il punto $1$
Dalla dimostrazione del punto $1$ so che il valore della media integrale è compresa fra il minimo e il massimo di $f$
- Per il [[../Limiti/Limiti#Teorema dei valori Intermedi |teorema dei valori intermedi]], che posso applicare ad $f$ poichè funzione continua, e ho che:
$$
\displaystyle{\frac{1}{b-a}} \int _{a}^b f(x)\, dx \in f([a,b])
$$
## Primitive
---
>[!tldr] Definizione
>Sia $f\in C([a,b],\mathbb{R})$
>Diciamo che $F:[a,b]\to\mathbb{R}$ è primitiva di $f$ se $F'(x)=f(x), \forall x\in[a,b]$