>[!definizione]
>I sistemi lineari [[Sistemi Lineari#Casi|sovradeterminati]] hanno un numero di equazioni superiori al numero di incognite, ossia sono della forma:
>$$Ax=b$$
>$$A\in\mathbb{R}^{m\times n},\quad x\in\mathbb{R}^n, \quad b\in\mathbb{R}^m,\quad m>n$$

I ***sistemi sovradeterminati*** potrebbero non avere soluzioni.

> In particolare, se:
- $\text{rank}(A)\neq \text{rank}(A|b)$: Il sistema è **incompatibile**, non c'è *nessuna soluzione*.
- $\text{rank}(A)= \text{rank}(A|b)$: Il sistema è **compatibile**.
$$
\begin{cases}
\text{rank}(A)=n\quad \text{Unica Soluzione} \\
\text{rank}(A)<n \quad \infty^{n-\text{rank}(A)} \text{ Soluzioni}
\end{cases}
$$

>[!danger] Attenzione
>La risoluzione di un sistema lineare sovradeterminato risulta essere un problema [[Condizionamento#Condizionamento di un Problema|mal posto]].

## Least Squares
---
> Cerchiamo di rendere il problema ***ben posto***.

>[!info] Risoluzione di Sistemi Lineari sovradeterminati nel senso dei minimi quadrati
>Cerchiamo la soluzione del sistema, nel ***senso dei minimi quadrati***:
>- Definito il vettore residuo come:
>$$r(x):=Ax-b$$
>
>Cerchiamo il vettore $x^* \in \mathbb{R}^n$ che rende minima la [[Norma|norma 2]] al ***quadrato del residuo***.

$$
x^*=\arg\min\limits_{x\in\mathbb{R}^n }\|r(x)\|_{2}^2=\arg\min\limits_{x\in\mathbb{R}^n }\|Ax-b\|_{2}^2
$$
$$
\begin{array}\
F(x)=\|Ax-b\|_{2}^2=(Ax-b)^T(Ax-b)=x^TA^TAx-x^TA^Tb-b^TAx+b^Tb= \\
=x^TA^TAX-2x^TA^Tb+b^Tb
\end{array}
$$
- Poniamo $G=A^TA$

> Si ha che $G$ è [[1 - Forme Bilineari#Matrici Simmetriche e Antisimmetriche|simmetrica]].

$$
F(x)=x^TGx-2x^TA^Tb+b^Tb
$$
Per *calcolare* il valore di $x^*\in\mathbb{R}^n$ che ***rende minimo*** $F(x)$, calcoliamo il [[Calcolo Differenziale#Gradiente|gradiente]] della funzione $F(x)$ e **imponiamo che si annulli**.

>[!tip] Ricorda
>Il gradiente rispetto ad $x$ della forma quadratica $x^TGx$ con $G$ ***simmetrica*** è:
>$$2Gx$$
>- Allora si ha:
>
>$$\nabla F(x)=2Gx-2A^Tb=0$$

Il vettore $x^*$ che annulla il gradiente della funzione $F(x)$ è la soluzione del sistema lineare:
$$
Gx=A^Tb
$$
- Equazioni note come ***equazioni normali***.

> Ora dobbiamo verificare che il [[7 - Determinante di una Matrice|determinante]] della matrice $G$ sia ***diverso da zero***.

- È inoltre necessario che la matrice Hessiana valutata nella soluzione sia definita positiva.
$$
\nabla^2F(x)=2G=2A^TA
$$

>[!help] Pre Requisiti
>La matrice $G$ deve essere [[1 - Forme Bilineari#Matrici Simmetriche e Antisimmetriche|simmetrica]] e [[3 - Forme Quadratiche#Tipi di Forme Quadratiche|definita positiva]].

- Verifichiamo che sia ***definita positiva***.

$$
\forall x\neq 0,\quad x^TA^TAx>0
$$
> Si osserva che $x^TA^TAx$ può essere vista come:

$$
(Ax)^TAx=\|Ax\|_{2}^2
$$
Per le *proprietà sulle norme*:
$$
\|Ax\|_{2}^2>0 \quad \forall Ax\neq 0
$$

>[!check] Teorema
>Dato il ***sistema lineare sovradeterminato*** $Ax=b$ dove $A\in\mathbb{R}^{m\times n},\quad x\in\mathbb{R}^n, \quad b\in\mathbb{R}^m,\quad m>n$
>$\arg\min\limits_{x\in\mathbb{R}^n }\|Ax-b\|_{2}^2\iff$ è la *soluzione* di $A^TAx=A^Tb$
>>[!quote]
>>La soluzione è unica se e solo se la matrice $A$ ha [[6 - Cambiamenti di Base#Rango di una Matrice|rango massimo]].

Se questa condizione è verificata, il vettore $x^*$ tale che:
$$
\arg\min\limits_{x\in\mathbb{R}^n }\|Ax-b\|_{2}^2
$$
Può essere sempre calcolato, come ***soluzione delle equazioni normali***:
$$
A^TAx=A^Tb
$$
>Il sistema può essere risolto utilizzando il [[Risoluzione di Sistemi Lineari#Metodo di Cholesky|metodo di Cholesky]].

### Condizionamento
> Poiché

$$
K_{2}(A^TA)=(K_{2}(A))^2
$$
>[!danger] Significato
>Il sistema delle *equazioni normali* può ***risultare mal condizionato*** anche quando il problema nella forma originale non lo è.

Se il problema è "*mediamente mal condizionata*"  il metodo delle equazioni normali è ***numericamente pericoloso***.

>[!hint] Soluzione
>È necessario individuare una ***trasformazione ortogonale*** che applicata al residuo $r=Ax-b$, trasformi il vettore in modo tale da rendere più facile la soluzione del problema.

>[!abstract] Proprietà
>Una matrice ortogonale $Q\in\mathbb{R}^{m\times n}$ applicata ad un vettore $y\in\mathbb{R}^m$, ne mantiene inalterata la norma $2$ al quadrato.
>$$\|y\|_{2}^2=\|Qy\|_{2}^2$$

> Dimostrazione

Ricordiamo che una ***matrice ortogonale*** $Q$ è tale che: $Q^TQ=QQ^T=I$
$$
\|y\|_{2}^2=y^Ty=y^TQ^TQy=(Qy)^T(Qy)=\|Qy\|_{2}^2
$$

> ***Osservazione***

Dato un vettore $y\in\mathbb{R}^m$, sia $m>n$ consideriamo la sua *norma al quadrato*.
$$
\|y\|_{2}^2=\sum_{i=1}^my^2_{i}=\sum_{i=1}^ny^2_{i}+\sum_{i=n+1}^my^2_{i}
$$
- Suddividiamo il vettore $y$ in due vettori $\tilde{y}_{1}$, costituito dalle prime $n$ componenti del vettore $y$ e $\tilde{y}_{2}$, formato dalle rimanenti.
$$
y=\begin{bmatrix}
\tilde{y}_{1} \\
\tilde{y}_{2}
\end{bmatrix}
$$
$$
\|y\|_{2}^2=\|\tilde{y}_{1}\|_{2}^2+\|\tilde{y}_{2}\|_{2}^2
$$
