## Generalità sui Metodi
---
>[!info]
>Per la risoluzione di un [[../Equazioni Lineari/Sistemi Lineari|sistema lineare]] $Ax=b$ con matrice $A$ *reale*, [[../../Algebra e Geometria/Frome Bilineari e Prodotti Scalari/1 - Forme Bilineari#Matrici Simmetriche e Antisimmetriche|simmetrica]] e [[../../Algebra e Geometria/Frome Bilineari e Prodotti Scalari/3 - Forme Quadratiche#Tipi di Forme Quadratiche|definita positiva]], un'altra famiglia di [[../Equazioni Lineari/Risoluzione di Sistemi Lineari#Metodi Iterativi|metodi iterativi]] è data dai cosi detti ***metodi di discesa***.

>[!check] Notazione
>Dati due vettori colonna $x,y\in\mathbb{R}^n$ con la notazione $<x,y>$ si intende il [[../../Algebra e Geometria/Frome Bilineari e Prodotti Scalari/4 - Prodotto Scalare|prodotto scalare]] $x^Ty$.

### Teorema 1
>[!cite]
>Sia $A\in\mathbb{R}^{n\times n}$, matrice *simmetrica* e *definita positiva*, $b,x\in\mathbb{R}^n$
><u>Allora</u>
>La soluzione del sistema lineare $Ax=b$ coincide con il punto di minimo della seguente ***funzione quadratica***.
>$$F(x)=\frac{1}{2}<Ax,x> - <b,x> =\frac{1}{2}x^TAx-b^Tx=\frac{1}{2}\sum_{i=1}^n\sum_{j=1}^na_{ij}x_{i}x_{j}-\sum_{i=1}^nb_{i}x_{i}$$
>Dove la forma quadratica $Q(x)= <Ax,x\geq x^TAx$ è positiva per $x\neq0$
>>[!quote] Conclusione
>>Il teorema afferma che il vettore che risolve il sistema lineare coincide con il vettore che ***minimizza la forma quadratica***.

##### Dimostrazione
>Consideriamo il sistema $Ax=b$
- Definiamo il vettore residuo $r=Ax-b$

>[!abstract] Se $x^*$ è la soluzione del sistema, allora $r=Ax^*-b=0$

Ora consideriamo la funzione quadratica $F(x)$ e cerchiamo il suo *punto di minimo*.
- Calcoliamo il gradiente di $F$ e uguagliamolo a zero.
$$
\nabla F=\begin{bmatrix}
\displaystyle\frac{ \partial F }{ \partial x_{1} } \\
\displaystyle\frac{ \partial F }{ \partial x_{2} } \\
\vdots \\
\displaystyle\frac{ \partial F }{ \partial x_{n} } 
\end{bmatrix}=0
$$
Sviluppiamo $F(x)$

$$
\begin{array}
\ F(x)=\frac{1}{2}(a_{11}x_{1}^2+a_{12}x_{1}x_{2}+\dots+a_{1i}x_{1}x_{i}+\dots+a_{1n}x_{1}x_{n}+ \\ a_{21}x_{2}x_{1}+a_{22}x_{2}^2+\dots+a_{2i}x_{2}x_{i}+\dots+a_{2n}x_{2}x_{n}
+ \\
\dots \\
a_{i1}x_{i}x_{1}+a_{i2}x_{i}x_{2}+\dots+a_{ii}x_{i}^2+\dots+a_{in}x_{i}x_{n}
+ \\
\dots \\
a_{n1}x_{n}x_{1}+a_{n2}x_{n}x_{2}+\dots+a_{ni}x_{n}x_{i}+\dots+a_{nn}x_{n}^2
)- \\
-(b_{1}x_{1}+b_{2}x_{2}+\dots+b_{i}x_{i}+\dots+b_{n}x_{n})\end{array}
$$


> Calcoliamo $\displaystyle\frac{ \partial F }{ \partial x_{i} }\quad \forall i\in[1,n]$

$$
\displaystyle\frac{ \partial F }{ \partial x_{i} }=\frac{1}{2}(a_{1i}x_{1}+a_{2i}x_{2}+\dots+a_{ni}x_{n}+a_{i1}x_{1}+a_{i2}x_{2}+\dots+2a_{ii}x_{i}+\dots+a_{in}x_{n})-b_{i} 
$$
Per ipotesi la matrice $A$ è ***simmetrica*** quindi $a_{ij}=a_{ji}$ quindi:
$$
\displaystyle\frac{ \partial F }{ \partial x_{i} }=\frac{1}{2}(2a_{i1}x_{1}+2a_{i2}x_{2}+\dots+2a_{ii}x_{i}+\dots+2a_{in}x_{n})-b_{i} 
$$
- Cioè
$$
\displaystyle\frac{ \partial F }{ \partial x_{i} }=\sum_{j=1}^n a_{ij}x_{j}-b_{i}=0 \quad i=1,\dots,n
$$

>[!quote] In termini vettoriali

$$
\nabla F=Ax-b
$$
>[!check]
>Risulta che il vettore che annulla il gradiente coincide con la *soluzione del sistema lineare* che rende nullo il residuo.

>Verifichiamo che il punto che annulla il gradiente è un punto di minimo

$$
H_F(\mathbf{x}) = 
\begin{bmatrix}
\displaystyle\frac{\partial^2 F}{\partial x_1^2} & \displaystyle\frac{\partial^2 F}{\partial x_1 \partial x_2} & \cdots & \displaystyle\frac{\partial^2 F}{\partial x_1 \partial x_n} \\
\displaystyle\frac{\partial^2 F}{\partial x_2 \partial x_1} & \displaystyle\frac{\partial^2 F}{\partial x_2^2} & \cdots & \displaystyle\frac{\partial^2 F}{\partial x_2 \partial x_n} \\
\vdots & \vdots & \ddots & \vdots \\
\displaystyle\frac{\partial^2 F}{\partial x_n \partial x_1} & \displaystyle\frac{\partial^2 F}{\partial x_n \partial x_2} & \cdots & \displaystyle\frac{\partial^2 F}{\partial x_n^2}
\end{bmatrix}
$$
>[!hint] Osservazione
>Poiché $\displaystyle\frac{ \partial F }{ \partial x_{i} }=a_{i1}x_{1}+a_{i2}x_{2}+\dots+a_{ii}x_{i}+\dots+a_{ij}x_{j}+\dots+a_{in}x_{n}-b_{i}$
>- Si ha
>$$\displaystyle\frac{ \partial F }{ \partial x_{i}\partial x_{j} }=a_{ij} $$
>Quindi $H_{F}(x)=A$


Risulta che la matrice Hessiana coincide con la matrice $A$ che è ***simmetrica*** e ***definita positiva***.
> Vale il seguente risultato

Se $H_{F}(x^{*})$ è simmetrica e definita positiva allora il punto critico $x^*$ in cui si annulla il gradiente è ***punto di minimo*** per la funzione $F$.

>[!done] Risultato
>Il risultato del teorema ci permette di affermare che per la risoluzione di *sistemi lineari* con matrice ***simmetrica definita positiva*** in generale possono essere usati i metodi per determinare il ***minimo di una funzione quadratica***.

I metodi iterativi consistono nel determinare a partire da un vettore $x$ al passo $k$ un vettore direzione $p$ al passo $k$ *opportuno* e nel correggere $x^{(k)}$ in questa direzione in modo che il valore della funzione quadratica $F$ il nuovo iterato diminuisca.
$$
F(x^{(k)}+\alpha^{(k)}p^{(k)})<F(x^{(k)})
$$
##### Pseudocodice
```pseudo
	\begin{algorithm}
	\caption{Steep Descent}
	\begin{algorithmic}
	\State $ x^{(0)},k=0 $
	\While{$\text{Fino a Convergenza}$}
	\State $ \text{Determina la direzione }p^{(k)} $
	\State $ \text{Scegli lo step-size} \alpha^{(k)} $
	\State $ x^{(k+1)}=x^{(k)}+\alpha^{(k)}p^{(k)} $
	\State $ k++ $
    \EndWhile
	\end{algorithmic}
	\end{algorithm}
```
### Scelta dello Step-Size
>Nel caso in cui $A$ sia nota si vede che:

$$
\begin{array}
\ F(x^{(k)}+\alpha^{(k)}p^{(k)})=\frac{1}{2}<A(x^{(k)}+\alpha^{(k)}p^{(k)}),(x^{(k)}+\alpha^{(k)}p^{(k)})> -<b,(x^{(k)}+\alpha^{(k)}p^{(k)})> = \\
=\frac{1}{2}< Ax^{(k)},x^{(k)}>+\frac{1}{2}\alpha^{(k)}<Ax^{(k)},p^{(k)}>+\frac{1}{2}\alpha^{(k)}<Ap^{(k)},x^{(k)}>+ \\
+\frac{1}{2}(\alpha^{(k)})^2<Ap^{(k)},p^{(k)}>+<b,x^{(k)}>-\alpha^{(k)}<b,p^{(k)}>
\end{array}$$
>[!check]
>Tenendo conto del fatto che $<Ax^{(k)},p^{(k)}> = <Ap^{(k)},x^{(k)}>$ e ponendo $r^{(k)}=Ax^{(k)}-b$, si ha:

$$
F(x^{(k)}+\alpha^{(k)}p^{(k)})=F(x^{(k)})+\frac{1}{2}(\alpha^{(k)})^2<Ap^{(k)},p^{(k)}>+\alpha^{(k)}<r^{(k)},p^{(k)}>
$$
Che è una ***funzione quadratica*** in $\alpha^{(k)}$

> Per determinare il valore di $\alpha^{(k)}$ che rende minima $F$ nella direzione $p^{(k)}$ basta considerare:

$$
\displaystyle{\frac{\text{d}F}{\text{d}\alpha^{(k)}}}= \alpha^{(k)}<Ap^{(k)},p^{(k)}>+<r^{(k)},p^{(k)}>
$$
E uguagliarla a $0$

>[!tip] Step-Size
>Chiamiamo ***Step-Size*** o *Learning Rate* (nelle reti neurali)
>$$\alpha^{(k)}=-\displaystyle{\frac{<r^{(k)},p^{(k)}>}{<Ap^{(k)},p^{(k)}>}}$$
>>[!quote] Significato
>>Questo significa quanto muoversi in una direzione per ***diminuire il valore della funzione***.

#### Teorema Vettore Residuo
>[!check] Teorema
>Nel *punto di minimo* $x^{(k)+1}=x^{(k)}+\alpha^{(k)}p^{(k)}$, ottenuto muovendosi lungo la **direzione** $p^{(k)}$ con $\alpha^{(k)}$, il **vettore residuo** $r^{(k+1)}=Ax^{(k+1)}-b$ risulta ***ortogonale*** alla direzione $p^{(k)}$, cioè.
>$$<r^{(k+1)},p^{(k)}> ={0}$$

##### Dimostrazione
Essendo
$$r^{(k+1)}= Ax^{(k+1)}-b=r^{(k)}+\alpha^{(k)}Ap^{(k)}$$
> Si ottiene:

$$
<r^{(k+1)},p^{(k)}> = <r^{(k)},p^{(k)}>+\alpha^{(k)}<Ap^{(k)},p^{(k)}>
$$
Che risulta $0$ scegliendo $\alpha^{(k)}$ secondo lo ***step-size***
$$
<r^{(k+1)},p^{(k)}> = <r^{(k)},p^{(k)}>+-\displaystyle{\frac{<r^{(k)},p^{(k)}>}{\cancel{ <Ap^{(k)},p^{(k)}> }}}\cancel{ <Ap^{(k)},p^{(k)}> }=0
$$
### Scelta della Direzione
>[!info]
>Per quanto riguarda la scelta delle ***direzioni di discesa*** $p^{(k)}$, se si considera la relazione:
>$$\alpha^{(k)}=-\displaystyle{\frac{<r^{(k)},p^{(k)}>}{<Ap^{(k)},p^{(k)}>}}$$
>Si può affermare che $p^{(k)}$ **non** deve essere *ortogonale al residuo* $r^{(k)}$ o **non** deve essere *ortogonale al gradiente* $\nabla F(x^{(k)})$  perché porterebbe a $\alpha^{(k)}=0$.

Consideriamo lo [[../../Analisi/Taylor/Formula di Taylor|sviluppo in serie di Taylor]] della $F(x^{(k)}+\alpha^{(k)}p^{(k)})$ in un intorno di $x^{(k)}$:
$$
F(x^{(k+1)})=F(x^{(k)}+\alpha^{(k)}p^{(k)})=F(x^{(k)})+\underbrace{ \alpha^{(k)}\nabla F(x^{(k)})^Tp^{(k)} }_{ <\nabla F(x^{(k)}),p^{(k)}> }+\dots+\circ(\mid\alpha^{(k)}\mid)
$$
- Ora richiediamo: $F(x^{(k)}+\alpha^{(k)}p^{(k)})<F(x^{(k)})\quad \text{per } \alpha^{(k)}>0$

<u>Allora</u>
- La direzione $p^{(k)}$ *deve soddisfare la seguente condizione*:
$$
<\nabla F(x^{(k)},p^{(k)})> \ <0
$$
>[!done] Rappresenta la condizione di direzione ammissibile

Ci dice che l'angolo fra la nuova direzione di discesa e il gradiente deve avere $\cos$ **negativo**, cioè $\displaystyle\frac{\pi}{2}<\theta< \frac{3\pi}{2}$.

>[!hint]
>Poiché la condizione di ammissibilità per la direzione di discesa è data in funzione del ***gradiente*** questi metodi vengono chiamati ***metodi del gradiente***.

## Steepest Descent
---
>[!tldr] Idea
>Il metodo di discesa "***Steepest Descent***" è caratterizzato dalla scelta ad ogni passo $k$ , della direzione $p^{(k)}$ come l'***antigradiente*** della funzione $F$ calcolato nell'iterato $k$-esimo:
>$$p^{(k)}=-\nabla F(x^{(k)})=-Ax^{(k)}+b=-r^{(k)}$$
>>[!quote] Antigradiente
>>Poiché il gradiente è la direzione di massima crescita questo significa che l'**antigradiente** coincide con la direzione di massima decrescita.

> La scelta dello ***step-size***, diventa:

$$
\alpha^{(k)}=-\displaystyle{\frac{<r^{(k)},p^{(k)}>}{<Ap^{(k)},p^{(k)}>}}=\displaystyle{\frac{<r^{(k)},r^{(k)}>}{<Ar^{(k)},r^{(k)}>}}
$$
- e:
$$
x^{(k+1)}=x^{(k)}+\alpha^{(k)}p^{(k)}
$$

### Pseudocodice
```pseudo
	\begin{algorithm}
	\caption{Steepest Descent}
	\begin{algorithmic}
	\State $ x^{(0)},k=0 $
	\While{$\text{Fino a Convergenza}$}
	\State $ p^{(k)}=-\nabla f(x^{(k)}) $
	\State $ \alpha^{(k)}=\displaystyle{\frac{<r^{(k)},r^{(k)}>}{<Ap^{(k)},p^{(k)}>}} $
	\State $ \text{Aggiorna l'iterato} $
	\State $ x^{(k+1)}=x^{(k)}+\alpha^{(k)}p^{(k)} $
	\State $ r^{(k+1)}=r^{(k)}+\alpha^{(k)}Ap^{(k)} $
	\State $ k++ $
    \EndWhile
	\end{algorithmic}
	\end{algorithm}
```

>[!hint] Aggiornamento del Resto
>$$\begin{array}\ r^{(k+1)}=Ax^{(k+1)}-b= \\=A(x^{(k)}+\alpha^{(k)}p^{(k)})-b= \\ =Ax^{(k)}-b+\alpha^{(k)}Ap^{(k)}= \\ =r^{(k)}+\alpha^{(k)}Ap^{(k)}\end{array}$$

Si considera che il procedimento iterativo ha ***raggiunto la convergenza*** quando $\|r^{(k+1)}\|_{2}\leq\text{tol}$

##### Esempio
$$ A=\begin{bmatrix} 8 & 4 \\ 4 & 3 \end{bmatrix}\quad b=\begin{bmatrix} 8 \\ 10 \end{bmatrix}\quad x=\begin{bmatrix} -2 \\ 6\end{bmatrix}$$
> Iterato iniziale $x^{(0)}=\begin{bmatrix}0 \\ 0\end{bmatrix}$

![[attachements/SteepestDescent.png|550]]

>[!caution] Concetto
>La direzione $p^{(0)}$ è **opposta** alla *direzione del gradiente* alla curva di livello $F(x^{(0)})=\text{const}$ nel punto $x^{(0)}$

### Velocità di Convergenza
>[!info]
>Nel caso del metodo del gradiente applicato alla minimizzazione di una forma quadratica $F(x)=\frac{1}{2}<Ax,x>-<b,x>$ con $A$ matrice [[../../Algebra e Geometria/Frome Bilineari e Prodotti Scalari/1 - Forme Bilineari#Matrici Simmetriche e Antisimmetriche|simmetrica]] e [[../../Algebra e Geometria/Frome Bilineari e Prodotti Scalari/3 - Forme Quadratiche#Tipi di Forme Quadratiche|definita positiva]], il metodo ha  [[../Equazioni non Lineari/Ordine di Convergenza#Ordini|ordine di convergenza lineare]].

##### Misurare l'Errore
>Definiamo la *Norma Indotta* dalla matrice simmetrica e definita positiva $A$ su $x$.

$$
\|x\|_{A}^2=x^TAx
$$
>[!fail] Errore
>Definiamo l'***errore*** al passo $k$
>$$e^{(k)}=x^{(k)}-x^*$$

Si ha, quindi:
$$
\displaystyle{\frac{\|e^{(k+1)}\|_{A}}{\|e^{(k)}\|_{A}}}\approx\rho
$$
Il ***fattore di convergenza*** dipende dall'[[../Condizionamento e Stabilità/Condizionamento#Quantificare il Condizionamento|indice di condizionamento della matrice]].
$$
\rho=\displaystyle{\frac{K(A)-1}{K(A)+1}}
$$
- Dove $K(A)$ è l'[[../Equazioni Lineari/Condizionamento di un Sistema Lineare|indice di condizionamento]] di $A$.

>[!done] Condizionamento
>Tanto più $K(A)$ è alto, tanto più il rapporto si approssima a $1$.
>- Più è ***lenta la convergenza***.

$$
\|e^{(k)}\|_{A}\leq \left( \displaystyle{\frac{K(A)-1}{K(A)+1}} \right)^k\cdot\|e^{(0)}\|_{A} 
$$