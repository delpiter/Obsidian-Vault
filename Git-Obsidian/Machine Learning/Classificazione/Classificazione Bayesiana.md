## Approccio Bayesiano
---
> Il problema è posto in ***termini probabilistici***.

Ripasso di probabilità:
- [[../../Matematica Discreta e Probabilità/Probabilità/2 - Unione di Eventi|Unione di Eventi]]
- [[../../Matematica Discreta e Probabilità/Probabilità/Variabili Continue/8 - Variabili Aleatorie Continue|Variabili Aleatorie Continue]]

**Se** tutte le distribuzioni in gioco sono note l'*approccio Bayesiano* costituisce la miglior regola di classificazione possibile.
- "Se" molto forte, vanno conosciute tutte le distribuzioni esatte dei dati.

> [!tldr] Idea
> Sia $V$ uno spazio di pattern di dimensione $d$ e $W=\{ w_{1},w_{2},\dots,w_{s} \}$ un insieme di $s$ classi disgiunte costituite da elementi di $V$.

Per ogni $x\in V$ e per ogni $w_{i}\in W$, indichiamo com $p(x\mid w_{i})$ la densità di probabilità condizionale che il prossimo pattern $x$ sia sotto l'ipotesi che la sua classe di appartenenza sia $x$.

Per ogni $w_{i}\in W$, indichiamo con $P(w_{i})$ la probabilità a priori di $w_{i}$, ovvero la probabilità che il prossimo pattern da classificare sia di classe $w_{i}$.

Per ogni $x\in V$ indichiamo con $p(x)$ la densità di probabilità assoluta di $x$, ovvero la densità di probabilità che il prossimo pattern da classificare sia $x$.

$$
p(x) = \sum_{i=1}^{s} p(x|w_{i})\cdot P(w_{i})
$$
*Dove*
$$
\sum_{i=i}^{s}P(w_{i}) = 1
$$

Per ogni $w_{i}\in W$ e per ogni $x\in V$ indichiamo con $P(w_i\mid x)$ la probabilità a posteriori di $w_{i}$ dato $x$, ovvero la probabilità che avendo osservato il pattern $x$, la classe di appartenenza sia $w_{i}$.


> [!cite] Per il teorema di Bayes
> $$P(w_{i}|x)=\frac{p(x|w_{i})\cdot P(w_{i})}{p(x)}$$

#### Classificatore di Bayes
> [!quote] Classificatore
> Dato un pattern $x$ da classificare in una delle $s$ classi $w_{1},w_{2},\dots,w_s$ di cui sono note
> - Le probabilità a priori $P(w_{1}), P(w_{2}),\dots,P(w_{s})$
> - Le densità di probabilità condizionali $p(x|w_{1}),p(x|w_{2}),\dots,p(x|w_{s})$

La ***regola di Bayes*** assegna $x$ alla classe $b$ per cui è massima la probabilità a posteriori:
$$
b = \arg\max_{i = 1, \dots, s}{\{ P(w_{i}|x) \}}
$$

Massimizzare la probabilità a posteriori significa massimizzare la densità di probabilità condizionale tenendo conto della probabilità a priori delle classi.

La regola si dimostra ottima in quanto minimizza l'errore di classificazione.

> Ad esempio nel caso di $2$ classi e $d=1$:

$$
P(\text{error}) = \int_{\Re_1}{p(x|{w_2}) P(w_{2})dx} + \int_{\Re_2}{p(x|{w_1}) P(w_{1})dx}
$$

![[attachements/BayesExample.png]]


> [!todo] Approcci
> Stimare le probabilità a priori è abbastanza semplice ma la conoscenza della densità condizionali è ***possibile solo in teoria***.

Nella pratica ci sono due soluzioni:
- Approccio parametrico
- Approccio non parametrico
	- Attraverso il metodo ***Parzen Window***
#### Approccio parametrico
Consiste nel fare ipotesi sulla forma delle distribuzioni e si apprendono i parametri fondamentali dal training set.
- Funziona solo per alcuni fenomeni (altezza ok)

