## Introduzione
---
>[!tldr] Idea
>***Kubernetes*** è una architettura software con una struttura client-server che esegue su un [[Docker Swarm|cluster]] (un gruppo di host) in cui dispiega la sua applicazione.

L'interfacciamento dell'amministratore di *kubernetes* avviene tipicamente mediante un client, ad esempio `kubectl`.

### Elementi
> [!help] Nodes
> Gli **host** del cluster vengono detti *nodi*.

È presente un nodo ***master*** che gestisce tutto il cluster.

> [!abstract] Pods
> ***Kubernetes*** organizza maggiormente l'applicazione definendo delle unità, dette ***pods***, composte da uno o più [[Container]] che hanno necessità di lavorare strettamente tra di loro come se fossero tutti in uno *stesso host virtuale*.

I container di uno stesso *pod* sono infatti realizzati per poter:
- Condividere uno stesso indirizzo `IP`.
- Avere lo stesso spazio delle porte di protocollo.
	- Cioé due container appartenenti allo stesso pod non possono attestarsi sulla stessa porta.
- Comunicare tra di loro mediante `localhost`.
- Interagire tra di loro mediante le classiche ***Inter Process Communications*** (Comunicazione tra processi di uno stesso *host*).

> Due container in *pod diversi* per comunicare ***devono specificare l'indirizzo*** `IP` del pod a cui appartiene l'altro container.

>[!done] Repliche
>Ogni pod è contenuto in un solo nodo, ma in un nodo possono essere contenuti più pods, ciascuno dei quali risulterà dotato di un proprio `IP`.


> [!note] Label
> Ciascun pod può essere classificato mediante una ***label***, una stringa dotata di un nome e un valore.

Tutti i pods a cui è stata assegnata una *label* con **stesso nome e valore** possono essere considerati ***equivalenti*** per fornire una funzionalità.


> [!caution] Selectors
> La ricerca di una risorsa può essere effettuata specificando un ***selettore***, specificando come filtro una *label* e il suo valore richiesto.

esempio:
- I pods possono essere filtrati mediante la label `"role=production"`

> [!failure] Deployements
> Un ***deployement*** è un insieme di pod uguali che forniscono un servizio.

Serve quando vengono dispiegate più istanze di uno stesso pod in modo da *creare repliche su cui distribuire il carico di lavoro*.


> [!todo] Services
> I ***services*** sono una struttura di *kubernetes* create per avere un punto di accesso unico ai **servizi di un deployement**.

Il servizio comprende: 
- Il modo per accedere ai *pods*:
	- Indirizzo `IP` del pod o il nome con cui il [[../../Reti/Application Layer/DNS|DNS]] mappa il pod.
- La politica con cui viene effettuato il bilanciamento del carico.
> [!done] Pro
> Chi vuole usufruire di un servizio ***non*** ha bisogno di conoscere **dove si trova il container**, solo il nome del servizio.

> Bilanciamento del carico
- Può essere implementato direttamente da *kubernetes* o può essere usato un **servizio di bilanciamento esterno**.
#### Creazione del Cluster

> [!todo] Operazioni
> Quando si dispiega una applicazione in un cluster, prima si istanziano i singoli **pods**, creando il *deployement*, poi davanti a ciascun gruppo, si  istanzia il ***servizio*** che regola l'accesso ai pod del servizio.

Per fare il deploy di ciascun gruppo di pods e di ciascun servizio si utilizza un [[Docker Compose#File YAML|file]] che descrive le proprietà del pod o del servizio.

### Architettura
> L'architettura di **kubernetes** prevede che i nodi del cluster siano connessi da una rete di overlay.

Tra i nodi del cluster ci deve essere un nodo che svolge il ruolo di master.
- Il master **NON** esegue pods applicativi


> [!help] Lavoro del Master
> Il ***master*** esegue diversi **servizi** necessari per la gestione della rete di nodi.

> `API` server
- Espone le funzioni di gestione del cluster. Le richieste sono inviate da una macchina esterna al cluster, ma interna alla rete.

> *Controller*
- Controlla lo stato del cluster, può fare o richiedere modifiche dove necessario.

> `etcd`
- **Database** che contiene informazioni sullo *stato del cluster* e dei *pods*.
	- Presente in `k8s` ma non in `k3s`.

> *Scheduler*
- È responsabile di decidere in quale nodo dispiegare un nuovo pod.

![[attachements/kubernetesArchitecture.png]]
### Autoscaling
> [!Tip] Info
> L'***autoscaling*** è una tecnica utilizzata nel cloud computing per incrementare e/o ridurre in maniera *dinamica* la **quantità di risorse computazionali** messe a disposizione da una server farm.

*Kubernetes* offre tre strumenti per effettuare autoscaling:

> 1. ***Horizontal Pod Autoscaler***.

L'`HPA` è una risorsa disponibile all'interno di *kubernetes*, è il meccanismo che consente di scalare automaticamente il ***numero di repliche di un pod***, sulla base dell'osservazione di determinate metriche.
- È possibile creare una risorsa `HPA` tramite la definizione di un file `{yaml icon} yaml` o attraverso l'utilizzo del comando:
```sh
kubectl autoscale deployment foo --max=5 --cpu-percent=80
# if the cpu usage goes above 80% increase pods up until 5 max.
```

```yaml
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
 name: php-apache
spec: # what deployment to monitor
 scaleTargetRef:
  apiVersion: apps/v1
  kind: deployment
  name: php-apache
 minReplicas: 1
 maxReplicas: 10
 metrics: # what resource to monitor and the thresholdk
  - type: Resource
    resource:
     name: cpu
     target:
      type: Utilization
      averageUtilization: 50
```

> 2. ***Vertical Pod Autoscaler***.

Il `VPA` è il meccanismo che consente di incrementare le risorse (`CPU` e *memoria*) richieste da un pod al nodo su cui risiede.
- Di utilizzo *poco comune*.

> 3. ***Cluster Autoscaler***.

Il **cluster autoscaler** è il meccanismo che consente di aumentare o diminuire il *numero di nodi di un cluster* su cui eseguire i pods.
Ostacoli:
- Accensione remota di un dispositivo fisico (risolvibile tramite *Wake on Lan* o *Proxmox*).
- `MAAS`-Metal As A Service, estensione del [[../../Reti/Application Layer/DHCP|DHCP]], si finge un server `DHCP` e invia, oltre alla configurazione `DHCP`, ordini in modo tale che venga installato un sistema operativo specifico (L'immagine risiede nel server `MAAS`).