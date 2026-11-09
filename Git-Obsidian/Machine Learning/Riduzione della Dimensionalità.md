## Definizioni
---
> [!info] 
> L'obbiettivo dei metodi per la ***riduzione di dimensionalità*** è quello di eseguire un mapping dallo spazio iniziale $\mathbb{R}^{d}$ ad uno spazio di dimensione inferiore $\mathbb{R}^{k}$, con $k< d$.

Può essere vista come una forma di ***compressione con perdita di informazione***.
- L'obbiettivo è scartare le ***informazioni non rilevanti*** o meno rilevanti per il problema di interesse.

> [!hint] Osservazione
> Ridurre di dimensionalità non significa *mantenere* alcune informazioni e *cancellarne* altre, ma ***combinare le dimensioni*** in modo opportuno.

## Tecniche principali
---
### Lineari
#### Principal Component Analysis
> [!cite] Definizione
> Trasformazione non supervisionata, nota anche come *Karhunen Loeve* **transform**.
> Esegue un mapping lineare con l'obbiettivo di ***perservare l'informazione*** del pattern.

Dato un training set $T = \{ x_{i}\in \mathbb{R}^{d}, i=1,\dots,n \}$ siano:
$$
\overline{x}=\frac{1}{n}\sum_{i=1,\dots,n}x_{i}\\
\Sigma =\frac{1}{n-1} \sum_{i=1,\dots,n}(x_{i}-\overline{x})(x_{i}-\overline{x})^{t}
$$

Il vettore medio $\in \mathbb{R}^{d}$ e la matrice di covarianza $\in \mathbb{R}^{d\times d}$
- Definizioni simili a quelle usate per il [[Classificazione/Classificazione Bayesiana|classificatore di Bayes]].

La divisione per $n-1$ è dovuta alla correzione di Bessel per caso unbiased.


