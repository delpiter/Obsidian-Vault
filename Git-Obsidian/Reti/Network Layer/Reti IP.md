#reti_2
## Classe delle Reti
---
> Definite diverse *classi di network* differenziate per dimensione.

>[!info] Classe A
> Gli indirizzi di ***classe*** `A` hanno il primo `bit` uguale a $0$.

Intervallo di Indirizzi:
- Da `0.0.0.0` a `127.255.255.255`

>[!help] Classe B
> Gli indirizzi di ***classe*** `B` hanno i primi `bit` uguali a $10$.

Intervallo di Indirizzi:
- Da `128.0.0.0` a `191.255.255.255`

>[!summary] Classe C
> Gli indirizzi di ***classe*** `C` hanno i primi `bit` uguali a $110$.

Intervallo di Indirizzi:
- Da `192.0.0.0` a `223.255.255.255`

>[!caution] Classe D
> Gli indirizzi di ***classe*** `D` (o *multicast*) hanno i primi `bit` uguali a $1110$.

Intervallo di Indirizzi:
- Da `224.0.0.0` a `239.255.255.255`

>[!tldr] Classe E
> Gli indirizzi di ***classe*** `D` (*sperimentale*) hanno i primi `bit` uguali a $1111$

Intervallo di Indirizzi:
- Da `240.0.0.0` a `255.255.255.254`

La definizione delle classi è **standard**, quindi nota a tutti.
- I **router** riconoscono la classe di una rete dai primi `bit` dell'indirizzo, ricavando di conseguenza il ***net-ID***.

![[NetworkClasses.jpg]]

