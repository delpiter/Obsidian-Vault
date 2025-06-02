## Paradigma generale dell'AI
---
>[!example] Paradigma
>4 Passaggi fondamentali nella creazione di una ***intelligenza artificiale***.

> 1. Acquisizione di dati:
- Elemento fondante di qualsiasi applicazione correlata al ML è acquisire ***grandi quantità di dati***.

> 2. Data Processing
- Tecniche con cui vengono ***elaborati i dati*** per adattarli al meglio al modello.

> 3. Modello
- **Nucleo principale** del sistema AI.
- Può essere visto come un *insieme di tecniche matematiche e statistiche*, in grado di **apprendere da una certa distribuzione di dati** forniti in input e di *generalizzare* su nuovi dati.

> 4. Predizione
- Valutare l'*efficacia del sistema sviluppato* con appropriate metriche.


![[AIGeneralConcept.png]]

### Organizzazione dei Dati
> Una volta ottenuti i dati raccolti, è necessario **organizzarli**.

>[!abstract] Training Set
>I dati sui quali il *modello apprende automaticamente* durante la fase di apprendimento (**training**).

Solitamente contiene la maggior parte del set di dati (circa $70\%$).

>[!done] Validation Set
>Parte del ***training set***.
>Su questi dati, vengono messi a punto gli ***iperparametri***.
>- Parametri inseriti *manualmente*.

Contiene circa il $15\%$ dei *dati totali*.

>[!question] Test Set
>Dati su cui il ***modello viene testato*** durante la fase di test.

Contiene circa il $15\%$ dei *dati totali*.
### Tasks
> Ci sono diverse task nel machine learning, a seconda dell'output che vogliamo.

#### Classificazione
>[!Definizione] 
>Dato un input specifico, il modello (***classifier***) emette una ***classe***.
>-  Se ci sono duce classi, chiamiamo il problema classificazione ***binaria***.
>- Altrimenti classificazione ***multiclasse***.

> ***Classe***:
- Una classe è un set di dati con **proprietà comuni**.
- Correlato al concetto di etichetta
- Il concetto è ***semantico***, in quanto strettamente dipendente dal contesto.

>[!example] Esempi

1. Rilevamento spam (classi: *si*/*no* **spam**).
2. Riconoscimento facciale (classi: *identità*).
3. Diagnosi medica (classi: **tumore** *maligno*/*benigno*).

#### Regressione
>[!definizione]
>La **regressione** viene utilizzata per modellare la relazioni tra le variabili indipendenti e la variabile dipendente.
>>[!quote] A parole
>>Dato uno specifico input, il modello (***regressore***) restituisce un valore continuo e non una *classe*.

>[!example] Esempi

1. Stima dell'altezza di una persona in base al peso.
2. Stima dei prezzi di vendita degli appartamenti nel mercato immobiliare.
3. Previsione dell'energia prodotta da un sistema fotovoltaico.

#### Clustering
>[!definizione]
>Clustering significa *identificare* gruppi (***cluster***) di dati con caratteristiche simili.

Spesso applicato in un ambiente di ***apprendimento non supervisionato***.
- La natura non supervisionata del problema lo rende ***più complesso***.

Anche il numero di *cluster* non è noto a priori.

>[!example] Esempi

1. Definizione di gruppi di utenti basati sul consumo.
2. Raggruppamento di individui in base alle analogie del DNA.
