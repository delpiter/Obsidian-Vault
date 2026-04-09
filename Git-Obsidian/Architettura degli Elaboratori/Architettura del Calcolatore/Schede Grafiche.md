>*Il compito della scheda grafica è quello di tradurre la rappresentazione dell'immagine prodotta dal processore in un formato visualizzabile dal monitor*


![[attachements/gpu.png]]
>[!info] GPU
>***G***raphical ***P***rocessing ***U***nit
>Processore *secondario*, inserito nelle *schede grafiche*, creato per ***limitare lo spreco di tempo*** di [[La CPU|CPU]]
>La `GPU` può essere utilizzata sia per la grafica `3D` sia per la grafica [[../../Definizioni/Definizioni_Architettura#Raster Graphics|raster]]
>La `CPU` del calcolatore non calcola più la posizione e il colore di tutti i `PIXEL`, ma invia un comando alla `GPU` indicandogli cosa ***deve essere disegnato***

^985740

- Quando i Monitor erano basati su ***tubo catodico*** (`CRT`), i loro segnali di ingresso erano analogici
	- La *scheda grafica* aveva il compito di convertire la rappresentazione digitale dell'immagine in ***segnali analogici***
	- La traduzione vera e propria del segnale è realizzata dal `RAMDAC`
		- ***R***andom ***A***ccess ***M***emory ***D***igital ***A***nalog ***C***onverter

## Formati Output
---
>*Oggi tutti i monitor sono LCD e prevedono un input digitale, quindi il ruolo della scheda grafica non è più quello di tradurre il segnale da digitale ad analogico*

>[!abstract] Ruolo della scheda
>- ***Adattare*** l'immagine adeguando *colori* e *risoluzione*
>- Mettere a disposizione una ***memoria locale*** da utilizzare come *buffer*
>- Supportare l'accelerazione grafica, es. `3D`

### Principali formati
>[!tip] VGA
>***V***ideo ***G***raphics ***A***rray
>Standard analogico progettato per monitor a tubo catodico
>Utilizzato per compatibilità anche da diversi monitor `LCD`
>>[!fail] Diversi problemi di rumore elettrico e distorsione immagine

>[!tldr] DVI
>***D***igital ***V***isual ***I***nterface
>Introdotto con i monitor `LCD`
>Risolve i problemi del `VGA` facendo corrispondere a ogni `PIXEL` dell'output un `PIXEL` dello schermo

>[!tip] HDMI
>***H***igh ***D***efinition ***M***ultimedia ***I***nterface
>Questo standard ha come obbiettivo la *sostituzione degli standard precedenti*.
>È in grado di trasportare anche ***dati audio***

>[!tldr] DP
>***D***isplay ***P***ort
>Standard utilizzato principalmente per collegare una ***sorgente video digitale*** a un ***monitor***
>Può trasportare anche *audio* e *altri tipi di dato*


>[!warning] Attenzione
>Non utilizzare un collegamento `VGA` quando è disponibile un altro collegamento
>Con un monitor `LCD` che nasce come digitale, richiederebbe una doppia conversione
>- Da *digitale* ad *analogico*, poi da *analogico* di nuovo a *digitale*
>Con rilevante perdita di qualità

## Risoluzioni
---
>[!info] Definizione
>La risoluzione è la ***dimensione*** della griglia di `PIXEL`
>Determina la ***definizione dell'immagine***

### Risoluzioni Tipiche
| Risoluzione       | N Pixel     | Aspect Ration |
| ----------------- | ----------- | ------------- |
| $320\times 200$   | $64.000$    | $8:5$         |
| $640\times 480$   | $307.000$   | $4:3$         |
| $800\times 600$   | $480.000$   | $4:3$         |
| $1024\times 768$  | $786.432$   | $4:3$         |
| $1280\times 1024$ | $1.310.720$ | $5:4$         |
| $1600\times 1200$ | $1.920.000$ | $4:3$         |
| $1920\times 1080$ | $2.073.600$ | $16:9$        |
- Formato tipico al giorno d'oggi:
	- $16:9$

### Profondità del Colore
>[!info] Colore del `PIXEL`
>La ***profondità del colore*** dei `PIXEL` indica il numero di `BIT` utilizzati per codificare il ***colore*** di ogni singolo `PIXEL`

| Profondità | N Colori     | N Byte | Nome               |
| ---------- | ------------ | ------ | ------------------ |
| $4$-`BIT`  | $16$         | $0.5$  | Standard `VGA`     |
| $8$-`BIT`  | $256$        | $1$    | $256$-Color Mode   |
| $16$-`BIT` | $65.536$     | $2$    | High Color         |
| $24$-`BIT` | $16.777.216$ | $3$    | True Color (`RGB`) |

![[attachements/Resolutions.png]]

### Interfaccia

>[!warning] Problema

- Al crescere del livello di ***definizione*** delle immagini cresce la quantità di ***memoria richiesta*** per rappresentare l'immagine.
>[!fail] Il flusso di dati dalla memoria alla `GPU` rischia di saturare la capacità del `BUS`


Per questo è necessario, oltre ad aumentare le dimensioni della ***memoria dedicata***
- Ampliare la ***banda di trasmissione*** del `BUS` o inserire `BUS` o porte dedicate

>[!info] AGP
>***A***ccelerated ***G***raphic ***P***ort
>Utilizzando una porta `AGP` la `GPU` utilizza tramite un ***accesso diretto***, parte della memoria centrale

>[!info] PCIe
>***P***eripheral ***C***omponent ***I***nterconnect ***e***xpress
>Stessa interfaccia usata nelle [[Organizzazione della Memoria#Interfacce PCI|SSD NVME]] 
>Sostituisce `AGP` come interfaccia di connessione delle *schede grafiche* in quanto offre una ***larghezza di banda maggiore***

## Accelerazione Grafica
---
>*Per poter sfruttare la capacità di accelerazione delle schede grafiche è necessario che le applicazioni conoscano le funzioni da esse implementate*

>[!info] Librerie Standard
>A causa dell'elevato numero e delle differenze fra le schede grafiche è stato necessario implementare delle librerie standard, come:
>- ***OpenGL*** $\to$ *Cross Platform* e *Cross Language* `API`
>- ***DirectX11/12*** $\to$ `API` per Windows
>- ***Cuda***, ***NVAPI*** $\to$ `API` per schede Nvidia 
>- ***Vulkan*** $\to$ `API` per schede AMD
