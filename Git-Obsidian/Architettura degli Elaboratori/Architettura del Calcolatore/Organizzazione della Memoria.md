## Memoria Principale
---
>[!info] `RAM`
>La `RAM`, ***R***andom ***A***ccess ***M***emory, o *memoria principale* è quella parte del calcolatore preposta a **immagazzinare** i *programmi in esecuzione* e i relativi *dati*
>Il termine `RAM` significa 
>- "*memoria il cui accesso può avvenire in modo casuale e non obbligatoriamente in modo sequenziale*"
>
>>[!done] Tipi
>>La `RAM` può essere **statica** (`SRAM`) o **dinamica** (`DRAM`)
>>- entrambe le [[Le Memorie|memorie]] sono di tipo ***volatile***

La `RAM` si compone di un ***numero di celle***, ognuna delle quali è in grado di memorizzare una *parte delle informazioni*
- Ogni *cella* è associata ad un ***indirizzo*** che la identifica univocamente

 Tutte le *celle* di una memoria mantengono lo ***stesso numero*** di `BIT`
 - Il numero di `BIT` associato a un indirizzo è detto *word*
 - La dimensione minima è il `BYTE`
 - La dimensione della *word* determina anche le dimensioni dei ***registri*** e delle ***istruzioni***

>[!done] Indirizzamento

Gli indirizzi di memoria sono espressi tramite numeri binari:
- Se un indirizzo ha $m$ `BIT` il numero massimo di celle indirizzabili sarà $2^m$

### Assemblaggio
>*I **chip** di memoria non vengono venduti singolarmente ma sono normalmente organizzati su schede stampate*
>*Ogni scheda contiene generalmente da $8$ a $16$ **chip***

![[attachements/Ram Stick.png]]

 #### Tipi di Memoria Principale
>[!tldr] SIMM
>***S***ingle ***I***nline ***M***emory ***M***odule
>È un tipo di *banco di memoria* dove i ***contatti dorati*** si trovano solo su un lato della scheda

>[!summary] DIMM
>***D***ual ***I***nline ***M***emory ***M***odule
>È un tipo di *banco di memoria* dove i ***contatti dorati*** si trovano su entrambi i lati della scheda
>La velocità dipende dalla ***tipologia di memoria*** (`DDR`, `DDR2`, `DDR3`, `DDR4`, `DDR5`)

>[!tldr] SO-DIMM
>***S***mall ***O***utline ***DIMM***
>Sono ***DIMM*** a dimensioni ridotte usate in genere nei portatili

>[!summary] ECC-DIMM
>***E***rror ***C***orrecting ***C***ode ***DIMM***
>I moduli `ECC-DIMM` prevedono meccanismi di ***correzione di errore***.
>Per motivi di ***risparmio e bassa probabilità di errore***, questi chip non sono presenti su calcolatori ordinari
>>[!question] Probabilità di errore
>>Alcune ricerche hanno dimostrato che, anche se con probabilità ridicola, i ***raggi cosmici*** possono causare errori nei singoli `BIT` delle `RAM`

## ROM
---
>[!info] *R*ead *O*nly *M*emory
>Questo tipo di memoria ***non può essere cancellata o riscritta***.
>- Conserva il proprio valore anche se *non alimentata* (***non volatile***)
>
>Utilizzata solitamente per la ***memorizzazione permanente di programmi stabili***

>[!warning] Realizzazione

La realizzazione di `ROM` non può essere fatta nella pratica da aziende che *progettano circuiti*, in quanto richiede una particolare tecnica costruttiva (***mascheratura***)
- Pertanto è necessario operare ***direttamente sul chip di silicio*** per modificarne la struttura

La produzione di `ROM`, di conseguenza deve essere per forza appaltata a *grosse aziende produttrici di chip*
- È conveniente solo per grandi quantità di chip uguali

