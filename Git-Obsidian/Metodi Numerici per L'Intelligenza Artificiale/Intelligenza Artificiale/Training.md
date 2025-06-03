> Il processo di apprendimento è una caratteristica chiave delle [[Reti Neurali|ANN]].

> [!failure] Iterativamente
> 1. I dati di addestramento vengono passati attraverso la rete per ***calcolare le predizioni***.
> 2. Si confrontano le predizioni della rete con i valori desiderati usando una [[Reti Neurali#Cost e Loss Function|funzione loss]].
> 3. I pesi della rete vengono aggiornati iterativamente nella ***direzione che minimizza la loss***.

> ***Epoca***:
- Il processo si ripete per più iterazioni (*epoche*), presentando ogni volta i dati di addestramento, finché la rete non converge o la *performance è soddisfacente*
## Forward Propagation
---
>[!info]
>Con ***forward propagation*** si intende la propagazione delle informazioni in avanti dal livello di *input* a quello di *output*.

Sia $f$ la [[Neurone#Funzioni di Attivazione|funzione di attivazione]].
$$
a_{i}^{(\mathscr{l})}=\sum_{j=1}^{n^{(\mathscr{l})}}w_{ji}^{(\mathscr{l})}z_{j}^{(\mathscr{l}-1)}
$$
$$
z_{i}^{(\mathscr{l})}=f(a_{i}^{(\mathscr{l})})
$$
> Sia $\hat{y}=[\hat{y}_{1},\hat{y}_{2},\dots,\hat{y}_{s}]$ l'output prodotto dalla rete con l'input $x=[x_{1},x_{2},\dots,x_{d}]$.
- $y=[y_{1},y_{2},\dots,y_{s}]$ è il **vettore delle etichette corrispondente**.

Scegliamo come ***loss function*** la somma dei quadrati degli errori.
$$
L(y,\hat{y}(w))=\frac{1}{2}\sum_{i=1}^{s}(y_{i}-\hat{y}_{i}(w))^{2}=\frac{1}{2}\| y-\hat{y}(w) \|_{2}^{2} 
$$
- Con $w=\{ w^{(1)},w^{(2)},\dots,w^{(l)} \}$, dove $w^{(j)}$ rappresenta l'insieme dei pesi al layer $j$-esimo

> Il problema diventa un problema di minimizzazione:

$$
w^{*}=\underset{ w }{ \arg\min }\left\{  C(w)=\frac{1}{n_{T}}\sum_{j=1}^{n_{T}}L(y^{(j)},\hat{y}^{(j)}(w))  \right\}
$$
- Ci limitiamo a supporre che $C(w)$ sia una funzione ***continuamente differenziabile***.
## Backwards Propagation
---
> Legato alla tecnica usata per il calcolo delle derivate della funzione di errore sulle regole di ***derivazione delle funzioni composte***.

Per calcolare il vettore dei pesi:
$$
w^{*}=\{ w^{(1)},\dots,w^{(l)} \}\in\underset{ w }{ \arg\min }\ C(w)  =\frac{1}{n_{T}}\sum_{j=1}^{n_{T}}L(y^{(j)},\hat{y}^{(j)}(w))
$$
ricorriamo al [[Metodi di Discesa#Steepest Descent|metodo del gradiente]].
$$
w^{(k)}=w^{(k-1)}-\eta \nabla C(w^{(k-1)})
$$
- Dove $\eta$ rappresenta lo ***step-size***.

>[!question] Risulta necessario calcolare $\nabla C(w)$

- Sfrutta la tecnica della ***Chain Rule***

>[!help] Derivata composta di funzioni di più variabili reali
>Sia $x(t)=(x_{1}(t),x_{2}(t),\dots,x_{n}(t))^{T}$ un vettore di $\mathbb{R}^{n}$ le cui componenti sono $n$ funzioni derivabili.
>Sia $f:\mathbb{R}^{n}\to \mathbb{R}$ una funzione differenziabile in $x(t)$.
>La funzione composta $F(t)=f(x(t))$ ***è differenziabile*** in $t$ e si ha:
>$$F'(t)= <\nabla f(x(t)),x'(t)>$$

##### Esempio
> Consideriamo una rete ***MLP*** formata da un nodo di input, uno di output, 2 layer nascosti costituiti da un solo neurone.

Per ottenere l’insieme di pesi $w=[w_{11}^{(1)},w_{11}^{(2)},w_{11}^{(3)} ]$ ricorreremo al metodo di discesa del gradiente.
- $k^{k+1}=w^{k}-\eta\nabla L(w^{k})$

Calcoliamo $\nabla L$:
- Derivata parziale di $L$ rispetto a $w_{11}^{(3)}$:
$$
L(\hat{y}_{1})=L(z_{1}^{(3)})=L(z_{1}^{(3)}(a_{1}^{(3)}))=L(z_{1}^{(3)}(a_{1}^{(3)}(w_{11}^{(3)})))
$$
$$
\displaystyle\frac{ \partial L }{ \partial w_{11}^{(3)} }=\displaystyle\frac{ \partial L }{ \partial z_{1}^{(3)} }\displaystyle\frac{ \partial z_{1}^{(3)} }{ \partial a_{1}^{(3)} }\displaystyle\frac{ \partial a_{1}^{(3)} }{ \partial w_{11}^{(3)} }    
$$
> $\displaystyle\frac{ \partial L }{ \partial z_{1}^{(3)} }$
- Si calcola *facilmente*, derivando rispetto all'output della rete l'espressione analitica della ***loss-function***.

$$
\displaystyle\frac{ \partial L }{ \partial z_{1}^{(3)} }=\displaystyle\frac{ \partial L }{ \partial \hat{y}_{1} } 
$$

> $\displaystyle\frac{ \partial z_{1}^{(3)} }{ \partial a_{1}^{(3)} }$
- Sapendo che $z_{1}^{(3)}=f(a_{1}^{(3)})$
$$
\displaystyle\frac{ \partial z_{1}^{(3)} }{ \partial a_{1}^{(3)} }=f'(a_{1}^{(3)})
$$

> $\displaystyle\frac{ \partial a_{1}^{(3)} }{ \partial w_{11}^{(3)} }$
- $a_{1}^{(3)}=w_{11}^{(3)}z_{1}^{(2)}$
$$
\displaystyle\frac{ \partial a_{1}^{(3)} }{ \partial w_{11}^{(3)} }=z_{1}^{(2)} 
$$

>[!done] Conclusione

$$
\displaystyle\frac{ \partial L }{ \partial w_{11}^{(3)} }= \displaystyle\frac{ \partial L }{ \partial \hat{y}_{1} } f'(a_{1}^{(3)})z_{1}^{(2)}
$$

- Derivata parziale di $L$ rispetto a $w_{11}^{(2)}$:
$$
L(\hat{y}_{1})=L(z_{1}^{(3)})=L(z_{1}^{(3)}(a_{1}^{(3)}))=L(z_{1}^{(3)}(a_{1}^{(3)}(z_{1}^{(2)})))=L(z_{1}^{(3)}(a_{1}^{(3)}(z_{1}^{(2)}(a_{1}^{(2)}(w_{11}^{(2)})))))
$$
$$
\displaystyle\frac{ \partial L }{ \partial w_{11}^{(3)} }=\displaystyle\frac{ \partial L }{ \partial z_{1}^{(3)} }\displaystyle\frac{ \partial z_{1}^{(3)} }{ \partial a_{1}^{(3)} }\underbrace{ \displaystyle\frac{ \partial a_{1}^{(3)} }{ \partial z_{1}^{(2)} } }_{ w_{11}^{(3)} }\underbrace{ \displaystyle\frac{ \partial z_{1}^{(2)} }{ \partial a_{1}^{(2)} } }_{ f'(a_{1}^{(2)}) }\underbrace{ \displaystyle\frac{ \partial a_{1}^{(2)} }{ \partial w_{11}^{(2)}} }_{ z_{1}^{(1)} }   
$$
> Quindi:

$$
\displaystyle\frac{ \partial L }{ \partial w_{11}^{(3)} }=\displaystyle\frac{ \partial L }{ \partial \hat{y}_{1} }f'(a_{1}^{(3)})w_{11}^{(3)}f'(a_{1}^{(2)})z_{1}^{(1)} 
$$

- Derivata parziale di $L$ rispetto a $w_{11}^{(1)}$

$$
\displaystyle\frac{ \partial L }{ \partial w_{11}^{(1)} }= \displaystyle\frac{ \partial L }{ \partial \hat{y}_{1} }f'(a_{1}^{(3)})w_{11}^{(3)}f'(a_{1}^{(2)})w_{11}^{(2)}f'(a_{1}^{(1)})z_{1}^{(0)}
$$
>[!hint] Alcune Semplificazioni

*Poniamo*:
- $\delta_{1}^{(3)}=\displaystyle\frac{ \partial L }{ \partial \hat{y}_{1} }f'(a_{1}^{(3)})$
- $\delta_{1}^{(2)}=\delta_{1}^{(3)}w_{11}^{(3)}f'(a_{1}^{(2)})$
- $\delta_{1}^{(1)}=\delta_{1}^{(2)}w_{11}^{(2)}f'(a_{1}^{(1)})$

> Le formule del gradiente della loss function $L$ rispetto a tutti i pesi sono:

$$
\begin{array}
\ \displaystyle\frac{ \partial L }{ \partial w_{11}^{(3)} }=\delta_{1}^{(3)} z_{1}^{(2)} \\
\displaystyle\frac{ \partial L }{ \partial w_{11}^{(2)} }=\delta_{1}^{(2)} z_{1}^{(1)} \\
\displaystyle\frac{ \partial L }{ \partial w_{11}^{(1)} }=\delta_{1}^{(1)} z_{1}^{(0)}
\end{array}
$$
>[!summary] Conclusione
>L'***aggiornamento dei pesi per l'epoca successiva*** sarà la seguente:
>$$w^{k+1}=w^{k}-\eta \nabla L(w^{k})$$

> Omettendo gli indici $k$ e $k+1$ dell'epoca:

$$
\begin{array}
\ w_{11}^{(3)}=w_{11}^{(3)}-\eta \delta_{1}^{(3)}z_{1}^{(2)} \\
w_{11}^{(2)}=w_{11}^{(2)}-\eta \delta_{1}^{(2)}z_{1}^{(1)} \\
w_{11}^{(1)}=w_{11}^{(1)}-\eta \delta_{1}^{(1)}x_{1}
\end{array}
$$

>[!example] Riassumendo:

$$
\displaystyle\frac{ \partial L }{ \partial w_{ji}^{(l)} }=\delta_{i}^{(l)}z_{j}^{(l-1)} 
$$
- Dove, se il neurone $i$, appartiene al layer di uscita $L$:
$$
\delta_{i}^{(L)}=\displaystyle\frac{ \partial L(\hat{y}_{i}) }{ \partial a_{i}^{(L)} }=f'(a_{i}^{(L)})\displaystyle\frac{ \partial L(\hat{y}_{i}) }{ \partial \hat{y}_{i} }
$$

## Tecniche di Ottimizzazione del Gradiente
---
### Batch Gradient Descent
>[!definizione]
>Per il calcolo della funzione costo $C(w)$ vengono usati tutti i campioni del training set:
>$$w^{*}\in \arg\min_{w}\left\{  C(w)=\frac{1}{n_{T}}\sum_{j=1}^{n_{T}}L(y^{(j)},\hat{y}^{(j)})  \right\}$$

> *Idea*:
- Si considera l'intero set di addestramento
- Si esegue la forward propagation e si calcola la funzione di costo
- Si aggiornano i parametri usando il tasso di variazione della funzione costo

>[!warning] Attenzione
>Se molti dati sono presenti nel set di addestramento, non è possibile calcolare la funzione di costo.

> Metodo ideale ma realmente irrealizzabile
### Stochastic Gradient Descent
>[!tldr] Idea
>Si utilizza una ***singola osservazione*** per calcolare la funzione di costo.
>Passiamo una sola osservazione alla volta, calcoliamo il costo e aggiorniamo i parametri.

Ogni aggiornamento viene chiamato ***iterazione***.

### Mini-Batch Stochastic Gradient Descent
>[!tldr] Idea
>Per calcolare la funzione di costo si considera un ***sottoinsieme dell'intero set di dati***.
>Si divide il set in *diversi set più piccoli*, e si esegue la back propagation ogni volta che un mini-set viene esaurito.

## Iperparametri
---
>[!info]
>Gli ***iperparametri*** sono parametri esterni al modello di [[Machine Learning]] che devono essere impostati *prima* dell'avvio del processo di addestramento.

>[!example] Gli iperparametri sono:

1. *Learning Rate*
2. Numero di *Epoche*
3. Dimensione del *Mini-Batch*
4. *Architettura* del Modello
5. *Regolarizzazione*
6. Inizializzazione dei *Pesi*
7. [[Neurone#Funzioni di Attivazione|Funzione di Attivazione]]

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
>Il ***momentum*** è una tecnica usata per accelerare la convergenza e ridurre le oscillazioni durante l'allenamento con il [[Metodi di Discesa#Steepest Descent|Gradient Descent]].
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

![[AdaptiveLearningRate.png|400]]
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
s_{j}^{(k)}=s_{j}^{(k+1)}+(\nabla C(w_{j}^{(k)}))^{2}
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

> $v^{0}=0$ e $s^{0}=0$ sono *sbilanciati*, per compensare, si usano le seguenti normalizzazioni:

$$
\hat{v}_{j}^{(k)}=\displaystyle{\frac{v_{j}^{(k)}}{1-\beta_{1}^{k}}} \qquad 
\hat{s}_{j}^{(k)}=\displaystyle{\frac{s_{j}^{(k)}}{1-\beta_{2}^{k}}}
$$

L'equazione di aggiornamento diventa:
$$
w_{j}^{(k+1)}=w_{k}^{(k)}-\frac{\eta}{\sqrt{ \hat{s}_{j}^{(k)}+\varepsilon }}\hat{v}_{j}^{(k)}
$$
