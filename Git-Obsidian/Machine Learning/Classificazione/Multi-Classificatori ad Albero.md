## Random Forest
---
> Il random forest appartiene alla famiglia di [[Multi-Classificatori#Multi-classificatori|metodi di bagging]] (***B***ootstrap ***Agg***regat*ing*).

> [!tldr] Idea
> Vengono estratti con ***re-imbussolamento*** un sottoinsieme $S_{j}$ di pattern dal training set, solitamente i $2/3$ del totale, l'addestramento del classificatore $C_{j}$ avviene sul sottoinsieme $S_{j}$.

In Random Forest i singoli classificatori sono ***decision tree classifiers***

> Decision Tree Classifier
- I decision tree classifier sono uno strumento usato in applicazioni con pattern ***categorici o mixed***.

Esistono diversi tipi di alberi tra cui:
- `ID3`, `C4.5` `CART`

Per la crescita dell'albero a partire da un training set si sceglie in modo greedy ad ogni livello la coppia che meglio separa le classi.

Per la ***classificazione di un nuovo pattern*** si deve:
- visitare l'albero
- una volta giunti a una foglia si classifica il pattern sulla base della classe più comune nel nodo.

### Apprendimento di un albero CART
> [!info] Definizione
> Per ogni nodo, l'algoritmo suddivide gli $m$ pattern entranti del training set in *due sottoinsiemi* disgiunti di dimensioni $m_{left}$ e $m_{right}$.

La suddivisione avviene in modo [[../Algoritmi e Strutture Dati/Greedy/Gli Algoritmi Greedy|greedy]], considerando una singola feature $k$ e una soglia $t_{k}$.
- La coppia $(k,t_{k})$ è scelta come quella che produce i sottoinsiemi più puri, ovvero minimizzando:
$$
J(k,t_{k})=\frac{m_{left}}{m} G_{left}+\frac{m_{rigth}}{m}G_{right}
$$
$G_{left}$ e $G_{right}$ sono le ***impurità*** dei due sottoinsiemi.
Per calcolare le impurità si possono usare ***Gini impurity*** (default) o ***Entropia***.

Dove $p_{i}$ sono le ***probabilità delle classi***.
$$
Gini=1-\sum_{i=1}^{s}p_{i}^{2}
$$
Computazionalmente più semplice rispetto a entropia e con più o meno gli stessi risultati rispetto a ***entropy***.
$$
Entropy=-\sum_{i=1}^{s} p_{i}\log_{2}(p_{i})
$$
Entropy è usato quando le classi coinvolte sono ***più o meno equiprobabili***.


> [!caution] Ricorsione
> Il processo ***continua ricorsivamente*** dividendo i sottoinsiemi creati fino a quanto
> - Si raggiunge in ogni ramo la profondità massima specificata ([[../../Metodi Numerici per L'Intelligenza Artificiale/Intelligenza Artificiale/Training#Iperparametri|iperparametro]] $max\_depth$)
> - Non è più possibile ridurre ulteriormente le impurità.

### Altri iperparametri
> In random forest per rendere maggiormente indipendenti i classificatori:

> [!abstract] Indipendenza
> Per ogni nodo la scelta delle feature $k$ migliore su cui partizionare *non è fatta sull'intero insieme* delle $d$ feature, ma su un ***sottoinsieme random*** $d'$ di feature

Un valore tipico è $d'=\sqrt{ d }$
- Ogni albero può "*vedere*" solo $d'$ feature rispetto alle totali per ***aumentare l'indipendenza***.

Senza questo accorgimento molti *tree* sceglierebbero con elevata probabilità le ***stesse variabili discriminanti***.


> [!done] Random forest opera simultaneamente su due tipi di bagging: uno sui pattern del training e uno sulle feature


> [!summary] Numero di tree in una forest
> Il ***numero di tree*** varia generalmente da alcune centinaia ad alcune migliaia.

Aumentare $n$-estimators oltre al valore ottimale in genere **non produce overfitting** ma rende il sistema meno efficiente.

## Ada Boost
---
> Ada Boost appartiene alla famiglia dei metodi di ***boosting***.
- Più classificatori *weak* sono combinati per realizzare un ***classificatore strong***.

> [!tldr] Idea
> A differenza del *bagging* l'apprendimento avviene in maniera ***incrementale*** e prevede di aggiungere a ogni iterazione un *classificatore efficace sui pattern critici*.

Ad ogni iterazione si assegna un peso a ciascun pattern del training set aggiornando il peso dell'iterazione precedente.
- I pattern ***classificati erroneamente*** hanno *peso maggiore* e contribuiscono maggiormente nella selezione del prossimo classificatore.

Per semplicità si introduce una versione binaria estendibile alla **versione multiclasse**.


> [!cite] Siano
> - $(x_{1},y_{1}),\dots,(x_{n},y_{n})$ i pattern del training set e le rispettive etichette con $y_{i}\in\{ +1,-1 \}$
> - $w^{t}$ il peso del pattern $x_{i}$ all'iterazione $t$
> - $h^{t}(x)\to\{ +1,-1 \}$ il classificatore introdotto all'iterazione $t$ e scelto tra i classificatori $h_{j}^{t}(x)$ disponibili all'iterazione $t$.
> - $\alpha^{t}$ il peso del classificatore $h^{t}(x)$ nell'ambito del multi classificatore.

> ***Passo iniziale***

$$
w_{i}^{1}=\frac{1}{n}, \qquad i=1,..,n
$$
Tutti i pattern hanno lo stesso peso iniziale

Per $t=1,\dots,T$
1. *Normalizza* i pesi: $w_{i}^{t}/\sum_{j=1,\dots,n}w_{j}^{t}$ per $i=1..,n$
2. Per ogni classificatore $h_{j}^{t}(x)$ disponibile calcolare l'errore
$$
\epsilon_{j}=\sum_{i=1,\dots,n}w_{i}^{t}\cdot I(h_{j}^{t}(x_{i})\neq y_{i})
$$
con
$$
I(cond)=\begin{cases}
0 \qquad cond=true \\
1 \qquad else
\end{cases}
$$
3. Scegli come $h^{t}$ il classificatore $h^{t}_{j}$ con minor $\epsilon_{j}$
4. Calcola il peso del classificatore
$$
\alpha^{t}=\frac{1}{2}\ln\left( \frac{1-\epsilon^{t}}{\epsilon^{t}} \right) 
$$
dove $\epsilon^{t}=\min \epsilon_{j}$
5. Aggiorna i pesi
$$
w_{i}^{t+1}=w_{i}^{t}\cdot e^{ -\alpha^{t}y_{i}h^{t}(x_{i}) }
$$
> [!hint] Osservazione
> $y_{i}h^{t}(x_{i})$ è $=1$ se il pattern è ***correttamente classificato***, $-1$ *altrimenti*.

- $w_{i}^{t+1}$ aumenta se $z>0$ cioè $\alpha^{t}$ **positivo** e classificazione **errata** oppure $\alpha^{t}$ **negativo** e classificazione **corretta**.
- $w_{i}^{t+1}$ diminuisce se $z<0$ (casi complementari)

Al termine dell'addestramento, il classificatore finale (**strong**) è la media pesata dei weak classifiers:
$$
H(x)=sign\left( \sum_{t=1,\dots,T}\alpha^{t}h^{t}(x)\right)
$$


> [!question] Quanto deve contare un classificatore

$$
\alpha^{t}=\frac{1}{2}\ln\left( \frac{1-\epsilon^{t}}{\underbrace{ \epsilon^{t} }_{ \text{error rate} }} \right) 
$$

```functionplot
---
title: AdaBoost
xLabel: Error Rate
yLabel: Alpha
bounds: [0,1,-3,3]
disableZoom: true
grid: true
---
f(x)=(1/2)*log((1-x)/x)
```
Un classificatore binario con errore $0.5$ ha peso $0$
- il peso aumenta esponenzialmente quando l'errore è superiore a $0.5$
- diventa negativo se l'errore è superiore a $0.5$
