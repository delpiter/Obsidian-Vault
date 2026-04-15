>[!question] Cosa succede quando vogliamo creare una applicazione nel mondo reale?

>[!help] System Integrator

Il ***system integrator*** è la figura che si occupa di progettare e realizzare sistemi complessi, costituiti da multipli componenti che *interagiscono con la rete*.
- Necessita di competenze che spaziano in **molti ambiti dell'informatica**.
	- [[../Reti/Standards/ISO-OSI|Protocolli di rete]], sicurezza nei sistemi di rete, [[../Programmazione/Introduzione Programmazione/Linguaggi|programmazione]], ***virtualizzazione***, etc...

## L'integrazione nel mondo dell'Automazione
---
>[!info]
>L'integrazione con il resto del mondo concerne spesso l'***esportazione real-time di dati*** di sensori della macchina, su cui si opera con vari sistemi.

L'integrazione richiede la conoscenza di protocolli di comunicazione specifici per l'ambiente dell'automazione ed i meccanismi di sicurezza.
- Protocolli STUN e TURN cercano di capire se c'è modo di istanziare una comunicazione attraverso il [[../Reti/Network Layer/Network Security/Network Address Translation|NAT]].

![[attachements/IntegrationOfRealSystems.png]]

## Sistemi a Micro-Servizi
---
>[!abstract] Applicativi Monolitici vs Micro-Servizi
>Gli applicativi moderni nel mondo reale sono costituiti da molteplici componenti separati e personalizzabili detti ***micro servizi***.

Se un sistema monolitico aveva bisogno di due librerie (possibilmente in conflitto), un sistema a micro-servizi separa i due concetti in componenti diversi.
- I ***componenti sono detti micro-servizi***.
- Possono essere in esecuzione su uno stesso host o su *macchine diverse*.

![[attachements/MicroServices.png]]

>[!example] Esempi di micro-servizi
- *Macchine virtuali* con [[../Sistemi Operativi/Teoria/3 - Livelli del Sistema Operativo#Introduzione|Sistema Operativo]] a scelta.
- *Disco virtuale* accedibile dalle macchine virtuali.
- *Archive Storage*, per archiviazione a basso costo per accessi rari.
- *Distributore di carico web* e istanziatore a runtime di nuove `VM` per sopperire a picchi di carico (**kubernetes**).
- [[../Reti/Data Link Layer/Networks/VPN|VPN]], [[../Reti/Application Layer/DNS|DNS]].
- *Multi factor authentication*.
- etc...

> Esempio reale:
- Il server web [[../Tecnologie Web/Architettura del Web#Web Solution Stack|Apache]] è solitamente creato come micro-servizio.

>[!question] Perché sviluppare un sistema a micro-servizi

Un applicativo strutturato in tanti componenti disaccoppiati (***loosely coupled***) e distribuiti su diversi host porta a considerare un'applicazione come un sistema.

### Vantaggi
>[!abstract] Riusabilità
>Le componenti trasformati in micro-servizi possono **essere usati da diversi applicativi**.

>[!summary] Scalabilità
>Vengono replicati e bilanciati *i soli micro servizi che necessitano*.

>[!failure] Deployment
>Può essere realizzato sia su una stessa macchina che su ***macchine differenti***.

### Problematiche
> C'è una forte necessità di comunicazione.

Si richiede di:
- Costruire micro-servizi che espongono **solo interfacce software** e protocolli di comunicazione **standard**.
- Progettare le applicazioni stesse che *utilizzino questi standard*.
- Assicurare che la rete ***permetta il passaggio dei messaggi***.

>[!todo] Progettare le Comunicazioni
>Parte fondamentale della progettazione di un sistema "a ***micro-servizi***" è costituito dalla *progettazione delle comunicazioni tra i componenti*.

#### Message Broker
> I ***bus di messaggi*** vengono chiamati in modi diversi (come message bus o broker).

>[!tldr] Protocolli
>Esistono diversi protocolli per lo scambio di messaggi, tra cui MQTT e AMQP #addLink.

> I protocolli, solitamente:
- Definiscono il formato dei messaggi.
- Permettono di scegliere le modalità di consegna dei messaggi.
- Mantengono i messaggi in coda.
- Mettono a disposizione delle `API` per diversi linguaggi.

### Sicurezza
>  La ***sicurezza*** è un criterio base di progettazione trasversale a tutti i sistemi.

>[!info]
> La ***Centralizzazione/coordinamento*** dei sistemi di autenticazione ed autorizzazione è essa stessa un *fattore di sicurezza* poiché limita i punti di attacco e favorisce il controllo.

> ***Scenari***
- Sicurezza nei *mezzi trasmissivi*.
	- Canali wireless.
	- Comunicazioni Applicative.
- Autenticazione delle entità:
	- [[../Reti/Crittografia|Certificati]].
- Autenticazione degli Utenti:
	- Autenticazione **multi-fattore**.

#### Single Sign On
>[!definizione]
>***Single Sign On*** è un generico meccanismo che concede ad un utente l'autorizzazione ad utilizzare più applicazioni mediante una sola verifica iniziale di credenziali.

> L'implementazione può essere fatta in modi diversi a seconda di:
- Dove si trova il computer su cui opera l'utente (stesso **dominio** o **dominio diverso** dal server delle applicazioni).
>[!hint] Join di un PC
>Un computer si trova nello stesso dominio se nel file system del `OS` sono presenti le chiavi di cifratura univoche mediante le quali il `PC` riesce a comunicare con il server del ***Directory Service***.
>- L'aggiunta di un `PC` si dice **Join**.
- Quale **sistema operativo** opera sul computer.
- Se le applicazioni sono **base web** o *no*. (Nel caso web esistono [[../Reti/Application Layer/HTTP#Cookie|cookie e sessioni]]).
>[!help] Approccio RESTful
>Ogni richiesta ad un server ***non fa affidamento*** ad uno stato di una comunicazione precedente.
>- Il *server non mantiene traccia* dello stato, l'utente deve mandare ***tutte le informazioni necessarie*** per fruire il servizio. ^8d35e7

#### SSO all'interno di un dominio
> Vengono usati due protocolli:

>[!failure] Network Time Protocol
>Protocollo utilizzato per la ***sincronizzazione degli orologi*** di due dispositivi connessi ad internet.

>[!tip] Kerberos
>Protocollo che attraverso ***chiavi di cifrature*** e ***marche temporali*** identificano i due attori della comunicazione.
- Protocollo usato da ***microsoft active directory***. #addLink

Composto da due server:
- Uno per l'**autenticazione**.
- Uno per la **generazione delle chiavi**.
>[!danger] Limitazione
>Per utilizzare il protocollo **kerberos** è necessario che le due macchine (*client* e *server*) siano "**joinate**" nello stesso dominio.

#### SSO per Applicazioni Web
>[!hint] Shibboleth
>


![[attachements/Shibboleth.png]]

> 3 Casi:
- Il ***server esegue le operazioni*** e ritorna solo informazioni da visualizzare (classico paradigma client-server per applicazioni web).
- 