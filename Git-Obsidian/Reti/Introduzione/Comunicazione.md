## Tipi di Comunicazione
---
### Connection Oriented
>[!caution] Concetto
>Una modalità di fornire un servizio si dice ***connection oriented*** quando si stabilisce una **connessione**.
>Una *connessione* è una ***associazione logica*** fra due o più sistemi al fine di trasferire informazioni.

#### Fasi della Comunicazione
>[!abstract] Instaurazione della Connessione
>Fatto tramite lo scambio di opportune ***informazioni iniziali***

Prima che i [[Segnali]] di utente possano essere trasmessi, la rete deve instaurare un circuito fra **terminale chiamante** e **terminale chiamato** (circuito *end-to-end*)

>[!tl;dr] Dialogo
>Trasferimento dei *dati* veri e propri

I due terminali si ***scambiano informazioni*** utilizzando il circuito dedicato.

>[!caution] Disconnessione

Al termine del dialogo il circuito deve essere rilasciato al fine di poter essere usato per altre chiamate.

### Connectionless
>[!abstract] Concetto
>In un trasferimento di dati di tipo ***connectionless*** non è necessario instaurare alcuna connessione prima di effettuare il *trasferimento dei dati*.
>- Per ogni *accesso al servizio* vengono fornite **tutte le informazioni necessarie** per il trasferimento dei dati.
>
>>[!done] Ogni unità di dati viene trasferita in modo **indipendente** dalle altre.

### Modalità di Dialogo
> 3 Modalità di dialogo:

>[!done] Confermato
>Il dialogo ***confermato*** prevede una esplicita conferma da parte del destinatario
>- [[#Connection Oriented]]

>[!missing] Non Confermato
>Il dialogo ***non confermato*** non prevede alcuna conferma.
>- [[#Connectionless]]

>[!question] Parzialmente Confermato
>La *richiesta* viene **confermata** dal service-provider.

![[DialogMode.png|300]]
## Flussi di Comunicazione
---
![[CommunicationFlow.png]]

>[!Regola Generale]
>Il singolo ***flusso informativo*** è identificato da:
>- [[Protocollo IP|IP]] **sorgente** e **destinatario**.
>- [[Livello di Trasporto#Numero di Porta|Numero di Porta]] **sorgente** e **destinatario**.

## Server e Client
---
>[!caution] Server
> I ***server*** sono calcolatori disposti a comunicare con gli altri.
> Con il termine ***server*** indichiamo un'applicazione che rende disponibile un *servizio* mediante un'*interfaccia standard* (***protocollo***).
>>[!done] Apertura Passiva
>>Il processo *server* si predispone a ricevere una connessione eseguendo una ***apertura passiva***.

>[!tip] Client
>Con il termine ***client*** indichiamo un'*applicazione* che è in grado di **utilizzare i** [[Servizi]] messi a disposizione da un **server**.
>>[!done] Apertura Attiva
>>Il processo *client* è colui che fa partire un **software in modo attivo** per comunicare con qualcun altro.

>[!warning] Problema
>Il Client deve conoscere [[Protocollo IP|IP]] e [[Livello di Trasporto#Numero di Porta|numero di porta]] del server
>>[!question] Come fa il client a conoscerli?

Per il ***livello transport***:
- [[Livello di Trasporto#Well Known Port|Well Known Ports]]

## Peer to Peer
---
>Variante del concetto di *Client-Server*.

>[!summary] **P2P**
>Nel ***Peer to Peer*** gli host in rete sono tutti equivalenti e fungono *alternativamente* sia da **client** sia da **server**.

In una rete ***P2P*** qualsiasi nodo utilizza e mette a disposizione contemporaneamente risorse e informazioni in rete.

*Auto Scalabile*: 
- Nuovi **peer** agenti da *server* possono essere aggiunti fornendo nuove capacità e funzionalità

>[!example] Esempio

- [µTorrent](https://www.utorrent.com/)
- Skype