> Il *ciclo di vita del software* comprende le attività svolte durante il periodo di ***esistenza di un sistema informatico***.

## Attività
---
>[!caution] Definizione Strategica

In questa sezione il cliente (*azienda*) realizza il ***capitolato***.
- Il capitolato è un documento che descrive **tutte le specifiche necessarie** che il software deve avere.

>[!tip] Pianificazione

Vengono definiti gli obbiettivi e viene condotto uno *studio di fattibilità* per individuare possibili strategie di attuazione.
- In questa fase vengono fatte le stime di ***3 fattori***:
	1. *Costi*
	2. *Benefici*
	3. *Tempi*

>[!hint] Controllo Qualità

Viene predisposto un piano di *controllo qualità* per il progetto.
- Ha lo scopo di ***garantire il rispetto delle specifiche*** e di controllare che il sistema realizzato si comporti come previsto.

>[!tl;dr] Analisi dei Requisiti

***Formalizza i requisiti*** avvalendosi di tecniche di modellazione della realtà ([[UML]]).
- Produce *macro-specifiche* per la fase di progettazione
- Risponde alla domanda "***Cosa Fare?***"

>[!abstract] Progettazione del Sistema

Interpreta i requisiti in una ***soluzione architetturale di massima***.
- Produce *specifiche indipendenti dai particolari strumenti* che saranno usati per la costruzione del sistema.

>[!todo] Progettazione Esecutiva

Vengono descritti struttura e comportamento dei *componenti dell'architettura*.
- Vengono prodotte specifiche che possano dar luogo a un ***prodotto funzionante***.

>[!bug] Realizzazione e Collaudo in fabbrica

Il sistema viene ***implementato*** sulla piattaforma scelta e viene testato internamente ($\alpha$-**test**) sulla base dei casi prova definiti in fase di analisi.
- L'$\alpha$-*test* è la *prima verifica del software*.

>[!done] Certificazione

La ***certificazione*** garantisce al cliente che il software raggiunga gli standard di qualità.
- Ha lo scopo di verificare che il sistema sia stato sviluppato secondo i criteri previsti dal metodo tecnico di progetto.

>[!missing] Installazione

Il sistema viene ***installato e configurato***.
- Vengono recuperati *eventuali dati pregressi* se il nuovo software è una sostituzione di uno vecchio.

>[!bug] Collaudo del sistema installato

Gli *utenti finali* testano "***in vitro***" il prodotto installato ($\beta$-**test**).
Si possono evidenziare:
- ***Errori Bloccanti***: Malfunzionamenti che pregiudicano l'attività di collaudo.
- ***Errori Non Bloccanti***: Malfunzionamenti che non pregiudicano l'attività di collaudo.
- ***Problemi di Operatività***: Una funzionalità richiesta non viene attuata adeguatamente.
- ***Problemi Funzionali***: Una funzionalità richiesta non è implementata.
Per ognuno di questi casi il problema deve essere sistemato in un arco di tempo predefinito.
- Es. *Errori bloccanti* ($24h$), *Errori non bloccanti* ($7gg$), etc...

>[!help] Production Stage

Quando il collaudo da esito positivo il sistema viene ***messo in produzione***.
- Sostituendo gradualmente l'eventuale sistema preesistente.

>[!hint] Diagnosi

Durante la fase di *esercizio* gli utenti rilevano eventuali errori.

>[!failure] Manutenzione

Gli errori che si manifestano durante il funzionamento vengono segnalati e corretti (*manutenzione correttiva*).
- Può essere necessario intervenire per adattare il sistema a cambiamenti del dominio (*manutenzione adattiva*).

>[!info] Evoluzione

Si valutano le possibilità di far evolvere il sistema incorporando ***nuove funzionalità*** o ***migliorandone l'operatività***.
- Manutenzione *Evolutiva o Perfettiva*.
