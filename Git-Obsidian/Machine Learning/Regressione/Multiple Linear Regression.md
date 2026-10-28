## Multiple Linear Regression
---
> Generalizziamo a iperpiani per $x\in\mathbb{R}^{d}$

> Sia $X$ la matrice rettangolare $(n\times (d+1))$ ottenuta inserendo sulle righe gli $n$ pattern del training set e inserendo a destra una colonna con tutti i valori $1$.
- Questa ultima colonna servirà per ***gestire il termine noto*** senza una gestione specifica.

$$
X=\begin{bmatrix}{}
x_{11} & \dots & x_{1d}  &  1 \\
x_{21} & \dots & x_{2d}  &  1 \\
\dots & \ddots & \dots & \dots \\
x_{n1} & \dots & x_{nd}  &  1 
\end{bmatrix}
$$
> Siano

$$
y=\begin{bmatrix}{}
y_{1} \\
y_{2} \\
\vdots \\
y_{n}
\end{bmatrix} \qquad \beta=\begin{bmatrix}
\beta_{1} \\
\beta_{2} \\
\vdots \\
\beta_{d+1}
\end{bmatrix}
$$


I ***vettori*** costruiti a partire dai valori della *variabile indipendente* e dai $d+1$ parametri da determinare.

> [!cite] Generalizzazione
> Le relazioni tra variabili indipendenti e dipendente possono essere scritte attraverso le equazioni:
> $$y_{i}=\sum_{j=1,\dots,d+1}x_{ij}\cdot\beta_{j}\qquad i=1,\dots,n$$

O in forma matriciale come:
$$
y=X\beta
$$
Per $n>(d+1)$ abbiamo che $X$ è rettangolare, quindi il sistema di equazioni è [[../../Metodi Numerici per L'Intelligenza Artificiale/Equazioni Lineari/Sistemi Sovradeterminati|sovradeterminato]].

La funzione obbiettivo da minimizzare può essere scritta come:
$$
\| y-X\beta\|^{2}
$$
Ancora una volta le *equazioni normali* possono essere ottenute ***derivando rispetto ai parametri***.
$$
(X^{t}X)\beta^{*}=X^{t}y
$$
Infine invertendo, otteniamo i parametri del modello:
$$
\beta^{*}=(X^{t}X)^{-1}X^{t}y
$$

### Note

> [!hint] Se $n=(d+1)$

La matrice $X$ è quadrata e l'iperpiano di regressione tocca tutti i punti ([[../../Metodi Numerici per L'Intelligenza Artificiale/Interpolazione/Interpolazione Polinomiale|Interpolazione]]).


> [!summary] Se $n>(d+1)$
> 

Significa che il numero di equazioni è **superiore** al numero di incognite e l'iperpiano *approssima i punti*.


> [!caution] Invertibile
> 

Per essere ***invertibile*** la matrice $X^{t}X$ deve essere a rango massimo.
- Ci possono essere problemi nel caso di punti collineari.


> [!fail] Malcondizionamento

