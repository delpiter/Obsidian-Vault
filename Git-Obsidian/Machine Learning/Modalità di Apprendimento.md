## Batch, Incrementale, Naturale
---
### Batch
> [!abstract] Definizione
> L'addestramento in modalità ***batch*** è effettuato **una sola volta** su un training set dato.

- Terminato il training, il sistema passa in **working mode** e **non è più in grado di apprendere**.
- La maggior parte dei sistemi ML opera in questo modo.

### Incrementale
> [!abstract] Definizione
> Dopo l'addestramento iniziale sono possibili **ulteriori sessioni di addestramento**.

- **Scenari:** sequenze di batch, *unsupervised tuning*.

> [!warning] Rischio: catastrophic forgetting
> Il sistema **dimentica** ciò che aveva appreso in precedenza.
### Naturale
> [!abstract] Definizione
> **Addestramento continuo** (per tutta la vita).

- Addestramento attivo anche in working mode.
- Coesistenza di approccio **supervisionato** e **non supervisionato**.

Approccio di tipo "***human-like***"
- Una piccola quantità iniziale di istruzioni dirette (i genitori che etichettano gli oggetti durante l'infanzia), combinata con una grande quantità di *unsupervised experience*.

## Reinforcement Learning
---
> [!abstract] Definizione
> Il **reinforcement learning** apprende un **comportamento**: l'obiettivo è apprendere un comportamento ottimale a partire dalle esperienze passate.

Un **agente** esegue azioni che modificano l'ambiente, provocando passaggi da uno **stato** all'altro.
- Quando ottiene risultati positivi, l'agente riceve una **ricompensa** (*reward*, positivo o negativo).
- Il reward può essere **ritardato** rispetto all'azione (o alla sequenza di azioni) che lo ha determinato.

> [!hint] Obiettivo
> Apprendere l'**azione ottimale in ciascuno stato**, in modo da massimizzare la **somma dei reward** ottenuti nel lungo periodo.
## Parametri e funzione obiettivo
---
In generale, il comportamento di un modello $M$ di machine learning è regolato da un insieme di **parametri** $\Theta$ (ad es. i pesi delle connessioni in una rete neurale). 

Per rendere esplicita la dipendenza si indica il modello come $M(\Theta)$.

> [!tl;dr] Apprendimento
> L'***apprendimento*** consiste nel determinare il *valore ottimo* $\Theta^{*}$ dei parametri.

Dato un training set $Train$ e un insieme di parametri, la **funzione obiettivo** $f(Train, M(\Theta))$ può indicare:

> **Ottimalità** della soluzione, da **massimizzare**:

$$\Theta^{*}=\text{argmax}_{\Theta}\, f(Train, M(\Theta))$$

> **Errore o perdita** (*loss function*), da **minimizzare**:

$$\Theta^{*}=\text{argmin}_{\Theta}\, f(Train, M(\Theta))$$

$f$ può essere ottimizzata:

- **Esplicitamente**, con metodi che operano a partire dalla *definizione matematica*.
- **Implicitamente**, usando euristiche che modificano i parametri in modo coerente con $f$.

![[../Metodi Numerici per L'Intelligenza Artificiale/Intelligenza Artificiale/Training#Iperparametri]]

### Selezione automatica iperparametri
> La ricerca di valori ottimali per gli iperparametri può essere lunga e noiosa.

Conviene automatizzare quando possibile.

> [!summary] Grid Search
> Per ogni ***iper-parametro*** si definisce un *insieme di valori* da provare.
> Il sistema è valutato su **tutte le combinazioni** di valori su tutti gli *iper-parametri*.

Questo processo può essere molto costoso
- Si applica una tecnica chiamata coarse to fine, partendo con esecuzioni a grana grossa delle distanze tra gli iperparametri, raffinando in maniera incrementale i valori.

## Organizzazione dei dati
---
![[../Metodi Numerici per L'Intelligenza Artificiale/Intelligenza Artificiale/Machine Learning#Organizzazione dei Dati]]

Lo **split** può essere:
- **random** (*shuffling*)
- **mirato**, ad es. per mantenere separati i periodi temporali di train e test.

> [!warning] Serie temporali
> Quando il sistema è addestrato su un periodo storico e produce previsioni per un periodo successivo, uno split random **non è corretto**.

 Una divisione casuale porta a una ***sovrastima delle prestazioni***, perché il training set include data point temporalmente vicini (e molto simili) a quelli di test.

> [!danger] Cherry picking
> **Non usare il test set** per orientare le scelte durante lo sviluppo di un sistema (strategia, feature, modello).

Il rischio di **overfitting** è particolarmente forte quando il test set è di dimensioni limitate.

### K-fold cross validation
> [!help] Definizione
> La ***k-fold cross validation*** è la procedura che permette una scelta più **robusta degli iperparametri**.

>Esempio: 15000 pattern, $k=5$
- **5000** pattern sono scorporati a priori per il **test**.
- I **10000** rimanenti vengono mescolati e suddivisi in **5 fold** da **2000** pattern ciascuno.

#### Procedura
Per ogni combinazione di *iperparametri* $H_i$ da valutare:
1. Si esegue il training **5 volte**, scegliendo ogni volta un fold come **valid set** e i 4 rimanenti come **train**.
2. Si calcola l'accuratezza $\text{avg\_acc}_i$ come **media** (o **mediana**) delle 5 accuratezze sui rispettivi valid set.

<u>Poi:</u>
3. Si sceglie la combinazione di iperparametri con il **migliore** $\text{avg\_acc}$.
4. Si **riaddestra** il modello su **tutto il training set**.
5. Solo a questo punto si verificano le prestazioni sul **test set**.

## Model vs Data Optimization
---
> Molto tempo viene speso dai progettisti di applicazioni di ML per l’*ottimizzazione del modello* e dei suoi **iperparametri**.

> [!help] Ma...
> Nelle applicazioni pratiche però è più conveniente dedicare tempo all'***ottimizzazione dei dati***.

A parità di tempo investito i **benefici sono maggiori**.

Per miglioramento della qualità dei dati si intende:
- La pulizia dei dati
- L'identificazione dei failure del sistema e la collezione di nuovi dati per i casi critici.
- Tecniche di data augmentation
- Tecniche di supporto all'etichettatura automatica dei dati.
	- Etichettatura incrementale e self-labelling.

## Problemi Closed e Open Set
---
> Nel caso più semplice si assume che il pattern da classificare appartenga a una delle classi note (closed set).

Es. classificare le persone in $\{uomini, donne\}$.


> [!attention] Attenzione
> In molti casi reali invece i pattern da classificare possono appartenere a una delle classi note o a **nessuna di queste** (*open set*).

Es. Classificare tutta la frutta in $\{mele, pere, banane\}$.
- Se esce un *kiwi*?

> ***Due soluzioni***
- Si aggiunge alle classi un'ulteriore classe fittizia "***il resto del mondo***" e si aggiungono al training set i cosiddetti "*esempi negativi*".
- Si consente al sistema di **non assegnare il pattern**.
	- Si definisce una soglia e si assegna il pattern alla classe più probabile solo quando la probabilità supera la soglia.
## Anomaly Detection
---
> [!tldr] Idea
> L'obbiettivo è capire se si sta verificando una ***situazione anomala*** prima che sia troppo tardi.

Come la ***prevenzione dello stop di un macchinario*** prima della rottura.

Si può approcciare il problema **apprendendo** in modo ***non supervisionato*** la singola classe del *funzionamento normale*.
- Dopo l'addestramento il modello analizza lo stato del sistema e produce un allarme anomalia quando il sistema si discosta dal funzionamento "normale".

## Explainable AI
> Una delle critiche maggiori rivolte ai modelli di ML è il loro funzionamento "***black box***" che non permette di capire il perché di certe decisioni.

> [!hint] XAI
> Alcuni modelli rendono disponibili nativamente metriche per quantificare l'***importanza delle feature*** usate a livello globale.

Altri modelli permettono un'analisi locale del singolo data point, permettono di capire l'importanza delle singole feature nella sua classificazione.


Per la classificazione di immagini esistono tecniche tipo GradCam che permettono di evidenziare i pixel che hanno avuto un ruolo determinante nella classificazione.
