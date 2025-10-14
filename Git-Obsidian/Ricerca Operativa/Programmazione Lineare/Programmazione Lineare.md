>[!tldr] Idea
>La ***programmazione lineare*** consiste nel *minimizzare* o *massimizzare* una **funzione obbiettivo** lineare in presenza di vincoli lineari.

Si consideri un problema di *programmazione lineare continua* con $n$ variabili decisionali e $m$ vincoli.
$$
\begin{array}
\ \min z = \sum_{j=1}^{n}c_{j}x_{j} \\
s.t. \sum_{j=1}^{n} a_{ij}x_{j} \geq b_{i}\qquad i=1,\dots,m \\
x_{j} \geq 0 \qquad j=1,\dots,n
\end{array}
$$
> Dove:
- $x_{j}$: sono le **variabili decisionali**.
- $c_{j}$: **coefficienti di costo** della variabile $x_{j}$.
- $b_{i}$: **termine noto** del vincolo $i$.
- $a_{ij}$: **coefficiente** della variabile $x_{j}$ nel **vincolo** $i$.
- $z$: valore della **funzione obbiettivo**.

Una rappresentazione più compatta del problema è la seguente:
$$
\begin{array}
\ \min z = c^{T}x \\
s.t. \ Ax\geq b \\
x>0
\end{array}
$$
> Dove:

$$
c=\begin{bmatrix}
c_{1} \\
c_{2} \\
\vdots \\
c_{n}
\end{bmatrix}\quad x=\begin{bmatrix}
x_{1} \\
x_{2} \\
\vdots \\
x_{n}
\end{bmatrix}\quad 
b=\begin{bmatrix}
b_{1} \\
b_{2} \\
\vdots \\
b_{n}
\end{bmatrix}\quad
A = \begin{bmatrix}
a_{11} & a_{22} & \dots  & a_{1n} \\
a_{21} & a_{22} & \dots  & a_{2n} \\
\vdots & \vdots & \ddots & \vdots  \\
a_{m1} & a_{m2} & \dots  & a_{mn}
\end{bmatrix}
$$
- La matrice $A$ è anche detta *matrice dei vincoli*.

### Assunzioni Implicite
> Nella formulazioni di un problema di ***programmazione lineare*** sono implicite alcune assunzioni.

>[!abstract] Proporzionalità
>Ogni variabile $x_{j}$ contribuisce con la quantità:
>- $c_{j}x_{j}$ al valore della funzione obbiettivo.
>- $a_{ij}x_{j}$ al vincolo $i$.

>[!summary] Additività
>Il **valore della funzione obbiettivo** è dato dalla *somma dei contribuiti* $c_{j}x_{j}$ forniti da ciascuna variabile $j$.
>
>Il contributo totale ad ogni vincolo $i$ è dato dalla *somma dei contributi* $a_{ij}x_{j}$ forniti da ciascuna variabile $j$.

>[!check] Dati Deterministici
>I coefficienti $c_{j},a_{ij}$ e $b_{i}$ devono essere noti.
>- Nel caso in cui alcuni dati fossero di natura *stocastica*, devono essere approssimati con ***dati deterministici***.

>[!caution] Continuità delle Variabili
>Le variabili *possono assumere* ***tutti i valori reali*** che soddisfano i vincoli.

### Soluzione di un Problema di Programmazione Lineare
>[!failure] Soluzione Ammissibile
>Una soluzione $x$ che ***soddisfa i vincoli*** $Ax \geq b$ è detta ***soluzione ammissibile***.

>[!help] Regione Ammissibile
>L'*insieme di tutte le soluzioni ammissibili* di un problema è detta ***regione ammissibile***.

>[!done] Soluzione Ottima
>La *soluzione ammissibile* $x^{*}$ che minimizza o massimizza il valore della funzione obbiettivo è detta ***soluzione ottima***.

>[!question] Problema Senza Soluzione
>Se la regione ammissibile è *vuota* diremo che il ***problema non ha soluzione*** o che il problema non è ammissibile.

## Programmazione Lineare Intera
---
>[!bug] Mixed Integer Programming
> Un problema di programmazione lineare intera prevede il vincolo aggiuntivo che le variabili decisionali ***devono assumere valori interi***.

![[MixedIntegerProgramming.png]]

$$
\begin{array}
\ \min z = \sum_{j=1}^{n}c_{j}x_{j} \\
s.t. \sum_{j=1}^{n} a_{ij}x_{j} \geq b_{i}\qquad i=1,\dots,m \\
x_{j} \geq 0 \qquad j=1,\dots,n \\
x_{j} \quad \text{ integer}
\end{array}
$$


### Problema della Dieta
>[!question] Problema
>Determinare la composizione della ***dieta di costo minimo***, che garantisca un contributo minimo giornaliero di energia ($2000\ Kcal$), di proteine ($55g$) e di calcio ($800\ mg$) scegliendo tra:

| Alimenti          | Porzione | Ener. (kcal) | Prot. (g) | Calcio (mg) | Costo (Euro) |
|-------------------|----------|--------------|-----------|-------------|--------------|
| Fiocchi avena     | 28 g     | 100          | 5         | 2           | 0.30         |
| Pollo             | 100 g    | 205          | 32        | 12          | 0.90         |
| Uova              | 2        | 160          | 13        | 54          | 0.80         |
| Latte             | 237 cc   | 160          | 8         | 285         | 0.50         |
| Torta ciliegie    | 170 g    | 420          | 4         | 22          | 2.00         |
| Maiale e piselli  | 260 g    | 260          | 14        | 80          | 1.90         |

Aggiungiamo l'ulteriore ***vincolo*** sul numero di ***porzioni-giorno*** per ciascun alimento.
- Fiocchi Avena: $\leq 4$
- Pollo: $\leq 3$
- Uova: $\leq 2$
- Latte: $\leq 8$
- Torta di Ciliege: $\leq 2$
- Maiale e Piselli: $\leq 2$

> Per formulare matematicamente il problema facciamo uso delle seguenti ***variabili decisionali***.

- $x_{1}$: N. porzioni di Fiocchi Avena.
- $x_{2}$: N. porzioni di Pollo.
- $x_{3}$: N. porzioni di Uova.
- $x_{4}$: N. porzioni di Latte.
- $x_{5}$: N. porzioni di Torta di Ciliege.
- $x_{6}$: N. porzioni di Maiale e Piselli.

>[!abstract] Formulazione Matematica

$$
\min z = 
\begin{bmatrix}
100 & 205 & 160 & 160 & 420 & 260
\end{bmatrix}
$$