La matrice $X^{t}X$ è spesso [[../../Metodi Numerici per L'Intelligenza Artificiale/Equazioni Lineari/Condizionamento di un Sistema Lineare|mal condizionata]].
- Il problema può essere risolto in modo più stabile usando la [[../../Metodi Numerici per L'Intelligenza Artificiale/Equazioni Lineari/Problema Minimi Quadrati#Decomposizione in Valori Singolari|Decomposizione in Valori Singolari]] o `SVD`.

Si dimostra che:
$$
\beta^{*} =V\Gamma^{+}U^{t}y
$$
- Dove $\Gamma^{+}$ è la pseudo inversa di $\Gamma$

#### Esempio
> Stima del prezzo delle case

Il ***California housing dataset*** contiene $20640$ pattern, ciascuno riferito a un quartiere in California.
- I pattern sono vettori $9$ dimensionali, dove la variabile indipendente è costruita dal seguente vettore:
	- $[\text{MedInc},\text{ HouseAge},\text{ AveRooms}, \text{ AveBedrms}, \text{ Population}, \text{ AveOccup}, \text{ Lat}, \text{ Long}]$
	- La variabile dipendente è il valore target dal costo medio delle case nel quartiere ($1\equiv 100K\$$).

Dopo il  training, il root mean square error è di circa
- $0.723$ nel training set
- $0.727$ nel test set.

### Accuratezza di predizione
> [!cite] Root Mean Square Error
> `RMSE` è la radice quadrate del criterio `MSE` (*mean square error*)
> $$\frac{1}{n}\sum_{i=1,\dots,n}(\text{pred}_{i}-\text{true}_{i})^{2}$$
> ***implicito*** nell'ottimizzazione least square del modello lineare.

Altri modi di valutare l'accuratezza di predizioni (non direttamente utilizzabili come loss per il modello lineare) sono:

> [!hint] Mean Absolute Error 
> $$\frac{1}{n}\sum_{i=1,\dots,n}|\text{pred}_{i}-\text{true}_{i}|$$

Più robusta di `MSE` rispetto ai dati outliers, mantenendo l'unità di misura.


> [!caution] Mean Absolute Percentage Error
> $$\frac{1}{n}\sum_{i=1,\dots,n} \left| \displaystyle{\frac{\text{pred}_{i}-\text{true}_{i}}{\text{true}_{i}}} \right| $$

Una variante del `MAE` dove la penalizzazione dipende dallo scostamento percentuale rispetto alla grandezza dei pattern.

>Esempio
- Misurazione dei pesi dei polli, con errore possibile di qualche decina di grammi.
	- Se la misurazione viene fatta ad un pulcino l'errore conta di più.

### Variabile indipendente non Lineare
> Con un semplice accorgimento è possibile continuare ad usare la regressione lineare per approssimare i dati con curve e superfici.


> [!tldr] Idea
> Nella teoria introdotta l'importante è che la funzione di regressione sia ***lineare rispetto ai parametri*** non alla variabile indipendente, i cui elementi possono comparire elevati a potenza, combinati, come argomento di funzioni, etc.

> Esempio: per $d=1$ e modello quadratico $y=\beta_{1}x^{2}+\beta_{2}x+\beta_{3}$

Scriviamo $X$ come:
$$
X=\begin{bmatrix}
x_{1}^{2} & x_{1} & 1 \\
x_{2}^{2} & x_{2} & 1 \\
\vdots & \vdots & \vdots \\
x_{n}^{2} & x_{n} & 1 \\
\end{bmatrix}
$$

Ottenendo:
![[attachements/NonLinearIndependentVar.png]]

## Regressione non Lineare
---
### Dipendenza Nota
> [!info] 
> Nel caso di ***dipendenza non lineare*** del modello dai parametri, non esiste soluzione Least Square in "*forma chiusa*".

Se la dipendenza ***è nota***, per la risoluzione si possono applicare tecniche iterative di ottimizzazione numerica come
- [[../../Metodi Numerici per L'Intelligenza Artificiale/Metodi di Discesa/Metodi di Discesa|Gradient Descent]]
- Gauss-Newton

### Dipendenza Sconosciuta
> [!todo] Tecniche
> Per alcune tecniche di ***classificazione*** esiste una variante efficace per *problemi di regressione*.

Alcuni casi notevoli sono i seguenti

> [!hint] Reti neurali
> Anche le reti neurali addestrate con back propagation consentono di risolvere efficacemente problemi di regressione. #addLink
##### Support Vector Regressor
> A partire dal modello [[../Classificazione/Support Vector Machines|SVM]]

Rispetto alla classificazione, qui si inverte la logica:

> [!tldr] Idea
> Vogliamo che nella fascia de margine ***ricada il maggior numero di pattern*** del training set.

![[attachements/SupportVectorRegressor.png]]

L'approssimazione può essere **lineare** o **non-lineare**.

L' [[../../Metodi Numerici per L'Intelligenza Artificiale/Intelligenza Artificiale/Training#Iperparametri|iperparametro]] $C$ e i regolarizzatori del ***kernel*** permettono il controllo dell'overfitting.
##### Random Forest Regressor
>[!tldr] Idea
>Stessa logica di creazione della [[../Classificazione/Multi-Classificatori ad Albero#Random Forest|foresta]] con ***doppio bagging*** su feature e pattern, ma con gli alberi `CART` usati come *regressori*.

In questo caso ogni nodo (*foglie comprese*) predice un valore pari alla media delle $y$ dei pattern ad esso appartenenti.
- La regola di suddivisione indotta dalla coppia minimizza l'`MSE` delle $y$ nei due nodi figli.

![[attachements/RandomTreeRegressor.png]]

Produce un'***approssimazione costante a tratti***.
L'iperparametro della profondità degli alberi è il principale regolarizzante per il ***controllo dell'overfitting***.

##### Gradient Boosting Regressor Trees
> [!tldr] Idea
> Tecnica di ***boosting*** che aggiunge iterativamente *nuovi regression tree* addestrati sui residuali.

Il multi classificatore si ottiene ***sommando i contributi*** dei singoli regressori.
![[attachements/GradientBoostingRegressor.png]]
#### Vantaggi
> I vantaggi di un modello ***non lineare*** sono i seguenti

> [!caution] Maggiore flessibilità
> Data dai più gradi di libertà.

> [!check] Controllo della complessità della soluzione

> [!swap] Loss Alternative
> Possibilità di utilizzare loss alternative rispetto a `MSE`, come `MAE` e `MAPE`
