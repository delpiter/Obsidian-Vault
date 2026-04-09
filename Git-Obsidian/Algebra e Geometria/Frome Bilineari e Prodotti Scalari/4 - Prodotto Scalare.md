## I Prodotti Scalari
---
>[!info] Definizione
>Sia $V$ uno [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Spazio Vettoriale|spazio vettoriale]] su $\mathbb{K}=\mathbb{R}$
>Un ***prodotto scalare*** è una [[1 - Forme Bilineari#Forma Bilineare|forma bilineare]] [[1 - Forme Bilineari#Tipi di Forme Bilineari|simmetrica]] e [[3 - Forme Quadratiche#Tipi di Forme Quadratiche|definita positiva]]

#### Esempio
1. $V=\{ \text{ funzioni } [a,b]\to\mathbb{R} \}$

*Sia* $\beta(f,g)=\displaystyle\int_{a}^b f(t)\cdot g(t)\, dt$

>[!question] È un prodotto scalare?

- È ***bilineare*** e ***simmetrica***
>[!question] È definita positiva?

$$
f(t)=\begin{cases}
1\qquad \text{ se }t=\displaystyle{\frac{a+b}{2}} \\
0 \qquad \text{ altrimenti}
\end{cases}
$$
- $q(f)=\beta(f,f)=\displaystyle\int_{a}^b f(t)^2 \, dt=0$
 Quindi $q(f)=0$, ma $f\neq0$

>[!fail] $\beta$ non è definita positiva, $\beta$ non è un prodotto scalare

2. $U=\{ f:[a,b]\to \mathbb{R}, \text{ funzioni continue} \}$
*Sia* $\beta(f,g)=\displaystyle\int_{a}^b f(t)\cdot g(t)\, dt$

>[!question] È un prodotto scalare?

- Come prima è ***bilineare*** e ***simmetrica***
>[!question] È definita positiva?

Sia $f\neq 0$ allora $\exists p\in \mathbb{R}$
- Poiché $f$ è continua esiste un intorno di $p$ in cui $f(x)>0$ e quindi l'integrale ***deve essere positivo***
$$
\int _{a}^b f(t)^2 \, dt >0\implies q(f)>0\qquad \forall f\neq 0
$$
Per ciò, $\beta$ è ***definita positiva***

>[!done] $\beta$ è un prodotto scalare


### Prodotto Scalare Standard
>[!summary] Definizione
>Sia $V=\mathbb{R}^n \qquad v=(x_{1},\dots,x_{n}),\qquad u=(y_{1},\dots,y_{n})$
>E sia $\beta(v,u)=x_{1}y_{1}+\dots+x_{n}y_{n}=x^{T}y$
>>[!done] $\beta$ è un prodotto scalare detto ***prodotto scalare standard*** o *canonico*

La sua matrice nella base canonica $e_{1},\dots,e_{n}$ è: ^e3d996
$$
I_{n}=\begin{pmatrix}
1 & 0 & \dots & 0 \\
0 & 1 & \dots & 0 \\
\dots  & \dots & \dots & \dots\\
0 & 0 & \dots & 1
\end{pmatrix}
$$

### Notazione
>[!info] Semplificazione
>Sia $V$ uno [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Spazio Vettoriale|spazio vettoriale]] su $\mathbb{K=\mathbb{R}}$ e sia $\beta$ un [[#I Prodotti Scalari|prodotto scalare]] su $V$
>Invece di $\beta(v,u)$ scriveremo semplicemente $(v,u)$ o $<v,u>$ o $v\cdot u$
>Invece di $q(v)$ scriveremo $\mid\mid v \mid\mid^2$ cioè, definiamo la ***norma*** di $v$ o la ***lunghezza***
>$\mid\mid v\mid\mid=\sqrt{ (v,v) }$
>Diciamo che $\mid\mid v\mid\mid$ è un ***versore*** se $\mid\mid v\mid\mid =1$

### Vettori Ortogonali
>[!info] Definizione
>Diciamo che $v,u$ sono ***ortogonali*** se $(v,u)=0$

#### Vettori Ortonormali
>[!summary] Definizione
>Diciamo che un insieme di vettori $v_{1},\dots,v_{n}$ sono ***ortonormali*** se sono versori tra di loro ***ortogonali***, cioè se:
>$$\forall i,j \qquad (v_{i},v_{j})=\begin{cases} 1 \qquad \text{se } i=j \\ 0 \qquad \text{se } i\neq j \end{cases}$$

#### Base Ortonormale
>[!Teorema] 
>Sia $V$ uno [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Spazio Vettoriale|spazio vettoriale]] su $\mathbb{K}=\mathbb{R}$ con un prodotto scalare
><u>Allora</u>
>$\exists$ una base ***ortonormale*** rispetto a tale prodotto scalare

##### Dimostrazione
Per il [[2 - Diagonalizzare Forme Bilineari#Teorema di Sylvester|teorema di Sylvester]]
Poiché il ***prodotto scalare*** è una ***forma bilineare simmetrica***
- $\exists$ una base $v_{1},\dots,v_{n}$ in cui la matrice è
$$
\begin{pmatrix}
I_{p} \\
 & I_{r-p} \\
 &  & 0
\end{pmatrix}
$$
E poiché è definita positiva, la segnatura è $(n,0)$
- Cioè la matrice è $I_{n}$
- Dunque $(v_{i},v_{j})=(I_{n})_{ij}=\begin{cases}1 \qquad \text{se } i=j \\ 0 \qquad \text{se } i\neq j\end{cases}$

##### Legame tra Prodotto Scalare e Prodotto Scalare Standard
>[!abstract] Proprietà Vettori Ortonormali
>Il ***prodotto scalare*** di due vettori è uguale al prodotto [[#Prodotto Scalare Standard]] dei vettori delle loro coordinate rispetto ad una ***base ortonormale***

>[!caution] Dimostrazione

Sappiamo che se $\beta$ è una forma bilineare e $A$ è la sua matrice rispetto a $v_{1},\dots,v_{n}$ e se:
- $v=x_{1}v_{1}+\dots+x_{n}v_{n}$
- $u=y_{1}v_{1}+\dots+y_{n}v_{n}$

Dove $x_{i}$ e $y_{i}$ sono le [[../Basi dell'algebra/3 - Teoremi su Spazi Vettoriali#Teorema delle Coordinate|coordinate]]

<u>Allora</u>

$$
\beta(v,u)=(x_{1},\dots,x_{n})A\begin{pmatrix}
y_{1} \\
\dots \\
y_{n}
\end{pmatrix}
$$

Se $\beta$ è un ***prodotto scalare*** e $v_{1},\dots,v_{n}$ è una ***base ortonormale***

<u>Allora</u>

$$
A=I_{n}\implies (v,u)=(x_{1},\dots,x_{n})I_{n}\begin{pmatrix}
y_{1} \\
\dots \\
y_{n}
\end{pmatrix}=(x_{1},\dots,x_{n})\begin{pmatrix}
y_{1} \\
\dots \\
y_{n}
\end{pmatrix}= x_{1}y_{1}+x_{2}y_{2}+\dots+x_{n}y_{n}
$$

##### Proprietà

>[!abstract] Indipendenza Lineare
>Se $v_{1},\dots,v_{k}$ sono tra loro ***ortogonali***
><u>Allora</u>
>Sono [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Dipendenza Lineare|linearmente indipendenti]]

>[!caution] Dimostrazione

Sappiamo che $(v_{i},v_{j})=0 \quad \forall i\neq j$ e vogliamo mostrare che se:
- $a_{1}v_{1}+\dots+a_{k}v_{k}=\underline{0}$

<u>Allora</u>

$a_{1}=0,\dots,a_{k}=0$

In effetti $\forall i\in\{ 1,\dots,k \}$ dalla uguaglianza precedente, facendo il ***prodotto scalare***, ottengo:
$$
\begin{array}
\ (v_{i},a_{1}v_{1}+\dots+a_{k}v_{k})=(v_{i},\underline{0})=0 \\
a_{1}\cancelto{ 0 }{ (v_{i},v_{1}) }+\dots+a_{i}\underbrace{ (v_{i},v_{i}) }_{ \neq 0 }+\dots+a_{k}\cancelto{ 0 }{ (v_{i},v_{k}) } \\
\implies a_{i}(v_{i},v_{i})=0 \implies a_{i}=0 \forall i\in\{ 1,\dots,k \}
\end{array}
$$


###### Esempio Prodotto Scalare
Consideriamo la [[1 - Forme Bilineari#Forma Bilineare|forma bilineare]] su $\mathbb{R}^2$
- $v=(a_{1},a_{2}), \quad u=(b_{1},b_{2})$
$$
\beta(v,u)=a_{1}b_{1}+5a_{2}b_{2}+2a_{1}b_{2}+2a_{2}b_{1}
$$
>[!question] È un prodotto scalare?

Osserviamo che $\beta$ è ***bilineare*** e ***simmetrica***
- $\beta(u,v)=b_{1}a_{1}+5b_{2}a_{2}+2b_{2}a_{1}+2b_{1}a_{2}$
>[!question] È definita positiva?

Nella base $e_{1},e_{2}$ $\beta$ ha la matrice:$\begin{pmatrix}1 & 2 \\2 & 5\end{pmatrix}$
Ponendo $v_{1}=e_{1}$ e $v_{2}=e_{2}-2e_{1}=(-2,1)$
In modo che:
- $\beta(v_{1},v_{2})=\beta(e_{1},e_{2})-2\beta(e_{1},e_{2})=2-2=0$
- $\beta(v_{2},v_{2})=4\beta(e_{1},e_{1})+\beta(e_{2},e_{2})-4\beta(e_{1},e_{2})=4+5-4(2)=1$

La matrice di $\beta$ nella base $v_{1},v_{2}$ è $\begin{pmatrix}1 & 0 \\0 & 1\end{pmatrix}$
- La segnatura di $\beta$ è $(2,0)$
- Cioè $\beta$ è ***definita positiva***

>[!done] $\beta$ è un prodotto scalare

E $v_{1}=(1,0),v_{2}=(-2,1)$ è una base ortonormale rispetto a $\beta$

>[!summary] Notiamo che ad esempio se $v=(-1,1)$ e $u=(3,1)$

$$
\beta(v,u)=-1(3)+5(1)(1)+2(-1)(1)+2(1)(3)=6
$$
Mettendo i vettori come ***combinazione lineare della base ottenuta prima***:
- $v=v_{1}+v_{2}$
	- *Coordinate* $(1,1)$
- $u=5v_{1}+v_{2}$
	- *Coordinate* $(5,1)$

$$
(1,1)I_{2}\begin{pmatrix}
5 \\
1
\end{pmatrix}=1\cdot 5+1\cdot 1=6
$$

### Disuguaglianza di Cauchy-Schwarts
>[!info] Definizione
>Sia $V$ uno [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Spazio Vettoriale|spazio vettoriale]] su $\mathbb{K}=\mathbb{R}$ e consideriamo un prodotto scalare su $V$
>>[!abstract] Proposizione
>>$$\mid (v,u)\mid\leq\mid\mid v\mid\mid \cdot \mid\mid u \mid\mid$$
>>- $\forall v,u\in V$
>
>L'uguaglianza vale $\iff$ $v,u$ sono linearmente dipendenti
>Di conseguenza, $\forall v,u\in V$
>- $\displaystyle{\frac{\mid(v,u)\mid}{\mid\mid v \mid\mid \cdot\mid\mid u\mid\mid}}\leq1$
>
>Cioè
>$$-1\leq\displaystyle{\frac{(v,u)}{\mid\mid v \mid\mid \cdot \mid\mid u\mid\mid}}\leq1$$


#### Angolo Convesso
>[!info] Definizione
>Definisco l'***Angolo Convesso*** tra $v$ e $u$ come:
>$$\arccos\left( \displaystyle{\frac{(v,u)}{\mid\mid v \mid\mid\cdot\mid\mid u\mid\mid}} \right) $$

Quindi un prodotto scalare ci permette di misurare non solo la lunghezza dei vettori, ma anche gli ***angoli che essi formano fra loro***

#### Distanza Euclidea
>[!tldr] Definizione
>Il prodotto scalare ci permette anche di definire la ***distanza euclidea*** tra due punti $P,Q\in V$
>$$d(P,Q)=\mid\mid \overrightarrow{PQ}\mid\mid$$

##### Esempio
>$P=(3,1) \quad Q=(5,0)$

- $\overrightarrow{PQ}=(5-3,0-1)=(2,-1)$

Rispetto al [[#Prodotto Scalare Standard]]:
$$
d(P,Q)=\sqrt{ ((2,-1),(2,-1)) }=\sqrt{ 5 }
$$
Rispetto al prodotto scalare dell'[[#Esempio Prodotto Scalare|esempio]] precedente:
$$
d(P,Q)=\sqrt{ \beta((2,-1),(2,-1)) }=\sqrt{ 4+5-4-4 }=1
$$


##### Proprietà
>[!abstract] Consideriamo un prodotto scalare su $V$ e la distanza euclidea ad essa associata
>La ***distanza euclidea*** ha le seguenti proprietà
>1. $d(P,Q)\geq 0$ e $d(Q,P)=0 \iff P=Q$
>2. $d(P,Q)=d(Q,P) \qquad \forall P,Q\in V$
>3. $d(P,Q)\leq d(P,R)+d(R,Q)\quad \forall P,Q,R \in V$
>>[!done] Anche detta ***disuguaglianza triangolare***

###### Dimostrazione
>1.

Poiché un prodotto scalare è [[3 - Forme Quadratiche#Tipi di Forme Quadratiche|definito positivo]]
$$
(\overrightarrow{PQ},\overrightarrow{PQ})\geq 0  
$$
e
$$
\text{vale l'uguaglianza}\iff \overrightarrow{PQ}=\underline{0} \text{ cioè }P=Q
$$

>2.

Osserviamo che se $a\in\mathbb{R},\mid\mid av\mid\mid = \sqrt{ (av,av) }=\mid a\mid \sqrt{ (v,v) }=\mid a\mid\cdot\mid\mid v \mid\mid$
- In particolare, per $a=-1$
$$
d(P,Q)=\mid\mid \overrightarrow{PQ} \mid\mid =\mid\mid -\overrightarrow{QP}\mid\mid= \mid-1\mid \cdot\mid\mid QP\mid\mid = \mid\mid QP\mid\mid=d(Q,P)
$$

>3.

Osserviamo che se $v,w\in V$
$$
\mid\mid v+w\mid\mid\leq\mid\mid v\mid\mid+\mid\mid w \mid\mid
$$
Perché:
$$
\mid\mid v+w \mid\mid^2 = (v+w,v+w)=(v,v)+(w,w)+\underbrace{ 2(v,w) }_{ \leq  2\mid\mid v\mid\mid\cdot\mid\mid w \mid\mid}\leq\mid\mid v\mid\mid^2+\mid\mid w\mid\mid^2+2\mid\mid v\mid\mid\cdot\mid\mid w\mid\mid=
$$
$$
=(\mid\mid w\mid\mid +\mid\mid v \mid\mid)^2
$$

In particolare per $v=\overrightarrow{PR}$ e $w=\overrightarrow{RQ}$
- $v+w=\overrightarrow{PR}+\overrightarrow{RQ}\leq \overrightarrow{PQ}$

