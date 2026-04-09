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

>[!help] Ricorrenti
>Nelle ***reti ricorrenti*** sono previste *connessioni di feedback*, in genere verso neuroni dello *stesso livello*, ma anche all’**indietro**.

### Cost e Loss Function
>[!missing] Loss Function
>La ***loss function*** è una misura dell'errore della previsione da un modello di [[Machine Learning]] rispetto ai dati di training.
>Rappresenta la **discrepanza** tra l'*output previsto* dal modello e l'*output reale*.


> Caso [[Machine Learning#Tasks|Classificazione]].

- *Binary Cross Entropy*
$$
BCE=-y_{i}\cdot\log(\hat{y}_{i})-(1-y_{i})\cdot\log(1-\hat{y}_{i})
$$

- *Categorical Cross Entropy*
$$
CCE=-\sum_{i}y_{i}\cdot\log(\hat{y}_{i})
$$
In entrambi i casi $\hat{y}_{i}$ è l'$i$-esimo valore scalare emesso dal modello (*prediction*) e $y_{i}$ è la corrispondente **label**.

Per usare la Cross Entropy Loss, si necessita di avere delle ***probabilità nel layer di output***.
> ***Softmax Layer***
- Usato per trasformare l'output della rete in probabilità.
$$
p_{i}=\frac{e^{ a_{i} }}{\sum_{k=1}^{n}e^{ a_{k} }}
$$
## Convolutional Neural Network
---
> Create dopo le reti ***MLP*** (Multi Layer [[Neurone#Neurone Artificiale|Perceptron]]).

Le reti ***MLP*** sono computazionalmente troppo pesanti per essere impiegate nell'elaborazione di immagini.

>[!info] CNN
>Le ***CNN*** sono reti progettate espressamente per *processare immagini*.
>Hanno una struttura a 3 dimensioni:
>- *Larghezza* ($W$)
>- *Altezza* ($H$)
>- *Profondità* ($C$)

> ***Convoluzione***.
- Operazione di image processing attraverso la quale si applicano filtri digitali, per ***estrarre feature dalle immagini***.
- Applicata con un meccanismo di ***sliding window***.

Un filtro (*kernel*) $h$ (piccola maschera $2D$ di pesi di dimensione $F\times F$)  viene fatto scorrere su ogni pixel $(x,y)$ di un'immagine input.
- Per ogni posizione, viene generato un valore output eseguendo il [[../../Algebra e Geometria/Frome Bilineari e Prodotti Scalari/4 - Prodotto Scalare|prodotto scalare ]] tra la *maschera* e la *porzione di input coperta*.

![[attachements/Convolution.png|500]]

>[!summary] Composizione

Una `CNN` tradizionale è composta da un *insieme di layer sequenziali*:
- Inizialmente una serie di ***Convolution Layers*** (*Feature Extractor*).
	- Hanno il compito di ridurre la dimensionalità del volume di input.

*Flatten layer*
- Usato per collegare il ***Feature Extractor*** con una rete ***MLP*** fully connected
- "Srotola" il volume di input.

La rete *fully-connected* alla fine esegue il compito di classificazione in base all'input dalla *parte convoluzionale*.

