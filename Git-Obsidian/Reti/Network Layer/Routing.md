> Esistono più percorsi per raggiungere una destinazione da una sorgente

>[!todo] Internet
> Internet è una "***rete di reti***", il cui componente elementare è la ***network*** [[Protocollo IP|IP]].

Le ***network*** `IP` sono interconnesse da apparati che svolgono la funzione di "***ponte***".
- *Router* o *Gateway*.
- I calcolatori in una **network** `IP` sono connessi dalla medesima **infrastruttura di rete fisica** ([[ISO-OSI#TCP-IP|Livelli]] 1 e 2).

Ogni network `IP` può essere implementata con una **tecnologia specifica**.
- `Wi-Fi`, `ADSL`, Ethernet, etc... #addLink 

>[!important] Ipotesi Fondamentale
>Tutti gli host appartenenti alla medesima **network** `IP` sono in grado di parlare tra loro grazie alla tecnologia con cui essa viene implementata.


## Rete Logica e Fisica
---
>[!tldr] Rete Logica
>La ***rete Logica*** è la **network** `IP` a cui un `host` appartiene logicamente.

>[!caution] Rete Fisica
>La ***rete Fisica*** è la rete (es LAN #addLink) a cui un `host` è *effettivamente connesso*.

L'[[ISO-OSI|architettura a strati]] nasconde gli indirizzi fisici e consente alle applicazioni di lavorare solo con [[Protocollo IP#L'indirizzo IP|indirizzi IP]].

## Interconnesione
---
>[!help] Interconnettere le network `IP`
>Per far parlare tra di loro le "*isole*" è necessario che vi siano dei *collegamenti* fra le **isole**, degli *apparati* che permettono di usare i collegamenti.
>Deve inoltre essere possibile scegliere il giusto collegamento verso la **network** `IP` destinataria.

### Router
>[!definizione]
>Il ***router*** è un dispositivo elettronico che connette due o più network `IP` inoltrando informazioni.
>- Ha funzioni dal livello $1$ al livello $3$ [[ISO-OSI|OSI]].

Il singolo calcolatore terminale sceglie un router come *gateway* verso le altre ***network*** `IP`, instrada il datagram verso il router.

Il *router* ha il compito di decidere **in che direzione** inviare il datagram.
- Instradamento (*routing*).
- Il singolo salto viene detto `hop`.