[[../../Matematica Discreta e Probabilità/Probabilità/Variabili Continue/12 - Variabile Normale o Gaussiana|Distribuzione Normale]]

##### Distribuzione normale multivariata.
> [!Notazione] 
> Si usa a pedice l'indice del pattern e ad apice la componente scalare:
> - $x_{i}$: pattern $i$-esimo (vettore)
> - $x_{i}^{j}$ componente $j$-esima del pattern $i$-esimo (scalare).

La densità di probabilità nella distribuzione multinormale ($d>1$):
$$
p(x) = \frac{1}{(2\pi)^{d/2}\mid\Sigma\mid^{1/2}} e^{-\frac{1}{2}(x - \mu)^t\Sigma^{-1}(x - \mu)}
$$

> Dove:
- $\mu$ è il vettore medio.
- $\Sigma=[\sigma^{ij}]$ la matrice di covarianza $(d\times d)$.
- $|\Sigma|$ e $\Sigma^{-1}$ sono rispettivamente il determinante e l'inversa di $\Sigma$
- La matrice di covarianza è sempre simmetrica e definita positiva, pertanto ammette inversa.


Nel caso con $d=2$ la forma della distribuzione è quella di un'ellisse.
- $\mu$ è la posizione del centro.
- $\sigma^{11}$ e $\sigma^{22}$ determinano l'allungamento sui due assi dell'ellisse.
- $\sigma^{12}$ e $\sigma^{21}$ controlla la rotazione dell'ellisse rispetto agli assi cartesiani.

> Per calcolare $\mu$

$$
\mu = \frac{1}{n} \sum_{i=1,\dots,n}x_{i}
$$

> Per calcolare $\Sigma$

$$
\Sigma =\begin{bmatrix}
\sigma^{11} & \sigma^{12} & \dots & \sigma^{1d} \\
\sigma^{21} & \sigma^{22} & \dots & \dots \\
\dots & \dots & \dots & \dots \\
\sigma^{d1} & \dots & \dots & \sigma^{dd} \\
\end{bmatrix}, \quad\sigma^{ij}=\frac{1}{n}\sum_{k=1,\dots,n}(x_{k}^{i}-\mu^{i})(x_{k}^{j}-\mu^{j})
$$
O in notazione vettoriale:
$$
\Sigma = \frac{1}{n}\sum_{i=1,\dots,n}(x_{i}-\mu)(x_{i}-\mu)^{t}
$$
#### Distanza di Mahalobis
> [!cite] Definizione
> $$(x - \mu)^t\Sigma^{-1}(x - \mu)$$

Se tolgo la ***matrice di covarianza inversa***, $(x-\mu)$ sarebbe una semplice *distanza euclidea*
- Le diverse componenti della matrice tengono conto dei *relativi spazi di variazione* e della loro correlazione.

#### Distribuzioni Multinormali
> [!Example] Esempio
> Nell'esempio sono visualizzate le densità condizionali di due classi di pattern corrette sulla base delle rispettive ***probabilità a priori***.

![[attachements/MultinormalDistributions.png]]

Se la classificazione è eseguita usando la ***regola Bayesiana*** lo spazio è suddiviso in ***regioni non connesse***.


> [!caution] Decision Boundary
> Un ***decision boundary*** o ***decision surface*** è una zona di confine tra regioni che il classificatore associa a classi diverse.

Sul *boundary* la classificazione è ***ambigua***.

#### Approccio non Parametrico
> Non vengono fatte ipotesi sulle *distribuzioni dei pattern* e le densità di probabilità sono stimate **direttamente dal training set**.

In generale la stima della densità è affrontabile in spazi a dimensionalità ridotta.

> [!danger] Curse of Dimensionality
> La stima diventa ***critica*** al crescere della dimensionalità

*Esempio*:
- In un cubo `3D` di lato $1$ la distanza media di due punti è $0.66$.
- In un ipercubo con $1M$ di dimensioni, la distanza media di due punti è $408.25$.

