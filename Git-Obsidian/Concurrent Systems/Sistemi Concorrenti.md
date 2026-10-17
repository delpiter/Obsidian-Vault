## Concorrenza
---
>[!definizione]
>Nell'informatica la ***concorrenza*** è una proprietà dei sistemi dove numerosi processi computazionali vengono eseguiti *nello stesso momento* e che potenzialmente *interagiscono* tra di loro.
>>[!done] Definizione Moderna
>> La ***concorrenza*** riguarda gli aspetti fondamentali di un sistema di numerosi agenti computazionali *attivi simultaneamente* e che interagiscono tra di loro.

> Esempi
- Microservizi (sistemi distribuiti)
- Operating system scheduler (progrimmi multi-threaded e multi-process).
- Database Managment Systems

Le attività possono avere un qualche tipo di [[../High Performance Computing/Parallelizzare i Loop#Data Dependence|dipendenza]] tra di loro.

> [!question] Perché serve la programmazione parallela?
> Serve per sfruttare i **computer paralleli**, migliorare le **prestazioni** (*reattività e throughput*) e per supportare (al livello di astrazione appropriato) il design e lo sviluppo di ***sistemi software complessi***.

### Terminologia

>[!caution] Programmazione Concorrente
>

La *programmazione concorrente* consiste nella creazione di programmi dove multiple attività computazionali si sovrappongono nel tempo (***overlap***) e **interagiscono** in qualche maniera.
- Non è necessaria l'esecuzione dei vari programmi su processori fisici differenti.
- Ilprogramma concorrente focus è sull'organizzazione del programma.

> [!hint] Programma Concorrente
>

Un programma concorrente è un *insieme finito* di programmi sequenziali che possono essere eseguiti in parallelo (es. sovrapposti nel tempo).

L'esecuzione di un programma sequenziale è chiamata ***processo*** (*thread*).

> [!summary] Programmazione [[../High Performance Computing/Parallelizzare i Loop|parallela]]
>

La *programmazione parallela* è l'esecuzione di multipli programmi che si sovrappongono nel tempo tramite l'esecuzione su **processori fisici separati**.
- Il focus è sulle prestazioni del programma.

> [!failure] Programmazione distribuita
>

La programmazione distribuita si può usare quando i processori sono distribuiti attraverso una rete.
- Memoria, clock sono indipendenti tra i vari processori.

> ***Concorrente vs. Parallelo***

La concorrenza è una **modalità di strutturare il software**, per scrivere codice pulito che interagisce bene con il mondo reale.
- È un modello per la costruzione del software, facile da capire e da ragionare.

> [!warning] La concorrenza non è parallelismo
> Non è parallelismo ma **abilita** il parallelismo.

## Architetture Parallele
---

![[../Architettura degli Elaboratori/Architetture a Confronto/Architetture Parallele#Multiprocessori]]

![[../Architettura degli Elaboratori/Architetture a Confronto/Architetture Parallele#Multicomputer]]

### Interleaving
> Approccio classico per modellare la concorrenza è l'utilizzo dell'*interleaving*.

![[../Sistemi Operativi/Teoria/8 - Concorrenza#^4dcb27]]

![[../Sistemi Operativi/Teoria/attachements/Interleaving.png]]

Lo *scenario* dove due azioni vengono **eseguite allo stesso momento** viene scomposto in ***due scenari possibili*** con una esecuzione *sequenziale* delle due azioni:
- Prima l'azione $A$ poi l'azione $B$
- Prima l'azione $B$ poi l'azione $A$


> [!cite] Preservando l'ordine della sequenza di azioni  relative ad ogni singolo processo.
> 

> [!danger] Non Determinismo
> A causa dell'interleaving possiamo avere ***diversi scenari possibili*** come risultato dall'esecuzione di processi concorrenti.

Il numero di scenari possibili potrebbe ***non essere finito***.
- Siccome I processi eseguono a velocità relative le azioni di processi differenti sono *alternati arbitrariamente*.

## Perché studiare la programmazione concorrente
---
> [!question] Prestazioni

La risposta principale è: per un ***aumento delle prestazioni***.
- Aumento del throughput sfruttando hardware parallelo
- Aumento della responsiveness ottimizzando il tempo tra `CPU` e attività di `I/O`.

### Speedup
![[../High Performance Computing/Valutazione delle Performance#Speedup]]

> [!caution] Throughput
> *Più task* eseguiti nello *stesso intervallo* di tempo.

> Il nuovo ***bottleneck***: la *memoria*
- La memoria principale condivisa e il bus di collegamento ***sono potenziali bottleneck***
- Aumenta l'importanza della [[../Architettura degli Elaboratori/Architettura del Calcolatore/Cache|Cache]].

> [!question] 2\) Perché la programmazione concorrente?

> ***Astrazione e ingegnerizzazione***
- Definire un proprio livello di astrazione per programmi che interagiscono con l'ambiente.

Gli oggetti della Programmazione ad oggetti **non sono sufficienti**.

Concorrenza usata come uno strumento per la ***progettazione e costruzione*** di software.
- Un modo diverso di pensare come vengono risolti i problemi.
- Con **algoritmi** e ***strutture dati*** specifiche

La programmazione concorrente incide su ***tutto lo spettro dell'ingegneria***:
- Modellazione, progettazione, implementazione, verifica e testing

> [!tldr] Processi
> Un ***processo*** è un programma sequenziale in esecuzione.

È l'***unità di base*** di un sistema concorrente

Un processo è indipendente rispetto alla velocità di esecuzione.
- Ciascun processo dovrebbe essere ***completamente asincrono*** con gli altri.