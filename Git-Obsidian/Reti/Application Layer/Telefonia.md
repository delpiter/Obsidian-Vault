## VoIP
---
>[!info] Voice over [[Protocollo IP|IP]]
>Il protocollo ***VoIP*** è un protocollo di telefonia *digitale* su rete **IP**.

Per funzionare il protocollo richiede:
- *Digitalizzazione* e *compressione* del **segnale** vocale.
- *Terminale* e *segnalazione* connessi a rete **IP**.
- Rete **IP** per il trasporto.

![[VoIP.png]]

>[!abstract] IP Trunking
>L'**IP trunking** è una tecnologia **IP** basata su collegamenti della rete di trasporto.
>Non ha impatto sulla rete di accesso e sull'utente, ma può avere impatto sulle tariffe.

>[!help] Telefonia IP
>Tecnologia **IP** per la fornitura del servizio di telefonia.
>Ha ***impatto*** sulla rete di **accesso** e sulla rete di **trasporto**.

### Standard
>[!missing] Standard *ITU* basato su $H.323$
> Uno standard **ambizioso** e **completo**.
>- Conseguentemente **complesso**.
>
>Ormai *Obsoleto*.

>[!hint] Standard *IETF* basato su protocollo SIP
>Struttura gerarchica a domini.
>Ogni organizzazione controlla il ***proprio dominio telefonico***.
>- I domini comunicano tramite rete **IP**.
>
>>[!note] Integrato in IMS e parte del VoLTE.

>[!abstract] Standard basato su protocollo proprietario
>Usati da applicazioni come *WhatsApp* e *Telegram*.
>Sfruttano una tecnologia ***Peer-To-Peer***.
>- Tutti gli utenti appartengono alla stessa rete.

#### Session Initiation Protocol
> Protocollo concepito per gestire connessioni di dialogo fra entità remote.

![[SIP.png|500]]

I gateway si identificano come terminali.
- Hanno il compito di "***tradurre***" i messaggi tra l'*endpoint* e altri protocolli.

>[!caution] Protocollo Stateful su base Transazione
>Una ***transazione*** è un messaggio di andata e ritorno.
>Approccio:
>- *Request Iniziale* e attesa di *final response*.
>- Provisional Responses
>	- Informazioni aggiuntive **potenzialmente inaffidabili.**
>
>>[!hint] I messaggi sono correlati tra di loro tramite un **ID**

![[StatefulSIP.png]]

>[!abstract] Dialogo
>Il dialogo si compone di ***diverse transazioni***.

![[Dialog.png|400]]

