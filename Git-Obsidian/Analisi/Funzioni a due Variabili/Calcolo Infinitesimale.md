## Limiti
---
>[!info] Definizioni
>>[!example] Definizione con successione
>>Diciamo una successione
>>$\{ (x_{n},y_{n}) \}_{n\in\mathbb{N}}$ in $\mathbb{R}^2$ tende a $c=(x_{0},y_{0})$ se:
>>$$|(x_{n},y_{n})-(x_{0},y_{0})|=\sqrt{ (x_{n}-x_{0})^2+(y_{n},y_{0})^2 }\to 0$$
>>>[!done] In breve
>>> La distanza dei punti deve tendere a $0$ da qualsiasi direzione
![[attachements/limiteR3.png]]

### Definizione di Intorno
>[!info] Definizione
>Sia $(x_{0},y_{0})\in\mathbb{R}^2$, diciamo che:
>$\mathrm{U}_{(x_{0},y_{0})}$ è un intorno di $(x_{0},y_{0})$ se è della forma:
>$$\mathrm{U}_{(x_{0},y_{0})} = \{ (x,y)\in\mathbb{R}^2 : |(x,y)-(x_{0},y_{0})|<\delta\}$$
>>[!done] In Breve
>> Tutti i punti all'interno di una circonferenza di raggio $\delta$

### Definizione di Limite per $\mathbb{R}^3$
>[!info] Definizione
>>[!example] Definizione con Successione
>>Sia $f:\mathbb{R}^2 \to\mathbb{R}$ Sia $(x_{0},y_{0})\in\mathbb{R}^2,l\in\overline{\mathbb{R}}$
>>Diciamo che:
>>$$\lim\limits_{(x,y)\to (x_{0},y_{0})}f(x,y) = l$$
>>Se $\forall$ successione $\{ (x_{n},y_{n}) \}\in\mathbb{R}^2:$
>>$$(x_{n},y_{n})\to(x_{0},y_{0})$$
>>si ha:
>>$$\lim\limits_{n\to +\infty}f(x_{n},y_{n}) = l$$
>
>Alternativa Equivalente
>
>>[!example] Definizione con Intorno
>>Sia $f:\mathbb{R}^2\to\mathbb{R}$, sia $(x_{0},y_{0})\in\mathbb{R}^2,l\in\overline{\mathbb{R}}$
>>Diciamo che $$\lim\limits_{(x,y)\to (x_{0},y_{0})}f(x,y)=l$$
>>Se $\forall$ intorno $\mathrm{U}_{l}$ di $l$
>>$\exists$ un intorno $\mathrm{U}_{x_{0},y_{0}}:$
>>$$\forall(x,y)\in\mathrm{U}_{(x_{0},y_{0})}$$
>>si ha: 
>>$$f(x,y)\in\mathrm{U}_{l}$$

![[attachements/geogebra-export.png]]
- Per trovare la non-esistenza del limite basta trovare 2 limiti da direzione diversa con soluzione diversa
#### Es
$$
\lim\limits_{(x,y)\to (0,0)} \displaystyle{\frac{xy}{x^2+y^2}}
$$
- Se restringo la mia funzione alla retta $y=x$
>[!done] In Breve
>"Guardo" la funzione solo su $y=x$

$$
\lim\limits_{x\to 0} \displaystyle{\frac{x^2}{2x^2}} = \frac{1}{2}
$$
- Analogamente se restringo la funzione alla retta $y=-x$
$$
\lim\limits_{x\to 0} \displaystyle{\frac{-x^2}{2x^2}} = -\frac{1}{2}
$$

## Calcolo del Limite
---
>[!info] Coordinate Polari
>Per riuscire a calcolare il limite da qualsiasi direzione è possibile scrivere il punto come [[../Insiemi/Numeri Complessi#Forma Trigonometrica|coordinate polari]], così che sia il [[../Insiemi/Numeri Complessi#Modulo|modulo]] a tendere a $0$

#### Es
$$
\lim\limits_{(x,y)\to(0,0) } \displaystyle{\frac{x^3+xy^2}{x^2+y^2}}
$$
- Passiamo a coordinate polari
$$
\begin{cases}
x=\rho cos(\theta) \\
y=\rho sin(\theta)
\end{cases}
\,\,\,\rho>0,\theta \in[0,2\pi]
$$
- Quindi tornando al limite:
$$
\lim\limits_{\rho\to 0} \displaystyle{\frac{\rho^3cos^3(\theta)+\rho^3cos(\theta)sin^2(\theta)}{\rho^2}} = 0
$$
## Funzioni Continue
---
>[!info] Definizione
>Sia $f:\mathbb{R}^2\to\mathbb{R}$
>Sia $(x_{0},y_{0})\in\mathbb{R}^2$
>Diciamo che $f$ è continua in $(x_{0},y_{0})$ se 
>$$\lim\limits_{(x,y)\to (x_{0},y_{0})}f(x,y)=f(x_{0},y_{0})$$

## Teorema di Weierstruss
---
>[!info] Teorema
>Sia $A\subseteq\mathbb{R}^2$ un insieme [[Elementi di Algebra Lineare e Geometria Analitica#Insiemi Aperti e Chiusi|chiuso]] e [[Elementi di Algebra Lineare e Geometria Analitica#Insiemi Limitati|limitato]]
>Sia $f:A\to\mathbb{R}$ Continua
><u>Allora</u>
>$f$ Ammette minimo e massimo assoluti

