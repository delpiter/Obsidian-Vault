## Expectation Maximization con Gaussian Mixture
---
> Si ipotizza che i pattern siano stati generati da un *mix di distribuzioni*.

Ogni classe ha dati in accordo con una specifica distribuzione.
- Al termine della generazione i pattern appaiono come prodotti da una unica ***distribuzione multi-modale***.

> [!help] Obbiettivo
> L'***obbiettivo del clustering*** con `EM` è risalire ai *parametri delle singole distribuzioni* che li hanno generati.

A tal fine si ipotizza nota la forma delle distribuzioni e si assume, per semplicità, che esse siano tutte dello stesso tipo.

Il caso più frequente è quello di *mix* di $s$ ***distribuzioni multinormali*** ([[../../Matematica Discreta e Probabilità/Probabilità/Variabili Continue/12 - Variabile Normale o Gaussiana|gaussiane]]), di cui si vogliono stimare i parametri di definizione:
$$
p(x\mid \Theta)=\sum_{i=1,\dots,s}\alpha_{i}\cdot p_{i}(x\mid \theta_{i})
$$
Con
- $\Theta=\{ \alpha_{1},\alpha_{2},\dots,\alpha_{s},\theta_{1},\theta_{2},\dots,\theta_{s} \}$ è il vettore di parametri che definisce il mix di distribuzioni $p_{i}(\cdot\mid \theta_{i})$ è una multinormale con parametri $\theta_{i}$
	- $\theta_{i}=\{ \mu_{i},\Sigma_{i} \}$

### Idea
> La stima dei parametri avviene secondo il criterio generale del **maximum likelihood**.


> [!cite] Likelihood
> In generale il likelihood $\mathcal{L}$ dei parametri $\Theta$ dati i pattern $X$ corrisponde alla ***probabilità di aver ottenuto i pattern*** dati i parametri
> $$\mathcal{L}(\Theta\mid X)=p(X\mid \Theta)$$

Per semplicità al posto del likelihood, si massimizza il suo ***logaritmo***.

Considerando i *pattern indipendenti* la probabilità di avere ottenuto i pattern del training set è il ***prodotto delle probabilità delle singole generazioni***.

$$
\log p(X\mid \Theta) = \prod_{j=1,\dots,n} p(x_{j} \mid \Theta) = \sum_{j=1,\dots,n}\log\left( \sum_{i=1,\dots,s}\alpha_{i}\cdot p_{i}(x_{j}\mid \theta_{i}) \right) 
$$

> [!fail] Complessità
> Purtroppo questa massimizzazione è molto difficile a causa della sommatoria dentro al logaritmo.

Per eliminare la sommatoria, ci servirebbe sapere ogni pattern $x_{j}$ del training set da quale componente $p_{i}$ della mixture è stato generato.

A tal fine si utilizza `EM`, che è un approccio iterativo nato per il calcolo del maximum likelihood nel caso in cui i dati a disposizione $X=\{ x_{1},x_{2},\dots,x_{n} \}$ siano incompleti per la mancanza di alcuni valori $Y=\{ y_{1},y_{2},\dots,y_{n} \}$.

Ogni pattern completo $z_{j}=[x_{j},z_{j}], j=1,\dots,n$.