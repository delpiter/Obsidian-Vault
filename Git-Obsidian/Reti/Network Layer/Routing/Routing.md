> Esistono più percorsi per raggiungere una destinazione da una sorgente

>[!todo] Internet
> Internet è una "***rete di reti***", il cui componente elementare è la ***network*** [[../Protocollo IP|IP]].

Le ***network*** `IP` sono interconnesse da apparati che svolgono la funzione di "***ponte***".
- *Router* o *Gateway*.
- I calcolatori in una **network** `IP` sono connessi dalla medesima **infrastruttura di rete fisica** ([[../../Standards/ISO-OSI#TCP-IP|Livelli]] 1 e 2).

Ogni network `IP` può essere implementata con una **tecnologia specifica**.
- [[../../Data Link Layer/Networks/802.X/Rete Wireless|Wi-Fi]], `ADSL`, [[../../Data Link Layer/Networks/802.X/Rete Ethernet|Ethernet]], etc...

>[!important] Ipotesi Fondamentale
>Tutti gli host appartenenti alla medesima **network** `IP` sono in grado di parlare tra loro grazie alla tecnologia con cui essa viene implementata.


## Rete Logica e Fisica
---
>[!tldr] Rete Logica
>La ***rete Logica*** è la **network** `IP` a cui un `host` appartiene logicamente.

>[!caution] Rete Fisica
>La ***rete Fisica*** è la rete (es [[../../Data Link Layer/Networks/LAN]]) a cui un `host` è *effettivamente connesso*.

L'[[../../Standards/ISO-OSI|architettura a strati]] nasconde gli indirizzi fisici e consente alle applicazioni di lavorare solo con [[../Protocollo IP#L'indirizzo IP|indirizzi IP]].

## Interconnesione
---
>[!help] Interconnettere le network `IP`
>Per far parlare tra di loro le "*isole*" è necessario che vi siano dei *collegamenti* fra le **isole**, degli *apparati* che permettono di usare i collegamenti.
>Deve inoltre essere possibile scegliere il giusto collegamento verso la **network** `IP` destinataria.

### Router
>[!definizione]
>Il ***router*** è un dispositivo elettronico che connette due o più network `IP` inoltrando informazioni.
>- Ha funzioni dal livello $1$ al livello $3$ [[../../Standards/ISO-OSI|OSI]].
>
>È il nodo di commutazione nelle [[../Reti IP]] specializzato per l'utilizzo del [[../Protocollo IP]].

Il singolo calcolatore terminale sceglie un router come *gateway* verso le altre ***network*** `IP`, instrada il datagram verso il router.

Il *router* ha il compito di decidere **in che direzione** inviare il datagram.
- Instradamento (*routing*).
- Il singolo salto viene detto `hop`.

#### Tipologie
> ***Small Office and HOme*** (`SOHO`) router
- Di utilizzo domestico, interfaccia sulla `LAN`.

> ***Access Router***
- Usato dagli `ISP` per dare *accesso ad un servizio*.

> ***Enterprise Router***
- *Interconnessione* fra `LAN` per organizzazioni di medie dimensioni.

> ***Backbone Router***
- Per [[../../Introduzione/Introduzione#Rete di Transito|reti di trasporto]] e connessioni *inter-domain*.

#### Funzioni dei Router
>[!caution] Routing

>[!abstract] Forwarding
- Con ***forwarding table*** costruita con i contenuti della *tabella di routing*.
- Usato per *inoltrare il datagram*.
- Ottimizzata per il *Fast table lookup* (o `FIB` Forward Information Base).
	- Si ottiene a partire dalle informazioni della *Routing Information Base*.

>[!failure] Switching

>[!missing] Trasmission
## Routing Diretto e Indiretto
---
>[!abstract] Direct Delivery
>L'[[../Protocollo IP|IP]] sorgente e destinatario sono sulla ***stessa network***.

Il datagram viene spedito *direttamente al destinatario*.

>[!caution] Indirect Delivery
>`IP` sorgente e destinatario **non** sono sulla ***stessa network***.

L'host sorgente invia il datagram ad un **router intermedio**.

### Routing
>[!definizione]
>Il ***routing*** è la *scelta del percorso* su cui inviare i dati.

I **router** formano una struttura interconnessa e cooperante.
- I datagram passano tra router fino a raggiungere il destinatario.

#### Tabella di Routing IP
>[!summary] Routing Table
>La tabella di routing è una base di dati contenente:
>> Righe o *route*
>- Insieme di informazioni relative alla singola informazione di routing.
> 
>> Colonne o *fields*
>- Informazioni del medesimo tipo relative a opzioni di instradamento.

Il formato della tabella dipende dal [[../../../Sistemi Operativi/Teoria/3 - Livelli del Sistema Operativo#Introduzione|sistema operativo]] e dall'implementazione.

È una tabella risultato dei ***protocolli di routing***.
##### Route
> I campi tipici della singola **route** sono:

>[!help] Destination `D`
>Un numero `IP` valido.

>[!missing] Netmask `N`
>Maschera di rete.

>[!abstract] Gateway `G`
>Numero `IP` a cui consegnare il datagram.

>[!summary] Network Interface `NI`
>Interfaccia di rete da usare per la consegna del datagram.

>[!todo] Metric `M`
>Specifica il costo della particolare route.

| Destination  | Netmask       | Gateway       | Interface | Metric |
| ------------ | ------------- | ------------- | --------- | ------ |
| 10.0.0.0     | 255.255.255.0 | 192.168.1.1   | ppp0      | 10     |
| 172.16.5.0   | 255.255.255.0 | 172.16.1.254  | ppp1      | 20     |
| 192.168.50.0 | 255.255.255.0 | 0.0.0.0       | en0       | 0      |
| 0.0.0.0      | 0.0.0.0       | 192.168.1.254 | en1       | 100    |
| 10.10.20.0   | 255.255.255.0 | 172.16.5.1    | en2       | 30     |
| 224.0.0.0    | 240.0.0.0     | 0.0.0.0       | ppp2      | 1      |

>[!todo] Uso della tabella di Routing

1. Il singolo nodo riceve un datagram.
2. Estrae dall'intestazione il `IP_D`
3. Selezione la route per tale `IP_D` confrontandolo con i campi `D` presenti nella tabella (***table lookup***).
	- Si confrontano `IP_D` e l'elemento `D` di ciascuna route usando la **netmask**. 
	- La procedura viene detta "*longest prefix match*".
		- `{c} R = IP_D & N;`
	- Se `{c} R== D;`
		- La *route viene selezionata*, altrimenti si passa al record successivo.
4. Se la route esiste, esegue l'azione di routing suggerita dai campi `G` e `NI`.
	1. Se non esiste ***genera un errore*** (`ICMP` - Destination Unreachable).

>[!hint] Ordinamento
>Le **route** nella tabella sono ordinate in funzione della ***netmask*** decrescente.
>- *Garantisce di considerare in ordine* i singoli host, le reti piccole e grandi.
>
>>[!attention] È possibile implementare eccezioni
>>
##### Ruolo del Gateway
>[!info]
>Il ***Gateway*** è il responsabile della consegna del datagramma.

>Il routing `IP` è basato sull'*appartenenza alla network*.
- Host di network diverse comunicano ***tramite gateway***.

Il **table lookup**, dopo aver scelto la `D`-esima riga:
- La funzione di routing invia il datagram a `NI` con l'obbiettivo di consegnarlo al **gateway**.

>[!hint] Osservazione
>Serve anche per specificare il tipo di instradamento:
>> Diretto
>- Se il gateway è: `IP` locale (*windows*), `0.0.0.0` (*linux*).
>
>> Indiretto
>- Se il gateway è il numero `IP` del router da contattare.

###### Aggregazione
> Non è necessario che un router **conosca il dettaglio** di come le reti sono connesse ad un altro router.

>[!done] È sufficiente una informazione più riassuntiva

> Esempio

![[../attachements/Aggregation.png]]

Le reti:
- `137.204.64.0\24`
- `137.204.65.0\24`
- `137.204.66.0\24`
- `137.204.67.0\24`

Si possono semplificare nel seguente modo:
- `137.204.64.0\22`

Il router `R2` non serve sapere come sono divise.

## Rappresentazione della Rete
---
>[!info]
>Ad una generica [[../Reti IP|rete]] si può facilmente associare un [[../../../Algoritmi e Strutture Dati/Strutture Dati/Grafi/I Grafi#Terminologia|grafo orientato]].

I **nodi** rappresentano i *terminali* e gli **archi** rappresentano i *collegamenti*.
- L'orientamento dell'arco rappresenta la ***direzione di trasmissione***.

> Il ***peso degli archi*** può essere espresso in termini di:
- Numero di nodi attraversati.
- Distanza Geografica.
- Ritardo introdotto.
- Capacità del collegamento.
- Una *combinazione dei precedenti*.