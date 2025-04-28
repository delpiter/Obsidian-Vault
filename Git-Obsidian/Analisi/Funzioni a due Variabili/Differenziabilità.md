## Richiamo
---
![[Derivate#Teorema di Caratterizzazione delle Funzioni Derivabili]]

- Il concetto è equivalente anche per funzioni a due variabili reali
>[!question] Qual è l'unico oggetto che è tangente ad una funzione a due variabili in un punto?

## Trovare il Piano Tangente al Grafico
---
>Determinare, nel caso ci sia, l'equazione del piano tangente al grafico di una funzione $f$ nel punto $(x_{0},y_{0})$
#### Primo Passo

>[!info] Svolgimento
>>[!tip] Intersezione Piano $y=y_{0}$
>>Seziono (o interseco) il grafico della funzione con il piano $y=y_{0}$
>>Individuo così la curva descritta da
>>$$z=f(x,y_{0})$$
>
>>[!tip] Intersezione Piano $x=x_{0}$
>>Seziono (o interseco) il grafico della funzione con il piano $x=x_{0}$
>>Ottenendo così la curva descritta da:
>>$$z=f(x_{0},y)$$
>
>![[pianoTangente.png]]

#### Passo 2
Mi scrivo le equazioni delle rette tangenti:
$$
z =f(x,y_{0})
$$
$$
\begin{cases}
z=f(x_{0},y_{0})+ \displaystyle{\frac{df}{dx}}(x_{0},y_{0})(x-x_{0}) \\
y=y_{0}
\end{cases}
$$
$$
z=f(x_{0},y)
$$
$$
\begin{cases}
z=f(x_{0},y_{0})+ \displaystyle{\frac{df}{dy}}(x_{0},y_{0})(y-y_{0}) \\
x=x_{0}
\end{cases}
$$
![[derivataR3.png|500]]
#### Il Piano
Esiste un piano che contiene entrambe le rette:

>[!info] Definizione
>Se $f$ ammette un piano tangente nel punto $(x_{0},y_{0},f(x_{0},y_{0}))$, esso ha necessariamente l'equazione:
>$$
z=f(x_{0},y_{0})+ \displaystyle{\frac{df}{dx}}(x_{0},y_{0})(x-x_{0})+ \displaystyle{\frac{df}{dy}}(x_{0},y_{0})(y-y_{0})
>$$

## Funzione Differenziabile
---
>[!info] Definizione
>Sia $f:\mathbb{R}^2\to\mathbb{R}$ o $f:A\to\mathbb{R}, A\subseteq\mathbb{R}^2 \text{ Aperto}$
>Sia $(x_{0},y_{0})\in\mathbb{R}^2$, supponiamo $f$ sia derivabile
>Diciamo che $f$ è differenziabile in $(x_{0},y_{0})$ se $f(x,y)=$
>$$f(x_{0},y_{0})+\displaystyle{\frac{df}{dx}}(x_{0},y_{0})(x-x_{0})+ \displaystyle{\frac{df}{dy}}(x_{0},y_{0})(y-y_{0})+ \underbrace{ \circ(|(x,y)-(x_{0},y_{0})|) }_{\displaystyle \circ( \sqrt{ (x-x_{0})^2 +(y-y_{0})^2}) }$$
>Per $(x,y)\to (x_{0},y_{0})$

- Si può scrivere anche con l'incremento:
>[!tip] Equivalente
>$$f(x_{0}+h,y_{0}+k)=f(x_{0},y_{0})+\displaystyle{\frac{df}{dx}}(x_{0},y_{0})h+ \displaystyle{\frac{df}{dy}}(x_{0},y_{0})k+ \circ(\sqrt{ h^2+k^2 })$$
>Per $(h,k)\to(0,0)$
>
>>[!example] Differenziale
>>Chiamo differenziale di $f$ nel punto $(x_{0},y_{0})$
>>La funzione lineare
>>$$\begin{array}
\ df_{(x_{0},y_{0})}:\mathbb{R}^2\to\mathbb{R} \\
(h,k) \mapsto \displaystyle{\frac{df}{dx}}(x_{0},y_{0})h+ \displaystyle{\frac{df}{dy}}(x_{0},y_{0})k
\end{array}
$$

### Funzione Differenziabile 2 volte
>[!info] Definizione
>Diciamo che $f$ è derivabile $2$ volte in $(x_{0},y_{0})$ se $f$ è derivabile e $\partial xf$ e $\partial yf$ sono [[Calcolo Differenziale#Derivabilità|derivabili]]
>E le indico come:
>>[!tip] Notazione
>>$$\displaystyle\frac{ \partial^2 f }{ \partial x^2 } = \displaystyle\frac{ \partial  }{ \partial x } \left( \displaystyle\frac{ \partial f }{ \partial x }  \right) \quad \displaystyle\frac{ \partial^2 f }{ \partial y^2 } = \displaystyle\frac{ \partial  }{ \partial y } \left( \displaystyle\frac{ \partial f }{ \partial y }  \right) \quad\displaystyle\frac{ \partial^2 f }{ \partial x \partial y } = \displaystyle\frac{ \partial  }{ \partial x } \left( \displaystyle\frac{ \partial f }{ \partial y }  \right) \quad \displaystyle\frac{ \partial^2 f }{ \partial x \partial y } = \displaystyle\frac{ \partial  }{ \partial y } \left( \displaystyle\frac{ \partial f }{ \partial x }  \right) $$

### Matrice Hessiana
>[!info] Definizione
>Chiamiamo [[Elementi di Algebra Lineare e Geometria Analitica#Matrici su $ mathbb{R}$ di tipo $(m,n)$|matrice]] Hessiana di $f$ in $(x_{0},y_{0})$ la matrice:
>$$H_{f}(x_{0},y_{0})\begin{pmatrix}
\displaystyle\frac{ \partial^2 f }{ \partial x^2 }(x_{0},y_{0})  & \displaystyle\frac{ \partial^2 f }{ \partial x \partial y }(x_{0},y_{0}) \\
\displaystyle\frac{ \partial^2 f }{ \partial y^2 }(x_{0},y_{0})  & \displaystyle\frac{ \partial^2 f }{ \partial y \partial x }(x_{0},y_{0})
\end{pmatrix}
>$$

### Teorema di Schwartz
>[!info] Teorema
>Sia $A\subseteq\mathbb{R}^2$, $f:A\to\mathbb{R}$, $f\in C^2(A,\mathbb{R})$
><u>Allora</u>
>$$\displaystyle\frac{ \partial^2 f }{ \partial x \partial y }(x,y) =
\displaystyle\frac{ \partial^2 f }{ \partial y^2 }(x,y)$$
## Relazione funzione Differenziabile e Continua
---
>[!info] Teorema
>Se $f$ è differenziabile in $(x_{0},y_{0})$
><u>Allora</u>
>$f$ è continua in $(x_{0},y_{0})$

### Dimostrazione
Passo al limite nella definizione di differenziabilità
$$f(x_{0}+h,y_{0}+k)=f(x_{0},y_{0})+\displaystyle{\frac{df}{dx}}(x_{0},y_{0})h+ \displaystyle{\frac{df}{dy}}(x_{0},y_{0})k+ \circ(\sqrt{ h^2+k^2 })$$
>Per $(h,k)\to(0,0)$

$$
\lim\limits_{(h,k)\to (0,0)}f(x_{0}+h,y_{0}+k)=f(x_{0},y_{0})
$$
#### Esercizi Esempio
Determinare l'equazione del piano tangente al grafico di $f$ nel punto $(P_{0},f(P_{0}))$
- $f(x,y)=x^3-2x^2y-5xy^2+y^3$
	- $f(x_{0},y_{0})=f(0,1) = 1$
	- $\displaystyle\frac{ \partial f }{ \partial x }(x,y)=3x^2-4xy-5y^2\to \displaystyle\frac{ \partial f }{ \partial x }(0,1)=-5$
	- $\displaystyle\frac{ \partial f }{ \partial y }(x,y)=-2x^2-10xy+3y^2\to \displaystyle\frac{ \partial f }{ \partial y }(0,1)=3$

$$
z=1-5x+3(y-1) = -5x+3y-2
$$
Determinare il differenziale di $f$ all'origine
- $f(x,y)=x^2+x(y-1)+2y$
	- $\displaystyle\frac{ \partial f }{ \partial x }(x,y)=2x+y-1 \to \displaystyle\frac{ \partial f }{ \partial x }(0,0)=-1$
	- $\displaystyle\frac{ \partial f }{ \partial y }(x,y)=x+2\to \displaystyle\frac{ \partial f }{ \partial y }(0,0)=2$

$$
df_{(0,0)}(h,k)=-h+2k
$$
>[!info] Teorema
>Sia $f:\mathbb{R}^2\to\mathbb{R}$, Sia $(x_{0},y_{0})\in\mathbb{R}^2$
>Se $f\in C^1(\mathbb{R}^2,\mathbb{R})=\left\{  f:\mathbb{R}^2\to\mathbb{R} \text{ derivabili, con } \displaystyle\frac{ \partial f }{ \partial x } ,\displaystyle\frac{ \partial f }{ \partial y }\text{ continue }\right\}$
><u>Allora</u>
>$f$ è differenziabile

### Riassumendo
$$f\in C^1 \implies f \text{ differenziabile } \implies f \text{ continua}$$
- Ma:
$$
f \text{ derivabile} \cancel{ \implies } f \text{ continua}
$$