> Un sistema di equazioni non lineari può essere scritto nella forma:

$$
\begin{cases}
f_{1}(x_{1},x_{2},\dots,x_{n})=0 \\
f_{2}(x_{1},x_{2},\dots,x_{n})=0 \\
f_{3}(x_{1},x_{2},\dots,x_{n})=0 \\
\dots \\
f_{n}(x_{1},x_{2},\dots,x_{n})=0
\end{cases}
$$
Con $f_{i}:\mathbb{R}^n\to\mathbb{R}$, $i=1,\dots,n$ funzioni non lineari ***continue e differenziabili***.

>[!abstract] Consideriamo la funzione $F:\mathbb{R}^n\to \mathbb{R}^n$, funzione a valori vettoriali

$$
X=\begin{bmatrix}
x_{1} \\
x_{2} \\
\dots \\
x_{n}
\end{bmatrix}\in\mathbb{R}^n\to F(X)=\begin{bmatrix}
f_{1}(x_{1},x_{2},\dots,x_{n}) \\
f_{2}(x_{1},x_{2},\dots,x_{n}) \\
\dots \\
f_{n}(x_{1},x_{2},\dots,x_{n})
\end{bmatrix}
$$

>[!quote] Calcolare la soluzione del sistema
>Calcolare il vettore $\alpha=[\alpha_{1},\alpha_{2},\dots,\alpha_{n}]^T\in\mathbb{R}^n$ che annulla le equazioni ***equivale*** a calcolare $\alpha=[\alpha_{1},\alpha_{2},\dots,\alpha_{n}]^T\in\mathbb{R}^n$ tale che $F(\alpha)=0$


