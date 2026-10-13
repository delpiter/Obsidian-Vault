## Support Vector Machines
---
> ***SVM*** è uno degli strumenti più utilizzati per la [[../Tipi di Machine Learning#Classificazione|classificazione]] di pattern.

> [!quote] Info
> Invece di stimare le densità di probabilità delle classi, *Vapnik* suggerisce di risolvere direttamente il problema di interesse, ovvero determinare le superfici decisionali tra le classi (***classification boundaries***).

Nasce come classificatore binario, estendibile a più classi.

Esistono diversi tipi di `SVM`, di seguito vengono trattati per gradi di avanzamento.

### SVM Lineare
> [!tldr] Idea
> Date due classi di [[../Dati e Pattern|pattern]] multidimensionali ***linearmente separabili***, tra tutti i possibili iperpiani di separazione `SVM` determina quello in grado di separare le classi con il *maggior margine possibile*.

Due insiemi si dicono ***linearmente separabili*** quando è possibile tracciare una retta, piano o *iperpiano* ($n$ dimensioni) che divide completamente i punti delle due classi.

Il margine è la distanza minima di punti delle due classi nel training set dall'***iperpiano*** individuato.

![[attachements/SVMMargin.png]]

La massimizzazione del ***margine*** è legata alla *generalizzazione*.
Se i pattern del training set sono classificati con **ampio margine** si può sperare che anche pattern del test set vicini al confine tra le classi siano gestiti correttamente.
- Possiamo vedere il problema con un ***problema di ottimizzazione vincolata***.
- Come tale ammette solo un **minimo globale**.

#### Geometria: Pattern Separabili
> [!Cite] Teoria
> Date due classi di pattern ***linearmente separabili*** e un training set contenente $n$ campioni $(x_{1},y_{1}),\dots,(x_{n},y_{n})$ dove $x_{i}\in \mathbb{R}^{d}$ sono i pattern multidimensionali e $y_{i}\in \{ 1, -1 \}$ le etichette delle classi.
>>[!done] Esistono diversi iperpiani in grado di eseguire la separazione voluta.

Un generico *iperpiano* è definito dai parametri $(w,b)$:
$$
D(x)=\underbrace{ w^{T}\cdot x }_{ \text{prod scalare} } +b
$$
> Dove
- $w$ è il vettore normale all'*iperpiano*
- $b/||w||$ è la distanza dell'*iperpiano* dall'origine
- $D(x)=0$ è il luogo dei vettori sul piano.

$$
x=x_{p}+r \frac{w}{||w||}, \qquad D(x_{p})=0
$$
$$
D(x)=w\cdot x+b=r \cdot||w||
$$

![[attachements/HyperPlane.png]]

La distanza di un vettore $x$ dall'iperpiano vale: $r=\frac{D(x)}{||w||}$.

Gli iperpiani $(w,b)$ che separano i pattern con distanza minima $\frac{1}{||w||}$ soddisfano per $i=1,\dots,n$, le equazioni:
- $w\cdot x_{i}+b\geq +1$ se $y_{i}=+1$
- $w\cdot x_{i}+b\leq -1$ se $y_{i}=-1$

O in modo più compatto:
$$
y_{i}[w\cdot x_{i}+b] \geq 1
$$


La minima distanza tra l'*iperpiano* di separazione e un pattern del **TS** e un pattern del training set è detta margine ($\tau$).

![[attachements/Margin.png]]

La distanza dei punti che giacciono sull'iperpiano $D(x)=+1$  dall'iperpiano di separazione $D(x)=0$ è $\frac{1}{||w||}$ e lo stesso vale per i punti dell'iperpiano $D(x)=-1$, pertanto il margine è $\tau=\frac{2}{||w||}$

> [!hint] Osservazione
> L'iperpiano ***ottimo*** $(w,b)$ secondo `SVM` è quello che soddisfa i vincoli di separazione dei pattern e massimizza il margine $\tau$.

- ***Minimizza***: $||w||^{2}/2$
- Con i ***vincoli***: $y_{i}[w\cdot x_{i}+b]-1 \geq 0\qquad \forall i\in1,\dots,n$ 

> [!info] Support Vector
> I pattern del training set che giacciono sul margine (cerchi pieni in figura), sono detti ***support vector***.

Tali pattern, che costituiscono i casi più complessi definiscono **completamente** la soluzione del problema che può essere espressa come funzione ***di solo tali pattern***.

##### Problema di Ottimizzazione
> [!help] Info
> Il problema di ottimizzazione può essere risolto passando a una formulazione ***Lagrangiana*** e successivamente una formulazione ***duale***.

> Formulazione Lagrangiana

Si introduce un moltiplicatore $\alpha_{i}$ per ogni vincolo nella forma:  *equazione* $\geq 0$ e si sottrae il vincolo moltiplicato per $\alpha_{i}$ dalla *funzione obbiettivo*.

$$
Q(w,b,\alpha) = \frac{1}{2}w^{T}\cdot w-\sum_{i=1}^{n}\alpha_{i}(\underbrace{y_{i} [w^{T}\cdot x_{i}+b]-1 }_{ \text{vincolo} })
$$
- Il coefficiente Lagrangiano $\alpha_{i}$ peggiora la soluzione trovata a fronte di una *violazione di un vincolo*.

Trasformando il problema in ***forma duale*** si possono esprimere i parametri $w$ e $b$ in funzione dei moltiplicatori $\alpha_{i}$.
- Elimina la dipendenza diretta da $w$ e $b$, permettendo la risoluzione massimizzando la funzione obbiettivo rispetto ai soli $\alpha_{i}$.

$$
Q(\alpha)=\sum_{i=1,\dots,n}\alpha_{i}-\frac{1}{2}\sum_{i,j=1,\dots,n}\alpha_{i}\alpha_{j}y_{i}y_{j}(x_{i}\cdot x_{j})
$$
con i vincoli
$$
\sum_{i=1,\dots,n} y_{i}\alpha_{i}=0 \qquad \text{ e }\qquad \alpha_{i}\geq 0 \text{ per }i=1,\dots,n 
$$


> Questo problema di ottimizzazione può essere risolto con un algoritmo di programmazione ***quadratica***.

> [!hint] Consiste nel derivare i valori ottimi di $\alpha_{1}^{*}, \alpha_{2}^{*}, \dots,\alpha_{n}^{*}$

Le condizioni del problema duale assicurano che $\alpha_{i}^{*}=0$ per tutti i vettori che **non** sono ***support vector***.

L'iperpiano ottimo è quindi:
$$
w^{*} =\sum_{i=1,\dots,n}\alpha_{i}^{*}y_{i}x_{i}
$$
$$
b^{*}=y_{s}-\sum_{i=1,\dots,n}\alpha_{i}^{*}y_{i}(x_{i}^{T}\cdot x_{s})
$$
Dove $(x_{s}, y_{s})$ è uno dei *support vector* e $w^{*}$ e $b^{*}$ sono i valori ottimi per inclinazione e posizione del piano.

La funzione della distanza dell'iperpiano sarà dunque:
$$
D(x)=w^{*}\cdot x +b^{*}=\sum_{i=1,\dots,n}\alpha_{i}^{*}y_{i}(x^{T}\cdot x_{i})+b^{*}
$$
- Ma molti $\alpha_{i}^{*}$ sono $0$ e quindi non è necessario salvarsi tutto il training set ma solo i pattern i cui support vector sono $\neq 0$


> [!question] Come classifico un pattern $x$?

Il segno della funzione $D(x)$ consente di classificare un generico pattern $x$.
- Guardando il $|D(x)|$, `SVM` fornisce le distanze, quindi la confidenza di classificazione, **NON** la *probabilità*.

#### Vantaggi

> [!done] Vantaggi di `SVM`
> 

- Definizione della soluzione sulla base di un numero *ridotto* di ***support vector***.
- Il numero di support vector $n_{sv}$ indica la ***complessità del problema***.
- L'errore medio è limitato da $n_{sv}/n$
- Scala molto bene rispetto alla *dimensionalità* $d$ dello ***spazio delle feature***.

#### SVM Lineare: Pattern non Separabili
> [!warning] Attenzione
> Non sempre tutti gli insiemi di pattern possono essere separati da ***un iperpiano***

È necessario ***rilassare i vincoli di separazione***, per far si che alcuni pattern (il minor numero possibile) possano valicare il confine della classe.

Vengono introdotte delle variabili di slack positive $\xi_i$ con $i=1,\dots,n$ e si modificano i vincoli di separazione.
- Permettono la violazione del vincolo introducendo un *malus* sulla soluzione.
$$
y_{i}[w^{T} \cdot x_{i}+b]\geq 1-\xi_{i}
$$
Per ogni pattern $x_{i}$ del *training set* la variabile $\xi_{i}$ codifica la deviazione dal margine.
![[attachements/RelaxedSVM.png]]

L'*iperpiano ottimo* deve ancora ***massimizzare il margine*** e allo stesso tempo minimizzare il numero di elementi *non correttamente classificati*.

Il problema di ottimizzazione viene così modificato:
> Minimizzare:

$$
\displaystyle{\frac{||w||^{2}}{2}}+C \sum_{i=1,\dots,n}\xi_{i}
$$
- $C$ è l'[[../../Metodi Numerici per L'Intelligenza Artificiale/Intelligenza Artificiale/Training#Iperparametri|iperparametro]] che indica quanto è importante il margine rispetto alla violazione dei vincoli.

> Vincoli:

$$
y_{i}[w^{T}\cdot x_{i} +b] \geq 1-\xi_{i} \qquad \text{per } i=1,\dots,n
$$

Passando attraverso la forma ***Lagrangiana/duale*** otteniamo un risultato *uguale al caso linearmente separabile* tranne che per l'introduzione del limite superiore $C$.
$$
Q(\alpha)=\sum_{i=1,\dots,n}\alpha_{i}-\frac{1}{2}\sum_{i,j=1,\dots,n}\alpha_{i}\alpha_{j}y_{i}y_{j}(x_{i}\cdot x_{j})
$$
Con i vincoli
$$
\sum_{i=1,\dots,n} y_{i}\alpha_{i}=0 \qquad \text{ e }\qquad \alpha_{i}\geq 0 \geq C \text{ per }i=1,\dots,n 
$$

![[attachements/SVMHyperparameter.png]]

### SVM non Lineari
> Per avere separazione dei pattern con superfici molto complesse

> [!tldr] Idea
> Viene definito un ***mapping*** $\Phi$ non lineare dei pattern dallo spazio di partenza $\mathbb{R}^{d}$ verso uno spazio $\mathbb{R}^{m}$ a più alta dimensionalità.

$$
\Phi:\mathbb{R}^{d}\to \mathbb{R}^{m} := \Phi(x)=[g_{1}(x),g_{2}(x),\dots,g_{m}(x)]
$$
Nello spazio $\mathbb{R}^{m}$ dove ci sono maggiori gradi di libertà i pattern possono essere più ***facilmente separati da un iperpiano usando la teoria nota***.
- I piani dello spazio esteso si mappano a delle superfici complesse nello spazio originale.


> [!hint] Osservazione
> Analizzando la formulazione del problema ***Lagrangiano-duale*** si nota che i vettori del training set appaiono solo in forma di prodotti scalari tra coppie di vettori.

Questa proprietà permette di evitare la manipolazione di vettori nello spazio $\mathbb{R}^{m}$.

Per opportuni mapping $\Phi$ è possibile ricondurre il prodotto scalare di due pattern in $\mathbb{R}^{m}$ in una funzione $K$ detta **kernel** dei due pattern originali nello spazio $\mathbb{R}^{m}$.

> Per funzionare la mappatura deve rispettare:

$$
\Phi(x)\cdot\Phi(x')=K(x,x')
$$


> [!cite] Teorema
> Per il ***teorema di Mercer*** se la funzione $K$ soddisfa alcuni requisiti, allora esiste un mapping $\Phi$ verso uno spazio di dimensionalità maggiore che gode della proprietà.

> [!example] Esempi
> 

> Polinomio di grado $q$

Le componenti $g_{i}(x)$ sono ottenute come tutte le possibili combinazioni di elevamento a potenze $\leq q$ delle compoenti di $x$.
Esempio per $d=2$ e $q=2$
$$
\Phi(x) = \Phi([x_{1},x_{2}]) = [1,x_{1},x_{2},x_{1}x_{2},x_{1}^{2},x_{2}^{2},x_{1}x_{2}^{2},x_{2}x_{1}^{2},x_{1}^{2}x_{2}^{2}]
$$
Quindi $m=9$
Si dimostra che:
$$
K(x,x')=[(x\cdot x')+1]^{q}
$$

> Radial Basis Function di ampiezza $\sigma$

$$
K(x,x')=e^{ \left( \displaystyle{\frac{||x-x'||^{2}}{2\sigma^{2}}} \right) }
$$

