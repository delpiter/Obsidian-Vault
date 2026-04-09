## Intel Core i7
---
>[!abstract] Architettura
>Esternamente si presenta come una `CPU` [[Tipologie di Architetture#CISC|CISC]] a $32 /64$ `BIT` basato sullo stesso ***ISA*** dei modelli precedenti
>Infatti, in disaccordo con i principi [[Tipologie di Architetture#RISC|RISC]]:
>- Le istruzioni sono ***molte e complesse***
>- I registri visibili sono solo 8
>- La ***lunghezza delle istruzioni*** è variabile da $1$ a $17$ `Byte`
>>[!done] Architettura "Interna"
>>All'interno, però, contiene un nucleo `RISC` moderno che fa largo uso di [[Pipelining]] e [[Pipelining#Architetture Superscalari|architetture superscalari]]
>
>Di seguito l'architettura "***Sandy Bridge***", realizzata a partire dal 2011, contiene un numero di core variabili tra 2 e 6

![[attachements/Sandy-Bridge.png]]
>*Schema dell'architettura di un singolo core*

>[!info] Memory Subsystem
>Include la [[../Architettura del Calcolatore/Cache]] privata $L_{2}$ unificata, dati e istruzioni insieme
>- In caso di *miss*, si interfaccia con la cache $L_{3}$ condivisa dai diversi core

>[!abstract] Front End
>Ha il compito di prelevare le istruzioni dalla cache $L_{1}$ le istruzioni e di decodificarle nell'ordine del programma
>La decodifica scompone ciascuna istruzione `CISC` in una sequenza di micro-operazioni `RISC`, successivamente eseguite dal cuore `RISC` del processore
>>[!Micro-op Cache]
>>Piccola memoria che contiene la decomposizione di una istruzione complessa, nel caso venga usata spesso
>
>>[!example] Predizione di Salto
>>In questo livello fanno parte anche le [[Predizione di Salto|predizioni di salto dinamico/statico]] i cui dettagli non sono noti

>[!info] Out-Of-Order Control
> Le micro operazioni sono trasferite dalla micro-op cache allo schedulatore
>>[!tldr] Scheduler/Renaming
>>Lo scheduler è in grado di ***eseguire le operazioni fuori ordine***
>>Renaming, assegna i registri ***accessibili al programmatore ai registri fisici*** (*molti di più*)
>
>>[!caution] Retirement Unit
>>L'unità di ritiro garantisce che i risultati prodotti siano equivalenti rispetto a un'esecuzione in ordine

![[attachements/Corei7DataPath.png]]
>*Una vista semplificata del datapath di un core i7*

### Famiglie Intel x86
>[!info] Linea Core
>`CPU` destinate a computer di fascia medio-alta e workstation
>- *Core i3*, *Core i5*, *Core i7*, *Core i9*

>[!abstract] Linea Xeon
>`CPU` destinate a server di fascia alta, derivate dalla linea core ma con caratteristiche più avanzate, come il supporto per memoria `ECC` e numero di core più alto

>[!caution] Linea Atom
>`CPU` per dispositivi ultra-portatili, come Notebook e schede per sistemi embedded, caratterizzate da piccole dimensioni e consumi molto contenuti

>[!Example] Linea Pentium/Celeron:
>`CPU` destinate a computer di fascia medio-bassa

## AMD
---
>[!info] *A*dvanced *M*icro *D*evices
>`AMD` è il secondo produttore mondiale di microprocessori
>In competizione con intel da 1975, quando `AMD` iniziò a produrre processori $\text{x}86$-*compatibili*
>>[!done] Successi di AMD
>>- **Atlon 64**
>>	- Primo processore desktop con supporto $64$ `BIT` della famiglia $\text{x}86$
>>- **Opteron**
>>	- Processore destinato alla fascia server
>>- **Phenom** (2007)
>>- ***APU***
>>	- ***A***ccelerated ***P***rocess ***U***nit, `CPU` e `GPU` integrate nello stesso chip, usate in console come *Ps4 e Xbox One*
>>- Serie ***Zen***
>>	- Prime `CPU` a $7nm$. Architettura di processori odierni (***Ryzen***)

## CPU RISC non x86 per Server
---
>[!Abstract] SPARC
>***S***calable ***P***rocessor ***ARC***hitecture
>È il nome di un'architettura "aperta" e non proprietaria per microprocessori `RISC`- [[../../Definizioni/Definizioni_Architettura#Ordinamento dei `BYTE`|Big Endian]]
>Nel corso degli anni (1985-2010) l'architettura ha subito diverse revisioni
>- Versione 9 introduce la gestione dei dati a $64$ `BIT`
>
>>[!fail] Progetto Abbandonato

>[!info] Power
>Architettura di microprocessori `RISC` $32$ e $64$ `BIT` creata da `IBM`
>Nel 91' l'alleanza Apple-IBM-Motorola ne derivò un'implementazione di successo nota come ***PowerPC***
>Apple adottò *PowerPC* per il suo ***Machintosh***
>*PowerPC* negli anni 90 era l'***architettura più potente*** per personal computer
>>[!fail] PowerPC non resse il confronto con la concorrenza, soprattutto per non compatibilità con $\text{x}86$
>
>>[!tldr] Utilizzata in seguito come base per altri progetti non $\text{x}86$ tra cui il processore dell'Xbox 360

>[!abstract] Itanium
>Architettura `RISC` nativa a $64$ `BIT` con ***ISA IA-64*** progettata da *intel* e *HP*
>Il progetto eredita soluzioni innovative implementate nell'architettura ***Alpha***
>>[!fail] Architettura abbandonata nel 2019

### IA-64
>*Di seguito alcune caratteristiche di questi ISA*

>[!abstract] Parallelismo a livello di Istruzione
>***Esplicito nelle istruzioni macchina*** piuttosto che determinato dal processore durante l'esecuzione
>Questo tipo di parallelismo è noto come `EPIC`
>>[!example] Explicit Parallel Instruction Computing
>>In questo caso è il compilatore a dover capire quali istruzioni possono essere eseguite in parallelo
>
>Pertanto i processori `EPIC` non necessitano di circuiti complessi per l'[[Predizione di Salto#Esecuzione Fuori Ordine|esecuzione fuori sequenza]]

>[!caution] Previsti fino a 256 registri a $64$ `BIT`
>128 interi + 128 in virgola mobile

>[!info] Più pipeline parallele
>Il [[Pipelining]] può essere gestito a livello software

>[!abstract] Utilizzo di predicati di salto
>Come `CMOV`, si realizza aggiungendo un ***registro predicato*** davanti alle istruzioni
>Durante l'esecuzione se il valore del predicato è `FALSE` l'istruzione non viene eseguite
>- Molto ***dannoso per il pipelining***

## CPU per Sistemi Embedded
---
>[!info] *ARM*
>***A***dvanced ***R***ISC ***M***achine
>Indica una famiglia di processori `RISC` a $32$ `BIT` sviluppata dall'azienda inglese "***ARM Holdings***" che detiene la proprietà intellettuale di molti "*core*" di `CPU` embedded
>*ARM* ***non produce direttamente hardware***, ma vende ***licenze di produzione*** dei suoi core a grandi produttori di `CPU`
>Si tratta di `CPU` `RISC` di disegno architetturale semplice e pulito ***caratterizzate da basso consumo***

### Core Cortex
>*Presentati nel 2005 come evoluzione futura ARM*

>[!abstract] Cortex-M
>*M* $\to$ Microcontroller
>Naturale evoluzione di `ARM 7` e `ARM 9` (core classici ad *aritmetica intera*) per device embedded senza grandi necessità di performance

>[!Info] Cortex-R
>*R*$\to$ Real-Time
>Per sistemi embedded con requisiti prestazionali ***medio-elevati***

>[!tldr] Cortex-A
>*A*$\to$ Applications
>Per sistemi con requisiti prestazionali ***elevati*** come smartphone e tablet
>Include ***floating point*** e `SIMD`
>>[!example] Cortex A7
>>Fino s 4 core, ciascuno con una pipeline parzialmente superscalare
>>Scelto come ***soc*** per ***Raspberry Pi 2***
>
>>[!caution] Cortex A72
>>Fino a 4 core per [[../../Definizioni/Definizioni_Architettura#Cluster|Cluster]], architettura superscalare a tre vie e ***predizione di salto sofisticata***
>

### ISA ARM
>*Come da filosofia `RISC`, l'**ISA** `ARM` ha:*

>[!tldr] Un ***insieme ridotto di istruzioni*** (100 o meno)

>[!info] Le istruzioni operano unicamente su registri
>Per accedere alla memoria si usano specifiche istruzioni di ***load e store***

>[!tip] Esecuzione Condizionale
>La maggior parte delle istruzioni permette ***esecuzione condizionale***
 
>[[../../Definizioni/Definizioni_Architettura#Ordinamento dei `BYTE`|endianess]]"
>È possibile operare in ***little endian o big endian***

### Apple M1
>[!info] M1
>L'`M1` è il primo `SoC` progettato da Apple per ***Mac*** e ***iPad Pro***
>Il chip è prodotto con tecnologia $5nm$ e contiene $16$ miliardi di transistor
>È un progetto di grande successo capace di unire elevate prestazioni a consumi ridotti
>>[!tip] Struttura
>>Contiene 8 core
>>- 4 sono ad ***elevate prestazioni*** e maggior consumo
>>- 4 sono a ***prestazioni e consumo ridotti***
>
>>[!example] Altri chip integrati
>>1. Una `GPU` a 8 core
>>2. Un Neural Processing Unit a $16$ core per accelerare reti neurali
>>3. `UMA`, una sorta di memoria cache $L_{3}$ di grande capacità, su questa memoria, `CPU`, `GPU`, `NPU` possono condividere i dati senza copie/spostamenti fra memorie diverse
>

![[attachements/M1-Architecture.png]]