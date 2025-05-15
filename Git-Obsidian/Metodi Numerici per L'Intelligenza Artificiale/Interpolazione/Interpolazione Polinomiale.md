>[!check] Introduzione
>Definiamo $\mathbb{P}_{n}[x]$ lo [[2 - Campi e Spazi Vettoriali#Spazio Vettoriale|spazio vettoriale]] dei polinomi nella variabile $x$ di **grado** minore o uguale a $n$ e a ***coefficienti reali***.
>$$\mathbb{P}_{n}[x]:=\{ \alpha_{0}+\alpha_{1}x+\alpha_{2}x^2+\dots+\alpha_{n}x^n|\alpha_{i}\in\mathbb{R} \}$$

La [[3 - Teoremi su Spazi Vettoriali#Base Canonica|base canonica]] dello spazio appena descritto è ***rappresentata dalle funzioni base***:
$$
\phi_{0}(x)=1,\quad \phi_{1}(x)=x,\quad\phi_{2}=(x)x^2,\quad \phi_{3}(x)=x^3,\ \dots\ , \phi_n(x)=x^n
$$

## Interpolazione Polinomiale di Dati Sperimentali
---
>[!tldr] Idea
>Note le coppie $(x_{i},y_{i})$ con $i=0,\dots,n$ e $x_{i}\neq x_{k}\quad i\neq k$ dove $x_{i}$ sono detti ***nodi*** e $y_{i}$ rappresentano le ***valutazioni di un fenomeno*** nelle posizioni $x_{i}$, il problema dell'***interpolazione polimoniale*** consiste nel determinare il polinomio 
>$$P_{n}(x)\in\mathbb{P}_{n}[x]$$
>Tale che 
>$$P_{n}(x_{i})=y_{i}$$

Equivale ad individuare i coefficienti $\alpha_{i}$ del polinomio $P_{n}(x)$ tale che sia soddisfatta la ***condizione di interpolazione***.

Una volta individuati, avremo la formula analitica del ***polinomio interpolatore*** che potremo *valutare anche in altre posizioni* $\overline{x}$ che **non** fanno parte del nostro insieme di punti.

> Indichiamo con $\xi_{1}=\min\{ x_{0},x_{1},x_{2},\dots,x_{n} \}$ e $\xi_{2}=\max\{ x_{0},x_{1},x_{2},\dots,x_{n} \}$

>[!help] Interpolazione
>Parliamo di ***interpolazione*** se $\overline{x}\in [\xi_{1},\xi_{2}]$

>[!abstract] Estrapolazione
>Parliamo di ***estrapolazione*** se $\overline{x}\notin [\xi_{1},\xi_{2}]$

> $P_{n}(x_{i})=y_{i}$ significa imporre:

$$
P_{n}(x_{i})= \alpha_{0}+\alpha_{1}x_{i}+\alpha_{2}x_{i}^2+\dots+\alpha_{n}x_{i}^n=y_{i}
$$
Se scriviamo questa relazione per ogni $i$, ricaviamo il seguente [[Sistemi Lineari|sistema lineare]]:
$$
\begin{cases}
\alpha_{0}+\alpha_{1}x_{0}+\alpha_{2}x_{0}+\dots+\alpha_{n}x_{0}^n=y_{0} \\
\alpha_{1}+\alpha_{1}x_{1}+\alpha_{2}x_{1}+\dots+\alpha_{n}x_{1}^n=y_{1} \\
\dots \\
\alpha_{n}+\alpha_{1}x_{n}+\alpha_{2}x_{n}+\dots+\alpha_{n}x_{n}^n=y_{n} \\
\end{cases}
$$
>[!hint] Coefficienti
>I coefficienti $\alpha_{i}$ del polinomio che soddisfa le ***condizioni di interpolazione*** sono la soluzione del **sistema lineare**.
>$$A\alpha=y$$

Dove la matrice dei coefficienti $A$ di questo sistema è la matrice di dimensione $(n+1)\times(n+1)$.
- ***Matrice Quadrata*** poiché il numero di condizioni che imponiamo è uguale a quello delle incognite.
$$
A=\begin{bmatrix}
1 & x_{0} & x_{0}^2 & \dots & x_{0}^n \\
1 & x_{1} & x_{1}^2 & \dots & x_{1}^n \\
\dots & \dots & \dots & \ddots & \dots \\
1 & x_{n} & x_{n}^2 & \dots & x_{n}^n \\
\end{bmatrix}
$$
- Che è la [[Condizionamento di un Sistema Lineare#Esempi|matrice di Vandermonde]]. 
Il vettore $y=\begin{bmatrix}y_{0}\\y_{1}\\\dots\\y_{n}\end{bmatrix}$ è il vettore di ordine $n+1$ la cui $i$-*esima* componente è rappresentata dalla $i$-esima ***valutazione*** $y_{i}$.

Il vettore $\alpha$ è il ***vettore delle incognite***.

>[!info]
>Il sistema ammette ***una ed una sola soluzione*** *se e solo se* la matrice dei coefficienti è quadrata e a [[6 - Cambiamenti di Base#Rango di una Matrice|rango massimo]].

- Sappiamo che è quadrata.
- È sempre a rango massime poiché $x_{i}\neq x_{k},\quad i\neq k$

>[!done] Il polinomio interpolatore esiste sempre ed è unico.

#### Problema
>[!danger] Attenzione
>Come visto in [[Condizionamento di un Sistema Lineare#Esempi|precedenza]] la matrice di Vandermonde, è una matrice ***molto mal condizionata***.
>- La soluzione del sistema lineare è un problema [[Condizionamento#Condizionamento di un Problema|molto mal condizionato]], molto sensibile alle *perturbazioni sui dati*.

Occorre cambiare approccio
### Polinomi di Lagrange
>[!definizione] Base di Lagrange
> È necessario ***cambiare la base*** per lo spazio $\mathbb{P}_{n}[x]$
> Una base che fa sì che la *matrice del sistema lineare* che nasce dall'imposizione delle **condizioni di interpolazione** coincida con la [[5 - Matrici di Applicazioni Lineari#Matrice Identità|matrice Identità]] è la ***base di Lagrange***.

Gli $n+1$ ***polinomi di Lagrange***, $L_{j}^{(n)}$ sono polinomi di grado $n$ che rappresentano una base per lo spazio dei polinomi $\mathbb{P}_{n}[x]$ e *soddisfano le condizioni*:
$$
L_{j}^{(n)}(x_{i})=\begin{cases}
1\qquad \text{se }i=0 \\
0\qquad \text{se }i\neq0
\end{cases}
$$

^71e316

Il polinomio $P_{n}(x)=\alpha_{0}L_{0}^{(n)}(x)+\alpha_{1}L_{1}^{(n)}(x)+\dots+\alpha_{n}L_{n}^{(n)}(x)$.
- Imponendo le ***condizioni di interpolazione***, ricaveremo il seguente sistema lineare:
$$
\begin{cases}
\alpha_{0}L_{0}^{(n)}(x_{0})+\alpha_{1}L_{1}^{(n)}(x_{0})+\dots+\alpha_{n}L_{n}^{(n)}(x_{0})=y_{0} \\
\alpha_{0}L_{0}^{(n)}(x_{1})+\alpha_{1}L_{1}^{(n)}(x_{1})+\dots+\alpha_{n}L_{n}^{(n)}(x_{1})=y_{1} \\
\dots \\
\alpha_{0}L_{0}^{(n)}(x_{n})+\alpha_{1}L_{1}^{(n)}(x_{n})+\dots+\alpha_{n}L_{n}^{(n)}(x_{n})=y_{n}
\end{cases}
$$
Che scritto in termini matriciali diventa:
$$
\begin{bmatrix}
L_0^{(n)}(x_0) & L_1^{(n)}(x_0) & \dots & L_n^{(n)}(x_0) \\
L_0^{(n)}(x_1) & L_1^{(n)}(x_1) & \dots & L_n^{(n)}(x_1) \\
\vdots & \vdots & \ddots & \vdots \\
L_0^{(n)}(x_n) & L_1^{(n)}(x_n) & \dots & L_n^{(n)}(x_n)
\end{bmatrix}
\begin{bmatrix}
\alpha_0 \\
\alpha_1 \\
\vdots \\
\alpha_n
\end{bmatrix}
=
\begin{bmatrix}
y_0 \\
y_1 \\
\vdots \\
y_n
\end{bmatrix}
$$

Che per la proprietà dei ***polinomi base di Lagrange*** si riduce a:
$$
\begin{bmatrix}
1 & 0 & \dots & 0 \\
0 & 1 & \dots & 0 \\
\vdots & \vdots & \ddots & \vdots \\
0 & 0 & \dots & 1
\end{bmatrix}
\begin{bmatrix}
\alpha_0 \\
\alpha_1 \\
\vdots \\
\alpha_n
\end{bmatrix}=\begin{bmatrix}
y_0 \\
y_1 \\
\vdots \\
y_n
\end{bmatrix}
$$
E quindi il vettore soluzione $\alpha$ coincide con il vettore termine noto $y$.

#### Ricavare la Base di Lagrange
> Ricaviamo le funzioni [[2 - Campi e Spazi Vettoriali#Base|base]] $L_{j}^{(n)}\quad j=0,\dots,n$

$L_{j}^{(n)}$ è un polinomio che soddisfa le condizioni:
![[#^71e316]]

>[!quote] Cioè
>Si ***annulla in tutti i punti*** $x_{i}, \ i\neq j$ ed è *diverso da zero* solo nel punto $x_{j}$.
>Sarà quindi della forma:
>$$L_{j}^{(n)}(x)=c(x-x_{0})(x-x_{1})\dots(x-x_{j-1})(x-x_{j+1})\dots(x-x_{n})$$

> Determiniamo $c$ in maniera tale che $L_{j}^{(n)}(x_{j})=1$

*Impongo*:
$$
L_{j}^{(n)}(x_{j})=c\prod_{\begin{array}\ k=0 \\ k\neq j\end{array}}^{n}(x_{j}-x_{k})=1
$$
Da cui segue:
$$
c=\frac{1}{\prod_{\begin{array}\ k=0 \\ k\neq j\end{array}}^{n}(x_{j}-x_{k})}
$$
***Quindi***:
$$
L_{j}^{(n)}(x)=\prod_{\begin{array}\ k=0 \\ k\neq j\end{array}}^{n} \frac{(x-x_{k})}{(x_{j}-x_{k})}
$$
>[!cite] Espandendo
>$$L_{j}^{(n)}(x)=\displaystyle{\frac{(x-x_{0})(x-x_{1})\dots(x-x_{j-1})(x-x_{j+1})\dots(x-x_{n})}{(x_{j}-x_{0})(x_{j}-x_{1})\dots(x_{j}-x_{j-1})(x_{j}-x_{j+1})\dots(x_{j}-x_{n})}}$$

>[!tip] Proprietà
>I polinomi base della *base di Lagrange* godono della proprietà di partizione dell'unità.
>$$\sum_{i=0}^{n}L_{j}^{(n)}(x)=1 \qquad \forall x \in [x_{0},x_{n}]$$
>Se $x_{0}<x_{1}<x_{2}<\dots<x_{n}$.

#### Polinomio Interpolatore nella Forma di Lagrange
>[!info]
> Date le coppie $(x_{i},y_{i})$ con $i=0,\dots,n$, $x_{i}\neq x_{j}, i\neq k$ il polinomio di grado $n$ che interpola può essere espresso dalla seguente ***forma di Lagrange***.
>$$P_{n}(x)=\sum_{j=0}^{n}y_{i}L_{j}^{(n)}(x)$$

Sfruttando la proprietà dei ***polinomi base di Lagrange*** relativi ai punti $x_{0},x_{1},x_{2},\dots,x_{n}$ si vede che $P_{n}(x)$ fornisce una *nuova espressione del polinomio interpolatore*.

>[!summary] Dimostrazione

> Calcoliamo $P_{n}(x)$ in un qualunque punto $x_{i}$.

Otteniamo:
$$
P_{n}(x_{i})=\sum_{j=0}^{n}y_{i}L_{j}^{(n)}(x_{i})=y_{i}
$$
- Verifichiamo che valga esattamente $x_{i}$

$$
P_{n}(x_{i})=y_{0}L_{0}^{(n)}(x_{i})+y_{1}L_{1}^{(n)}(x_{i})+\dots+y_{i}L_{i}^{(n)}(x_{i})+\dots+y_{n}L_{n}^{(n)}(x_{i})
$$
Per la proprietà dei polinomi di Lagrange:
![[#^71e316]]

L'unico polinomio di Lagrange diverso da zero nel punto $x_{i}$ è $L_{i}^{(n)}(x_{i})$ che nel punto $x_{i}$ vale $1$.
$$
P_{n}(x_{i})=y_{i}
$$
>[!done] Questo vale per tutti i punti $x_{i}$.

#### Complessità Computazionale
>[!caution] Complessità
>Per il calcolo del ***polinomio di Lagrange*** di grado $n$ sono necessarie $n$ *moltiplicazioni* per determinare il numeratore e $n$ per il denominatore.
>Di questi polinomi ne dobbiamo calcolare $n+1$.
>>[!cite] Totale
>>In totale il numero di moltiplicazioni da effettuare sono $2n(n+1)$.
>>A queste bisogna aggiungere $n+1$ moltiplicazioni per ***eseguire la sommatoria***.
>
>Quindi la [[Complessità di Algoritmi|complessità computazionale]] della ***valutazione del polinomio interpolatore di Lagrange*** in un punto è $O(2n^{2})$

Se dobbiamo effettuare la *valutazione* in $M>n$ punti avremo una complessità computazionale dell'ordine di $O(2n^{2}\cdot M)$
- In generale $M$ è ***molto maggiore*** di $n$.

>[!danger] Problema
>Il polinomio interpolatore di Lagrange presenta una ***grande difficoltà di applicazione***:
>- Se dopo aver costruito il polinomio di grado $n$ che *interpola* le coppie $(x_{i},y_{i})$, si vuole aggiungere una coppia $(x_{i+1},y_{i+1})$, è necessario ***costruire ex-novo*** tutte le *funzioni di Lagrange*.

Il polinomio ***interpolatore di Newton*** risolve questo problema e ha una *complessità computazionale* di $O\left( \frac{n^{2}}{2}+n\cdot M \right)$
