## Classificazione
---
> [!info] 
> ***Classificare*** significa assegnare una classe a un [[Dati e Pattern|pattern]].

La classificazione si dice *binaria* se le classi sono solo $2$ altrimenti *multi-class*.

> Es.
- ***Spam detection***
	- *classi* - spam e non spam
- ***Credit card fraud detection***
	- *classi* - fraudolento e non fraudolento
- ***Face recognition***: 
	- Binario in caso di *face verification*
		- Data una faccia verificare che una seconda faccia sia la **stessa persona**.
	- Multiclasse in caso di *face recognition*
		- Una classe a persona.
- ***Pedestrian classification***
	- *classi* - pedone, animale, bici, moto, etc...

## Regressione
---
>[!tldr] Idea
>Applicare la [[../Metodi Numerici per L'Intelligenza Artificiale/Intelligenza Artificiale/Machine Learning#Regressione|regressione]] significa assegnare un valore continuo a un pattern.

Risolvere un *problema di regressione* corrisponde ad apprendere una ***funzione approssimante*** delle coppie (input, output) date.
Utile per la predizione di valori continui

> Es 
- Stimare l'*altezza* di una persona **dato il peso**
- Stima dei *prezzi* degli appartamenti nel mercato immobiliare
- Stima del *rischio* per compagnie assicurative.
- Object detection

## Clustering
---
> [!hint] Info
> Nel [[../Metodi Numerici per L'Intelligenza Artificiale/Intelligenza Artificiale/Machine Learning#Clustering|clustering]] vengono individuati gruppi (*cluster*) di pattern con caratteristiche simli.

Le **classi** del problema non sono note e i pattern non sono etichettati
- La natura **non supervisionata** del problema lo rende più complesso della classificazione.
- Spesso non si conosce neanche il numero di cluster.
- I cluster individuati possono essere usati come classi

> Esempi
- **Marketing**: definizione di gruppi di utenti in base ai consumi
- **Genetica**: raggruppamento di individui sulla base di analogie `DNA`

## Riduzione della dimensionalità
---
> [!tldr] Idea
> La ***riduzione della dimensionalità*** consiste nella riduzione del numero di dimensione dei pattern in input.

In pratica viene appreso un mapping da $\mathbb{R}^d$ a $\mathbb{R}^{k}$ con $k<d$.
L'operazione comporta una perdita di informazione, l'obbiettivo è la ***conservazione delle info importanti***.
- La definizione di importante varia da applicazione ad applicazione.

## Representation Learning
---
>[!todo] Info
> Il successo di molte applicazioni di machine learning dipende dall'efficacia di ***rappresentazione dei pattern*** in termini di feature

> Esempio: analisi delle immagini

Per migliorare il successo si possono fare dei passaggi intermedi come:
- Preprocessing delle immagini
- Estrazione delle feature (*forme*, *colori*, *dimensioni*, etc).

La definizione di feature ad-hoc per le diverse applicazioni prende il nome di ***feature engineering***.

Gran parte delle tecniche di deep learning es. ([[../Metodi Numerici per L'Intelligenza Artificiale/Intelligenza Artificiale/Reti Neurali#Convolutional Neural Network|CNN]]) operano in questo modo utilizzando come input i raw data ed estraendo automaticamente le feature necessarie per risolvere il problema di interesse.

### Problemi nel dominio di Visione
> ***Classificazione***
- Determina la *classe* dell'oggetto

> ***Localization***
- Determina la *classe* dell'oggetto e la sua *posizione* nell'immagine (bounding box).

> ***Detection***
- Determina per ogni oggetto la *classe* e la *posizione* nell'immagine (bounding box)

> ***Segmentation***
- Al posto di una bounding box *etichetta i singoli pixel* dell'immagine a classi con indici delle classi.

## Modelli Discriminativi e Generativi
---
> [!info] Discriminativi
> I modelli ***discriminativi*** (*classificatori*) hanno l'obbiettivo di assegnare un nuovo data-point a una classe.

La cosa importante è apprendere il ***decision boundary*** che separa le classi.

> [!abstract] Generativi 
> I modelli ***generativi*** apprendono la *distribuzione probabilistica* degli esempi usati per il loro addestramento.

Dopo l'addestramento sono in grado di:
- **Generare** *nuovi dati sintetici* a partire da numeri random
- **Modificare** o **trasformare** l'input fornito
- **Classificare** l'input comparando le probabilità che sia generato dalle diverse classi.

La moderna generative `AI` fa largo uso di modelli generativi basati su reti neurali profonde.

> [!warning] Attenzione
> Il termine ***generative*** può essere ambiguo in quanto le tecniche di *genAI* possono risolvere problemi che non richiedono la produzione creativa di contenuti.

## Apprendimento
---
> [!hint] Supervisionato
> Nell'***apprendimento supervisionato*** sono note le classi dei pattern usati per l'addestramento.

Il [[Divisione dell'insieme dei dati#Training Set|training set]] è etichettato
- Situazione tipica nella ***classificazione e regressione***.


> [!fail] Non Supervisionato
> Nell'***apprendimento non supervisionato*** Non sono note le classi dei pattern utilizzati per l'addestramento.

Il training sett non è etichettato
- Soluzione tipica nel clustering e nella maggior parte di tecniche di riduzione di dimensionalità

Anomaly detection
- è spesso considerata un'applicazione unsupervised: si hanno molti esempi di funzionamento normale ma pochi casi di errore.


> [!attention] Semi-supervisionato
> Il training set è etichettato parzialmente.

La distribuzione dei pattern non etichettati può aiutare a ottimizzare la regola di classificazione.