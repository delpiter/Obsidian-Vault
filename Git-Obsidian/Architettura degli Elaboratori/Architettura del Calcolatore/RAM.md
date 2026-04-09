## RAM Statica
---
>[!info] `SRAM`
>Le `SRAM` sono realizzate con circuiti simili a [[../Algebra di Bool e Logica Digitale/Circuiti Sequenziali#Flip-Flop|flip-flop]] di tipo `D`
>Tali memorie sono *molto veloci*, ***alcuni nanosecondi*** per *lettura e scrittura*
>- Tali memorie sono anche ***piuttosto costose***
>
>Questo tipo di memoria viene tipicamente utilizzato per realizzare ***registri*** e ***cache***, entrambe interni alla `CPU`

![[attachements/8Bit-Registry.png]]
>*Registro a $8$ `BIT`, realizzato con $8$ Flip-Flop D*

- Gli $8$ *flip-flop* hanno gli ***input clock*** collegati fra di loro e sono pilotati da una porta `NOT`
	- In questo circuito la memoria è *attivata* sul ***fronte di discesa***
- Per la scrittura è sufficiente rendere i dati stabili sugli *input* $I_{n}$, e inviare un ***impulso*** su `CK`
- Il `BYTE` memorizzato è ***sempre disponibile*** sui pin $O_{n}$

### Realizzazione di un Chip `SRAM`
>*La figura che segue, mostra lo schema di una `SRAM` $4\times 3$ realizzata con $12$ flip-flop D*

![[attachements/SRAM-4x3.png]]
- $I_{0},I_{1},I_{2}$ sono gli *input dati*, necessari per la ***scrittura*** di un dato in *memoria*
- $O_{0},O_{1},O_{2}$ sono gli *output dati*, nei quali ***verranno posti dalla memoria*** le *parole* che devono essere messe in *output*
- $A_{0},A_{1}$ sono i due input per la *selezione dell'indirizzo* della ***parola di interesse***

>[!tldr] Addres Decoder
>Nella parte centrale a sinistra si può trovare un ***decoder*** che decifra l'indirizzo $A_{0},A_{1}$ e attiva di conseguenza la linea ***corrispondente all'indirizzo***

>[!info] `CS` `RD` `OE`
>>[!tip] *C*hip *S*elect
>>Il ***chip select*** abilita il chip per scritture o letture
>
>>[!tldr] *R*ea*D*
>>L'*input* ***read*** indica se il circuito verrà usato per *scrivere* ($1$) o per *leggere* ($0$)
>
>>[!abstract] *O*utput *E*nable
>>Indica al ***chip*** se deve o meno mandare in *output* i *valori letti*

### Read
In fase di ***lettura*** `CS`, `RD` e `OE` sono "*alti*", pertanto:
- Il ***clock*** dei *flip-flop* non viene mai *attivato*
- Gli *output* $Q$ della parola selezionata "*passano*" attraverso le porte `AND` selezionate dal decodificatore di indirizzi per giungere agli `OR` a 4 *input*

Come ultimo stadio, le uscite degli `OR` sono collegate a [[../../Definizioni/Definizioni_Architettura#Tri-State Buffer|tri-state buffer]]
- Nel circuito appare come ***simbolo triangolare***
- Agiscono come *interruttori elettronici* capaci di ***collegare/scollegare elettricamente*** due parti di un circuito

L'`AND` a tre *input* (`CS`$\cdot$`RD`$\cdot$`OE`) abilita i *buffer tri-state* di uscita rendendo disponibile la parola selezionata su $O_{1},O_{2},O_{3}$

>[!question] Perché usare un *buffer tri-state* al posto di un semplice `AND`?

Il bus di *dati* è unico per *input* e *output* 
- È necessario quindi, quando non serve, non mandare nulla in output per evitare interferenze
- A differenza della porta `AND` il *buffer tri-state* toglie *interamente* la *corrente*
### Write
In fase di ***scrittura*** `CS` ha un valore "*alto*", mentre `RD` e `OE` hanno valore "*basso*"
- I dati devono essere disponibili su $I_{0},I_{1},I_{2}$
- L'output della porta `CS`$\cdot$`!RD` è ora "*alto*" e il ***clock*** dei *flip-flop* della parola selezionata viene attivato permettendo la scrittura nella `RAM`

## RAM Dinamica
---
>[!info] *D*ynamic *RAM*
>Le `DRAM` non sono realizzate con *flip-flop* ma con ***array di celle*** ognuna costituita da un ***transistor*** più un ***condensatore***

![[attachements/DRAM-4x4.png]]

>[!tldr] Condensatore
>Il ***condensatore*** è un componente in grado di mantenere per un *piccolo periodo* la ***carica elettrica*** accumulata (*memoria*)

È necessario prevedere un ***circuito di rinfresco*** delle cariche
- Ogni pochi millisecondi tale circuito "*ricarica*" le celle attive consentendo loro di ***mantenere lo stato logico***


### Differenza `DRAM` e `SRAM`
Rispetto alle `SRAM` le `DRAM` sono più ***economiche e dense***
- Circa un *transistor* contro 6 per ogni `BIT`

Sono anche ***significativamente più lente*** 

### DRAM Asincrone
>[!info] *A*sync *DRAM*
>Le prime `DRAM` erano ***asincrone***, la comunicazione con la [[La CPU|CPU]] non è sincronizzata da un ***segnale di clock***
>Sono necessarie ***linee di sincronizzazione addizionali*** perché le parti possano *scambiare le informazioni*

#### Esempio RAM Asincrona
>*Esempio di lettura da parte della `CPU` di dati da memoria asincrona sul `BUS` che collega `CPU` e memoria*

![[attachements/AsyncMemory.png]]
>[!abstract] "*Legenda*"
>- Le linee "*doppie*", come *ADDRESS* e *DATA*, sono dei `BUS`, formati da *tanti fili elettrici* quanti sono i `BIT` che trasporta.
>	- L'*incrocio* fra queste linee indica che è stata effettuata una ***scrittura***
>
>- Le linee "*singole*", Come *MSYN* e *SSYN*, sono dei semplici ***dati di controllo***, formati da *un singolo filo elettrico* che assume o $0$ o $1$
>- Una barra sopra a uno dei `BUS` di controllo indica che quel `BUS` è **attivo** a *livello basso*
>- Il cambio di stato da $0$ a $1$ o viceversa è rappresentato da una *linea obliqua* per dire che il passaggio ***non è istantaneo***

>[!attention] Funzionamento

- La `CPU` rende disponibile sul `BUS` indirizzi (*ADDRESS*) l'***indirizzo della cella di memoria*** che vuole *leggere*
- La `CPU` attiva `MREQ` (***M***emory ***Req***uest), `RD` (*Accesso alla memoria* in lettura) e infine `MSYN` attivato con un piccolo delay per ***assicurarsi la stabilità elettrica degli input***
	- (***M***aster ***Syn***cronization) un segnale di *sincronizzazione* `CPU`
- Quando la memoria vede `MSYN` esegue il lavoro nel minor tempo possibile, e non appena è pronta rende disponibile il valore sul `BUS` *dati* (*DATA*) e attiva `SSYN` 
	- (***S***lave ***Syn***cronization)un segnale di *sincronizzazione memoria*
- Quando la `CPU` vede `SSYN` attivo, legge i dati dal `BUS` *dati* e disattiva `MREQ`, `RD` e `MSYN`
	- La memoria a sua volta disattiva `SSYN`

>[!done] HandShake
>La sequenza di ***eventi interlacciati*** che caratterizza lo scambio di dati *asincrono* prende il nome di ***handshake***

### RAM Sincrone
>[!info] *S*ynchronus *DRAM*
>Introdotte dopo le `DRAM` *Asincrone*, le `SDRAM` sono un tipo di `RAM` dinamica dove un segnale di ***clock*** è responsabile di ***stabilire le tempistiche precise*** nello scambio *dati*
>La risposta è sempre inviata dopo un *numero prefissato* di cicli di **clock****
>- La `CPU` dopo avere inviato la richiesta ***può dedicarsi ad altro***, nell'*attesa* che la memoria sia pronta

Le `DRAM` sincrone sono più *semplici da realizzare*, *interfacciare* e ***consentono la modalità burst***
#### Esempio RAM Sincrona
>*Esempio di lettura da parte della `CPU` di dati da memoria sincrona sul `BUS` che collega `CPU` e memoria*

![[attachements/SyncMemory.png]]

![[attachements/Delays.png]]
>*Tutti i tempi riportati in tabella costituiscono dei vincoli che devono essere rigidamente rispettati al fine di consentire un dialogo corretto tra le due parti*

>[!attention] Funzionamento

Assumiamo che il ***clock*** operi a $40 MHz$, assumiamo inoltre che la lettura dalla memoria richieda $40ns$ dal momento in cui l'indirizzo è stabile sul `BUS`

- Per eseguire una lettura la `CPU` mette l'indirizzo sul `BUS` sul fronte di salita di $T_{1}$
- `MREQ` e `RD` vengono attivati (*attivi bassi*) dalla `CPU`
- Poiché la memoria richiede $40ns$ dal momento in cui l'indirizzo è stabile
	- Essa *non è in grado* di fornire la risposta entro $T_{2}$
	- Per avvertire la `CPU` di ***non aspettare dati***, la memoria attiva il segnale `WAIT` (*attivo basso*) che fa sì che *vengano aggiunti* $1$ o più stati d'attesa
- Quando la memoria è pronta a fornire la parola, disabilita `WAIT` 
	- Durante la prima metà di $T_{3}$ la memoria *mette i dati* sul `BUS`
- Sul fronte di discesa $T_{3}$ la `CPU` legge i dati sul `BUS` e disattiva `MREQ` e `RD`

#### Modalità Burst
![[attachements/BurstMode.png]]

- La `CPU` mette sul `BUS` indirizzi (*address*) l'indirizzo di partenza del blocco e sul `BUS` dati (*data*) il ***numero di parole da trasferire***
- Inoltre, attiva la linea `BLOCK` per comunicare che si tratta di un trasferimento "*burst*"
- La memoria recupera ***le parole del blocco***, ma il ciclo di `WAIT` si ha *solo per la prima* parola
	- Dopodiché viene resa disponibile ***una parola per ciclo***

>[!tldr] ‎ 
>Nei sistemi moderni gli *accessi* alla ***memoria principale*** avvengono quasi esclusivamente in modalità ***burst***
>- La *cache* interposta tra `CPU` e `DRAM` trasferisce **blocchi** di e *non* **singole parole**

## DDR
---
>[!info] *D*ouble *D*ata *R*ate
>Le memorie `DDR` sono le memorie più utilizzate nei `PC` 
>Si tratta di una variante delle `SDRAM`, può inviare i dati alla `CPU` due volte ogni *ciclo ci clock*
>![[attachements/SDR_DDR.png]]

In oltre, nella specifica `DDR` sono previsti $2$ canali di accesso paralleli a $64$ `BIT` ($128$ `BIT` *totali*)

### Generazioni
Esistono diverse generazioni con caratteristiche sempre più performanti

>[!warning] Attenzione
>***Larghezza di banda*** (*bandwitdth*)$\neq$ ***Latenza*** (*latency*)
>- *Bandwidth* $\to$ `BIT` trasferiti al secondo

Per una `DDR` che opera con frequenza di `BUS` pari a $N\ MHz$, la ***larghezza di banda*** si calcola come:
$$
N\times2 \times 8 
$$

Il tempo necessario per reperire la prima parola è invece noto come ***latenza*** e raramente è minore di $10ns$