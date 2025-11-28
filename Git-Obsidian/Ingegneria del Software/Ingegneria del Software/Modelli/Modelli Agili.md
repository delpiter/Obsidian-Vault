>[!info]
>I ***modelli agili*** sono modelli prescrittivi per la [[Produzione|produzione del software]], basati su una ferrea disciplina.
>- Trascurano la fragilità delle persone che realizzano il software.

>[!abstract] Caratteristiche

- Incoraggiano la **soddisfazione del cliente** e una consegna incrementale anticipata.
- Impiegano team di progettazione **compatti** e **motivati**.
- Scoraggiano l'utilizzo di *modelli formali* ([[UML]]).
- Incoraggiano la **semplicità di sviluppo**.
- Richiedono comunicazione continua tra sviluppatori e utenti.
- Incoraggiano il continuo [[Modelli Evolutivi#^f6e995|refactoring]].

## Extreme Programming
---
> Più diffuso *modello di processo agile*.

>[!hint] Pianificazione
>Definisce un insieme di ***user story*** che descrivono le funzionalità del software (con priorità assegnate dal cliente).

I progettisti assegnano a ogni ***user story*** un costo (in termini di settimane di sviluppo).
- Una ***user story*** che richiede più di 3 settimane di sviluppo *deve essere frammentata*.

>[!info] Deign
> Persegue la ***massima semplicità***.

Viene scoraggiata la progettazione di funzionalità aggiuntive.
Si incoraggia l'utilizzo di schede `CRC` (Classe-Responsabilità-Collaborazione).

Se viene individuato un problema di design, si crea un prototipo operativo (*spike solution*) che viene poi valutato.
- ***Spike***: software molto piccolo ($1/2gg$ di sviluppo) concentrato su una singola funzione.

>[!caution] Programmazione
>Si basa sul ***pair programming***.

Due persone con ruoli leggermente differenti, collaborano alla stessa workstation per sviluppare il software.
- Fornisce un meccanismo di soluzione in tempo reale dei problemi.

>[!check] Testing
>Prima della programmazione vengono definiti degli ***unit test***.
>- Test di *ogni componente*.

In questa fase vengono implementati tutti gli unit test con uno strumento di supporto che ne consenta l'automazione.

> Dopo il primo rilascio del progetto, il team calcola la ***velocità del progetto***.
- Il numero di user story implementate nella prima release.
- Parametro usato per stimare le date di consegna e le pianificazioni per le *prossime release*.

## Unified Process
---
>[!info] `UP`
>***Unified Process*** è un processo di sviluppo del software *iterativo* e *incrementale*, guidato dai [[Use Case Diagram|casi d'uso]].

È ***component-based***, ***model-based*** e [[Paradigma ad Oggetti|object oriented]].

Un modello di `UP` si basa su tre concetti fondamentali:

>[!question] Chi

Una **risorsa** o **ruolo** definisce il *comportamento* e le responsabilità di un individuo o gruppo.

>[!question] Cosa

Il **comportamento** è espresso in termini di *attività* e *manufatti*.

>[!question] Quando

Si modellano **flussi di lavoro**.
- Sequenze di attività correlate eseguite da ruoli che producono *manufatti*.

### Manufatti
> **Set di Gestione**
- Elaborati di pianificazione e operazionali.

> **Set dei Requisiti**
- Documento di visione.
- Modello dei Casi d'uso.

> **Set di Progettazione**
- Modello di design e architetturale
- Modello di test

> **Set di Implementazione**
- Codice sorgente ed eseguibili.
- File di dati.

> **Set di Rilascio agli Utenti**
- Script di Installazione.
- Documentazione Utente.
- Materiale Formativo.

### Flussi di Lavoro
>[!help] Info
>I flussi di lavoro non sono rigidamente sequenziali e vengono svolti dal progetto in ***ogni iterazione***.

> Prevedono le seguenti fasi:
- Requisiti.
- Analisi.
- Progettazione.
- Implementazione.
- Test.
- Deployment.
- Gestione di configurazione. (Versioning)
- Gestione progetto. (strategie per gestire un processo)
- Ambiente. (infrastrutture di sviluppo)

### Fasi e Milestone
>[!todo] Info
> Le fasi sono sequenziali e corrispondono a [[Definizioni_Ingegneria-del-Software#Milestone|milestone]] significativi.

> **Inception**
- È l'***avvio***, definisce gli obbiettivi del progetto, ne analizza la fattibilità, i costi e i prodotti concorrenti.
>[!example] Milestone: Documenti di fattibilità

> **Elaboration**
- ***Pianifica*** il progetto e ne definisce le caratteristiche funzionali, strutturali e architetturali.
>[!example] Milestone: Specifica dei requisiti e architettura verificata

> **Construction**
- ***Sviluppa*** il progetto attraverso una serie di iterazioni.
>[!example] Milestone: Versione sistema in **beta**

> **Transition**
- ***Consegna*** il sistema agli utenti finali (comprende marketing, installazione e mantenimento).
>[!example] Milestone: Versione in produzione

>[!summary] Ogni fase può essere composta da una o più iterazioni

![[WorkFlow.png]]

