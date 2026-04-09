![[../Introduzione/Introduzione#Canale]]

## Canale di Comunicazione
---
> I canali di comunicazione si trovano nel livello ***Data Link***.

>[!abstract] Protocolli di Linea
>Protocolli usati in un canale sequenziale a banda costante di tipo ***punto a punto*** o ***punto-multipunto***.
>- L'informazione (***frame***) arriva nella *stessa sequenza* con cui è stata inviata, ma con un **ritardo di propagazione** circa uguale per ogni segnale.

## Controllo del Canale
---
>[!question] Serve per risolvere i problemi di carattere semantico prodotti dal livello fisico.

I servizi di ***controllo del canale*** rendono affidabile e sicuro il servizio di collegamento che lo *strato 2* offre allo *strato 3*.

>[!summary] Funzioni
>- *Strutturazione* del Flusso di dati.
>- Controllo e *gestione degli errori* di trasmissione.
>- *Controllo* di flusso.
>- Controllo di *sequenza*.
>- Gestione del *protocollo di accesso*.

#### Problematiche di Sincronismo
> Per riconoscere i `bit` in ricezione occorre determinare gli ***istanti di campionamento*** per ricostruire il **sincronismo**.

>[!check] Soluzioni
>Il canale può essere tenuto ***sempre pieno*** di `bit`
>- Il *protocollo di linea* deve garantire la presenza di segnale anche quando non ha dati da trasmettere
>
>Il canale può avere momenti di vuoto di segnale
>- All'inizio di ogni trasmissione deve essere inserito un ***preambolo di sincronismo***.

> Garantisce la corretta lettura dei singoli `bit`.
##### Sincronismo di Frame
> Bisogna distinguere le [[../Standards/ISO-OSI#Trasferimento dei Dati|PDU]].

>[!caution] Sincronismo
>Si deve garantire il ***sincronismo di frame***.
>
>Protocolli *asincroni*
>- I **frame** possono *iniziare* e *finire* in ***ogni istante***.
>- Le informazioni aggiuntive sono usate per *riconoscere l'inizio e la fine del frame*.
>
>Protocolli *sincroni*
>- I frame devono iniziare e terminare in ***istanti predefiniti***.

#### Affidabilità
>[!question] Come garantire l'affidabilità?

È necessario controllare:

>[!fail] Errori di trasmissione

>[!missing] Sequenzialità dei dati

>[!caution] Flusso dei dati