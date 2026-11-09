## Grammatiche Probabilistiche Libere dal Contesto
---
> [!info] Probabilistic Context-Free Grammar
> Una `PCFG` è una ***quintupla*** $G=(V,\Sigma, P,S,D)$ dove $(V,\Sigma,P,S)$ è una [[../Linguistica Formale/Grammatiche e Linguaggi Liberi dal contesto#Context-Free Grammars|CFG]] e $D$ è una funzione che assegna una probabilità $p$ ad ogni produzione in $P$.

Per ciascuna variabile $A\in V$, la somma delle probabilità delle produzioni $A$ deve essere $1$.

Denotiamo la produzione probabilistica con:
$$
A\to \beta [p]
$$
> [!quote] A parole
> Data una variabile $A$ , $A$ viene espansa ad una sequenza $\beta$ con una ***probabilità*** $p$.

> Esempio: produzioni di una variabile $Adjs$ in una `PCFG`:

$$
\begin{align}
& Adjs \to Adjective \qquad \ \ [0.80] \\
& \qquad \ \ \mid Adjective \ \ Adjs \ [0.20]
\end{align}
$$
La somma delle probabilità di $Adjs$ deve arrivare a $1$.