## Introduzione
---
### Memory Manager
>[!info]
>Il ***memory manager*** è la parte del sistema operativo che gestisce la ***memoria principale***
>- In alcuni casi, può gestire anche parte della memoria secondaria

##### Compiti
Il ***memory manager*** ha due compiti principali:
- Tenera **traccia** della memoria *libera* e *occupata*
- ***Allocare*** memoria ai processi e ***deallocarla*** quando non più necessaria

## Binding
>[!definizione] Definizione
>Il ***binding*** è l'associazione di indirizzi di memoria ai dati e alle istruzioni di un programma

#### Tipi di Binding
>[!abstract] Durante la Compilazione
>Gli indirizzi vengono ***calcolati al momento della compilazione*** e resteranno tali ad ogni esecuzione del programma
>>[!warning] Problemi
>>- Codice fortemente ***legato*** alla macchina
>>- Bisogna assicurarsi che a due programmi non venga associata una ***stessa area di memoria***

> Il codice generato viene detto codice ***assoluto***

>[!done] Vantaggi

- Non richiede hardware speciale
- Semplice e molto veloce

>[!fail] Svantaggi

- Non funziona con la *multiprogrammazione*

---
>[!abstract] Durante il Caricamento
>Il codice generato dal compilatore non contiene ***indirizzi*** assoluti ma ***relativi***
>- Durante il caricamento il loader si preoccupa di ***aggiornare tutti i riferimenti*** agli *indirizzi* di memoria.

>Il codice viene detto ***rilocabile***

>[!done] Vantaggi

- Non richiede hardware speciale
- Permette di gestire *multiprogrammazione*

>[!fail] Svantaggi

- Richiede una ***traduzione degli indirizzi*** da parte del loader

---
>[!abstract] Durante l'esecuzione
>L'individuazione dell'indirizzo di memoria effettivo viene effettuato durante l'esecuzione da un componente hardware specifico:
>>[!tldr] Memory Management Unit

>[!done] Vantaggi

- Permette di gestire *multiprogrammazione*
- Alto risparmio di memoria

>[!fail] Svantaggi

- Richiede ***hardware specifico***
#### Indirizzi Logici e Fisici
>[!info] Spazio di Indirizzamento Logico
>Ogni processo è associato ad uno ***spazio di indirizzamento logico***
>- Gli indirizzi usati sono *indirizzi logici*, **riferimenti** a questo spazio di indirizzamento

>[!caution] Spazio di Indirizzamento Fisico
>Ad ogni indirizzo logico *corrisponde* un indirizzo fisico
>- È il compito dell'`MMU` di tradurre ogni ***indirizzo logico in indirizzo fisico***


>[!abstract] Registro di Rilocazione
>Se il valore del ***registro di rilocazione*** è $R$, uno spazio logico $0,\dots,Max$ viene tradotto in uno spazio fisico $R, \dots, R+Max$
>>[!warning] Registro Limite
>> Il ***registro limite*** viene usato per implementare meccanismi di protezione della memoria:
>> Se l'indirizzo da convertire è $\leq$ del ***registro limite*** allora procedi con la *rilocazione*, altrimenti *lancia un errore*

##### Loading Dinamico
>[!definizione] Significato
>Consente di poter *caricare* alcune ***routine di libreria*** solo quando vengono richiamate

- Tutte le routine a ***caricamento dinamico*** risiedono su un *disco*, e quando servono, *vengono caricate*

##### Linking Dinamico
>Se il *linker* collega e risolve tutti i riferimenti dei programmi, si dice ***linking statico***
>- Le routine di libreria vengono ***copiate in ogni programma*** che le usa

