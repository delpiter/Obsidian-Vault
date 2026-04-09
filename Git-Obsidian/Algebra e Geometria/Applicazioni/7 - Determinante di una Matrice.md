>[!question] Una matrice $A, n\times n$, è invertibile?

>[!tldr] Idea
>Si crea una "***funzione test***" che ad ogni matrice associa un numero
>- Se questo numero è $=0$ allora $A$ non è ***invertibile***
>- Se questo numero è $\neq 0$ allora $A$ è ***invertibile***

>*Questa funzione si chiama* ***determinante***

## Determinante
---
>[!info] Definizione
>Data una matrice $A\in \mathcal{M}_{n\times n}(\mathbb{K})$
>Il ***determinante*** di $A$ è definito nel seguente modo *ricorsivo*
>>[!abstract] ‎ 
>>- Se $n=1$, $A=(a_{11}) \implies \det(A)=a_{11}$
>>- Se $n>1$, riduciamo il calcolo del *determinante* di $A$ al *determinante* di matrici più piccole mediante la regola di ***Laplace***
>>$$\det(A)=\sum_{i=1}^n(-1)^{i+j}\cdot a_{ij}\cdot \det(A^{ij})$$
>>Dove $A^{ij}$ è la *matrice* ottenuta rimuovendo l'$i$-esima riga e la $j$-esima colonna

###  Proprietà
>*Abbiamo così definito ricorsivamente una funzione*

$$
\det:\mathcal{M}_{n\times n}(\mathbb{K})\to \mathbb{K}
$$
$$
A\mapsto \det(A)
$$
Questa funzione ha le ***seguenti proprietà***

>[!Proprietà 1]
>Il *determinante* è una funzione ***alternante***
>- Se scambio due colonne qualsiasi tra di loro il determinante ***cambia segno***
>$$\det(A')=-\det(A)$$

>[!done] In particolare
>Il risultato di Laplace non dipende dalla colonna scelta

>[!Proprietà 2]
>Il *determinante* è ***multilineare***
>- Se ho due matrici che differiscono per ***una sola colonna***
>$$A=(v_{1},\dots,v_{i},\dots,v_{n}),B=(v_{1},\dots,v_{i'},\dots,v_{n})$$
><u>Allora</u>
>$$\det(v_{1},\dots,av_{i}+b_{vi'},\dots,v_{n})=a\det(A)+b\det(B),\quad a,b\in \mathbb{K}$$

>[!Proprietà 3]
>Il *determinante* della [[5 - Matrici di Applicazioni Lineari#Matrice Identità|matrice identità]] è $1$
>$$\det(I_{n})=1$$

>[!Proprietà 4]
>Il *determinante* è l'unica funzione $\mathcal{M}_{n\times n}(\mathbb{K})\to\mathbb{K}$ che ***verifica le proprietà*** 1, 2, 3.

>[!Proprietà 5]
>Il *determinante* di una matrice è uguale al *determinante* della ***matrice trasposta***
>$$\det(A)=\det(A^T)$$

>[!done] In particolare
>Lo sviluppo di ***Laplace*** può essere fatto *rispetto a una riga* invece che *rispetto ad una colonna*
>Le proprietà 1 e 2 valgono anche per le righe

>[!Proprietà 6]
>Il *determinante* del **prodotto fra matrici** è uguale al ***prodotto fra determinanti***
>$$\det(A\times B)=\det(A)\times \det(B)$$

>[!Proprietà 7]
>Se il *determinante* di una matrice $A$ è diverso da $0$, $A$ è ***invertibile***
>$$\det(A)\neq 0 \iff A \text{ invertibile}$$


#### Esempio
$$
A=\begin{pmatrix}
-3 & 0 & 0 & 4 \\
7 & 2 & 11 & 9 \\
2 & 0 & -1 & 3 \\
1 & 0 & 0 & 0
\end{pmatrix}
$$
Scegliamo una ***collonna***
- Per comodità scegliamo la colonna con più $0$, $j=2$

$$
\det(A)=(-1)^{1+2}\cdot0\cdot\det(A^{12})+(-1)^{2+2}\cdot2\cdot\det(A^{22})+(-1)^{3+2}\cdot0\cdot\det(A^{32})+(-1)^{4+2}\cdot0\cdot\det(A^{42})=
$$
$$
=(-1)^{2+2}\cdot2\cdot\det(A^{22})
$$

Ora calcolo la matrice $A^{22}$
$$
A^{22}=\begin{pmatrix}
-3 & 0 & 4 \\
2 & -1 & 3 \\
1 & 0 & 0
\end{pmatrix}
$$
- Scelgo $j=2$
$$
\det(A)=2\cdot(-1)^{2+2}\cdot(-1)\cdot \det\begin{pmatrix}
-3 & 4 \\
1 & 0
\end{pmatrix}
=-2\cdot(-1)^{1+2}\cdot_{4}\det(1)=2\cdot 4\cdot1 = 8
$$

### Osservazioni
>[!info] $n=2$

>Se $n=2$, la regola di Laplace implica che:
$$\det(A)=a_{11}a_{22}-a_{21}a_{12}$$


>[!info] $n=3$

> Se $n=3$, lo sviluppo di *Laplace* rispetto alla prima colonna otteniamo la [[../../Definizioni/Definizioni_Analisi#Regola di Sarrus|regola di Sarrus]]

#### Esercizio
>*I vettori* $v_{1}=(-3,7,2,1), v_{2}=(0,2,0,0), v_{3}=(0,11,-1,0),v_{4}=(4,9,3,0)$

>[!question] I vettori $v_{1},v_{2},v_{3},v_{4}$ formano una base in $\mathbb{R}^4$?

Vediamo un modo nuovo di calcolarlo

$$
\det(v_{1},v_{2},v_{3},v_{4})=8
$$
- Calcolato l'esempio precedente
- $8\neq 0\iff A$ è *invertibile* $\iff$ i vettori colonna sono indipendenti $\iff v_{1},v_{2},v_{3},v_{4}$ sono base di $\mathbb{R}^4$

### Osservazione
>*Se* $A$ *è invertibile,* $\det(A^{-1})=\det(A)^{-1}$

>[!tldr] Infatti
>$$A\times A^{-1} = I_{n}\implies \det(A\times A^{-1}) = \det(I_{n})=1$$
>$$\det(A)\times \det(A^{-1})=1 \implies \det(A^{-1})=\det(A)^{-1}$$

>[!Proposizione]
>Se $A$ e $M$ sono [[6 - Cambiamenti di Base#Matrici Simili|simili]] allora hanno lo ***stesso determinante***

#### Dimostrazione
>$A$ *e* $M$ *simili* *vuol dire che* $\exists B$ *invertibile tale che* $M=B^{-1}\times A \times B$

Per la proprietà 6 e l'osservazione precedente
$$
\det(M) = \cancel{ \det(B)^{-1} }\det(A)\cancel{ \det(B) } \implies \det(M)=\det(A)
$$
### $\det(f)$
>[!info] Definizione
>Data $f:V\to V$ [[1 - Applicazioni Lineari|lineare]], definiamo $\det(f)=\det(A)$
>Dove $A$ è la *matrice* che *rappresenta* $f$ in qualsiasi [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Base|base]]
>Per la proposizione precedente, ***non dipende dalla base scelta*** se $A$ e $M$ rappresentano la stessa $f$ in ***basi diverse***
>>[!done] Osservazione
>>$$f\text{ isomorfismo }\iff \det(f)\neq 0$$

