## Reti IP Private
---
>[!info]
>Alcuni gruppi di [[Protocollo IP|indirizzi]] sono riservati a reti `IP` *private*.
>- **Non sono raggiungibili** dalla rete pubblica.

I [[Routing#Router|router]] **non** instradano datagram destinati a tali indirizzi.

Gli indirizzi privati possono essere ***riutilizzati in reti isolate***.

## Reti IP Pubbliche
---

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
>[!abstract] `[RFC 1700]`
> Ci sono una serie di ***indirizzi riservati***. 

> `0.0.0.0`
- Indica l'host corrente senza specificarne l'indirizzo.

> ***Host-ID*** tutto a $0$
- Viene usato per indicare la rete.

> ***Host-ID*** tutto a $1$
- È l'indirizzo di broadcast #addLink per quella rete.

> `0.x.y.z`
- Indica un certo **Host-ID** sulla rete corrente senza specificare il **Net-ID**.

> `255.255.255.255`
- È l'***indirizzo di broadcast*** su internet.

> `127.x.y.z`
- È l'indirizzo di ***loopback*** che **redirige** i datagram agli strati superiori dell'*host corrente*.