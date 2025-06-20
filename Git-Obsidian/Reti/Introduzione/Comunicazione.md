## Funzioni della Rete
---
>[!summary] Funzioni Principali
>Di seguito le funzioni principali della rete:
>- **Trasmissione**.
>- **Commutazione**.
>- **Segnalazione**.
>- **Gestione**.

### Trasmissione
>[!definizione] 
>La trasmissione consiste nel ***trasferimento fisico del segnale*** da punto a punto o da un punto a molti punti.

### Commutazione
>[!definizione]
>***Instradamento*** delle informazioni all’interno della rete al fine di permettere la *comunicazioni fra punti terminali* per soddisfare le richieste degli utenti.

> Tecniche di Commutazione:

#### Commutazione di Circuito

> Per le reti telefoniche

La rete crea un canale di comunicazione dedicato fra due terminali che vogliono comunicare:
- Detto ***circuito di commutazione***.

Il circuito è **riservato** ad uso esclusivo dei terminali *chiamante* e *chiamato*.

Esiste un ritardo iniziale dovuto al tempo per **instaurare** il circuito
- Dopo di ché la rete garantisce la [[Servizi#Trasparenza Temporale|trasparenza temporale]].

##### Fasi della Comunicazione
>[!abstract] Instaurazione della Connessione
>Fatto tramite lo scambio di opportune ***informazioni iniziali***

Prima che i [[Segnali]] di utente possano essere trasmessi, la rete deve instaurare un circuito fra **terminale chiamante** e **terminale chiamato** (circuito *end-to-end*)

>[!tl;dr] Dialogo
>Trasferimento dei *dati* veri e propri

I due terminali si ***scambiano informazioni*** utilizzando il circuito dedicato.

>[!caution] Disconnessione

Al termine del dialogo il circuito deve essere rilasciato al fine di poter essere usato per altre chiamate.

#### Commutazione di Pacchetto
> Per rete telegrafica o reti di calcolatori.

>[!tldr] Idea
>Trasporta informazioni in ***forma numerica***.

Le informazioni di utente sono *strutturate in messaggi* unitamente ad opportune informazioni di **segnalazione**.

> Commutazione di *Pacchetto*
- I messaggi vengono suddivisi in sotto-blocchi di lunghezza massima prefissata, detti ***pacchetti***:


> Tecniche di commutazione

>[!caution] Connection Oriented
>Una modalità di fornire un servizio si dice ***connection oriented*** (*circuito virtuale*)quando si stabilisce una **connessione**.
>Una *connessione* è una ***associazione logica*** fra due o più sistemi al fine di trasferire informazioni.

>[!abstract] Connectionles
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