>[!summary] Dinamico
>È possibile *posticipare il linking* delle routine di libreria al momento del ***primo riferimento*** durante l'*esecuzione*
>- Consente di avere eseguibili più **compatti**
>- In memoria esiste una sola istanza della libreria, e tutti i programmi eseguono codice di questa istanza
>
> Questa libreria si chiama [[#^8c1dc6|codice reentrant]].


>[!done] Vantaggi

- Risparmio di memoria
- Consente l'***aggiornamento automatico*** delle versioni delle librerie

>[!fail] Svantaggi

- Può causare problemi di "***versioning***"

>[!definizione] Codice Reentrant
>Il ***codice reentrant*** (*multi-instance*) è una routine riutilizzabile che diversi programmi possono chiamare, interrompere e riprendere simultaneamente

^8c1dc6

## Allocazione
---
>[!definizione] Definizione
>È una delle funzioni principali del gestore di memoria
>Consiste nel ***reperire e assegnare*** uno *spazio di memoria fisica* ad un programma

### Tipi di Allocazione
#### In Base alle Zone
>[!info] Allocazione Contigua
> Tutto lo spazio assegnato ad un programma deve essere formato da ***celle consecutive***

>[!example] Allocazione Non Contigua
> È possibile assegnare a un programma ***aree di memoria separate***

- L'`MMU` basata su rilocazione è in grado di eseguire solo ***allocazione Contigua***

#### In Base alla Modalità
>[!cite] Statica
>Un programma **deve mantenere** la propria *area di memoria* dal caricamento alla terminazione
>- ***Non*** è possibile *riallocare* il programma durante l'esecuzione

>[!abstract] Dinamica
>Durante l'esecuzione, un programma ***può essere spostato*** all'interno della memoria

### Allocazione a Partizioni Fisse
>[!definizione] Descrizione
>La memoria disponibile viene ***suddivisa in partizioni***
>Ogni processo viene caricato in una delle partizioni *libere* che ha ***dimensioni sufficiente a contenerlo***

Allocazione di tipo Statica e Contigua


>[!done] Vantaggi

- Molto ***semplice*** da implementare

>[!fail] Svantaggi

- Largo *spreco di memoria*, dato dalla [[#^f4efb4|frammentazione Interna]]
- *Parallelismo limitato* dal numero di partizioni

>[!info] Frammentazione della Memoria
>Se un processo occupa una ***dimensione inferiore*** a quella della partizione a cui viene associato, lo spazio non utilizzato è *sprecato*

^f4efb4

### Allocazione a Partizioni Dinamiche
>[!definizione] Descrizione 
>La memoria disponibile viene *assegnata* nella ***quantità richiesta*** ai vari processi richiedenti
>Nella memoria possono essere presenti ***zone inutilizzate*** per effetto della terminazione dei processi

Allocazione ***statica*** e ***contigua***

>[!warning] Problema
>Dopo un certo numero di allocazioni e deallocazioni di memoria, lo spazio libero appare suddiviso in piccole aree
>- Fenomeno della [[#^f4efb4|Frammentazione Esterna]]

#### Compattazione
>[!info] Concetto
>Consiste nella *riallocazione* dei programmi **durante la loro esecuzione**.
>- La ***compattazione*** viene eseguita ***solo se*** è possibile riallocare i programmi
> 
> Compattare la memoria significa *spostare tutti i programmi* in modo da ***riunire le aree inutilizzate***


>[!done] Vantaggi

- Risolve il problema della ***frammentazione esterna***

>[!fail] Svantaggi

- Operazione ***molto onerosa***
- Non può essere usata in sistemi interattivi

### Allocazione Dinamica con Strutture Dati
> Quando la memoria è ***assegnata dinamicamente*** è necessario avere una *struttura dati* per mantenere informazioni sulle ***zone libere e occupate***

#### Mappa di Bit
>[!info] 
>La memoria viene suddivisa in unità di allocazione, ad ogni unità corrisponde un `BIT` in una ***bitmap***
>- Le unità libere sono associate ad un `BIT` di valore $0$
>- Le unità occupate sono associate ad un `BIT` di valore $1$

La ***dimensione dell'unità*** di allocazione è un parametro importante

>[!done] Vantaggi

- Dimensione fissa e calcolabile

>[!fail] Svantaggi

- Per individuare uno spazio di memoria di dimensione $k$ è necessario cercare una sequenza di $k$ bit $0$ consecutivi
	- Tale operazione è $O(n)$, dove, $n$ è il numero di unità di allocazione

#### Lista di Puntatori
>[!info]
>Si mantiene una lista dei blocchi allocati e liberi
>Ogni elemento della lista specifica:
>- Se si tratta di un *processo* ($P$) o di un *blocco libero* (**hole**. $H$)
>- La ***dimensione*** (inizio/fine) del segmento

>Allocazione

Un blocco libero viene ***selezionato e suddiviso*** in due parti:
- Un blocco $P$ della dimensione *desiderata*
- Un blocco $H$ della dimensione *rimanente* del blocco selezionato

> Deallocazione

4 Casi possibili
![[MemoryDeallocationPointerList.png]]

##### Selezione del Blocco Libero
>[!info] First Fit
>Si scorre la lista dei blocchi liberi fino a quando non trova il ***primo segmento vuoto*** grande abbastanza da *contenere* il processo

>[!abstract] Next Fit
>Come ***first fit***, ma invece di ripartire sempre dall'*inizio*, riparte dal punto dove si era fermato all'*ultima allocazione*
>>[!tldr] Curiosità
>> Il **next fit** ha performance peggiori di ***first fit***

>[!Summary] Best Fit
>Selezione il ***più piccolo*** fra i blocchi presenti in memoria che riesce a *contenere il programma*
>>[!warning] Commenti
>> Più lento di ***first fit*** e genera più ***frammentazione***

>[!Example] Worst Fit
>Selezione il ***più grande*** fra i blocchi presenti in memoria che riesce a *contenere il programma*

## Paginazione
---
>[!definizione] Descrizione
>Lo *spazio di indirizzamento logico* di un processo viene suddiviso in un insieme di blocchi di dimensione fissa chiamati ***pagine***
>
>La *memoria fisica* viene suddivisa in un insieme di blocchi della stessa dimensione delle pagine, chiamati ***frame***
>>[!example] Processo Allocato in memoria
>> Vengono reperiti **ovunque** dalla memoria un numero *sufficiente di frame* per **contenere** le *pagine* del processo

Serve un meccanismo che mappa una *pagina* ad un *frame* nella memoria fisica

![[Paging.png]]

### Dimensione delle Pagine
>[!question] Come scegliere la dimensione della pagina?

La dimensione delle pagine deve essere una ***potenza di due*** per *semplificare* la trasformazione da indirizzi **logici** a **fisici**

>[!caution] Trade Off
>La scelta della dimensione deriva da un trade-off
>- Con ***pagine piccole***, la *tabella* delle pagine *cresce* di **dimensioni**.
>- Con ***pagine grandi***, lo spazio di memoria perso per [[#^f4efb4|frammentazione interna]] può essere considerevole

### Page Table
#### Soluzione 1
>[!note] Registri Dedicati 
>La tabella può essere contenuta in un insieme di registri ad alta velocità all'interno dell'`MMU` o `CPU`
>>[!warning] Troppo costoso

#### Soluzione 2
>[!Totalmente in memoria] 
>>[!warning] Il numero di accessi in memoria verrebbe raddoppiato

#### Soluzione
>[!info] Translation Lookaside Buffer
>Un `TLB` ha un funzionamento simile alla ***cache***
>Costituito da un insieme di **registri associativi** ad alta velocità, ogni registro è diviso in *chiave-valore*
>>[!caution] Operazione di lookup
>> Viene *richiesta la ricerca* di una chiave
>> - La chiave viene *confrontata* con **tutte** le chiavi nel ***buffer***
>> - Se è presente, ritorna il valore corrispondente (`TLB` ***hit***)
>> - Se non è presente (`TLB` ***miss***) si utilizza la tabella in memoria

![[TraslationLookasideBuffer.jpg]]

## Segmentazione
---
>[!info] Descrizione
>In un sistema con ***segmentazione*** la memoria è suddivisa in aree differenti dal punto di vista funzionale
>>[!example] Esempi
>> *Aree Text*:
>> - Contengono il codice **eseguibile**
>> - Condivise da più processi
>> 
>> *Aree dati*
>> - Possono essere condivise o no
>>
>> *Area Stack*
>> - Read/Write, non può essere condivisa

Lo ***spazio di indirizzamento logico*** è dato da un insieme di segmenti
- Un *segmento* è una area di memoria contenente elementi tra loro affini
- Ogni segmento è caratterizzato da un ***nome*** e ***lunghezza***
- Ogni riferimento in memoria è dato da (nomeSegmento, Offset)

>[!warning] Spetta la compilatore la suddivisione di un programma in segmenti

## Soluzione Odierna
---
>[!info] Segmentazione e Paginazione
>È possibile usare i metodi di ***segmentazione*** e ***paginazione*** *combinati*
>Ogni **segmento** è diviso in **pagine** che vengono allocate in **frame** liberi
>>[!caution] Requisiti Hardware
>> La `MMU` deve avere sia il **supporto** per la *segmentazione* sia per la *paginazione*

>[!done] Benefici
>Si uniscono i benefici delle due soluzioni:
>- **Segmentazione** -> Condivisione e Protezione
>- **Paginazione** -> No [[#^f4efb4|frammentazione esterna]]

## Memoria Virtuale
---
>[!definizione] Definizione
>Tecnica che permette l'*esecuzione* di processi che ***non*** sono ***completamente in memoria***
>- Permette di eseguire in concorrenza processi che hanno necessità di *memoria maggiore di quella disponibile*
>
>>[!warning] Tecnica che può diminuire le prestazioni se usata nel modo sbagliato

### Funzionamento
> Ogni processo ha accesso ad uno ***spazio di indirizzamento virtuale*** che può essere più grande di quello fisico

>[!note] Indirizzi Virtuali
>Possono essere mappati su ***indirizzi fisici*** della *memoria centrale* oppure mappati su *memoria secondaria*

In caso di *accesso* ad indirizzi virtuali mappati in *memoria secondaria*:
- I dati associati vengono ***trasferiti*** in memoria principale
- Se la memoria è piena, si ***sposta*** in memoria secondaria i dati contenuti in ***memoria principale***

### Meccanismi
>[!info] Demand Paging
>Si utilizza la ***tecnica della paginazione***, ammettendo che alcune pagine possano essere in *memoria secondaria*

Nella tabella delle pagine, si aggiungerà un `BIT` (`v`, ***valid***) che indica se la pagina è presente in *memoria centrale* o no

>Quando un processo tenta di accedere ad una pagina ***non in memoria***

Il processore genera un *trap* (***page fault***)
- Un componente del sistema operativo (***pager***) si occupa di **caricare** la pagina mancante in memoria, e di **aggiornare** di conseguenza la *tabellla*

#### Meccanismi di Rimpiazzo
>[!info] Algoritmi di Sostituzione
>In mancanza di frame liberi, bisogna applicare degli *algoritmi* per decidere quale pagina "***sostituire***"

##### Demand Paging
- **Individua** la pagina in memoria secondaria
- Individua un **frame libero**
- Se non esiste
	- Chiama l'*algoritmo di rimpiazzamento*
	- Aggiorna la tabella delle pagine (modifica della *pagina da sostituire*)
	- Aggiornare la pagina "***vittima***" sul disco
	- Aggiorna la *tabella dei frame*
- Aggiorna la *tabella dei frame*
- **Leggi** la pagina da *disco*
- Aggiorna la tabella delle pagine
- Riattiva il processo

#### Algoritmi di Rimpiazzamento
>[!abstract] Obbiettivi
>***Minimizzare*** il numero di *page fault*

##### FIFO
>[!definizione] Descrizione
>Se c'è necessità di liberare un frame in memoria viene individuato come "*vittima*" il frame che fu per ***primo caricato in memoria***

>[!done] Vantaggi

- Semplice

>[!fail] Svantaggi

- Vengono talvolta scaricate pagine che sono sempre utilizzate

>[!tldr] Anomalia di Belady
>Non è detto che *aumentando il numero di frame*, il *numero di page fault* ***diminuisca***

##### Algoritmo MIN
>[!definizione] Descrizione
>Selezione come pagina "*vittima*" una pagina che non sarà più acceduta o che non verrà acceduta nel futuro più lontano

>[!done] Vantaggi

- Algoritmo ottimale perché fornisce il ***minimo numero di page fault***

>[!fail] Svantaggi

- Algoritmo solo teorico: richiede la ***conoscenza dei riferimenti futuri*** del programma

##### Algoritmo LRU
>[!definizione] Descrizione
>Selezione come pagina "*vittima*" una pagina che è stata usata ***meno recentemente*** in passato (***least recently used***)

[[Cache#Tecniche di Gestione|Least Recently Used]]

>[!warning] Necessario uno specifico supporto hardware 

###### Reference Bit
> Tutte le volte che una pagine è acceduta, il reference bit associato alla pagina viene aggiornato a $1$

Periodicamente è possibile osservare quali ***pagine sono state accedute*** e non, osservando i ***reference bit***

>[!abstract] Meccanismo
>Quando bisogna *sostituire una pagina*, viene scansionata la [[#Page Table]]:
>Se la pagina scansionata risiede nella `RAM`:
>- Se il **reference** `BIT` è uguale a $1$, viene **impostato** a $0$
>- Se il **reference** `BIT` è uguale a $0$, viene **rimossa** la pagina

Non conosciamo l'*ordine* in cui sono state usate
- Possiamo usare queste informazioni per *approssimare* l'algoritmo `LRU`
### Swapper
>[!definizione] Swap
> Con questo termine si intende l'azione di ***copiare l'intera area di memoria*** usata da un processo
> - Memoria secondaria -> Memoria principale (***swap-in***)
> - Memoria principale -> Memoria secondaria (***swap-out***)

> Obsoleto

### Trashing
>[!definizione] Definizione
>Un processo si dice che è in ***trashing*** quando spende più tempo per la paginazione che per l'esecuzione

>Si ha trashing se:

- Diversi processi tendono a "*rubarsi i frame*"
- Non si riescono a tenere in memoria frame utili a breve termine
	- Generando ***page fault ogni pochi passi***


### Working Set
>[!definizione] Definizione
>Si definisce ***working set*** di *finestra* $\Delta$ l'insieme delle pagine accedute nei più recenti $\Delta$ riferimenti

> È una rappresentazione approssimata del concetto di località

>[!note] $\Delta$ Troppo piccolo
>Si rischia di ***considerare non più utile*** ciò che in realtà serve

>[!asd] $\Delta$ Troppo grande
>Si ***considera utile*** anche ciò che ***non serve*** più

Con una ***ampiezza ben calcolata***, il *working set* è una buona approssimazione dell'insieme delle *pagine* "*utili*"

>[!abstract] Proprietà
>Sommando l'ampiezza di ***tutti i working set*** dei processi attivi, il valore deve essere *minore* del numero di **frame disponibili**
>Altrimenti il sistema è in ***trashing***

