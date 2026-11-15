## Master Data Management
---
> Diverso dalle altre tecniche per la dimensione.

> [!tldr] Idea
> Il ***progetto di integrazione*** viene limitato ai *master data*.
> Definiamo ***master data management*** l'insieme delle discipline, tecnologie e soluzioni in grado di creare e mantenere consistenti, aggiornati e accurati i ***dati di importanza critica***.

Se in due sorgenti sono presenti tanti dati comuni, *non integro tutti i dati* ma solamente quelli **più importanti**.

Limito le operazioni ai master data o dati di importanza critica (spesso le anagrafiche).

> [!cite] Master Data
> Con ***master data*** si indica l'insieme dei dati che descrivono entità fondamentali per il business di una azienda.

Invece di avere numerose sorgenti creo un hub che gestisce questi dati critici.

### Scegliere i Master Data
> Tra le tipologie di dati ci sono

- Dati **non strutturati**: email documenti e pagine web
- ***Transazionali***: ordini fatture trouble ticket
- ***Metadati***: descrizione di attributi, glossario aziendale
- ***Gerarchici***: descrivono le relazioni tra i concetti
- ***Master***: persone, cose, luoghi e concetti.


> [!example] Caratteristiche dei Master Data
> 

> ***Quantità***
- La creazione di un'architettura per la gestione dei `MD` si giustifica solo per la *quantità elevata di informazioni*.

> ***Lifetime***
- I `MD` tendono a essere *meno volatili* dei dati transazionali. 
- Un dato `MD` "**dura**" molto di più di una fattura, che dopo un anno non ha più valore informativo.

> ***Valore***
- Maggiore è il valore di una informazione, maggiore la probabilità che sia considerato un `MD`

>***Complessità***
- Per dati con *limitate problematiche di gestione* è **poco utile** allestire un meccanismo `MDM`.

> ***Riusabilità***
- Un *concetto riutilizzato* da più sistemi aziendali richiede con elevata probabilità una gestione basata su `MDM`.

> ***Centralità***
- I `MD` sono *centrali a più applicazioni* e vengono da esse creati, modificati, letti e cancellati.
### Gestione dei Master Data
> Il `MDM` impatta pesantemente i processi aziendali e determina **problemi di natura organizzativa**.

> [!question] Chi è il proprietario dei dati?

> [!question] Chi è il responsabile della loro manutenzione?
> 

Le principali fasi di un progetto `MDM` sono:
1. Identificare le ***sorgenti dati***.
2. Specificare **produttori** e **consumatori** di `MD`
	1. Numero di attori, tipo di operazioni che incidono sulla complessità
3. Raccogliere **meta dati** sui `MD`
	1. Definire univocamente i `MD` sia a livello sintattico (formato e tipo di dato) che semantico.
4. Identificare gli **esperti** dei `MD`
	1. Per ogni sorgente si identificano persone in grado di descrivere come devono essere trasformati.
5. Definire il **processo di data governance** e il relativo **gruppo di lavoro**
	1. Deve avere le competenze e l'autorità per prendere decisioni relative ai `MD`
6. Sviluppare un **modello di gestione** dei `MD`
	1. Fase più importante, si decide:
		- Quale architettura usare
		- Quale formato scegliere
		- Quali record sono inclusi/esclusi
7. Scegliere uno **strumento** (nel caso non sia sviluppato internamente)
8. **Progettare** e **implementare** l'*infrastruttura* di gestione
9. Generare e testare i `MD`.
10. **Modificare le applicazioni** produttrici e consumatrici di `MD`
	1. In base alle politiche di gestione prescelte
11. Definire il **processo di manutenzione**

> [!question] Qual è la fase più difficile

1. Data cleaning e standardizzazione
2. Definizione del processo di Governance
3. Implementazione della soluzione

### Architetture per MDM
> Le quattro architetture si distinguono lungo due assi:
- **dove risiede la proprietà del dato** (sorgenti o hub)
- **quanto è stretto l’accoppiamento temporale** tra sorgenti e hub (asincrono o sincrono).

Il livello di invasività sui sistemi esistenti cresce in modo coerente con questi due assi.
#### A Consolidamento

> [!tldr] Idea  
> L'hub centrale è un _**punto di raccolta e sintesi**_: le sorgenti inviano periodicamente i propri dati, che vengono integrati, ripuliti e deduplicati per produrre i _**golden record**_.

