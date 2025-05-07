## Direzioni Coniugate
---
>[!definizione]
>Data un'ellisse ed una ***direzione*** $p^{(0)}$, tutti i punti medi delle corde parallele alla direzione *sono allineati* e formano una ***direzione*** $p^{(1)}$ che si dice ***coniugata*** alla direzione data.

![[Direction.png|600]]

Due direzioni $p^{(k)},p^{(k-1)}$ coniugate rispetto all'ellisse soddisfano la relazione:
$$<Ap^{(k)},p^{(k-1)}> = <p^{(k)},Ap^{(k-1)}> = 0$$
- Dove $A$ è la ***matrice dell'ellisse***.

## Metodo del Gradiente Coniugato
---
>[!tldr] Idea
>La scelta della direzione di discesa $p^{(k)}$ tiene conto anche della ***direzione di discesa dell'iterazione precedente***. 

Al generico passo $k$ partendo dal punto $x^{(k)}$, ottenuto muovendosi lungo la direzione $p^{(k-1)}$ e in cui è stato calcolato il residuo $r^{(k)}$ (*ortogonale* a $p^{(k-1)}$)
- Si sceglie la **nuova direzione di discesa** come quella *appartenente al piano* $\pi_{k}$ passante per $x^{(k)}$e individuato da $r^{(k)}$ e $p^{(k-1)}$.
 
>[!check] $p^{(k)}$
>$$p^{(k)}=-r^{(k)}+\gamma_{k}p^{(k-1)}\qquad k=1,2,\dots$$

Il parametro $\gamma$ sarà scelto in modo che la direzione $p^{(k)}$ ***punti verso il centro dell'ellisse***.

>[!quote] Cioè, deve soddisfare
>$$<Ap^{(k)},p^{(k-1)}> = <p^{(k)},Ap^{(k-1)}> =0$$

Sostituendo l'espressione di $p^{(k)}$ alla espressione precedente, si ottiene:
$$
\gamma_{k}=\displaystyle{\frac{<r^{(k)},Ap^{(k-1)}>}{<p^{(k-1)},Ap^{(k-1)}>}}
$$
Utilizzando tale valore si ottiene la nuova direzione $p^{(k)}$, e il nuovo punto $x^{(k)}$ viene calcolato come punto di minimo nella direzione $p^{(k)}$:
$$
x^{(k+1)}=x^{(k)}+\alpha^{(k)}p^{(k)}
$$
- Con
$$
\alpha^{(k)}=-\displaystyle{\frac{<r^{(k)},p^{(k)}>}{<Ap^{(k)},p^{(k)}>}}
$$

>[!abstract] Caso $n=2$

