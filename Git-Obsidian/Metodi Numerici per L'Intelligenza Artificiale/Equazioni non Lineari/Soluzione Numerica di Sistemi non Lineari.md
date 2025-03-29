>[!help] Problema
>Data una funzione $f:\mathbb{R}\mapsto\mathbb{R}$ ***non lineare*** consideriamo il problema di determinare i valori $\alpha\in\mathbb{R}$ tali che $f(\alpha)=0$.
>Tali valori sono chiamati ***zeri*** o ***radici*** della funzione $f$.

> Esempi di funzioni non lineari

- $x+4\sin(x)=0$
- $e^x+x^2=0$
- $\sqrt{ x }-\log(x)=0$

 Calcolare gli zeri di queste funzioni risulta spesso ***molto complesso***.
 - Risulta preferibile disporre di algoritmi che ***forniscono approssimazioni***.

>[!tldr] Idea
>L'***approssimazione numerica di una radice*** $\alpha$ di $f(x)$ si basa sull'uso di metodi iterativi che consistono nella costruzione di una *successione di iterati* $x_{1},x_{2},x_{3},\dots,x_{k},\dots$ che ***tende*** alla soluzione $\alpha$ del problema.
>$$\lim\limits_{k\to+\infty }x_{k}=\alpha$$

È necessario rendere il problema [[Condizionamento#Condizionamento di un Problema|ben posto]]:
- Individuare un intervallo $I$ contenente una sola radice.
- Applicare il metodo fino a ***convergenza alla soluzione***.

### Molteplicità
>[!def] Definizione
>Se $\alpha\in\mathbb{R}$ è tale che $f(\alpha)=0$ ed $f'(\alpha)\neq0$, $x$ viene chiamata ***radice semplice***.
>In generale se $f^{(k)}(\alpha)=0,\quad k=0,\dots,m-1$ e $f^{(m)}(\alpha)\neq0$ allora $\alpha$ è detta ***radice multipla*** di [[9 - Matrici Diagonali#Molteplicità|molteplicità]] $m$

> Esempio
- La funzione $f(x)=(x+2)^2$ ha in $x=-2$ uno *zero* di ***molteplicità*** $2$.

Infatti:
$$
\begin{array}
\ f'(x)=2(x+2) \\
f''(x)=2
\end{array}
$$
## Condizionamento del Problema
---
> Sia $\alpha$ tale che $f(\alpha)=0$ con $\alpha$ ***zero semplice***.

>[!abstract] Approssimazione
>Il valore calcolato numericamente $\tilde{\alpha}=\alpha+\delta$, e $\delta>0$.
>Con $\delta$ piccolo, $\tilde{\alpha}$ ***può essere vista*** come la radice dell'equazione:
>$$\tilde{f}(x)=f(x)+\varepsilon g(x)=0$$
>Con $\varepsilon>0$, $\varepsilon$ piccolo, $f(x),g(x)$  [[Differenziabilità#Funzione Differenziabile|differenziabili]].

Dove la differenza $|\tilde{f}(x)-f(x)|=|\varepsilon g(x)|$ rappresenta la ***perturbazione sulla funzione originale*** (*perturbazione sui dati*).
- La differenza $|\tilde{\alpha}-\alpha| = |\delta|$ è la ***perturbazione sui risultati***.

Si ha quindi che $\tilde{f}(\tilde{\alpha})=0$

> Si consideri uno sviluppo in serie di [[Formula di Taylor|Taylor]] del primo ordine di $\tilde{f}(x)$ in un intorno di $\alpha$

$$
0=\tilde{f}(\alpha+\delta)=\tilde{f}(\alpha)+\delta\tilde{f}'(\alpha)+\frac{1}{2}\delta^2\tilde{f}''(\xi)\qquad \xi \in(\alpha,\alpha+\delta)
$$
**Trascurando** i termini del secondo ordine:
$$
0=\tilde{f}(\alpha+\delta)\approx \tilde{f(\alpha)}+\delta\tilde{f}'(\alpha)
$$
- Sostituiamo nell'equazione la *definizione* di $\tilde{f}(x)$ e ricordiamo che $\tilde{\alpha}=\alpha+\delta$.
$$
0\approx f(\alpha) +\varepsilon g(\alpha)+\delta(f'(\alpha)+\varepsilon g'(\alpha))
$$
Per *ipotesi* $f(\alpha)=0$
$$
\varepsilon g(\alpha)+\delta f'(\alpha)+\varepsilon\delta g'(\alpha)\approx 0
$$
- Ora considerando $\varepsilon\cdot\delta$ ***trascurabile***.
$$
\varepsilon g(\alpha)+\delta f'(\alpha)\approx 0
$$
>Da cui

$$
\delta\approx -\displaystyle{\frac{\varepsilon g(\alpha)}{f'(\alpha)}}
$$
>[!hint] $|\tilde{\alpha}-\alpha|= |\delta|\approx K|\varepsilon g(\alpha)|$
>Dove la quantità $K=\displaystyle{\frac{1}{f'(\alpha)}}$ rappresenta l'[[Condizionamento#Quantificare il Condizionamento|indice di condizionamento]] del ***problema***.

Se $|f'(\alpha)|$ è molto piccolo allora il problema è ***mal condizionato***.

#### Esempi
>[!done] Problema Ben Condizionato

<font color="CornflowerBlue">$f(x)=\displaystyle\frac{x^2}{18}-\frac{2}{9},\quad x\in[0,3]$</font>
<font color="red">$\tilde{f}(x)=\displaystyle\frac{x^2}{18}-\frac{2}{9}+0.01,\quad x\in[0,3]$</font>

```functionplot
---
title: 
xLabel: 
yLabel: 
bounds: [0,3,-0.3,0.3]
disableZoom: false
grid: true
---
f(x)=(x^2/18)-(2/9)
g(x)=(x^2/18)-(2/9)+0.01
```

La funzione $f(x)$ si annulla nel punto di ascissa $x=2$
- La funzione $\tilde{f}(x)$ si annulla nel punto di ascissa $x\approx1.945$

Un ***errore assoluto*** del 1% sulla funzione porta ad un errore assoluto di circa 5% sulla soluzione.

>[!fail] Problema Mal Condizionato

<font color="CornflowerBlue">$f(x)=\displaystyle{\frac{x}{10}}-\frac{\sin(x)}{10},\quad x\in[-\pi,\pi]$</font>
<font color="red">$f(x)=\displaystyle{\frac{x}{10}}-\frac{\sin(x)}{10}+0.01,\quad x\in[-\pi,\pi]$</font>

```functionplot
---
title: 
xLabel: 
yLabel: 
bounds: [-4,4,-0.4,0.4]
disableZoom: false
grid: true
---
f(x)=(x/10)-(sin(x)/10)
g(x)=(x/10)-(sin(x)/10)+0.01
```

La funzione $f(x)$ si *annulla* nel punto di ascissa $x=0$
- La funzione $\tilde{f}(x)$ si annulla nel punto di ascissa $x\approx0.8538$

Un ***errore assoluto*** del 1% sulla funzione porta ad un errore assoluto di circa 85% sulla soluzione.

>[!hint] Conclusione
>Il calcolo di radici multiple di molteplicità è un ***problema numericamente molto difficile***.