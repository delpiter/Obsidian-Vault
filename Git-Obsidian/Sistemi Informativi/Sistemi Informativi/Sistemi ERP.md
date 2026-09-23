## I sistemi Enterprise Resource Planning
---
> [!info] Enterprise Resource Planning
> `ERP` è la ***gestione integrata dei processi aziendali***.
> `ERP` è un software che promette l'integrazione "*seamless*" di tutte le **informazioni che attraversano l'azienda**.
>>[!done] Un database, una applicazione e una interfaccia unificata in tutta l'azienda.

> Alcune informazioni possono essere:
- finanziarie
- contabili
- delle risorse umane 
- della supply chain e dei clienti.

> [!tldr]  Idea: Avere una copertura completa di tutti i processi aziendali.


![[Sistemi Informativi/attachements/ERP.png]]


> [!question] Perché conviene
> 

Il vantaggio dell'integrazione sta nella ***circolarità dell'informazione***.
- Se voglio accelerare i processi, ho bisogno che le **informazioni circolino**.
- Un **dato integrato** mi permette di avere una ***informazione accessibile a tutti i processi*** aziendali.

I moduli (citati in precedenza #todo) rappresentano il *core* degli `ERP` a cui possono essere aggiunti ulteriori moduli, tra cui:
- ***Product Lifecycle Managment*** - **PLM**
	- Fornisce supporto alla **gestione della documentazione tecnica** del prodotto e dei relativi processi produttivi.
- ***Supply Chain Managment*** - **SCM**
	- Fornisce supporto alla **pianificazione e al controllo** delle attività interaziendali.
- ***Customer Relationship Managment*** - **CRM**
	- Fornisce supporto all'**interazione con il cliente**.

> [!hint]  Quando utilizzare `ERP`

Il sistema `ERP` funziona in maniera efficacie per ***aziende medio grandi*** che necessitano *processi standardizzati*.
- Un sistema `ERP` in una azienda piccola potrebbe **limitare il funzionamento dell'azienda**.
- La standardizzazione dei processi **non è sempre un bene**.
*Flessibilità* e *rapidità di azione* sono fattori più importanti della standardizzazione.


### Caratteristiche di ERP
> L'`ERP` ha 3 caratteristiche fondamentali:
- Unicità dell'informazione
- Estensione e modularità funzionale
- Prescrittività
### Unicità dell'informazione
> [!tldr] Idea
> Tutte le elaborazioni condividono ***uno e un solo valore*** per ogni informazione.

L'unicità dell'informazione è ottenuta usando un'*unica base di dati condivisa*, che offre i seguenti vantaggi:
- **Sincronizzazione dei dati**
    - Permette la sincronizzazione dei processi interdipendenti
- **Assenza di ridondanza**
    - Non sono più necessarie complesse procedure di aggiornamento dei dati che spesso porta a errori di consistenza.
- **Tracciabilità degli aggiornamenti**
- **Affidabilità dell'informazione**
    - Provenendo da un'unica sorgente, non si rischia che i dati direzionali siano inconsistenti

> [!warning] Quando manca l'unicità

> Esempi
- Il mancato pagamento di un cliente è registrato nel sistema contabile, ma fino alla sincronizzazione degli archivi il sistema commerciale continuerà ad accettare ordini dal cliente.
- Le scorte di materie prime sono memorizzate, oltre che sulla base dati del magazzino, anche su quella di programmazione: per ogni materiale esisteranno quindi due giacenze inconsistenti.
- I dati di vendita di una multinazionale sono registrati da sistemi locali eterogenei; il consolidamento dei dati richiede ogni volta un processo ad hoc e dura alcuni giorni
#### Estensione e modularità
> L'ampiezza della copertura dei sistemi `ERP` fa sì che questi possano essere usati come _**unica soluzione**_ per il SI.

> [!abstract] Definizione  
> La ***modularità*** del sistema permette all'azienda di scegliere solo i moduli di interesse.

> Strategie adottabili:
- ***Incrementale***
    - Si acquistano progressivamente i moduli che nella precedente configurazione del SI mancavano o erano realizzati mediante sistemi legacy inadeguati
- ***One stop shopping***
    - Si predilige la linearità acquistando i moduli di un solo vendor, possibilmente in un'unica tranche
- ***Best of breed***
    - Vengono utilizzati i moduli di diversi vendor che meglio si prestano alle esigenze dell'azienda o che vengono considerati i migliori

> [!example] Approcci tipici
 
- **Aziende con funzioni core di "nicchia"**: si adotta un approccio _best of breed_ per le funzioni core dell'azienda e un unico fornitore per le rimanenti
- **Aziende con funzioni core generiche**: si adotta un unico fornitore che copre tutte le funzionalità possibili, e un approccio _best of breed_ per le funzioni non coperte

> [!danger] Problema  
> Usando più vendor diversi, l'unicità dell'informazione probabilmente andrebbe persa
### Prescrittività

> [!abstract] Definizione  
> I sistemi `ERP` incorporano la ***logica del processo gestionale***.

È necessario far aderire i processi aziendali a quelli definiti nell'`ERP`. 
L'approccio a un progetto `ERP` è ***invertito*** rispetto a quanto avviene nella progettazione di un SI *ad-hoc*.

I sistemi **non** devono tuttavia considerarsi **oggetti immutabili**:
- esistono margini di *personalizzazione*, necessari a gestire il gap tra il modulo standard e le specificità delle aziende.

> [!impatto] Impatto organizzativo  
> L'impatto organizzativo può essere elevato, tuttavia:
 
- I processi `ERP` sono basati sulle **best practices** del settore
- Garantiscono la **correttezza** e la **standardizzazione** delle operazioni
- Favoriscono la razionalizzazione dei processi, facendo coincidere il progetto informatico ERP con un progetto di **BPR** (_Business Process Reengineering_)

