## Automatic Repeat Request
---
>[!info]
>I protocolli **ARQ** sono un tipo di [[Controllo dell'Errore]] usati nelle trasmissioni di dati per *assicurarsi* una comunicazione **affidabile** su un canale **non affidabile**.
>>[!quote] Affidabile
>>- Identifica **errori di trasmissione**.
>>- Riconosce **perdita di informazioni**
>>- Riconosce **perdite di sequenza**

Vengono usati nel ***data link layer*** e ***transport layer***.

### Sliding Window
> Tecnica utilizzata quando serve la consegna dei ***frame ordinati*** temporalmente.

>[!caution] Meccanismo
>Il meccanismo usato è quello della ***numerazione a finestra scorrevole***.
>>[!cite] Numerazione
>>I protocolli **ARQ** *numerano sequenzialmente le unità informative* ([[../Standards/ISO-OSI#Trasferimento dei Dati|PDU]] o `bit`) da consegnare ai protocolli superiori.

Trasmettitore e ricevitore mantengono *due contatori*:
- $S$ conta in modo sequenziale le unità informative ***inviate***.
	- Permette il "**posizionamento**" nel flusso.
- $R$ conta le unità informative ***ricevute***.
	- Permette la *conferma di ricezione*.

![[attachements/SlidingWindow.png|600]]

>[!missing] Controllo degli Errori
>Alle **PDU** viene applicata una codifica di canale
>> Il ricevitore
>- Verifica la correttezza delle **PDU** ricevute con il rilevatore di errore
>- Ignora le **PDU** errate
>- Può far partire le *procedure di ritrasmissione*.
>
>> Il trasmettitore
>- Ritrasmette i *frame* ***non correttamente ricevuti***.

>[!done] Pro
>1. Permette la gestione automatica del controllo di flusso.
>2. Permette di riconoscere l'errata ricezione o perdita di dati.
>3. Permette di ricostruire in ricezione la corretta sequenza di dati.
#### Anknowledge
> La corretta ricezione viene *confermata dal ricevitore*.

Il ricevitore invia al trasmettitore il proprio valore di $R$
- **PDU** ricevuta corretta aumenta $R$
- **PDU** ricevuta in modo errato viene ignorata e $R$ *rimane invariata*.

>[!example] Tipi di conferme
>***Esplicita***
>- Ogni **PDU** ricevuta correttamente *genera una conferma*.
>
>***Implicita***
>- Una **PDU** di conferma con $R=n$ conferma la ricezione fino a $n-1$.
>
>***Piggybacking***
>- Viaggia inserita in una **PDU** contenente *dati utili*.

>Gli ***ACK*** sono **PDU** specializzate che *non portano dati utente* ma solo informazioni di controllo per il protocollo.
- Servono nel caso **ARQ** non possa usare il *piggybacking*.
- Il ricevitore non abbia dati da trasmettere.

>[!info] Round Trip Time (*RTT*)
>È il tempo necessario per effettuare un'"**andata e ritorno**" sul canale
>- Tempo trascorso fra la partenza dell'ultimo `bit` di un frame e la ricezione dell'**ACK**.

#### Time Out
> Il protocollo può entrare in uno strato di [[../../Sistemi Operativi/Teoria/9 - Condivisione di Risorse#Deadlock|deadlock]]. 

>[!danger] Se sia i frame che gli **ACK** sono perduti

È necessario un ***time out*** per riprendere il dialogo
- Un clock parte al termine della trasmissione di ciascun frame.
- Se si raggiunge il ***time out*** senza avere conferma si *ritrasmette il frame*.

![[attachements/TimeOut.png|500]]

> Problemi della dimensione del Time Out
- ***Troppo Breve***
	- Non si attende l'arrivo dell'**ACK**, causa il rinvio non necessario di frame.
- ***Troppo lungo***
	- *Inutile attesa* prima di ritrasmettere i frame.

>[!abstract] Recupero dell'errore (*go-back-n ARQ*)
>> Viene perso il frame $N$
>
>Il **ricevitore** scarta tutti i frame successivi e a seconda dell'implementazione *segnala* al trasmettitore la mancata ricezione o *rimane in silenzio*.
>
>Il **trasmettitore** ritrasmette tutti i ***frame*** a partire dal numero $N$.

Concetto molto ***semplice*** ma ***inefficiente***.
![[attachements/ErrorRecover.png|600]]

>[!hint] Recupero dell'errore (*Selective Repeat ARQ*)
>Viene rinviato solamente il frame $N$.
>- Il *ricevitore* deve **riordinare i frame**.

Più ***efficiente*** ma ***complesso***.
##### Finestra di Trasmissione
>[!definizione]
>$W_{T}$ è il ***numero massimo di frame*** che il trasmettitore può inviare senza ricevere alcuna conferma.

La numerazione dei frame viene effettuata **modulo** $M$
- $M=2^n$ dove $n$ è il numero di `bit` usati per la numerazione.

>[!warning] Si può procedere con la trasmissione solo al ricevimento delle conferme

>[!question] Perché limitare la dimensione della finestra?

- Garantire l'unicità di numerazione dei *frame*

##### Controllo di Flusso
>Il ricevitore
- Deve essere in grado di *gestire un'intera finestra*.
- Accorda il *flusso di frame* in arrivo tramite gli **ACK**.

>[!caution] A pieno regime
>Si ha un nuovo **frame** ogni $T_{e}$
>- $T_{e}$ è il tempo necessario per *elaborare un frame*.

