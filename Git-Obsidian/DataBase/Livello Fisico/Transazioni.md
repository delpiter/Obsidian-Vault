>[!definizione]
>Una ***transazione*** è vista come una sequenza di *operazioni elementari* di **lettura** e **scrittura** di oggetti del **DB** che a partire da uno *stato consistente* porta il DB in un ***nuovo stato finale consistente***.

L'inizio della *transazione* viene indicato dalla parola chiave `{sql icon}BEGIN`. 

È possibile definire dei "***savepoint***"
- Usati da una *transazione* per disfare **solo parzialmente** il lavoro svolto. (Comando `{sql icon}SAVEPOINT`).

Le transazioni possono essere eseguite:
- In ***serie*** (*serial execution*) seguendo uno *schedule*.
- In maniera ***concorrente*** (*Interleaved execution*).
### Esiti di una Transazione
> Una transazione può avere ***solo due esiti***.

>[!done] Terminare correttamente
>Avviene **solo** quando l’applicazione esegue una *particolare istruzione* [[SQL]], detta `{sql icon}COMMIT`, che comunica "*ufficialmente*" al ***Transaction Manager*** il termine delle operazioni.

>[!fail] Terminare non Correttamente
>Una ***transazione*** termina *anticipatamente* in due casi:
>1. La ***transazione*** decide che non ha senso continuare e "*abortisce*" eseguendo l'istruzione `{sql icon}ROLLBACK`.
>2. Il ***sistema*** non è in grado di garantire la corretta esecuzione.

- Per tornare a un *savepoint*: `{sql icon}ROLLBACK TO SAVEPOINT`

#### Tipi di Guasti
> 3 Tipi di malfunzionamento:

- ***Transaction Failure***: Quando una *transazione* abortisce.
- ***System Failure***: Interruzione di *transazioni* attive causati da un'**anomalia hardware o software**.
- **Media Failure**: Il contenuto della base di dati viene danneggiato.

### Gestione della Concorrenza
>Il *Transaction Manager* deve garantire che transazioni che eseguono in concorrenza ***non interferiscano*** tra loro.

4 Tipi di problemi:

>[!missing] Lost Update
>Due *transazioni* leggono lo **stesso dato** e lo aggiornano, con il secondo aggiornamento il ***primo viene perso***.
>- **Write -> Write Dependency**

>[!hint] Dirty Read
>Lettura di un dato che è stato modificato da una transazione ma non ancora "*Committed*". (*Uncommitted dependency*)
>- **Write -> Read Dependency**