Nel caso $n=2$ il ***metodo del gradiente coniugato*** raggiunge la soluzione in $2$ passi.
- La direzione $p^{(1)}$, [[#Direzioni Coniugate|coniugata]] rispetto alla direzione $p^{(0)}$ **passa per il centro dell'ellissi** che corrisponde al *minimo della funzione*.

![[ConjugateGradient.png|600]]

### Semplificazioni
> Ora applichiamo alcune semplificazione che riducono la [[Complessità di Algoritmi|complessità computazionale]].

>[!caution] Residuo
>È possibile definire una formula ricorsiva che aggiorna il *residuo* $r^{(k)}$ usando una quantità ***necessaria per calcolare altre grandezze***.
>$$r^{(k)}=Ax^{(k)}-b=Ax^{(k-1)}-b+\alpha^{(k)}Ap^{(k)}\implies r^{(k)}=r^{(k-1)}+\alpha^{(k)}+Ap^{(k)}$$

> Semplificazione $2$.

>[!check] Teorema
>Nel ***metodo del gradiente coniugato*** le direzioni di discesa $p^{(k)}$ con $k=0,1,\dots$ formano un sistema di direzioni coniugate, mentre i vettori residui $r^{(k)}$, con $k=0,1,\dots$ formano un ***sistema ortogonale***.
>$$\begin{array}\ <r^{(k)},r^{(j)}> =0 \\ <Ap^{(k)},p^{(j)}> = 0 \end{array}\qquad k\neq j, j=0,1,\dots,k-1$$

Ciò significa che la direzione $p^{(k)}$ è coniugata a **tutte** le *precedenti direzioni di discesa*.
- Il residuo $r^{(k)}$ è [[4 - Prodotto Scalare#Vettori Ortogonali|ortogonale]] a ***tutti i precedenti residui***.

>[!hint] Osservazione
>Poiché in $\mathbb{R}^n$ non si possono avere più di $n$ vettori in una ***matrice ortogonale***, in teoria il metodo appartiene alla classe dei [[Risoluzione di Sistemi Lineari#Metodi Diretti|metodi diretti]].
>- In pratica a causa di [[Errore di Rappresentazione|errori di arrotondamento]] il metodo non termina al passo $k=n-1$.

Possiamo dire quindi:
$$
<r^{(k+1)},p^{(k)}> = 0
$$
Sostituendo nella relazione che esprime il risultato generale l'espressione di $p^{(k)}$ si ottiene:
$$
<r^{(k+1)},-r^{(k)}+\gamma^{(k)}p^{(k-1)}> = 0
$$
$$
0=-<r^{(k+1)},r^{(k)}>+\gamma^{(k)} \underbrace{ <r^{(k+1)},p^{(k-1)}> }_{ 0 }
$$

>[!help] Parametro $\alpha^{(k)}$
>È possibile trovare una espressione semplificata per il parametro $\alpha^{(k)}$
>$$<r^{(k)},p^{(k)}> = <r^{(k)},-r^{(k)}+\gamma^{(k)}p^{(k-1)}> =-<r^{(k)},r^{(k)}>+\underbrace{ \gamma^{(k)}<r^{(k)},p^{(k-1)}> }_{ 0 }$$

Otteniamo quindi:
$$
\alpha^{(k)}=\displaystyle{\frac{<r^{(k)},r^{(k)}>}{<Ap^{(k)},p^{(k)}>}}\qquad k=1,2,\dots
$$
> Da questa formula è possibile trovare una formula computazionalmente più efficiente per $\gamma^{(k)}$

$$
\gamma^{(k)}=\displaystyle{\frac{<r^{(k)},r^{(k)}>}{<r^{(k-1)},r^{(k-1)}>}}
$$
### Pseudocodice
```pseudo
	\begin{algorithm}
	\caption{Gradiente Coniugato}
	\begin{algorithmic}
\State $ x^{(0)} $
\State $ r^{(0)}=Ax^{(0)}-b $
\State $ p^{(0)}=-r^{(0)} $
\State $ k=0 $
	\While{$\text{Arresto}\leq \varepsilon$}
	\State $ \alpha^{(k)}=\displaystyle{\frac{<r^{(k)},r^{(k)}>}{<Ap^{(k)},p^{(k)}>}} $
	\State $ x^{(k+1)}=x^{(k)}+\alpha^{(k)}p^{(k)} $
	\State $ r^{(k+1)}=r^{(k)}+\alpha^{(k)}Ap^{(k)} $
	\State $ \text{Arresto}=\|r^{(k+1)}\|_2^2 $
	\State $ \gamma^{(k+1)}=\displaystyle{\frac{<r^{(k+1)},r^{(k+1)}>}{<r^{(k)},r^{(k)}>}} $
	\State $ p^{(k+1)}=-r^{(k+1)}+\gamma^{(k+1)}p^{(k)} $
	\State $ k=k+1 $
    \EndWhile
	\end{algorithmic}
	\end{algorithm}
```

#### Confronto
> Confrontiamo Graficamente ($n=2$) il metodo del gradiente coniugato e il [[Metodi di Discesa#Steepest Descent|metodo steepest descent]].
 
![[Comparison.png]]
### Velocità di Convergenza
>[!info]
> Nel caso del ***metodo del gradiente coniugato*** applicato alla minimizzazione di una [[3 - Forme Quadratiche|forma quadratica]] $F(x)=\frac{1}{2}<Ax,x> - <b,x>$ con $A$  [[1 - Forme Bilineari#Matrici Simmetriche e Antisimmetriche|simmetrica]] e [[3 - Forme Quadratiche#Tipi di Forme Quadratiche|definita positiva]], il metodo ha [[Ordine di Convergenza#Ordini|ordine di convergenza lineare]].

Per misurare l'errore, si definisce la norma indotta dalla matrice simmetrica definita positiva $A$ su $x$ come:
$$
\|x\|_{A}^2=x^TAx
$$
- Pertanto, definendo l'errore al passo $k$
$$
e^{(k)}=x^{(k)}-x^*
$$
> Si ha

$$
\displaystyle{\frac{\|e^{(k+1)}\|_{A}}{\|e^{(k)}\|_{A}}}\approx\rho
$$
L'***ordine di convergenza è lineare*** e il fattore di convergenza $0<\rho<1$ determina quanto *rapidamente* si riduce l'errore nelle iterazioni.

> Il fattore di convergenza dipende dall'***indice di condizionamento della matrice***.

$$
\rho=\displaystyle{\frac{\sqrt{ K(A) }-1}{\sqrt{ K(A) }+1}}
$$
