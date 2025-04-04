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
