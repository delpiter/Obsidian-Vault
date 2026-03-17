## Container Networking
---
>[!caution] Container Networking
>Con il termine ***container*** [[Reti IP|networking]], si riferisce all'abilità di un container di connettersi e comunicare con altri [[Container]] e altri servizi **non-docker**.

I container hanno il *networking* abilitato di default, e sono in grado di creare connessioni all'esterno.
- Un container ***non ha conoscenza*** su che tipo di rete è connesso o se i suoi [[Comunicazione#Peer to Peer|peer]] sono altri container, vede solo un'interfaccia con un [[Protocollo IP|indirizzo IP]], un **gateway**, una [[Routing#Tabella di Routing IP|routing table]] e altri dettagli della rete.

### User-defined networks
> Può essere utile separare gruppi di container che dovrebbero avere completo accesso tra di loro, ma accesso ristretto ad altri gruppi.

>[!todo] User Networks
>Si possono creare delle ***reti personalizzate***, e connettere *gruppi di container* alla stessa rete.

Una volta connessi ad una rete user-defined, i container possono comunicare con gli altri usando ***indirizzi*** `IP` o ***nomi dei container***.
### Drivers
> Il sottosistema di rete di docker è collegabile, utilizzando i **driver**.

Esistono diversi *driver di default* che forniscono funzionalità di rete di base.

| Driver       | Description                                                         |
| :----------- | :------------------------------------------------------------------ |
| [[#Bridge]]  | The default network driver.                                         |
| [[#Host]]    | Remove network isolation between the container and the Docker host. |
| None         | Completely isolate a container from the host and other containers.  |
| [[#Overlay]] | Swarm Overlay networks connect multiple Docker daemons together.    |
| [[#IPVlan]]  | Connect containers to external VLANs.                               |
| [[#MACVlan]] | Containers appear as devices on the host's network.                 |
Il tipo di rete che un container utilizza è indifferente dal punto di vista del container.
- Il container vede: [[Protocollo IP|indirizzo IP]], un **gateway**, una [[Routing#Tabella di Routing IP|routing table]], i servizi [[DNS]] e altri servizi.

#### Bridge
> Quando docker engine inizia per la prima volta ha una singola rete chiamata "***default bridge***".

>[!definizione]
>In termini di docker, una ***rete bridge*** utilizza un bridge software, che permette ai container connessi alla *stessa rete bridge* di comunicare, garantendo un'isolazione dai container che **non** appartengono alla stessa rete bridge.

Il container viene connesso al *default bridge* in automatico quando viene eseguito un container senza l'opzione `--network`
- Container connessi al **default bridge** hanno accesso ai servizi di rete al di fuori dell'host.
- Solitamente usate quando le applicazioni vengono eseguite in container stand-alone che necessitano di una comunicazione tra di loro.

Permettono la **connessione a servizi esterni**.

>[!info]
>Ogni container connesso ad un ***bridge*** è connesso ad una **sottorete** `IPv4`.

> Di default:
- Permette accesso senza restrizioni ai container connessi nella rete dell'host e da altri container connessi allo stesso **bridge**.
- Blocca l'accesso da altri container in reti al di fuori della rete host.
	- Per abilitarlo, è necessario: configurare il kernel per permettere `IP` forwarding e cambiare le policy delle tabelle `IP FORWARD` da `DROP` a `ACCEPT`.
- Supporta la pubblicazione di porte dove il traffico è inoltrato tra i container.

>[!warning]
>Il default bridge è considerato un dettaglio ***legacy*** di *docker*, è consigliato utilizzare una **user-defined network** per utilizzo in [[Il Ciclo di Vita del Software#Attività|esercizio]]. 
#### Host
>[!info]
>***Rimuove l'isolazione*** di rete tra il container e l'host docker, il container utilizzerà direttamente la rete dell'host.

#### Overlay
>[!info]
>Gli ***overlay network*** connettono diversi [[Docker#Architettura|Docker daemon]] insieme e abilitano servizi di gruppo per comunicare con gli uni gli altri.

Questa strategia rimuove la necessità di fare ***routing*** a livello del [[3 - Livelli del Sistema Operativo#Introduzione|sistema operativo]] tra i container.

#### MacVlan
>[!info]
>Le ***macVlan*** permettono di assegnare indirizzi [[Struttura del Data Link#Medium Access Control|MAC]] al container, rendendolo un dispositivo fisico nella rete.

Il ***docker daemon*** indirizza il traffico ai container attraverso gli indirizzi `MAC`.
- I driver ***macVlan*** è la miglior scelta quando si parla di applicazioni legacy che si aspettano di essere connessi direttamente alla rete fisica.

### Porte Pubblicate
>[!help]
>Di default un container **non** ha nessuna porta aperta al mondo esterno, per aprirla si deve usare il comando `--publish` o `-p`, con la seguente sintassi:
>- `{sh} -p hostPort:containerPort`

- Questo crea una regola del [[Firewall]] che ***mappa*** una porta del container a una porta dell'host docker.

| Flag Value                            | Description                                                                                                                                               |
| ------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `{sh} -p 8080:80`                     | Map a [[TCP]] port `80` in the container to the port `8080` in the host                                                                                   |
| `{sh} -p 192.168.10.100:8080:80`      | Map a `TCP` port `80` in the container to port `8080` on the docker host for connections to `IP` `192.168.10.100` of the host.                            |
| `{sh} -p 8080:80/tcp -p 8080:80/udp ` | Maps a `TCP` port `80` in the container to `TCP` port `8080` in the host and map an `UDP` port `80` in the container to the `UDP` port `8080` in the host |

Per vedere tutte le porte definite in un container, esegui il comando:  `{docker icon} docker port containerID`.

### Impostare un indirizzo IP
> Di default, al container è assegnato un indirizzo `IP` per ogni rete docker a cui si connette.

L'indirizzo è assegnato da una ***pool di indirizzi*** assegnata alla rete.

>[!note] DHCP
> Il ***docker daemon*** agisce come un server [[DHCP]] per ogni container.
> Ogni rete ha una **subnet mask** e un **gateway** di default.

Quando un container viene inizializzato può essere connesso ad una singola rete usando il flag `--network`.
> Si può:
- Specificare l'indirizzo `IP` assegnato usando i flag `--ip` o `--ip6`
- Specificare l'hostname del container tramite il flag `--hostname`.

>[!done] Aggiunta di altre reti

Per potere aggiungere collegamenti di rete a *container in esecuzione*, si deve usare il comando `docker network connect`.
### DNS
> Di default il container eredita la **configurazione** [[DNS]] dell'host.

>[!help] Docker DNS
>Il ***DNS embedded*** di docker, oltre a mappare i nomi dei container agli indirizzi `IP`, mappa anche l'indirizzo `IP` del container con il servizio #addLink che il container implementa.

Si possono sovrascrivere queste opzioni di base quando si ***creano i container***.
