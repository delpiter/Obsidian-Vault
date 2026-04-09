## Il DBMS
---
>[!info]
>Un [[../Introduzione#DBMS|DBMS]] è un insieme di programmi che permettono all'utente di *definire*, *costruire*, *manipolare* e *condividere* una **base di dati**.

>[!example] Funzionalità Principali

- Supporto per almeno un **modello dei dati**.
- Uso di **cataloghi** per memorizzazione la descrizione di DB.
- Supporto di **viste multiple**.
- **Indipendenza** tra programmi e dati.
- **Gestione efficiente e efficace** di grandi quantità di dati persistenti e condivisi.
- **Linguaggio di alto livello** per la definizione di dati, interazioni con il DB e amministrazione dei dati.

Il **DBMS** ha il compito di creare una astrazione logica con cui i dati sono resi disponibili dall'utente.
- Ciò definisce un ***modello dei dati***

> Un ***Modello dei Dati*** è una collezione di *concetti* usati per **descrivere** i dati, le loro **associazioni** e i **vincoli** che devono rispettare.

>[!abstract] Catalogo
>Il *sistema* di basi di dati contiene anche una ***descrizione completa*** della sua struttura e dei suoi vincoli.
>Tale definizione è memorizzata nel ***catalogo*** del sistema.
>>[!cite] Metadati
>>Le informazioni memorizzate nel catalogo sono dette ***metadati***.

Il catalogo è usato dal **DBMS** e dagli utenti che necessitano di informazioni sulla *struttura*.

## Indipendenza Fisica e Logica
---
>[!important] Importante
>Un obbiettivo del **DBMS** consiste nel fornire caratteristiche di *indipendenza logica* e *fisica*.

La soluzione è comunemente nota come ***architettura a 3 livelli***.
![[attachements/ThreeLevelArchitecture.png]]
### Indipendenza Fisica
>[!info]
>L'***organizzazione fisica dei dati*** dipende da considerazioni legate all'efficienza delle strutture adottate.

La **riorganizzazione** fisica ***dei dati*** o la **creazione** di ***strutture di accesso***, <u>**NON**</u> deve comportare modifiche allo schema logico del **DB**.
- **Non** deve causare *effetti collaterali* sui programmi applicativi.

### Indipendenza Logica
>[!tldr]
>L'***indipendenza logica*** è intesa come la possibilità di *aggiornare* la *struttura logia dei dati* di un database senza dover modificare i programmi che li elaborano.
### Livello Fisico
>[!abstract] Files
> Il "***DB Fisico***" consiste in una serie di file, residenti su dispositivi di memoria permanenti che contengono *dati*, *indici* e altre tipologie di *strutture*.

Lo [[../Definizioni Importanti#Schema|schema]] **fisico** descrive come il DB, definito a livello logico è ***rappresentato a livello fisico***.
- La gestione del DB fisico è a carico del *Data Base Administrator*.

### Livello Esterno
>[!hint] Livello delle Viste
>Il *livello esterno* è costruito a partire dallo ***schema logico*** integrato mediante la definizione di [[../Interrogazioni/DML#Viste|viste]] ad hoc che descrivono *parte dello schema logico* secondo le esigenze di operatività dei diversi utenti.

La distinzione tra **livello esterno** e **logico** può, in molti casi, risultare *trasparente* agli utenti, che, ad esempio, in un ***RDBMS*** “*vedono*” semplicemente un insieme di tabelle.

## Regolamentare gli Accessi
---
>Gli utenti di un DB sono classificabili in tipologie, a cui vanno associate ***autorizzazioni distinte***.

>[!info] Gestione Autorizzazioni
>La ***gestione delle autorizzazioni*** può risultare complessa, per questo motivo sono previste figure di *Data Base Administrator* che conferiscono agli utenti i "**giusti**" privilegi.

Il [[../Interrogazioni/SQL#Componenti SQL|DCL]] di [[../Interrogazioni/SQL|SQL]] semplifica la concessione di privilegi a una classe di utenti.

## Persistenza dei Dati
---
> Un **DBMS** deve garantire *persistenza nei dati*.

>[!caution] Concorrenza
>Un **DBMS** deve garantire che gli accessi ai dati, da parte di diverse applicazioni, non interferiscano tra loro ***violando vincoli di integrità***.

È necessario far ricorso a opportuni meccanismi di ***controllo*** *della* [[../../Sistemi Operativi/Teoria/8 - Concorrenza|concorrenza]].

>[!danger] Protezione dai Guasti
>È possibile che per qualche motivo (*disk failure*, *interruzioni di rete*, *intervento dell’utente*, *transaction abort*, *errori software*, ...) solo una parte delle operazioni da eseguire sia **effettivamente eseguita**.

Per garantire l'integrità il **DBMS** deve provvedere ad annullare tali modifiche.
- Si usano le [[Transazioni]]
## Proprietà ACID
---
>[!help] ***A***tomicity 
>La [[#Transazione]] è ***indivisibile*** nella sua esecuzione e la sua esecuzione deve essere o totale o nulla.

>[!abstract] ***C***onsistency
>Quando inizia una ***transazione*** il database si trova in uno *stato consistente* e al termine della transazione il database **deve ancora essere** in un stato consistente.

>[!note] ***I***solation
>Un’***esecuzione concorrente*** di più transazioni è "*equivalente*" a un’***esecuzione seriale*** delle stesse.

>[!check] ***D***urability
>Detta anche ***persistenza***.
>Al termine della ***transazione*** i dati modificati *devono essere stati memorizzati* in un dispositivo durevole e deve essere registrato il **completamento della transazione**.

## Moduli di un DBMS
---
![[attachements/DBMSmodules.png]]

>[!example] Moduli

- La base di dati e il catalogo del **DBMS** sono *memorizzati su disco*.
- L'accesso al disco è controllato dal [[../../Sistemi Operativi/Teoria/3 - Livelli del Sistema Operativo#Introduzione|sistema operativo]].
- Alcuni **DBMS** hanno un modulo di ***gestione del buffer***, per pianificare operazioni di lettura e scrittura su disco.
- Un **gestore dei dati archiviati** che controlla l'accesso alle informazioni memorizzate su disco.

#### Layer del DBMS
![[attachements/DBMSLayers.png]]