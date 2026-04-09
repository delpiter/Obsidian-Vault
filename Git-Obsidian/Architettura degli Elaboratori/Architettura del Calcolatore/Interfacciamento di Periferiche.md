>*L'interfacciamento "intelligente" di periferiche richiede l'implementazione di alcune tecniche che permettono di massimizzare l'efficienza del sistema*

>[!example] Obbiettivi

- *Evitare* che una periferica come un disco fisico che deve trasferire in memori $1Mb$ di dati ***tenga impegnata la `CPU` durante il trasferimento*** 
- *Evitare* di mantenere la `CPU` ***costantemente impegnata*** nel monitorare una o più *periferiche* che devono compiere un certo lavoro
- Pilotare tramite la `CPU` dispositivi esterni "***lenti***" come schede $I /O$ o dispositivi seriali

## DMA
---
>[!info] *D*irect *M*emory *A*ccess
>La tecnica del `DMA` consente il *trasferimento di blocchi dati*, anche di notevoli dimensioni, tra la memoria e le periferiche ***senza richiedere l'intervento*** della `CPU`

A tal fine è necessario disporre di un circuito denominato ***controllore `DMA`*** che governa il funzionamento

### Funzionamento
>*Il controllore `DMA` ha al suo interno $4$ **registri**, che vengono inizialmente caricati dal software attraverso la `CPU`*

Il ***Primo registro***:
- Contiene l'***indirizzo iniziale di memoria*** dal quale *leggere o scrivere*

Il ***Secondo registro***:
- Indica quanti `BYTE` o parole *devono essere trasferiti*

Il ***Terzo registro***:
- Specifica il ***numero di identificazione del dispositivo*** o l'indirizzo dello spazio di $I /O$ da usare

Il ***Quarto registro***:
- Indica se i dati vanno *letti o scritti* dal/sul ***dispositivo***

![[attachements/Direct Memory Acces.png]]

A questo punto la `CPU` da il ***via all'operazione*** di trasferimento
- Il controllore usa il `BUS` per *leggere i valori* dal dispositivo e *scriverli in memoria*
- Il controllore agisce come [[BUS dei Calcolatori#Master e Slave|Master]] del `BUS` ed è in grado di ***pilotare le linee necessarie***

>[!done] Durante il trasferimento la `CPU` è rimasta libera

## Polling e Interrupt
---
### Polling
>[!info] Definizione
>Il ***polling*** è la tecnica più elementare per far sì che la [[La CPU|CPU]] sia ***costantemente informata*** sullo ***stato di una periferica***
>- È come una interrogazione periodica della periferica

>[!fail] Ciò implica la necessità di:
>- Sprecare ***preziosi cicli*** per l'*interrogazione periodica*
>- Scrivere ***codice molto più complesso***, decine di periferiche devono essere gestite dalla stessa `CPU`

### Interrupt
>[!info] Definizione
>Attraverso la tecnica dell'***interrupt*** una periferica può *inviare un segnale elettrico* su una determinata linea della `CPU` (`INT`) per ***segnalare un determinato evento***
>La `CPU` può decidere di ***accettare o meno l'interruzione*** ed ***eseguire o meno la richiesta***

Data la presenza nel sistema di *diverse periferiche*:
- Diversi *interrupt* potrebbero essere ***scatenati contemporaneamente***

>[!done] Occorre un sistema di arbitraggio basato su priorità

- Simile a quello dei [[BUS dei Calcolatori#Arbitraggio del BUS|BUS]]

#### Funzionamento 
I primi `PC` utilizzavano un *chip* che si interponeva tra la `CPU` e le linee di richiesta interrupt ***provenienti dalle periferiche***

![[attachements/Interrupt Chip.png]]
- Quando un dispositivo richiede interrupt è sufficiente che ***attivi la propria linea*** `IRx`
- Quando vengono attivate una o più linee il controllore ***attiva la linea*** `INT` della `CPU`
- Quando la `CPU` è in grado di accettare l'***interrupt*** lo segnala attraverso la linea `INTA`:
	- ***Int***errupt ***A***cknowledge
- Il controllore invia alla `CPU` ***informazioni circa la periferica*** con priorità più alta che ha fatto richiesta
- L'hardware della `CPU` utilizza questa informazione come ***offset di una tabella*** di puntatori, chiamati ***interrupt vector***, per trovare l'indirizzo della *funzione da eseguire* in risposta all'*interrupt*
![[attachements/Interrupt Vector.png]]