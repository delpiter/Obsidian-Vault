## Local Area Network
---
>[!definizione]
>Una `LAN` è una [[Infrastrutture di Telecomunicazioni|Infrastruttura di Telecomunicazioni]] che consente ad apparati indipendenti di comunicare in un'*area limitata*.

Le `LAN` sono *reti di calcolatori* e devono essere implementate scegliendo protocolli par tutti gli strati dell'[[ISO-OSI|OSI]].
- Le dimensioni limitate rendono convenienti soluzioni particolari per gli strati $1$ e $2$.

### Topologie
> Per le `LAN` inizialmente si sono usate le [[Topologie di Rete|topologie punto-multipunto]].

>[!example] Topologie
- A **BUS** unidirezionale
- A **BUS** bidirezionale
- A doppio **BUS**
- Ad anello
>[!hint] Caratteristiche
>[[Reti IP#Broadcast|Broadcast]]:
>- La `LAN` fornisce in modo nativo una comunicazione *da uno a tutti*.
>
>**Collisione**
>- Su un mezzo di trasmissione condiviso c'è la possibilità che più utenti ***inviino informazioni contemporaneamente***.

### Accesso al Canale di Collegamento
>[!caution] Canali Punto-Punt
>Solo la ***sorgente e la destinazione*** hanno accesso al canale.

La sorgente può liberamente ***impegnare tutta la capacità***.

>[!summary] Canali ad Accesso Multiplo
>Più sorgenti accedono al canale *contemporaneamente*, determinando una "***collisione***".

>[!help] Canali ad Accesso Controllato
>Il canale è *condiviso* ma l'accesso viene ***controllato*** in modo centralizzato o distribuito per **evitare collisioni**.

#### Tassonomia
```mermaid
mindmap
  root((Tecniche 
        di 
        Accesso Multiplo))
    Canalizzazione
      FDMA
      TDMA
      CDMA
    Accesso Dinamico
      Accesso Ordinato
        Prenotazione
        Trasferimento di Permesso
      Accesso a Contesa
```


> I protocolli ad [[LAN#Tassonomia|accesso conteso]] ammettono le collisioni e cercano di gestirle.
#### Con Rilevazione del Canale
>[!info] CAP
>La ***Channel Access Procedure*** è l'insieme delle procedure che la stazione effettua per realizzare l'accesso al canale.

>[!caution] CRA
>Il ***Collision Resolution Algorithm*** è l'insieme delle procedure che la stazione effettua per rilevare e recuperare situazioni di collisione.

### Cablaggio Strutturato
> Una `LAN` moderna viene cablata secondo una ***struttura gerarchica*** di $4$ livelli.

>[!help] Campus Distributor
>Centro stella di **comprensorio** (*cablaggio verticale*).
- Interconnette più armadietti di rete per realizzare una `LAN` estesa

>[!abstract] Building Distributor
>Centro stella di **edificio**, contenitore degli apparati attivi della `LAN`.
- Punto di arrivo del **floor distributor**.
- ***Patch Cord***: Spezzone di cavo che connette le porte dello switch ai *patch panel*.
- ***Patch Panel***: Pannello che presenta un insieme di connettori per cavi [[Rete Ethernet#Doppini|UTP]]. 

>[!caution] Floor Distributor
>Centro stella del **piano** (*cablaggio orizzontale*).
- Cavi che collegano le prese a muro con l'armadio di rete in una ***rete a stella***.

>[!hint] Telecommunication Outlet
>***Prese utente***
- Punto di accesso alla `LAN` per l'utente.

### Interconnessione tra LAN
>[!info]
>Per interconnettere più `LAN` servono ***apparati di interconnessione*** che a seconda della funzionalità prendono *nomi diversi*.

>[!example]
- ***Repeater***
	- Collega 2 o più *mezzi di trasmissione*, opera a [[Descrizione dei Livelli#Physical Layer|Livello 1]], amplifica il segnale, rigenera i `bit` entranti e li *sincronizza*.
- ***Bridge***
	- Opera a [[Descrizione dei Livelli#Data Link Layer|Livello 2]] e può interconnettere `LAN` di **tipo diverso** ([[Rete Ethernet|ethernet]] con *Token Ring*).
		- Separa i dati di uno standard dal suo header e inserisce l'**header** dello standard dell'altra rete.
	- Separa i **domini di collisione**.
- [[Routing#Router|Router]].
- Gateways

#### Switch
>[!definizione]
>Uno ***switch*** è un bridge ad alta densità di porte, ciascuna delle quali è connessa con *una sola stazione*.

È in grado di ***trasferire contemporaneamente*** *frame* da più **porte di ingresso** a più **porte di uscita**.
- Opera una funzione di commutazione a livello 2 basata sull'indirizzo [[Struttura del Data Link#Medium Access Control|MAC]].

>[!caution] Differenza con l'**hub**
- Un `hub` è un `bus` collassato, in grado di fare solamente ***broadcast dei frame***.
- Uno **switch** è in grado di fare una *ritrasmissione selettiva dei frame*.

Internamente uno switch contiene una *tabella*:
- Per ogni indirizzo `MAC` collegato, assegna una **porta dello switch**.