>[!info] 
>Un DBMS "*convenzionale*" gestisce i dati facendo riscorso principalmente a [[../../Architettura degli Elaboratori/Architettura del Calcolatore/Organizzazione della Memoria#Dischi Magnetici|dischi magnetici]] e [[../../Architettura degli Elaboratori/Architettura del Calcolatore/Organizzazione della Memoria#Solid State Drive|solid-state drive]] (spesso organizzati in configurazioni [[../../Architettura degli Elaboratori/Architettura del Calcolatore/Organizzazione della Memoria#RAID|RAID]]).

Per essere elaborati, i dati devono essere **trasferiti** in [[../../Architettura degli Elaboratori/Architettura del Calcolatore/RAM|memoria centrale]].
- Il trasferimento avviene in termini di ***data block*** (*pagine*).
	- Piccole pagine -> Più operazioni *I*/*O*.

> Le operazioni di *I*/*O* costituiscono il ***collo di bottiglia del sistema***.

Per ottimizzare l'implementazione fisica del **DB**:
- Opportune *organizzazioni delle tuple* sui dispositivi fisici.
- Strutture di accesso *efficienti*.
- Idonee politiche di *gestione dei buffer*.
- Strategie per l'esecuzione delle [[../Interrogazioni/SQL|query]].

## Livelli di Astrazione
---
>[!help] Applicazione
>A ***livello di applicazione*** si opera normalmente su *record* (**logici**).

>[!note] Sistema
>A ***livello di sistema*** di archiviazione si lavora su *blocchi di byte* (es. $4096$), la cui dimensione può **dipendere** da diverse caratteristiche o può essere stabilita dall'utente.

### Il DataBase Fisico
>[!tldr] Idea
>A livello fisico un [[../Introduzione#Database|Database]] consiste in un insieme di file, ognuno dei quali viene visto come una ***collezione di pagine*** di dimensione fissa.

Ogni pagina memorizza ***più record*** (corrispondenti alle [[../Progettazione Logica/Modello Relazionale/Modello Relazionale#Relazione|tuple logiche]]).
- Un record consiste di più campi (*attributi*), di ***lunghezza fissa o variabile***.

>[!note] Nota Bene
>I "*file*" del **DBMS** non corrispondono necessariamente a quelli del ***file system*** del [[../../Sistemi Operativi/Teoria/3 - Livelli del Sistema Operativo#Introduzione|sistema operativo]].

>[!question] Perché non usare il File System?

Le prestazioni di un **DBMS** dipendono fortemente dall’*organizzazione fisica dei dati* sui dispositivi di memorizzazione.
- L'allocazione dei dati dovrebbe mirare a ***ridurre i tempi di accesso***.

È necessario conoscere *come i dati dovranno essere elaborati* e quali sono le ***correlazioni logiche*** tra di essi.

> Il ***File System*** non conosce queste informazioni.

#### Rappresentazione dei Valori
> Per ogni tipo di dati di [[../Interrogazioni/SQL|SQL]] è definito un formato di rappresentazione specifico nel contesto di un **DBMS**.

> `{sql icon} CHAR(n)`
- Si allocano $n$ `byte`, usando un eventuale carattere speciale per stringhe lunghe meno di $n$.

>`{sql icon} VARCHAR(n)`
- Si allocano $m+p$ `byte`, con $m$ ($\leq n$) `byte` usati per gli $m$ caratteri presenti e $p$ `byte` per memorizzare il valore di $m$.

> `{sql icon} DATE` e `{sql icon} TIME`
- Rappresentati con ***stringhe di lunghezza fissa***.
- Per le date: 10 *caratteri* `YYYY-MM-DD`.

Per ogni tipo di record del **DB** deve essere definito uno schema *fisico* che permetta di ***interpretare*** correttamente il significato dei `byte` del record.

>[!help] Record a lunghezza Fissa
> Caso più semplice:
> - Oltre alle *informazioni logiche*, si memorizza anche l'***ordine*** in cui gli attributi sono memorizzati.

>[!abstract] A Lunghezza Variabile
>Diversi casi, per esempio:
>-  Un file che contiene ***record di tipo diverso***.
>- Record con attributi la cui ***lunghezza può variare***.

Possibile *soluzione*:
- Memorizzare prima ***tutti i campi a lunghezza fissa***, e poi tutti quelli a ***lunghezza variabile***
- Per ogni campo a lunghezza variabile si ha un "*prefix pointer*" che riporta l'indirizzo del primo `byte` del campo.

![[attachements/VariableLenghtRecord.png]]

Ogni record include un header che, può contenere informazioni tra cui:
- ***Identificatore della relazione*** a cui appartiene.
- Identificatore del record nel **DB**.
- Un *timestamp* che indica quando il record è stato **inserito**/**modificato**.

### Organizzazione delle Pagine
>[!info]
>La ***directory*** è un campo che contiene un puntatore per ***ogni record nella pagina***.
>L'identificatore di un record (`RID`) nel **DB** è formato da una coppia: (`PID`, `Slot`)
>- *Identificatore della pagina* e *posizione nella directory*.

Il ***buffer manager*** ha il compito di gestire le *richieste di una pagina*.
- Lavora in maniera simile alla [[../../Sistemi Operativi/Teoria/19 - Gestione della Memoria#Paginazione|paginazione]] nei ***sistemi operativi***.
