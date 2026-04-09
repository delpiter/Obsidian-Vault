## Costanti
- - -
>[!info] Definizione
>$$
\begin{array}
/f : \mathbb{R} \to \mathbb{R} \\
f(x) =k, \; k \in \mathbb{R}
\end{array}
>$$


```functionplot
---
title: 
xLabel: 
yLabel: 
bounds: [-5,5,-5,5]
disableZoom: true
grid: true
---
f(x)=3
```
## Polinomi
- - -
>[!info] Definizione
>$$
\begin{array}
/f: \mathbb{R} \to \mathbb{R} \\
f(x) = ax^p+bx^{p-1}+\dots+ax+a \\
p \in \mathbb{N} \\
\end{array}
>$$
###### Es
$f(x)=3x^4-2x^2+2x+1$

```functionplot
---
title: 
xLabel: 
yLabel: 
bounds: [-3,3,-3,3]
disableZoom: true
grid: true
---
y=3x^4-2x^2+2x+1
```
## Valore assoluto
- - -
>[[../Breve ripasso#Valore assoluto|Definizione]]
>$$
\begin{array}
/f: \mathbb{R} \to \mathbb{R} \\
f(x)=|x|
\end{array}
>$$

```functionplot
---
title: 
xLabel: 
yLabel: 
bounds: [-3,3,-3,3]
disableZoom: true
grid: true
---
y=abs(x)
```
## Funzione Segno
- - -
>[!info] Definizione
>$$
\begin{array}
/f: \mathbb{R}\setminus \{0\} \to \mathbb{R} \\ \\
f(x)=segno(x)=\begin{cases}
1\;\text{se}\;x>0 \\
-1\;\text{se}\;x<0
\end{cases}
\end{array}
>$$


```functionplot
---
title: 
xLabel: 
yLabel: 
bounds: [-2,2,-2,2]
disableZoom: true
grid: true
---
f(x)=sign(x)
```
## Parte intera
- - -
>[!info] Definizione
>$$
\begin{array}
/f(x)=\lfloor x \rfloor \\
f:\mathbb{R}\to\mathbb{R} \\
f:=max\{z \in\mathbb{Z}|z\leq x\}
\end{array}
>$$

```functionplot
---
title: 
xLabel: 
yLabel: 
bounds: [-5,5,-5,5]
disableZoom: true
grid: true
---
f(x)=floor(x)
```
## Funzione Periodica
- - -
### Parte Frazionaria
>[!info] Definizione
>$$
\begin{array}
/f:\mathbb{R}\to\mathbb{R} \\
f(x)=x-\lfloor x \rfloor
\end{array}
>$$

```functionplot
---
title: 
xLabel: 
yLabel: 
bounds: [-4,4,-4,4]
disableZoom: true
grid: true
---
f(x)=x-floor(x)
```
## Funzione Esponenziale
>[!info] Definizione
>$a^p, p\in\mathbb{Q}$
>Per la priprietà di densità di $\mathbb{Q}$ in $\mathbb{R}$, posso estendere tale definizione da $p \in \mathbb{Q}$ a $p \in \mathbb{R}$

### Proprietà
- Sempre strettamente positiva ($a^x>0, \forall x \in \mathbb{R}$)
- $a^{x+y}=a^x\cdot a^y$
- $(a^x)^y=a^{x\cdot y}$
- $a^x\cdot b^x=(ab)^x\ \ \ \ \ \ \ \ a,b\in\mathbb{R}^+\setminus\{0,1\}$
- Se $a >1$
	- $exp_{a}$ è [[Introduzione Funzioni#Crescente|strettamente crescente]]
- Se $0<a<1$
	- $exp_{a}$ è [[Introduzione Funzioni#Decrescente|strettamente descrescente]]
- $exp_{a}:\mathbb{R}\to\mathbb{R}^+\setminus\{0\} \to$ [[Introduzione Funzioni#Iniettività e surriettività|Invertibile]]
### Grafici
<font color="CornflowerBlue">$\boxed{a>1}$ </font>
<font color="red">$\boxed{0<a<1}$</font>

```functionplot
---
title: 
xLabel: 
yLabel: 
bounds: [-10,10,-10,10]
disableZoom: true
grid: true
---
f(x)=2^x
g(x)=(1/2)^x
```
## Funzione Logaritmica
- - -
>[!info] Definizione
>Sia $a \in \mathbb{R}^+ \setminus\{0,1\}$, chimamiamo **Logaritmo** in base $a$, la funzione inversa di $exp_{a}$ e lo indico con:
>$$
>log_{a}:=(exp_{a})^{-1} \ \ \ \ \ \ [log_{a}:\mathbb{R}^+\setminus{0}\to \mathbb{R}]
>$$
### Proprietà
- $\forall x,y \in \mathbb{R}^+\setminus\{0\}, \log_{a}(x\cdot y)=\log_{a}x + \log_{a}y$
- $\log_{a}x^\alpha=\alpha\log_{a}x \ \ \ \ \ \alpha\in\mathbb{R}$

#### Dimostrazione proprietà 1
> Voglio dimostrare che $\log_{a}(x\cdot y)=\log_{a}x+\log_{a}y$
- Per la proprietà della [[Introduzione Funzioni#Funzione Identità|funzione identità]]
	- $\huge{a^{\log_{a}(x\cdot y)}=a^{\log_{a}x}\cdot a^{\log_{a}y}}$
	- Per la proprietà della funzione esponenziale
	- $\huge{a^{\log_{a}x}\cdot a^{\log_{a}y}=a^{\log_{a}x+\log_{a}y}}$
	- Poichè la funzione è iniettiva i due esponenti devono essere per forza uguali
### Grafici
<font color="CornflowerBlue">$\boxed{a>1}$ </font>
<font color="red">$\boxed{0<a<1}$</font>

```functionplot
---
title: 
xLabel: 
yLabel: 
bounds: [-10,10,-10,10]
disableZoom: true
grid: true
---
f(x)=log(x)
g(x)=log(x)/log(1/2)
```

#### Osservazione
- Esponenziale e logaritmo sono specchiati rispetto alla bisettrice
	- In generale $f$ e $f^{-1}$ sono simmetriche rispetto alla retta $y=x$

## Funzioni trigonometriche
- - -
>[!info] Definizione Circonferenza goniometrica
>Sia $U=\{(x,y)\in\mathbb{R}\times\mathbb{R}|x^2+y^2=1\}$
>La circonferenza goniometrica è una circonferenza di raggio $1$

[[../../Definizioni/Definizioni_Analisi#Valori Notevoli|Alcuni valori notevoli]]

Considerando una retta $a$ con origine $O$ (*centro della circonferenza goniometrica*), e l'angolo che la retta fa con l'asse delle ascisse.

> Chiamiamo $A$ l'intersezione di $a$ con la circonferenza

Se $A=(x,y)$ definiamo:
- $cos(\alpha)=x$
- $sin(\alpha)=y$
### Coseno
>[!definizione] Definizione
>$$\begin{array}\ cos:\mathbb{R}\to\mathbb{R} \\\alpha\mapsto x_{p}\end{array}$$
#### Proprietà
- Il coseno è una funzione periodica di periodo $2\pi\text{-periodo}$
- $cos(\alpha)\in[-1,1]\ \ \ \forall \alpha \in\mathbb{R}$
- $sen^2(\alpha)+cos^2(\alpha)=1 \ \ \ \ \forall\alpha\in\mathbb{R}$
- $cos(\alpha)=cos(-\alpha) \to \text{funzione pari}$
- $cos(\alpha)=-cos(\pi-\alpha)$
#### Grafico

```functionplot
---
title: 
xLabel: 
yLabel: 
bounds: [-5,5,-5,5]
disableZoom: true
grid: true
---
f(x)=cos(x)
```
#### Teorema del Coseno
>[!info]
>Dato un triangolo di lati $a,b,c$ e detti $\alpha,\beta,\gamma$ gli angoli opposti a tali lati, vale la relazione:
>$$a^2=b^2+c^2-2bc\ cos(\alpha)$$

### Seno
>[!definizione] Definizione
>$$\begin{array}/Sen:\mathbb{R}\to\mathbb{R} \\\alpha\mapsto y_{p}\end{array}$$
#### Proprietà
- Il seno è una funzione periodica di periodo $2\pi\text{-periodo}$
- $sen(\alpha)\in[-1,1]\ \ \ \forall \alpha \in\mathbb{R}$
- $sen^2(\alpha)+cos^2(\alpha)=1 \ \ \ \ \forall\alpha\in\mathbb{R}$
- $sen(\alpha)=-sen(-\alpha) \to \text{funzione dispari}$
- $sen(\alpha)=sen(\pi-\alpha)$
#### Grafico

```functionplot
---
title: 
xLabel: 
yLabel: 
bounds: [-5,5,-5,5]
disableZoom: true
grid: true
---
f(x)=sin(x)
```
#### Teorema dei Seni
>[!info]
>Dato un triangolo di lati $a,b,c$ e detti $\alpha,\beta,\gamma$ gli angoli opposti a tali lati, vale la relazione:
>$$\frac{a}{sin(\alpha)}=\frac{b}{sin(\beta)}=\frac{c}{sin(\gamma))}$$
### Formule Seno e Coseno
$$
\begin{array}
\ \forall x_{1},x_{2}\in\mathbb{R},cos(x_{1}+x_{2})=cos(x_{1})\cdot cos(x_{2})-sen(x_{1})\cdot sen(x_{2}) \\
\forall x_{1},x_{2}\in\mathbb{R},sen(x_{1}+x_{2})=cos(x_{1})\cdot sen(x_{2})+cos(x_{2})\cdot sen(x_{1}) \\
\forall x \in \mathbb{R}, cos(2x)=cos^2(x)-sen^2(x) \\
\forall x\in\mathbb{R},sen(2x)=2cos(x)\cdot sen(x)
\end{array}
$$
### Tangente
>[!info] Definizione Tangente
>La tangente è una funzione $\pi\text{-periodica}$ ed è definita nel dominio:
>$tan:\{\alpha\in\mathbb{R}|\alpha \neq \displaystyle{\frac{\pi}{2}+k\pi},k\in\mathbb{Z}\}$
>$tan:\mathbb{R}\setminus\left\{ \displaystyle{\frac{\pi}{2}}+k\pi,k\in\mathbb{Z} \right\}\to\mathbb{R}$
- La tangente può essere scritta anche come rapporto fra seno e coseno
- $tan(\alpha)=\displaystyle{\frac{sen(\alpha)}{cos(\alpha)}}$
- La tangente è una funzione dispari

#### Grafico

```functionplot
---
title: 
xLabel: 
yLabel: 
bounds: [-10,10,-10,10]
disableZoom: true
grid: true
---
f(x)=tan(x)
```

### Cotangente
>[!info] Definizione
>Reciproco della funzione Tangente, la tangente sarà posta sull'asse delle $y$ al contrario della tangente
>$cotan:\mathbb{R}\setminus\left\{ k\pi,k\in\mathbb{Z} \right\}\to\mathbb{R}$
>$cotan(\alpha) =\displaystyle{\frac{cos(\alpha)}{sen(\alpha)}}=\displaystyle{\frac{1}{tan(\alpha)}}$

- La cotangente è una funzione dispari
#### Grafico

```functionplot
---
title: 
xLabel: 
yLabel: 
bounds: [-10,10,-10,10]
disableZoom: true
grid: true
---
f(x)=cos(x)/sin(x)
```
### Funzioni Inverse
- Per ottenere le [[Introduzione Funzioni#Funzione inversa|funzioni inverse]] di funzioni periodiche è necessario restringere il dominio
#### Arcoseno
>[!info] Definizione
>Il seno nell'intervallo:
>$sen:\left[ -\displaystyle{\frac{\pi}{2}}, \displaystyle{\frac{\pi}{2}}\right] \to[-1,1]$ è invertibile
>>[!tldr] Funzione inversa
>>$arcsin:[-1,1]\to  \left[ -\displaystyle{\frac{\pi}{2}}, \displaystyle{\frac{\pi}{2}}\right]$
##### Grafico

```functionplot
---
title: 
xLabel: 
yLabel: 
bounds: [-2,2,-2,2]
disableZoom: true
grid: true
---
f(x)=asin(x)
```
#### Arcocoseno
>[!info] Definizione
>Il coseno nell'intervallo:
>$cos:[0,\pi] \to[-1,1]$ è invertibile
>>[!tldr] Funzione inversa
>>$arcos:[-1,1]\to  [0,\pi]$
##### Grafico

```functionplot
---
title: 
xLabel: 
yLabel: 
bounds: [-3,3,-2,4]
disableZoom: true
grid: true
---
f(x)=acos(x)
```
#### Arcotangente
>[!info] Definizione
>La tangente nell'intervallo:
>$tan:\left[ -\displaystyle{\frac{\pi}{2}}, \displaystyle{\frac{\pi}{2}}\right] \to\mathbb{R}$ è invertibile
>>[!tldr] Funzione inversa
>>$arctan:\mathbb{R}\to  \left[ -\displaystyle{\frac{\pi}{2}}, \displaystyle{\frac{\pi}{2}}\right]$


```functionplot
---
title: 
xLabel: 
yLabel: 
bounds: [-5,5,-5,5]
disableZoom: true
grid: true
---
f(x)=atan(x)
```
#### Es
$$sen(x)=\displaystyle{\frac{3}{4}}$$
>Nell'intervallo $\left[ -\displaystyle{\frac{\pi}{2}},\displaystyle{\frac{\pi}{2}} \right]$ c'è una sola soluzione trovata applicando la funzione inversa
$$
x = arcsen\left( \displaystyle{\frac{3}{4}} \right)
$$
- Applicando la funzione inversa si vanno a "perdere" tutte le soluzioni periodiche a causa del restringimento del dominio
- Per indicare tutte le soluzioni:
$$
\begin{array}
/x = arcsen\left( \frac{3}{4} \right) + 2k\pi, k\in\mathbb{Z}\ \text{ e }\ x = \pi-arcsen\left( \frac{3}{4} \right) + 2k\pi, k\in\mathbb{Z} \\
\text{Riassumendo: } \\
\left\{ arcsen\left( \frac{3}{4} \right)+2k\pi,\ k\in\mathbb{Z} \right\} \cup\{\pi-arcsen\left( \frac{3}{4} \right)+2k\pi,\ k\in\mathbb{Z}\}
\end{array}
$$