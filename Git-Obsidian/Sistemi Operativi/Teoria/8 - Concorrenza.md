## Introduzione
---
> In un sistema operativo sono presenti un gran numero di attività che vengono eseguite più o meno ***contemporaneamente*** dal processore

>[!warning] Senza delle regole, la consistenza delle attività sarebbe ***difficile*** da descrivere e realizzare

>[!todo] Assioma di *Finite Progress*
>Ogni [[6 - Processi, Schedule e Thread#Processi|processo]] viene eseguito ad una velocità ***finita***, ma ***sconosciuta***


>[!question] Che cos'è la ***concorrenza***?

>La concorrenza riguarda la gestione di *processi multipli*

Esistono 3 modalità di gestione di processi multipli
### Multiprogramming
>[!info] Definizione
>Nel ***Multiprogramming*** è presente un solo processore ma più processi
>- I processi multipli sono *alternati nel tempo*, ad ogni istante al massimo un processo è in esecuzione
>
>>[!note] Il *parallelismo* è apparente

>[!abstract] Concetto: ***Interleaving***
>I processi sono alternati con una velocità tale da dare l'impressione di avere un multiprocessore

![[attachements/Interleaving.png]]

### Multiprocessing
>[!info] Definizione
>Nel ***Multiprocessing*** sono presenti un più processori
>- I processi vengono eseguiti simultaneamente
>
>>[!note] Il *parallelismo* è reale

>[!abstract] Concetto: ***Overlapping***
>I processi sono "sovrapposti" nel tempo, si definisce "*overlapping*" la sovrapposizione temporale dei processi

![[attachements/Overlapping.png]]

### Distributed Processing
>[!info] Definizione
>Nel ***Distributed Processing*** più processi vengono eseguiti su un insieme di computer distribuiti e indipendenti
>
>>[!note] Il *parallelismo* è reale

## Esecuzione Concorrente
>[!example] Definizione
>Due programmi si dicono in ***esecuzione concorrente*** se vengono eseguiti in parallelo, con parallelismo **reale** o **apparente**
>>[!abstract] Concorrenza
>>La concorrenza è l'insieme di tecniche per risolvere i problemi associati all'esecuzione concorrente, come la *comunicazione* e la *sincronizzazione*

>[!question] Dove si può trovare la concorrenza?

1. Nelle applicazioni multiple
2. Nelle applicazioni strutturate su processi
3. Nella struttura del sistema operativo

>[!caution] Ci sono differenze tra parallelismo reale e apparente?

>Per come è fatta la gestione dei dati e il sistema operativo, non c'è alcuna differenza

I problemi derivano dal fatto che ***non*** è possibile *predire* gli istanti temporali in cui vengono eseguite le istruzioni
- Due processi potrebbero accedere ad una o più risorse condivise *contemporaneamente*

##### Proprietà dei Programmi Concorrenti
>[!info] Definizione
>Una *proprietà di un programma* concorrente è un attributo che rimane vero per ogni possibile esecuzione

>Ne esistono due tipi:

>[!example] Safety
>"*Nothing Bad Happens*"
>Indica che se il programma avanza, sta andando nella direzione "*voluta*"
>>[!note] I meccanismi di sincronizzazione servono a ***garantire*** questa proprietà

Nei programmi sequenziali:
- Esprime la correttezza dello *stato finale*

>[!done] Liveness
>"*Something Good eventually Happens*"
>Il programma avanza, senza fermarsi
>>[!note] I meccanismi di sincronizzazione utilizzati ***non devono prevenire*** l'avanzamento del programma

Nei programmi sequenziali:
- La *terminazione* del programma
#### Race Condition
>[!info] Definizione
>Si dice che un sistema di processi multipli presenta una ***race condition*** qualora il risultato finale dell'esecuzione *dipenda* dalla temporizzazione con cui vengono eseguiti i processi
>- Per scrivere un programma concorrente si deve **eliminare** la *race condition*

## Notazioni
---
>Esistono diverse notazioni utilzzate per ***Descrivere Processi Concorrenti***

>[!attention] Notazione Esplicita
>

```c
process name {
	...statements...
}
```

>[!hint] Notazione *cobegin*/*coend* 
>Ogni statement viene eseguito in ***concorrenza***
>Le istruzioni che seguono il *coend* sono eseguite solo quando **tutti gli statement** sono terminati

```c
cobegin
	...statement1...
	...statement2...
	...statement3...
	...
coend
```

>[!tl;dr] Notazione *fork*/*join*/*quit*
>`fork w`
>- Inizia l'esecuzione di un processo $w$ *concorrente* al processo **attualmente in esecuzione**
>
>`quit`
>- Termina l'esecuzione del processo
>
>`join <counter>` 
>- Aspetta la terminazione di `<count>` processi

## Interazioni fra Processi
---
> È possibile classificare le modalità di interazione tra processi in base a quanto sono "consapevoli" uno dell'altro

### Tipologie di Concorrenza
>I processi fra di loro possono essere di due tipi

>[!example] In Competizione
>I due processi "***competono***" per le stesse risorse
>- La soluzione della *competizione* avviene tramite **sincronizzazione implicita**, gestita dal *sistema operativo*

>[!abstract] In Cooperazione
>I due processi "*condividono*" risorse per comunicare delle informazioni
>- La soluzione della *cooperazione* avviene tramite **sincronizzazione esplicita** e *gestita dal programmatore*

### Tipologie di Interazione
>[!warning] Processi "*ingnari*" uno dell'latro
>Sono due processi *indipendenti*, non progettati per lavorare insieme
>- Condividono lo stesso **ambiente comune**
>>[!done] Sono processi in ***Competizione***

>[!note] Processi "*indirettamente*" a conoscenza uno dell'altro
>Sono processi che *condividono risorse*, al fine di scambiarsi informazioni
>- Non si conoscono, comunicano tramite le **risorse condivise**
>>[!done] Sono processi in ***Cooperazione***

>[!todo] Processi "*direttamente*" a conoscenza uno dell'altro
>Sono processi che *comunicano* uno con l'altro sulla base dei loro `id`
>- La comunicazione è diretta, spesso basata su scambio di messaggi
>>[!done] Sono processi in ***Cooperazione***

## Riassunto
---
| Tipo                              | Relazione               | Meccanismo       | Problemi di Controllo                                               |
|:--------------------------------- | ----------------------- | ---------------- | ------------------------------------------------------------------- |
| Processi "ignari"                 | Competizione            | Sincronizzazione | [[9 - Condivisione di Risorse]]: Mutua esclusione, deadlock e starvation |
| Processi con conoscenza indiretta | Cooperazione(*sharing*) | Sincronizzazione | [[9 - Condivisione di Risorse]]: Mutua esclusione, deadlock e starvation |
|      Processi con conoscenza diretta     |Cooperazione (*comunicazione*)  |       Comunicazione| [[9 - Condivisione di Risorse]]: Deadlock e starvation|


