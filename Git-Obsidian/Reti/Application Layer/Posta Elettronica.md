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
> Il protocollo **SMTP** \[RFC821\] è un protocollo utilizzato per trasmettere messaggi dal *client* al *server* e **tra i server**.
> Il trasferimento delle informazioni avviene tramite connessione #addLink ***TCP***:
> - Attraverso la [[Livello di Trasporto#Numero di Porta|porta]] $25$.

> I messaggi devono essere in formato [[Rappresentazione dei Caratteri#ASCII|ASCII]] a $7$ `bit`.

Il protocollo si basa sulla disponibilità nella rete di computer dedicati, chiamati *mail server*.
- Questi ospitano le caselle di posta (*mailbox*).

![[SMTP.png]]

### Protocolli di Accesso
---
#### POP3
>[!info]
>Il protocollo **POP3** (***P***ost ***O***ffice ***P***rotocol ***3***) \[RFC1939\] utilizza il protocollo di trasporto #addLink TCP sulla [[Livello di Trasporto#Numero di Porta|porta]] $110$ del server
> 

Il protocollo **POP3** presenta diverse *limitazioni*:
- Non consente di creare gerarchie di cartelle
- Dopo la lettura del messaggio , esso viene eliminato dal *server*.
#### IMAP4
>[!tip] Info
>Il protocollo **IMAP4** (***I***nternet ***M***essage ***A***ccess ***P***rotocol ***v4***) \[RFC3501\], supera le limitazione poste dal protocollo **POP3**.
>- Le mail possono restare nel *server*, nella quale è possibile definire una **gerachia di cartelle** a discrezione dell'utente.

A differenza di **POP3**, **IMAP** mantiene lo stato della mailbox da un accesso al successivo.

**IMAP** utilizza il protocollo ***TCP*** sulla [[Livello di Trasporto#Numero di Porta|porta]] $143$
## MIME
---
>[!tldr] MIME Types
>Il **MIME** (***M***ultipurpose ***I***nternet ***M***ail ***E***xtensions) è uno standard che estende il formato dei messaggi *e-mail* per supportare sia caratteri ***ASCII*** sia altri tipi di formati multimediali come audio, video, immagini, etc...

> Il contenuto **multimediale** viene codificato in formato testuale.

L'intestazione dei messaggi di posta dichiarano il tipi di contenuto *MIME* in modo tale che chi riceve il messaggio possa decodificarlo correttamente.