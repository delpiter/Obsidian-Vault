>*Il [[7 - Determinante di una Matrice|determinante]] permette di dire se una matrice $A$ è invertibile*

>[!question] In caso affermativo, come trovo $A^{-1}$?

## Matrice Inversa
---
>[!check]
>$$A^{-1}=\frac{1}{\det(A)}\cdot \text{cof}(A)^T$$
>Dove il ***cofattore*** è definito nel seguente modo:
>$$\text{cof}(A)_{ij}=(-1)^{i+j}\det(A^{ij})$$
>>[!done] A Parole
>>La matrice inversa è definita dall'inverso del [[7 - Determinante di una Matrice|determinante]] moltiplicato per il [[Git-Obsidian/Analisi/Definizioni_Analisi#Matrice Trasposta|trasposto]] del *cofattore*

#### Esercizio
$$
A=\begin{pmatrix}
3 & 5 \\
2 & 4
\end{pmatrix}
$$
$$
\det(A)=(3\cdot4)-(2\cdot5) = 2\neq0
$$
- $A$ è *invertibile*
$$
\begin{array}
\ \text{cof}(A)=\begin{pmatrix}
a_{11} & a_{12} \\
a_{21} & a_{22}
\end{pmatrix} \\
a_{11}=\det(4)\cdot(-1)^{1+1} \\
a_{21}=\det(2)\cdot(-1)^{2+1} \\
a_{12}=\det(5)\cdot(-1)^{2+1} \\
a_{22}=\det(4)\cdot(-1)^{2+2}
\end{array}
$$
$$
\text{cof}(A)=\begin{pmatrix}
4 & -2 \\
-5 & 3
\end{pmatrix}\implies\text{cof}(A)^T=\begin{pmatrix}
4 & -5 \\
-2 & 3
\end{pmatrix}
$$

Ora moltiplichiamo per l'***inverso del determinante***
$$
A^{-1}=\frac{1}{2}\begin{pmatrix}
4 & -5 \\
-2 & 3
\end{pmatrix}=\begin{pmatrix}
2 & \displaystyle-\frac{5}{2} \\
-1 & \displaystyle \frac{3}{2}
\end{pmatrix}
$$
>[!done] Infatti

$$
A\times A^{-1}=\begin{pmatrix}
3 & 5 \\
2 & 4
\end{pmatrix}\times\begin{pmatrix}
2 & -\frac{5}{2} \\
-1 & \frac{3}{2}
\end{pmatrix}=I_{2}
$$

## Matrice Inversa con Gauss
---
>*Osserviamo che [[Risoluzione di Sistemi#Metodo di Gauss|l'algoritmo di Gauss]] ci permette anche di trovere l'inversa di una matrice $A$ in modo **computazionalmente più efficiente** rispetto al metodo del cofattore*

### Algoritmo di Gauss-Jordan
>[!info] Passaggi
>Sia $A$ matrice $n\times n$ invertibile
>Prendo la matrice $(A|I_{n})$ e applico ad essa l'algoritmo di Gauss fino ad ottenere
>$$(I_{n}|B)$$
><u>Allora</u>
>$$B=A^{-1}$$

#### Esempio
$$
A=\begin{pmatrix}
3 &5 \\
2 & 4
\end{pmatrix}
$$
>*Prendiamo $A|I_{2}$*

$$
A|I_{2}=\begin{pmatrix}
3 & 5 & 1 & 0 \\
2 & 4 & 0 & 1
\end{pmatrix}
$$

Applico il metodo di Gauss
- Successivamente trovo $\overline{A|I_{2}}$
$$
\begin{pmatrix}
3 & 5 & 1 & 0 \\
0 & \frac{2}{3} & -\frac{2}{3} & 1
\end{pmatrix} =
\begin{pmatrix}
1 & \frac{5}{3} & \frac{1}{3} & 0 \\
0 & 1 & -1 & \frac{3}{2}
\end{pmatrix}
$$

Ora cerco di ottenere la *matrice identità* nelle ***prime due colonne***

$$
I-\frac{5}{3}II\begin{pmatrix}
1 & 0 & 2 & -\frac{5}{2} \\
0 & 1 & -1 & \frac{3}{2}
\end{pmatrix}
$$

Quindi:
$$A^{-1}=\begin{pmatrix}
2 & -\frac{5}{2} \\
-1 & \frac{3}{2}
\end{pmatrix}$$

>[!question] Perché Funziona?

Se $A$ è la matrice nella base canonica della funzione $f(x,y)=(3x+5y,3x+4y)$
- Allora $A^{-1}$ è la matrice dell'applicazione $f^{-1}(a,b)\implies$ l'unico $(x,y):f(x,y)=(a,b)$
- Che trovo risolvendo il seguente sistema

$$
\begin{cases}
3x+5y=a \\
2x+4y =b
\end{cases}\iff
\begin{cases}
x=2a-\frac{5}{2}b \\
y=-a+\frac{3}{2}b
\end{cases}
$$

>[!done] Abbiamo fatto le stesse operazioni