## Forme Quadratiche
---
>[!info] Definizione
>Una forma quadratica su $\mathbb{R}^2$ è un polinomio omogeneo di grado 2 in $(h,k)$:
>$$q(h,k)=a_{11}h^2+a_{12}hk+a_{21}hk+a_{22}k^2$$
>>[!done] In oltre
>>Posso assegnargli una matrice
>>$$
A=\begin{pmatrix}
a_{11}  & a_{12} \\
a_{21}  & a_{22}
\end{pmatrix}
>>$$
>>Nel senso che:
>>$$q(h,k)=(h,k)\cdot \begin{pmatrix}
a_{11}  & a_{12} \\
a_{21}  & a_{22}
\end{pmatrix} \cdot \begin{pmatrix}
h \\
k
\end{pmatrix}
>>$$

### Categorie di Forme Quadratiche
>[!info] Definizione
>Data una forma quadratica $q(h,k)$, diciamo che essa è:
>1)  Definita:
>-  **Definita Positiva** se $q(h,k)>0 \forall (h,k)\in\mathbb{R}^2$
>- **Definita Negativa** $q(h,k)<0 \forall (h,k)\in\mathbb{R}^2$
>2) Semi Definita:
>- **Semidefinita Positiva** se $q(h,k)\leq0$
>- **Semidefinita Negativa** se $q(h,k)\geq0$
>	- $\forall(h,k)\in\mathbb{R}^2,\exists(h,k)\neq(0,0) :q(h,k)=0$
>3) **Indefinita** se $\exists(h_{1},k_{1})\in\mathbb{R}^2:q(h_{1},k_{1})>0$ e $\exists(h_{2},k_{2})\in\mathbb{R}^2:q(h_{2},k_{2})>0$

---

>[!question] Domanda
>Come faccio a capire se una forma quadratica è definita, semi definita o indefinita?

### Risposta
>[!info] Teorema
>Sia $q$ una forma quadratica con matrice
>$$A=\begin{pmatrix}
a_{11}  & a_{12} \\
a_{21} & a_{22}
\end{pmatrix}
>$$
>>[!tip] $1)$
>>$$
\begin{array}
\ q \text{ è definita positiva } \Leftrightarrow \begin{cases}
a_{11}>0 \\
\det A>0
\end{cases} \\
\ q \text{ è definita negativa } \Leftrightarrow \begin{cases}
a_{11}<0 \\
\det A>0
\end{cases} \\
\end{array}
>>$$
>
>>[!example] $2)$
>>$$
\begin{array}
\ q \text{ è semi definita positiva } \Leftrightarrow \begin{cases}
a_{11}>0 \\
\det A=0
\end{cases} \\
\ q \text{ è semi definita negativa } \Leftrightarrow \begin{cases}
a_{11}<0 \\
\det A=0
\end{cases} \\
\end{array}
>>$$
>
>>[!tip] $3)$
>>$$
q \text{ è indefinita }\Leftrightarrow \det A<0
>>$$


## Classificazione dei Punti Critici
---
>[!info] Definizione
>Chiamiamo ***punti critici*** o ***punti stazionari*** di $f$ i punti in cui si annulla il [[Calcolo Differenziale#Gradiente|gradiente]]
### Ricordo
![[Tayolor per funzioni a due Variabili#Formula di Taylor]]
Osserviamo che se $(x_{0},y_{0})$ è punto critico $df_{(x_{0},y_{0})}(h,k)t$ si annulla
##### Osservazione
Se $d^2f_{(x_{0},y_{0})}$ è [[#Forme Quadratiche |definito positivo o negativo]], posso dedurre che $(x_{0},y_{0})$ è un [[Funzioni di due Variabili Reali#Estremanti Locali|estremante locale]]

---
>[!info] Teorema
>Sia $A\subseteq\mathbb{R}^2$ [[Elementi di Algebra Lineare e Geometria Analitica#Insiemi Aperti e Chiusi|aperto]], $f:A\to\mathbb{R}$
>Sia $(x_{0},y_{0})$ punto critico di $f$
><u>Allora</u>
>
>>[!tip] Classificazione
>>1) Se $d^2f_{(x_{0},y_{0})}$ è definito positivo $\implies(x_{0},y_{0})$ è punto di Minimo Locale
>>2) Se $d^2f_{(x_{0},y_{0})}$ è definito negativo $\implies(x_{0},y_{0})$ è punto di Massimo Locale
>>3) Se $d^2f_{(x_{0},y_{0})}$ è indefinito $\implies(x_{0},y_{0})$ non è ne Max ne Min Locale e lo chiamiamo punto **Sella**
>>4) Se $d^2f_{(x_{0},y_{0})}$ è semi definito $\implies$ caso dubbio