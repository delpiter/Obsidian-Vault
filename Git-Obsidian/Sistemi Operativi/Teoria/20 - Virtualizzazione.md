## Virtualizzazione vs Emulazione
---
>[!definizione] Virtualizzazione
>Tramite ***virtualizzazione*** è possibile eseguire uno o più [[3 - Livelli del Sistema Operativo#^9f2787|sistemi operativi]] su un ***unico dispositivo***.
>Ciò avviene in un ambiente *protetto* e *monitorato* che prende il nome di **macchina virtuale**

Il *sistema operativo* in cui viene eseguita la macchina virtuale, viene detto
- Sistema ***ospitante*** (***host***)

La macchina virtuale è chiamata ***ospite*** (***guest***)

>[!info] Emulazione
> Nell'***emulazione*** l'hardware viene completamente emulato dal programma di controllo.
> Ogni istruzione che il sistema *guest* esegue, viene tradotta in una sequenza di istruzioni della macchina ***host***
>>[!warning] Performance
>>Il processo di emulazione risulta *più lento* rispetto alla ***virtualizzazione***

> Differenze

Il codice della ***macchina virtuale*** viene eseguito direttamente dall'***host***
- Il ***guest*** pensa di essere eseguito da una macchina *reale*
- Il *codice* della ***macchina virtuale***, perciò deve essere codice macchina *eseguibile dalla macchina hardware reale* sottostante

>[!done] In Breve
>>[!abstract] Virtualizzazione
>>`CPU` virtuale *compatibile* con la `CPU` fisica
>
>>[!summary] Emulazione
>>Permette di usare un processore *virtuale* che ***non*** è compatibile con quello *reale*

## Container
---
> 2 Possibilità di ***virtualizzazione***

>[!caution] Hardware Level
>Nel caso delle ***macchine virtuali***, all'utente del *sistema di virtualizzazione* viene presentata un'interfaccia su cui installare un *sistema operativo*
>>[!fail] Contro
>>Molto lenta l'esecuzione di un'istruzione
>>- Deve passare numerosi "*step*" prima di essere eseguita dall'hardware reale

>[!tldr] OS Level
>Nel caso dei ***container*** all'utente viene presentata una partizione del *sistema operativo corrente*, su cui installare ed eseguire applicazioni che *rimangono isolate* nella partizione
>>[!info] Specifiche
>>Il singolo container ***non ha un kernel*** proprio
>>- Questo rende il container più veloce di una *macchina virtuale*
>>- Si appoggia a quello della macchina ***host***
>
>>[!warning] Limitazione
>>Il *sistema operativo* del ***container*** è deve essere lo stesso della macchina ***host***
>>- Le [[3 - Livelli del Sistema Operativo#System Call|system call]] chiamate dal ***container*** sono le stesse del sistema operativo ***host***


![[Type_of_Virtualization.png]]

#### Composizione
>[!info] Componenti
>La virtualizzazione ***OS-Level*** è composta da:
>- Un solo ***kernel***, quello del sistema ***host***
>- Multiple istanze isolate di *user-space*
>
>>[!definizione] User-Space
>> Lo ***user-space*** consiste in un *file system* del container
>> - Su di esso posso *scaricare* librerie e *installare* applicazioni senza interferire con gli *altri container*
>> 
>> Nello ***user-space*** sono presenti, inoltre, delle *interfacce di rete virtuali* usate per:
>> - Comunicare con la ***rete esterna***
>> - Comunicare con la macchina ***host***
>> - Comunicare con altri ***container***

### Software per Container
> Ricordiamo solo i Principali

>[!abstract] Docker
>Si appoggia sul *sistema operativo* ***linux*** che fornisce a livello kernel un supporto per container detto `LXC` (***L***inu***X*** ***C***ontainer)

>[!summary] Hyper-V
>Software di *Microsoft*, fornisce unità di isolamento chiamate *container* ma in realtà sono ***macchine virtuali***

>[!example] Container di Windows Server
>Sono effettivamente dei *container*

### Lavorare con le Immagini Docker
>[!info] Immagine
> I container Docker sono eseguiti a partire da "***immagini di container***" che hanno un formato standardizzato
> - L'immagine contiene il *file system* ***iniziale*** del container
> 	- Come appare il *file system* al momento in cui il container comincia la propria ***esecuzione***
> 
>

L'immagine contiene altre ***informazioni***
- Indicazioni di ***script*** o ***processi*** da mettere in esecuzione al *momento di avvio*

>[!warning] Attenzione
>Le immagini container possono essere *scaricate* da internet
>- Un qualunque malintenzionato può caricare una immagine che esegue ***istruzioni non sicure***