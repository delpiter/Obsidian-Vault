
>Di seguito una breve spiegazione di ogni strato dello [[ISO-OSI|stack ISO-OSI]]

![[attachements/StackIso-Osi.png]]
## Physical Layer
---
>[!hint] Scopo
>Lo scopo del ***livello fisico*** è quello di *attivare*, *mantenere* e *disattivare* la connessione fisica fra due entità di livello 2.

Specifica le modalità di invio dei singoli `bit` sul **mezzo fisico di trasmissione**.

Per fare questo deve specificare le caratteristiche:
- **Meccaniche**
- **Elettriche**
- **Funzionali**
- **Procedurali**

## Data Link Layer
---
>[!hint] Scopo
>Il ***livello data link*** deve *attivare*, *mantenere* e *disattivare* la connessione fisica fra due entità di livello 3.
>Questo strato rende **affidabile** il collegamento fra i nodi di rete.

Funzioni tipicamente svolte dal livello 2:
- Strutturazione del flusso di dati in ***unità di dialogo*** (*frames* o *trame*).
- Controllo e gestione degli ***errori di trasmissione***.
- Controllo di ***flusso***.
- Controllo di ***sequenza***.

## Network Layer
---
>[!hint] Scopo
>Lo scopo del ***network layer*** è di far giungere le unità di informazioni (**packets**) al destinatario, scegliendo la strada *attraverso la rete*.

Si occupa del problema della *commutazione*.
- Nelle reti si usa la [[../Introduzione/Comunicazione#Commutazione di Pacchetto|Commutazione di Pacchetto]].
- La funzione svolta dal livello 3 viene detta ***routing***

> Occorre un modo per individuare i destinatari
- È necessario uno ***schema di indirizzi***.
- Lo schema deve essere *universale*.

## Transport Layer
---
>[!hint] Scopo
>Lo scopo del ***transport layer*** è fornire un canale sicuro **end-to-end** (da utente a utente), *svincolando* gli *strati superiori* da tutti i **problemi di rete**.

Una tipica funzione è adattare la dimensione dei frammenti forniti dagli strati superiori (*files*) a quella richiesta dalle reti (*packets*)
- Funzione di pacchettizzazione (***fragmenting/reassembling***).

Può avere altre funzioni:
- Controllo dell'**errore**.
- Controllo di **flusso**.
- etc...

## Session Layer
---
>[!hint] Scopo
>Il ***session layer*** suddivide il dialogo fra le applicazioni in ***unità logiche*** (*sessioni*).

Permette la chiusura ordinata (***soft***) del dialogo:
- Garanzia che tutti i dati trasmessi siano ***arrivati a destinazione***.

Per fare le sue funzioni introduce dei *punti di sincronizzazione*.

## Presentation Layer
---
>[!hint] Scopo
>Il ***presentation layer*** adatta il *formato* dei dati usato dagli interlocutori, *preservandone il significato*.

Ogni interlocutore ha una sua **sintassi locale** e durante il dialogo bisogna concordare una **sintassi di trasferimento**.

## Application Layer
---
>[!hint] Scopo
>L'***application layer*** è l'utente della rete e pertanto non deve offrire servizi a nessuno
>Rappresenta il *programma applicativo* (**application**) che per svolgere i compiti ha ***bisogno di comunicare*** con altre *applicazioni remote*.

>Le **applicazioni** ***non*** possono essere standardizzate completamente