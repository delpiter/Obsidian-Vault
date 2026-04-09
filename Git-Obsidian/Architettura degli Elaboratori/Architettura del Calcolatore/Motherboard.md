>[!info] Scheda Madre
>La *scheda madre* (***motherboard***) è una *scheda elettronica* che raccoglie in sé tutta la *circuiteria* e i *collegamenti di interfaccia* tra i vari componenti interni principali del `PC`

![[attachements/Motherboard.png]]
## Contenuti Motherboard
---
>[!done] CPU Socket

Il ***socket*** è dove risiede la [[La CPU|CPU]], ne esistono di diversi [[../Algebra di Bool e Logica Digitale/Circuiti Digitali#Tipi di Package|tipi]]:
I più usati al giorno d'oggi sono:
- `LGA`
	- I pin non sono sulla `CPU` ma risiedono all'interno del ***socket*** ($\text{LGA }1200$, $AM5$)
		- Tutte le `CPU` di ultima generazione sono di questo tipo
- `PGA`
	- I pin risiedono sulla `CPU`, il ***socket*** è formato da una serie di *fori* ($AM 4$)

>[!caution] `BUS` Interno

Il [[BUS dei Calcolatori#BUS|BUS]] è la via principale per lo *scambio di informazioni* tra i vari **dispositivi**
- Ci possono essere più `BUS` differenziati in base alla ***velocità di comunicazione***
	- Ormai è usato solamente il `BUS` [[BUS dei Calcolatori#PCI-Express|PCI-e]]

>[!abstract] Slot di Espansione

Si tratta di porte verso i `BUS` interni progettate per permettere di collegare alla *scheda madre* altre ***schede di espansione***

>[!abstract] Slot per moduli *RAM*

Solitamente posizionati a *destra del socket*
- Sono presenti dai $2$ ai $4$ slot `DIMM` per i banchi di [[Organizzazione della Memoria#Memoria Principale|RAM]] (motherboard per *consumatori comuni*)

>[!todo] Dispositivi $I /O$

Sono presenti nella *motherboard* i controllori dei dispositivi $I / O$  **fondamentali**:
- [[Organizzazione della Memoria#Serial ATA|SATA]]
- [[Organizzazione della Memoria#Dischi Magnetici|HDD]]
- [[Organizzazione della Memoria#Dischi Ottici|CD e DVD]]

>[!todo] Connettori per ulteriori dispositivi $I /O$

Al fine di semplificare la ***comunicazione*** tra calcolatori e dispositivi $I/O$ sono stati definiti alcuni ***protocolli standard*** per la loro connessione:
- [[BUS dei Calcolatori#USB|USB]]
- *Ethernet*
- Etc...

>[!tip] Chipset

![[../../Definizioni/Definizioni_Architettura#Chipset]]

In passato il chipset era diviso in due per problemi di velocità delle periferiche:
- ***Northbridge***
	- Gestiva le periferiche più veloci come la ***scheda grafica***
- ***Southbridge***
	- Gestiva le periferiche più lente come ***dischi magnetici*** e ***SATA***