## Forma Bilineare
---
>[!info] Definizione
>Sia $\mathbb{K}$ un [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Campo|campo]] e $V$ uno [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Spazio Vettoriale|spazio vettoriale]] su $\mathbb{K}$
>Una ***forma bilineare*** su $V$ è un'applicazione $\beta$:
>$$\begin{array}\ V\times V \to \mathbb{K} \\ (v,u)\mapsto \beta(v,u) \end{array}$$
>Che è [[../Applicazioni/1 - Applicazioni Lineari#Applicazione Lineare|lineare]] in ciascuno degli argomenti
>>[!done] In Breve
>>$\forall v,v',u,u'\in V, \forall a\in\mathbb{K}$
>>1. $\beta(v+v',u)=\beta(v,u)+\beta(v',u)$
>>2. $\beta(v,u+u')=\beta(v,u)+\beta(v,u')$
>>3. $\beta(av,u)=a\beta(v,u)=\beta(v,au)$

#### Eesempio
>$V=\mathbb{R}^2,\mathbb{K}=\mathbb{R}, v=(x_{1},x_{2}), u=(y_{1},y_{2})$

$$
\beta(v,u)=2x_{1}y_{1}+x_{1}y_{2}+3x_{2}y_{1}-x_{2}y_{2}
$$
>[!quesiton] $\beta$ è lineare?

>*Sia $v'=(x_{1}',x_{2}')$*

>[!abstract] Somma

$$
\begin{array}
\ \beta(v+v',u)=\beta((x_{1}+x_{1}',x_{2}+x_{2}'),(y_{1},y_{2}))= \\
=2(x_{1}+x_{1}')y_{1}+(x_{1}+x_{1}')y_{2}+2(x_{2}+x_{2}')y_{1}(x_{2}+x_{2}')y_{2} = \\
\beta(v,u)+\beta(v',u)
\end{array}
$$
- Analogo per il ***secondo vettore***

>[!abstract] Prodotto

$$
\begin{array}
\ \beta(av,u)=\beta((ax_{1},ax_{2}),(y_{1},y_{2}))= \\
=2ax_{1}y_{1}+ax_{1}y_{2}+3ax_{2}y_{1}-ax_{2}y_{2}= \\
=a(2x_{1}y_{1}+x_{1}y_{2}+3x_{2}y_{1}-x_{2}y_{2}) = a\beta(v,u)
\end{array}
$$
- Analogamente si mostra $\beta(v,au)$

>[!done] $\beta$ è *bilineare*


#### Esempio
>*Sia $V=\mathbb{R}^2$,  $\mathbb{K}=\mathbb{R}$,  $v=(x_{1},x_{2})$,  $u=(y_{1},y_{2})$*

$$
\beta(v,u)=x_{1}x_{2}+y_{1}y_{2}
$$
>[!abstract] Prodotto

$$
\begin{array}
\ \beta(av,u)=(ax_{1})(ax_{2})+y_{1}y_{2}=a^2x_{1}x_{2}+y_{1}y_{2}\neq \\
\neq ax_{1}x_{2}+ay_{1}y_{2}=a\beta(v,u)
\end{array}
$$

>[!fail] $\beta$ non è bilineare

## Tipi di Forme Bilineari
---
>[!info] Simmetrica
>Una [[#Forma Bilineare]] $\beta$ su $V$ è ***simmetrica*** se:
>$$\beta(v,u)=\beta(u,v)$$
>$\forall v,u\in V$

>[!info] Antisimmetrica
>Una [[#Forma Bilineare]] $\beta$ su $V$ è ***antisimmetrica*** se:
>$$\beta(v,u)=-\beta(u,v)$$
>$\forall v,u\in V$

#### Esempi
>*Sia $V=\mathbb{R}^2$, $v=(x_{1},x_{2})$, $u=(y_{1},y_{2})$*

>[!summary] 1. $\beta_{1}(v,u)=2x_{1}y_{1}-3x_{1}y_{2}-3x_{2}y_{1}+4x_{2}y_{2}$

- $\beta_{1}(u,v)=2x_{1}y_{1}-3x_{2}y_{1}-3x_{1}y_{2}+4x_{2}y_{2}$

>[!caution] Simmetrica

>[!summary] 2. $\beta_{2}(v,u)=x_{1}y_{2}-x_{2}y_{1}$

- $\beta_{2}(u,v)=y_{1}x_{2}-y_{2}x_{1}=-\beta_{2}(v,u)$

>[!attention] Antisimmetrica

>[!summary] 3. $\beta(v,u)=2x_{1}y_{2}-3x_{2}y_{1}$

- $\beta((1,0),(1,1))=2$
- $\beta((1,1),(1,0))=-3$

>[!fail] Ne *simmetrica* ne *antisimmetrica*

>[!summary] 4. Può esistere una forma sia simmetrica che antisimmetrica?

- $\beta(v,u)\underset{ S }{ = } \beta(u,v)\underset{ A }{ = }-\beta(v,u)$
$$
\beta(v,u)=0 ,\ \ \ \ \ \ \forall v,u \in V
$$
>[!done] Esiste ma è unicamente $\beta=0$

### Osservazione
>[!abstract] Oss
>Ogni forma ***bilineare*** si può scrivere come somma di una forma ***bilineare simmetrca*** $\beta_{S}$ e di una ***forma bilineare antisimmetrica*** $\beta_{A}$
>$$\beta_{S}(v,u)=\displaystyle{\frac{\beta(v,u)+\beta(u,v)}{2}}$$
>$$\beta_{A}(v,u)=\displaystyle{\frac{\beta(v,u)-\beta(u,v)}{2}}$$
>$$\beta=\beta_{S}+\beta_{A}$$

## Matrice di Forme Bilineari
---
>[!info] Definizione
>Sia $\beta$ una ***forma bilineare*** su $V$ e sia $v_{1},\dots v_{n}$ una base di $V$
>Dati $v,u\in V$ scriviamo $v=a_{1}v_{1}+\dots+a_{n}v_{n}$, $\quad u=b_{1}v_{1}+\dots+b_{n}v_{n}$
>Con $a_{i}\in\mathbb{K}$ e $b_{i}\in\mathbb{K}$
>>[!abstract] Possiamo Dire:
>>$$\beta(v,u)=\beta(a_{1}v_{1}+\dots+a_{n}v_{n},b_{1}v_{1}+\dots+b_{n}v_{n})$$
>>$$\begin{array}\ \underset{ L^1 }{ =}a_{1}\beta(v_{1},b_{1}v_{1}+\dots+b_{n}v_{n})+\dots+a_{n}\beta(v_{n},b_{1}v_{1}+\dots+b_{n}v_{n})= \\ \underset{ L^2 }{ = }a_{1}b_{1}\beta(v_{1},v_{1})+\dots+a_{1}b_{n}\beta(v_{1},v_{n})+\dots+
a_{n}b_{1}\beta(v_{n},v_{1})+\dots+a_{n}b_{n}\beta(v_{n},v_{n})\end{array}$$
>>Che è come dire:
>>$$\sum_{i,j=1}^n a_{i}b_{j}\beta(v_{i},v_{j})$$
>
>>[!done] Morale
>>Per conoscere quanto fa $\beta$ su una ***qualsiasi coppia di vettori***, mi basta sapere quanto fa ***ogni coppia di vettori*** nella base di $V$

>[!info] Definizione
>La ***matrice*** della ***forma bilineare*** nella base $v_{1},\dots,v_{n}$ è la matrice $A$:
>$$A_{i,j}=\beta(v_{i},v_{j})$$
>*$i$-esima riga e $j$-esima colonna*

>[!abstract] Osservazione

>*Se $v=a_{1}v_{1}+\dots+a_{n}v_{n}$ e $u=b_{1}v_{1}+\dots+b_{n}v_{n}$*

$$
\beta(v,u)=(a_{1},\dots,a_{n})A\begin{pmatrix}
b_{1} \\
\dots \\
b_{n}
\end{pmatrix}=\sum a_{i}b_{j}A_{ij}=\sum a_{i}b_{j}\beta(v_{i},v_{j})
$$
#### Esempio
>*Sia* $v_{1}=(1,1),v_{2}=(1,-1)$ *base di* $V=\mathbb{R}^2$

$$
\beta(v,u)=x_{1},y_{1}+2x_{1}y_{2}-x_{2}y_{1}+3x_{2}y_{2}
$$
>[!question] Qual è la matrice di $\beta$ nella base data?

- $\beta(v_{1},v_{1})=5$
- $\beta(v_{1},v_{2})=-5$
- $\beta(v_{2},v_{1})=1$
- $\beta(v_{2},v_{2})=3$

>[!done] $$A=\begin{pmatrix} 5 & -5 \\ 1 & 3\end{pmatrix}$$

>[!question] Trovare il valore di $\beta(v,u)$ con $v=(2,0), u=(3,1)$

- $v=v_{1}+v_{2}$
- $u=2v_{1}+v_{2}$

$$
\beta(v,u)=\underset{ \text{ Coordinate di } v }{ (1,1) }\begin{pmatrix}
5 & -5 \\
1 & 3
\end{pmatrix}\underset{ \text{Coordinate di } u }{ \begin{pmatrix}
2 \\
1
\end{pmatrix} }=(6,-2)\begin{pmatrix}
2 \\
1
\end{pmatrix}=12-2=10
$$
## Matrici Simmetriche e Antisimmetriche
---
>[!info] Matrici Simmetriche
>Una matrice $A$ è ***simmetrica*** se
>$$A_{ij}=A_{ji}\ \ \ \ \forall i$$
>>[!done] Ovvero
>>Una matrice è ***simmetrica*** se $A^T=A$

>[!info] Matrici Antisimmetriche
>Una matrice $A$ è ***antisimmetrica*** se
>$$A_{ij}=-A_{ji}\ \ \ \ \forall i$$
>>[!done] Ovvero
>>Una matrice è ***antisimmetrica*** se $A^T=-A$

#### Esempio
$$
A_{1}=\begin{pmatrix}
3 & 4 \\
4 & 2
\end{pmatrix}
$$
- È una ***matrice simmetrica***
$$
A_{2}=\begin{pmatrix}
0 & -3  \\
3 & 0
\end{pmatrix}
$$
- È una ***matrice antisimmetrica***
$$
A_{3}=\begin{pmatrix}
2 & 3 \\
-1 & 1
\end{pmatrix}
$$
- Non è ne ***simmetrica*** ne ***antisimmetrica***


### Osservazione
>[!abstract] ‎ 
>Una forma bilineare $\beta$ è ***simmetrica*** (o ***antisimmetrica***)$\iff$ la sua matrice in una base qualsiasi è ***simmetrica*** (o ***antisimmetrica***)

### Matrici Congruenti
>[!info] Definizione
>Due matrici $A,M$ sono ***congruenti*** se
>$\exists$ una matrice invertibile $B:M=B^TAB$
>>[[../Basi dell'algebra/1 - Introduzione#Relazione di Equivalenza|relazione di equivalenza]]

>[!Teorema]
>Due matrici $A,M$ sono congruenti $\iff$ rappresentano la ***stessa forma bilineare*** in basi diverse

#### Dimostrazione
Siano $\mathcal{B}=\{ v_{1},\dots,v_{n} \}$ e $\mathcal{B'}=\{ u_{1},\dots,u_{n} \}$ basi di $V$

>[!abstract] Consideriamo $2$ vettori $v,u\in V$

- $v=a_{1}v_{1}+\dots+a_{n}v_{n}=x_{1}u_{1}+\dots+x_{n}u_{n}$
- $u=b_{1}v_{1}+\dots+b_{n}v_{n}=y_{1}u_{1}+\dots+y_{n}u_{n}$

Sia $B$ la ***matrice del cambiamento*** di base, cioè:
$$
\begin{pmatrix}
a_{1} \\
\dots \\
a_{n}
\end{pmatrix}=B\begin{pmatrix}
x_{1} \\
\dots \\
x_{n}
\end{pmatrix}, \begin{pmatrix}
b_{1} \\
\dots \\
b_{n}
\end{pmatrix}=B\begin{pmatrix}
y_{1} \\
\dots \\
y_{n}
\end{pmatrix}
$$
$$
\beta(v,u)=(a_{1},\dots,a_{n}) A\begin{pmatrix}
b_{1} \\
\dots \\
b_{n}
\end{pmatrix}
$$
Ma $(a_{1},..,a_{n})$ non è altro che:
$$
\left( B\begin{pmatrix}
x_{1} \\
\dots \\
x_{n}
\end{pmatrix} \right)^T =(x_{1},\dots,x_{n})B^T
$$
E $\begin{pmatrix}b_{1} \\ \dots \\ b_{n} \end{pmatrix}$ non è altro che:
$$
B\begin{pmatrix}y_{1} \\ \dots \\ y_{n} \end{pmatrix}
$$
Quindi ho che:
$$
\beta(v,u)=(x_{1},\dots,x_{n})\underbrace{ B^TAB }_{ M }\begin{pmatrix}y_{1} \\ \dots \\ y_{n} \end{pmatrix}
$$
>[!done] ‎In *conclusione*
>$$(x_{1},\dots,x_{n})M\begin{pmatrix}y_{1} \\ \dots \\ y_{n} \end{pmatrix}$$