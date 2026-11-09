## Derivate di funzioni Composte in $\mathbb{R}^2$
---
>[!info] Metodo "intuitivo"
>Sia $f:\mathbb{R}^2\to\mathbb{R}, g:\mathbb{R}\to\mathbb{R}$
>Definisco
>$h:\mathbb{R}^2\to\mathbb{R}$
>$$h(x,y)=g(f(x,y)) = (g_{o}f)(x,y)$$
>>[!example] Esempio
>>$$
\begin{cases}
\partial xh = g'(f(x,y))\partial xf(x,y) \\
\partial yh = g'(f(x,y))\partial yf(x,y)
\end{cases}
>>$$

>[!info] Metodo secondario
>Sia $f:\mathbb{R}^2\to\mathbb{R},g:\mathbb{R}\to\mathbb{R}^2$
>Considero $h:\mathbb{R}\to\mathbb{R}$
>$$h(t)=f(g_{1}(t),g_{2}(t))$$
>>[!example] Esempio
>>$$h'(t)=\partial xf(g_{1}(t),g_{2}(t))g_{1}'(t)+ \partial yf(g_{1}(t),g_{2}(t))g_{2}'(t) = \nabla f(g_{1}(t),g_{2}(t))\cdot (g_{1}'(t),g_{2}'(t))$$

## Formula di Taylor al $2^o$ Ordine
---
>[!info] Definizione
>Sia $A\subseteq\mathbb{R}^2$, $A$ aperto, sia $f:A\to\mathbb{R}$
>Sia $(x_{0},y_{0})\in A$, supponiamo $f\in C^2(A,\mathbb{R})$
>Sia $V=(h,k)$ versore
>Considero
>$$H(t)=f(\underbrace{ x_{0}+th }_{ g_{1}(t) },\underbrace{ y_{0}+tk }_{ g_{2}(t) })$$

### Formula per $H$ di punto iniziale $t=0$ e ordine $2$
$$
H(t)=H(0)+H'(0)t+\displaystyle{\frac{H''(0)}{2}}t^2+\circ (t^2)\text{ per }t\to0
$$
Calcolo i singoli componenti
##### $H(0)$
$$
f(x_{0},y_{0})
$$
##### $H'(t)$
$$
H'(t)=\partial xf(x_{0} +th,y_{0}+tk)h +\partial yf(x_{0} +th,y_{0}+tk)k
$$
- $H'(0)=\partial xf(x_{0},y_{0})h +\partial yf(x_{0},y_{0})k$

##### $H''(t)$
$$
H''(t) = \displaystyle\frac{ \partial^2 f }{ \partial x^2 }(x_{0}+th,y_{0}+tk)h^2 + 2\displaystyle\frac{ \partial^2 f }{ \partial x \partial y }(x_{0}+th,y_{0}+tk)hk+\displaystyle\frac{ \partial^2 f }{ \partial y^2 }(x_{0}+th,y_{0}+tk)k^2 
$$
- $H''(0)=\displaystyle\frac{ \partial^2 f }{ \partial x^2 }(x_{0},y_{0})h^2 + 2\displaystyle\frac{ \partial^2 f }{ \partial x \partial y }(x_{0},y_{0})hk+\displaystyle\frac{ \partial^2 f }{ \partial y^2 }(x_{0},y_{0})k^2$

#### Conclusione
$$
\begin{array}{}
H(t)= f(x_{0}+th,y_{0}+tk) = f(x_{0},y_{0})+ \\
+(\underbrace{ \partial xf(x_{0},y_{0})h +\partial yf(x_{0},y_{0})k }_{ \displaystyle df_{(x_{0},y_{0})}(h,k) })t+ \\
+\left( \underbrace{ \displaystyle{\displaystyle\frac{ \partial^2 f }{ \partial x^2 }(x_{0},y_{0})h^2 + 2\displaystyle\frac{ \partial^2 f }{ \partial x \partial y }(x_{0},y_{0})hk+\displaystyle\frac{ \partial^2 f }{ \partial y^2 }(x_{0},y_{0})k^2 }}_{ \displaystyle d^2f_{(x_{0},y_{0})}(h,k) } \right) \displaystyle{\frac{t^2}{2}} +\\
+\circ(t^2) \text{ per }t\to0
\end{array}
$$
#### Formula di Taylor
$$
f(x_{0}+th,y_{0}+tk) = f(x_{0},y_{0})+df_{(x_{0},y_{0})}(h,k)t+d^2f_{(x_{0},y_{0})}(h,k)t^2 +\circ(t^2)
$$