>*Abbiamo visto che se $f,g$ sono [[1 - Applicazioni Lineari#Applicazione Lineare|lineari]], anche la loro composizione $g_{o}f$ è lineare*

>[!question] Che relazione c'è fra la matrice di $g_{o}f$ e le matrici di $g$ e $f$?

## Prodotto Riga $\times$ Colonna
---
>[!info] Introduzione
>Siano $V,U,W$ spazi vettoriali su $\mathbb{K}$ con [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Base|basi]]:
>$(v_{1},\dots,v_{n}),(u_{1},\dots,u_{m}),(w_{1},\dots,w_{l})$
>E siano $f:V\to U$ e $g:U\to W$ [[1 - Applicazioni Lineari#Applicazione Lineare|applicazioni lineari]]
>Sia $A$ la matrice di $f$ e $B$ la matrice di $g$ in tali basi
>>[!tip] Vogliamo calcolare la matrice dell'applicazione lineare $g_{o}f_:V\to W$
>
>$f(v_{i})=\displaystyle\sum_{j=1}^ma_{ji}u_{j}$
>$g(u_{j})=\displaystyle\sum_{h=1}^lb_{hj}w_{h}$
>$$(g_{o}f)(v_{i})=g\left( \sum_{j=1}^ma_{ji}u_{j} \right)=\sum_{j=1}^ma_{ji}g(u_{j})=\sum_{j=1}^m\sum_{h=1}^la_{ji}b_{hj}w_{h}$$

Il coefficiente di $w_{h}$ in questa somma è:
$$
\sum_{j=1}^ma_{ji}b_{hj}
$$
Abbiamo scoperto che la *matrice* di $g_{o}f$ in *tali basi* è la matrice che ha,
- Alla $h$-esima ***riga*** e $i$-esima ***colonna***, il numero

>[!definizione] Prodotto Riga $\times$ Colonna
>Definiamo "*prodotto riga $\times$ colonna di $B$ e $A$*"
>come la matrice $BA$ che ha come elemento
>$(BA)_{hi}$ il numero:
>$$\sum_{j\in\{ 1,\dots,m \}}b_{hj}a_{ji}$$
>>[!done] A parole
>>Abbiamo scoperto che la *matrice* di $g_{o}f$ in *tali basi* è la matrice che ha,
>>alla $h$-esima ***riga*** e $i$-esima ***colonna***, il numero descritto dalla *sommatoria*

### Esempio
>*Sia* $V=U=W$ *con base* $e_{1}=(1,0),e_{2}=(0,1)$ *e* $g(x,y)=(2x-y,-x+3y),f(x,y)=(5x+2y,-2x+y)$

Troviamo le matrici di $g$ e $f$
- $g(e_{1})=(2-0,-1+0)=(2,-1)$
- $g(e_{2})=(0-1,-0+3)=(-1,3)$
- $f(e_{1})=(5+0,-2+0)=(5,-2)$
- $f(e_{2})=(0+2,-0+1) = (2,1)$

Otteniamo così le *matrici*:
$$
\text{matrice di }g\to B=\begin{pmatrix}
2 & -1 \\
-1 & 3
\end{pmatrix},
\text{matrice di }f\to A=\begin{pmatrix}
5 & 2 \\
-2 & 1
\end{pmatrix}
$$
Ora facciamo il prodotto *riga* $\times$ *colonna* $B\times A$
$$
BA=\begin{pmatrix}
2 & -1 \\
-1 & 3
\end{pmatrix}\times
\begin{pmatrix}
5 & 2 \\
-2 & 1
\end{pmatrix}
=\begin{pmatrix}
2\cdot5+(-1)\cdot(-2) & 2\cdot2+(-1)\cdot(1) \\
(-1)\cdot5+3\cdot(-2) & (-1)\cdot2+3\cdot 1
\end{pmatrix}=
$$
- Ottenendo così la *matrice*:
$$
\begin{pmatrix}
12 & 3 \\
-11  & 1
\end{pmatrix}
$$
> Ora controlliamo:

$$
\begin{array}
\ (g_{o}f)(x,y)=g(5x+2y,-2x+y) \\
=(2(5x+2y)-(2x+y),-(5x+2y)+3(-2x+y))= \\
=(12x+3y,-11x+y)
\end{array}
$$


## Matrice Identità
---
>*Consideriamo l'applicazione $id:V\to V,v\mapsto v$, cioè $id(v)=v\quad\forall v \in V$*

>[!question] Qual è la sua matrice?

Fissiamo una [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Base|base]] $v_{1},\dots,v_{n}$ di $V$
- $id(v_{1})=v_{1}=1v_{1}+0v_{2}+\dots+0v_{n}$
- $id(v_{2})=v_{2}=0v_{1}+1v_{2}+\dots+0v_{n}$
- $\dots$
- $id(v_{n})=v_{n}=0v_{1}+0v_{2}+\dots+1v_{n}$

>[!done] Matrice Identità

Chiamiamo la seguente matrice la ***matrice identità***, e la indichiamo con $\text{I}_{n}$
$$
\begin{pmatrix}
1 & \dots & 0 \\
\vdots & \ddots & \vdots \\
0 & \dots & 1
\end{pmatrix}
$$

### Osservazioni

>[!tldr] Osservazione 1
>La matrice di $id$ è $I_{n}$ qualsiasi sia la base scelta per $V$

---

>[!tldr] Osservazione 2
>Per ogni $f:V\to V$, la composizione tra $f$ e la funzione identità $id$ è uguale a $f$
>$$id_{o}f=f,f_{o}id=f$$
>Perché $id(f(v))=f(v)$ e $f(id(v))=f(v)$

Quindi, se $f$ è [[1 - Applicazioni Lineari#Applicazione Lineare|lineare]] e, fissata una base di $V$, $A$ è la sua matrice
<u>Allora</u>
$$
A\times I_{n}=A, I_{n}\times A=A
$$

>[!done] $I_{n}$ è l'***elemento neutro*** rispetto al prodotto riga per colonna

---

>[!tldr] Osservazione 3
>Un'[[1 - Applicazioni Lineari#Applicazione Lineare|applicazione lineare]] $f:V\to U$ è un [[4 - Isomorfismo#Isomorfismo|isomorfismo]] $\iff$ è invertibile,
>Cioé:
>$$\exists f^{-1}:U\to V$$
>Tale che $f_{o}f^{-1}=id_{u}$ e $f^{-1}_{o}f=id_{v}$
>>[!done] In altre parole
>>Se $A$ è la matrice di $f$ in una base $v_{1},\dots,v_{n}$ di $V$
>><u>Allora</u>
>>$f$ è ***invertibile*** $\iff A$ è "***invertibile***"
>>Cioè esiste una matrice $A^{-1}$ tale che $A\times A^{-1} = I_{n}$, $A^{-1}\times A = I_{n}$
>>- $A^{-1}$ è la matrice di $f^{-1}$

---

>[!tldr] Osservazione 4
>Se $\text{dim}(V)\neq \text{dim}(U)$ sappiamo, come [[2 - Teorema del Rango#Conseguenze del Teorema del Rango|conseguenza del teorema del rango]], che ***non esistono isomorfismi*** da $V$ a $U$
>Quindi solo le matrici quadrate ***possono essere invertibili***

>[!done] Se il numero di *righe* di $A$ è diverso dal numero di *colonne*, sicuramente $A$ non è *invertibile*

#### Domanda
>[!question] Se invece $A\in \mathcal{M}_{n,n}=\{ \text{matrici }n\times n \}$, ha senso chiedersi: *è invertibile*?

Cioè, esiste una matrice, che chiamerò $A^{-1}$, tale che $A\times A^{-1}=I_{n}$,$A^{-1}\times A = I_{n}$?