### Indirizzi Riservati
>[!abstract] [RFC 1700](https://www.rfc-editor.org/rfc/rfc1700.html)
> Ci sono una serie di ***indirizzi riservati***. 

> `0.0.0.0`
- Indica l'host corrente senza specificarne l'indirizzo.

> ***Host-ID*** tutto a $0$
- Viene usato per indicare la rete.

> ***Host-ID*** tutto a $1$
- È l'indirizzo di ***broadcast*** per quella rete.

> `0.x.y.z`
- Indica un certo **Host-ID** sulla rete corrente senza specificare il **Net-ID**.

> `255.255.255.255`
- È l'***indirizzo di broadcast*** su internet.

> `127.x.y.z`
- È l'indirizzo di ***loopback*** che **redirige** i datagram agli strati superiori dell'*host corrente*.

### CIDR
>[!info] [RFC 1519](https://www.rfc-editor.org/rfc/rfc1519.html)
> Il ***Classes Inter Domain Routing*** è un meccanismo per estendere il concetto di subnetting all'intera rete internet.

Le reti `IP` vengono definite tramite la coppia **net-ID**/**netmask**.

>[!hint] Obbiettivi
- Allocazione di reti `IP` di ***dimensioni variabili*** (uso più efficiente dello spazio di indirizzi).
- Accorpamento delle informazioni di routing.

#### Supernetting
>[!missing] Info
>Il supernetting consiste nel [[Routing#Aggregazione|raggruppare]] più reti con indirizzi consecutivi.

Nelle [[Routing#Tabella di Routing IP|tabelle di routing]] vengono indicate con una sola entry con l'opportuna netmask.

> Esempio: una rete con circa $2000$ indirizzi

Una rete di classe `B` è troppo grande.
- Uso $8$ reti di classe `C` ($8\times 256 = 2048$).
- dalla `194.24.0.0` alla `194.24.7.0`
Si accorpano le $8$ reti contigue in un'unica super-rete
- ID: `194.24.0.0\21`
- Subnet Mask: `255.255.248.0`

>[!info] Subnetting e Supernetting
>***Subnetting e Supernetting*** sono operazioni duali.
>- Subnetting $n$ `bit` del'*Host-ID* diventano parte del *Net-ID*.
>- Supernetting $n$ `bit` del'*Net-ID* diventano parte del *Host-ID*.
## Broadcast
---
>[!cite] Definizione
>La ***comunicazione broadcast*** è un metodo per l'invio di messaggi da una sorgente a tutte le destinazioni in una *network* **senza conoscere i singoli indirizzi**.

Si definisce ***indirizzo di broadcast*** l'indirizzo che ha l'[[Protocollo IP#Semantica dell'Indirizzo|Host-ID]] composto da soli $1$.

> Esempio: `137.204.191.0/26`
- Broadcast: `137.204.191.63`

## Multicast
---
>[!summary] Definizione
>La ***comunicazione multicast*** è un metodo per l'invio di messaggi da *una sorgente* a *multiple destinazioni* (non necessariamente tutte).

Si definiscono gli ***indirizzi multicast***:
- da `224.0.0.0` a `239.255.255.255`.

I router possono usare diversi protocolli per l'utilizzo del multicast, come:
- [[Routing Globale#Interior Gateway Protocol|RIP_v2]].
- [[Open Shortest Path First|OSPF]].

### Internet Group Management Protocol
> L'`IGMP` serve per dichiarare l'appartenenza ad un ***gruppo di multicast***.

Prevede messaggi per *iscriversi*, *abbandonare* e *valutare l'appartenenza* ad un **gruppo**.
## Reti IP Private
---
>[!hint] Info
>Alcuni gruppi di [[Protocollo IP|indirizzi]] sono riservati a reti `IP` *private*.
>- **Non sono raggiungibili** dalla rete pubblica.

I [[Routing#Router|router]] **non** instradano datagram destinati a tali indirizzi.

Gli indirizzi privati possono essere ***riutilizzati in reti isolate***.

### Indirizzi IP Privati
>[!example] [RFC 1918](https://www.rfc-editor.org/rfc/rfc1918.html) e [RFC 4193](https://www.rfc-editor.org/rfc/rfc4193.html)
> Sono `RFC` rispettivamente per `IPv4` e `IPv6` che definiscono degli intervalli di indirizzi `IP` destinati a reti `IP` usate da enti per finalità interne e quindi ***non connesse alla rete globale***.

> `IPv4`
- Da `10.0.0.0` a `10.255.255.255` (`10.0.0.0/8`)
- Da `172.16.0.0` a `172.31.255.255` (`172.16.0.0/12`)
- Da `192.168.0.0` a `192.168.255.255` (`192.168.0.0/16`)

Poiché gli indirizzi privati non hanno significato globale, le informazioni di routing circa le reti private ***non vengono propagate***.
### Relazione Indirizzi Fisici e Indirizzi IP
>[!info]
>Gli **host** comunicano attraverso una ***rete fisica*** (es. LAN #addLink) quindi devono conoscere reciprocamente gli indirizzi fisici #addLink.

>[!question] Come ricavo l'indirizzo fisico conoscendo solo l'`IP`

#### Protocollo ARP
>[!cite] Address Resolution Protocol
>`ARP` [RFC 826](https://www.rfc-editor.org/rfc/rfc826.html) è un protocollo che serve a mappare gli indirizzi `IP` agli indirizzi fisici.

##### Funzionamento
1. Il nodo sorgente invia un [[Controllo del Canale#Canale di Comunicazione|frame]] in **broadcast** (`ARP Request`) contenente l'indirizzo `IP` del nodo destinazione.
2. Tutte le stazioni della rete leggono il frame.
3. Il destinatario risponde al mittente inviando un messaggio che contiene il proprio indirizzo fisico (`ARP Reply`).
4. L'host si salva in una tabella `cache ARP` le corrispondenze tra indirizzi logici e fisici.

> `{sh icon} arp -a`
- Comando per visualizzare il contenuto della `cache ARP`.

## Le Sottoreti
---
>[!todo] Info
> A un'amministrazione è assegnata una network.
> L'amministrazione potrebbe essere suddivisa in ***sotto-amministrazioni logicamente separate***.

Si può avere una ***sotto-ripartizione locale*** net/host ID *indipendente dalle classi*.

>[!hint] Si frammenta l'***host-ID*** in due parti
- La prima identifica la **sottorete**.
- La seconda identifica i singoli host della **sottorete**.

La ripartizione deve essere ***locale e reversibile***.
