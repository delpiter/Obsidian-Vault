> Il primo passo per determinare l'[[Definizioni_Algoritmi#Problema di Ottimizzazione|algoritmo di ottimizzazione]] per un problema consiste nel definire il ***modello matematico***.

>[!attention] Modello Matematico
>Un ***modello matematico*** si rappresenta come segue:
>$$\begin{array}\ z_{p} = \min f(x) \\ \text{s.t.}\ g_{i}(x)\leq b_{i} \quad \forall i=1,\dots,n \\ \qquad h_{j}(x) = d_{j} \quad \forall j=1,\dots,m \\ x\geq0 \end{array}$$

**Dove**:
- $f(x)$ è detta ***funzione obbiettivo***
- Le espressioni $g_{i}(x)\leq b_{i}$ e $h_{j}(x)=d_{j}$ rappresentano i [[Supporto alle Decisioni#Ottimizzazione Vincolata|vincoli]].
- E $x=(x_{1},\dots,x_{l})$ sono le variabili.

Se $f,g$ e $h$ sono lineari parliamo di ***programmazione lineare continua***.
- Se abbiamo il vincolo aggiuntivo che la soluzione $x$ debba avere *componenti intere*, allora parliamo di ***programmazione lineare intera***.

## Bounds
---
> Dato un problema di programmazione lineare $P$ di "*minimo*":

>[!abstract] Lower Bound
>Un ***lower bound*** $z_{LB}$  è una stima per difetto del valore della soluzione ottima $z_{p}$ ($z_{LB}\leq z_{p}$).

Le procedure per calcolare i lower bound sono dette ***procedure di bounding***.

>[!failure] Upper Bound
>Una soluzione ammissibile corrisponde a un valido ***upper bound*** $z_{UP}$ ed è quindi una stima per eccesso del valore della soluzione ottima $z_{p}$ ($z_{UP}\geq z_{p}$).

Le procedure per calcolare soluzioni ammissibili sono dette ***euristici***.

>[!done] Esatti
>Un ***algoritmo esatto*** è un algoritmo che garantisce la determinazione della soluzione ottima di $P$.
