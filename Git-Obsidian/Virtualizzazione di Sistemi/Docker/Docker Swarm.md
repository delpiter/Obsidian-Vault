## Stack e Tsak
---
>[!tldr] Idea
>Uno ***swarm*** è composto da uno o più nodi (*macchine*). Uno dei nodi assume il ruolo di manager, mentre gli altri.

Il **manager** copre anche il ruolo di *worker*, solitamente viene tenuto "scarico" per permettere di gestire il cluster.

Uno **swarm** è in grado di eseguire uno *stack*

>[!abstract] Stack
> Uno ***stack*** è un gruppo di [[Docker Compose#Sintassi|servizio]].
> Ogni servizio è descritto attraverso un file [[Docker Compose]].

Un servizio può essere distribuito su più nodi worker del cluster, creando più istanze su ogni nodo worker.
- Ogni istanza di un container con un servizio è chiamata ***task***.

Ogni task di un servizio è una *replica del servizio stesso*, ogni worker può eseguire più repliche di uno o più servizi.

![[attachements/DockerSwarmStack.png]]

Uno stack, quindi non è altro che un insieme di **task** raggruppati in servizi, eseguiti su un cluster di *nodi worker* e coordinati da un *nodo manager*.
- Il manager **coordina** i nodi worker e **distribuisce** le task agli stessi.
- Il manager ha il compito di ricevere le richieste dei clienti e ridistribuirle ai servizi istanziati sui nodi worker.


>[!caution] Assunzioni di rete
>Il `{sh icon} docker swarm` manager utilizza le `iptables` per *inoltrare le connessioni* dei clienti alla replica selezionata.
>I messaggi di **swarm** tra il manager e i nodi worker utilizzano le porte [[../../Reti/Transport Layer/TCP|TCP]] $2376$ e $2377$.
>Si assume che i nodi sono connessi attraverso una rete.

## Operazioni
---
> Ogni operazione disponibile per *docker swarm* è rivolto o al nodo manager o a un nodo worker.

>[!info] Init

> **Master**

Inizializza il nodo corrente come nodo manager, richiede come parametro uno degli [[../../Reti/Network Layer/Protocollo IP|indirizzi ip]] del nodo manager.
- Questo indirizzo sarà quello raggiungibile dai nodi worker.

```sh
docker swarm init --advertise-addr 10.133.7.101
```

>[!help] Create

> **Master**

Crea un servizio partendo da una immagine e espone una porta del container sull'host.

```sh
docker service create --name myRegistry --publish published=5000,target=5000 registry:2
```

>[!summary] List

> Master-Worker

Elenca i servizi disponibili

```sh
docker service ls
```

>[!abstract] Deploy

Dispiega una applicazione partendo da un **compose file**.

```sh
docker stack deploy --compose-file docker-compose.yml myStack
```

>[!failure] Join

> Worker

Il nodo worker richiede al nodo manager di entrare nel cluster specificato.
- Richiede una chiave di sicurezza generata dal manager con il comando `docker swarm init` e l'`IP` del nodo manager.

```sh
docker swarm join --token SWMTKN-1-uuid 10.133.7.101
```

Altri comandi si possono trovare [qui](https://docs.docker.com/engine/swarm/)
