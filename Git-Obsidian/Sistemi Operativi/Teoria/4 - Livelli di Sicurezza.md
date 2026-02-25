## Distinzione tra Modo kernel e Modo Utente
---

>[!info] Stato di esecuzione
>La `CPU` è fatta per lavorare con uno stato di esecuzione:
>Quando la `CPU` è nello stato di livello di privilegio $0$, consente l'esecuzione di quasi tutte le operazioni
>>[!abstract] Differenza di privilegi
>>Più il livello di privilegio ***aumenta***, più il *set di istruzioni* viene ***ristretto***
>>- Diminuisce man mano quello che la `CPU` è in grado di fare

![[Protection-Levels.png|400]]
> *Livello di privilegio / protezione*

Il livello $3$ è il livello di privilegio utilizzato quando viene usata una ***applicazione utente***

La suddivisione in "***rings***" di protezione della `CPU` è un supporto dell'hardware che consente al sistema operativo di realizzare ***politiche di sicurezza***.

>[!hint] [[Virtualizzazione]]
>Recentemente i sistemi operativi hanno aggiunto un *nuovo livello* "$-1$" usato unicamente per gestire operazioni potenzialmente pericolose da ***parte di macchine virtuali***.
### Cambio di Livello di privilegio
> Nel momento in cui l'applicazione chiama una system call
 
Il meccanismo con cui la [[3 - Livelli del Sistema Operativo#System Call|system call]] viene chiamata, cambia lo ***stato di esecuzione*** e il ***livello di privilegio*** della `CPU` per poter eseguire quella istruzione
- Quando la *system call* finisce, si esegue l'***operazione opposta***, torna al livello di protezione precedente

>[!info] Cambi Continui
>La `CPU` cambia continuamente il suo ***modo di protezione***
>- Il cambiamento viene fatto solo tramite ***chiamata o terminazione*** della *system call*
>>[!caution] Strumento di Cambiamento
>>Il cambiamento è fatto tramite "`interrupt`"

### Librerie e Chiamate di sistema
>Le ***system call*** forniscono ai processi i *servizi* offerti dal *sistema operativo*

>[!Realizzazione]
>Il modo in cui sono realizzate *cambia* al variare della `CPU` e del *sistema operativo*
>Si possono usare *direttamente* utilizzando ***linguaggi di basso livello***
>Possono essere chiamate *indirettamente* utilizzando ***linguaggi di alto livello***

>[!abstract] API
>L'insieme di tali funzioni di libreria rappresentano le ***API***, l'**interfaccia** che il sistema operativo offre ai ***programmi di alto livello***
>Le librerie messe a disposizioni del *sistema operativo* sono dette ***librerie di sistema***
>>[!done] Cambio di hardware
>>Cambiando sistema  operativo o cambiando processore i nomi delle funzioni delle ***API*** rimangono gli stessi, ma cambia il modo di ***invocare le system call***

Alcune *API* molto diffuse sono:
- `Win32` per windows
- `POSIX` per sistemi *unix-like*
- `Java API` per le *Java Virtual Machines*

![[Levels-API.png]]

>[!question] Quali system call utilizza un eseguibile?

>Su ***linux*** esiste un comando che permette di vedere quali ***system call*** sono usate da un programma in esecuzione

```bash
strace command
```

Esso esegue il ***comando specificato*** come argomento fino a che questo termina
- Intercetta e visualizza le *system call* che sono chiamate dal processo e i segnali che sono ricevuti dal processo

```bash
strace ifconfig 

execve("/sbin/ifconfig", ["ifconfig"], [/* 52 vars */]) = 0 brk(NULL) = 0x12f3000 
access("/etc/ld.so.nohwcap", F_OK) =-1 ENOENT(No such file or directory) 
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS,-1, 0) = 0x7f37cb8ee000 access("/etc/ld.so.preload", R_OK) =-1 ENOENT(No such file or directory) 
open("/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3 fstat(3, {st_mode=S_IFREG|0644, st_size=71665, ...}) = 0 
mmap(NULL, 71665, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f37cb8dc000 close(3
```