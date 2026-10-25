> [!quote] Definizione
> Il Business Process Reengineering è un ***paradigma di gestione delle risorse*** che mira a migliorare l’efficienza e efficacia di un’azienda attraverso un’approccio radicale alla ***revisione e riprogettazione dei processi*** aziendali, a seguito di una innovazione degli strumenti informatici.

Il `BPR` permette un ***miglioramento significativo*** e [[../L'innovazione nei Sistemi Informativi#Approcci di Miglioramento|discontinuo]] nelle prestazioni di un [[../Azienda#Processo Aziendale|processo aziendale]], in termini di costi, qualità, servizio e tempi.
- A parità di business, ho la possibilità di stravolgere in maniera profonda la struttura dei processi.

Il primo step è quello di capire, costruire, modellare e interpretare i processi aziendali.
- Cosa prende in **input** il *processo*
- Quali sono le **fasi** del *processo*
- Quali sono gli **output** del *processo*
- **Chi è il cliente** che riceve il processo.

Nel `BPR` il ridisegno dei processi può focalizzarsi su 3 principali tipi di cambiamento:
![[attachements/BusinessProcessReengineering.png]]

> ***Streamlining***
- Ricerca il *miglioramento delle prestazioni* modificando il processo attuale.

> **Business Process Re-engineering**
- Approccio radicale sui processi, ricerca un *cambiamento radicale* sul processo attuale.
- Molti processi aziendali vengono "***stravolti***".

> **Enterprise Transformation**
- Approccio radicale sul business, ricerca una *riconfigurazione del business*
	- Es. `BMW`, radicale cambiamento dal mercato dell'aviazione al mercato automobilistico

### Fasi del BPR
#### 1) Analisi dell'As-Is 
> [!tldr] Idea
> Capisco qual è la mia ***situazione a livello di processo***, dove stanno le *inefficienze*, identifico i *processi da re-ingegnerizzare*.

- **Descrivere** i processi
- Identificazione del **breakthrough**
- Analisi dei **tempi di ciclo**
- Analisi della **creazione del valore**

##### Descrizione dei processi
> [!summary] Info
> La ***scomposizione dei processi*** dettaglia i processi per successivi livelli di approfondimento.

> ***Macroprocesso***
- utile nelle fasi iniziali per strutturare l’analisi e individuare le aree di intervento

> ***Processo***
- illustra, ad un livello ragionevolmente dettagliato, le operazioni svolte da un’azienda

> ***Fase***
- descrive il modo in cui un processo è implementato

> ***Attività***
- livello adottato nello studio dei processi, suddivisione di fasi secondo una logica sequenziale

Le variabili di progettazione dei processi rilevanti ai fini della loro corretta analisi e progettazione sono:
- **Flusso delle attività**
	- sequenza delle attività attraverso cui il processo è svolto
	- incide direttamente sulla qualità dell’output e può essere modellato con diagrammi che esprimono la sequenza ([[../../Ingegneria del Software/UML/UML|UML]])
- **Organizzazione del processo**
	- determina il livello di accorpamento delle attività
	- sia dal punto di vista della suddivisone operativa del lavoro, sia della struttura di coordinamento e controllo aziendale
	- espresso tramite diagrammi [[#Linear Responsibility Charting|LRC]]
- **Competenze delle risorse umane**
	- indice direttamente sulla qualità dell’output
- **Sistema di misurazione e controllo prestazioni**
	- viene realizzato tramite sistemi [[Key Performance Indicator|KPI]] o di **Balanced Scorecard**

###### Linear Responsibility Charting
> [!info] 
> Diagramma che permette di ***incrociare l'organigramma aziendale con l'attività***.

Si ottiene incrociando le *attività di processo* con le *divisioni aziendali*.
Il ruolo è indicato dalle etichette inserite nelle celle della griglia risultante.
- `D` -> Decide, autorizza, ratifica
- `E` -> Esegue
- `A` -> Partecipa e fornisce assistenza operativa.
- `I` -> È sistematicamente informato.

> Esempio

![[attachements/LinearResponsibilityCharting.png]]

##### Identificazione del Breakthrough
> [!hint] Info 
> L'obbiettivo di questa fase è cercare di capire come, con un insieme limitato di risorse possiamo ottenere un *miglioramento* nel processo che ***giustifica i costi***.

Due modalità principali
- ***Benchmarking***: consiste nel misurare e comparare con altre aziende dello stesso mercato (**standard esterni di eccellenza**) il processo aziendale.
- ***La voce del cliente***: approccio più *bottom up*, questa analisi può essere condotta tramite vari metodi:
	- Sondaggi e questionari
	- Interviste
	- Social media e recensioni online
	- Focus group: gruppi di discussione con clienti selezionati
	- etc...

##### Analisi dei tempi ciclo
> [!quote] Definizione
> Il ***tempo di ciclo*** è il tempo necessario per concludere un ciclo di processo.

È la tecnica maggiormente utilizzata nell'***analisi dell'efficienza*** del processo.

> Il tempo di ciclo può essere suddiviso in diverse fasi:
- Tempo di lavorazione: tempo effettivo dedicato alla realizzazione dell'attività.
- Tempo di attesa durante il quale il lavoro è tra una fase e l'altra.
- Setup time.
- Tempo di movimentazione: impiegato per spostare materiali o informazione.
- Tempo di inattività.

> [!important] È fondamentale focalizzarsi sui processi che contribuiscono maggiormante alla creazione del valore
> 

##### Analisi della creazione del valore
> [!info] 
> In questa fase si devono porre alcune domande tipiche di interviste mirate per capire come procedere con l'operazione

Si deve capire se l'operazione:
- è veramente fondamentale
- non è più necessaria
- esiste una nuova tecnologia per farlo in maniera migliore

#### 2) Definizione delle priorità di intervento
> [!tldr] Idea
> Cerco di capire ***dove devo intervenire*** per avere un *miglioramento*, dove conviene e dove non conviene intervenire.

Non tutti i business sono uguali in relazione alle difficoltà del ridisegno
![[attachements/ProcessComplexityChart.png]]

- Le $y$ sono tutti i vincoli che derivano dal contesto in cui lavora l'azienda
- Le $x$ è la complessità interna all'azienda

La scelta dei processi sui quali intervenire deve tenere conto:
- dell'impatto potenziale
- della difficoltà di implementazione
- tempo disponibile per la realizzazione

##### Analisi di Pareto
> [!cite] Principio di Pareto
> L'$80\%$ dei problemi/inefficienze derivano dal $20\%$ delle cause.

L'***analisi di Pareto*** ha come obbiettivo principale quello di *evidenziare le cause principali di un problema* per permettere alle organizzazioni di concentrarsi su quelle aree.

Suddivisa in diverse fasi:
- Raccolta dei dati
- Classificazione in categorie e ordinamento in ordine di frequenza o impatto
- Creazione del grafico di Pareto
- Identificazione del $20\%$ cruciale.

#### 3) Reingegnerizzazione dei processi per rimuovere le barriere
> Fase non eseguita dagli informatici, ma fatto da consulenti strategici che operano nel contesto del `BPR`

> [!tldr] Idea
> Vengono usati nuovi strumenti analitici per aiutare a concepire ***nuovi modi di organizzare*** il flusso di lavoro.

Alcune modalità sono:
- Parallelizzazione
- Riallocazione di esperti funzionali (***Caso Biblus***) #addLink
- Eliminazione di funzioni tradizionali
- Cicli di miglioramento continuo
##### Ruolo della tecnologia nell'innovazione
> Le tecnologie informatiche sono parte integrante delle tecniche di re-engineering.

La tecnologia ***è un fattore abilitante*** dell'innovazione, per esempio l'adozione di processi paralleli è abilitata dai software di collaborazione.

> [!warning] Attenzione
> È necessario pensare alla **scelta delle tecnologie** di implementazione **dopo avere fatto innovazione** su processi e informazioni.

Di conseguenza ci sono ***due tipologie innovazione***:
> Innovazione ***technology-driven***
- Si basa su *tecnologie estremamente innovative* tale per cui gli stake holder non riescono ad immaginarne l'utilizzo
	- Es. uso di `LLM` #addLink per fare uno screening dei bandi e indicare quelli potenzialmente interessanti.

> Innovazione ***application-driven***
- Si basa su *tecnologie note* tale per cui gli stake holder del servizio ne conoscono la potenzialità
	- ***My cicero*** che consente di pagare il parcheggio mediante app, software che si basa su *tecnologie note da 15 anni*

#### 4) Implementazione del cambiamento
> Eseguita effettivamente da società di *consulenza informatica*

> [!bug] Sviluppato da ***programmatori***.

#### 5) Istituzionalizzazione delle misure per il miglioramento
> [[Key Performance Indicator]]

## Il ridisegno dei processi: modello a 6 fasi
---
> [!abstract] Panoramica  
> Il modello articola il ***ridisegno dei processi*** in *sei fasi sequenziali*, dalla condivisione degli obiettivi di business fino alla pianificazione dell’implementazione.

> [!hint] Fase 1 - Condivisione degli obiettivi di business  

> **Attività**
- Documentare la visione aziendale e gli obiettivi

> **Risultati**
- Quadro di riferimento degli orientamenti strategici e degli obiettivi di sviluppo

> [!info] Fase 2 - Definizione delle linee guida  

> **Attività**
- Selezionare i processi di gestione da considerare, identificare le skill necessarie e selezionare le risorse
- Strutturare i team e pianificare le attività
 
> **Risultati** 
- Quadro dei processi e priorità
- Macro target definiti
- Struttura operativa del programma

> [!example] Fase 3 - Analisi di base e benchmark  

> **Attività**
- Analizzare i processi attuali e i sottoprocessi chiave
- Confrontare i processi con maggiore potenziale di miglioramento con le best practice

> **Risultati**
- Diagrammi di flusso dei processi
- Mappatura dei processi
- Benchmark con i concorrenti

> [!tip] Fasi 4 e 5 - Generazione di concetti innovativi e progettazione del cambiamento

> **Attività**
- Sviluppare la visione di un processo eccellente
- Definire i requisiti in termini di risorse

> **Risultati**
- Diagrammi di flusso e lista dei cambiamenti
- Interfacce critiche dei nuovi processi

> [!success] Fase 6 - Pianificazione dell’implementazione  

> **Attività**
- Preparare e concordare un piano di implementazione
- Accordarsi sulla struttura organizzativa post implementazione
- Allineare i criteri di misurazione 

> **Risultati**
- Programma di produzione.