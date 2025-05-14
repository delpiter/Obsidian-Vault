## Metodo QR
---
>Risoluzione di sistemi [[Sistemi Sovradeterminati|sovradeterminati]].

>[!info] ***QRLS***
> Una volta calcolata la fattorizzazione $QR$ di una matrice $A$ con le [[Risoluzione di Sistemi Lineari#Metodo di Householder|Trasformazioni Successive ortogonali di Householder]], poiché $Q$ è **ortogonale**, consideriamo:
>$$\|Q^T(Ax-b)\|_{2}^2=\|Q^TAx-Q^Tb\|_{2}^2=\|R_{1}x-Q^Tb\|_{2}^2$$
>- Ottenuto *premoltiplicando ambo i membri* di $A=QR$ per $Q^T$.

Posto $h=Q^Tb=\begin{bmatrix}\underbrace{ h_{1} }_{ n \text{ componenti} }\\ \underbrace{ h_{2} }_{ m-n \text{ componenti}}\end{bmatrix}$
si ha:
$$
\left\| 
\left( 
\underbrace{ \begin{bmatrix}
\ddots  & & R_1 \\
0 & \ddots &  \\
\dots & \dots & \dots \\
0 & 0 & 0 
\end{bmatrix}}_{n  } x-\begin{bmatrix}
h_1 \\
h_2
\end{bmatrix}\right) 
\right\|_2^2=\left\| 
\begin{matrix}
(R_1 x - h_1) \\
- h_2
\end{matrix} 
\right\|_2^2$$
$$
\arg\min_{x \in \mathbb{R}^n} \|Ax - b\|_2^2 
= \arg\min_{x \in \mathbb{R}^n} \left\{ \|R_1 x - h_1\|_2^2 + \|h_2\|_2^2 \right\}
= \arg\min_{x \in \mathbb{R}^n} \|R_1 x - h_1\|_2^2 + \|h_2\|_2^2.
$$

> Quindi il minimo sarà ottenuto per $x^*$ che risolve il sistema lineare $R_{1}x=h_{1}$

>[!tldr] Idea
>Il metodo $QR$ consiste nel calcolare i due fattori $Q$ e $R$ di $A$, nel valutare $h_{1}$ e risolvere il sistema lineare $R_{1}x=h_{1}$ con $R_{1}$ matrice triangolare superiore.
>Il valore del residuo assunto per questo valore di $x$ sarà dato da:
>$$\min_{x\in\mathbb{R}^n}\|Ax-b\|_{2}^2=\|h_{2}\|_{2}^2$$

>[!done] Vantaggi

1. Si lavora **sempre** solo sulla matrice $A$, senza passare da $A^TA$
2. La [[Risoluzione di Sistemi Lineari#Fattorizzazione $QR$|fattorizzazione]] $QR$ è *abbastanza stabile*.

## Decomposizione in Valori Singolari
---
> Data la matrice $A\in\mathbb{R}^{m\times n}$, la sua **decomposizione in valori singolari** è caratterizzata dal seguente *teorema*:

>[!check] Teorema
>Sia $A\in\mathbb{R}^{m\times n}$ a rango $k\leq\min(m,n)$, allora esistono due matrici ortogonali $U\in\mathbb{R}^{m\times n}$ e $V\in\mathbb{R}^{m\times n}$ tali che:
>$$U^TAV=\Sigma=diag(\sigma_{1},\sigma_{2},\dots,\sigma_{k},0,\dots,0)$$

I valori sulla diagonale di $\Sigma$ sono detti valori singolari di $A$ e soddisfano:
$$
\sigma_{1}\geq \sigma_{2}\geq\dots\geq\sigma_{k}\geq0
$$
- Se la matrice $A$ ha [[6 - Cambiamenti di Base#Rango di una Matrice|rango]] $k=n$ avremo $\sigma_{n}>0$
$$
\Sigma=\begin{bmatrix}
\sigma_{1} &  &  & 0\\
 & \sigma_{2}  \\
 &  & \ddots \\
 0 &  &  & \sigma_{n} \\
- & - & - & - \\
0 &  0 & \dots & 0 \\
\vdots &\vdots & \vdots & \vdots 
\end{bmatrix}
$$

- Se ha rango $k<n$ avremo che $\sigma_{k}>0$ e $\sigma_{k+1}=\sigma_{k+2}=\dots=\sigma_{n}=0$
$$
\Sigma=\begin{bmatrix} \sigma_{1} &  &  &  &  & 0\\ & \sigma_{2}  \\ &  & \ddots \\ &  &  & \sigma_{k} \\ &  &  &  & 0\\ 0&  &  &  &  & \ddots \\ - & - & - & -  & - & -\\ 0 &  0 & \dots & 0  & 0 & 0\\ \vdots &\vdots & \vdots &   \vdots & \vdots & \vdots \end{bmatrix}
$$ 
^110784


>[!info] Singolar Value Decomposition
>$U^TAV=\Sigma$ è detta ***decomposizione in valori singolari*** (***SVD***) di $A$ e può essere anche scritta come:
>$$A=U\Sigma V^T$$
>Le colonne di $U$ e $V$ sono dette, rispettivamente, *vettori singolari* **sinistri** e **destri** di $A$.

I valori singolari di una matrice hanno le *seguenti proprietà*:
- $\sigma_{i}$ sono sempre ***reali*** e $\geq 0$.
- $\sigma_{1}$ è il *massimo valore singolare* (indicato con $\sigma_{\max}$).
- Il $\sigma_{i}>0$ più *piccolo* è detto $\sigma_{\min}$.
- Il rapporto $\displaystyle\frac{\sigma_{\max}}{\sigma_{\min}}$ ci fornisce l'[[Condizionamento#Quantificare il Condizionamento|indice di condizionamento]] della *matrice* $A$.
- Il numero di valori singolari non nulli rappresenta il ***rango della matrice*** $A$.
- $\sigma_{i}(A)=\sqrt{ \lambda_{i}(A^TA) }\quad i=1,\dots,n$.

> Usando i valori singolari e i corrispondenti vettori singolari, si può ottenere la ***decomposizione spettrale*** di $A$ nella forma:

$$
A=\sum_{j=1}^n\sigma_{j}u_{j}v_{j}^T=\sigma_{1}u_{1}v_{1}^T+\sigma_{2}u_{2}v_{2}^T+\dots+\sigma_{n}u_{n}v_{n}^T
$$
#### Decomposizione
> Dobbiamo aggiungere una *condizione* sulla soluzione cercata perché essa risulti ***unica***.

>[!info] Consideriamo
>$$\|Ax-b\|_{2}^2=\|U^T(Ax-b)\|_{2}^2=\|U^TAVV^Tx-U^Tb\|_{2}^2=\|\Sigma V^Tx-U^Tb\|_{2}^2$$

Se $k\leq n$ è il rango di $A$:
$$
c=V^Tx,\qquad d=U^Tb=\begin{bmatrix}
u_{1}^Tb \\
u_{2}^Tb \\
\vdots \\
u_{n}^Tb \\
\vdots \\
u_{m}^Tb
\end{bmatrix}=\begin{bmatrix}
\underbrace{ d_{1} }_{ n } \\
\underbrace{ d_{2} }_{ m-n }
\end{bmatrix}
$$
Otteniamo
$$
\underset{ x\in\mathbb{R}^n }{ \arg\min }\|Ax-b\|_{2}^2=\underset{ c\in\mathbb{R}^n }{ \arg\min }\|\Sigma c-d\|_{2}^2=\underset{ c\in\mathbb{R}^n }{ \arg\min }\|\Sigma c-d_{1}\|_{2}^2+\|d_{2}\|_{2}^2
$$
dove $\Sigma=$ [[#^110784|Matrice]].

Per ***rendere minimo il residuo*** dobbiamo calcolare il valore di $c$ che annulla $\Sigma c-d_{i}$, cioè *risolvere*:
$$
\Sigma c=d_{i}
$$
- Si ha: $c_{i}=\displaystyle{\frac{d_{i}}{\sigma_{i}}},\quad i=1,\dots,k$

>[!help] Minima Norma
>Ora poniamo $c_{i}=0$ per $i=k+1,\dots,n$ che rappresenta una condizione aggiuntiva per ottenere fra le *infinite soluzioni*, quella di ***minima*** [[Norma]].

Ricaviamo ora
$$
x=Vc=\sum_{i=1}^kc_{i}v_{i}$$
- dove $v_{i}, i=1,\dots,n$ indicano le *colonne* della matrice $V$
Poiché $c_{i}=\displaystyle{\frac{d_{i}}{\sigma_{i}}}=\displaystyle{\frac{u_{i}^Tb}{\sigma_{i}}}$, con $u_{i}$ *colonne* della matrice $U$, otteniamo:
$$
x=\sum_{i=1}^k \displaystyle{\frac{u_{i}^Tb}{\sigma_{i}}}v_{i}
$$
>[!done] Che rappresenta la soluzione di minima norma del problema dei minimi quadrati

Il valore del residuo sarà:
$$
\min_{x\in\mathbb{R}^n}\|Ax-b\|_{2}^2=\|d_{2}\|_{2}^2
$$
## Approssimazione dei Minimi Quadrati di un insieme di dati Sperimentali
---
>[!info]
>Siano assegnate $m$ coppie di ***valori sperimentali*** $(x_{i},y_{i})$ con $i=1,\dots,m-1$ , (*in cui tutte le ascisse siano distinte tra loro*), che **descrivono** in modo discreto l’**andamento di un fenomeno** reale. Si vuole determinare il *polinomio di grado* $n$, $m>n$:
>$$P_{n}(x)=\sum_{j=0}^n\alpha_{j}x^j$$
>I cui coefficienti $\alpha_{j}$ si ottengono risolvendo ***nel senso dei minimi quadrati*** il sistema lineare sovradeterminato ottenuto dalle equazioni:
>$$P_{n}(x_{i})=y_{i}$$

Indichiamo:
- Con $\alpha$ il vettore di dimensione $n+1$ dei coefficienti della [[2 - Campi e Spazi Vettoriali#Combinazioni Lineari|combinazione lineare]]:
$$
\alpha=\begin{bmatrix}
\alpha_{0} \\
\vdots \\
\alpha_{n}
\end{bmatrix}
$$
- Con $y$ il vettore di dimensione $m$ delle *misure sperimentali*.
$$
y=\begin{bmatrix}
y_{0} \\
\vdots \\
y_{m-1}
\end{bmatrix}
$$
- Con $B$ la matrice $m\times(n+1)$ con rango $n+1$ data da:
$$
B=\begin{bmatrix}
x_{0}^0  & x_{0}^1 & \dots & x_{0}^n \\
x_{1}^0  & x_{1}^1 & \dots & x_{1}^n \\
\dots & \dots & \dots & \dots \\
x_{m}^0  & x_{m}^1 & \dots & x_{m}^n
\end{bmatrix}
$$
	- ([[Condizionamento di un Sistema Lineare#Caso 2|Matrice di Vandermonde]]).
	- In cui l'elemento di posto $(i,j)$ è dato da $b_{ij}=x_{i}^j$

>[!hint] Osservazione
>Individuare i coefficienti del polinomio $P_{n}(x)=\sum_{j=0}^n\alpha_{j}x^j$ in maniera tale che $P_{n}(x_{i})=y_{i}$, **equivale** a determinare la soluzione nel ***senso dei minimi quadrati del sistema lineare sovradeterminato*** $B\alpha=y$.

Che equivale a trovare il vettore dei coefficienti $\alpha$:
$$
\alpha^*=\underset{ \alpha\in\mathbb{R}^n }{ \arg\min }\|B\alpha-y\|_{2}^2
$$

