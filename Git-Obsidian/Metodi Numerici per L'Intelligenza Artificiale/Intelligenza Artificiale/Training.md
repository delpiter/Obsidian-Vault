![[../../Machine Learning/Reti Neurali/Training|Training]]
## Learning Rate
---
>[!question] Come scegliere il Learning Rate?

>[!definizione]
>Una funzione $f:\mathbb{R}^{n}\to \mathbb{R}$ è detta ***lipshitziana*** se esiste una costante $L>0$ tale che per ogni coppia di punti $x,y\in\mathbb{R}^{n}$ valga la seguente *disuguaglianza*:
>$$\| f(x)-f(y) \| \leq L\| x-y \| $$
>>[!quote] Significato
>> Una funzione Lipschitziana ha una ***crescita limitata***, la *variazione verticale* della funzione in due punti del dominio **non può** essere più grande della *variazione orizzontale* moltiplicata per $L$ (*costante di Lipschitz*).

> Esempio

La funzione $f(x)=\sin(x)$ è una funzione lipschitziana con costante $L=1$.
```functionplot
---
title: 
xLabel: 
yLabel: 
bounds: [-4,4,-4,4]
disableZoom: false
grid: true
---
f(x)=sin(x)
g(x)=x
h(x)=-x
```
>[!check] Teorema
> Ipotizziamo che $f:\mathbb{R}^{n}\to \mathbb{R}$ sia una funzione *convessa e differenziabile* con gradiente $\nabla f(x)$ *continuo* di **Lipschitz** con costante $L$, e che esista  $x^{*}$ tale che $\nabla f(x^{*})=0$ cioè esiste un ***punto stazionario***.
> <u>Allora</u>
> La *successione degli iterati* del metodo della discesa del gradiente:
> $$x^{k+1}=x^{k}-\eta \nabla f(x^{k})$$
> converge ad $x^{*}$ a patto che
> $$0<\eta< \frac{2}{L}$$ 

 Sfortunatamente *quasi tutti i problemi* di ottimizzazioni nell'allenamento di reti neurali sono ***non convessi***.

#### Importanza del Learning Rate
>[!missing] Valori Bassi di $\eta$

- Possono far si che sia necessario un ***numero elevato di passi*** prima che l'allenamento sia completato.
- Possono far si che i pesi ***rimangano bloccati in un minimo locale***, che è *sub ottimale*.

>[!abstract] Valori Alti di $\eta$

- Permettono di mitigare questi problemi e passando oltre i minimi locali, raggiungendo il minimo in un ***numero limitato di passi***.
- Può succedere che i pesi *oltrepassino* il ***minimo target***.

### Gradient Descent con Momentum
> Metodo che risolve i problemi introdotti dalla non convessità della ***funzione loss***.

>[!failure] Momentum
>Il ***momentum*** è una tecnica usata per accelerare la convergenza e ridurre le oscillazioni durante l'allenamento con il [[../Metodi di Discesa/Metodi di Discesa#Steepest Descent|Gradient Descent]].
>Si introduce una variabile aggiuntiva chiamata $v^{(k)}$ (*momentum*).
>- Il *momentum* al passo $k$ è una combinazione della **velocità al passo precedente** e del **gradiente corrente**.
>
>$$v^{(k)}=\beta v^{(k-1)}\nabla C(w^{(k)})$$
>
>$\beta$ prende il nome di ***coefficiente di momentum*** ($0\leq\beta< 1$).

L'aggiornamento dei pesi diventa:
$$
w^{(k+1)}=w^{(k)}-\eta v^{(k)}
$$
> Si basa sullo stesso concetto di momentum, *quantità di moto*, in ***fisica***.

### Learning Rate Adattivo
> Uno degli iperparametri più *difficili da regolare*.

 >[!info] Learning Rate Basso 
> La funzione costo diminuisce ma *richiede molto* più **tempo** per converge

>[!failure] Learning Rate Alto
> La funzione costo  ***raggiunge un valore*** migliore di quello  iniziale,ma è ancora lontano da un valore ottimale.

>[!summary] Learning Rate Molto Alto
>La funzione costo *inizialmente diminuisce* poi inizia ad **aumentare**

>[!missing] Learning Rate Buono 
> La funzione costo  ***diminuisce costantemente*** fino a raggiungere 
il valore minimo possibile

![[attachements/AdaptiveLearningRate.png|400]]
#### Learning Rate Scheduling
> Un learning rate alto è auspicabile all'inizio, uno basso è più appropriato nella fase finale.

##### Step Decay
>[!tldr] Idea
> Riduce il learning rate iniziale $\eta_{0}$ di un fattore $\delta$ ogni numero predefinito di *epoche*.

$$
\eta=\eta_{0}\cdot\delta^{\left \lfloor\ \displaystyle\frac{n}{s} \right\rfloor} 
$$

