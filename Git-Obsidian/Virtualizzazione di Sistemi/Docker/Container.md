## Containerizzazione
---
>[!definizione]
>Un ***container*** è un *ambiente di esecuzione isolato* in user space, privo di un proprio *kernel*, costituito da un gruppo di processi che condividono una visione limitata e controllata delle risorse di sistema dell'host.

>La ***tecnologia dei container*** sposta il focus dalla virtualizzazione del server verso la *virtualizzazione dell'applicazione*, creando per l'applicazione un contesto di esecuzione virtualizzato che **non è più tutto un server**.

La virtualizzazione a ***livello del sistema operativo*** è composta da:
- Un ***solo*** [[../../Sistemi Operativi/Teoria/3 - Livelli del Sistema Operativo#Kernel|kernel]], quello del sistema host.
- Multiple *istanze isolate di user-space*.

>[!help] User-Space
>Lo ***user-space*** consiste in un *file system* del container su cui si possono scaricare librerie e installare applicazioni senza interferire con gli altri container.
>Sono presenti delle interfacce di rete virtuali usate per comunicare con: 
> - La [[../../Reti/Network Layer/Reti IP|rete]] **esterna**.
> - La **macchina host**.
> - Altri **container**.

>[!warning] Limitazione
>Il *sistema operativo* del ***container*** è deve essere lo stesso della macchina ***host***.
>- Le [[../../Sistemi Operativi/Teoria/3 - Livelli del Sistema Operativo#System Call|system call]] chiamate dal ***container*** sono le stesse del sistema operativo ***host***.

> In un ambiente Linux un *container* è una struttura composta da:
1. Un'**immagine iniziale** (filesystem statico, read only).
2. Un **processo principale**, che può creare altri processi.
3. Un set di **namespaces**.
4. Una configurazione di `Cgroups`.
5. Un profilo di **capabilities** e **filtri** di chiamate di sistema.

### Meccanismi Fondamentali
#### Namespaces
>[!tl;dr] Isolamento delle Risorse
>I ***namespaces*** danno al container l'illusione di essere una macchina separata, gli fanno vedere un sottoinsieme delle risorse dell'host.

Per ciascun namespace del container, l'host ha un namespace corrispondente.

> In particolare sono $7$:
1. `PID` *Namespace*: Fornisce una ***gerarchia di processi separata***, il processo principale del container diventa il `PID` $1$.
2. Net *Namespace*: Isola lo [[../../Reti/Standards/ISO-OSI|stack di rete]], il container vede le proprie interfacce di rete, [[../../Reti/Network Layer/Routing/Routing#Tabella di Routing IP|tabelle di routing]], [[../../Reti/Transport Layer/Livello di Trasporto#Numero di Porta|porte]] e regole di [[../../Reti/Network Layer/Network Security/Firewall|firewall]], indipendenti dall'host.
3. Mount (`MNT`) *Namespace*: Isola i punti di montaggio. Il container vede una propria gerarchia di file, impedendo l'accesso ai file dell'host, a meno che non vengano esplicitamente montati (***bind mount***).
4. `UTS` *Namespace*: Permette al container di avere il proprio **hostname e nome di dominio**.
5. `IPC` *Namespace*: Isola i meccanismi di comunicazione tra processi, come code di messaggi, segmenti di memoria condivisa e [[../../Sistemi Operativi/Teoria/13 - Semafori|semafori]].
6. User *Namespace*: Permette la mappatura degli `ID` utente e gruppo, un utente che agisce come root `UID 0` nel container, può corrispondere a un **utente non privilegiato**.
7. `CGroup` *Namespace*: Isola la gerarchia dei **CGroup** dell'host.

#### Control Groups
>[!todo] Limitazione e Monitoraggio
>I `CGroups` determinano quanto il container può consumare a livello di risorse.

> Il container vede le seguenti restrizioni:
- *CGroup* delle risorse di calcolo ([[../../Architettura degli Elaboratori/Architettura del Calcolatore/La CPU|CPU]]): **Limitazione del tempo** di `CPU` e pinning su core specifici.
- *CGroup* della memoria ([[../../Architettura degli Elaboratori/Architettura del Calcolatore/RAM|RAM]]): **Limiti rigidi sulla memoria fisica** e sulle swap. Se il gruppo di processi eccede il limite, interviene l'Out Of Memory Killer nel contesto del container.
- *CGroup* dell'I/O: Limitazione della **larghezza di banda** o delle operazioni al secondo **verso i dischi**.
- *CGroup* dei `PIDs`: Limita il **numero massimo di processi** che possono essere creati all'interno del container.

>[!danger] Attenzione
> ***Non indicare limitazioni***, significa che il container instanziato, può usare *tutte le risorse* della macchina fisica.
#### Capabilities
>[!hint] Restrizione dei Privilegi
>In un *container*, anche se l'utente è root, il **kernel** utilizza le ***POSIX Capabilities*** per scomoporre i privilegi del superuser in *unità granulari*.

Quando si mette in esecuzione un container è possibile assegnare o negare alcuni privilegi al container. 
### Software per Container
> Ricordiamo solo i Principali

>[!abstract] Docker
>Si appoggia sul *sistema operativo* ***linux*** che fornisce a livello kernel un supporto per container detto `LXC` (***L***inu***X*** ***C***ontainer).

Al giorno d'oggi il *daemon* runc non si appoggia più sui container `LXC` ma usa una propria implementazione.
- Un daemon è un processo in background di lunga durata che viene eseguito dal sistema operativo, senza l'interazione dell'utente. ^f4ae14

![[../attachements/ContainerEcosystemLinux.png]]

>[!summary] Hyper-V
>Software di *Microsoft*, fornisce unità di isolamento chiamate *container* ma in realtà sono ***macchine virtuali***

>[!example] Container di Windows Server
>Sono effettivamente dei *container*
