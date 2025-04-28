## Derivata Parziale
---
>[!info] Definizione
>Sia $A\subseteq\mathbb{R}^2$,$f:A\to\mathbb{R}$, $A$ insieme [[Elementi di Algebra Lineare e Geometria Analitica#Insiemi Aperti e Chiusi|aperto]]
>>[!example] Su $x$
>>Diciamo che $f$ è derivabile rispetto ad $x$ nel punto $(x_{0},y_{0})\in A$ se esiste
>>$$\lim\limits_{x\to x_{0}} \displaystyle{\frac{f(x,y_{0})-f(x_{0},y_{0})}{x-x_{0}}}=\lim\limits_{h\to 0} \displaystyle{\frac{f(x_{0}+h,y_{0})-f(x_{0},y_{0})}{h}}\in\mathbb{R}$$
>
>>[!example] Su $y$
>>Analogamente diciamo che $f$ è derivabile rispetto ad $x$ nel punto $(x_{0},y_{0})\in A$ se esiste
>>$$\lim\limits_{y\to y_{0}} \displaystyle{\frac{f(x_{0},y)-f(x_{0},y_{0})}{y-y_{0}}}=\lim\limits_{h\to 0} \displaystyle{\frac{f(x_{0},y_{0}+h)-f(x_{0},y_{0})}{h}}\in\mathbb{R}$$

### Notazioni
- Per indicare la derivata parziale di una funzione di due variabili si posso usare diverse notazioni
$$
\displaystyle{\frac{\partial f}{\partial x}},\displaystyle{\frac{d f}{d x}},f_{x},\partial_{x}f |\displaystyle{\frac{\partial f}{\partial y}},\displaystyle{\frac{d f}{d y}},f_{y},\partial yf
$$
#### Es
- $f(xy)=2xe^{xy}$
$$
\displaystyle{\frac{df}{dx}}(x,y)=2e^{ xy }+ye^{ xy }2x
$$
$$
\displaystyle{\frac{df}{dy}}(x,y)=2x^2e^{ xy }
$$
### Derivabilità
>[!tip] Definizione
>Diciamo che $f$ è derivabile in $(x_{0},y_{0})$ se esistono le due derivate parziali:
>$$\displaystyle{\frac{df}{dx}}, \displaystyle{\frac{df}{dy}}$$

#### Osservazione
Sia $f$ derivabile in $(x_{0},y_{0})$ non implica che $f$ sia continua

### Gradiente
>[!info] Definizione
>$$\nabla f(x_{0},y_{0}) = \left[ \displaystyle\frac{ \partial f }{ \partial x }(x_{0},y_{0}) ,\displaystyle\frac{ \partial f }{ \partial y }(x_{0},y_{0})  \right]$$
>
>>[!done] In Breve
>>Il gradiente indica la ***direzione di massima pendenza*** della funzione in un punto.
>>In altre parole, il gradiente "*punta*" nella direzione in cui la funzione *cresce più rapidamente*.

## Derivata Direzionale
---
>[!info] Definizione
>Sia $(x_{0},y_{0})\in\mathbb{R}^2, \underbrace{ V }_{ Versore }=1(cos(\theta),sin(\theta)), \theta \in[0,2\pi]$
>Data $f:\mathbb{R}^2\to\mathbb{R}$
>
>>[!done] A Parole
>>Voglio vedere come varia $f$ lungo la direzione $V$
>
>Considero il rapporto incrementale di $f$
>$$\displaystyle{\frac{f(x_{0}+tcos(\theta),y_{0}+tsin(\theta))-f(x_{0},y_{0})}{t}}$$
>
>>[!done] In Breve
>>Se esiste il limite per $t\to0$ del rapporto incrementale ed è in $\mathbb{R}$ dico che $f$ è derivabile lungo la direzione $V$ nel punto $(x_{0},y_{0})$
>$$\lim\limits_{t\to 0}\displaystyle{\frac{f(x_{0}+tcos(\theta),y_{0}+tsin(\theta))-f(x_{0},y_{0})}{t}} = 0$$

- Indichiamo la derivata direzionale di $f$ lungo $V$ con:
$$
D_{V}f\text{ oppure }\delta_{V}f
$$

## Teorema del Gradiente
--- 
>[!info] Teorema
>Sia $f:A\to\mathbb{R}$, $A\subseteq\mathbb{R}^2$ Aperto, sia $(x_{0},y_{0})\in A$
>Sia $V=(cos(\theta),sin(\theta))$
>Se $f$ è [[Differenziabilità#Funzione Differenziabile|differenziabile]] in $(x_{0},y_{0})$
><u>Allora</u>
>$$D_{v}f(x_{0},y_{0})= \nabla f(x_{0},y_{0})\cdot V$$

### Dimostrazione
Considero la definizione di derivata direzionale:
$$
\displaystyle{\frac{f(x_{0}+\overbrace{tcos(\theta)}^{h},y_{0}+\overbrace{tsin(\theta)}^{k})-f(x_{0},y_{0})}{t}}
$$
- Uso la definizione di [[Differenziabilità#Funzione Differenziabile|differenziabilità]]:
$$
\displaystyle{\frac{\cancel{ f(x_{0},y_{0}) }+\partial xf(x_{0},y_{0})\cancel{ t }cos(\theta)+\partial yf(x_{0},y_{0})\cancel{ t }sin(\theta)-\cancel{ f(x_{0},y_{0}) }+\circ(t)}{\cancel{ t }}}
$$
- Passo al limite per $t\to0$
$$D_{v}f(x_{0},y_{0})=\partial xf(x_{0},y_{0})cos(\theta)+\partial yf(x_{0},y_{0})sin(\theta) = \nabla f(x_{0},y_{0})\cdot V$$
#### Osservazione
Da tale formula si osserva che $D_{v}f(x_{0},y_{0})$ è massima quando $V=\nabla f(x_{0},y_{0})$
>[!done] In Breve
>$\nabla f(x_{0},y_{0})$ indica la direzione di massima crescita

$$
D_{v}f max \Leftrightarrow \nabla f\cdot Vmax \Leftrightarrow \nabla f \parallel V \Leftrightarrow \text{ direzione }\nabla f = \text{ direzione }V \Leftrightarrow D_{v}f max = \text{ dir } \nabla f
$$
#### Osservazione
Se guardo la variazione di $f$ lungo un vettore $V$ tangente ad una [[Funzioni di due Variabili Reali#Curva di Livello|linea di livello]] "vedo" una $f$ costante e dunque:
$$
D_{v}f(x_{0},y_{0}) = 0 = \nabla f(x_{0},y_{0})\cdot V \Leftrightarrow \nabla f(x_{0},y_{0}) \perp V
 $$
