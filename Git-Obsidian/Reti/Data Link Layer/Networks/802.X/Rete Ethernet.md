## 802.3
---
> Basato sul [[LAN#Con Rilevazione del Canale|protocollo di accesso]].

### Carrier Sensing Multiple Access
>[!info] Carrier Sensing
> Ogni stazione che debba trasmettere rivela presenza di un segnale sul bus e ***trasmette solo se è libero***.

> ***Tipologie***

$1$-*Persistent*:
- Si **aspetta la fine** del frame e poi si trasmette.

$0$-*Persistent* o non *Persistent*:
- Si fa partire l'algoritmo di ***back-off***.

$p$-*Persistent*:
- Si trasmette con probabilità $p$ e si fa partire l'algoritmo di back off con probabilità $(1-p)$.
### CSMA with Collision Detection
>[!tldr] Idea
>Protocollo che ***limita*** ma ***non elimina*** la possibilità che due stazioni parlino in *contemporanea*.

Permette un'utilizzazione **molto efficiente della banda disponibile**.
#### Collisioni
>[!todo] Collision Domain
>Il ***collision domain*** è l'insieme delle stazioni connesse alla medesima rete ethernet che *possono collidere in trasmissione*.

Per garantire il funzionamento del `CSMA-CD` si devono imporre vincoli alla dimensione massima della [[LAN]].
- In funzione della **dimensione dei frame**.
- In funzione della **velocità di trasmissione**.

> ***Intervallo di Vulnerabilità***: $2\tau$
- Chiamiamo `A` e `Z` le stazioni più distanti sul `bus` e $\tau$ il tempo di propagazione + il tempo di rilevazione.
- `A` esegue il carrier sensing all'istante $t_{A}$
	- Se `Z` fa carrier sensing tra $t_{A}$ e $t_{A}+\tau$ **non rileva attività** e può iniziare a trasmettere.
	- Se `Z` ha trasmesso tra $t_{A}$ e $t_{A}-\tau$ `A` non rileva il segnale di `Z` e ***si ha collisione***.
#### Slot Time
>[!info]
>Lo ***slot time*** è il tempo necessario per trasmettere $512$ `bit` in reti a $10$ e $100$ `Mbit/s`.
>- $4096$ `bit` in reti a $1$`Gbit/s`

Il [[Controllo del Canale#Canale di Comunicazione|frame]] deve avere una dimensione minima uguale allo slot time.

Lo **slot time** deve essere superiore alla somma:
- Del tempo di *andata e ritorno del segnale*
- Del tempo necessario per **rilevare la collisione** e lanciare la *sequenza di jamming*.
Fissata la dimensione dello **slot time** ogni trama di dimensione minore *viene scartata*
- Viene imposto il *tempo di propagazione massimo* e quindi la dimensione massima della rete.

>[!fail] Sequenza di Jamming
>La ***sequenza di  jamming*** deve essere abbastanza lunga da garantire il *riconoscimento di una collisione* nel circuito di collision detection ($33$ `bit`).

#### Formato del Frame
![[FrameEthernet.png]]

>[!abstract] Campi del Frame

> ***Preamble***
- Campo necessario per la ***sincronizzazione***.
- Composto da $7$`byte` *tutti uguali* (`10101010`).
	- Producono a $10Mbps$ un'onda quadra a $10Mhz$ per $5.6\mu s$.

> ***Start Frame Delimiter***
- Un `byte` uguale a `10101011` per segnalare l'***inizio del frame***.

> **Lunghezza**/**Tipo**
- Per `IEEE 802.3` la lunghezza indica quanti `byte` ci sono nel **campo dati**.
	- Il **tipo del payload** è dato dall'[[Struttura del Data Link#Logical Link Control|LLC]], i primi $4$`bit` sono sempre a $0$.
- Per *ethernet* indica il **tipo di payload** contenuto nel campo dati.
	- Uno dei primi $4$ `bit` è $\neq$ da $0$.
	- Gli altri `bit` rappresentano la lunghezza.

> ***Dati***
- Contiene il ***payload del livello superiore***.
- Il *padding* porta il frame alla lunghezza minima di $64$ `byte` nel caso il campo dati **non fosse abbastanza lungo**.

> ***Frame Checking Sequence***
- Contiene `bit` di *ridondanza* ([[Controllo dell'Errore#Codici Polimoniali|Codice polinomiale di grado 32]]).

> ***Indirizzi***
- [[Struttura del Data Link#Medium Access Control|MAC]].

>[!caution] Delimitazione dei Frame
>Due frame devono essere separati almeno da un ***Inter-Frame Gap***.

#### Funzionamento
> Due host `A` e `B` iniziano la trasmissione contemporaneamente. 

>[!fail] La trasmissione provoca una collisione
>Avvenuta una collisione si mette in moto il seguente procedimento.

1. Un host qualsiasi che si accorge per primo della collisione (*ricevendo pacchetti incompleti*) ***interrompe la trasmissione***.
2. Lo stesso host immette sulla rete un pacchetto, diverso da tutti gli altri, noto come ***sequenza di jamming*** (lungo $48$`bit`).
3. Gli host in ascolto, riconosciuto il *jamming*, interrompono la trasmissione e **scartano i frammenti ricevuti**.
4. Prima di ricominciare la trasmissione, ogni host attende un tempo *semi casuale* dato dall'***algoritmo di backoff esponenziale binario***.

>[!failure] Algoritmo Backoff Esponenziale Binario
>Si attende un tempo semi casuale, ogni fallimento di trasmissione (*collisione*), si aumenta il tempo di attesa.

Dopo $16$ collisioni la **trasmissione viene abortita**.