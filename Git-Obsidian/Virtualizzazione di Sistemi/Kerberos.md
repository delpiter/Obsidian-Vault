## Origini
---
>[!info]
>***Kerberos*** è un sistema di autenticazione nato nel $1983$ dalla collaborazione tra `MIT`, `IBM` e `DEC`.

Il nome *kerberos* deriva dalla mitologia greca (cane a tre teste che guarda le porte del'inferno).

Il cane simboleggia con le tre teste i tre scopi originali del sistema:
- [[../Reti/Application Layer/HTTPS#Autenticazione e Confidenzialità|Autenticazione]].
- ***Autorizzazione***: Autorizzare un client autenticato ad utilizzare un servizio.
- [[../Reti/Crittografia|Cifratura]].

## Obbiettivi
---
> [!tldr] Idea
> ***Kerberos*** è un server fidato di gestione di chiavi (Trusted key server system).

 Fornisce un *servizio di autenticazione* **centralizzato** basato su [[../Reti/Crittografia#Simmetrica|chiavi private simmetriche]], separato dal servizio stesso.



> [!important] Importante
> Permette agli utenti di accedere a servizi distribuiti nella rete, ***senza che l'utente debba fidarsi dei server fornitori del servizio***.

Si deve invece fidare del server di autenticazione centralizzato.

L'autenticazione si basa su un nuovo modello di fiducia a chiavi private con terza parte fidata.
- Nel sistema ***kerberos*** le due parti si trovano in una relazione di fiducia **solo** verso una terza parte avente funzione di garante dell'identità dell'uno verso l'altro.

### Key Distribution Center

> [!help] KDC
> La terza parte è chiamata ***key distribution center*** e si occupa di un dominio detto ***Realm***.

I *principal* di un realm sono *sia utenti che servizi* che si possono **autenticare** tramite **kerberos**.


> Struttura del nome di un principal:
- `primary/instance@realmName`

Dove:
- *primary* è il nome dell'utente o servizio.
- *instance* è la qualifica di un utente.

Ciascun client e server condivide con il `KDC` una chiave (*key*) crittografica.
- Il `KDC` si occupa di presentare un principal ad un altro principal tramite le chiavi, mantenendone la segretezza reciproca.

### Assunzioni di Kerberos
> Di seguito alcune assunzioni del sistema kerberos

1. Le **password** non sono "*facili*".
2. Le **workstation** sono *sicure* (no keylogger).
3. La **rete** è *insicura*.
	- Riferito alla rete che collega client e server a *kerberos*.


> [!quote]
> In the kerberos architecture, every realm (security domain) **must** operate a *phisically secure environment* that hosts a **key distribution center**.


> [!caution] Strategie
> 

- [[Scenari di Integrazione#Single Sign On|Single sign-on]].
- Le password non sono mai trasmesse in chiaro.
- Si usano *solo* **chiavi private** tra i due che devono comunicare.
- Implementa un protocollo di autenticazione che estende di Needham-Schroeder per la distribuzione di chiavi.
- Il `KDC` mantiene una **chiave segreta per ciascun principal** (utente, servizio o host) che deve comunicare.


> [!failure] Requisiti
> La sicurezza è basata anche sui ***timestamp dei ticket***, è di importanza critica che gli orologi dei server siano regolati con accuratezza.
> 

I ticket hanno una *scadenza breve* per prevenire attacchi di forza bruta e di replica.
- Se gli orologi subiscono scostamenti si rende la ***rete vulnerabile a questi attacchi***.

>[!help] NTP
> Il ***network time protocol*** è un protocollo che serve a sincronizzare gli orologi dei vari computer attraverso una rete a commutazione di pacchetto.

Protocollo client/server, in un dominio [[Ciro/Active Directory|Active Directory]] di solito è il primary domain controller.
### Applicabilità
> Kerberos non è facilmente applicabile in tutti i contesti

> [!abstract] Kerberize
> Le applicazioni devono essere ***modificate per usare il protocollo kerberos***, uno specifico protocollo di comunicazione tra l'entità (app) che richiede un servizio e l'entità che lo deve fornire.

Alcune applicazioni supportano già kerberos:
- `AFS` e `NFS` ([[Docker/File System del Container#File System Distribuiti|File System Distribuiti]]).
- [[../Tecnologie Web/Architettura del Web#Web Solution Stack|Apache]] e Apache2.
- Cisco routers e switches.
- Mac OS X
- Microsoft Windows
- OpenSSH
- PAM (Pluggable Authentication Modules).
- Qualsiasi software `{java icon} java` che usi `jaas/jgss`.

È comunque possibile modificare qualsiasi applicazione affinché utilizzi kerberos.

### Overview
> [!help] Ambiente
> Un ***ambiente kerberos*** consiste di:
> - Un server kerberos (`KDC`)
> - Un insieme di clients registrati sul server che condividono le chiavi con esso.
> - Un insieme di server applicativi che condividono le chiavi con il server.

![[attachements/KerberosOverview.png]]


> Steps
1. L'applicazione utente negozia inizialmente con l'AS per identificarsi.
2. L'autentication server fornisce una credenziale di autenticazione non corrompibile (ticket granting ticket: `TGT`).
3. L'utente esegue richieste di accesso ai servizi dal Ticket Granting Server sulla base dei `TGT`.

La chiave $K_{c}$ che un utente $c$ usa per criptare le comunicazioni con l'AS è ricavata tramite l'*applicazione di una funzione di hash della password* dell'utente.
