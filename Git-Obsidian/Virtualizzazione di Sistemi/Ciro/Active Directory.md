> ***Active Directory*** è un servizio di directory proprietario sviluppato da Microsoft.


> [!info] Dominio Windows
> Un ***dominio windows*** è un gruppo logico di computer che condividono un database di directory centralizzato (*domain controller*).
>> [!caution] Domain Controller
>> Il ***domain controller*** è un server che risponde alle richieste di autenticazione all'interno del dominio.

Questo database contiene gli ***account utente*** e delle ***informazioni sulle risorse*** appartenenti al dominio, come le stampanti e le condivisioni di file.
- All'interno del dominio ad un utente può essere garantito o negato l'accesso a risorse usando un unico username e password.

### Directory Service
---
>[!definizione]
>Il ***directory service*** è un programma o un insieme di programmi che provvedono ad *organizzare*, *gestire* e *memorizzare informazioni* e *risorse* **centralizzate all'interno di reti di computer**.

Queste informazioni sono poi rese disponibili agli utenti tramite la rete stessa, fornendo anche un controllo agli accessi.

> I directory service forniscono uno strato di astrazione intermedio tra le **risorse da una parte** e gli **utenti dall'altra**.

La struttura dati è simile a quella di un [[../../DataBase/Introduzione|database]] ma:
- Organizzato in struttura gerarchia ad albero
- Ottimizzato in lettura
- Non gestisce le transazioni

Ogni entry ha un ***set di attributi***.
- Ogni attributo ha un nome e uno o più valori e sono definiti nello ***schema***.
- Ogni entry ha un identificativo unico chiamato *Distinguished Name* (`DN`) formato da:
	- Una Relative `DN` (`RDN`), il nome vero e proprio.
	- Un Parent `DN`, il path per arrivare alla entry.
- Paragonabile al ***pathname di un file***.

### Schema
> Lo schema è un insieme di definizioni e vincoli riguardanti la struttura del ***directory information tree***.


> [!info]
> Lo ***schema*** contiene la lista delle classi e degli attributi di oggetti definiti alla directory.

Ricorda lo schema di un database.

## Active Directory
---
>[!definizione]
>***Active Directory*** è principalmente un *insieme di protocolli di rete* in cui il principale di esse è un servizio di directory che lavora in simbiosi con protocolli di autenticazione e naming.

Questi protocolli sono:
- Lightweight Directory Access Protocol (`LDAP`)
	- Protocollo di accesso a un servizio di directory
	- Definisce il protocolli per lo scambio di informazioni della directory tra *client* e *server*.
- [[../Kerberos|Kerberos]]
	- Protocollo che permette l'autenticazione degli utenti, permette il [[../Scenari di Integrazione#Single Sign On|Single Sign On]]
