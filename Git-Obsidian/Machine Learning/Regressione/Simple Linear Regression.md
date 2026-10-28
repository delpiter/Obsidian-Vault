## Simple Linear Regression
---
> [!cite] Definizione
> Dato un training set contenente $n$ pattern $(x_{1},y_{1}),\dots,(x_n, y_{n})$ e la seguente dipendenza tra variabile indipendente e dipendete:
> $$y_{i}=\alpha+ \beta\cdot x_{i}+\epsilon_{i}$$
> La soluzione ai ***minimi quadrati*** ([[../Metodi Numerici per L'Intelligenza Artificiale/Equazioni Lineari/Sistemi Sovradeterminati#Least Squares|Least Squares]]) del problema consiste nel determinare l'equazione della retta.

Dove:
- $\epsilon_{i}$ è l'errore di misura (incognito) del pattern $x_{i}$
- $\alpha$ e $\beta$ sono parametri da ***determinare***.

Bisogna trovare la funzione $f(x)=\alpha+ \beta\cdot x+\epsilon$ che minimizza la somma dei quadrati dei residui.
$$
\alpha^{*},\beta^{*} = \arg\min_{\alpha,\beta} \sum_{i=\mathbf{i}..,n}(f(x)-y_{i})^{2}
$$
Il problema di minimizzazione può essere facilmente risolto uguagliando a zero le derivate parziali della funzione obiettivo rispetto ai parametri $\alpha, \beta$ ottenendo le cosiddette ***equazioni normali***.

Risolvendo il sistema di due equazioni in due incognite si ottiene:
$$
\beta^{*}=\displaystyle{\frac{\sum_{i=1,\dots,n}(x_{i}-\overline{x})(y_{i}-\overline{y})}{\sum_{i=1,\dots,n}(x_{i}-\overline{x})^{2}}},\qquad \alpha^{*}=\overline{y}-\beta^{*}\overline{x}
$$

Dove $\overline{x}$ e $\overline{y}$ sono la media degli $x_{i}$ e $y_{i}$.

> [!important] Attenzione
> Sono necessari almeno due punti con $x_{i}$ diversi, altrimenti il ***denominatore si annulla***.