>[!caution] Unrepeatable Read
>Accade quando una *transazione* legge la **stessa** [[Modello Relazionale#Relazione|tupla]] due volte e ottiene ***valori diversi***, a causa di una **modifica intermedia** da parte di una *seconda transazione*. (*Inconsistent Analysis*)
>- **Read -> Write Dependency** 

>[!abstract] Phantom Row
>Accade quando una *transazione* *ri-esegue* una [[DML|query]] e trova nuovi valori che **non erano presenti** nella prima esecuzione.

#### Cascading Abort
>Quando una transazione $T$ fallisce, il *Recovery Manager* deve eliminare gli effetti da essa prodotti.

>[!warning] Attenzione
>Anche le transazioni che hanno eseguito "***dirty read***" leggendo dati da $T$ devono essere eliminate.

>[!info] Cascading Abort
>Avviene un effetto detto ***cascading abort***, una *catena di fallimenti* delle **transazioni** alterate da $T$, e delle **transazioni** eventualmente alterate da queste, e così via.

>[!danger] Problema
>Il problema nasce quando il **cascading abort** coinvolge anche *transazioni* che ***hanno eseguito*** `COMMIT`.

Due possibilità, ***entrambi non corrette***:
- Lasciare permanenti gli effetti di $T_{2}$ violando la *semantica di read*.
- Annullare gli effetti prodotti da $T_{2}$ violando la *semantica di commit*.

##### Recoverability
>[!check] Transazione Recoverable
>Si dice che una ***transazione*** $T$ è "*recoverable*" se le viene impedito di eseguire `COMMIT` prima che **tutte le transazioni**, che scrivono valori letti da $T$, eseguano `COMMIT` o *abortiscano*.

$T_{j}$ legge $x$ da una transazione attiva $T_{i}$ se:
1. $T_{j}$ legge $x$ *dopo* che $T_{i}$ l'ha modificato.
2. $T_{i}$ non fallisce *prima* che $T_{j}$ legga $x$.
3. *Ogni transazione* che modifica $x$ fra il tempo che intercorre tra la modifica di $x$ da parte di $T_{i}$ e la lettura di $x$ da parte di $T_{j}$ fallisce prima che $T_{j}$ legga $x$.

>[!quote] Una transazione $T_{j}$ legge da $T_{i}$ se $T_{j}$ legge qualche dato scritto da $T_{i}$


Per evitare il ***cascading abort*** è sufficiente *impedire* che una transazione esegua ***dirty read***.
- Significa ritardare ogni $read[x]$ fino a che tutte le transazioni che hanno operato $write[x]$ sono state **completate con successo** o sono state fatte **abortire**.

### Isolation
> Una comune tecnica usata dai DBMS per evitare i problemi visti consiste nell’uso di [[13 - Semafori|lock]].

Nei [[Git-Obsidian/DataBase/Introduzione#DBMS|DBMS]] ci sono:
- $S$ (*shared*): Lock **condiviso**, necessario per leggere.
- $X$ (*exclusive*): Lock **esclusivo**, necessario per scrivere e modificare.

>[!info] Lock Manager
>Il ***Lock Manager*** è un modulo del **DBMS** che si occupa di tener traccia delle risorse *correntemente in uso*, delle transazioni che le *stanno usando* e delle transazioni che ne hanno *fatto richiesta*.

Lo **Scheduler** della maggior parte dei sistemi reali è di fatto realizzato estendendo il *Transaction Manager* (**TM**) con un *Lock Manager* (**LM**).

![[DMBSScheduler.png]]


[[SQL]] mette a disposizione meccanismi di base per influenzare il modo con cui una **transazione** viene *eseguita*.
- Se una transazione sa di dover *elaborare molte tuple* di una relazione può **richiedere esplicitamente** di porre un **lock** sull'*intera relazione*.

###### Livelli di Isolamento

| Isolation Level    | Phantom | Unrepeatable Read | Dirty Read | Lost Update |
| ------------------ | ------- | ----------------- | ---------- | ----------- |
| *Serializable*     | **NO**  | **NO**            | **NO**     | **NO**      |
| *Repeatable Read*  | **YES** | **NO**            | **NO**     | **NO**      |
| *Read Committed*   | **YES** | **YES**           | **NO**     | **NO**      |
| *Read Uncommitted* | **YES** | **YES**           | **YES**    | **NO**      |

#### Strict 2-Phase Locking
> Il ***two phase locking*** (**2PL**) è il protocollo più usato per lo *scheduler* nei DBMS centralizzati.

>[!abstract] Regole
>- A seguito di una *richiesta di operazione su un certo dato* da parte della **transazione** $T$, viene assegnato il ***lock*** corrispondente **solo se** non vi sono lock *incompatibili* sul dato stesso detenuti da altre **transazioni**.
> ---
>  
>- Un ***lock*** acquisito dalla **transazione** $T$ **non** può essere rilasciato almeno fino alla conferma dell’avvenuta esecuzione da parte di **DM** dell’operazione corrispondente.
> ---
> 
> - Lo scheduler rilascia i ***lock*** acquisiti da $T$ in *una volta sola*, al termine della **transazione**; più precisamente, quando il *Data Manager* **conferma** l’avvenuta esecuzione di `{sql icon}COMMIT` o `{sql icon}ABORT`.

> Si può dimostrare che *se*:
- Una transazione prima acquisisce **tutti i lock necessari**.
- Rilascia i lock solo al termine dell'esecuzione.

<u>Allora</u>
- È garantito l'isolamento completo delle transazioni.

>[!danger] Effetti collaterali
>[[9 - Condivisione di Risorse#Deadlock|Deadlock]].


#### Assenza di Phantom Row
> Problema ***più difficile da risolvere***.

>[!cite] Soluzioni
>Si può acquisire un $S$-*lock* su tutta la **table**, e poi richiedere gli $x$-*lock* per le ***tuple che si vogliono modificare***.
>- Nuovo tipo di lock: ***Predicate Lock***.
>	- Riguarda tutte le tuple che *soddisfano un predicato*.

### Azioni di Ripristino
>[!caution] Transaction Undo
>Eseguito in seguito all'`ABORT` di una *transazione*.

>[!help] Global Undo
>Ripristino da un ***system failure***.
>Interessa *transazioni* **non** ancora **completate** al momento del guasto.

>[!abstract] Partial Redo
>Ripristino da un ***system failure***.
>Interessa *transazioni* **completate** al momento del guasto.

>[!missing] Global Redo
>Recovery da *dump* completa ridondanza.
>>[!quote] Dump
>>Il dump del **DB** è una copia di archivio del Database (o parte di esso).

#### Log File
>[!info]
>Il ***log file*** è un file in cui vengono registrate le **operazioni di modifica** eseguite dalle *transazioni*.

>[!example] Esempio di Log


| LSN   | T       | PID      | before(P) | after(P)  | prevLSN |
| ----- | ------- | -------- | --------- | --------- | ------- |
| ...   |         |          |           |           |         |
| $235$ | $T_{1}$ | `Begin`  | -         | -         | -       |
| $236$ | $T_{2}$ | `Begin`  | -         | -         | -       |
| $237$ | $T_1$   | `P15`    | (abc, 10) | (abc, 20) | $235$   |
| $238$ | $T_2$   | `P18`    | (def, 13) | (ghf, 13) | $236$   |
| $239$ | $T_1$   | `Commit` | -         | -         | $237$   |
| $240$ | $T_2$   | `P19`    | (def, 15) | (ghf, 15) | $238$   |
| $241$ | $T_3$   | `Begin`  | -         | -         | -       |

###### Write Ahead Log Protocol
>[!check] WAL
>Se una **transazione** deve essere *disfatta*, è indispensabile che le before image siano registrate nel Log prima che le relative pagine del **DB** siano ***effettivamente modificate***.

- Si scrive prima sul *Log* e poi sul **DB**.
	- Garantisce il rispetto della proprietà [[Funzionalità DBMS#Proprietà ACID|Atomicity]].
- Forzare la scrittura di tutti i log record di una transazione prima del commit
	- Garantisce [[Funzionalità DBMS#Proprietà ACID|Durability]].

>[!caution] Implementazione

La responsabilità del protocollo `WAL` è del ***Buffer Manager***.
![[BufferManager.png]]

> Quando una **transazione** $T$ modifica una pagina $P$, il ***Buffer Manager*** ha 2 possibilità:

>[!danger] Steal
>Scrive $P$ quando *più conviene*, anche prima della terminazione di $T$.

>[!warning] No-Steal
>Mantiene la pagina $P$ nel buffer e attende che $T$ abbia eseguito il `COMMIT` *prima di scrivere su disco*.

> Casi:

- ***Transaction Failure***:
	- Per annullare le modifiche si *scandisce il Log file a ritroso*, ripristinando le "**before image**" delle pagine modificate.

- ***System Failure***:
	- Il **Recovery Manager** attiva la *procedura di restart* che provvede a riportare il **DB** in uno ***stato consistente***, facendo l’Undo di tutte le transazioni attive all’atto del guasto.

- ***Media Failure***:
	- Si ha un ripristino che usa una *copia* archiviata del **DB**.