- Network Time Protocol (`NTP`)
	- Protocollo che serve a sincronizzare gli orologi dei vari computer attraverso una rete a [[../../Reti/Introduzione/Comunicazione#Commutazione|commutazione di pacchetto]]
- [[../../Reti/Application Layer/DNS|DNS]]
	- Record DNS usati:
		- ***SRV***: Localizzatore di servizi
		- ***PTR***: Restituisce un nome di dominio dato un `IP`.

### Struttura di Active Directory
#### Domini, Alberi e Foreste
> Alcune definizioni

>[!info] Dominio
>Un ***dominio*** è un gruppo *logico* di computer che condividono un database di directory centralizzato.

Un dominio di active directory è solitamente un dominio non accessibile dall'esterno (`.local`).

> [!caution] Albero
> Un ***albero*** è una struttura di domini che *condividono uno spazio dei nomi contiguo*.


> [!tip] Foresta
> Una ***foresta*** è un insieme di alberi che non condividono uno spazio dei nomi contiguo ma condividono il **global catalog**, lo schema e la configurazione della directory.

#### Organization Units

> [!info] Info
> Una ***organization unit*** è un contenitore che ci permette di organizzare gli oggetti (`OU`, *computer*, *users*, *groups*, etc...) per meglio rappresentare la struttura dell'organizzazione.

**Non** hanno uno spazio dei nomi separato.
- Due utenti in diverse `OU` **NON** possono avere lo **stesso username**.

All'interno delle `OU` vengono tipicamente inseriti i computer ai quali si vogliono applicare particolari impostazioni a seconda delle `OU` a cui appartengono (`Group Policy`).
- Una group policy è una regola che viene applicata a tutti i dispositivi del gruppo.

Le group policy possono essere ad un dominio, ai siti o alle singole `OU`.
#### Sites

> [!hint] Info
> I ***sites*** sono raggruppamenti fisici e non logici di computer, spesso legati da una *stessa sottorete* `IP`.

La definizione dei *sites* è indipendente dalla struttura dei domini delle `OU`.
- Vengono utilizzati per controllare il traffico di replicazione fra i vari domini.

Definiscono le connessioni identificando connessioni lente (`WAN`, `VPN`) dalle connessioni veloci (`LAN`).
- Principale utilizzo è quello di permettere ai client di connettersi al domain controller più vicino.
#### Le partizioni

> [!abstract] Info
> Le informazioni all'interno di un `AD` sono ***logicamente suddivise in partizioni***.

> ***Schema Partition***
- Ne esiste una sola nella foresta, contiene la definizione degli oggetti e le regole per la creazione e la gestione.
- Viene replicata in ogni ***domain controller***.

> ***Configuration Partition***
- Come per lo schema partition ne esiste solo una replicata in ogni `DC`.
- Contiene la [[../../Reti/Introduzione/Topologie di Rete|Topologia]] della foresta.

> ***Domain Partition***
- Ne esistono diverse nella foresta, una per ogni dominio.
- Contengono informazioni sugli utenti, gruppi, computer e `OU` del dominio.

> ***Application Partition***
- Vengono memorizzate le informazioni delle *applicazioni di Active Directory*.
- Es. vengono memorizzate le informazioni del `DNS`.

#### Global Catalog

> [!help] Info
> Un domain controller configurato come ***global catalog*** conserva tutte le *informazioni relative al suo dominio* più le informazioni relative agli altri domini della foresta.

Contiene oltre all'intera partizione del proprio dominio, una replica parziale e di sola lettura delle *partizioni degli altri domini*.

> Funzioni del ***Global Catalog***
1. Viene usato per fare le ricerche dei client in Active Directory
2. Logon dell'utente e appartenenza ai gruppi universali
3. Quando un utente si autentica tramite lo User Principal Name il `GC` si occupa di capire a quale dominio appartiene per poi contattare un domain controller di quel dominio.
#### Replicazione all'interno del Dominio
> Alcuni dati della directory sono replicati attraverso un meccanismo chiamato `DFS`

> [!failure] Distributed File System
> Il `DFS` è un set di servizi che permette di presentare diverse condivisioni su diversi server, come unica unità ed eventualmente replicarle fra loro.

Si compone di due servizi principali:
- `DFS Namespace`, è il servizio che si occupa di presentare le varie condivisioni come una unica unità
- `DFS Replication`, è il servizio che si preoccupa di mantenere sincronizzate fra loro le unità distribuite.

#### Ruoli in Active Directory

> In Active Directory i domain controller sono allo stesso livello di importanza.

Ogni modifica agli oggetti può essere fatta da qualunque `DC` (*multimaster update*).
- Eventuali conflitti vengono gestiti attraverso il *conflict resolution* (Last edit wins).
- In alcuni casi è meglio prevenire tale conflitto.

> [!abstract] Operation Master
> Per evitare questi conflitti è possibile definire un **operation master**, l'unico `DC` in grado di apportare modifiche.

Questo ruolo è "trasferibile" tra controller, da qui il nome `FSMO` (Flexible Single Master Operation)

##### Ruoli FSMO

> [!help] Per-domain role
> 

> ***PDC Emulator***
- Master per la sincronizzazione degli orologi e il cambio delle password utenti.

> ***RID Master***
- Gestisce i relative ID degli oggetti creati, responsabile dello spostamento degli oggetti tra domini.

>***Infrastructure Master***
- Gestisce la consistenza dei riferimenti degli oggetti tra i domini.


> [!abstract] Per-forest role
> 

> ***Schema Master***
- Gestisce i cambiamenti dello schema della foresta e la propagazione delle modifiche.

>***Domain Naming Master***
- Gestisce l'aggiunta o la rimozione di domini in una foresta.

### Tools di Active Directory

> [!help] Active Directory Domains and Trusts

> Permette di:
- *Visualizzare* i domini della foresta
- *Gestire* il livello di funzionalità del dominio e della foresta
- *Cambiare* il ruolo **domain name master**

