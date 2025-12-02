>I *protocolli di posta elettronica* sono divisi in due: **Invio** del Messaggio e **Ricezione**

>[!Caution] Fase di Invio
>La ***fase di invio*** di una *e-mail* è controllata tramite il ***SMTP***.
>I server ricevono le *e-mail* dai clienti.
>- I server sono in grado di fare da *relay*.

![[Send-Email.png]]

>[!abstract] Fase di Ricezione
>La ***fase di ricezione*** di una *e-mail* è eseguita tramite **protocolli diversi**.
>Alcuni Protocolli:
>- **POP3**
>- **IMAP4**
>Il client dovrà andare a leggere la posta dai server.
>

![[Read-Email.png]]
#### Standard E-mail
> Il messaggio standard delle e-mail è in formato [[Rappresentazione dei Caratteri#ASCII|ASCII]].

Il pacchetto è formato da:
>[!abstract] Envelope
>Anche detto ***header***, contiene informazioni come:
>- Chi ha *scritto* la mail (`From`).
>- A chi è *destinata* la mail (`To`), include anche i `cc` e `ccn`.
>- *Oggetto* della mail (`Subject`).

>[!help] Body
>Nel ***body*** della mail è contenuto il ***testo*** stesso del messaggio e, se ci sono, dei file allegati ([[#MIME]]).

## Simple Mail Transfer Protocol
---
>[!info]
> Il protocollo **SMTP** [RFC 821](https://www.rfc-editor.org/rfc/rfc821.html) è un protocollo utilizzato per trasmettere messaggi dal *client* al *server* e **tra i server**.
> Il trasferimento delle informazioni avviene tramite connessione [[TCP]]:
> - Attraverso la [[Livello di Trasporto#Numero di Porta|porta]] $25$.

> I messaggi devono essere in formato [[Rappresentazione dei Caratteri#ASCII|ASCII]] a $7$ `bit`.

Il protocollo si basa sulla disponibilità nella rete di computer dedicati, chiamati *mail server*.
- Questi ospitano le caselle di posta (*mailbox*).

![[SMTP.png]]

### Protocolli di Accesso
---
#### POP3
>[!info]
>Il protocollo **POP3** (***P***ost ***O***ffice ***P***rotocol ***3***) [RFC 1939](https://www.rfc-editor.org/rfc/rfc1939.html) utilizza il protocollo di trasporto [[TCP]] sulla [[Livello di Trasporto#Numero di Porta|porta]] $110$ del server
> 

Il protocollo **POP3** presenta diverse *limitazioni*:
- Non consente di creare gerarchie di cartelle
- Dopo la lettura del messaggio , esso viene eliminato dal *server*.
#### IMAP4
>[!tip] Info
>Il protocollo **IMAP4** (***I***nternet ***M***essage ***A***ccess ***P***rotocol ***v4***) [RFC 3501](https://www.rfc-editor.org/rfc/rfc3501.html), supera le limitazione poste dal protocollo **POP3**.
>- Le mail possono restare nel *server*, nella quale è possibile definire una **gerachia di cartelle** a discrezione dell'utente.

A differenza di **POP3**, **IMAP** mantiene lo stato della mailbox da un accesso al successivo.

**IMAP** utilizza il protocollo ***TCP*** sulla [[Livello di Trasporto#Numero di Porta|porta]] $143$
## MIME
---
>[!tldr] MIME Types
>Il **MIME** (***M***ultipurpose ***I***nternet ***M***ail ***E***xtensions) è uno standard che estende il formato dei messaggi *e-mail* per supportare sia caratteri ***ASCII*** sia altri tipi di formati multimediali come audio, video, immagini, etc...

> Il contenuto **multimediale** viene codificato in formato testuale.

L'intestazione dei messaggi di posta dichiarano il tipi di contenuto *MIME* in modo tale che chi riceve il messaggio possa decodificarlo correttamente.