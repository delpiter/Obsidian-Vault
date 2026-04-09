## Forma Quadratica
---
>[!info] Definizione
>Sia $V$ uno [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Spazio Vettoriale|spazio vettoriale]] su $\mathbb{K}$ e $\beta$ una [[1 - Forme Bilineari#Forma Bilineare|forma bilineare]] [[1 - Forme Bilineari#Tipi di Forme Bilineari|simmetrica]] su $V$
>La ***forma quadratica*** associata a $\beta$ è $q:V\to\mathbb{K}$
>$$q(v)=\beta(v,v) \qquad \forall v \in V$$
>>[!tip] Osservazione
>>***Non*** c'è alcuna ***perdita di informazione***
>>Data $q$ posso ricostruire $\beta$, perché 
>>$q(v+u)-q(v)-q(u)=\beta(v+u,v+u)-\beta(v,v)-\beta(u,u)=$
>>$=\beta(v,v)+\beta(u,u)+2\beta(v,u)-\beta(v,v)-\beta(u,u)$
>>$\implies \beta(v,u)=\displaystyle{\frac{q(v+u)-q(v)-q(u)}{2}}$

### Osservazioni
>[!abstract] Osservazione 1
>Si chiama forma quadratica perché $\forall a \in\mathbb{K}$
>$$q(av)=\beta(av,av)=a^2\beta(v,v)=a^2p(v)$$

>[!todo] Osservazione 2
>Se $q$ è una forma quadratica,
>$$q(\underline{0})=\beta(\underline{0},\underline{0})=0$$
#### Esempio
>*Sia $V=\mathbb{R}^2 \qquad v=(x_{1},x_{2}),u=(y_{1},y_{2})$*

$$
\beta(v,u)=2x_{1}y_{1}+3x_{1}y_{2}+3x_{2}y_{1}-x_{2}y_{2}
$$
>[!caution] La forma quadratica associata a $\beta$ è

$$
q(v)=\beta(v,v)=2x_{1}^2+6x_{1}x_{2}-x_{2}^2
$$
## Tipi di Forme Quadratiche
---
>[!info] Definizione
>Sia $V$ uno [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Spazio Vettoriale|spazio vettoriale]] su $\mathbb{R}$, $\beta$ una [[1 - Forme Bilineari#Forma Bilineare|forma bilineare]] [[1 - Forme Bilineari#Tipi di Forme Bilineari|simmetrica]] su $V$ e sia $q$ la ***forma quadratica*** associata a $\beta$
>>[!abstract] $1.$
>>$q$ è ***definita positiva*** se $q(v)>0 \qquad \forall v\neq \underline{0}, v\in V$
>
>>[!example] $2.$
>>$q$ è ***definita negativa*** se $q(v)<0 \qquad \forall v\neq \underline{0}, v\in V$
>
>>[!abstract] $3.$
>>$q$ è ***semidefinita positiva*** se $q(v)\geq0 \qquad\forall v\in V$
>
>>[!example] $4.$
>>$q$ è ***semidefinita negativa*** se $q(v)\leq0 \qquad\forall v\in V$
>
>>[!danger] $5.$
>>$q$ è ***indefinita*** se $\exists v_{1},v_{2}\in V:q(v_{1})>0,q(v_{2})<0$

#### Esempio
>$V=\mathbb{R}^2 \qquad \mathbb{K=\mathbb{R}} \qquad v=(x_{1},x_{2})$

1. $q(v)=x_{1}^2+x_{2}^2$

 È ***definita positiva*** perché $x_{1}^2+x_{2}^2>0\quad\forall(x,y)\neq(0,0)$

2. $q(v)=-x_{1}^2-x_{2}^2$

 È ***definita negativa*** perché $-x_{1}^2-x_{2}^2<0\quad\forall(x,y)\neq(0,0)$

3. $q(v)=x_{1}^2$

È ***semidefinita positiva*** perché $x_{1}^2\geq 0 \forall v=(x_{1},x_{2})$
- Ma per esempio il vettore $(0,3)$ è un ***vettore non nullo*** su cui $q$ vale $0$

4. $q(v)=-x_{1}^2$

È ***semidefinita negativa*** perché $-x_{1}^2\leq 0 \forall v=(x_{1},x_{2})$
- Ma per esempio il vettore $(0,3)$ è un ***vettore non nullo*** su cui $q$ vale $0$

5. $q(x_{1},x_{2})=x_{1}^2-x_{2}^2$

È ***indefinita*** perché ad esempio:
- $q(e_{1})=1>0$
- $q(e_{2})=-1<0$


### Relazione con la Matrice Diagonale
>[!info] ‎ 
>>[!abstract] $1.$
>>$q$ è ***definita positiva*** $\iff$ la [[2 - Diagonalizzare Forme Bilineari#Teorema di Sylvester|segnatura]] di $\beta$ è $\underbrace{ (n,0) }_{ \text{"solo 1"} }$
>>- $\exists$ una base in cui la matrice di $\beta$ è $I_{n}$
>
>>[!example] $2.$
>>$q$ è ***definita negativa*** $\iff$ la [[2 - Diagonalizzare Forme Bilineari#Teorema di Sylvester|segnatura]] di $\beta$ è $\underbrace{ (0,n) }_{ \text{"solo -1"} }$
>>- $\exists$ una base in cui la matrice di $\beta$ è $-I_{n}$
>
>>[!abstract] $3.$
>>$q$ è ***semidefinita positiva*** $\iff$ la [[2 - Diagonalizzare Forme Bilineari#Teorema di Sylvester|segnatura]] di $\beta$ è $\underbrace{ (r,0) }_{ \text{"1 e 0"} }\qquad r<n$
>
>>[!example] $4.$
>>$q$ è ***semidefinita negativa*** $\iff$ la [[2 - Diagonalizzare Forme Bilineari#Teorema di Sylvester|segnatura]] di $\beta$ è $\underbrace{ (0,r) }_{ \text{"-1 e 0"} }\qquad r<n$
>
>>[!danger] $5.$
>>$q$ è ***indefinita*** $\iff$ la [[2 - Diagonalizzare Forme Bilineari#Teorema di Sylvester|segnatura]] di $\beta$ è $(p,r-p)$ con $p>0,r-p>0$

#### Esempio
>*Sia $f:\mathbb{R}^n\to\mathbb{R}$ una funzione di $n$ variabili, derivabile $2$ volte*

Dato $v\in\mathbb{R}^n$ definiamo l'***Hessiana*** di $f(v)$ come $Hf(v)$
Come la matrice:
$$
Hf(v)_{ij}=\displaystyle{\frac{\partial f}{\partial x_{i}}\left( \frac{\partial f}{\partial y_{i}} \right)(v) }
$$
- *Se le derivate seconde sono continue, è una* ***matrice simmetrica***

>[!info] Serve per capire la natura dei punti critici

- Se $Hf(v)$ è ***definita positiva*** $\implies$ il punto $v$ è un ***punto di minimo***
- Se $Hf(v)$ è ***definita negativa*** $\implies$ il punto $v$ è un ***punto di massimo***
- Se $Hf(v)$ è ***indefinita*** $\implies$ il punto $v$ è un ***punto di sella***