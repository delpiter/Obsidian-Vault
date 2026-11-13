> Il processo di apprendimento è una caratteristica chiave delle [[Reti Neurali|CNN]].

> [!failure] Iterativamente
> 1. I dati di addestramento vengono passati attraverso la rete per ***calcolare le predizioni***.
> 2. Si confrontano le predizioni della rete con i valori desiderati usando una [[Reti Neurali#Cost e Loss Function|funzione loss]].
> 3. I pesi della rete vengono aggiornati iterativamente nella ***direzione che minimizza la loss***.

> ***Epoca***:
- Il processo si ripete per più iterazioni (*epoche*), presentando ogni volta i dati di addestramento, finché la rete non converge o la *performance è soddisfacente*


> [!quote] L'addestramento consiste nel determinare il valore dei pesi $w$ che determinano il mapping desiderato tra input e output.

Il mapping desiderato dipende dal problema che vogliamo risolvere.
- Può essere [[../Tipi di Machine Learning#Classificazione|classificazione]], [[../Regressione/Regressione|Regressione]], o tanto altro. 
## Forward Propagation
---
>[!info]
>Con ***forward propagation*** si intende la propagazione delle informazioni in avanti dal livello di *input* a quello di *output*.

Una volta addestrata, una rete neurale può semplicemente processare pattern ***attraverso la forward propagation***.

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


> [!hint] Info
> Il numero totale di pesi o parametri è $$N_{\text{param}} = \underbrace{d\cdot n_1 + \sum_{i=1}^{l-1} (n_i\, n_{i+1}) + n_l\cdot s}_{\text{pesi}} + \underbrace{\sum_{i=1}^{l}( n_i )+ s}_{\text{bias}}$$, dove:
> - $d$ è il numero di **neuroni di input**.
> - $s$ è il numero di **neuroni di output**.
> - $l$ è il numero di **layer nascosti**.
> - $n_{i}$ è il numero di **neuroni al layer** $i$.

## Backwards Propagation
---
> Legato alla tecnica usata per il calcolo delle derivate della funzione di errore sulle regole di ***derivazione delle funzioni composte***.

Per calcolare il vettore dei pesi:
$$
w^{*}=\{ w^{(1)},\dots,w^{(l)} \}\in\underset{ w }{ \arg\min }\ C(w)  =\frac{1}{n_{T}}\sum_{j=1}^{n_{T}}L(y^{(j)},\hat{y}^{(j)}(w))
$$
Con $y$ output atteso e $\hat{y}$ output predetto.

Ricorriamo al [[../../../Metodi di Discesa/Metodi di Discesa#Steepest Descent|metodo del gradiente]].
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
\begin{array}{}
\displaystyle\frac{ \partial L }{ \partial w_{11}^{(3)} }=\delta_{1}^{(3)} z_{1}^{(2)} \\
\displaystyle\frac{ \partial L }{ \partial w_{11}^{(2)} }=\delta_{1}^{(2)} z_{1}^{(1)} \\
\displaystyle\frac{ \partial L }{ \partial w_{11}^{(1)} }=\delta_{1}^{(1)} z_{1}^{(0)}
\end{array}
$$
>[!summary] Conclusione
>L'***aggiornamento dei pesi per l'epoca successiva*** sarà la seguente:
>$$w^{k+1}=w^{k}-\eta \nabla L(w^{k})$$

> Omettendo gli indici $k$ e $k+1$ dell'epoca:

$$
\begin{array}{}
w_{11}^{(3)}=w_{11}^{(3)}-\eta \delta_{1}^{(3)}z_{1}^{(2)} \\
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
\delta_{i}^{(L)}=\displaystyle\frac{ \partial L(\hat{y}_{i}) }{ \partial a_{i}^{(L)} }=f'(a_{i}^{(L)})\displaystyle\frac{ \partial L(\hat{y}_{i}) }{ \partial \hat{y}_{i}}
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

È l'approccio più utilizzato per implementare la *back propagation*.
- Ogni aggiornamento viene chiamato ***iterazione***.

Ad ogni epoca gli $n$ pattern sono ordinati in maniera casuale e poi suddivisi considerandoli sequenzialmente in ***gruppi di uguale dimensione*** $\text{size}_{mb}$.
- $\text{size}_{mb}=1$ "***stocastico***" o *one line*.
- $\text{size}_{mb}=n$ "***full***" o *batch*.
#### Mini-Batch Stochastic Gradient Descent
>[!tldr] Idea
>Per calcolare la funzione di costo si considera un ***sottoinsieme dell'intero set di dati***.
>Si divide il set in *diversi set più piccoli*, e si esegue la back propagation ogni volta che un mini-set viene esaurito.

#### Tarare il batch size
> Definire il valore ottimale di $size_{mb}$ **non è banale**: bisogna bilanciare efficienza computazionale e capacità di generalizzazione.


> [!abstract] Batch size grande

Per $size_{mb}$ più grandi aumenta la **velocità del training**:
- meno aggiornamenti del gradiente per epoca;
- processing più efficiente dei minibatch grandi (parallelismo hardware).

> [!warning] Limite di memoria  
> Nei modelli di grandi dimensioni, $size_{mb}$ è limitato dalla **memoria disponibile nella GPU**.


> [!help] Batch size piccolo

I modelli *generalizzano meglio* quando convergono a **flat minima** (minimi piatti) rispetto agli **sharp minima** (minimi acuti).
- **Minibatch piccoli o medi**:
    - più esplorativi (maggiore _randomness_ nel gradiente);
    - meno attratti dagli sharp minima.
    - Tempo di training più lento rispetto a $size_{mb}$ grande
#### Relazione con il learning rate
> $size_{mb}$ e $\eta$ **non sono indipendenti**:

- In genere, con minibatch più grandi si può usare un learning rate **più aggressivo (maggiore)**, grazie a un effetto "media" più forte nelle correzioni (il gradiente stimato è meno rumoroso).
- Alcuni autori propongono un **aumento lineare di $\eta$** all'aumentare di $size_{mb}$ (_linear scaling rule_).
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