- $\eta_{0},\delta$ e $s$ sono iperparametri, $n$ è l'*iterazione corrente*.
```functionplot
---
title: 
xLabel: 
yLabel: 
bounds: [0,100,0,0.1]
disableZoom: true
grid: true
---
f(x)=0.1*pow(0.5, floor(x/10))
```

##### Exponential Decay
>[!tldr] Idea
>Il ***decadimento esponenziale*** ha la seguente forma matematica:
>$$\eta = \eta_{0}\cdot e^{-\delta n}$$


```functionplot
---
title: 
xLabel: 
yLabel: 
bounds: [0,100,0,0.1]
disableZoom: true
grid: true
---
f(x)=0.1*exp(-0.5*x)
```

##### Time Decay
>[!tldr] Idea
>***Decadimento basato sul tempo***:
>- Modifica il learning rate iniziale in funzione del *numero di iterazioni eseguite* (n).
>
>$$\eta = \displaystyle{\frac{\eta_{0}}{1+\delta\cdot n}}$$


```functionplot
---
title: 
xLabel: 
yLabel: 
bounds: [0,100,0,0.1]
disableZoom: true
grid: true
---
f(x)=0.1/(1+0.5*x)
```

##### A Confronto

```functionplot
---
title: Adaptive Learning Rate
xLabel: Epochs 
yLabel: Learning Rate
bounds: [0,100,0,0.1]
disableZoom: true
grid: true
---
f(x)=0.1*pow(0.5, floor(x/10))
f(x)=0.1*exp(-0.5*x)
f(x)=0.1/(1+0.5*x)
```

### Metodi di Aggiornamento Adattivo del Learning Rate
#### Adagrad
>[!info] Adaptive Gradient Algorithm
>***Adagrad*** adatta il *Learning Rate* ai parametri, eseguendo aggiornamenti più **grandi** per i parametri *poco frequenti* e aggiornamenti più **piccoli** per quelli *frequenti*.

$$
s_{j}^{(k)}=s_{j}^{(k-1)}+(\nabla C(w_{j}^{(k)}))^{2}
$$
$$
w^{(k+1)}_{j}=w_{j}^{(k)}-\displaystyle{\frac{\eta}{\sqrt{ s_{j^{(k)}+\varepsilon} }}}\nabla C(w_{j}^{(k)})
$$
- Minore è il gradiente accumulato, minore sarà il valore di $s_{k}$, ciò porta a un ***learning rate maggiore***.

> ***Effetti***:
- Aggiornamenti più *grandi* per parametri più **rari**.
- Aggiornamenti più *piccoli* per parametri **frequenti**.
- Riduzione del rischio di **sovrastima**.

#### RMSProp
>[!info] Root Mean Square Propagation
>***RMSProp*** è stato introdotto per *ridurre la diminuzione aggressiva del learning rate* di **Adagrad**.
>Modifica la parte di *accumulo del gradiente* di Adagrad con una ***media ponderata esponenziale*** dei gradienti al quadrato invece della somma dei gradienti al quadrato.

$$
s_{j}^{(k)}=\gamma s_{j}^{(k-1)}+(1-\gamma)(\nabla C(w_{j}^{(k)}))^{2}\qquad \gamma>0
$$
$$
w^{(k+1)}_{j}=w_{j}^{(k)}-\displaystyle{\frac{\eta}{\sqrt{ s_{j^{(k)}+\varepsilon} }}}\nabla C(w_{j}^{(k)})
$$

> ***Effetti***:
- Riduzione del *decadimento aggressivo*.
- Maggiore *stabilità*.
- *Convergenza* più affidabile.

#### ADAM
>[!info] Adaptive Moment Estimation
>L'obiettivo principale di ***ADAM*** è quello di combinare i vantaggi di due altri algoritmi di ottimizzazione: *RMSprop* e *Momentum*.

- Utilizza la ***media pesata esponenziale*** dei gradienti ai passi precedenti, per ottenere una *stima del momento* del gradiente per ogni parametro.
$$
v_{j}^{(k)}=\beta_{1} v_{j}^{(k-1)}+(1-\beta_{1})\nabla C(w_{j}^{(k)})
$$
- E del momento secondo del gradiente
$$
s_{j}^{(k)}=\beta_{2} s_{j}^{(k-1)}+(1-\beta_{2})(\nabla C(w_{j}^{(k)}))^{2}
$$


L'equazione di aggiornamento diventa:
$$
w_{j}^{(k+1)}=w_{k}^{(k)}-\frac{\eta}{\sqrt{ \hat{s}_{j}^{(k)}+\varepsilon }}\hat{v}_{j}^{(k)}
$$

**ADAM** adatta in modo dinamico il learning rate per ciascun parametro del modello utilizzando le ***stime del momentum*** del *primo e del secondo grado*.