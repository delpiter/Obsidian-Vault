## Scheduling
---
>Per rappresentare uno [[6 - Processi, Schedule e Thread#Schedule|schedule]] si utilizzano i diagrammi di Gantt

![[attachements/GanttDiagram.png]]
- Ogni *linea* rappresenta una *risorsa diversa*, in questo caso sarebbe un **processore con due core**

### Politiche di Scheduling
> Esistono due tipi di scheduler che si basano sugli eventi che possono causare un [[6 - Processi, Schedule e Thread#Mode Switching e Context Switching|Context Switch]]

>[!info] Cambio di Stato del Processo
>1.  Da **Running** a *Waiting*
>2. Da **Running** a *Ready*
>3. Da **Waiting** a *Ready*
 
>[!caution] Terminazione del Processo
>4. Quando il processo stesso **Termina** la propria esecuzione

#### Scheduler Non-Preemptive
>[!abstract] Definizione
>Uno scheduler ***Non-Preemptive*** è uno scheduler in cui il *context switch* avviene solamente nel caso in cui il processo **termina** o si mette in **attesa** di una *risorsa*
>- Va avanti finché non è forzato a fermarsi
>
>>[!done] Pro
>>Non richiede alcuni meccanismi hardware come timer programmabili
>>- Sono ***più semplici*** da progettare


#### Scheduler Preemptive
>[!hint] Definizione
>Uno scheduler ***Preemptive*** è uno scheduler in cui il *context switch* può avvenire in **qualsiasi condizione**
>- ***Terminazione*** del Processo
>- Il processo si mette in ***attesa*** di una risorsa
>- Il suo ***quanto di tempo*** termina
>- $\dots$
>
>>[!done] Pro
>>Permette di *utilizzare al meglio* le *risorse* del calcolatore

### Criteri di Scelta di uno Scheduler
> Ci sono delle *metriche fondamentali* per capire la bontà di una **tecnica di scheduling**

##### Criteri da Massimizzare

>[!info] Utilizzo della risorsa

>La *percentuale di tempo* in cui la `CPU` è occupata ad eseguire dei processi

>[!abstract] Throughput

>Numero di *processi completati* per unità di tempo
> - Dipende dalla *lunghezza* dei processi

##### Criteri da Minimizzare

>[!caution] Tempo di Turnaround

>Tempo che trascorre dalla **creazione** di un processo alla sua **terminazione**

>[!example] Tempo di Attesa

> Tempo **trascorso** da un processo nella coda **Ready**

>[!note] Tempo di Risposta

>Tempo trascorso fra *sottomissione* di un processo e il tempo di *prima esecuzione*

## Algoritmi di Scheduling
---
>Esistono una larga gamma di *algoritmi di scheduling*, di seguito alcuni:

### First Come First Served
>[!info] ***FCFS***
>È un algoritmo che esegue per *primo* il processo che *arriva per primo*
>- Algoritmo di tipo ***Non-Preemptive***

L'implementazione è semplice, basta una *coda* con politica `FIFO`

>[!danger] Problemi

Questo algoritmo provoca elevati *tempi medi di attesa* e *turnaround*
- Processi `CPU` *bound* ritardano i process i`I/O` *bound*
>[!caution] Convoy Effect
>Il *convoy effect* avviene quando una serie di processi `I/O` *bound* sono in coda dietro al processo `CPU` *bound*
>- Mentre i processi `I/O` *bound* sono in attesa della disponibilità della risorsa che il processo `CPU` *bound* sta occupando, la **ready queue** ***rimane vuota***

### Shortest Job First

>[!info] SJF
>Lo *Shortest Job First* (più precisamente Shortest next `CPU` *burst* First) è un algoritmo che assegna alla `CPU` il processo **ready** che ha la minima durata del `CPU` *burst* successivo

L'algoritmo è **ottimale** rispetto al *tempo di attesa*
- Tuttavia à **impossibile** da implementare nella pratica
- È solo possibile fornire delle *approssimazioni* tramite ***tecniche euristiche***

##### Calcolo Approssimato
>Il calcolo della durata del prossimo `CPU` *burst* è basato sul concetto di media esponenziale dei `CPU` *burst* precedenti

>[!abstract] Concetto
>Sia $t_{n}$ il tempo dell'$n$-esimo `CPU` *burst* e $T_{n}$ la corrispondente previsione
>Sia $\alpha$ il peso che voglio dare alle operazioni:
>>[!question] Devo dare più peso alla *previsione* o al *tempo effettivo*?

Dati questi dati si può calcolare una sorta di **media pesata** fra il valore di tempo del *burst* previsto e la durata effettiva
- $T_{n+1}$ si può approssimare come seque:

$$
T_{n+1}=\alpha t_{n}+(1-\alpha)T_{n}
$$

Andando a sostituire ad ogni passo il valore di $t_{n}$ precedente:
$$
T_{n+1}=\sum_{j=0}^n \alpha(1-\alpha)^j\cdot t_{n-j} +(1-\alpha)^{n+1} T_{0}
$$

##### Tipologia dell'Algoritmo
> L'algoritmo ***SJF*** può essere sia **Preemptive** che **Non-Preemptive**

>[!note] Non Preemptive
>Una volta il processo più "*corto*" è in esecuzione, esso continua fino alla sua **terminazione**.

>[!tldr] Preemptive
>Il processo in esecuzione può essere inserito nella coda **ready**, se durante la sua esecuzione è entrato un processo con un `CPU` *burst* più *breve* di quanto rimane da eseguire al processo corrente
>- ***Shortest Remaining Time First***

### Round Robin
>[!info] Concetto
>Il ***round robin*** è un *algoritmo di scheduling* basato sul concetto di **time slice**
>- Si divide l'esecuzione del programma in ***diversi periodi di tempo*** di lunghezza uguale
>- Il processo ***rimane in esecuzione*** finché non si ferma da solo o *termina il suo quanto di tempo*

L'insieme dei processi in stato `ready` è organizzato come una coda

>[!attention] Due casi
>1. Il processo lascia il processore ***volontariamente***  
>	- Ha necessità di utilizzare un'altra *risorsa*
>2. Il processo esaurisce il suo *time slice*
>	- Viene reinserito in fondo alla coda dei processi `ready` 

>[!danger] La durata del quanto di tempo è un parametro **critico**

Se è *breve*:
- Il sistema è poco efficiente, dovendo cambiare processo attivo molto spesso

Se è *lungo*:
- In presenza di numerosi processi pronti, ci sono ***lunghi periodi di inattività*** per ciascun processo

>[!done] È necessario che l'hardware fornisca un timer (***interval timer***) che agisce sull'interruzione della `CPU`

## Scheduling a Priorità
---
>Non tutti i processi sono uguali

>[!example] Soluzione
>Si definisce ad ogni processo una *specifica priorità*
>Lo *scheduler* sceglierà il processo pronto con ***priorità più alta***

Le priorità possono essere:
- Definite dal sistema operativo
> Vengono usate una o più ***quantità misurabili*** per **calcolare** la priorità di un processo

- Definite esternamente
>Non definite dal sistema operativo, ma ***imposte dal livello utente***


![[attachements/Process_Priority_Queues.png]]
> Divisione dei processi con *diversa priorità* in *diverse code*

### Priorità Statica
>[!info] Concetto
>Nello *scheduling* con ***priorità statica***, la priorità del processo **non cambia mai** durante la vita del processo stesso

>[!danger] Problema: Starvation

Può capitare che un processo a priorità bassa, ***non venga mai eseguito***
- Altri processi con priorità più alta continuano a "sorpassarlo"

### Priorità Dinamica
>[!info] Concetto
>Nello *scheduling* con ***priorità dinamica***, la priorità del processo **può cambiare** durante la vita del processo stesso

>[!done] Problema Risolto: Starvation

> Tecnica di *scheduling*: ***Aging***

L'*aging* è una tecnica che consiste nell'***incrementare gradualmente*** la priorità dei processi in attesa
- Nessun processo rimarrà in attesa per un *tempo indefinito* perché prima o poi raggiungerà la ***priorità massima***

#### Scheduling Multi-livello
>All'interno di ogni classe di processi è possibile usare una ***politica specifica adatta*** alla caratteristica della classe

>[!example] Esempio
>- Processi server -> Priorità statica
>- Processi utenti interattivi -> round robin
>- Altri processi utente -> FIFO

## Scheduling Real-Time
---
>[!info] Concetto
>In un sistema ***real-time*** la correttezza dell'esecuzione non dipende solamente dal *valore restituito*, ma anche dall'*istante temporale* nel quale il risultato viene emesso

>Scheduler Real-Time

>[!note] Earliest Deadline First
>È una *politica di scheduling* per processi periodici ***Real-Time***
>Viene scelto di volta in volta il processo che ha la *deadline più prossima*
>- Viene considerato algoritmo di *priorità dinamica* perché la priorità relativa di due processi ***varia in momenti diversi***

### Hard Real-Time
>[!attention] Definizione
>La *deadline* di esecuzione dei programmi **non deve essere superata** in nessun caso
>- L'avvenimento del caso contrario potrebbe causare ***effetti catastrofici***

Sistemi come:
- Controlli Aerei
- Centrali Nucleari
- Etc...

### Soft Real-Time
>[!tip] Definizione
>La *deadline* di esecuzione dei programmi non è stretta come nei sistemi ***Hard Real-Time***
>- Errori occasionali sono *tollerabili*