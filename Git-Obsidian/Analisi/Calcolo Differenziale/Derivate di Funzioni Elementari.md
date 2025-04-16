## Monomio
---
>[!tip] Funzione
>$$
\begin{array}
\ f(x) = x^n, n\in\mathbb{N} \\
f'(x)=nx^{n-1}
\end{array}
>$$
- Utilizzando la [[Definizioni_Analisi#Formula del Binomio di Newton|formula del binomio di newton]] voglio calcolare $f'(c), \forall c\in\mathbb{R}$
### Dimostrazione
$$
\begin{array}
\ \lim\limits_{h\to 0 } \displaystyle{\frac{(c+h)^n-c^n}{h}} = \lim\limits_{h\to 0} \displaystyle{\frac{\displaystyle\left( \sum^n_{k=0} \binom{n}{k}c^{n-k}h^k\right)-c^n}{h}} = \\
=\lim\limits_{h\to 0} \displaystyle{\frac{\cancel{ c^n }+n c^{n-1}h+\displaystyle\left( \sum^n_{k=2} \binom{n}{k}c^{n-k}h^k\right)-\cancel{ c^n }}{h}} =
\end{array}
$$
- Poichè la somma per $h\to 0$ tende a 0 ho:
$$
\displaystyle{\frac{n\cdot c^{n-1}\cdot h}{h}} = nc^{n-1}
$$
## Esponenziale
---
>[!tip] Funzione
>$$
\begin{array}
\ f(x)=e^x, c\in\mathbb{R} \\
f'(x) = e^{ x }
\end{array}
>$$

### Dimostrazione
$$f'(c)=\lim\limits_{x\to c} \displaystyle{\frac{e^x-e^c}{x-c}}=\lim\limits_{x\to c} \displaystyle{\frac{e^c(e^x-c-1)}{x-c}} = e^c$$
## Teorema dell'algebra delle Derivate
---
>[!info] Teorema
>Sia $I$ intervallo di $\mathbb{R}$, $f,g:I\to\mathbb{R},c\in I,k\in\mathbb{R}$
>Se $f,g$ sono entrambe derivabili in $c$
><u>Allora</u>
>$(f+g)'(c)=f'(c)+g'(c)$
>$(f\cdot g)'(c)=f'(c)\cdot g(c)+f(c)\cdot g'(c)$
>$\displaystyle{\left( \frac{f}{g}\right)(c)}= \displaystyle{\frac{f'(c)\cdot g(c)-f(c)\cdot g'(c)}{(g(c))^2}}, g(c)\neq0$
>$(kf)'(c) = kf'(c)$

### Dimostrazione Proprietà 1
$$
\begin{array}
\ \displaystyle{\frac{(f+g)(x)-(f+g)(c)}{x-c}} = \displaystyle{\frac{f(x)+g(x)-f(c)-f(x)}{x-c}} =\\
= \displaystyle{\frac{f(x)-f(c)}{x-c}} + \displaystyle{\frac{g(x)-g(c)}{x-c}} \\
\end{array}
$$
- Passiamo al limite per $x\to c$
- $$
\lim\limits_{x\to c}\underbrace{ \displaystyle{\frac{f(x)-f(c)}{x-c}} }_{ \displaystyle f'(c) } +\lim\limits_{x\to c} \underbrace{ \displaystyle{\frac{g(x)-g(c)}{x-c}} }_{ \displaystyle g'(c) }
$$
### Dimostrazione  Proprietà 2
$$
\begin{array}
\ \displaystyle{\frac{(f\cdot g)(x)-(f\cdot g)(c)}{x-c}}=\displaystyle{\frac{f(x)g(x)-f(x)g(c)+f(x)g(c)-f(c)g(c)}{x-c}}= \\
= f(x)\displaystyle{\frac{(g(x)-g(c))}{x-c}}+g(c) \displaystyle{\frac{(f(x)-f(c))}{x-c}}
\end{array}
$$
- Passiamo al limite per $x\to c$
$$
\lim\limits_{x\to c} \underbrace{ f(x) }_{ f(c) }\underbrace{ \displaystyle{\frac{(g(x)-g(c))}{x-c}} }_{ g'(x) }+g(c) \underbrace{ \displaystyle{\frac{(f(x)-f(c))}{x-c}} }_{ f'(x) }
$$
### Dimostrazione Proprietà 3
$$
\begin{array}
\ \displaystyle{\frac{\left( \frac{f}{g} \right)(x)-\left( \frac{f}{g} \right)(c)}{x-c}} = \displaystyle{\frac{\displaystyle{\frac{f(x)}{g(x)}}-\displaystyle{\frac{f(x)}{g(c)}}+\displaystyle{\frac{f(x)}{g(c)}}-\displaystyle{\frac{f(c)}{g(c)}}}{x-c}}
\end{array}
$$
## Derivate di Funzioni Composte
---
>[!info] Teorema
>Siano $I,J$ [[Git-Obsidian/Analisi/Funzioni/Introduzione Funzioni#Intervallo|intervalli]] di $\mathbb{R}$, $f:I\to\mathbb{R}$, $g:J\to\mathbb{R},f(I)\subseteq J$
>Sia $c\in I$
>Supponiamo $f$ derivabile in $c$ e $g$ sia derivabile in $f(c)$
><u>Allora</u>
>$$(g_{o}f)'(c)=g'(f(c))f'(c)$$
### Dimostrazione
$$
\displaystyle{\frac{(g_{o}f)(x)-(g_{o}f)(c)}{x-c}}= \displaystyle{\frac{g(f(x))-g(f(c))}{x-c}}
$$
- Per ipotesi $g$ è derivabile in $f(c)$ e dunque per il [[Derivate#Teorema di Caratterizzazione delle Funzioni Derivabili|teorema di caratterizzazione di funzioni derivabili]] si ha:
$$
g(y) = g(f(c))+g'(f(c))\cdot (y-f(c))+\circ(y-f(c)) \text{ per }y\to f(c)
$$
- Posso sostituire $y=f(x)$ infatti: $f(x)\to f(c) \text{ per } x\to c$ poichè $f$ è continua
$$
g(f(x)) = g(f(c))+g'(f(c))\cdot (f(x)-f(c))+\circ(f(x)-f(c)) \text{ per }f(x)\to f(c)
$$
- Applico la definizione di derivata
$$
\begin{array}
\ 
\lim\limits_{x\to c} \displaystyle{\frac{\cancel{ g(f(c)) }+g'(f(c))\cdot (f(x)-f(c))+\circ(f(x)-f(c))-\cancel{ g(f(c)) }}{x-c}}= \\
= \lim\limits_{x\to c}g'(f(c))\cdot\underbrace{  \displaystyle{\frac{f(x)-f(c)}{x-c}} }_{ f'(c) } = g'(f(c))f'(c)
\end{array}
$$
## Derivata della Funzione Inversa
---
>[!info] Teorema
>Sia $I$ [[Git-Obsidian/Analisi/Funzioni/Introduzione Funzioni#Intervallo|intervallo]] di $\mathbb{R}$, $f:I\to\mathbb{R}$ invertibile e derivabile in $c\in I$
>Supponiamo $f'(c)\neq 0$
><u>Allora</u>
>Posto $y=f(c)$, si ha:
>$$(f^{-1})'(y)= \displaystyle{\frac{1}{\underbrace{ f'(f^{-1}(y)) }_{ c }}}$$
### Dimostrazione Geometrica
![[Pasted image 20231031153153.png]]
- Equazione di $r : y=\underbrace{ m }_{ f'(x) }x+q$
	- $x= \displaystyle{\frac{y-q}{m}}$
- Equazione di $s:y= \displaystyle{\frac{x}{m}}- \displaystyle{\frac{q}{m}}$
- Quindi il coefficiente angolare di $s$ è $\displaystyle{\frac{1}{m}} \implies \displaystyle{\frac{1}{f'(x)}}$
### Osservazione
Considero $f(x)=x^b, x>0,b\in\mathbb{R}$
$$
f(x)=e^{ln(x^b)} \implies f'(x) = \underbrace{ e^{b\cdot ln(x)} }_{ \displaystyle g'(f(x)) }\cdot \displaystyle{\underbrace{ \frac{b}{x} }_{ f'(x) }}=x^b\cdot \displaystyle{\frac{b}{x}} = bx^{b-1}
$$
$$
\lim\limits_{h\to 0^+} \displaystyle{\frac{h^b}{h}} = \begin{cases}
0 \text{ se }b>1 \\
1 \text{ se }b=1 \\
+\infty \text{ se } 0<b<1
\end{cases}
$$
>[!done] In Breve
>$x^b$ è derivabile in $0$ se $b\geq 1$
## Logaritmo
>[!tip] Funzione
>$$
\begin{array}
\ f(x)=ln(x)=(exp)^{-1}(x) \\
f'(x) = \displaystyle{\frac{1}{x}}
\end{array}
>$$
### Dimostrazione
$$
\begin{array}
\ (ln)'(x) = \displaystyle{\frac{1}{exp(ln(x))}} = \displaystyle{\frac{1}{x}}
\end{array}
$$
## Funzioni Trigonometriche
---
### Seno
>[!tip] Funzione
>$$
\begin{array}
\ f(x)=sin(x) \\
f'(x) = cos(x)
\end{array}
>$$

#### Dimostrazione
$$
\begin{array}
\ f'(c)=\lim\limits_{h\to 0} \displaystyle{\frac{sen(c+h)-sen(c)}{h}}= \\
\lim\limits_{h\to 0} \displaystyle{\frac{sen(c)cos(h)+sen(h)cos(c)-sen(c)}{h}}= \\
= \lim\limits_{h\to 0} sen(c)\displaystyle{\underbrace{ \frac{(cos(h)-1)}{h} }_{ 0 }}+\displaystyle{\underbrace{ \frac{sen(h)}{h} }_{ 1 }cos(c)} = cos(c)
\end{array}
$$
### Coseno
>[!tip] Funzione
>$$
\begin{array}
\ f(x)=cos(x) \\
f'(x) = -sin(x)
\end{array}
>$$
#### Dimostrazione
$$
\begin{array}
\ f'(c)= \lim\limits_{h\to 0} \displaystyle{\frac{cos(c+h)-cos(c)}{h}} = \lim\limits_{h\to 0} \displaystyle{\frac{cos(c)cos(h)-sen(c)sen(h)-cos(c)}{h}} \\
\lim\limits_{h\to 0} cos(c)\displaystyle{\frac{cos(h)-1}{h}}- \displaystyle{\frac{sen(c)sen(h)}{h}}
\end{array}
$$
### Tangente
>[!tip] Funzione
>$$
\begin{array}
\ f(x)=tan(x) =\displaystyle{\frac{sen(x)}{cos(x)}},x\neq \displaystyle{\frac{\pi}{2}}+k\pi, k\in\mathbb{Z} \\
f'(x)= \displaystyle{\frac{1}{cos^2(x)}} = 1+tan^2(x)
\end{array}
>$$

#### Dimostrazione
$$
\begin{array}
\ f'(x)= \displaystyle{\frac{cos(x)\cdot cos(x)-(-sen(x)\cdot sen(x))}{cos^2(x)}}= \\
= \displaystyle{\frac{cos^2(x)+sen^2(x)}{cos^2(x)}}= \displaystyle{\frac{1}{cos^2(x)}}=1+ tan^2(x)
\end{array}
$$

### Arcoseno
>[!tip] Funzione
>$$
\begin{array}
\ f(x)=arcsen(x), \ \ \ \ arcsen(x)\in\left[ - \displaystyle{\frac{\pi}{2}}; \displaystyle{\frac{\pi}{2}} \right] \\
f'(x) = \displaystyle{\frac{1}{\sqrt{ 1-x^2 }}}
\end{array}
>$$

#### Dimostrazione
$$
\begin{array}
\ f'(x)= \displaystyle{\frac{1}{sen'(arcsen(x))}} = \displaystyle{\frac{1}{cos(arcsen(x))}}=\displaystyle{\frac{1}{\sqrt{ 1-x^2 }}}
\end{array}
$$

>[!done] $cos(arcsen(x))$
>Il coseno dell'arcoseno di $x$ è il valore del coseno dell'angolo ottenuto facendo l'arcoseno di $x$
>$cos^2(x)=1-sen^2(x)$
>Ma l'arcoseno di $x$ non è altro che il risultato di $sin(x)$ quindi nel nostro caso:
>$cos(x)=\sqrt{ 1-x^2 }$

### Arcocoseno
>[!tip] Funzione
>$$
\begin{array}
\ f(x)= arccos(x),\ \ \ \ \ arccos(x)\in\left[ 0;\pi \right] \\
f'(x) = - \displaystyle{\frac{1}{\sqrt{ 1-x^2 }}}
\end{array}
>$$

#### Dimostrazione
$$
f'(x) = \displaystyle{\frac{1}{cos'(arccos(x))}} = \displaystyle{\frac{1}{-sen(arccos(x))}}=- \displaystyle{\frac{1}{\sqrt{ 1-x^2 }}}
$$
### Arcotangente
>[!tip] Funzione
>$$
\begin{array}
\ f(x)=arctan(x) \\
f'(x) = \displaystyle{\frac{1}{1+x^2}}
\end{array}
>$$

#### Dimostrazione
$$
\begin{array}
\ f'(x)= \displaystyle{\frac{1}{tan'(arctan(x))}}= \displaystyle{\frac{1}{1+\underbrace{ tan^2(arctan(x)) }_{ \displaystyle x^2 }}} = \displaystyle{\frac{1}{1+x^2}}
\end{array}
$$