>[!info] Gradiente
>Il [[../../Analisi/Funzioni a due Variabili/Calcolo Differenziale#Gradiente|gradiente]] di una funzione $f:\mathbb{R}^n\to\mathbb{R}$ differenziabile è dato da:
>$$\nabla f(X) = \begin{bmatrix}\displaystyle\frac{\partial f(X)}{\partial x_1} \\\displaystyle\frac{\partial f(X)}{\partial x_2} \\\vdots \\\displaystyle\frac{\partial f(X)}{\partial x_n}\end{bmatrix}$$

### Matrice Jacobiana
>[!definizione]
>La ***matrice Jacobiana*** di $F(X)$ è la matrice le cui *entrate* sono le **derivate parziali** di ciascuna funzione $f_{i}(x_{1},x_{2},x_{3},\dots,x_{n})$, $i=1,\dots,n$ rispetto a *ciascuna variabile* $j=1,\dots,n$.

$$
J(X) =
\begin{bmatrix}
\displaystyle\frac{\partial f_1(X)}{\partial x_1} & \displaystyle\frac{\partial f_1(X)}{\partial x_2} & \cdots & \displaystyle\frac{\partial f_1(X)}{\partial x_n} \\
\displaystyle\frac{\partial f_2(X)}{\partial x_1} & \displaystyle\frac{\partial f_2(X)}{\partial x_2} & \cdots & \displaystyle\frac{\partial f_2(X)}{\partial x_n} \\
\vdots & \vdots & \ddots & \vdots \\
\displaystyle\frac{\partial f_n(X)}{\partial x_1} & \displaystyle\frac{\partial f_n(X)}{\partial x_2} & \cdots & \displaystyle\frac{\partial f_n(X)}{\partial x_n}
\end{bmatrix}
$$
Che può essere riscritto come:
$$
J(X) =
\begin{bmatrix}
\displaystyle\frac{\partial F(X)}{\partial x_1} & \displaystyle\frac{\partial F(X)}{\partial x_2} & \cdots & \displaystyle\frac{\partial F(X)}{\partial x_n}
\end{bmatrix}
$$
- *Dove*
$$
\frac{\partial F(X)}{\partial x_i} =
\begin{bmatrix}
\displaystyle\frac{\partial f_1(X)}{\partial x_i} \\
\displaystyle\frac{\partial f_2(X)}{\partial x_i} \\
\vdots \\
\displaystyle\frac{\partial f_n(X)}{\partial x_i}
\end{bmatrix}
$$
> Poiché

$$
\nabla F(X)=
\begin{bmatrix}
\displaystyle\frac{\partial F(X)}{\partial x_1} \\
\displaystyle\frac{\partial F(X)}{\partial x_2} \\
\vdots \\
\displaystyle\frac{\partial F(X)}{\partial x_n}
\end{bmatrix}
$$
Si ha quindi che $\nabla F(X)=J^T(X)$

## Metodo di Newton Raphson
---
> Analizziamo il caso $n=2$

Dato:
$$
F(X)=F(x_{1},x_{2})=\begin{bmatrix}
f_{1}(x_{1},x_{2}) \\
f_{2}(x_{1},x_{2})
\end{bmatrix}
$$
- Individuare il vettore $\alpha=[\alpha_{1},\alpha_{2}]^T\in\mathbb{R}^2$ tale che $F(\alpha)=\begin{bmatrix}f_{1}(\alpha_{1},\alpha_{2}) \\f_{2}(\alpha_{1},\alpha_{2})\end{bmatrix}=\begin{bmatrix}0\\0\end{bmatrix}$

>[!hint] Geometricamente
>Equivale ad individuare un ***punto del piano*** in cui entrambe le funzioni si *annullino contemporaneamente*.

> Consideriamo il polinomio di Taylor di grado $1$ bivariato centrato in un intorno del punto $X_{k}=\left[x^{(k)}_{1},x^{(k)}_{2}\right]^T\in\mathbb{R}^2$ (l'iterato $k$-*esimo*) per entrambe le funzioni $f_{1},f_{2}$

Tali polinomi rappresentano il ***piano che meglio approssima ciascuna delle funzioni*** bivariate.
$$
x_3 = P_1(x_1, x_2) = f_1\left(x_1^{(k)}, x_2^{(k)}\right) + \frac{\partial f_1}{\partial x_1}\left(x_1^{(k)}, x_2^{(k)}\right)(x_1 - x_1^{(k)}) + \frac{\partial f_1}{\partial x_2}\left(x_1^{(k)}, x_2^{(k)}\right)(x_2 - x_2^{(k)})
$$
$$
x_3 = Q_1(x_1, x_2) = f_2\left(x_1^{(k)}, x_2^{(k)}\right) + \frac{\partial f_2}{\partial x_1}\left(x_1^{(k)}, x_2^{(k)}\right)(x_1 - x_1^{(k)}) + \frac{\partial f_2}{\partial x_2}\left(x_1^{(k)}, x_2^{(k)}\right)(x_2 - x_2^{(k)})
$$

>[!abstract] Obbiettivo
>Il nostro obbiettivo è di individuare un punto del piano $X_{k+1}=\left[x_{1}^{k+1},x_{2}^{k+1}\right]^T$ in cui $F(X_{k+1})=0$.


$$
\begin{cases}
\displaystyle 0 = f_1\left(x_1^{(k)}, x_2^{(k)}\right) + \frac{\partial f_1}{\partial x_1}\left(x_1^{(k)}, x_2^{(k)}\right)(x_1 - x_1^{(k)}) + \frac{\partial f_1}{\partial x_2}\left(x_1^{(k)}, x_2^{(k)}\right)(x_2 - x_2^{(k)}) \\
\displaystyle 0 = f_2\left(x_1^{(k)}, x_2^{(k)}\right) + \frac{\partial f_2}{\partial x_1}\left(x_1^{(k)}, x_2^{(k)}\right)(x_1 - x_1^{(k)}) + \frac{\partial f_2}{\partial x_2}\left(x_1^{(k)}, x_2^{(k)}\right)(x_2 - x_2^{(k)})
\end{cases}
$$

^263baf

- Questo sistema di equazioni lineari rappresenta l'intersezione di due piani tangenti alle due superfici in $X_{k}=\left[x^{(k)}_{1},x^{(k)}_{2}\right]^T$ con il piano $x_{3}=0$

>[!hint] Geometricamente
>Significa trovare il punto sulla ***retta  di intersezione*** dei due piani tangenti in cui si ha $x_{3}=0$

Indicato con:
$$
J(X_k) = 
\begin{bmatrix}
\displaystyle\frac{\partial f_1}{\partial x_1}\left(x_1^{(k)}, x_2^{(k)}\right) & \displaystyle\frac{\partial f_1}{\partial x_2}\left(x_1^{(k)}, x_2^{(k)}\right) \\
\displaystyle\frac{\partial f_2}{\partial x_1}\left(x_1^{(k)}, x_2^{(k)}\right) & \displaystyle\frac{\partial f_2}{\partial x_2}\left(x_1^{(k)}, x_2^{(k)}\right)
\end{bmatrix}
$$

Lo Jacobiano di $F(X)$ calcolato in $X_{k}$

- $F(X_{k})=\left[ f_{1}(x_{1}^{(k)}),f_{2}(x_{2}^{(k)}) \right]^T$
- $X-X_{k}=\left[ x_{1}-x_{1}^{(k)},x_{2}-x_{2}^{(k)} \right]^T$

Il [[#^263baf|sistema]] si può esprimere in forma matriciale come
$$
\begin{array}
\ 0=F(X_{k})+J(X_{k})(X-X_{k}) \\
J(X_{k})(X-X_{k})=-F(X_{k}) \\
\end{array}
$$
> Sotto l'ipotesi che $\det J(X_{k})\neq 0$ si ricava:

$$
\cancel{ J^{-1}(X_{k})J(X_{k}) }(X-X_{k})=-J^{-1}(X_{k})F(X_{k})
$$
- E si determina il procedimento iterativo:

$$X_{k+1}-X_{k}=-J^{-1}(X_{k})F(X_{k})$$

>[!hint] Osservazione
>Possiamo notare che $-J^{-1}(X_{k})F(X_{k})$ è la soluzione del sistema lineare
>$$J(X_{k})s_{k}=-F(X_{k})$$

*Quindi*
- $X_{k+1}=X_{k}+s_{k}$

### Pseudocodice
>L'algoritmo si può schematizzare come:

- Dato $X_{0}\in\mathbb{R}^n$ ed ,$F$ per ogni iterazione $k$
```pseudo
	\begin{algorithm}
	\caption{Newton-Raphson}
	\begin{algorithmic}
\State $ \text{Valutare } J(X_{k-1})$
\State $ \text{Risolvere il sistema lineare } J(X_{k})s_{k}=-F(X_{k})$
\State $\text{Porre }X_k=X_{k-1}+s_{k-1}$
	\end{algorithmic}
	\end{algorithm}
```

>[!help] Convergenza
>È un metodo a [[Ordine di Convergenza#Convergenza Locale e Globale|convergenza locale]] e [[Ordine di Convergenza#Ordini|ordine di convergenza]] *quadratico*.
#### Esempio
>[!example] Esempio 1
>Calcolare il punto di intersezione tra il cerchio di coordinate $x^2_{1}+x^2_{2}-9$ e la retta $x_{1}+x_{2}=3$

Si tratta di risolvere il sistema
$$
\begin{cases}
f_{1}(x_{1},x_{2})=x^2_{1}+x^2_{2}-9=0\\
f_{2}(x_{1},x_{2})=x_{1}+x_{2}-3 =0
\end{cases}
$$
$$
F(X)=F(x_{1},x_{2})=\begin{bmatrix}
f_{1}(x_{1},x_{2}) \\
f_{2}(x_{1},x_{2})
\end{bmatrix}=\begin{bmatrix}
x_{1}^2+x_{2}^2-9 \\
x_{1}+x_{2}-3
\end{bmatrix}
$$
Calcoliamo la ***Jacobiana***:
$$
J(X)=\begin{bmatrix}
2x_{1} & 2x_{2} \\
1 & 1
\end{bmatrix}
$$

### Varianti del Metodo di Newton-Raphson
> Alcune varianti al metodo possono *migliorarne l'efficienza*.

>[!caution] Metodo delle Corde
>Si utilizza lo stesso *Jacobiano* $J(X_{0})$ o una sua approssimazione $A(X_{0})$ per tutte le iterazioni $k$.
>Si potrebbe quindi [[../Equazioni Lineari/Risoluzione di Sistemi Lineari#Fattorizzazione|fattorizzare]] $J(X_{0})=LU$ e utilizzare i medesimi $L$ e $U$ ***per ogni iterazione***.

>[!abstract] Metodo di Shamanskii
>Si valuta lo *Jacobiano* ogni $m$ iterazioni e quindi lo si utilizza per le $m$ iterazioni successive.
>$$J_{k+i}=J_{i}, \quad i=1,\dots,m$$
>Giunti al calcolo di $x_{k+m+1}$ si rivaluta lo *Jacobiano*.

### Iterato Iniziale
>[!question] Come trovo l'iterato iniziale?

Per trovare l'iterato iniziale si utilizza un ***approccio grafico***

L'approccio grafico offre un modo intuitivo per *visualizzare queste soluzioni*.

> Considerando le funzioni $f_{1}(x_{1},x_{2})$ e $f_{2}(x_{1},x_{2})$ come superfici nello spazio tridimensionale:

$$x_{3}=f_{1}(x_{1},x_{2}),\quad x_{3}=f_{2}(x_{1},x_{2})$$
Le soluzioni corrispondono ai punti in cui entrambe le superfici assumono il valore $x_{3}=0$.

>[!help] Curve di Livello
>Le [[../../Analisi/Funzioni a due Variabili/Funzioni di due Variabili Reali#Curva di Livello|curve di livello]] a quota zero di queste superfici sono date da:
>- $f_{1}(x_{1},x_{2})=0$
>- $f_{2}(x_{1},x_{2})=0$

Queste *curve* sono tracciate nel piano $x_{1}x_{2}$e descrivono tutti i punti $(x_{1},x_{2})$ dove ciascuna superficie "tocca"  il piano orizzontale $x_{3}=0$.
- I punti $x_{1}x_{2}$ che si trovano ***sull'intersezione*** di queste due curve di livello sono esattamente i punti in cui sia $f_{1}$ che $f_{2}$ sono *uguali a zero*.

>[!hint] Possiamo esaminare il grafico e stimare uno di questi punti

#### Esempio
$$
\begin{cases}
f_{1}(x_{1},x_{2})=x^2_{1}+x^2_{2}-4=0\\
f_{2}(x_{1},x_{2})=x^2_{1}-x^2_{2}-1=0
\end{cases}
$$

![[attachements/FirstIterateGraphicalMethood.png|500]]


![[attachements/FirstItearte.png|500]]

### Metodo di Newton-Rapshon per il calcolo del Minimo
>[[../../Analisi/Funzioni a due Variabili/Punti Critici|Masismi e Minimi di una funzione a due variabili]].

>[!info]
>Data $f:\mathbb{R}^n\mapsto \mathbb{R},\quad f\in C^2$ (*differenziabile due volte con continuità*), trovare $X^*\in\mathbb{R}^n$ tale che $X^*=\arg\min\limits_{X\in\mathbb{R}^2}f(x)$.

I punti di stazionarietà locale $X^*$ sono soluzione del seguente *sistema non lineare*:

$$
\nabla f(X)=
\begin{bmatrix}
\displaystyle\frac{\partial f(X)}{\partial x_1} \\
\displaystyle\frac{\partial f(X)}{\partial x_2} \\
\vdots \\
\displaystyle\frac{\partial f(X)}{\partial x_n}
\end{bmatrix}=\begin{bmatrix}
0 \\
0 \\
\dots \\
0
\end{bmatrix}
$$
Con $X=\begin{bmatrix}x_{1}\\x_{2}\\\dots\\x_{n}\end{bmatrix}\in\mathbb{R}^n$

Per verificare se tale punto è un massimo, minimo o sella occorrerà esaminare la ***matrice*** [[../../Analisi/Funzioni a due Variabili/Differenziabilità#Matrice Hessiana|Hessiana]] $H(X)$.

$$
H(X) =
\begin{bmatrix}
\displaystyle\frac{\partial^2 f(X)}{\partial^2 x_1} & \displaystyle\frac{\partial^2 f(X)}{\partial x_{1}\partial x_2} & \cdots & \displaystyle\frac{\partial^2 f(X)}{\partial x_{1}\partial x_n} \\
\displaystyle\frac{\partial^2 f(X)}{\partial x_{2}\partial x_1} & \displaystyle\frac{\partial^2 f(X)}{\partial^2 x_2} & \cdots & \displaystyle\frac{\partial^2 f(X)}{\partial x_{2}\partial x_n} \\
\vdots & \vdots & \ddots & \vdots \\
\displaystyle\frac{\partial^2 f(X)}{\partial x_{n}\partial x_1} & \displaystyle\frac{\partial^2 f(X)}{\partial x_{n}\partial x_2} & \cdots & \displaystyle\frac{\partial^2 f(X)}{\partial^2 x_n}
\end{bmatrix}
$$

Consideriamo il ***polinomio di Taylor*** di grado 1 bivariato centrato in un intorno del punto $X_{k}$
- $P_1(x_1, x_2)$

$$
x_3 = 
\displaystyle\frac{\partial f\left(x_1^{(k)}, x_2^{(k)}\right)}{\partial x_1} 
+ \displaystyle\frac{\partial^2 f\left(x_1^{(k)}, x_2^{(k)}\right)}{\partial x_1^2}(x_1 - x_1^{(k)}) 
+ \displaystyle\frac{\partial^2 f\left(x_1^{(k)}, x_2^{(k)}\right)}{\partial x_1 \partial x_2}(x_2 - x_2^{(k)})
$$

- $Q_1(x_1, x_2)$

$$
x_3 = 
\displaystyle\frac{\partial f\left(x_1^{(k)}, x_2^{(k)}\right)}{\partial x_2} 
+ \displaystyle\frac{\partial^2 f\left(x_1^{(k)}, x_2^{(k)}\right)}{\partial x_2 \partial x_1}(x_1 - x_1^{(k)}) 
+ \displaystyle\frac{\partial^2 f\left(x_1^{(k)}, x_2^{(k)}\right)}{\partial x_2^2}(x_2 - x_2^{(k)})
$$


> Tali polinomi rappresentano il piano che meglio approssima ciascuna delle due componenti del gradiente in un intorno del punto $X_{k}$

>[!hint] Poiché $\nabla f$ non è lineare
>Usiamo l'**approssimazione** di ciascuna delle due componenti del gradiente in un intorno di $X_{k}$, e imponiamo che i *piani tangenti* da essi rappresentati si annullino.

$$
\begin{cases}
x_{3}=\displaystyle\frac{\partial f\left(x_1^{(k)}, x_2^{(k)}\right)}{\partial x_1} 
+ \displaystyle\frac{\partial^2 f\left(x_1^{(k)}, x_2^{(k)}\right)}{\partial x_1^2}(x_1 - x_1^{(k)}) 
+ \displaystyle\frac{\partial^2 f\left(x_1^{(k)}, x_2^{(k)}\right)}{\partial x_1 \partial x_2}(x_2 - x_2^{(k)}) \\
x_3 = \displaystyle\frac{\partial f\left(x_1^{(k)}, x_2^{(k)}\right)}{\partial x_2} 
+ \displaystyle\frac{\partial^2 f\left(x_1^{(k)}, x_2^{(k)}\right)}{\partial x_2 \partial x_1}(x_1 - x_1^{(k)}) 
+ \displaystyle\frac{\partial^2 f\left(x_1^{(k)}, x_2^{(k)}\right)}{\partial x_2^2}(x_2 - x_2^{(k)}) \\
x_{3}=0
\end{cases}
$$

Il sistema riscritto in termini matriciali diventa:
$$
0=\nabla f(X_{k})+H(X_{k})(X-X_{k})
$$

Sotto l'ipotesi che $\det H(X_{k})\neq0$ si ricava:
$$
X-X_{k}=-H^{-1}(X_{k})\nabla f(X_{k})
$$

> E si determina il procedimento iterativo:

$$
H(X_{k})s_{k}=-\nabla f(X_{k})
$$
*Quindi*
- $X_{k+1}=X_{k}+s_{k}$

>[!abstract] L'algoritmo diventa:

```pseudo
	\begin{algorithm}
	\caption{Newton-Raphson Min Point}
	\begin{algorithmic}
\State $ \text{Valutare } H(X_{k-1})$
\State $ \text{Risolvere il sistema lineare } H(X_{k})s_{k}=-\nabla f(X_{k})$
\State $\text{Porre }X_k=X_{k-1}+s_{k-1}$
	\end{algorithmic}
	\end{algorithm}
```