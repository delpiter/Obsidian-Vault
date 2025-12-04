## Routing Gerarchico
---
>[!cite] Autonomous System
>Un ***autonomous system*** è un insieme di router gestiti da un'unica amministrazione che usa un solo protocollo i routing e una logica per definire le metriche.
>
>>[!definizione] Definizione Moderna [RFC 1930](https://www.rfc-editor.org/rfc/rfc1930.html)
>>Un `AS` è un insieme di [[Protocollo IP#Semantica dell'Indirizzo|prefissi di rete]] `IP`, definite secondo la logica [[Reti IP#CIDR|CIDR]].
>> - Un `AS` può avere uno o più enti gestori che utilizzano una o più tecnologie.

È una area di [[Routing]] in un sistema di *routing gerarchico*.
- L'***Internet Routing Registries*** è un database con le politiche di routing degli `AS`.

Un `AS` può essere ulteriormente diviso in porzioni dette ***routing area*** (`RA`) interconnesse da una **backbone**.

Gli `AS` decidono autonomamente i ***protocolli*** e le ***politiche di routing*** che adottano all'interno.
- I protocolli interni ad un `AS` sono detti "***I***nterior ***G***ateway ***P***rotocol" (`IGP`).
- I protocolli esterni ad un `AS` sono detti "***E***xterior ***G***ateway ***P***rotocol" (`EGP`).

Gli `AS` non sono vincolati ad aree geografiche.
- ***Internet Region***: Porzione di internet contenuta in una area geografica.
	- Una *internet region* può essere servita da più [[Enti Importanti#Internet Service Provider|ISP]] un `ISP` può servire più `IR`.

>[!tldr] Concetto
>I ***routing gerarchico*** è l'identificazione di sottoinsiemi di rete *autonomi per l'instradamento* e di *punti di contatto fra sotto sistemi*.
### Routing a  livello Globale
> Tipologie di [[I Grafi|grafo]]:

- [[Topologie di Rete|Topologia]] dei sottoinsiemi della rete (*grafi di dettaglio*).
- Topologie dei sottoinsiemi interconnessi (*grafo semplificato*).
>[!hint] A ciascun livello non si ha conoscenza dell'altro

### Protocolli di Routing
>[!abstract] Un `AS` deve implementare il routing al suo interno usando uno o più `IGP`.
- RIP e OSPF

>[!caution] Un `AS` deve comunicare con gli altri `AS` per implementare routing fra `AS`
- Attraverso un protocollo `EGP`.
- BGP.

