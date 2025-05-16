## A Livello Unico
---
>[!info] Architettura $1$-Tier
>Nell'***architettura $1$-Tier*** è eseguito tutto sullo stesso livello, solitamente su una singola macchina.
>L'utente interagisce direttamente con il [[Git-Obsidian/DataBase/Introduzione#Database|DB]].

>[!done] Vantaggi

- **Semplice** da implementare e usare.
- **Bassa latenza** (**non** ci sono *livelli intermedi*).

>[!fail] Svantaggi

- Non **Scalabile**
- **Bassa Sicurezza**, adatto a piccoli sistemi.
- Nessuna separazione tra interfaccia utente e logica del database.
## A due Livelli
---
>[!info] Architettura $2$-Tier
>Separazione tra ***client e server***, il client gestisce l'interfaccia utente e la logica applicativa base, il server gestisce il [[Git-Obsidian/DataBase/Introduzione#DBMS|DBMS]] e i dati.
>La comunicazione avviene tramite driver (***ODBC*** o ***JDBC***).


>[!done] Vantaggi

- Migliore **separazione delle responsabilità**.
- **Più sicuro** e organizzato.

>[!fail] Svantaggi

- **Scalabilità limitata**
- Difficile da gestire in ambienti con *molti utenti*.

## A tre Livelli
---
>[!info] Architettura $3$-Tier
>Nell'architettura $3$-Tier viene introdotto un ***application server*** (*middleware*) tra client e **DBMS**.
>I tre livelli sono:
>- Livello di **Presentazione** (*Client*/*UI*).
>- Livello **Applicativo** (*Middleware*).
>- Livello **Dati** (*DBMS*).

>[!done] Vantaggi

- **Altamente scalabile**.
- Separazione netta dei ruoli, implica una **facilità di manutenzione**.
- Maggiore **sicurezza** (Il client non accede direttamente al database).
- Supporto a **load balancing**, **caching** e gestione centralizzata della logica.

>[!fail] Svantaggi

- **Complessità elevata** nella progettazione e manutenzione.
- Richiede più **risorse** e infrastruttura.

## Tipi di Database
---
>[!help] Centralizzato
>Un ***database centralizzato*** è un sistema in cui *tutti i dati* sono archiviati e gestiti in un singolo database, localizzato in un'unica posizione fisica.
>- Semplice da gestire ma molto **vulnerabile** a fronte di guasti.
>- **Poco scalabile**.

>[!abstract] Distribuito
>Un ***database distribuito*** è un sistema in cui i dati sono *distribuiti* su più macchine fisiche (*nodi*), ma **il sistema appare** agli utenti come un **unico database**.
>- Molto *scalabile* e *resistente*.
>- **Complesso** da gestire e più lento.

>[!info] Cloud
>I ***cloud database*** sono database che operano su *infrastrutture cloud*.
>I dati vengono archiviati e gestiti su **server remoti** gestiti da provider di servizi cloud come *Amazon Web Services* (**AWS**), *Microsoft Azure* e *Google Cloud Platform* (**GCP**). Questi database sono progettati per sfruttare le ***caratteristiche di scalabilità***, alta disponibilità e gestione automatizzata tipiche dei sistemi cloud.

>[!caution] Replicato
>Un ***database replicato*** è un sistema in cui i dati di un database vengono *copiati* (replicati) su più server o nodi. La replica può avvenire in **tempo reale** (*sincrona*) o con un certo **ritardo** (*asincrona*).
>I dati sono copiati su *più server*.
>- Alta disponibilità, la replica consente di leggere i dati anche se un **nodo si guasta**.
>- Molti **problemi di coerenza**.

>[!cite] Federato
>Il concetto di ***database federato*** si riferisce a un'*architettura* in cui **più sistemi di database separati**, anche se indipendenti, sono in grado di **interagire tra loro** e di condividere dati in modo *trasparente*.
>>[!quote] In altre parole
>>Un ***database federato*** permette di accedere a più *fonti di dati distribuite* senza che l'utente debba preoccuparsi di dove risiedano **fisicamente** i dati o quale tipo di database stia utilizzando.
>
>L'intero sistema di database federato ***appare come un unico database*** unificato, pur mantenendo la separazione tra le fonti di dati sottostanti.
