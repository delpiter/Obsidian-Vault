## 802.3
---
> Basato sul [[LAN#Con Rilevazione del Canale|protocollo di accesso]].

### Carrier Sense Multiple Access with Collision Detection
>[!tldr] Idea
>Protocollo che ***limita*** ma ***non elimina*** la possibilità che due stazioni parlino in *contemporanea*.

Permette un'utilizzazione **molto efficiente della banda disponibile**.

#### Collisioni
>[!todo] Collision Domain
>Il ***collision domain*** è l'insieme delle stazioni connesse alla medesima rete ethernet che *possono collidere in trasmissione*.

Per garantire il funzionamento del `CSMA-CD` si devono imporre vincoli alla dimensione massima della [[LAN]].
- In funzione della **dimensione dei frame**.
- In funzione della **velocità di trasmissione**.
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

### Strato Fisico
#### Codifica Manchester
>[!tldr] Idea
>Il segnale di clock del trasmettitore e il segnale dei dati vengono combinati per ***garantire una transizione per ogni*** `bit`.

Due convenzioni opposte:
- Nella prima il `bit` $1$ è rappresentato con una ***transizione al semiperiodo*** tra il segnale *alto* e il segnale *basso* ($0$ da basso a alto).
- La seconda afferma l'**esatto opposto**.

>[!done] Pro
- Si elimina il problema delle *lunghe sequenze di* `bit` con **uguale valore**.

#### Cavi per la Trasmissione
>[!info] Notazione
>$x \text{ Base } y$
>Dove
>- $x$ indica che il segnale può viaggiare per $x\cdot 100m$.
>- $y$ indica la velocità in $Mbps$.
##### Cavi Coassiali
> Un cavo coassiale è formato da:
- Un filo conduttore centrale (***core***).
- Racchiuso in una *guaina isolante*.
- A sua volta avvolta in un *foglio metallico* (***calza***).
- Ulteriormente rivestito da una **guaina isolante**.

>[!fail] Cavo ormai vecchio e poco usato

>[!caution] Thick Coax
>$10 \text{ Base }5$
> Cavo coassiale a $50\ohm$.
- Serviva per connettere le [[Routing Globale|backbone]].

>[!summary] Thin Coax
>$10 \text{ Base }2$
> Cavo coassiale a $50\ohm$, diametro molto più piccolo (*circa la metà*).
- Usato per raggiungere le *prese al muro*.

##### Doppini
> Il **doppino** è un cavo elettrico formato da **due fili conduttori** avvolti da una *guaina isolante* e attorcigliati per ridurre rumore esterno.

>[!abstract] Unshielded Twisted Pair
> $10 \text{ Base }T$
> Quattro coppie di fili ***attorcigliati***.

Connettore usato: `RJ45` (*Registered Jack*) o `RJ11`.
> Tipologie di cavo:
- ***Straight Through***: permette il collegamento tra la porta di uno *switch* e un `PC`
- ***Crossover***: permette il collegamento tra le porte di **due switch** o di **due** `PC`.

>[!bug] Shielded Twisted Pair e Foiled Twisted Pair
>> `STP` cavo in cui ogni coppia di fili è ***attorcigliata e schermata***.
>
>> `FTP` è un cavo `UTP` avvolto in un foglio metallico.

>[!failure] Evoluzioni Successive
>Fast Ethernet a $100$`Mbit/s` (`802.3u`).

> $100 \text{ Base } T4$

> $100 \text{ Base } TX$
 
> $100 \text{ Base } FX$: ***Fibra ottica multimodo***.

>[!done] Gigabit (`802.3z`)

> $1000 \text{ Base } SX$

> $1000 \text{ Base } LX$

> $1000 \text{ Base } CX$

> $1000 \text{ Base } T$