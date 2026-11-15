> Più il sistema è ***integrato*** più ho la [[../Sistemi Informativi/Sistemi ERP|Circolarità]] *dell'informazione*

Lo sviluppo di un sistema informativo è di tipo *incrementale e evolutivo* e quindi il suo risultato è un mosaico composto da **più frammenti** ognuno dei quali ***utilizza la tecnologia in voga al momento***.

> [!cite] Definizione
> Con il termine ***integrazione*** si indicano l'insieme di attività atte a costruire una versione *integrata* e *consistente* del sistema informatico.

Consideriamo 3 temi fondamentali

> ***Integrazione degli schemi*** dei dati
- Operazione a livello [[../../DataBase/Progettazione Concettuale/Modello Entity-Relationship#Entità|intensionale]] che rende consistenti gli schemi dei diversi moduli.

> Definire dei ***criteri di***  [[Pulizia dei Dati|pulizia dei dati]]
- Operazione a livello *estensionale* che controlla ed elimina eventuali inconsistenze ed errori.

> ***Trasformazione***
- Operazione a livello *estensionale* che trasforma i dati degli schemi locali nei dati dello schema globale.

>[!example] Esempio
> ***Extract, Transform, Load*** (`ETL`) è un processo di integrazione dei dati usato per muovere e preparare informazioni da diverse fonti in una singola repository.

La presenza di un livello di dati integrato ***modifica l'architettura del Sistema Informativo***
- Le applicazioni *operano su viste dello schema* integrato che possono essere virtuale o materializzato.

### I passi dell'integrazione dello schema
> Analizzando più in dettaglio la fase di integrazione si evidenziano le seguenti operazioni:

> [!hint] [[Analisi e Normalizzazione]]
> Consiste nell'***analizzare i diversi schemi locali*** producendo come risultato un *insieme di schemi concettuali* localmente completi e consistenti.

Spesso consiste in un vero e proprio ***reverse engineering***.
- Costruendo una *visione astratta della base di dati*.
- Dal punto di vista teorico vanno fatte *separatamente* da ogni sorgente di dati.

> [!help] Costruzione dello schema Riconciliato
> È la fase più importante in cui i diversi ***schemi locali vengono fusi*** in un *unico schema globalmente consistente*. 

> [!Definizione del Mapping] 
> Utilizzando lo schema logico riconciliato si **definisce la relazione** (***mapping***) tra concetti degli *schemi sorgenti* e dello *schema riconciliato*.

Il **mapping** è uno dei risultato dell'analisi insieme allo *schema riconciliato*.

Le funzioni di mapping sono usato quando si deve eseguire sui database locali una interrogazione espressa sullo schema riconciliato.

> Se ho due database ho due modi in cui posso definire *un concetto rispetto ad un altro* o viceversa.

***Global as a view*** (`GAV`)
- Il concetto globale è definito come una vista sulle sorgenti.
	- Aggiungere una **nuova sorgente** significa dover *riscrivere tutti gli schemi*.
- Esempio: Meccanismo delle ***viste*** nei database relazionali.

***Local as a view*** (`LAV`)
- Il mapping è definito in modo tale che io ho uno schema globale e *definisco le sorgenti come viste* rispetto allo schema globale.
- Localmente dico **come si traduce** lo schema globale nella sorgente locale.
	- L'aggiunta di un nuovo schema locale è semplicemente l'*aggiunta di una nuova view* dallo schema globale (molto più **flessibile**).

![[attachements/IntegrationSteps.png]]

Siamo molto fortunati se si è a disposizione di [[../../DataBase/Progettazione Concettuale/Modello Entity-Relationship|modelli ER]], spesso è possibile solamente leggere i dati ***senza conoscere la struttura*** del database.

Questa integrazione può essere ***virtuale*** o ***materializzata***:
 
> ***Virtuale***
- Viene definita solo la meta conoscenza necessaria per ottenere le informazioni sullo schema globale. (*view*).
- Si crea una view unica globale sui dati degli schemi locali.

> ***Materializzato***
- I dati vengono *trasformati* e *memorizzati* in versione duplicata.


> [!warning] Problema
> A causa delle complessità dell'operazione **non** è sempre possibile ottenere un ***unico schema globale***.

Talvolta è sufficiente creare *poche porzioni integrate* a partire da molti schemi locali
- Solitamente le ***anagrafiche***.

> [[Master Data Managment]]
- Nel `MDM` l'integrazione è ***limitata ai dati aziendali critici***.

## Domanda Frequente
> [!question] Se fossi un CIO e avessi un problema di circolazione di informazione, quali sono le tecniche che possono usare per migliorare?

Approcci possibili
- Evito problemi alla fonte, creo un `ERP` dall'inizio (approccio preventivo).
- Risoluzione a **posteriori**
	- **Integrazione** a posteriori
	- ***Master data management***
	- Data Mesh e data Fabric
