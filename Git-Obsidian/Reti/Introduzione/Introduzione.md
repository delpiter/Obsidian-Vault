## Comunicazione
---
>[!tl;dr] Etimologia
>Dal latino "***cum-munis***"
>- *Insieme*
>- *Compito*
>
>>[!question] Significato Odierno?
>>Condivisione e ***scambio di informazione***

>[!abstract] Telecomunicazione
>Tele ($T \mathcal{E} \lambda\mathcal{E}$), dal greco antico: ***Lontano***
>>[!done] Telecomunicazione
>>Comunicare Lontano

>La telecomunicazione pone un problema:
- Il problema di ***trasportare l'informazione*** nello spazio

## Definizioni di Base
---
### Rete
>[!definizione] Definizione
>Una ***rete*** è un sistema che connette due o più utenti per *condividere informazioni*

#### Componenti della Rete
>[!hint] Terminale
>I ***terminali*** fungono da *interfaccia* con l'**utente finale**

>[!caution] Collegamenti
>I ***collegamenti*** permettono il **trasferimento** di uno o più *flussi di informazione* fra punti remoti nello spazio
>È il *componente fisico* della trasmissione.

>I collegamenti sono realizzati con ***opportuni mezzi trasmissivi***
- ***Spazio libero*** (vuoto/aria)
- Cavi realizzati con ***materiali conduttori***
- ***Fibre ottiche*** in vetro

>[!todo] Nodi di Commutazione
>Sono gli *elementi cruciali* della rete.
>Utilizzano i ***mezzi trasmissivi*** al fine di creare *canali di comunicazione* sulla base dele richieste degli utenti
### Canale
>[!info] Definizione
>Il ***canale*** è l'entità logica o fisica che permette il *trasporto* dei **singoli flussi informativi** fra punti remoti nello spazio

Le telecomunicazioni utilizzano ***canali di comunicazione***

>Tipicamente un ***collegamento*** può essere usato per implementare più **canali**
#### Tipologie
>[!abstract] Monodirezionale
>L'informazione può essere trasferita in ***una sola direzione***

>[!summary] Bidirezionale
>L'informazione può essere trasferita in ***entrambe le direzioni***

>[!caution] Punto a Punto
>Un nodo è collegato con un singolo nodo

>[!todo] Punto Multipunto
>Un nodo può comunicare con tanti altri nodi
> #addLink ***Broadcast***
> - Un nodo trasmette allo stesso tempo a ***tutti i nodi della rete***
>
> #addLink ***Multicast***
> - Un nodo trasmette allo stesso tempo ad un ***sottoinsieme dei nodi***

## Rete di Accesso
---
>[!abstract] Definizione
>La ***rete di accesso*** è la parte della rete che collega l'*utente finale* (come un'azienda) alla rete di comunicazione più ampia

Le *reti di accesso* si trovano tra il **punto di distribuzione centrale** e l'**utente finale**

## Rete di Transito
---
>[!caution] Definizione
>La ***rete di transito*** è la parte di rete che gestisce il *traffico di dati* da una **zona geografica all'altra**.
>Solitamente più **robuste** e di **maggiore capacità** rispetto alle *reti di accesso*

È una rete che permette ai dati di ***viaggiare tra punti di accesso*** a livello globale o nazionale.

>Le reti di transito *includono*:

- Le ***grandi dorsali*** in fibra che attraversano i continenti
- Reti di telecomunicazione ***intercontinentale***
- Reti di ***backbone*** che gestiscono il traffico tra diversi *provider di servizi*

## Sistemi Aperti
---
>[!tl;dr] Obbiettivo
>L'*obbiettivo* dei ***sistemi aperti*** è quello di realizzare una rete di calcolatori in cui **qualunque** terminale comunica con **qualunque** fornitore di servizi mediante **qualunque** rete.

Per realizzare un *sistema aperto* è necessario stabilire delle regole comuni
- Stabilire degli ***standard*** ([[ISO-OSI]])

Tutte le proposte hanno in comune un'***architettura a strati***