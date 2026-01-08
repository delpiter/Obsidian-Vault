## 802.11
---
>[!cite] Onde Radio
> Le ***onde radio*** sono onde [[Elettromagnetismo|elettromagnetiche]] nella banda di frequenza compresa tra $0$ e $300 Ghz$.

Il protocollo utilizza la banda `ISM` (***I***ndustrial ***S***cientific ***M***edical - da $2.4$ a $2.4835Ghz$) a $2.4Ghz$.
- Disponibile per applicazioni industriali, scientifiche e mediche ***senza la richiesta di licenze***.
	- Con limitazioni sulla *potenza massima trasmessa*.

> Due *metodi principali*

>[!abstract] Direct Sequence Spread Spectrum
>Il `DS-SS` ha la dispersione di spettro in ***banda base***.
>>[!hint] Dispersione Spettrale
>>Nei *sistemi* a ***dispersione spettrale*** il segnale viene *distribuito* con un'operazione di **spreading** su una porzione di *banda più larga* rispetto a quella del segnale.
>>- Rende il segnale **noise-like** e porta una maggiore resistenza all'interferenza.
- Usato per tecnologie wireless come `Wi-Fi` (*Wireless-Fidelity*).

>[!caution] Frequency Hopping Spread Spectrum
>Il `FH-SS`  ha la dispersione di spettro a ***salto di frequenza***.

La ***frequenza del carrier*** cambia frequentemente tra numerosi canali in una sequenza pseudo-casuale.
- Usato per tecnologie come il `Bluetooth`.

### Frame
![[Pasted image 20251206115152.png]]

>[!abstract] Parametri

> ***Frame Control***
- Informazioni di controllo del frame (tipo, versione, sottotipo, etc).

> ***Duration***
- Durata della comunicazione del frame e del relativo `ACK`, serve ad evitare *collisioni*.

> ***Address*** (1-4)
- Indirizzi [[Struttura del Data Link#Medium Access Control|MAC]] di: *mittente*, *destinatario*, *Tx* (trasmettitore) e *Rx* (ricevente) radio.

> ***FCS***
- [[Controllo dell'Errore|Checksum]].
### Standard 802.11x
>[!help] `802.11a`
>Standard che sfrutta una delle più versatili tecniche di modulazione, implementa il `Wi-Fi` a ***banda larga***.
>- Raggiunge i $54$`Mbps` a $5.2Ghz$.

>[!todo] `802.11b`
>Standard con 2 nuove velocità: $5.5$`Mbps` e $11$`Mbps` a $2.4Ghz$.
>- Implementa il `Wi-Fi` a ***banda larga***.
- Migliorata la velocità di trasmissione con la variante `802.11g` in grado di raggiungere $54$ `Mbps`

#### Divisione dello Spettro
> Gli standard `802.11b/g` dividono entrambi lo spettro in $14$ sotto canali da $22Mhz$ ciascuno

![[802.11bg.png]]

Ciascuno nell'intervallo $2.402$ e $2.484GHz$.

>[!warning] I canali sono parzialmente sovrapposti tra loro in frequenza
>Tra due canali consecutivi esiste una **forte interferenza**.
- In presenza di più reti wireless, per evitare sovrapposizioni si usa la ***regola del*** $5$.
	- Si usano $2$ gruppi di canali distanti $5$: $[1, 6, 11]$ e $[2,7,12]$.

>[!question] Perché?
- Diverse nazioni possono avere dei canali riservati diversi per comunicazioni di emergenza.
- Compatibilità.

### Architettura di Rete
>[!tldr] Infrastructure `BSS`
>Architettura molto semplice composta da:
>- Uno o più ***wireless terminal***: i dispositivi mobili dotati di *interfaccia wireless*.
>- Un ***access point***: dispositivo che *connette i dispositivi mobili* tra di loro.

- In questo caso l'***access point*** gestisce l'utilizzo del canale tramite il [[Interfacciamento di Periferiche#Polling|polling]], attribuendo a turno le stazioni che devono trasmettere (L'`AP` è il `Rx` iniziale).
	- L'`AP` trasmette periodicamente un segnale di ***beacon*** che permette:
		- La **sincronizzazione** delle stazioni.
		- La rilevazione della presenza dell'`AP`.
		- La possibilità di entrare nel processo di polling.

> Oppure

>[!help] Modalità Ad-Hoc
>Independent `BSS`, in questa modalità le stazioni comunicano in modalità ***peer-to-peer***.

Il ricevente è anche il `Rx`.

>[!tldr] Infrastructure `ESS`
>L'***extended service set*** consiste in più reti `BSS` collegate tra di loro attraverso una backbone comune creando un *unica rete wireless*.

Permette ad un singolo dispositivo di connettersi a diversi access points ***attraverso un unico*** `SSID`.
#### Problemi di Accesso Multiplo
> 3 *problemi specifici*
##### Stazione Nascosta
> Supponiamo di avere 3 stazioni `A`, `B` e `C`, con i *raggi di azione raffigurati*.

Supponiamo che `A` stia trasmettendo a `B`.
![[Wifi_hidden_station_problem.svg|400]]

>[!fail] Se `C` ascolta il canale, lo troverà libero
>Sarà convinto di poter trasmettere a `B`, cosi facendo ***disturberà la trasmissione*** di `A`.
>>[!failure] Sia `A` che `C` saranno costrette a ritrasmettere

##### Stazione Esposta
> Supponiamo di avere 4 stazioni `S1`,`S2`,`R1` e `R2` con i raggi d'azione raffigurati.

Supponiamo che `S1` stia trasmettendo a `R1` e che `S2` voglia trasmettere a `R2`.
![[Pasted image 20251206112502.png]]

>[!fail] Ascoltando il canale `S2` sentirà la trasmissione di `S1`
>Concluderà erroneamente di ***non poter trasmettere***.
##### Soluzioni
>[!done] Virtual Carrier Sensing
>Soluzione per il problema della ***stazione nascosta***.

>[!tldr] Funzionamento
1. Il mittente invia un frame `RTS` (***R***equest ***T***o ***S***end) al destinatario, contente la *durata della trasmissione* 
	- Il **network allocation vector**, `NAV` mantiene il canale occupato per gli altri trasmettitori.
2. Il destinatario risponde, se è in grado di ricevere, con un frame `CTS` (***C***lear ***T***o ***S***end).
3. Alla ricezione del `CTS` il mittente ***inizia la trasmissione***.

>[!missing] Stazione Esposta
>Il problema della stazione esposta è risolvibile *solo* tramite un'***accurata progettazione fisica della rete***.

##### Collisioni
> Il protocollo [[Rete Ethernet#Carrier Sense Multiple Access with Collision Detection|CSMA/CD]] non è utilizzabile nelle `WLAN`.

>[!done] Carrier Sense Multiple Access with Collision Avoidance
>Questa tecnica introduce un *intervallo di tempo* durante il quale il trasmettitore **attende** al fine di accertarsi che non vi siano altri frame `RTS` o `CTS` sul canale.

- Se un mittente tenta una trasmissione provocando una collisione (non riceve il `CTS`), viene avviato un ***algoritmo di backoff esponenziale binario*** simile al `CSMA/CD`.