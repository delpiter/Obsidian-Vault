>[!check] Teorema dell'Errore
>Siano assegnate le coppie $(x_{i},y_{i}),\quad i=0,\dots,n$
>$$a\equiv x_{0}<x_{1}<\dots<x_{n}\equiv b$$
>e $y_{i}=f(x_{i})$ siano i valori assunti in questi punti da una funzione $f(x)$ definita in $[a,b]$ e $f(x\in C^{n+1}[a,b])$.
>Sia $P_{n}(x)$ il polinomio di grado $n$ che [[Interpolazione Polinomiale|interpola]] ***tali coppie di dati***.
>Sia $\overline{x}\in[a,b]$, indichiamo con
>$$E(\overline{x})=f(\overline{x})-P_{n}(\overline{x})$$
><u>Risulta che</u>
>$$E(\overline{x})=f(\overline{x})-P_{n}(\overline{x})=\frac{1}{(n+1)!}\omega_{n+1}(\overline{x})f^{(n+1)}(\xi)$$
>Dove $\xi \in (a,b)$ e $\omega_{n+1}(\overline{x})=\prod_{k=0}^{n}(\overline{x}-x_{k})$

Se $\overline{x}=x_{i}$, allora l'***errore è nullo***, poiché si annulla il fattore $\omega_{i+1}(\overline{x})$

*Risulta nullo* anche nel caso di dati provenienti da funzioni che hanno la **derivata** $n+1$ **nulla**.
- Polinomi di grado $n$.

## Convergenza del Polinomio Interpolatore
---
>[!info] 
>Al crescere del *numero dei punti di interpolazione* e quindi, del **grado del polinomio interpolatore**, nel caso in cui i punti $x_{i}$ siano scelti equidistanti nell'intervallo $[a.b]$:
>In genere ***non si ha la convergenza*** del polinomio interpolatore alla *funzione che ha generato i dati*.
>>[!quote] Risultato
>>Si ha al **centro** dell'intervallo una *buona approssimazione* e delle **fitte oscillazioni** agli **estremi**, tipiche dei *polinomi di grado elevato*.

>[!question] Da che cosa dipende l'errore di interpolazione?

***Dipende:***
1. Dalla **regolarità della funzione**.
2. Dalla **disposizione dei punti di interpolazione** sull'asse delle ascisse.

Possiamo minimizzare l'errore determinano i punti $x_{i}$ in modo che risulti minimo, il termine $\omega_{n+1}(\overline{x})$.

> Si mostra che se i punti $x_{i}$ vengono scelti come ***zeri dei polinomi di Chebichev***

$$
x_{i}=\cos\left( \displaystyle{\frac{1+2\cdot i}{2\cdot(n+1)}}\pi \right)
$$
Allora risulta *minimo* $\omega_{n+1}(\overline{x})$ e all'aumentare del numero dei punti di interpolazione is ha la ***convergenza alla funzione generatrice dei dati***.

## Condizionamento dell'Interpolazione Polinomiale
---
>[!check] Condizionamento
>Siano date le coppie $(x_{i},y_{i})$ con $x_{i}$ appartenenti all'intervallo $[a,b]$.
>Consideriamo le perturbazioni sui dati $\tilde{y_{i}}=y_{i}+\varepsilon_{i}$ e nell'[[../Numeri Finiti/Errore di Rappresentazione|errore relativo sui dati]].
>$$\displaystyle{\frac{\|\tilde{y}-y\|_{\infty}}{\|y\|_{\infty}}}$$
>Dove $\tilde{y}=(\tilde{y_{0}},\tilde{y_{1}},\dots,\tilde{y_{n}})^{T}$ e $y=(y_{0},y_{1},\dots,y_{n})^{T}$

Sia $P_{n}(x)=\sum_{i=0}^{n}y_{i}L_{i}(x)$ il polinomio che ***interpola le coppie originali*** e $\tilde{P}_{n}(x)=\sum_{i=0}^{n}\tilde{y}_{i}L_{i}(x)$ il polinomio che ***interpola le coppie perturbate*** $(x_{i},\tilde{y}_{i})$.

> Considerando ora la *differenza* tra il polinomio di interpolazione calcolato a partire dai ***dati perturbati*** e quello a partire dai ***dati esatti***.

$$
\tilde{P}_{n}(x)-P_{n}(x)=\sum_{i=0}^{n}L_{i}(x)(\tilde{y}_{i}-y_{i})
$$
- Passando ai *valori assoluti si ottiene*
$$
\mid\tilde{P}_{n}(x)-P_{n}(x)\mid\leq \max_{i=0,\dots,n}\mid\tilde{y}_{i}-y_{i}\mid\sum_{i=0}^{n}\mid L_{i}(x)\mid=\|\tilde{y}-y\|_{\infty}\lambda_{n}(x)
$$
>[!definizione] $\lambda_{n}(x)$
>$$\lambda_{n}(x)=\sum_{i=0}^{n}|L_{i}(x)|$$
>È chiamata ***funzione di Lebesgue***.

> Passando alle [[../Norma#Esempi di Norme|norme infinito]]:

$$
\max_{x\in[a,b]} |\tilde{P}_{n}(x)-P_{n}(x)|\leq\|\tilde{y}-y\|_{\infty} \max_{x\in[a,b]} \lambda_{n}(x)
$$
La relazione quindi *diventa*:
$$
\|\tilde{P}_{n}(x)-P_{n}(x)\|_{\infty} \leq\|\tilde{y}-y\|_{\infty} \cdot\|\lambda_{n}\|_{\infty}
$$
>[!info] Costante di Lebesgue
>$$\Lambda_{n}=\|\lambda_{n}\|_{\infty}$$

>[!done] Conclusione

Si ricava *facilmente* che:
$$
\displaystyle{\frac{\|\tilde{P}_{n}(x)-P_{n}(x)\|_{\infty}}{\|P_{n}(x)\|_{\infty}}}\leq\Lambda_{n} \displaystyle{\frac{\|\tilde{y}-y\|_{\infty} }{\|y\|_{\infty}}}
$$
- Dove $\Lambda_{n}$ è l'[[../Condizionamento e Stabilità/Condizionamento#Quantificare il Condizionamento|indice di condizionamento]].

Risulta che $\Lambda_{n}\geq 1$

Dalla definizione di $\Lambda_{n}$ si vede che la ***scelta dei nodi di interpolazione*** è fondamentale per il valore che può assumere la ***costante di Lebesgue***.

> Si può dimostrare che:

>[!danger] Con nodi equispaziati
>$$\Lambda_{n}\approx \displaystyle{\frac{2^{n+1}}{en\log_{e}(n)}}$$
>Per $n$ *grandi*.

>[!hint] Con nodi di Chebichev
>$$\Lambda_{n}\approx \frac{2}{n}\log_{e}(n)$$

> Se vengono scelti *gradi* $n$ **troppo elevati** l'interpolazione polinomiale risulta ***sensibile alle perturbazioni sui dati***
