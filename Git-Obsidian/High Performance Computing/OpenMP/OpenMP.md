## Introduzione
---
>[!definizione]
>`OpenMP` è un modello per ***programmazione parallela*** su architetture a [[../../Architettura degli Elaboratori/Architetture a Confronto/Architetture Parallele#Multiprocessori|architetture a memoria condivisa]].

È un modello portabile su **tutte** le architetture a *memoria condivisa*.

> Si basa sulla *parallelizzazione incrementale* (***Incremental Parallelization***)
- Si parallelizzano *blocchi individuali* di un programma, lasciando il resto **sequenziali**.

È ***compiler-based***
- È il *compilatore* che genera **thread**, i **programmi** e la **sincronizzazione**.

`OMP` supporta diversi linguaggi di programmazione:
- `{fortran icon} fortran`, `{c icon} C` `{cpp icon} C++`
- Principalmente formato da *direttive per il compilatore*.
- Ci sono alcune **routine di libreria**.

>[!done] `OpenMP`
- Permette ai programmatori di separare un programma in ***regioni seriali*** e ***parallele***.
- Fornisce ***costrutti di sincronizzazione***.

>[!fail] `OpenMP` **non**
- Parallelizza ***automaticamente***.
- Garantisce [[../Valutazione delle Performance#Speedup|speedup]].
- Evita *data races*.

### Modello di Esecuzione
>[!info]
>Un programma `OMP` inizia come un ***programma seriale*** con uno dei core della macchina.
>Possono essere presenti nel codice delle **regioni parallele**.
>- All'inizio delle regioni parallele viene creato un "***team***" di *thread* e il corpo della regione parallela viene **clonato** e i thread eseguono in maniera parallela.

Alla termine della regione parallela il team di thread "collassa" (join).

![[attachements/OMPExecutionModel.png]]
#### Pragmas
>[!note] `{c icon} #pragma`
>I `{c icon} #pragma` sono ***direttive del preprocessore*** che permettono comportamenti che non sono parte delle specifiche del [[../../Programmazione/Introduzione Programmazione/Linguaggio C]].

```c
#pragma omp construct [clause [clause ...]]
```

I compilatori che non supportano i `{c icon} #pragma` li *ignorano*.
- Tolte le direttive, rimane comunque un ***programma seriale***.

La maggior parte delle direttive `OpenMP` viene applicata al ***blocco strutturato*** che segue la direttiva.
- Il *blocco strutturato* deve avere un **singolo punto di ingresso** e un **singolo punto di uscita**.
- Non è possibile usare `{c icon} return`, `{c icon} goto` o altre strutture.

```c
#pragma omp parallel
{
	int x = 10;
	printf(x);
}
```

> Clausole di ***OpenMP***.
- [[Parallel Directive]]
- [[For Directive]]
- [[Reduction Clause]]
- [[Schedule Clause]]
- [[Collapse Directive]]
##### Calcolare i Tempi
> Per calcolare i tempi `OpenMP` mette a disposizione una funzione.

```c title:"Taking Times"
double tstart, tstop;
tstart = omp_get_wtime();
#pragma omp ... 
{
/* block of code to measure */
}
tstop = omp_get_wtime();
printf("Elapsed time: %f\n", tstop - tstart);
```

### Scope
> Nella Programmazione seriale lo [[../../Programmazione/Variabili/Visibilità e Tempo di Vita|scope]] di una variabile consiste nella sezione di un programma dove la variabile può essere usata.

>[!hint] Scope
> In `OpenMP` lo ***scope*** di una variabile si riferisce al **set di thread** che può accedere alla variabile.

Di *default* tutte le variabili visibili all'inizio del blocco parallelo sono ***condivise*** dai thread.
- Le variabili definite all'interno del blocco sono ***private per ciascun thread***.

##### Alterare il Comportamento di Default
>[!info]
>È possibile *alterare* il comportamento di default dello ***scope***.

`x` è un *insieme di variabili visibili* **prima** dell'inizio del blocco parallelo.

> `shared(x)`
- Tutti i thread hanno accesso alla **stessa area di memoria**.

> `private(x)`
- Ogni thread ha la **propria copia** della variabile.
- Le istanze locali di `x` **non** sono inizializzate.
- Update locali a `x` **sono persi** usciti dalla regione parallela.

> `firstprivate(x)`
- Ogni thread ha la **propria copia** della variabile.
- Le istanze locali di `x` **sono inizializzate** con il valore corrente di `x`.
- Update locali a `x` **sono persi** usciti dalla regione parallela.

> `default(shared)` o `default(none)`
- Ha *effetto* su tutte le variabili **non specificate** nelle altre clausole.
- `default(none)` si assicura che venga specificato lo ***scope*** di ogni variabile usata nel blocco parallelo. (*altamente raccomandato*)

#### Condividere Array
> 2 Tipi di array in `{c icon} C`

- `{c icon} int a[2] = {2, 3};`
- `{c icon} *b = (int*)malloc(2*sizeof(*b));`

> Dichiarare `firstprivate(a,b)`:
- `a` viene copiato per ogni thread (ognuno ha una ***copia privata***).
- `b` viene clonato il ***puntatore all'array*** (array condiviso, puntatore privato).

#### Istruzioni Atomiche
> È possibile definire delle regioni di codice che verranno eseguiti in maniera [[../../Sistemi Operativi/Teoria/9 - Condivisione di Risorse#Azioni Atomiche|atomica]].

> `omp atomic`
- Protegge gli ***aggiornamenti*** a una *variabile condivisa*.

> `omp critical`
- Protegge gli accessi a una [[../../Sistemi Operativi/Teoria/10 - Sezioni Critiche|sezione critica]].
- Tutti i thread prima o poi eseguiranno la ***sezione critica***.

>[!danger] Attenzione
>Le direttive `critical` e `atomic` **non** proteggono contro le [[../../Sistemi Operativi/Teoria/8 - Concorrenza#Race Condition|race condition]] causate dagli accessi alle *variabili condivise*.

#### Costrutti di Sincronizzazione
>[!summary] `{c icon} #pragma omp barrier`
>Tutti i thread nel team attivo ***devono raggiungere*** questo punto prima di continuare l'esecuzione.

>[!attention] `{c icon} #pragma omp master`
>Indica che la regione parallela deve essere eseguita dal ***processo master*** (thread con `rank=0`).
>Gli altri thread salteranno la regione di codice.
>>[!danger] NON c'è una barriera implicita alla fine

>[!info] `{c icon} #pragma omp single`
>Indica che la regione parallela deve essere ***eseguita una sola volta*** dal *primo thread* che entra nella regione.
>>[!done] C'è una barriera implicita alla fine del blocco.

