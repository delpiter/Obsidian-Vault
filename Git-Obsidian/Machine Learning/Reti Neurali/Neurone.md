## Neurone Biologico
---
>[!info] Composizione
> Il ***neurone biologico*** è composto da *4 parti*:

 1. Il corpo cellulare (**Soma**).
>  - *Elabora i segnali in ingresso* nel tempo e converte il valore in un output.
2. Estensioni delle cellule (**Dendriti**).
> - *Ricevono segnali elettrici e chimici* da altri neuroni e li *trasmettono* al **soma**.
3. Ulteriore estensione (**Assone**).
> - *Trasmette* il segnale elettrico dal **soma** *ad altri neuroni*.
4. Le **sinapsi**.
> - *Collegano il neurone ad altri neuroni* per trasmettere il segnale in uscita.

![[attachements/BiologicalNeuron.png]]

Il rewiring delle sinapsi è direttamente collegato a processi di apprendimento e memoria, secondo la ***regola di Hebb***.

> [!quote] Hebbian Rule
> Se due neuroni tra loro connessi da una o più sinapsi sono ripetutamente ***attivati simultaneamente*** allora le sinapsi che li connettono ***sono rinforzate***.


## Neurone Artificiale
---
>[!abstract] Perceptron
>Primo esempio di rete neurale.
>- È la prima formulazione matematica del neurone artificiale.
>Logicamente molto simile a quello ***biologico***.

L'idea è quella di avere la possibilità di addestrarlo in ***base all'errore dell'output***.

> Composto da:
- Una serie di input $in_{1},\dots,in_{d}$, i $d$ ingressi che il neurone $i$ riceve. 
- Una serie di pesi $w_{di}$ che collegano un neurone ad un altro.
- Un *bias* $w_{0i}$ ulteriore peso che si considera collegato a un ***input fittizio***.
- $f$ è una funzione di attivazione che **simula** il comportamento del neurone biologico.
	- Si attiva solo se i segnali ***superano una certa soglia***.

$$
net_{i}=\sum_{j=1,\dots,d}w_{ij}\cdot in_{j}+w_{0j}
$$
### Funzioni di Attivazione
>[!hint] Concetto
> Una funzione di attivazione determina se un neurone ***deve essere attivato o meno***.
> - *Semplici operazioni matematiche* per determinare se l'input della rete è rilevante o meno.
> 
> Le funzioni di attivazione possono essere di diversi tipi, ma in generale devono essere ***non lineari***, per consentire alla rete di apprendere relazioni complesse e ***derivabili***.

> Di seguito alcuni esempi di Funzione di attivazione

***ReLU***
$$
f(x)=\max(0,x)
$$
```functionplot
---
title:
xLabel: 
yLabel: 
bounds: [-6,6,-8,8]
disableZoom: true
grid: true
---
f(x)=max(0,x)
```
***Sigmoid***
$$
f(x)=\frac{1}{1+e^{-x}}
$$
```functionplot
---
title:
xLabel: 
yLabel: 
bounds: [-7,7,-1,1]
disableZoom: true
grid: true
---
s(x)=1/(1+exp(-x))
```

***Tanh***
$$
f(x)=\tanh(x)
$$
```functionplot
---
title:
xLabel: 
yLabel: 
bounds: [-7,7,-1,1]
disableZoom: true
grid: true
---
t(x)=tanh(x)
```

***Leaky ReLU***
$$
f(x)=\max\left( \frac{x}{10},x \right)
$$
```functionplot
---
title:
xLabel: 
yLabel: 
bounds: [-6,6,-8,8]
disableZoom: true
grid: true
---
l(x)=max(0.1x,x)
```
***ELU***
$$
\begin{cases}
x\qquad\qquad x\geq 0 \\
\alpha(e^{x}-1)\ \ x<0
\end{cases}
$$
```functionplot
---
title:
xLabel: 
yLabel: 
bounds: [-5,5,-8,8]
disableZoom: true
grid: true
---
e(x)=x>0?x:2*(exp(x)-1)
```

### Softmax
> I valori di uscita dei neuroni sono compresi nell'intervallo $[0\dots1]$, ma non abbiamo nessuna garanzia che la somma sui neuroni di uscita sia $1$.

> [!cite] SoftMax
> Quando una rete neurale è utilizzata come ***classificatore multi-classe***, l'impiego della funzione di attivazione *softmax* consente di trasformare i valori di net prodotti dall'ultimo livello della rete in ***probabilità delle classi***.

$$
z_{k}=f(net_{k})=\displaystyle{\frac{e^{ net_{k} }}{\sum_{c=1}^{s}e^{ net_{c} }}}
$$

I valori $z_{k}$ possono essere interpretati come probabilità delle classi
- Appartengono a $[0\dots1]$
- La loro somma è $1$.
## Tipologie di Reti Neurali
---
> Le reti neurali sono composte da gruppi di [[Neurone#Neurone Artificiale|Neuroni]] ***artificiali organizzati in livelli***.

>[!summary] Tipicamente

> Livelli presenti:
- Livello di ***Input***.
- Livello di ***Output***.
- Uno o più livello *intermedi* (***hidden layers***).

>[!abstract] FeedForward
>Nelle reti *feedforward* (`FFNN`) le connessioni collegano i neuroni di un livello con i neuroni di un **livello successivo**.
>**Non** sono consentite *connessioni all’indietro* o connessioni verso lo stesso livello.

Di gran lunga la rete più utilizzata.

>[!help] Ricorrenti
>Nelle ***reti ricorrenti*** sono previste *connessioni di feedback*, in genere verso neuroni dello *stesso livello*, ma anche all’**indietro**.

Complica notevolmente il flusso delle informazioni e l'addestramento.
- Sono reti più indicate per la ***gestione di sequenze*** (audio, video, frasi in linguaggio naturale) perché dotata di un *effetto memoria a breve termine*.


> [!summary] Multi Layer Perceptron
> Il ***percettrone*** deriva dal modello di neurone proposto da Rosenblatt, utilizza una funzione di attivazione lineare a *soglia* o *scalino*.
>

È una rete di ***almeno 3 livelli*** (1 *nascosto*) con funzioni di attivazione non lineari.

Un singolo percettrone o una rete di percettroni a due soli livelli può essere addestrato con una semplice regola detta ***delta rule***.