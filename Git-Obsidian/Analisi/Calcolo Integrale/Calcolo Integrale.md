## Teorema Fondamentale del Calcolo Integrale $I$
---
>[!info] Teorema
>Sia $f\in C^1([a,b],\mathbb{R})$
><u>Allora</u>
>$$\int _{a}^b f'(x)\, dx =f(b)-f(a)$$

### Dimostrazione
Suddividendo l'intervallo $[a,b]$ in n parti uguali ottengo che:
$$
\displaylines{
f(b) - f(a) = \\
\underbrace{ \sum_{i = 1}^{n} (f(x_{i}) - f(x_{i-1})) }_{ \displaystyle{\cancel{ f(x_{1}) } - f(a) \cancel{ + f(x_{2}) } \cancel{ - f(x_{1}) } + \cancel{ \dots } \cancel{ + f(x_{n-1}) } + f(b) \cancel{ - f(x_{n-1}) }} }
}
$$

- Anche chiamata "Somma Telescopica".

Per il [[../Calcolo Differenziale/Teoremi basati sulle Derivate#Teorema di Lagrange|teorema di Lagrange]] ad ogni intervallo $[x_{i},x_{i-1}]$
$\exists c_{i}\in[x_{i},x_{i-1}]:$
$$
\begin{array}
\ f'(c_{i}) = \displaystyle{\frac{f(x_{i})-f(x_{i-1})}{x_{i}-x_{i-1}}}\\
f(x_{i})-f(x_{i-1})=f'(c_{i})(x_{i}-x_{i-1})
\end{array}
$$
- Di conseguenza, ottengo:
$$
\underbrace{ \sum^n_{i=1}(f'(c_{i})(x_{i}-x_{i-1})) }_{\text{Def. Somma Reiman} }
$$
- Passo al limite
$$
f(b)-f(a)=\int _{a}^b f'(x) \, dx 
$$

## Teorema Fondamentale del Calcolo Integrale $II$
---
>[!info] Teorema
>Sia $f\in C([a,b],\mathbb{R})$
>Sia $F(x)=\displaystyle \int _{a}^x f(t) \, dt \to$ la funzione "_Integrale_" 
><u>Allora</u>
>$F$ è derivabile e $F'(c) = f(c), \forall c \in[a,b]$

### Dimostrazione
Sia $c\in[a,b]$
$$
\lim\limits_{x\to c} \displaystyle{\frac{F(x)-F(c)}{x-c}} = \lim\limits_{x\to c}\displaystyle{\frac{\displaystyle \int _{a}^x f(t) \, dt - \int _{a}^c f(t) \, dt}{x-c}} = \lim\limits_{x\to c} \underbrace{ \displaystyle{\frac{\displaystyle \int _{c}^x f(t)\, dt }{x-c}} }_{ \text{media integrale} }
$$
- Osserviamo che il risultato ottenuto è analogo alla [[Introduzione Integrali#Teorema della Media Integrale|media integrale]]
	- Applico il teorema

$\exists d_{x} \in (c,x): \displaystyle{\frac{1}{x-c}} \int _{c}^x f(t)\, dt = f(d_{x})$
- Passiamo poi al Limite
$$
\underbrace{ \lim\limits_{x\to c} \displaystyle{\frac{F(x)-F(c)}{x-c}} }_{ \displaystyle F'(c) } =\lim\limits_{x\to c} \displaystyle{\frac{1}{x-c}} \int _{c}^x f(t)\, dt =\lim\limits_{x\to c} f(d_{x})
$$
- Ma dato che $d_{x}$ è compreso fra $x$ e $c$, quando $x\to c$ anche $d_{x}\to c$, quindi
$$
F'(c)=f(c)
$$
## Integrazione per Parti
---
>[!info] Teorema
>Sia $f\in C([a,b],\mathbb{R})$ e sia $g\in C^1([a,b],\mathbb{R})$
>Sia $F$ una [[Introduzione Integrali#Primitive|primitiva]] di $f$
><u>Allora</u>
>$$\int _{a}^b f(x)g(x) \, dx = [F(x)g(x)]_{a}^b - \int _{b}^a F(x)-g'(x)\, dx  $$

### Dimostrazione
Considero
$$
(F\cdot g)'(x) = F'(x)g(x)+F(x)g'(x)
$$
- Integro
$$
\underbrace{ \int _{a}^b (Fg)'(x)dx\, dx }_{ \displaystyle [F(x)g(x)]_{a}^b } = \int _{a}^b \underbrace{ F'(x) }_{ f(x) }g(x) \, dx + \int _{a}^b F(x)g'(x)\, dx  
$$
Quindi
$$
\int _{a}^b { f(x) }g(x)\,dx = [F(x)g(x)]_{a}^b -\int _{a}^b F(x)g'(x)\, dx
$$
## Integrazione per Sostituzione
---
>[!info] Teorema
>Siano $I,J$ [[../Funzioni/Introduzione Funzioni#Intervallo|intervalli]] di $\mathbb{R}$
>Siano $f\in C(I,\mathbb{R}),\varphi\in C^1(J,I)$
><u>Allora</u>
>1) Se $\alpha,\beta\in J$$$\int _{\alpha}^\beta f(\varphi(t))\varphi'(t)\, dt = \int _{\varphi(\alpha)}^{\varphi(\beta)} f(x)\, dx  $$
>2) Se $\varphi:J\to I$ è invertibile, siano $a,b\in I$ $$\int _{a}^b f(x) \, dx = \int _{\varphi^{-1}(a)}^{\varphi^{-1}(b)} f(\varphi(t))\varphi'\, dx  $$

### Dimostrazione
Sia $F$ una primitiva di $f$
- Considero $F_{o}\varphi$ e la derivo
$$
(F_{o}\varphi)'(t)=F'(\varphi(t))\cdot \varphi'(t)=f(\varphi(t))\cdot \varphi'(t)
$$
- Integro fra $\alpha$ e $\beta$
$$
\int _{\alpha}^\beta (F_{o}\varphi)'(t)\, dx = \int _{\alpha}^\beta f(\varphi(t))\cdot \varphi'(t)\, dx 
$$
- Usando il teorema fondamentale di Integrazione
$$
\int _{\varphi(\alpha)}^{\varphi(\beta)} f(x) \, dx =F(\varphi(\beta))-F(\varphi(\alpha)) =\int _{\alpha}^\beta (F_{o}\varphi)'(t)\, dx = \int _{\alpha}^\beta f(\varphi(t))\cdot \varphi'(t)\, dx 
$$
## Integrazione di Funzioni Razionali
---
Consideriamo il seguente integrale:
>[!tip] Integrale
>$$\int _{a}^b  \displaystyle{\frac{P_{n}(x)}{{Q_{m}(x)}}}\, dx, n,m \in\mathbb{N}$$
>Dove:
>$P_{n}(x)$ è un polinomio di grado n,
>$Q_{m}(x)$ è un polinomio di grado m.

- Consideriamo il caso $m>n$, poichè altrimenti bastava fare la divisione.
### Caso $m=2,n<2$
Dato $Q_{m}(x)=Q_{2}(x) = ax^2+bx+c$
- Ho 3 casi
#### Caso $\triangle = b^2-4ac > 0$
Ho due radici distinte al denominatore
##### Es
$$
\int _{4}^5 \displaystyle{\frac{x+1}{x^2-4x+3}} \, dx 
$$
- Osservo che il denominatore si può scomporre
$$
\int _{4}^5 \displaystyle{\frac{x+1}{(x-3)(x+1)}} \, dx 
$$
- Ora cerco due numeri $A,B\in\mathbb{R}:$
$$
\displaystyle{\frac{x+1}{(x-3)(x+1)}} = \displaystyle{\frac{A}{x-3}}+ \displaystyle{\frac{B}{x+1}}
$$
- Questo processo si chiama scomposizione in fratti semplici
	- Applico il denominatore comune

$$
= \displaystyle{\frac{A(x+1)+B(x-3)}{(x-3)(x+1)}}
$$
- Questa frazione è uguale a quella originale se e solo se:
$$
\begin{array}
\ x+1 = Ax-A +Bx-3B \\
\Leftrightarrow x+1=x(A+B) -A-3B
\end{array}
$$
- Ora risolvo il sistema a due incognite
$$
\begin{array}
\ \Leftrightarrow\begin{cases}
A+B = 1 \to A=-B+1\\
-A-3B = 1 \to B-1-3B = 1 
\end{cases} \\
\Leftrightarrow\begin{cases}
A=2 \\
B=-1 
\end{cases}
\end{array}
$$
- Quindi
$$
\int_{4}^{5} \displaystyle{\frac{2}{x-3}} \, dx -\int_{4}^{5} \displaystyle{\frac{1}{x+1}} \, dx = [2log(x-3)-log(x-1)] _{4}^5
$$

#### Caso $\triangle = b^2-4ac = 0$
Procedimento analogo al precedente
$$
\int _{4}^5 \displaystyle{\frac{x+1}{(x+3)^2}} \, dx 
$$
- Separiamo il denominatore come:
$$
\int _{4}^5 \displaystyle{\frac{A}{x+3}}+\displaystyle{\frac{B}{(x+3)^2}}
$$

Occasionalmente è possibile procedere anche con il metodo della sostituzione

#### Caso $\triangle = b^2-4ac < 0$
In questo caso notiamo che il denominatore non si può scomporre.
- È necessario infatti cercare di ricondursi ad una arcotangente
$$
\begin{array}
\ \displaystyle \int_{1}^{2} \displaystyle{\frac{2x +1}{2+x^2}} \, dx \\
\displaystyle\int_{1}^{2} \displaystyle{\frac{2x}{2+x^2}}  \, dx + \displaystyle \int_{1}^{2} \displaystyle{\frac{1}{2+x^2}} \, dx  
\end{array}
$$
- Raccolgo il $2$ in modo da riportarmi alla forma: $1+x^2$
$$
\int_{1}^{2} \displaystyle{\frac{1}{2\left( 1+\left( \displaystyle{\frac{x}{\sqrt{ 2 }}} \right)^2 \right)}} \, dx 
$$
- A patto di moltiplicare e dividere per $\sqrt{ 2 }$ otteniamo:
$$
\displaystyle{\frac{\sqrt{ 2 }}{2}}\left[ arctan\left( \displaystyle{\frac{x}{\sqrt{ 2 }}} \right) \right]_{1}^2
$$
