> Durante la fase di analisi, confrontandosi con gli esperti del dominio applicativo, si devono verificare la completezza degli schemi locali, individuando eventuali correlazioni involontariamente omesse.

> [!important] Info
> Le trasformazioni **non** devono ***introdurre nuovi concetti***, ma esplicitare quelli ricavabili nelle sorgenti.

Se le sorgenti modellassero porzioni ***indipendenti e distinte*** del mondo reale il problema dell'[[Integrazione]] non esisterebbe.

Le diversità nelle rappresentazioni dei concetti comuni sono causate da:
- Diversità di Prospettiva
- Equivalenza dei costrutti del modello
- Incompatibilità delle specifiche.
### Diversità di Prospettiva
> [!hint] Info
> Uno ***stesso oggetto*** del dominio può differenziarsi in base agli *aspetti relativi* ai fini della funzione a cui sono preposti.

![[attachements/ViewDifference.png]]

Quello di destra:
- Porzione dello schema utilizzato per gestire l'organigramma aziendale per il quale *non è rilevante la distribuzione dei dipendenti sui vari progetti*.
A sinistra:
- ***potrebbe essere un vincolo*** l'appartenenza ad un dipartimento in base ai progetti a cui partecipa un dipendente.

### Equivalenza dei Costrutti
> [!summary] Info
> I *formalismi di modellazione* permettono di rappresentare uno ***stesso concetto*** utilizzano ***combinazioni diverse*** dei costrutti a disposizione.

La diversità è di tipo ***sintattico***:
- le due modellazioni sono *perfettamente equivalenti*.

![[attachements/ConstructEquivalence.png]]

### Incompatibilità delle Specifiche
> [!fail] Info
> Si verifica quando due schemi ***modellano una stessa porzione del dominio*** applicativo e racchiudono *concetti diversi in contrasto* tra loro.

![[attachements/SpecsIncompatibility.png]]

I due schemi sono incompatibili poiché in quello di sinistra un professore può tenere **al più un corso**.
- In quello di destra ne deve tenere **almeno due**.

### Concetti Comuni
> È necessario definire il tipo di relazione semantica esistente tra concetti comuni modellati diversamente in schemi distinti.

Ci sono 4 possibili ***relazioni*** tra ***due distinte rappresentazioni*** $R_{1}$ e $R_{2}$ di uno stesso concetto.


> [!cite] Identità
> $R_{1}$ e $R_{2}$ ***coincidono***.

Vengono usati gli stessi costrutti e il concetto è modellato dallo *stesso punto di vista*.

> [!cite] Equivalenza
> Due schemi sono ***equivalenti*** se le loro istanze possono essere messe in corrispondenza ***uno a uno***.

$R_{1}$ e $R_{2}$ hanno costrutti diversi, ma non sussistono errori di specifica o diversità di percezione.
- Implica che a livello estensionale esistono due insiemi di dati diversi ma equivalenti che memorizzano le stesse informazioni.

> [!cite] Comparabilità
> Due schemi sono ***comparabili*** $R_{1}$ e $R_{2}$ sono sono né *equivalenti* né *identici*, ma i costrutti utilizzati e i punti di vista dei progettisti ***non sono in contrasto*** tra di loro.

> [!cite] Incompatibilità
> Due schemi sono ***incompatibili*** $R_{1}$ e $R_{2}$ sono in *conflitto* a causa dell’**incoerenza** nelle specifiche.

> [!bug] Conflitto
> Si verifica un ***conflitto*** tra due rappresentazioni $R_{1}$ e $R_{2}$ di uno stesso concetto quando le due rappresentazioni ***non sono identiche***.

A seguito dell'integrazione molti concetti diversi ma correlati vanno a trovarsi nello stesso schema ***dando vita a nuove relazioni***.
- Tali relazioni sono dette ***proprietà inter schema***, devono essere identificate e rappresentate esplicitamente.
## Fasi dell'Integrazione
---
Di seguito la sequenza di passi concordata che devono essere svolti:
- ***Pre-Integrazione***
	- Comprende la fase di analisi e scelta della strategia di integrazioni
