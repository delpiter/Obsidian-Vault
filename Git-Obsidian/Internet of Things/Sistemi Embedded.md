## Embedded Systems
---
>[!definizione]
>I ***sistemi embedded*** sono sistemi di computazione *special purpose*.
>- Compiono funzioni o *task specifici* in **dispositivi fisici** o sistemi elettronici di dimensioni diverse e con scopi diversi.

I ***task*** di *sistemi embedded* richiedono una interazione con il mondo fisico tramite [[Sensori e Azionatori/Sensori e Azionatori]].

Tipicamente composti da due parti: [[../Definizioni/Definizioni_Architettura#Il Calcolatore|Hardware]] e [[../Definizioni/Definizioni_Architettura#Il Calcolatore|Software]].
- Potrebbe capitare che la parte ***software*** manchi.

>[!example] Esempi di Sistemi Embedded

>***Consumer Electronics***
- Smartphones, camera, ...

> ***Elettrodomestici***
- Termostato, frigoriferi "smart", ...

> ***Macchine e Veicoli***
- Drive System, Navigation System, ...

![[attachements/EmbeddedSystems.png]]

Un sistema embedded tipicamente ***esegue una applicazione specifica***.
- Un *programma infinito*, un **task** eseguito ripetutamente.

Progettati per essere **robusti** a per la ***minima utilizzazione di risorse*** (orientato all'efficienza).
- Con interfacce utente *ad hoc*.

>[!abstract] Caratteristiche dei Sistemi

"*One never ending program*"

> **Critical Systems**
- I sistemi embedded spesso sono fondamentali nel contesto dove sono usati.
- Devono essere **affidabili** e **sicuri**.

> **Reattività**
- I sistemi embedded sono tipicamente usati in applicazioni dove i sistemi devono reagire a degli ***stimoli del mondo fisico***.
- Nel caso di [[../Sistemi Operativi/Teoria/7 - Scheduler#Hard Real-Time|hard real time]] la violazione della deadline è considerata un fallimento del sistema.

> **Efficienza**
- I sistemi embedded sono progettati per avere una elevata efficienza energetica.
- Devono essere inoltre efficienti in termini di: dimensione del codice, tempo di esecuzione, costi.
## Cyber-Physical Systems
----
>[!definizione]
>I `CPS` sono i sistemi che integrano le **computazioni** con i **processi fisici**.

> Differenze con i *sistemi di information processing*
- Forte dipendenza dal tempo.
- Concorrenza.
- Reattività e eventi asincroni.

Formati da 3 sottosistemi
- **Parte fisica**.
- Parte **embedded** (una o più piattaforme equipaggiate di sensori).
- Parte Network #addLink

## Embedded System Architecture
---
![[attachements/HardwareArchitecture.png]]

### Processore
>[!caution] [[../Architettura degli Elaboratori/Architettura del Calcolatore/La CPU|CPU]]
>***General-Purpose processors***
>- Processori con un insieme di istruzioni e una architettura *predefinita*.
>- Il comportamento del sistema è definito dal programma (*software*).
>
>***Single-Purpose processors***
>- Circuiti progettati per implementare una *specifica funzione*.
>
>***Application-Specific processors*** (ASIP)
>- Processori programmabili ottimizzati a fare una specifica classe di applicazioni con *feature comuni*.


>[!abstract] Microcontroller Unit

Il ***microcontroller*** integra in un singolo chip tutti i componenti richiesti per avere una completa autonomia.
- È in grado di eseguire **autonomamente** i *task* per il cui sistema embedded è progettato.
#### System On a Chip
>[!help] SoC
>Il ***system on a chip*** è un [[../Architettura degli Elaboratori/Algebra di Bool e Logica Digitale/Circuiti Digitali#Circuiti Integrati|chip]] che integra un sistema completo (`CPU`, *memoria*, *controller* *I*/*O* e controller di rete).

È un ***circuito integrato complesso*** che include un *microcontroller* o un *microprocessore* con altri componenti.
- Es. Raspberry

### Sensori, Attuatori e Bus
>[!check] Sensori
> I ***sensori*** sono dei *dispositivi trasduttori* che rendono possibile: 
> - La **misurazione** di alcuni fenomeni fisici.
> - **Rilevare** e **quantificare** concentrazioni chimiche (fumo).

Possono essere:
- [[../Architettura degli Elaboratori/Rappresentazione dell'Informazione/Il Calcolatore e i Numeri Binari#I sistemi Digitali|analogici]] che [[../Architettura degli Elaboratori/Rappresentazione dell'Informazione/Il Calcolatore e i Numeri Binari#I sistemi Digitali|digitali]].
>[!example] Esempi
- Sensore di prossimità
- Di temperatura
- `GPS`
- Di luminosità

>[!abstract] Azionatori
>Gli ***azionatori*** sono dispositivi che producono degli effetti misurabili nell'ambiente.

>[!caution] [[../Architettura degli Elaboratori/Architettura del Calcolatore/BUS dei Calcolatori|BUS]]
>Le *interazioni* tra il processore e i sensori è possibile tramite i `BUS`.

Tipicamente ***seriali***.