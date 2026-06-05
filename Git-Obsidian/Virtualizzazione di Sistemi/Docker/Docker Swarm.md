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
- Questa operazione si può fare anche attraverso l'aggiunta di un servizio all'interno di un file `{yaml icon} .yaml`

```sh
docker service create --name myRegistry --publish published=5000,target=5000 registry:2
```

In particolare questo comando viene usato per creare il ***servizio di repository*** per mantenere tutte le *immagini nel nodo manager*.

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

## YAML per docker swarm
---
> È possibile creare un cluster (*swarm*) di container utilizzando il file formato [[Docker Compose#File YAML|YAML]].

>[!todo] Passaggi
>1. Instaurare il nodo manager e creare il servizio di repository.
>2. Creare i nodi worker e fare il deploy dei servizi.

Quando si utilizza ***docker swarm*** si possono dare informazioni aggiuntive riguardo il deploy del servizio, attraverso la chiave `deploy`, in questo campo si può specificare:
- quanti repliche inizializzare (`replicas: 4`)
- dove istanziare i container (`placement`)
	- `constraints` lista di regole (`"node.role == manager"`).

>[!example] Esempio

```yaml
services:
 myregistry:
 image: registry:2
 ports:
  - 5000:5000
 volumes:
 # Maps the named volume to the registry folder
  - registry_data:/var/lib/registry
 deploy:
  replicas: 1
  placement:
   constraints:
    - "node.role == manager"
volumes:
	registry_data: "..."
```

```yaml
services:
 nodejsapp:
  build:
   context: ./nodejs
   dockerfile: Dockerfile
   args:
    - IMAGE_VERSION=not_needed
  image: 10.133.7.101:5000/nodejsapp
  #take the image from the repository service in the manager node
  deploy:
   replicas: 1
   placement:
   constraints:
    - "node.role == manager"
   # I try up to 3 times to restart the service
   restart_policy:
    condition: on-failure # Can be: on-failure, any, or none
    delay: 5s # Wait before attempting restart
    max_attempts: 3 # Max number of attempts (optional)
    window: 120s # Time to check if restart works
  # The web server activates port 3000 only after it has connected to the db.
  # So I check by trying to connect on port 3000
  # and on the specific path /health.
  healthcheck:
   test: ["CMD", "curl", "-f", "http://localhost:3000/health"]
   # I request / or a dedicated endpoint like /health
   interval: 5s # Check every 5 seconds
   timeout: 3s # If it doesn't respond within 3 seconds, the individual test fails
   retries: 12 # Try 12 times (5s*12=60 sec of startup tolerance)
   start_period: 10s # Give the app 10 sec before starting the test
  # On container startup, nodejs tries to connect to mongodb,
  # if it fails it terminates and the task will be restarted
  command: ["nodejs", "index.js"]
  # restart: always # no longer valid in docker swarm,
  # use the equivalent under deploy: instead
  depends_on:
   - mongodb
  # condition: service_healthy # NOT USABLE in docker swarm
  # condition: service_started
  environment:
   # NOT USED, added only as an example
   - CONTAINER_FULL_PREFIX=container
  ports:
   - target: 3000 # The port inside the container
   - published: 3000 # The port outside on the host server
   - protocol: tcp
   - mode: host # <--- not using ingress mode,
  # no routing mesh for this service
  networks:
   - esterna
   - interna
  volumes:
   - nfs_shared_volume:/var/shared
 # the service that must start first
 mongodb:
  build:
   context: ./mongodb
   dockerfile: Dockerfile
   args:
    - IMAGE_VERSION=non_serve
  image: 10.133.7.101:5000/mymongo
  deploy:
   replicas: 1
# ...
```

>[!warning] Attenzione
>In ***docker swarm***, non è possibile utilizzare la proprietà `condition` dentro `depends_on`, poiché il controllo potrebbe essere riferito ad un *servizio in esecuzione in un altro nodo*. 

```yml
depends_on:
   - mongodb
    condition: service_healthy # NOT USABLE in docker swarm
```

#### Pubblicazione delle porte
> È possibile far si che tutti i nodi possano ricevere richieste per un servizio direttamente dall'esterno.

>[!abstract] Port Mode
>Esistono due opzioni:
>- `{yaml icon} ports: mode: ingress` espone la porta di un servizio su tutti i nodi.
>- `{yaml icon} ports: mode: host`, pubblica la porta solo sul nodo in cui il servizio è implementato (no *routing mesh*).

Questo espone la porta di un servizio su ***tutti i nodi***, anche quelli che non implementano il servizio.

Questa opzione attiva un meccanismo, detto ***routing mesh***:
- Quando un nodo riceve una richiesta su una porta pubblicata per un servizio, ***inoltra la richiesta*** ad un nodo che *implementa il servizio*.

>[!missing] Inefficienza
>Il *routing mesh* causa una notevole latenza, poiché una risposta ad una richiesta che è stata inoltrata ad un nodo ***deve ripercorrere la stessa route all'indietro***.

