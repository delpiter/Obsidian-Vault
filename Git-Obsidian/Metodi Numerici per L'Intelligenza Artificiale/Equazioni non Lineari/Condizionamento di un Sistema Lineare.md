>[!question] Come influiscono delle perturbazioni sugli elementi della matrice $A$ e sugli elementi del termine noto $b$?

> Sia $\| \ \|$ una qualunque [[Norma]] naturale, sia $A\in\mathbb{R}^{n\times m}$ matrice a [[2 - Teorema del Rango|rango]] massimo

- Sia $\delta A$ una matrice di perturbazione e $\delta b$ un vettore di perturbazione

Sia $x$ la soluzione del sistema.

##### Caso 1
>[!abstract] Perturbazione sul Termine Noto
>$$A(x+\delta x)=b+\delta b$$

Vogliamo stimare $\delta x$ in funzione di $\delta b$
$$
\begin{array}
\ Ax+A\delta x=b+\delta b \\
Ax-b+A\delta x=\delta b
\end{array}
$$
- Ma per ipotesi $Ax=b$, quindi $Ax-b=0$

$$
A\delta x=\delta b \implies \delta x=A^{-1}\delta b
$$
> Passando alle norme.

(1) 
$$
\| \delta x \|\leq \| A^{-1} \|\cdot\| \delta b \|   
$$
Inoltre: $\| b \|=\| Ax \|\leq \| A \|\| x \|\implies \frac{1}{\| x \|}\leq \| A\| \frac{1}{\| b \|}$  (2)

Moltiplicando membro a membro (1) e (2) si ha:
$$
\displaystyle{\frac{\| \delta x\| }{\| x \| }}\leq \| A^{-1} \|\| A \|  \displaystyle{\frac{\| \delta b\| }{\| b \| }}
$$
>[!hint] Condizionamento
>$K(A)=\| A^{-1} \|\| A \|$ rappresenta [[Condizionamento#Quantificare il Condizionamento|indice di condizionamento]] del problema del calcolo della ***soluzione di un sistema lineare***.

##### Caso 2
>[!abstract] Perturbazione sulla matrice e termine noto.
>$$(A+\delta A)(x+\delta x)=(b+\delta b)$$

Sotto l'ipotesi che $\| A^{-1} \|\| \delta A \|<1$, da cui si può dimostrare che [[Sistemi Lineari#Matrici Singolari|non è singolare]], vale la seguente relazione:
$$
\displaystyle{\frac{\| \delta x \| }{\| x \| }}\leq \| A^{-1} \|\| A \| \displaystyle{\frac{\displaystyle{\frac{\| \delta A \| }{\| A \| }+\frac{\| \delta b \| }{\| b \| }}}{1-\| A^{-1} \|\| A \|\frac{\| \delta A \| }{\| A \| }  }}  
$$
>[!hint] Osservazione
>L'***indice di condizionamento*** della [[5 - Matrici di Applicazioni Lineari#Matrice Identità|matrice identità]] è uguale a $1$, $K(I)=1$
>L'***indice di condizionamento*** di una matrice qualunque è in generale $\geq 1$
>>[!abstract] Nota Bene
>>Se $A$ è [[1 - Introduzione Isometrie#Matrice Ortogonale|ortogonale]] allora: 
>>$$K_{2}(A)=\| A \|_{2}\| A^{-1} \|_{2}=1  $$
>>>[!done] Se $A$ è **ortogonale** il problema è [[Condizionamento#Condizionamento di un Problema|ben condizionato]].

> In generale:

- $K(A)$ "***piccollo***" (ordine $10^p, p=0,1,2,3$) il problema è *ben condizionato*.
- $K(A)$ "***grande***" (ordine $>10^3$) il problema è *mal condizionato*.

###### Esempi
>[!missing] Matrice di Vandermonde
>Dato un vettore $x=(x_{0},x_{1},\dots,x_{n})$ la ***Matrice di Vandermonde*** è una matrice di dimensione $(n+1)\times(n+1)$ in cui il generico elemento $a_{ij}$ è dato da:
>$$a_{ij}=x_{i}^j, \quad i,j=0,\dots,n$$

$$
A_{v}=\begin{bmatrix}
1 & x_{0} & x_{0}^2 & \dots & x_{0}^n \\
1 & x_{1} & x_{1}^2 & \dots & x_{1}^n \\
\vdots & \vdots & \vdots & \ddots  & \vdots\\
1 & x_{n} & x_{n}^2 & \dots & x_{n}^n
\end{bmatrix}
$$
>[!fail] Matrice di Hilbert
>$$h_{ij}=\frac{1}{i+j-1},\quad i,j=1,\dots,n$$

$$
H=\begin{bmatrix}
1 & \frac{1}{2} & \dots & \frac{1}{n} \\
\frac{1}{2} & \frac{1}{3} & \dots & \frac{1}{n+1} \\
\vdots & \vdots & \ddots & \vdots \\
\frac{1}{n} & \frac{1}{n+1} & \dots & \frac{1}{2n-1}
\end{bmatrix}
$$
> Indice di condizionamento di $H$ di ordine $4$ è $K(H)=1.55\times 10^4$