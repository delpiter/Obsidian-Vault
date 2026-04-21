## Proxmox
---
>[!definizione]
>***Proxmox Virtual Enviroment*** è una piattaforma di virtualizzazione progettata per fornire infrastrutture *iper-convergenti*.

Proxmox permette la gestione di [[../Virtualizzazione|Macchine virtuali]] e [[../Docker/Container|Containers]].
- Basato su Linux Debian, utilizza una versione modificata del kernel di ubuntu.

**Proxmox** supporta due tipi di virtualizzazione:
- Virtualizzazione a livello di container
- Virtualizzazione "Full".

>[!info]
>
>> [!hint] `LXC`
>> ***Linux Containers*** è una virtualizzazione a livello di sistema operativo, viene usato per eseguire multiple istanze di sistemi linux indipendenti su un host *usando un solo kernel*.
>
>> [!hint] `KVM`
>> ***Kernel-Based Virtual Machine*** è un modulo di virtualizzazione di linux che permette al kernel di funzionare come un [[../Virtualizzazione#Hypervisor|hypervisor]].

Proxmox ha una [[../Docker/Docker#Nome di una Immagine Docker|repository]] di immagini `LXC` già pronte.

>[!caution] Migrazione a Caldo
>Proxmox permette una ***migrazione di una macchina virtuale in utilizzo*** da un nodo (potenzialmente molto utilizzato) ad un altro (più libero).
### Servizi di Proxmox
>[!example] Alcuni Servizi

> pve-cluster
- Gestisce il cluster e la configurazione condivisa.

> Corosync
- Servizio di comunicazione tra nodi del cluster.

> Pvdaemon
- Motore `API` di proxmox.

> Pveproxy
- Server web integrato, fornisce una interfaccia web e fa da ***reverse proxy*** verso le `API`.

> Pvestatd
- Servizio di monitoraggio, aggiorna `CPU`, `RAM`, disco e stato delle macchine e dei container.

> pve-ha-lrm (High Availability)
- Gestiscono l'alta disponibilità.

> Pvescheduler
- Pianifica task automatici, backup programmati e snapshot pianificati.

### Proxmox Storage
>[!abstract] `LVM`
>Il ***Logical Volume Manager*** è una tecnologia di gestione dei volumi logici in linux

Offre una maggiore flessibilità nella gestione dei dispositivi di archiviazione rispetto ai tradizionali file system basati su partizioni fisse.

> Caratteristiche principali
- *Gestione dinamica* dei volumi.
- *Espansione* e *riduzione* dei volumi.
- **Snapshot**, copia istantanea di un volume logico per fare backup.
- Gestione dello spazio *su più dischi*.
- `LVM` Cluster, consente a più nodi di ***accedere in modo sicuro*** ai volumi condivisi.

### Proxmox Autenticazione
> Per autenticarsi su proxmox si possono usare 3 diverse modalità


>[!hint] PAM

Attraverso la linux PAM standard authentication.
- Per utenti di sistema linux e autenticazione attraverso `PAM` (modulo di autenticazione linux)


> [!note] PVE

Proxmox VE authentication server
- Per gli utenti presenti in `/etc/pve/user.cfg`
- Non sono utenti del sistema linux
- Servono per accedere alle `GUI`/`API`
- Devono solo *amministrare* le ***vm***

> [!caution] Active Directory

L'[[Active Directory]] è un servizio per gestire in modo centralizzato autenticazione, autorizzazione e amministrazione di risorse di rete.
- Possibilità di sincronizzare tutti gli utenti del dominio
- Servono per accedere alle `GUI`/`API` e *usare* le ***vm***.

### Ruoli di Proxmox
| Role Name             | Description                                                                |
| --------------------- | -------------------------------------------------------------------------- |
| **Administrator**     | Full access to all resources and settings                                  |
| **PVEAdmin**          | Full access except user management                                         |
| **PVEDatastoreAdmin** | Full access to storage                                                     |
| **PVEDatastoreUser**  | Allocate/use storage, but no configuration changes                         |
| **PVEAuditor**        | Read-only access to all objects                                            |
| **PVEVMAdmin**        | Full control of VMs (create, modify, delete, start/stop)                   |
| **PVEVMUser**         | Basic VM usage (start, stop, console), no configuration                    |
| **PVETemplateUser**   | Can use VM templates                                                       |
| **PVEPoolAdmin**      | Full control over resource pools                                           |
| **PVEPoolUser**       | Use/access assigned pool resources                                         |
| **PVESysAdmin**       | System-level administration (nodes, network, etc.), but no user management |
| **PVESysAudit**       | Read-only access to system-level information                               |
| **PVEUserAdmin**      | Manage users, groups, and permissions                                      |
| **NoAccess**          | Explicitly denies access                                                   |

### Proxmox Network

>[!caution] Bridge (Linux Bridge)
* È la modalità più comune.
* Collega le ***VM*** direttamente alla rete fisica, come se fossero dispositivi reali.
* Le ***VM*** ottengono un [[../../Reti/Network Layer/Protocollo IP|IP]] dalla stessa rete del nodo *Proxmox*.
* Esempio: `vmbr0` collegato a `eth0`.

>[!hint] VLAN

* Permette di separare il traffico su *più reti logiche* usando una sola interfaccia fisica.
* Configurabile su bridge (es. `vmbr0.10`, `vmbr0.20`).
* Richiede switch compatibile [[../../Reti/Data Link Layer/Networks/802.X/Virtual LAN|VLAN]].

>[!definizione] SDN (Software Defined Networking)

* Funzionalità recente in Proxmox.
* Permette di gestire *reti virtuali*, [[../../Reti/Data Link Layer/Networks/Virtualizzazione di Rete#Tecnologie di Virtualizzazione|rete di overlay]] (VXLAN), e configurazioni multi-nodo.
* Si integra con ***firewall*** e automazione.

## Ansible
---
>[!tldr] Idea
>`Ansible` è un *sistema opensource* che permette l'***automazione e la gestione*** dell'infrasttruttura `IT`.

L'obbiettivo è il raggiungimento di uno stato $B$ a partire da uno stato $A$.

### Playbook
> I playbook sono file `{yaml icon} .yaml` che definiscono che cosa il sistema deve fare

```yaml title:Playbook
- name: Ansible script to install docker
  hosts: swarm #execute only on swarm nodes
  strategy: free
  become: true
  
  tasks:
	 - name: install docker dependencies
		apt:
			pkg:
				- ca-certificates
			    - curl
				- gnupg
			state: latest
			cache_valid_time: 86400
	
	- name: install python and pip
		apt:
			pkg:
				- python3
				- python3-pip
			state: latest
```

Si possono *creare utenti*, *installare pacchetti* e molto altro.