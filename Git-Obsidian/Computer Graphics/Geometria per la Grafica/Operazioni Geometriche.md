## Operazioni
---
### Prodotto Scalare
![[4 - Prodotto Scalare#Prodotto Scalare Standard]]

Una notazione equivalente è la seguente:
$$
<x,y> =x^{T}y
$$

> In generale un prodotto scalare su uno spazio vettoriale $\mathbb{R}^{n}$ è una [[1 - Applicazioni Lineari|applicazione]] da $\mathbb{R}^{n}\times\mathbb{R}^{n}$ a $\mathbb{R}$.

>[!hint] Proprietà
>1. $x\cdot y=y\cdot x\qquad \forall x.y\in \mathbb{R}^{n}$
>2. $x\cdot(\lambda_{1}y_{1}+\lambda_{2}y_{2})=\lambda_{1}x\cdot y_{1}+\lambda_{2}x\cdot y_{2}\qquad \forall x,y_{1},y_{2}\in \mathbb{R}^{n}, \quad \forall\lambda_{1},\lambda_{2}\in\mathbb{R}$
>3. $x\cdot x>0 \implies x\neq 0$

>[!abstract] Ortogonalità

Due vettori $x,y\in \mathbb{R}^{n}$ si dicono ***ortogonali*** se il loro *prodotto scalare* è **nullo**.

> Per misurare la lunghezza

![[Norma#^093ca9]]

>[!important] Importante
>La norma euclidea fornisce una nozione di lunghezza che rimane *inalterata* per **rotazioni**/**traslazioni** e **riflessioni** del vettore.

$$
\|a\|_{2}=\sqrt{ a^{T}a }=\sqrt{ a^{T}Q^{T}Qa }=\sqrt{ (Qa)^{T}(Qa) }=\|Qa\|_{2}
$$

>[!caution] Normalizzazione

Un vettore di lunghezza $1$ è detto ***vettore unitario***.
- Dato un vettore qualsiasi lo si può normalizzare (renderlo di *lunghezza unitaria*)
$$
x_{n}=\frac{x}{\|x\|_{2}}
$$
> Dimostrazione

$$
\left\| \frac{a}{\|a\|_{2}} \right\|_{2}=\frac{1}{\|a\|_{2}}\cdot\|a\|_{2}=1
$$

Un vettore normalizzato si dice ***versore***.

>[!definizione] Prodotto Scalare
>Siano $u,v \in \mathbb{R}^{n}$ allora il ***prodotto interno*** (*prodotto scalare*) è definito nel seguente modo:
>$$u\cdot v=\|u\|\cdot \|u\|\cos(\theta)$$

#### Interpretazione Geometrica
> Se $\|u\|\neq 1$, calcoliamo la lunghezza $\|a\|$ della proiezione di un vettore $v$ sul vettore $u$.

- $\|a\|=\|v\|\cos(\theta)$ è la ***lunghezza della proiezione ortogonale*** di $v$ su $u$.

Sostituendolo nella formula del prodotto scalare:
$$
u\cdot v=\|u\|\|v\|\cos(\theta)=\|u\|\|a\|
$$

>[!done] In Breve
>Il ***prodotto scalare*** tra due vettori $u$ e $v$ si può interpretare come il prodotto tra la *lunghezza del vettore* $u$ e la *lunghezza della proiezione ortogonale del vettore* $b$ su esso.

Si deduce inoltre che:
$$
\|a\|= \displaystyle{\frac{<u,v>}{\|u\|}}
$$
- Il prodotto scalare è un valore che da *informazioni sulla relazione tra i due vettori*.
- Il segno da informazioni sull'*angolo che formano i vettori*.

### Prodotto Vettoriale
>[!definizione]
>$a\times b$ è un vettore perpendicolare ad entrambi $a$ e $b$ ed ha la direzione definita dalla ***regola della mano destra***.

>[!hint] Proprietà

1. $\|a\times b\|=\|a\|\|b\|\sin(\theta)$
2. $\|a\times b\|$ è l'***area del parallelogramma*** individuato dai due vettori.
3. $\|a\times b\|=0$ se $a$ e $b$ sono *paralleli*.

###### Esempio
> Vettore [[Sistema di Coordinate#^d4f7f8|normale]] ad un triangolo definiti i vertici $(A,B,C)$

$$
n^{*}=(B-A)\times(C-A)
$$
$$
n=\frac{n^{*}}{\|n^{*}\|}
$$
> ***Area*** di un triangolo definiti i vertici $(A,B,C)$

$$
A=\frac{1}{2}\|(B-A)\times(C-A)\|
$$
### Coordinate Baricentriche
>[!definizione]
>Una ***combinazione affine*** è una *combinazione lineare di punti* con coefficienti che hanno somma $1$.
>$$P=\alpha_{0}P_{0}+\alpha_{1}P_{1}+\dots+\alpha_{n}P_{n}\qquad \alpha_{0}+\alpha_{1}+\dots+\alpha_{n}=1$$
>
>>[!done] Coordinate Baricentriche
>> I coefficienti $\alpha_{0}+\alpha_{1}+\dots+\alpha_{n}$ sono le ***coordinate baricentriche*** di $P$ nello *spazio affine*.

Le *coordinate baricentriche* di un punto permettono di esprimere la posizione di un punto rispetto ai vertici di un triangolo, o più in generale un [[Sistema di Coordinate#Simplesso|simplesso]], in modo ***indipendente dal sistema di coordinate***.

>[!hint] Applicazioni Pratiche
>- Determinazione della ***posizione relativa***, le coordinate indicano quanto "*peso*" ciascun vertice ha nel determinare la posizione del punto.
>- Consentono di [[Interpolazione Polinomiale|interpolare]] valori, come colori, temperature e altezze, definiti nei vertici del triangolo, per ottenere *valori continui in ogni punto interno*.
>- ***Geometria Computazionale***: facilitano il controllo di appartenenza di un punto a un triangolo, e migliorano l'efficienza degli algoritmi di #addLink *rendering*, *collision detection* e *mesh processing*.

La ***combinazione affine*** di due punti distinti descrive la *retta passante per i due punti*.

> Siano $Q$ e $R$ due punti dello *spazio affine reale* e sia $v=R-Q$
- Consideriamo la combinazione affine $\alpha+\beta=1$

$$
\begin{array}
\ P=\alpha R+\beta Q, \quad \beta=1-\alpha \\
P(\alpha)=\alpha R+(1-\alpha)Q \\
P(\alpha)=Q+\alpha(R-Q) \\
P(\alpha)=Q+\alpha v
\end{array}
$$

>[!caution] Combinazione Convessa
>Una ***combinazione convessa*** è una combinazione affine *con pesi positivi*.

>***Casi Speciali***:
- In una combinazione convessa di due punti in cui i coefficienti sono entrambi $0.5$ il punto risultante si trova a ***metà tra i due***.
- Nel caso di $n$ punti che formano un *poligono convesso*, qualsiasi punto risultante si trova all'***interno del poligono***.
	- Se tutti i pesi sono uguali a $\frac{1}{n}$, il punto risultante si chiama ***centroide*** dell'insieme dei punti.

> Consideriamo ora un triangolo $A,B,C$

Prendiamo un qualsiasi punto $P$ dato dalla combinazione convessa di $A,B,C$.

![[BarycentricCoordinates.png]]

Le aree risultanti: $APB, BPC$ e $APC$ sono *proporzionali alle coordinate baricentriche della combinazione*.
$$
P=\alpha_{0}A+\alpha_{1}B+\alpha_{2}C
$$
$$
\text{Area}_{ABC}=\text{Area}_{APB}+\text{Area}_{BPC}+\text{Area}_{APC}  
$$
- Ma sappiamo che $A_{PCB}=\alpha_{0}A_{ABC},\quad A_{PCA}=\alpha_{1}A_{ABC},\quad A_{PAB}=\alpha_{2}A_{ABC}$

**Quindi**:
$$
\alpha_{0}=\displaystyle{\frac{\text{Area(PCB)}}{\text{Area(ABC)}}}\qquad\alpha_{1}=\displaystyle{\frac{\text{Area(PAC)}}{\text{Area(ABC)}}}\qquad\alpha_{2}=\displaystyle{\frac{\text{Area(PAB)}}{\text{Area(ABC)}}}
$$
##### Interpolazione di Colore
>[!check] Colore in un Triangolo
>La formula per ***interpolare un colore*** $C_{P}$ in un punto $P$ interno a un triangolo $ABC$ con *colori assegnati ai vertici* è:
>$$C_{P}=\alpha_{0}C_{A}+\alpha_{1}C_{B}+\alpha_{2}C_{C}$$

> **Dove**
- $C_{A},C_{B},C_{C}$ sono i *colori associati* ai vertici.
	- Ogni colore può essere espresso come vettore $RGB$ ($C_{A}=(r_{A},g_{A},b_{A})$).
- $\alpha_{0},\alpha_{1},\alpha_{2}$ sono le coordinate baricentriche di $P$ rispetto al triangolo $ABC$.

Ogni vertice del triangolo ha un colore specifico
- Calcolo le coordinate baricentriche per ogni `pixel` o *frammento*.
- Durante la rasterizzazione, per ogni `pixel` che cade dentro al triangolo vengono calcolate le coordinate $\alpha_{0},\alpha_{1},\alpha_{2}$, *rispetto ai vertici*.
- Il colore del `pixel` viene calcolato come *combinazione lineare* dei colori dei ***vertici pesati dalle coordinate baricentriche***.
$$
\text{colore}(p)=\alpha_{0}\text{colore}(v_{1})+\alpha_{1}\text{colore}(v_{2})+\alpha_{2}\text{colore}(v_{3})
$$
![[ColorInterpolation.png]]

#### Convessità
>[!definizione]
>Un oggetto è ***convesso*** se e solo se comunque presi due punti nell'oggetto *tutti i punti sul segmento di linea* tra questi punti sono anche nell'oggetto.

![[Convexity.png]]

>[!help] Guscio Convesso

Dato un insieme di punti $P_{1},P_{2},\dots,P_{n}$, l'insieme di tutti i punti $P$ che possono essere rappresentati come combinazioni convesse è detto ***guscio convesso dell'insieme***.
- Il *guscio convesso* è la più piccola regione convessa che contiene **tutti** i punti dati.

### Distanze
#### Distanza tra due Punti
$$
\text{dist}(AB)=\|B-A\|=\sqrt{ <B-A,B-A> }=\sqrt{ (x_{B}-x_{A})^{2}+(y_{B}-y_{A})^{2} }
$$
#### Distanza tra un Punto e una Retta
> Bisogna cercare un punto $Q'$ tale che $(Q-Q')\perp v$.

![[DistancePoint-Vector.png]]

La distanza tra $Q$ e $l$ è uguale alla norma $\|Q-Q'\|$.
Utilizzando il *teorema di Pitagora*:
$$
L^{2}+\text{dist}(Q,Q')^{2}=\|Q-P_{0}\|^{2}
$$
- $L$ non è altro che la [[#Interpretazione Geometrica|proiezione ortogonale]] di $Q-P_{0}$ su $v$
$$
L=\displaystyle{\frac{<Q-P_{0},v>}{\|v\|}}
$$
Quindi ho che:
$$
\text{dist}(Q,Q')^{2}=\|Q-P_{0}\|- \displaystyle{\frac{<Q-P_{0},v>^{2}}{\|v\|^{2}}}
$$
### Forme Implicite
#### Equazione di una Linea in 2D
$$
Ax+By+C=0\quad A,B,C\in\mathbb{R}, AB\neq 0
$$

![[LineEquation.png]]

>[!caution] Intersezione Linea-Segmento

Un segmento $Q_{1}, Q_{2}$ interseca la linea se e solo se:
$$
(Ax_{1}+By_{1}+C)(Ax_{2}+By_{2}+C)\leq0
$$

#### Equazione di un Piano in 3D
> Un piano $\pi$ è definito da una normale $n$ ed un punto sul piano $(P_{0})$.

$$
Ax+By+Cz+D=0\quad A,B,C,D\in\mathbb{R}\quad ABC\neq 0
$$
![[PlaneEquation.png]]

Dove:
- $(x,y,z)$ sono le coordinate di un **punto** sul piano.
- $(A,B,C)$ sono le coordinate di un vettore **normale** al piano.

Un punto $Q$ appartiene al piano $\iff$ $<Q-P_{0},n>= 0$
- La normale $n$ è la *normale a tutti i vettori nel piano*.

>[!help] Distanza tra un Punto ed un Piano

>Bisogna proiettare il punto $Q$ sul *piano* nella direzione della normale.

$$
\text{dist}(Q,\pi) =\|Q'-Q\|
$$
$$
Q'-Q \parallel n \implies Q'-Q=sn ,\quad s\in\mathbb{R}
$$

***Quindi***
- $<Q'-P_{0},n> = 0$
- $<Q-P_{0}+sn,n> =0$
- $<Q-P_{0},n>+s<n,n>= 0$

Di conseguenza abbiamo che:
$$
s=-\displaystyle{\frac{<P_{0}-Q,n>}{\|n\|^{2}}}
$$
![[Point-Plane_Distance.png]]

In conclusione:
$$
\text{dist}^{2}(Q,\pi)=\| Q'-Q\|^{2}=s^{2}\|n\|^{2}=\displaystyle{\frac{<Q-P_{0},n>^{2}}{\|n\|^{2}}}
$$