La _proprietà dei dati_ rimane alle applicazioni sorgenti, che li modificano in piena autonomia.

- Il flusso è **unidirezionale**: dalle sorgenti verso l'hub, i golden record non tornano alle applicazioni
- L'allineamento è **asincrono** (tipicamente batch/ETL) rispetto agli eventi che creano e aggiornano i dati
    - L'architettura non garantisce che i `MD` siano sempre aggiornati
- I `MD` sono usati per **reportistica direzionale e analisi** (data warehouse, BI), dove un lieve ritardo è accettabile

> [!done] Impatto sulle applicazioni operative: minimo

#### A Registro

> [!tldr] Idea  
> L'hub è un _**indice di corrispondenze**_, non un contenitore di dati: memorizza _chiavi e collegamenti_ tra le rappresentazioni locali della stessa entità, senza copiarne i record.

Le sorgenti pubblicano i propri dati e l'hub contiene solo un riferimento ad essi; i dati vengono letti dalle sorgenti **a richiesta** (_virtualizzazione_).

- Esempio: Il cliente `123` nel modulo "_**ordini**_" corrisponde al cliente `257` nell'applicazione "_**fatturazione**_": il registro conserva il legame e ricostruisce una vista unica quando serve

La _proprietà dei dati_ rimane interamente alle applicazioni sorgenti.  
L'hub esegue gli algoritmi di **pulizia, standardizzazione e match** tra i record.

> [!warning] Contropartita  
> La qualità del dato non viene corretta alla fonte e l'interrogazione dipende dalla disponibilità delle sorgenti.

> [!done] L'impatto sulle applicazioni è minimo  
> È l'approccio più semplice da avviare.

#### A Coesistenza

> [!tldr] Idea  
> L'hub è un _**punto di convergenza bidirezionale**_: raccoglie i dati dalle sorgenti, costruisce la _versione master_ e poi la _**redistribuisce**_ sulle sorgenti, che beneficiano così di dati già ripuliti e armonizzati.

La _proprietà rimane alle sorgenti_, che continuano a modificare i dati: hub e sorgenti **coesistono** aggiornandosi a vicenda.

- L'aggiornamento **non è sincrono** con gli eventi
    - Possono esistere finestre temporali di disallineamento

In questo caso è necessario capire **quali dati** devono essere condivisi con l'hub centrale e come **risolvere i conflitti** quando la stessa informazione viene modificata in più punti.

> [!info] Compromesso  
> Buon equilibrio tra qualità del dato e invasività.

#### A Transazionale

> [!tldr] Idea  
> L'hub è la _**fonte unica di verità operativa**_: mantiene la _versione aggiornata_ dei `MD`, utilizzata in **modo sincrono** da tutte le applicazioni.

Metodo **più invasivo**: necessita una modifica di _ciascuna delle applicazioni coinvolte_ nell'integrazione, che non modificano più direttamente i `MD` ma inviano all'hub richieste di creazione o modifica.

La _**proprietà del dato è trasferita all'hub**_, che è l'unico soggetto che può modificarli sulla base delle segnalazioni delle sorgenti.

Il dato aggiornato deve essere reso disponibile in modo sincrono alle sorgenti

- L'hub utilizza _politiche transazionali_ per garantire la **consistenza** delle informazioni

I `MD` sono utilizzati sia nella normale operatività delle applicazioni operazionali sia per **armonizzare il comportamento** tra più applicazioni (regole di business e di qualità applicate in modo uniforme).

> [!summary] Confronto
> 
> |Architettura|Ruolo dell'hub|Proprietà|Sincronizzazione|Invasività|
> |---|---|---|---|---|
> |Consolidamento|Raccolta e sintesi|Sorgenti|Asincrona, unidirezionale|Bassa|
> |Registro|Indice di corrispondenze|Sorgenti|Dati letti a richiesta|Minima|
> |Coesistenza|Convergenza bidirezionale|Sorgenti|Asincrona, bidirezionale|Media|
> |Transazionale|Fonte unica operativa|Hub|Sincrona|Alta|

Le ultime due modalità (_coesistenza_ e _transazionale_) sono quelle più usate nella realtà, perché portano i benefici della qualità del dato anche nei processi operativi. Spesso si **parte da consolidamento o registro** per evolvere gradualmente verso modelli più integrati.