- ***Comparazione degli schemi***
- ***Allineamento degli schemi***
- ***Fusione e ristrutturazione degli schemi***
### Strategie di integrazione
> Indicando l'***ordine*** con cui si procede all'integrazione degli schemi.

![[attachements/IntegrationProcess.png]]

> [!abstract] Tecniche Ennarie
> Il processo di integrazione ***considera più di due schemi contemporaneamente***.

> Tecnica che conviene quando:
- Devo mettere assieme tanti sorgenti che più o meno riguardano la ***stessa area***.
- Devo integrare strutture piccole e semplici.

Molto complesso rispetto alle tecniche binarie.

> [!caution] Tecniche Binarie
> Il processo di integrazione considera sempre ***coppie di schemi***.

***Semplifica*** molto l'analisi in quanto gestisco solo due schemi alla volta.

Sono dette a scala quando i nuovi schemi sono integrati allo schema temporaneo determinato fino a quel momento.

> [!warning] Risciho
> Il rischio di questa tecnica è quello di ***non vedere tutte le sfaccettature*** del problema contemporaneamente.

Potrei fare scelte che dovranno essere rivisitate più tardi quando i rami dell'albero convergono.
#### Comparazione degli schemi
> Questa fase consiste in un'analisi comparativa dei diversi schemi che mira a identificare le correlazioni e conflitti tra i concetti in essi espressi.

I conflitti che possono essere evidenziati appartengono a 4 categorie:

> [!abstract] Conflitti di eterogeneità 
> Discrepanze dovute all'utilizzo di ***formalismi con diverso potere espressivo***

Ci possono essere:
- ***Conflitti sui nomi***
	- *Omonimie* (stesso nome per due concetti diversi)
	- *Sinonimie* (nomi diversi denotano uno stesso concetto)
- ***Conflitti semantici***
	- Quando due schemi *modellano la stessa porzione di mondo reale* a un diverso livello di astrazione/dettaglio.
- ***Conflitti strutturali***
	- Scelte diverse di modellazione per uno stesso concetto, possono essere:
	    - *di tipo*: stesso concetto due costrutti
	    - *di dipendenza*: 2+ concetti sono correlati con dipendenze diverse in schemi diversi
	    - *di chiave*: stesso concetto con `ID` diversi
	    - *di comportamento*: diverse politiche di cancellazione/modifica dei dati

### Allineamento e Fusione
> Una volta analizzate due soluzioni devo capire ***come unirle***.

Di solito si sceglie di mantenere lo schema con ***più potenza espressiva***.
- Devo stare comunque attento, questo rischia di *rilassare i vincoli di un database*.

>[!question] Perché ci sono queste discrepanze?

Come `int` - `float` o relazione $1-n$/$n-n$ nelle due soluzioni.

Spesso le due soluzioni ***sono omonime***.
- Esempio due soluzioni con ordini, da una parte il peso dell'ordine è *intero* dall'altra è *float*.
	- In una soluzione il peso era in **grammi** e nell'altro in **chili**.


> [!summary] Allineamento degli Schemi
> Con ***allineamento*** si intende *eliminazione dei conflitti* presenti tramite l’applicazione di **trasformazioni**

La soluzione è fatta in modo da *evitare perdita di informazioni* e la strategia migliore è la binaria a scala.

> [!caution] Fusione degli schemi
> Operazione di unione di due schemi e creazione di uno unico.

Il processo si basa su 3 principi:

> ***Completezza***
- Con la sovrapposizione risulteranno evidenti ulteriori proprietà inter-schema.

> ***Minimalità***
- Evitare forte ridondanza dei concetti che anche se espressi in modo univoco dai sorgenti risultano *duplicati* o *derivabili*.

> ***Leggibilità***
- Facilita e sveltisce le successive fasi di progettazione