La [[../Tipi di Machine Learning#Riduzione della dimensionalità|riduzione di dimensionalità]] è una delle tecniche possibili per contrastare la ***curse of dimensionality***.

##### Stima della Densità
> [!info] 
> La probabilità che un pattern $x$ cada all'interno di $\Re$ è:
> $$P_{1} =\int _{\Re} \,p(x^{'}) \text{d}x^{'} $$

Dati $n$ pattern indipendenti, la probabilità che $k$ di questi cadano nella regione $\Re$ è calcolabile attraverso la [[../../Matematica Discreta e Probabilità/Probabilità/3 - Variabili Aleatorie#Variabili Binomiali|distribuzione binomiale]].
$$
P_{k} =\binom{n}{k}P_{1}^{k}(1-P_{1})^{n-k}
$$
Il cui valore medio è $k=nP_{1}$

Ora, assumendo che la regione $\Re$ di volume $V$ sia piccola e che $p(\cdot)$ non vari significativamente all'interno di essa:
$$
P_{1}=\int _{\Re} \,p(x^{'}) \text{d}x^{'} \approx p(x)\cdot V
$$
$$
p(x)=\frac{P_{1}}{V} =\frac{k}{n\cdot V}
$$

> [!help] Parzen Window
> La regione $\Re$ denominata finestra è costituita da un ***ipercubo*** $d$-***dimensionale***, definito dalla funzione $\varphi$.

$$
\varphi(u) = \begin{cases}
1 \qquad |u_j|\leq \frac{1}{2}, \ j=1,\dots,d \\
0 \qquad \text{ else}
\end{cases}
$$
Dato un generico ***ipercubo*** centrato in $x$ e avente lato $h_{n}$ (volume $V_{n}=h_{n}^{d}$) il numero di pattern del training set che cadono all'interno dell'ipercubo è dato da:
$$
k_{n}=\sum_{i=1}^{n}\varphi\left( \displaystyle{\frac{x_{i}-x}{h_{n}}} \right) 
$$
Sostituendo $k_{n}$ si ottiene:
$$
p_{n}(x) = \frac{1}{n\cdot V_{n}} \sum_{i=1}^{n} \varphi \left( \displaystyle{\frac{x_{i}-x}{h_{n}}} \right)
$$

Dove:
- $V_{n}=h_{n}^{d}$

Nel caso in cui il numero di pattern non sia elevato, la dimensione della finestra $V_{n}$ ha un *forte impatto sul risultato*.
- Se la finestra è piccola, la stima risulta molto "**rumorosa**". Molto attratta dai campioni e statisticamente instabile.
- Se la finestra è grande la stima è più stabile ma piuttosto **vaga** e **sfuocata**.

> [!cite] Info
> Si dimostra che per ottenere convergenza, la ***dimensione della finestra*** deve essere calcolata tenendo conto del numero di campioni del training set:

$$
V_{n} = \frac{V_{1}}{\sqrt{ n }}
$$
Dove $V_{1}$ o $h_{1}$ è un ***iperparametro***.

> [!hint] Osservazione
> La ***stima della probabilità*** è uguale a quella con la *formula di Bayes*, l'unica differenza è l'utilizzo della **Parzen window** al posto della distribuzione normale multivariata.

###### Soft Kernel
> [!tldr] Idea
> Invece di finestra a ipercubo, si usano ***kernel function*** grazie alle quali ogni pattern $x_{i}$ contribuisce alla stima di densità in un intorno di $x$ in accordo con la distanza da $x$.

Le kernel function devono essere [[../../Matematica Discreta e Probabilità/Probabilità/3 - Variabili Aleatorie#Densità|funzioni densità]].

> Es. ***funzione multi normale***:

$$
\varphi(u) = \frac{1}{(2\pi)^{d/2}}e^{ \displaystyle{\frac{-u^{t}u}{2}} }
$$

![[attachements/ParzenWindow&SoftKernel.png]]