> [!tldr] Idea
> Per un dato $k$ ($k<d$, $k<n$, $k>0$) lo spazio $k$ dimensionale $S_{\overline{x},\Phi_{k}}$  è univocamente definito dal vettore medio della matrice di proiezione $\Phi_{k}\in \mathbb{R}^{d\times k}$ le cui colonne sono costituite dagli [[../Algebra e Geometria/Applicazioni/9 - Matrici Diagonali#Autovettore e Autovalore|autovettori]] di $\Sigma$ corrispondenti ai $k$ più grandi [[../Algebra e Geometria/Applicazioni/9 - Matrici Diagonali#Autovettore e Autovalore|autovalori]].

$$
\Phi_{k}= [\varphi_{i1},\varphi_{i2},\dots,\varphi_{ik}]
$$
Con $\lambda_{1}\geq \lambda_{2} \geq \dots \lambda_{ik} \geq \lambda_{id}$

> [!quote] In altre parole
> Gli autovalori indicano quali sono le *direzioni* più importanti, quindi scelgo di togliere quelle che ***hanno meno valore***. 

- Autovalore grande: i dati si "*allargano*" molto in quella direzione, che distingue bene i campioni tra loro.
- Autovalore piccolo: i dati sono quasi "*schiacciati*" in quella direzione, che quindi aggiunge poca informazione.

Una volta determinato lo spazio `PCA`, la proiezione di un pattern su tale spazio è semplicemente la *proiezione geometrica* di un vettore sull'iperpiano che definisce lo spazio.


> [!caution] Matematicamente
> Questa operazione è eseguita come prodotto della ***matrice di proiezione trasposta*** per il pattern al quale è preventivamente *sottratta la media*.

$\overrightarrow{PCA}(x,S_{\overline{x},\Phi_{k}})=\Phi_{k}^{t}(x-\overline{x})$


> [!warning] Retro-proiezione
> Dato un vettore nello spazio `PCA` la sua ***retro proiezione*** si ottiene moltiplicando il vettore per la matrice di proiezione e *sommando il vettore medio*.

Non sposta spazialmente il vettore, che giace ancora sullo spazio `PCA` ma opera un cambiamento di coordinate che ne permette la codifica in termini delle $d$ componenti dello spazio originale.

##### Scelta di $k$
> A volte la scelta di $k$ è obbligata: per esempio per la visualizzazione $2$D o $3$D dei dati.

Quando invece l'obbiettivo è scartare informazione inutile mantenendo gran parte del contenuto informativo si può scegliere $k$ nel modo seguente.

$$
k = \arg\min_{z}\left\{  \displaystyle{\frac{\sum_{i=1,\dots,z} \lambda_{i}}{\sum_{i=1,\dots,d} \lambda_{i}}}\geq t  \right\}
$$
> [!quote] A parole
> Fissata una percentuale $t$ del contenuto che si vuole preservare, si sceglie il minimo valore di $k$ per cui la somma dei più grandi $k$ autovalori rispetto alla somma di tutti gli autovalori è $\geq t$

Nella pratica per valori $d$ molto elevati si utilizza la [[../Metodi Numerici per L'Intelligenza Artificiale/Equazioni Lineari/Problema Minimi Quadrati#Decomposizione in Valori Singolari|decomposizione SVD]].
#### Linear Discriminant Analysis
> [!cite] Definizione
> Trasformazione supervisionata che privilegia le dimensioni che ***discriminano al meglio i pattern***.

Dato un training set contenente $n$ pattern $(x_{1},y_{1}),\dots,(x_{n},y_{n})$ dove $x_{i}\in \mathbb{R}^{d}$ siano:
- $s$ le classi
- $y_{i}$ le etichette dei pattern
- $n_{i}$ il numero di pattern
- $\overline{x}_{i}$ il vettore medio della classe $i$-esima

Per formulare il criterio di ottimizzazione di massima separazione tra le classi sono definite le seguenti ***matrici di scattering***.

> ***Within-Class*** $S_{w}$

- Indica come i vettori sono sparsi rispetto al centro delle classi

$$
S_{w}=\sum_{i=1,\dots,s}S_{i} \qquad S_{i}\sum_{x_{j}\mid y_{j}=i}(x_{j}-\overline{x})(x_{j}-\overline{x})^{t}
$$


> ***Between-Class*** $S_{b}$

- Indica come i centri delle classi sono sparsi rispetto al centro generale della distribuzioni.

$$
S_{b}=\sum_{i=1,\dots,s}n_{i}(x_{i}-\overline{x}_{0})(x_{i}-\overline{x}_{0})^{t} \qquad \overline{x}_{0}=\frac{1}{n}\sum_{i=1,\dots,s}n_{i}\cdot \overline{x}_{i}
$$


> [!hint] Criteri
> Tra i criteri di ottimizzazione possibili quello più usato è la massimizzazione della quantità:
> $$J_{1}=tr(S_{w}^{-1}S_{b})=\sum_{i=1,\dots,d}\lambda_{i}$$

Dove $tr$ è la ***somma degli autovalori*** (*traccia*) della matrice.

> [!quote] Intuizione
> Cerca di massimizzare lo scattering tra le classi $S_{b}$ minimizzando quello all'interno di ogni classe ($S_{w}^{-1}$)

Lo spazio `LDA` è definito dagli autovettori relativi ai primi $k$ autovalori della matrice $S_{w}S_{b}^{-1}$
### PCA vs LDA
> In figura due esempi di riduzione di dimensionalità da $d=2$ a $k=1$.

1. Il segmento che identifica la soluzione `PCA` è l'iperpiano sul quale proiettando i pattern, ***conserviamo al massimo l'informazione***.
2. Il segmento che identifica la soluzione `LDA` è l'iperpiano sul quale proiettando i pattern siamo in grado di ***distinguere al meglio le due classi***.

![[attachements/LDAvsPCA.png]]

Entrambi sono mapping lineari, ma la soluzione è profondamente diversa.

### Non Lineari
#### $t$-Distributed Stochastic Neighbour Embedding
> [!cite] $t$-`SNE`
> Tecnica *non lineare* e *non supervisionata* per la riduzione di dimensionalità.

Rappresenta insieme a `UMAP` lo stato dell'arte per la visualizzazione `2D` o `3D` di dati multidimensionali.


> [!hint] Preserva le distanze locali

#### UMAP
> [!cite] Uniform Manifold Approximation and Projection for Dimension Reduction
> `UMAP` è una tecnica di riduzione di dimensionalità non lineare e non supervisionata simile a $t$-`SNE` per la ***visualizzazione di dati multidimensionali***.

`UMAP` ha maggiore capacità di preservare, oltre alle distanze locali, le ***distanze a livello globale dei cluster***.