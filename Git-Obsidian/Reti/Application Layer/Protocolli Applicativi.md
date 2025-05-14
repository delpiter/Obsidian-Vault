>[!info] Concetto
>I [[ISO-OSI#TCP-IP|protocolli applicativi]] sono utilizzati dalle applicazioni per *scambiare informazioni* in **rete**.
>>[!example] Esempi
>>- [[HTTP]] per il *web*.
>>- `SMTP`, `POP3`, `IMAP` per la [[Posta Elettronica|posta elettronica]].
>>- [[FTP]] per il *trasferimento dei file*.
>>- [[DNS|DNS]] per la *risoluzione dei nomi di dominio* in indirizzi.
>>- **SSH** per l'*accesso remoto sicuro* ad un calcolatore.
>>- ...

I protocolli applicativi devono definire:
- Le **tipologie di messaggi** che vengono scambiati.
- La **sintassi** dei vari tipi di messaggio.
- Il significato (**semantica**) delle informazioni nei messaggi.
- Le **regole** che governano lo scambio dei messaggi.

## API dello Transport Layer
---
>[!abstract] Socket
>Il ***socket*** è l'interfaccia che le applicazioni usano per interagire con i protocolli dello [[Livello di Trasporto|transport layer]].

Sono forniti dal sistema operativo in esecuzione sull'**host** e accessibile tramite primitive.

>[!important] Il socket è una *quintupla*:
>Il ***socket*** è composto da:
>- [[Protocollo IP|Indirizzo]] *Sorgente*.
>- Indirizzo *Destinatario*.
>- [[Livello di Trasporto#Numero di Porta|Porta]] *Sorgente*.
>- Porta *Destinatario*.
>- *Protocollo Utilizzato* ([[TCP]]/[[UDP]]).

### Primitive Berkeley Socket
#### Stream Socket
>Primitive utilizzate per instaurare una ***comunicazione affidabile***.

>[!abstract] Primitive processo "*server*".
>**Socket**:
>- *Crea* una nuova entità [[ISO-OSI#Trasferimento dei Dati|T-SAP]].
>
>**Bind**:
>- Associa l'*indirizzo* al socket creato-
>
>**Listen**:
>- Si mette in *ascolto* sul socket creato.
>
>**Accept**:
>- Pone il server in *attesa* di *accettare* una richiesta da un client.
>
>**Send**/**Receieve**:
>- *Trasmette* / *Riceve* dati sulla connessione stabilita.
>
>**Close**:
>- *Chiude* la connessione e rilascia l'indirizzo del socket.

>[!caution] Primitive processo "*client*"
>**Socket**:
>- *Crea* una nuova entità.
>
>**Connect**:
>- *Blocca* il processo client e tenta di *aprire* una connessione verso il server, *sblocca* a connessione instaurata.
>
>**Send**/**Receieve**:
>- *Trasmette* / *Riceve* dati sulla connessione stabilita.
>
>**Close**:
>- *Chiude* la connessione e rilascia l'indirizzo del socket.

![[StreamSocket.png|500]]

>[!question] Come può un server gestire più richieste contemporanee?
##### Server Iterativo
>[!tldr] Idea
>In un ***server iterativo*** un *ciclo infinito* permette al server di rispondere a più richieste di connessione **successive**, ma in **sequenza**.

Una ***nuova*** connessione **non** viene servita finché non *termina* il servizio di quella in ***corso*** e di altre già in ***attesa***.

##### Server Concorrente
>[!tldr] Idea
>In un ***server concorrente*** un *ciclo infinito* permette al server di rispondere a più richieste di connessione **successive in parallelo**.

Si genera un nuovo [[6 - Processi, Schedule e Thread#Processi|processo]] o [[6 - Processi, Schedule e Thread#Thread|thread]] separato che **gestisce ogni nuova connessione**, tornando in ascolto di altre richieste.
#### Datagram Socket
> Primitive utilizzate per instaurare una comunicazione ***non affidabile***.

Funzioni `socket()`, `bind()` e `close()` *invariate*.

>[!fail] Funzioni rimosse
>Funzioni ***non più necessarie*** ad instaurare la comunicazione:
>- `listen()`, `accept()` e `connect()`

>[!todo] Funzioni diverse
>**Sendto**/**Recievefrom**:
>- *Trasmette*/*Riceve* dati a/da un socket remoto specifico.

![[DatagramSocket.png|500]]