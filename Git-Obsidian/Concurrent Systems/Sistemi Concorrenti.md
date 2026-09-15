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
- Il focus è sull'organizzazione del programma.

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

![[../Architettura degli Elaboratori/Architetture a Confronto/Architetture Parallele|Architetture Parallele]]