>[!tldr] Uso
>Inizialmente il [[../../Definizioni/Definizioni_Architettura#BIOS|BIOS]] dei `PC` era memorizzato su una memoria di questo tipo
>- Velocemente sostituita dalla `EPROM` e attualmente dalla memoria `FLASH`

### ROM Programmabili
>[!info] *P*rogrammable *ROM*
>`PROM`
>In fase di prototipazione di nuovi circuiti è molto più conveniente utilizzare circuiti `PROM` - Possono comunque essere scritti ***una sola volta***
>- La *scrittura* avviene attraverso ***segnali elettrici*** generati da apparecchiature di *basso costo* che operano ***bruciando dei fusibili***

### ROM Riprogrammabili
##### EPROM
>[!info] *E*rasable *PROM*
>Una `EPROM` è un particolare tipo di `PROM` che viene programmata analogamente alla `PROM`, ma il cui contenuto può essere cancellato con ***luce ultravioletta***
>- Con una esposizione di circa *15 minuti*
>E nuovamente riscritto utilizzando l'apposito programmatore

##### EEPROM
>[!info] *E*lecrically *EPROM*
>Una `EEPROM` è un particolare tipo di `EPROM` che può essere cancellata *elettricamente* in modo molto più veloce di una `EPROM`
>>[!tip] In-Circuit
>>La riprogrammazione può essere fatta "***in circuit***" ovvero ***senza smontare il chip dal circuito***

### FLASH
>[!info] Memorie *Flash*
>Questo tipo di memoria viene utilizzata oggigiorno in numerosi dispositivi ***mobili*** che necessitano di ***supporto di memorizzazione non volatile***.
>I *tempi di accesso* sono ***buoni*** e la memoria consente letture di singole parole.
>Come la `EEPROM` può essere riprogrammata ***in-circuit*** indirizzando, però, non una singola parola ma un intero "*blocco*" 
## Dischi Magnetici
---
>[!info] Hard Disk
>Un ***hard disk*** (***HD***) è un dispositivo ***elettro-meccanico*** per la conservazione di informazioni sotto forma *magnetica*, su supporto rotante a forma di ***piatto***, su cui agiscono delle ***testine*** di *lettura/scrittura*
>[[Le Memorie|Memoria]] di tipo ***persistente*** e ***on line***

![[attachements/HDD.png]]
### Testina
>[!tldr] La testina di lettura/scrittura
>La ***testina*** di un disco, contenente un induttore, è sospesa sopra la superficie e viene sostenuta da un cuscino ad area

![[attachements/HDD-Precision.png]]

### Scrittura
>[!info] Scrittura
>Quando la corrente **negativa** o **positiva** passa *attraverso la testina*, viene ***magnetizzata*** la superficie appena sotto la testina e le *particelle magnetiche si allineano* verso sinistra o destra a seconda della **polarizzazione della corrente**

### Lettura
>[!info] Lettura
>Quando una testina passa sopra ***un'area magnetizzata***, viene *indotta* una *corrente* **positiva** o **negativa** nella testina, e ciò permette di rileggere i `BIT` memorizzati precedentemente

### Struttura del Disco
>*Il disco rigido è formato da diverse parti, tra cui le principali:*


![[attachements/HDD-Parts.png]]

>[!tldr] Traccia
>La ***traccia*** è una sequenza circolare di `BIT`

>[!tip] Settore
>*Porzione* di traccia di ***dimensione fissa***
>Ogni settore è composto da:
>>[!info] Preambolo
>>Il ***preambolo*** è necessario alla testina per ***sincronizzarsi*** prima della *lettura/scrittura*
>
>>[!example] Dati
>>I ***dati*** sono l'insieme dei `BYTE` memorizzati nel *settore*, normalmente $512$
>
>>[!info] Codice di Correzione Errori
>>Il [[Correzione di Errori|Codice di Correzione Errori]] è utilizzato per individuare e correggere eventuali errori

![[attachements/HDD-Sector.png]]
>[!tldr] Cilindro
>Il ***cilindro*** è l'*insieme delle tracce* in una data posizione radiale
>Il cilindro è un concetto ***virtuale***, non esiste fisicamente un *cilindro*
>>[!question] Perché Cilindro?
>>Quando una testina legge nel disco, *ogni testina* di *ogni piatto* viene impostata alla ***stessa distanza dal centro*** di ogni piatto
>>"*Cilindro*", poiché per leggere un piatto la testina si mette a posto per leggere tutti i dischi a quella stessa distanza, formando una sorta di **cilindro**

Prima di poter leggere o scrivere la suddetta struttura (*tracce*, *settori*) deve ***essere creata***
- Questa operazione viene detta ***formattazione***

### Capacità
>*La capacità di un hard disk è in gran parte definita dalla densità di registrazione*

>[!info] Densità Lineare
>La densità lineare è limitata dalla difficoltà di individuare le variazione del campo magnetico sulla superficie del disco

>[!info] Densità di Area
>La densità del primo hard disk era di circa $2Kbits/in^2$
>Ora si sono superati i $1.3 Tbits/in^2$

### Prestazioni
>*Le prestazioni di un hard disk dipendono da diversi fattori*

>[!tip] Seek Time
>Il ***seek time*** è il tempo necessario per spostare le *testine* sul *cilindro* desiderato
>I *costruttori* del disco forniscono, in genere:
>>[!example] Average Seek
>>`8-10 ms`
>
>>[!done] Track-to-Track
>>`1 ms`
>
>>[!Full Stroke]
>>`15-20 ms`

>[!tip] Latency Time
>La ***latency time*** rappresenta il tempo necessario affinché il settore interessato all'operazione ***passi sotto la testina***.
>Questo fattore è definito dalla velocità di rotazione del disco che varia da $3.600$ a $15.000$ `RPM` (***R***otation ***P***er ***M***inute)
>- Con un *hard disk* moderno il latency time richiede ***qualche microsecondo***

## Solid State Drive
---
>[!info] Descrizione
>Si tratta di dispositivi *completamente elettronici*, normalmente basati su ***memorie flash***, e senza ***nessuna parte in movimento***
>*Ridotti* notevolmente i ***tempi*** di *lettura* e *scrittura*

![[attachements/SSD.jpg]]

>[!done] Pro

***Tempo di accesso***
- Eliminata la *costante di movimento*
- Tempo di accesso **inferiore** a 100 microsecondi, dalle 30 alle 100 volte più performanti di un hard disk

***Maggiore velocità di trasferimento di dati***
- Oltre i $7 Gb/sec$

***Minore possibilità di rottura e maggiore durata***
- Tasso di rottura inferiore agli *hard disk* (*molto fragili*)

***Rumorosità assente***

***Minori consumi***

***Maggiore capacità***
- Disponibili `SSD` da $100Tb$

>[!fail] Contro

***Maggiore prezzo per*** `BIT`
- Pari a circa *quattro volte* il ***costo*** di un disco tradizionale

***Possibile minore durata dell'unità***
- Il massimo numero di riscritture dello stesso `BIT` può andare da $3.000$ a $100.000$ cicli

## Interfacce
---
>*Esistono diversi tipi di interfacce di trasferimento di dati, implementate sui controller integrati del disco*

### IDE
>[!info] *I*ntegrated *D*rive *E*lectronix
>Interfaccia ormai ***obsoleta***
>È stata la tecnologia *più utilizzata* negli anni $'80$ 
>Il *controller integrato* indirizza i settori indicando:
>- Il numero di *testina* (4 `BIT`)
>- Il *settore* (6 `BIT`)
>- Il *cilindro* (10 `BIT`)
>

>[!done] Spazio Indirizzabile
>`512 BIT`$\times 2^4$ `BIT` $\times 2^6$ `BIT` $\times 2^{10}$ `BIT`


### EIDE
>[!info] *E*xtended *IDE*
>Supporta un diverso *schema di indirizzamento*, `LBA` (***L***ogical ***B***lock ***A***ddressing)
>Numera i **settori** da $0$ a $2^{28}-1$
>Sebbene sia necessario ***rimappare gli indirizzi*** in termini di settori, cilindri e testine, permette di ***aumentare lo spazio indirizzabile*** fino a $128 Gb\implies2^{28}\times2^9$ settori di $512$`BYTE`

#### Evoluzioni EIDE

>[!example] ATA-3
>***A***dvanced ***T***echnology ***A***ttachement

>[!example] ATAPI-4 ATAPI-5 ATAPI-6
>***ATA*** ***P***acket ***I***nterface
>Anche chiamate ***PATA***, ***P***arallel ***ATA***
>Velocità di *trasferimento dati* aumenta gradualmente fra le versioni
>***ATAPI-6***:
>- Indirizzi `LBA` passano a $48$ `BIT`, capacità massima aumentata fino a:
>$$2^{48}\times 2^9$$

>[!example] ATAPI-7
>Meglio nota come ***Serial ATA*** (`SATA`) rappresenta una rottura radicale con il passato
>Si passa da un *trasferimento parallelo* di $16$ o $32$ `BIT` per volta
>- Con cavi piatti a $40/80$ ***fili***
>
>Al ***trasferimento seriale*** di $1$ `BIT` per volta su un connettore a $7$ ***fili***

### Serial ATA
>[!info] SATA
>Denominato anche `SATA` è una vera e propria rivoluzione in quanto consente:
>- ***Velocità*** superiore fino a $600MB/sec$
>- Diminuzione di ***costo*** per cavi
>- Migliore ***ventilazione*** del `PC` e semplicità di montaggio
>- ***Hot Swap*** delle unità


![[attachements/SATA.jpg]]
### Interfacce PCI
>[!info] NVMe
>***N***on ***V***olatile ***M***emory ***e***xpress
>Progettate per sfruttare al massimo i vantaggi dei moderni `SSD`
>Velocità teorica di $64 Gbit/sec$ utilizzando 4 canali `PCIe`
>- ***P***eripheral ***C***omponent ***I***nterconnect ***E***xpress
>Possono avere la forma di una ***scheda di memoria*** collegata con un connettore `M.2`
>O sotto forma di un ***disco*** da `2.5` pollici collegato tramite connettore `U.2`

![[attachements/SSD-NVME.png]]

### SCSI e SAS
>[!info] SCSI
>***S***mall ***C***omputer ***S***ystem ***I***nterface (pronuncia ***SCASI***)
>Sviluppato *parallelamente* allo standard EIDE, destinato ai ***sistemi di fascia alta*** in ambito ***enterprise***
>La tecnologia di base dei dischi è la stessa.
>- Per utilizzare dischi `SCSI` è generalmente necessario utilizzare un ***controller aggiuntivo***


>[!info] SAS
>***S***erial ***A***ttatched ***S***CSI
>Analogamente al `PATA` anche `SCSI` si è evoluto verso un collegamento punto a punto di tipo seriale
>Non tanto differente in termini di ***prestazioni*** ma in termini di ***affidabilità***

## RAID
---
>*Creato per colmare il divario tra le prestazioni della `CPU` e quello dei dischi*

>[!info] RAID
>***R***edundant ***A***rray of ***I***ndependent ***D***isk
>Tecnologia di ***virtualizzazione dello storage*** che combina diversi ***dischi fisici*** in uno o più ***unità logiche***
>- Può essere gestito dal `SO` (*Software Raid*) o da un ***controller Hardware***
>- Appare al sistema come un ***disco unico***
>- Aumenta le prestazioni ***distribuendo i dati*** su più dischi a cui il controller accede in **parallelo**
>- Fornisce una modalità di ***backup e correzione di errori***
>- Permette il *funzionamento* anche se una unità ***non è attiva***

### Tipi di RAID
>[!abstract] RAID 0
>***Non Redundant Data Striping***
>Mette assieme 2 o più dischi

![[attachements/Raid0.png]]

>[!abstract] RAID 1
>***Redundant Data Striping***
>Esegue la Copia `BIT` a `BIT` di un disco in un altro

![[attachements/Raid1.png]]

>[!abstract] RAID 2
>***Data Striping at `BIT` Level***

![[attachements/Raid2.png]]

>[!abstract] RAID 3
>***Bit Interleaved Parity***

![[attachements/Raid3.png]]

>[!abstract] RAID 4
>***Block Interleaved Parity***


![[attachements/Raid4.png]]

>[!abstract] RAID 5
>***Block Interleaved Distributed Parity***

![[attachements/Raid5.png]]

## Dischi Ottici
---
>*I dischi ottici sono memorie di tipo persistente e off-line*
### CD
>[!info] Compact Disc
>I `CD` utilizzano un ***principio ottico*** per la memorizzazione persistente di informazioni
>Nati come supporto per la ***memorizzazione di musica***
>>[!abstract] Codifica
>>Le informazioni sono codificate per mezzo di *fori* (***Pit***) di $0.8$ micron di diametro alternati con *zone piane* (***Land***) lungo una ***unica spirale***
>>Un passaggio ***Pit-Land*** o ***Land-Pit*** codifica un $1$
>>L'***assenza di variazioni*** codifica lo $0$

![[attachements/CD.png]]

>[!abstract] Lettura
>Le informazioni sono lette tramite un ***raggio laser*** che viene *riflesso* diversamente al passaggio sui ***Pit*** e ***Land***


#### Produzione
I `CD` vengono prodotti utilizzando uno *stampo* ottenuto tramite ***erosione laser***.
- Su questo stampo verrà poi iniettata *resina liquida* che preserva gli incavi corrispondenti ai ***Pit***

Lungo la spirale, i dati sono memorizzati con la ***stessa densità***
- Il `CD` quindi deve ruotare con una ***velocità angolare non costante*** ($530$-$200$ giri al sec)
	- Mantenendo la medesima ***velocità lineare*** ($120cm/sec$) nelle diverse are del `CD`


### CD-ROM
>[!info] CD-Read Only Memory
>Utilizzano la tecnologia dei `CD` per memorizzare dati informatici

>[!fail] Problema: perdita di `BIT` durante la lettura

Al fine di evitare questo problema
- Ogni `BYTE` viene codificato da un ***simbolo*** di $14$ `BIT`
- Nei `BIT` in eccesso viene inserito un ***codice per la correzione dell'errore***

>[!abstract] Frame
>Un gruppo di $42$ **simboli** viene chiamato ***frame***
>Ogni *frame* contiene $192$ `BIT` di dati ($24$ `BYTE`) e $396$ `BIT` di *codice di correzione di errore*

>[!abstract] Settore
>Un gruppo di $98$ **frame** viene chiamato ***settore***
>Ogni *settore* inizia con un preambolo di $16$ `BYTE` che permette di *identificare il settore* e la *modalità di registrazione*

>*Esistono due modalità di registrazione*

>[!example] Modo $I$

- $16$ `BYTE` di preambolo $+2048$ `BYTE` di dati $+288$ `BYTE` di correzione di errori

![[attachements/CD-Sector.png]]


>[!example] Modo $II$

- $16$ `BYTE` di preambolo $+2336$ `BYTE` di dati
- Utilizzato da applicazioni che non richiedono controlli di correttezza come musica e video

### CD-R
>[!info] Compact Disk Recordables
>Svolgono le *stesse funzioni* del `CD-ROM` ma sono ***registrabili*** dagli utenti senza utilizzo dello stampo

- Diversamente dai `CD` la riflettività di ***pit*** e ***land*** viene ottenuta "*bruciando*" tramite un raggio laser uno strato di materiale colorato
	- Inserito tra il policarbonato e lo strato riflettente

![[attachements/CD-R.png]]

Lo standard `CD-R` prevede la possibilità di scrivere su un disco in modo ***incrementale***
- Un gruppo di ***settori*** consecutivi *scritti nello stesso momento* si chiama `CD-ROM tack`

Questa soluzione richiede la presenza di più `VTOC`
>[!info] VTOC
>***V***olume ***T***able ***O***f ***C***ontents
>Ne esiste una per ogni ***Track***
>In una `VTOC` è possibile inserire riferimenti alle `VTOC` precedenti
>- Il `SO` farà riferimento solo alla più recente

### DVD
>[!info] Digital Video Disk
>Nascono come supporto per la memorizzazione di ***video digitali***
>I `DVD` utilizzano lo stesso progetto dei `CD-ROM` inserendovi alcune innovazioni:
>1. ***Pit*** più piccoli
>2. ***Spirale*** più serrata
>3. ***Raggio laser*** rosso
>Permettono di memorizzare fino a $4.7GB$ ($133$ minuti di video digitale `MPEG-2`)

Lo **spazio** a disposizione non è ***mai sufficiente***
- Sono quindi stati introdotti *4 nuovi formati*

1. Lato Unico - Strato Unico $\to 4.7GB$
2. Lato Unico - Strato Doppio $\to 8.5GB$
3. Lato Doppio - Strato Unico $\to 9.5GB$
4. Lato Doppio - Strato Doppio $\to 17 GB$

La tecnologia a ***Doppio strato*** è ottenuta inserendo tra i due strati uno *strato semiriflettente*
- A seconda del punto su cui il laser è *messo a fuoco*, la ***riflessione*** avverrà da uno strato oppure l'altro

![[attachements/DVD.png]]

### Blue-Ray
>[!info] Blue Ray
>***Blue Ray*** è il nome della tecnologia progettata per sostituire i `DVD`
>Il nome deriva dall'uso di un ***laser blu*** e non più *rosso*
>- Avendo minore *lunghezza d'onda* consentiva di avere ***Pit*** e ***Land*** più piccoli
>
>Il primo apparecchio ad avere utilizzato *commercialmente* questa tecnologia fu la ***PlayStation 3***

Negli anni sono stati sviluppate diverse versioni di questa tecnologia
- Dischi in grado di memorizzare da $25GB$ a $200GB$
