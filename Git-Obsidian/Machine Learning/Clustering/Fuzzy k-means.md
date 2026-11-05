## Fuzzy K-Means
---
> [!help] Variante di K-Means
> La ***variante Fuzzy*** del [[K-Means]] consente a un pattern di appartenere con un grado di probabilità a diverse classi.

 La prima cosa da ridefinire è la metrica:
- Il criterio di ottimizzazione in questo caso è il seguente
$$
J_{fuz}=\sum_{i=1,\dots,s}\sum_{j=1,\dots,n} [P(C_{i}\mid x_{j},\Theta)]^{m}\cdot\|x_{j}-\theta_{i}\|^{2}
$$
Dove $P(C_{i}\mid x_{j},\Theta)$ è la probabilità che dato il pattern $x_{j}$ e l'insieme $\Theta=\{ \theta_{1},\dots,\theta_{s} \}$ di centroidi che definiscono la soluzione attuale, il cluster di appartenenza sia $C_{i}$

> [!hint] Osservazione
> I punti lontani ***influenzano poco la probabilità***.

I centroidi invece che come semplice media dei pattern si calcolano come ***media pesata rispetto alla probabilità di appartenenza***.
$$
\theta_{i}=\displaystyle{\frac{\sum_{j=1,\dots,n}P(C_{i}\mid x_{j},\Theta)\cdot x_{j}}{\sum_{j=1,\dots,n}P(C_{i}\mid x_{j},\Theta)}}
$$

Le probabilità di appartenenza si calcolano come:
$$
P(C_{i}\mid x_{j},\Theta)=\displaystyle{\frac{1}{\sum_{k=1,\dots,s}\left(\displaystyle{\frac{\|x_{j}-\theta_{i}\|}{\| x_{j}-\theta_{k}\|}}  \right)^{\displaystyle{\frac{2}{m-1}}} }}
$$
Dove:
- $\| x_{j}-\theta_{i}\|$ è la distanza dal punto $x_{j}$ al cluster $\theta_{i}$
- $\| x_{j}-\theta_{k}\|$ è un fattore normalizzante.
- $m>1$ è un iperparametro che definisce quanto l'appartenenza ai cluster debba essere sfumata, il valore tipico è $2$.

> [!quote] La ***probabilità di appartenenza*** è alta quando la distanza dal cluster è bassa.

Lo *pseudocodice* dell'algoritmo è molto simile al K-means
1. Inizializza $n$ e $s$
2. Inizializza casualmente $P(C_{i}\mid x_{j},\Theta)$ per $i=1,\dots,s$ e $j=1,\dots,n$
3. In loop finché $J_{fuz}$ cambia in modo significativo oppure si raggiunge un massimo di iterazioni:
	1. Calcola i centroidi $\Theta=\{ \theta_{1},\theta_{2},\dots,\theta_{s} \}$
	2. Calcola i gradi di appartenenza $P(C_{i}\mid x_{j},\Theta)$