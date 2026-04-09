## Virtualizzazione
---
>[!definizione]
>In informatica il termine ***virtualizzazione*** si riferisce alla possibilità di astrarre le componenti hardware degli elaboratori al fine di renderle disponibili al software **in forma di risorsa virtuale**.
>>[!todo] In pratica.
>La ***virtualizzazione*** è una tecnologia in cui si esegue un [[../Sistemi Operativi/Teoria/3 - Livelli del Sistema Operativo|sistema operativo]] ospitato isolandolo all'interno di una macchina ***che non è fisica*** ottenuta da uno strato software (*Virtual Machine Monitor* o *Hypervisor*).

Si possono virtualizzare applicazioni, server, storage, reti, etc...

>Tramite ***virtualizzazione*** è possibile eseguire uno o più [[../Sistemi Operativi/Teoria/3 - Livelli del Sistema Operativo#^9f2787|sistemi operativi]] su un ***unico dispositivo***.
- Ciò avviene in un ambiente *protetto* e *monitorato* che prende il nome di **macchina virtuale**.

Il ***sistema host*** è la macchina fisica su cui gira il sistema il sistema operativo.

La macchina virtuale è chiamata ***ospite*** (***guest***).

### Hypervisor
>[!hint] Definizione
>Un ***Hypervisor*** è un software che gestisce e mantiene le macchine virtuali all'interno di una macchina fisica.

> Tipologie
- Tipo 1 o ***Bare Metal***.
	- Si definisce virtualizzazione di tipo 1 una virtualizzazione nel quale il sistema *host* è assente e le sue funzioni ***vengono sostituite dall'hypervisor***.
- Tipo 2 o ***hosted***.
	- Si definisce virtualizzazione di tipo 2 una virtualizzazione nel quale l'hypervisor è un ***normale processo utente sul sistema operativo host***.
### Virtualizzazione Desktop e Server
>[!abstract] Desktop
>Consente di usare una ***virtual machine*** che esegue sul `PC` dell'utente.
>- Permette di eseguire altri sistemi operativi *sopra il sistema host*.

Realizzata tramite particolari software.

> Principali Software:
- ***VirtualBox*** (Multipiattaforma).
- ***Quemu*** (Linux).
- ***Vmware*** (Windows, MacOsX).
- ***UTM*** (MacOsX).
- ***Parallel*** (MacOsX).

>[!help] Server
>Esegue su Hardware in sale macchine, l'utente **opera** sulla macchina virtuale *da remoto*.

Realizzato mediante l'uso di sistemi operativi dedicati, permette di eseguire altri sistemi operativi ***direttamente sull'hardware***.
- Usata per virtualizzare servizi e server di organizzazioni di dimensioni diverse.

> Principali software:
- ***Proxmox***.
- ***Hyper-V***.
### Emulazione
>[!info] Emulazione
> Nell'***emulazione*** l'hardware viene completamente emulato dal programma di controllo.
> Ogni istruzione che il sistema *guest* esegue, viene tradotta in una sequenza di istruzioni della macchina ***host***.
>>[!warning] Performance
>>Il processo di emulazione risulta *più lento* rispetto alla ***virtualizzazione***.

> ***Differenze***

Il codice della ***macchina virtuale*** viene eseguito direttamente dall'***host***
- Il ***guest*** pensa di essere eseguito da una macchina *reale*.
- Il *codice* della ***macchina virtuale***, perciò deve essere codice macchina *eseguibile dalla macchina hardware reale* sottostante.

>[!done] In Breve
>>[!abstract] Virtualizzazione
>>`CPU` virtuale *compatibile* con la `CPU` fisica.
>
>>[!summary] Emulazione
>>Permette di usare un processore *virtuale* che ***non*** è compatibile con quello *reale*.

>[!danger] Prestazioni
>In un sistema emulato, senza accelerazione, le prestazioni calano fino a solo il $5-10\%$
### Tassionomia di Virtualizzazione
> Diverse possibilità di ***virtualizzazione***, basate su due macro categorie.

![[attachements/Virtualization.png]]

>[!caution] Hardware Level
>Nel caso delle ***macchine virtuali***, all'utente del *sistema di virtualizzazione* viene presentata un'interfaccia su cui installare un *sistema operativo*.
>>[!fail] Contro
>>Molto lenta l'esecuzione di un'istruzione
>>- Deve passare numerosi "*step*" prima di essere eseguita dall'hardware reale.

>[!tldr] OS Level
>Nel caso dei [[Docker/Container|Container]] all'utente viene presentata una partizione del *sistema operativo corrente*, su cui installare ed eseguire applicazioni che *rimangono isolate* nella partizione
>>[!info] Specifiche
>>Il singolo container ***non ha un kernel*** proprio
>>- Questo rende il container più veloce di una *macchina virtuale*
>>- Si appoggia a quello della macchina ***host***
>

Ha un basso overhead per il context-switch.

![[attachements/TypesOfVirtualizzation.png]]

#### Full e Para Virtualization
> La virtualizzazione hardware fornisce una interfaccia, su cui installare un sistema operativo, questo può essere distinto in ***Para virtualization*** e ***Full virtualization***.

>[!info] Para-Virtualization
>Nella ***Para-Virtualization*** la macchina virtuale presenta un'*interfaccia differente* confrontata con una macchina fisica.

Questo comporta di dover modificare il sistema operativo guest per consentire l'esecuzione all'interno all'interno della macchina virtuale stessa.
- L'hypervisor espone un insieme di `API` che il sistema guest dovrà usare ***per eseguire le istruzioni privilegiate***.
- Le chiamate a queste funzioni vengono definite ***Hypercall***.

>[!todo] Full-Virtualization
>Nella ***Full-Virtualization*** fornisce macchine virtuali che hanno la stessa interfaccia di una macchina fisica.

Il sistema ***guest non può identificare che si trova su una macchina virtuale***.

>[!abstract] Performance
>La ***full virtualization*** richiede un monitoraggio molto più pesante.

> *Esempio*: un sistema guest richiede una system call potenzialmente pericolosa.
1. L'hypervisor controlla ogni operazione e nel momento in cui si accorge di una operazione pericolosa.
2. Quando ne rileva una la blocca e genera una serie di operazioni alternative
3. Restituisce alla macchina guest il risultato voluto senza eseguire l'operazione pericolosa.
>[!warning] La full-virtualization è generalmente meno performante

![[attachements/Full&ParaVirtualization.png]]

## Cloud e Servizi
---
>[!tldr] Idea
>Il ***Cloud*** di un provider è essenzialmente un gruppo di datacenter in ciascuno dei quali vengono forniti dei [[Scenari di Integrazione#Sistemi a Micro-Servizi|micro-servizi]].

### Servizi
> I servizi cloud si distinguono per il livello di componibilità che offrono e per la capacità di scalare, trasparentemente all'utente.

Tipologie di Servizi:

>[!help] `SaaS` Software as a Service
>Un ***servizio applicativo*** che non vede né sistema operativo né host su cui lavora (es. *google documents*).

>[!todo] `PaaS` Platform as a Service
>Fornisce delle `API` di sviluppo per **comporre servizi più complessi**, senza conoscere il sistema operativo.

>[!tip] `IaaS` Infrastructure as a Service
>Fornisce una ***infrastruttura*** su cui installare servizi, come una *macchina virtuale*

#### Piattaforme di Gestione di Cloud Privati
> Un privato vuole costruire un proprio datacenter in cui realizzare un sistema cloud.

>[!abstract] Architettura
>Ciò è reso possibile da alcune ***architetture software*** che permettono id usare le risorse di più macchine fisiche *rendendole disponibili parzialmente su richiesta*.

Tra queste architetture ricordiamo:
- [OpenStack](https://www.openstack.org/)
- [OpenNebula](https://opennebula.io/)

È anche possibile usare kubernetes #addLink .