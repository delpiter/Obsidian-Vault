## Curve Interpolanti
---
>Dati i punti del piano $P_{i}, i=0,\dots,n$, dove possiamo pensare che le coordinate del punto $P_{i}$ possano essere considerate come [[Curve Parametriche|valutazione di due funzioni parametriche]].

$$
p_{i} \equiv \begin{pmatrix}
x=x(t_{i}) \\
y=y(t_{i})
\end{pmatrix}
$$
>[!todo] Curve Interpolanti 
>Vogliamo costruire la curva [[../../Metodi Numerici per L'Intelligenza Artificiale/Interpolazione/Interpolazione Polinomiale|interpolante]] i punti $P_{i}$: $C(t_{i})=P_{i}$

>[!hint] Osservazione
>Questo equivale a risolvere due problemi di interpolazione, uno per la funzione $x$ e uno per la funzione $y$.

Scegliamo una base di funzioni $\varphi$ per lo spazio in cui vogliamo costruire le ***funzioni interpolanti***.
- Interpoliamo quindi le coppie $(t_{i},x_{i})$ e $(t_{i},y_{i})$:

$$
\begin{array}
\ \displaystyle X_{n}(t)=\sum_{j=0}^{n}\alpha_{j}\varphi_{j}(t)\quad t.c. \ X_{n}(t_{i})=x_{i} \\
\displaystyle Y_{n}(t)=\sum_{j=0}^{n}\beta_{j}\varphi_{j}(t)\quad t.c. \ Y_{n}(t_{i})=y_{i}
\end{array}
$$
### Interpolazione di Hermite
>[!question] Problema
>Dati $n+1$ punti da *interpolare* $p_{i}$, $i=0,\dots,n$, costruiamo $n$ segmenti di curve costruite a partire da polinomi cubici, tali che nei ***punti di giunzione*** abbiano lo stesso valore e la stessa [[../../Analisi/Calcolo Differenziale/Derivate|derivata]] prima.

> ***Esempio***:

Assegnati agli estremi dell'intervallo $[0,1]$ i valori $f_{0}$ e $f_{1}$ della *funzione* e i valori $d_{0}$ e $d_{1}$ della **derivata prima**.

$P_{3}=a_{0}+a_{1}t+a_{2}t^{2}+a_{3}t^{3}$

>[!done] Il polinomio cubico che interpola questi dati si calcola imponendo le condizioni di interpolazione

$$
\begin{cases}
a_{0}=f_{0} \\
a_{0}+a_{1}+a_{2}+a_{3} = f_{1} \\
a_{1}=d_{0} \\
a_{1}+2a_{2}+3a_{3}=d_{1}
\end{cases}
$$

>[!quote] Hermite
>***Hermite*** dimostra che il polinomio $P_{3}$ che interpola questi dati si può esprimere come:
>$$P_{3}=f_{0}\cdot\phi_{0}(t)+d_{0}\cdot\phi_{1}(t)+f_{1}\cdot\psi_{0}(t)+d_{1}\cdot\psi_{1}(t)$$
>- *Dove*
> $$\begin{array}\ \phi_{0}(t)=2t^{3}-3t^{2}+1 \\\phi_{1}(t)=t^{3}-2t^{2}+t \\\psi_{0}(t)=-2t^{3}+3t^{2} \\\psi_{1}(t)=t^{3}-t^{2}\end{array}$$
> Con $0\leq t\leq 1$

#### Dimostrazione
> Il sistema lineare

$$
\begin{cases}
a_{0}=f_{0} \\
a_{0}+a_{1}+a_{2}+a_{3} = f_{1} \\
a_{1}=d_{0} \\
a_{1}+2a_{2}+3a_{3}=d_{1}
\end{cases}
$$
>[!tip] In termini matriciali si può scrivere come:

$$
\begin{bmatrix}
1 & 0 & 0 & 0 \\
1 & 1 & 1 & 1 \\
0 & 1 & 0 & 0  \\
0 & 1 & 2 & 3
\end{bmatrix}\begin{bmatrix}
a_{0} \\
a_{1} \\
a_{2} \\
a_{3}
\end{bmatrix}=
\begin{bmatrix}
f_{0} \\
f_{1} \\
d_{0} \\
d_{1}
\end{bmatrix}
$$
Da cui si ricava la ***soluzione***:
$$
\begin{bmatrix}
a_{0} \\
a_{1} \\
a_{2} \\
a_{3}
\end{bmatrix}=\begin{bmatrix}
1 & 0 & 0 & 0 \\
1 & 1 & 1 & 1 \\
0 & 1 & 0 & 0  \\
0 & 1 & 2 & 3
\end{bmatrix}^{-1}
\begin{bmatrix}
f_{0} \\
f_{1} \\
d_{0} \\
d_{1}
\end{bmatrix}
$$
- Poiché si ha che:
$$
\begin{bmatrix}
1 & 0 & 0 & 0 \\
1 & 1 & 1 & 1 \\
0 & 1 & 0 & 0  \\
0 & 1 & 2 & 3
\end{bmatrix}^{-1}=\begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & 0 & 1 & 0 \\
-3 & 3 & -2 & - 1 \\
2 & -2 & 1 & 1
\end{bmatrix}
$$

*Risulta che*:
$$
\begin{bmatrix}
a_{0} \\
a_{1} \\
a_{2} \\
a_{3}
\end{bmatrix}=\begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & 0 & 1 & 0 \\
-3 & 3 & -2 & - 1 \\
2 & -2 & 1 & 1
\end{bmatrix}
\begin{bmatrix}
f_{0} \\
f_{1} \\
d_{0} \\
d_{1}
\end{bmatrix}
$$
Sapendo che:
$$
P_{3}=a_{0}+a_{1}t+a_{2}t^{2}+a_{3}t^{3}=[1\ t\ \ t^{2} \ t^{3}]\begin{bmatrix}
a_{0} \\
a_{1} \\
a_{2} \\
a_{3}
\end{bmatrix}
$$
Sostituiamo il **risultato appena ottenuto**:
$$
P_{3}(t)=\begin{bmatrix}
1 & t & t^{2} & t^{3}
\end{bmatrix}\begin{bmatrix}
1 & 0 & 0 & 0 \\
0 & 0 & 1 & 0 \\
-3 & 3 & -2 & - 1 \\
2 & -2 & 1 & 1
\end{bmatrix}
\begin{bmatrix}
f_{0} \\
f_{1} \\
d_{0} \\
d_{1}
\end{bmatrix}=
$$
$$
=\begin{bmatrix}
1-3t^{2+2t^{3}} & 3t^{2-2t^{3}} & t-2t^{2}+t^{3} & -t^{2+t^{3}}
\end{bmatrix}\begin{bmatrix}
f_{0} \\
f_{1} \\
d_{0} \\
d_{1}
\end{bmatrix}
$$
> Ponendo:

$$
\begin{array}\ \phi_{0}(t)=2t^{3}-3t^{2}+1 \\\phi_{1}(t)=t^{3}-2t^{2}+t \\\psi_{0}(t)=-2t^{3}+3t^{2} \\\psi_{1}(t)=t^{3}-t^{2}\end{array}
$$
>[!done] Si ha che $P_{3}=f_{0}\cdot\phi_{0}(t)+d_{0}\cdot\phi_{1}(t)+f_{1}\cdot\psi_{0}(t)+d_{1}\cdot\psi_{1}(t)$

#### Polinomio Interpolatore di Hermite
> Noti i valori $(t_{i}, f_{i}, d_{i})$ con $i=0,\dots,n$

>[!caution] Polinomio Interpolatore
>Il ***polinomio interpolatore di Hermite*** $P_{H}(t)$ tale che $P_{H}(t_{i})=f_{i}$ e $P'_{H}(t_{i})=d_{i}$ si esprime come:
>$$P_{H}(t)=\sum_{i=0}^{n}\Phi_{i}(t)$$

***Dove***:
$$
\Phi_{i}(t)=f_{i}\cdot\phi_{0,i}(t)+d_{i}\cdot\phi_{1,i}(t)+f_{i+1}\cdot\psi_{0,i}(t)+d_{i+1}\cdot\psi_{1,i}(t)
$$
> Si può verificare che il polinomio espresso in questa forma, in ogni sotto intervallo coincide con un polinomio cubico che soddisfa le seguenti proprietà:

- $\Phi_{i}(t_{i})=\Phi_{i-1}(t_{i})=f_{i}$
- $\Phi'_{i}(t_{i})=\Phi'_{i-1}(t_{i})=d_{i}$

>[!quote] A parole
>$P_{H}(t)$ è formato da $n$ segmenti di polinomi cubici che nei punti di giunzione si ***raccordano in valore e derivata prima***.

Poiché le 4 funzioni $\phi_{0,i}(t),\phi_{1,i}(t),\psi_{0,i}(t),\psi_{1,i}(t)$ sono definite analiticamente nell'intervallo $[0,1]$ è necessario applicare una trasformazione affine che mappi il punto $t\in [t_{i},t_{i+1}]$ in $t\in[0,1]$.

- Consideriamo la trasformazione affine $t \to \hat{t}\in[0,1]$
$$
\hat{t}=\displaystyle{\frac{t-t_{i}}{t_{i+1}-t_{i}}}
$$

>[!warning] Attenzione!

$\phi_{0,i}(t),\psi_{0,i}(t)$ sono invarianti per *trasformazioni affini*.
- $\phi_{0,i}(\hat{t})=\phi_{0,i}(t)\qquad \psi_{0,i}(\hat{t})=\psi_{0,i}(t)$

$\phi_{1,i}(t),\psi_{1,i}(t)$ ***non*** sono invarianti per *trasformazioni affini*.
- $\phi_{1,i}(t)=\phi_{1,i}(\hat{t})(t_{i+1}-t_{i})\qquad\psi_{1,i}(t)=\psi_{1,i}(\hat{t})(t_{i+1}-t_{i})$

##### Valutazione del Polinomio
>[!check] Valutazione
>Per la ***valutazione del polinomio*** $P_{H}(t)$ , per ogni valore di $t$, bisogna fare la seguente osservazione:

Fissato un valore di $t\in[0,1]$:
- Bisogna valutare ognuna delle $\Phi_{i}$ in $t$ e poi fare la somma.

```pseudo
	\begin{algorithm}
	\caption{Evaluation}
	\begin{algorithmic}
	\For{$ t \in [0,1] $}
	\State $ \text{Identify the range } [t_{\overline{i}}, t_{\overline{i}+1}]$
	\State $ \text{Map the value of } t \text{ in the range } [0,1] $
	\State $ \text{Evaluate the point}$
	\State $ P=f_{\overline{i}}\cdot\phi_{0,\overline{i}}(t)+d_{\overline{i}}\cdot\phi_{1,\overline{i}}(t)(t_{\overline{i}+1}-t_{\overline{i}}) +f_{\overline{i}+1}\cdot\psi_{0,\overline{i}}(t)+d_{\overline{i}+1}\cdot\psi_{1,\overline{i}}(t)(t_{\overline{i}+1}-t_{\overline{i}})  $
	\EndFor
	\end{algorithmic}
	\end{algorithm}
```

### Curve Interpolanti di Hermite
>[!info]
>Nel caso di curve, dati $n+1$ punti da interpolare, in cui sono noti i *valori delle coordinate* ($p_{i}$) e i *valori delle derivate nei punti* ($d_{i}$).
>La ***curva cubica di Hermite*** si esprime come:

$$
C(t)=\begin{cases}
C_{x}(t)=\displaystyle\sum_{i=0}^{n-1}\Phi_{i}^{X}(t) \\
C_{y}(t)=\displaystyle\sum_{i=0}^{n-1}\Phi_{i}^{Y}(t)
\end{cases}
$$
**Dove**:
- $\Phi_{i}^{X}(t)=x_{i}\cdot\phi_{0,i}(t)+d^{x}_{i}\cdot\phi_{1,i}(t)+x_{i+1}\cdot\psi_{0,i}(t)+d^{x}_{i+1}\cdot\psi_{1,i}(t)$
- $\Phi_{i}^{Y}(t)=y_{i}\cdot\phi_{0,i}(t)+d^{y}_{i}\cdot\phi_{1,i}(t)+y_{i+1}\cdot\psi_{0,i}(t)+d^{y}_{i+1}\cdot\psi_{1,i}(t)$

## Valutazione delle Derivate
---
> Ci sono due classi di metodi per la ***valutazione della derivata in un punto***.

### Metodi Numerici per il Calcolo delle Derivate
> Dati $n+1$ punti da interpolare, per ogni curva abbiamo un punto iniziale $p_{i}$ e uno filale $p_{i+1}$ con tangenti $d_{i}$ e $d_{i+1}$

>[[../../Analisi/Calcolo Differenziale/Derivate|!abstract]]
>$$d_{i}=\displaystyle{\frac{p_{i+1}-p_{i}}{t_{i+1}-t_{i}}}$$

>[!summary] Differenze Finite
>Media tra due ***rapporti incrementali successivi***.
>$$d_{i}=\frac{1}{2}\left( \displaystyle{\frac{p_{i+1}-p_{i}}{t_{i+1}-t_{i}}}+\displaystyle{\frac{p_{i}-p_{i-1}}{t_{i}-t_{i-1}}} \right)$$

>[!caution] Cardinal Spline
>$$d_{i}=(1-c)\displaystyle{\frac{p_{i+1}-p_{i-1}}{2(t_{i+1}-t_{i-1}})}$$
>Dove:
>- $c$ è un *parametro di tensione*, agisce sulla ***lunghezza della tangente***.
>	- $c=1$ Tangente lunga $0$.
>	- $c=0$ Spline di tipo *Catmull Rom*.

>[!failure] Spline Catmull Rom
>$$d_{i}=\displaystyle{\frac{p_{i+1}-p_{i-1}}{2(t_{i+1}-t_{i-1}})}$$
>La tangente nel punto $p_{i}$ è parallela al segmento che congiunge il *punto precedente* e il *punto successivo*.

>[!todo] Spline di Kochanek-Bartles
>Note come `TBC` ***splines***, sono *spline cubiche di Hermite* in cui sono definiti tre parametri:
>- `T`=*tensione*, `B`=*bias*, `C`=*continuity*.

$$
d_{i}=(1-T)(1+B)(1+C)\displaystyle{\frac{p_{i}-p_{i-1}}{2(t_{i}-t_{i-1})}}+(1-T)(1+B)(1+C)\displaystyle{\frac{p_{i+1}-p_{i}}{2(t_{i+1}-t_{i})}}
$$
- Il parametro `T` varia la **lunghezza del vettore tangente**.
- Il parametro `B` varia la **direzione del vettore**.
- Il parametro `C` varia la **continuità**.