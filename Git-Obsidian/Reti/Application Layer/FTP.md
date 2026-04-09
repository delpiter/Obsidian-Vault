## File Transfer Protocol
---
>[!info]
>L'`FTP` [RFC 959](https://www.rfc-editor.org/rfc/rfc959.html) è un protocollo di rete utilizzato per il ***trasferimento di file*** tra un *client* e un *server* su una *rete*.
>Il protocollo regola la **comunicazione** tra due sistemi terminali dei quali uno agisce da client e uno da server.

Il protocollo consiste in due ***connessioni***:
- Dalla [[../Transport Layer/Livello di Trasporto#Numero di Porta|porta]] $21$ viaggiano i *comandi*.
- Dalla **porta** $20$ viaggiano i *file*/*dati*.

### Connessione di Controllo
>[!help] Idea
>La ***connessione di controllo*** è dedicata al trasferimento di **comandi**  e delle risposte tra *client* e *server*.

Il **server** utilizza la porta $21$ per la *connessione di controllo*.
### Connessione Dati
>[!caution] Idea
>La ***connessione dati*** è dedicata esclusivamente al trasferimento di file

Il **server** utilizza la porta $20$ per la *connessione dati*.

### Funzionamento
>[!abstract] Connessione
>Per iniziare il trasferimento, viene instaurata una connessione tramite una sorta di  [[../Transport Layer/TCP#^bd3d55|three-way-handshake]].

![[attachements/FTP.png|450]]

La connessione "**attiva**" avviene con i seguenti passaggi:
1. Il **client** sceglie due porte libere: una per i *comandi* e una per i *dati*.
2. Il **client** invia un messaggio al **server** tramite la *porta dei comandi*.
	- Il messaggio contiene la **porta utilizzata dal client** per il trasferimento dei dati.
3. Il **server** risponde con un **ACK** flag.
4. Il **server** invia messaggi "prova" sul canale di trasferimento di dati.
5. Il client risponde con un **ACK** flag.

>[!done] Il server apre la connessione "**data**".
### Connessione Passiva
> Usata se il *client* è schermato da un apparato [[../Network Layer/Network Security/Network Address Translation]] o [[../Network Layer/Network Security/Firewall]].

>[!cite] Passive Mode
> Nella modalità passiva, è il **client** che apre la connessione data.
>>[!question] Come fa il client a sapere quale porta usare?

È il **client** a comunicare al server l'inizio di una *comunicazione* "**passiva**"
- Il **server** risponderà con una *nuova porta* che verrà utilizzata per il trasferimento dei dati.
![[attachements/PassiveFTP.png|450]]

### Comandi
> Riportiamo di seguito i ***principali comandi***.

>[!info] Canale di Controllo

| Comando | Parametro      | Significato                                                   |
| ------- | -------------- | ------------------------------------------------------------- |
| *USER*  | Identificativo | **Identificazione** del client presso il server.              |
| *PASS*  | Password       | Invio di **chiave di sicurezza** per accedere al servizio.    |
| *QUIT*  |                | Richiesta di **chiusura** della connessione di **controllo**. |
| *PORT*  | Numero Porta   | Indicazione del **numero porta** per la connessione dati.     |

>[!tl;dr] Connessione dati

Per la connessione dati vengono messi diversi comandi per *creazione*, *modifica*, *lettura* e *eliminazione* di **file** e **directory**.