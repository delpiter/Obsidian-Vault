## Diagramma di Pert
> Un [[Diagramma di Gantt]] **non modella l'interdipendenza** delle attività.

Questa è invece la caratteristica del diagramma **PERT**.

Ad ogni attività possono essere associati diversi attributi:
- durata (o data di inizio e fine)
- predecessori
- risorsa
- costo

> [!cite] Definizione
> Il diagramma ***PERT*** (*Project Evaluation and Review Technique*) è la rappresentazione grafica del progetto su cui sono indicati:

- tutte le attività previste dalla [[Work Breakdown Structure|WBS]]
- le Milestone
- i condizionamenti reciproci temporali tra le attività (**legami di precedenza**)

> [!info] Nodi di inizio e fine
> Il primo nodo è sempre quello di **inizio progetto**; l'ultimo è sempre quello di **fine progetto**.

### Legami di precedenza
> Ci sono 4 tipologie di archi che si possono dividere in 2 categorie

> [!caution] In serie

- Finish To Start

> [!summary] In parallelo

- Start to Start
- Start to Finish
- Finish to Finish

| Legame           | Sigla | Significato                             |
| ---------------- | ----- | --------------------------------------- |
| Finish to Start  | FS    | B non può iniziare se A non è terminata |
| Start to Start   | SS    | B non può iniziare se A non è iniziata  |
| Start to Finish  | SF    | B non può finire se A non è iniziata    |
| Finish to Finish | FF    | B non può finire se A non è finita      |

A ogni legame può essere associato un **ritardo (lag)** oppure un **anticipo (lead)**.
### Critical Path Method (CPM)
> [!info] Obiettivo
> Il CPM serve a individuare l'insieme delle **attività critiche**, dette anche **attività a scorrimento zero**.

Lo **scorrimento** (*float*) è la capacità di far slittare un'attività senza far slittare le altre.

Conoscendo la durata prevista di ciascuna attività e le relative relazioni di precedenza, è possibile definire la **tempificazione** del progetto e il **percorso critico**, ossia la ***catena di attività che condiziona la durata del progetto***.
#### Fasi
> L'identificazione del percorso critico avviene in due fasi.


> [!caution] Forward pass (cammino in avanti)

Si parte dall'inizio del progetto e si **sommano** le durate delle attività fino a determinare la data di fine progetto. Per ogni attività si ottengono:
- **Early Start (ES)**: data di inizio al più presto
- **Early Finish (EF)**: data di fine al più presto

![[attachements/ForwardPass.png]]


> [!hint] Backward pass (cammino all'indietro)

Si parte dalla fine del progetto e si **sottrae** la durata di ciascuna attività. Per ogni attività si ottengono:

- **Late Start (LS)**: data di inizio al più tardi
- **Late Finish (LF)**: data di fine al più tardi

![[attachements/BackwardPass.png]]

> [!example] Esempio di backward pass
> Se un'attività, per non ritardare il progetto, deve finire al più tardi il **29** e dura **12 giorni**, il **17** è l'ultima data utile affinché l'attività precedente finisca e questa possa iniziare senza rischiare di consegnare in ritardo.
>
> `LS = LF − durata = 29 − 12 = 17`

##### Total Float
> [!abstract] Info
> Determinate le quattro date per ogni attività si calcola lo **scorrimento totale** (*Total Float*), cioè il ritardo massimo che la singola attività può avere senza ritardare il completamento del progetto.

$$
\text{Total Float} = \text{Late Start} − \text{Early Start}
$$

- Le attività con **Total Float = 0** sono **critiche**
- La catena formata dalle attività critiche è il **percorso critico**