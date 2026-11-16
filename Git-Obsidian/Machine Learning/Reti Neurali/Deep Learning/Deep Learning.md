> [!info] 
> Con il termine ***Deep Neural Network*** si denotano [[../../../Metodi Numerici per L'Intelligenza Artificiale/Intelligenza Artificiale/Reti Neurali|Reti Neurali]] profonde composte da molti livelli (almeno *2 nascosti*) organizzati gerarchicamente.

L'organizzazione gerarchia consente di ***condividere e riusare informazioni***.
- Lungo la gerarchia è possibile selezionare feature specifiche e scartare dettagli inutili.


> [!quote] Al giorno d'oggi
> Le `DNN` oggi maggiormente utilizzate consistono di un numero di livelli compreso tra $7$ e $700$.

Reti più profonde possono garantire prestazioni migliori a discapito dell'efficienza.

La profondità è solo uno dei fattori di complessità:
- Il *numero* di **neuroni**, di **connessioni** e di **pesi** caratterizzano la complessità di una `DNN`.

Maggiore è il numero di pesi (*parametri da apprendere*) maggiore è la complessità del training.

##### Ingredienti Necessai
> Alcune condizioni necessarie per il successo delle `DNN`


> [!info] Big Data
> Disponibilità di dataset etichettati di ***grandi dimensioni***.

> [!caution] GPU Computing
> Il training di modelli complessi richiede ***elevate potenze computazionali***.

> [!missing] Vanishing Gradient
> La ***retro propagazione del gradiente*** è problematica su reti profonde se si utilizza *sigmoide* come **funzione di attivazione**.

- Funzione [[../Neurone#Funzioni di Attivazione|Relu]]

### Tipologie di DNN
> [!abstract] Feed Forward
> Modelli per la [[../../../Metodi Numerici per L'Intelligenza Artificiale/Intelligenza Artificiale/Machine Learning#Classificazione|classificazione]] o [[../../Regressione/Regressione|Regressione]] con ***training supervisionato***.

- `FC DNN` - fully connected `DNN`
- `CNN` - Convolutional Neural Network.


> [!help] Ricorrenti
> Modelli con ***memoria e attenzione***.

- `RNN` - Recurrent Neural Network
- `LSTM` - Long Short-Term Memory
- ***Transformers***

Usati per sequenze, speech recognition, natural language processing, etc...

> [!missing] Non supervisionati
> Modelli addestrati a ***ricostruire l'input*** e utilizzati per il denoising, anomaly detection, etc...

- ***Autoencoders***

> [!quote] Generativi
> Modelli per generare ***dataset sintetici***.

- `GAN` - Generative Adversarial Networks.
- `VAE` - Variational Autoencoders

> [!strong] Reinforcement Learning
> Modelli per apprendere comportamenti.

- Deep Q-Learning
- PPO, GRPO

### Dropout
>  ***Dropout*** è una tecnica di regolarizzazione utile per controllare l'overfitting.

>[!tldr] Idea
> Durante il training alcuni neuroni sono *spenti*, per far si che l'output non dipenda da specifici neuroni ma sia determinato in modo più robusto.

Rallenta la convergenza ma può ***migliorare la generalizzazione***.
- Usato per addestrare `AlexNet` su ImageNet.

### Autodiff
> La maggiorparte dei framework di deep learning rende disponibili i meccanismi di composizione automatica del gradiente.

> [!abstract] Reverse-mode autodiff
> Si sfrutta la [[../../../Analisi/Calcolo Differenziale/Derivate di Funzioni Elementari#Derivate di Funzioni Composte|regola di derivazione a catena]] che permette di isolare il *contributo di ogni layer*, per poi ricomporre automaticamente i pezzi.

Se si definisce un nuovo layer $f$ non esistente per un framework è richiesto di definire solo i ***gradienti locali***.
- $\displaystyle{\frac{\text{d}y}{\text{d}x}}$ dell'output $y$ rispetto all'input $x$
- $\displaystyle{\frac{\text{d}y}{\text{d}w}}$ dell'output $y$ rispetto ai parametri locali $w$.

La propagazione e combinazione con il resto dei gradienti è ***eseguita automaticamente***.

In pratica input, output e pesi di un livello sono organizzati in ***tensori*** multidimensionali.
- Il calcolo dei gradienti richiede derivata parziali organizzate in [[../../../Metodi Numerici per L'Intelligenza Artificiale/Equazioni non Lineari/Sistemi di Equazioni non Lineari#Matrice Jacobiana|matrici Jacobiane]].
