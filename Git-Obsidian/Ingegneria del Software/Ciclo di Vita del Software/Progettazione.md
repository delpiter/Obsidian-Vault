>Quarta fase del [[Il Ciclo di Vita del Software|ciclo di vita del software]].

>[!definizione]
> La fase di ***progettazione*** riguarda tutte quelle attività che permettono di passare alla **raccolta ed elaborazione dei requisiti** di un *sistema software*.

È la fase che fa da "***ponte***" tra la fase di [[Analisi dei Requisiti|specifica ]] e quella di [[../Ingegneria del Software/Produzione|codifica]].

Durante la progettazione si decidono le modalità di passaggio da *che cosa* deve essere realizzato a *come* la realizzazione deve avere luogo.

> Due esigenze contrastanti:

- ***Progetto sufficientemente astratto***
	- Per poter essere confrontato con le specifiche da cui deriva.
- ***Progetto sufficientemente dettagliato***
	- In modo tale che la codifica possa avvenire senza ulteriore necessità di chiarire le operazioni da realizzare.

#### Obbiettivi
>[!info]
>L'obbiettivo principale è quello di produrre software con le ***caratteristiche di qualità*** che sono state dettagliate nella [[Analisi dei Requisiti|fase di analisi]] come:
>- Affidabilità, Modificabilità, Riusabilità, ...

Gli obbiettivi si possono riassumere nella diminuzione dei *costi* e *tempi* di produzione e nell'aumento della *qualità* del software.
- Più il codice è di **alta qualità**, **meno** saranno i ***costi di manutenzione del software*** (fase più costosa).


## Principi di Progettazione
---
> La progettazione trasforma le specifiche dell'utente in un insieme di specifiche *utilizzabili dai programmatori*.

>[!tldr] Idea
>Tutte le fasi della *progettazione* sono ispirate a un ***insieme di principi*** su cui si basano le tecniche e i metodi usati nelle fasi operative.

Il risultato del processo è l'***architettura del software***.
- L'insieme dei ***moduli*** che compongono il sistema, la *descrizione* della loro funzione e le *relazioni* tra di essi.

L'utilizzo di formalismi e metodologie nelle fasi di **progettazione**, **implementazione** e **documentazione**, permette di ridurre gli errori di progetto (*Incompletezza*, *inconsistenza*, *ambiguità*).

### Principi di Progettazione
>[!failure] Anticipazione dei Cambiamenti
>La progettazione deve anche ***prevedere le specifiche future***.
>- Ciò determina la *semplicità di manutenzione* durante il ciclo di vita del software.

> I cambiamenti possono essere:
- ***Noti a priori***: I servizi non inizialmente implementati devono essere comunque presi in considerazione.
- ***Non noti a priori***: Per poter affrontare modifiche non prevedibili, la progettazione deve rendere il progetto *facilmente modificabile*.

> I cambiamenti possono riguardare
- ***Periferiche e Hardware***.
- ***Dominio di applicazione***.
- ***Algoritmi e Strutture Dati***: Elementi che incidono sulle prestazione del software.

>[!summary] Separazione degli Argomenti
>Indica la necessità di ***individuare i diversi aspetti di un problema complesso*** e di trattarli separatamente al fine di semplificare la soluzione.

La suddivisione può essere fatta sulla base del:
- ***Tempo***
- ***Livello di Qualità***
- ***Vista***
- ***Livello di Astrazione***: Le specifiche vengono progressivamente raffinate.
- ***Dimensione***: Modularizzazione.

>[!tip] Modularità
>Con ***modulo*** si indica il *componente di base* di un sistema software che raccoglie un insieme di funzionalità strettamente legate.

> Benefici, capacità di:
- Scomporre un sistema complesso in parti più semplici.
- Comporre un sistema complesso a partire da moduli esistenti.
- Capire un sistema in funzione delle sue parti.
- Modificare un sistema modificando solo un piccolo insieme delle parti.

> ***Linee Guida***:
- I *servizi strettamente connessi* devono appartenere allo stesso modulo
- Ogni modulo deve essere realizzato in *modo indipendente*.
- Si deve essere in grado di operare su un modulo avendo una conoscenza minima degli altri.
>[!todo] ***Interfaccia***

La definizione dell'*interfaccia* dei moduli deve rispettare il concetto di ***information hiding***.
- L'*interfaccia* deve contenere tutte le informazioni necessarie ad un corretto utilizzo del modulo ***senza mostrarne i dettagli implementativi***.
- Principio che permette di modificare l'implementazione del modulo senza che ciò incida su altre componenti.

Bisogna specificare:
- Le *funzionalità a disposizione*.
- Le *modalità di fruizione del servizio*.
- La definizione dei *parametri di input*.
- La descrizione dell'*output*.

La suddivisione di un sistema in moduli rende necessario tener traccia delle interazioni tra gli stessi.

> Le relazioni descritte ***sono***:
- Di *utilizzo* (***USES***), indica quali moduli vengono usati per completare i servizi forniti.
- Di *composizione* (***PART OF***), descrive la struttura del sistema a diversi livelli di astrazione, permettendo di realizzare una documentazione più chiara.
- *Temporale*, descrive la sequenza con cui vengono realizzati i moduli.

Lo strumento più adatto per queste rappresentazioni è il [[../../Algoritmi e Strutture Dati/Strutture Dati/Grafi/I Grafi|grafo]].

>[!abstract] Astrazione
>L'***astrazione*** è lo strumento per capire e analizzare problemi complessi.
>- Consente di *identificare gli aspetti fondamentali* di un fenomeno e *ignorare i suoi dettagli*.

>[!help] Generalità
>Ogni volta che si deve risolvere un problema si cerca di capire qual è il ***problema più generale*** che si nasconde *dietro*.

Il problema più grande può essere:
- ***Più semplice*** di quello specifico.
- ***Già risolto*** in altre applicazioni.
- La soluzione può essere *riusabile*.