## SI e Aziende
---
> Un'**azienda** è una struttura di comando che governa processi operativi finalizzati al raggiungimento di uno o più obiettivi predefiniti.

I SI supportano sia i processi di governo (SI direzionali e analitici), sia i processi operativi (SI operativi).

![[Sistemi Informativi/attachements/visualAziende.png]]

_Figura: Catena del valore di Porter per un'azienda manifatturiera_

### SI operativi
> [!info]
> I sistemi informativi ***operativi*** informatizzano i processi volti all'**esecuzione** di attività o alla loro **programmazione**.

> Esempi
- Programmazione della fabbricazione e Fabbricazione;
- Programmazione della distribuzione e Distribuzione;
- Amministrazione;
- Gestione del personale;

L'importanza dei SI operativi in un'azienda dipende dall'**intensità informativa** del settore, ossia del contenuto informativo del settore.

> [!cite] Nota
> I ***SI*** supportano il *coordinamento delle attività* (la delocalizzazione aumenta la necessità di coordinamento); gli investimenti in tecnologia per i SI sono proporzionali al ruolo del SI (varia tra l'1% del fatturato nelle semplici manifatture e il 7% delle aziende di telecomunicazione).

![[Sistemi Informativi/attachements/OperativeSI.png]]
### SI direzionali
> [!info] 
> I SI ***direzionali*** supportano il *processo decisionale* fornendo informazioni a manager per aiutarli a decidere.

Il modello primario di questi sistemi deriva dal **modello del ciclo di controllo**:
![[Sistemi Informativi/attachements/directional-visual.png]]

Dal punto di vista informativo, i processi **direzionali** si differenziano da quelli **operativi** poiché:
- si basano su **indici**, ovvero informazioni *aggregate e riassuntive*;
- l'elaborazione **non è continua** ma **periodica**;
- sono **costruiti sopra i SI operativi** da cui estraggono le informazioni di base;
### SI analitici
> [!info] 
> I SI ***analitici*** supportano la *comprensione dei fenomeni di business*, si focalizzano su prodotti, clienti e processi:

- permettono di profilare i **clienti** studiando le relative abitudini e comportamenti;
- mantengono la storia del **prodotto** e permettono di monitorarne l'affidabilità. Sono utilizzati soprattutto per beni durevoli;

Si differenziano dai SI operativi per le stesse motivazioni dei *direzionali*.

> [!hint] Osservazione
>  Mentre i sistemi direzionali valutano fenomeni **interni** all'azienda, quelli analitici misurano fenomeni **esterni** all'azienda.

#### SI analitici per settori
> Di seguito si riporta una ***tabella esemplificativa*** dell'utilizzo dei SI analitici per l'analisi della clientela nei diversi settori produttivi.

| Settore                      | Numerosità dei clienti  | Finalità di analisi                                                                     |
| ---------------------------- | ----------------------- | --------------------------------------------------------------------------------------- |
| **Telefonia**                | Oltre 10 milioni        | profittabilità e comportamento/preferenze                                               |
| **Grandi banche**            | Oltre 1 milione         | profittabilità                                                                          |
| **Aziende elettriche e gas** | Da 100 mila a 1 milione | profittabilità e comportamento/preferenze                                               |
| **Pubblica amministrazione** | Oltre 10 milioni        | studi di settore, segmentazione dei contribuenti, individuazione dei potenziali evasori |
| **Grande distribuzione**     | Da 100 mila a 1 milione | comportamento/preferenze                                                                |

#### Mappa dei SI
> [!tldr] Idea
>Costruire una **mappa dei SI aziendali** significa scomporli in moduli a fini conoscitivi e di classificazione.

> [!Modulo]
> Un ***modulo*** rappresenta un *blocco di funzionalità software* che supportano una fase di un processo aziendale, **omogeneo per frequenza**.
 
Un *modulo* descrive un'esigenza informativa e quindi indica il potenziale impiego di tecnologia informatica.

La suddivisione in moduli è utilizzata anche dai **grandi produttori di package** (SAP, Microsoft, ORACLE) per strutturare le proprie offerte.

I moduli possono essere:
- **orizzontali**: non variano al variare della tipologia aziendale;
- **verticali**: sono utilizzati in specifici settori produttivi (bancario, manifatturiero, chimico);

### Il Portafoglio Applicativo Aziendale
> [!abstract] Portafoglio Applicativo Aziendale 
> Il ***portafoglio applicativo aziendale*** rappresenta una possibile mappa dei SI aziendali;

Può essere considerato un'esplosione della catena del valore di Porter ottenuta incrociando le _fasi del ciclo di trasformazione_ con la _tipologia delle attività_ applicabili per la pianificazione ed esecuzione di ciascuna fase del ciclo. 
- Ogni incrocio individua un modulo.

>[!hint] Nota
> La **pianificazione** ha lo scopo di determinare i piani e controllarne l'avanzamento. Le attività di pianificazione si distinguono per l'orizzonte temporale e il livello di dettaglio.

> [!hint] Nota
> Le **attività di esecuzione** attuano le operazioni pianificate producendo così l'output desiderato. I sistemi di supporto all'esecuzione elaborano informazioni in tempo reale originando benefici riconducibili ai risparmi su attività burocratiche o alle migliori prestazioni di tempi e costi dei processi.

![[Sistemi Informativi/attachements/paa-prof-pianif-table.png]]
_Figura: Profilo dei Livelli di Pianificazione_

![[Sistemi Informativi/attachements/port-esec.png]]
_Figura: Profilo delle Attività di Esecuzione_

![[Sistemi Informativi/attachements/port-applic.png]]
_Figura: Portafoglio Applicativo_

Al *portafoglio applicativo* corrisponde un **insieme di moduli standard**.

Il portafoglio applicativo si differenzia in base alla tipologia di azienda.

> Portafoglio aziende ***chimiche e siderurgiche***
- prodotto più semplice: meno enfasi sulla progettazione;
- poche materie prime;
- complesso il monitoraggio e la manutenzione degli impianti (CIM livello 2 e 3);
- notevole l'investimento sui ricambi degli impianti (e-procurement);
- necessità di coordinamento nei complessi multi-stabilimento (supply-chain management);

> Portafoglio aziende ***telefoniche***
- importanza primaria del contatto con il cliente (CRM);
- problematiche di gestione della rete complesse;

### Smart Manufacturing (AKA CIM)
> [!info] 
> Lo ***smart manufacturing*** è un'*architettura multilivello* che collega diversi livelli di un sistema di produzione ed è finalizzata all'*ottimizzazione* dei processi e alla gestione delle risorse.


> [!done] Vantaggi

- *riduzione* delle **scorte**: attraverso il controllo della produzione e della pianificazione;
- *riduzione* del **tempo di commercializzazione**;
- *aumento* della **qualità del prodotto**: analisi e controllo del processo di produzione;
- *riduzione* dei **costi** grazie alla maggiore efficienza della fabbrica;

> SM è organizzato in un'***architettura a 5 livelli***.

Ogni livello esegue le proprie elaborazioni ed è collegato con gli altri.

![[Sistemi Informativi/attachements/smartManufacturing.png]]
## I sistemi SCADA
> [!todo] Info
> Il componente di un sistema `CIM` preposto al controllo dei sistemi industriali, all'acquisizione e all'analisi dei dati da essi prodotti è denominato ***SCADA***.

I sistemi ***SCADA*** sono usati per *monitorare* e *controllare* grandi impianti industriali e sistemi meccanici/elettronici distribuiti sul territorio.
 
> I principali ambiti di applicazione sono:
- grandi impianti industriali e processi industriali complessi;
- telecomunicazioni;
- sistemi di gestione di acqua, fognature, distribuzione energia (HERA);
- sistemi di produzione dell'energia (impianti fotovoltaici ed eolici);
- raffinerie;
- trasporti (aeroporti, controllo del traffico, ferrovie);
- centri di ricerca (CERN);
 
> L'adozione di un sistema **SCADA** permette di risparmiare tempo e denaro:
- meno spostamenti per i lavoratori;
- riduzione delle esigenze del personale;
- aumento della produttività;
- maggiore reattività rispetto a situazioni anomale;
- riduzione dei costi di gestione;
- maggiore affidabilità degli impianti;

### Architettura dei Sistemi SCADA
![[Sistemi Informativi/attachements/ScadaVisual.png]]

> [[../../Internet of Things/Sensori e Azionatori/Sensori e Azionatori|Sensori e Azionatori]]
- pressione, velocità, luminosità, umidità, temperatura, livello, distanza;
- valvole, pompe, motori;

> ***Controlli***:
- **PLC** - **Programmable Logic Controller**: è un qualunque dispositivo programmabile in grado di risolvere una logica che implementa un algoritmo;
- **RTU** - **Remote Terminal Unit**: non elabora né risolve alcuna logica. È una unità terminale che, ricevuti gli "*ordini*" da una unità di classe superiore, non fa altro che eseguirli.
- **Gateway**: raccolgono le informazioni dai `PLC`/`RTU` e si occupano di trasferirle in tempo reale al *sistema centralizzato* implementando opportuni protocolli di trasmissione, crittografia e sicurezza tra cui:
    - **Modbus**
    - **DNP3**
- **Front-end Server**: ricevono i dati dai diversi siti e li traducono in un formato dal server `SCADA`.
- **SCADA Server**: implementa le funzionalità di monitoraggio e di gestione degli allarmi.
	- Opera in **tempo reale** tipicamente utilizzando uno stream dati.
	- Utilizza un **database** contenente una serie limitata di dati di dettaglio. 
- **Data Server**: si occupa di salvare una ***versione storica dei dati*** (es. campionamento ogni 15 minuti per ogni segnale). È la base dati utilizzata a fini di *analisi*:
    - statistiche;
    - tuning dei sistemi e ottimizzazione delle performance;
    - data mining;

### Evoluzione dei sistemi SCADA
> [!abstract] Scalabilità
> L'***incremento*** del *numero degli impianti* monitorati e dei segnali raccolti pone il problema dell'enorme mole di dati da gestire (in tempo reale), da memorizzare e da analizzare.

> [!summary] Capacità di analisi dei dati raccolti
> Ai moduli per il controllo operativo dei sistemi si aggiungono **moduli** per la ***valorizzazione dei dati storici raccolti***:

> Esempio
- data mining;
- analisi performance;

> [!Danger] Sicurezza
> I sistemi `SCADA` controllano ***infrastrutture critiche***. Il *livello di sicurezza* dei sistemi commerciali è basato su tecnologie che sono 5-10 anni in ritardo rispetto allo stato dell'arte dell'IT:

Oggi la sicurezza dei sistemi `SCADA` è basata sul funzionamento su [[../../Reti/Data Link Layer/Networks/VPN|VPN]] separate rispetto a quella aziendale.
### Dai sistemi SCADA all'Industria 4.0

>[!abstract] Industria 4.0
>Il termine ***Industria 4.0*** indica una *tendenza dell'automazione industriale* che integra nuove tecnologie produttive per **migliorare le condizioni di lavoro** e **aumentare la produttività** e la qualità produttiva degli impianti.

#### Le Tecnologie coinvolte
- [[../../Internet of Things/Tecnologie di Comunicazioni in IoT|IoT]]
#### I sistemi MES
> [!abstract] Manufacturing Execution Systems
> I ***MES*** permettono la *gestione della fabbrica* nel suo complesso (ricevono ordini dall'`ERP`), raccolgono informazioni dallo `SCADA` e forniscono informazioni aggiornate all'`ERP`.

> [!caution] Funzionalità
- assegnazione delle risorse e stato;
- pianificazione delle operazioni;
- spedizione della produzione;
- gestione del lavoro;
- gestione della qualità;
- analisi delle prestazioni;
- ottimizzazione del processo;
- tracciamento del prodotto;
- gestione della manutenzione;

> [!done] Title
>
- riduce il tempo del ciclo di produzione;
- riduce i costi di set up;
- elimina o riduce il tempo di inserimento dei dati;
- migliora l'efficienza della produzione;
- conferisce potere alle persone che operano nell'impianto;