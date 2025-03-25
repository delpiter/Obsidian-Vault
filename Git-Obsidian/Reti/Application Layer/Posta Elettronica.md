>I *protocolli di posta elettronica* sono divisi in due: **Invio** del Messaggio e **Ricezione**

>[!Caution] Fase di Invio
>La ***fase di invio*** di una *e-mail* è controllata tramite il ***SMTP***.
>I serve ricevono le *e-mail* dai clienti.
>- I server sono in grado di fare da *ralay*.

![[Send-Email.png]]

>[!abstract] Fase di Ricezione
>La ***fase di ricezione*** di una *e-mail* è eseguita tramite **protocolli diversi**.
>Alcuni Protocolli:
>- **POP3**
>- **IMAP4**
>Il client dovrà andare a leggere la posta dai server.
>

![[Read-Email.png]]
## Simple Mail Transfer Protocol
---
>[!info]
> Il protocollo **SMTP** \[RFC821\]è un protocollo utilizzato per trasmettere messaggi dal *client* al *server* e **tra i server**.
> Il trasferimento delle informazioni avviene tramite connessione #addLink ***TCP***:
> - Attraverso la [[Livello di Trasporto#Numero di Porta|porta]] $25$.

> I messaggi devono essere in formato [[Rappresentazione dei Caratteri#ASCII|ASCII]] a $7$ `bit`.

Il protocollo si basa sulla disponibilità nella rete di computer dedicati, chiamati *mail server*.
- Questi ospitano le caselle di posta (*mailbox*).

![[SMTP.png]]

### Protocolli di Accesso
---
#### POP3
>[!info] \[RFC1939\]
>Il protocollo **POP3** (***P***ost ***O***ffice ***P***rotocol ***3***) utilizza il protocollo di trasporto #addLink TCP sulla [[Livello di Trasporto#Numero di Porta|porta]] $110$ del server
> Dopo la lettura del messaggio , esso viene eliminato dalla *mailbox*.

Il protocollo **POP3** presenta diverse 

#### IMAP4
Mantenimento offline delle mail
Accessibile da più utenti
Messaggi mantenuti dal server
Accessibile parte singola del messaggio
Messaggi organizzati per cartelle

## MIME
---
>[!tldr] MIME Types
>Il **MIME** (***M***ultipurpose ***I***nternet ***M***ail ***E***xtensions) è uno standard che estende il formato dei messaggi *e-mail* per supportare sia caratteri ***ASCII*** sia altri tipi di formati multimediali come audio, video, immagini, etc...

> Il contenuto **multimediale** viene codificato in formato testuale.

L'intestazione dei messaggi di posta dichiarano il tipi di contenuto *MIME* in modo tale che chi riceve il messaggio possa decodificarlo correttamente.