> Sigmoid

$$
K(x,x')=\tanh(v(x\cdot x')+a)
$$
- $v$ e $a$ devono essere scelti opportunamente come $1$ e $1$.

> [!done] Kernel Trick
> Usando il ***kernel trick*** si può risolvere il problema di ottimizzazione senza particolari complicazioni rispetto al caso lineare.

$$
D(x)=\sum_{i=1,\dots,n}\alpha_{i}^{*}y_{i}K(x,x_{i})+b^{*}
$$
### Estensione Multiclasse
> [!question] Come gestire i problemi con più di $2$ classi?

Due approcci

> [!help] One against one

> [!summary] One against All
> Date $s$ classi $w_{1},w_{2},\dots,w_{s}$ per ogni classe $w_{k}$ si determina con `SVM` la superficie di separazione tra i pattern $w_{k}$ ($+1$) da una parte e i pattern di tutte le altre classi $w_{h}$ con $h\neq k$ ($-1$) dall'altra.

Si ottiene una funzione $D_{k}(x)$ che indica quanto $x$ è distante dalla superficie decisionale in direzione di $w_{k}$
- Maggiore è $D_{k}(x)$ più confidenti siamo dell'appartenenza di $x$ a $w_{k}$

Al termine del training si assegna il pattern $x$ alla classe $k^{*}$ per cui è massima la distanza dalla superficie decisionale.
$$
k^{*}=\arg \max_{k}\{ D_{k}(x) \}
$$
- È necessario eseguire $s$ training `SVM`

### SVM in Pratica

> [!question] Quando usare `SVM`?
> 

`SVM` permette di ottenere buoni risultati su ***dati numerici omogenei*** anche di elevata dimensionalità.
- Meno performante di multi classificatori basati su alberi decisionali su *dati tabulari eterogenei*.


> [!question] Lineare o Non Lineare?
> 

- Con dimensionalità alta ($> 5000$ dimensioni) si utilizza `SVM` **lineare**.
- Con dimensionalità bassa ($\sim20$ feature) si usa la non lineare con kernel `RBF`
- Con dimensionalità media ($\sim 200$) si provano entrambe le tipologie