##### Indirizzamento in SIP
> Gli *indirizzamenti* in **SIP** seguono lo schema base per gli [[Indirizzamento#In Internet|URI]].

>[!info] Ruoli del SIP URI
>Definire nominalmente un utente (***naming***)
>- `sip:user:password@host:port;uri-parameters?headers`
>
>Fornire le informazioni per contattare un utente
>- `sip:bob@137.204.57.10`

>[!example] Esempi

> Domain o Indirizzo IP

- `sip:unibo.test`
- `sip:192.168.42.1`

> SIP URI da chiamare

- `sip:bob@unibo.test`

> SIP Contact Address

- `sip:bob@192.168.42.1:1234`

> Service Identifier

- `sip:voicemail@service.com`
- `sip:user@anonymizer.org`

>[!help] Parametri
>I parametri nell'*URI* possono portare informazioni aggiuntive
>- `sip:bob@unibo.test;maddr=10.0.0.1`

##### Sintassi del Messaggio
> Molto simile al messaggio [[HTTP]]

> ***Request***:

>[!abstract] Start Line
>***Request-Line***
>Contiene il tipo di messaggio che si intende inviare.
>- `INVITE`, `ACK`, `BYE`,...

>[!cite] Header
>Specifica le ***intestazioni*** del messaggio.
>>[!note] Formato
>>`field-name:field-value`
>>I campi possono essere estesi su *più linee*, l'ordine dei campi non è rilevante.
>>- Tranne nel caso in cui due campi hanno lo stesso nome.

>[!tl;dr] Body
>Contenuto del messaggio **SIP** (*email*, *HTTP*).
>>[!attention] Contenuto
>>Il contenuto è definito dall'**header**.
>>- Tipi *multipart* ([[Posta Elettronica#MIME|MIME]])
>>- Tipi di *default* (**Text**)

> ***Response***:

>[!abstract] Start Line
>***Status-Line***
>Contiene la versione **SIP** e lo status-code.

>[!cite] Header
>Specifica le ***intestazioni*** del messaggio (*transaction*, *dialog*, ...).

>[!tl;dr] Body
>Contenuto del messaggio **SIP**
>>[!fail] Generalmente omesso


| Status Code | Significato                           |
| ----------- | ------------------------------------- |
| 1xx         | Provisional; *In ricerca*, *squillo*. |
| 2xx         | Success                               |
| 3xx         | Redirection                           |
| 4xx         | Client Error                          |
| 5xx         | Server Error                          |
| 6xx         | Global Failure                        |

>[!summary] Tipi di Risposte
>***Risposta Provvisoria***
>- Non terminano una transaction (**1xx**)
>
>***Risposta Definitiva***
>- Terminano una transaction (**2xx**,**3xx**,**4xx**,**5xx**,**6xx**)



# Chatty
---
# Argomentazione del documento: "VoIP e SIP"

## 1. Introduzione

La tecnologia VoIP (Voice over IP) rappresenta una svolta nel modo in cui viene gestita la comunicazione vocale, permettendo di trasmettere la voce attraverso reti IP. L'introduzione di questo documento evidenzia i vantaggi principali del VoIP rispetto alla telefonia tradizionale, tra cui:

- Riduzione dei costi
    
- Maggiore flessibilità
    
- Integrazione con altri servizi digitali
    

L'introduzione pone anche le basi per comprendere l'importanza del protocollo SIP, fondamentale per l'instaurazione, gestione e terminazione delle sessioni di comunicazione.

## 2. Cos'è il VoIP

Questa sezione spiega come la tecnologia VoIP consenta la trasmissione della voce in forma digitale, trasformandola in pacchetti IP. L'approccio consente:

- Uso di una rete unica per voce e dati
    
- Possibilità di scalabilità e personalizzazione
    

Si sottolinea anche l'importanza della QoS (Quality of Service) per garantire una qualità audio comparabile a quella della telefonia tradizionale.

## 3. Il protocollo SIP

Il SIP (Session Initiation Protocol) è un protocollo di segnalazione progettato per inizializzare, modificare e terminare sessioni multimediali interattive.

Punti chiave:

- È un protocollo testuale simile all'HTTP
    
- Lavora al livello applicativo del modello OSI
    
- Gestisce la localizzazione degli utenti, l'instaurazione della sessione, la gestione della sessione e la terminazione
    

## 4. Componenti principali del SIP

Questa sezione descrive i principali attori in una architettura SIP:

- **User Agent (UA)**: composto da User Agent Client (UAC) e User Agent Server (UAS)
    
- **Registrar Server**: riceve le registrazioni degli utenti
    
- **Proxy Server**: inoltra le richieste SIP ad altri server
    
- **Redirect Server**: fornisce al client un nuovo indirizzo per il destinatario
    

## 5. Messaggi SIP

Il documento elenca e spiega i messaggi SIP più comuni:

- **INVITE**: avvia una sessione
    
- **ACK**: conferma la ricezione dell'INVITE
    
- **BYE**: termina la sessione
    
- **CANCEL**: annulla una richiesta pendente
    
- **OPTIONS**: interroga le capacità di un server
    

Evidenzia anche le risposte SIP divise in classi (1xx, 2xx, 3xx, ecc.) secondo lo schema dei codici di stato simile a HTTP.

## 6. Registrazione e instaurazione della chiamata

In questa parte si illustra come un client SIP si registra presso un Registrar Server e come viene instaurata una chiamata SIP.

Fasi principali:

- Il client invia REGISTER al server
    
- Il Proxy Server elabora l'INVITE e coinvolge l'UAS
    
- Il dialogo viene stabilito tramite scambio di INVITE, RINGING, OK, e ACK
    

## 7. Considerazioni finali

Il documento conclude con osservazioni sui vantaggi del SIP:

- Standard aperto e flessibile
    
- Supporto per mobilità e presenza
    
- Facilmente integrabile con applicazioni web e mobile
    

Inoltre, si sottolineano le criticità da affrontare, come sicurezza e affidabilità, che devono essere gestite con tecnologie complementari (ad esempio, TLS, SRTP).
