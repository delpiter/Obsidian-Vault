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

![[BiologicalNeuron.png|400]]

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

