## Clausola Schedule
---
>[!todo] `{c icon} #pragma omp parallel for schedule(type, chunksize)`
>La clausola `schedule` si aggiunge al costrutto [[Parallel Directive|parallel]] [[For Directive|for]] di [[OpenMP]], e consente di definire come le iterazioni del ciclo vengono ***assegnate ai thread***.
>- ([[../../Sistemi Operativi/Teoria/7 - Scheduler|Scheduler]]).

Le iterazioni sono divise in **chunk** di `chunksize` iterazioni consecutive.
### Type
> Il tipo può essere:

>[!caution] `static`
>Le iterazioni sono ***assegnate ciclicamente*** ai thread.

Se `chunksize` non è specificata allora:
- `{c icon} chunksize = ceil(n_iteration/n_thread)`

>[!abstract] `dynamic` o `guided`
>Le iterazioni assegnate ai thread seguono il [[../Parallel Programming Patterns/Partition#Master-Worker Paradigm|Master-Worker Paradigm]].
>

Il `chunksize` di *default* è $1$.

In uno **schedule** `guided`, quando viene completato un *chunk* la dimensione dei nuovi *diminuisce*.

>[!note] `auto`
>Il **compilatore** e/o il **sistema runtime** determina la schedule.

>[!failure] `runtime`
>Lo ***schedule*** è determinato a run-time usando la [[../../Sistemi Operativi/Bash/Variabili|variabile d'ambiente]]: `{sh icon} OMP_SCHEDULE`.

- `{sh icon} OMP_SCHEDULE="static,1" ./my-prog.exe`


Lo ***schedule*** di default è ***implementation dependent***.
- `GCC` *dovrebbe* utilizzare `static` di default.

#### Scegliere il Tipo
>[!question] Quale tipo di schedule è il migliore per un programma?


| Clause    | When to Use                                         | Note                                                    |
| --------- | --------------------------------------------------- | ------------------------------------------------------- |
| `static`  | *Pre-determined* and predictable work per iteration | Least work at run-time: Scheduling done at compile-time |
| `dynamic` | *Unpredictable highly variable* work                | Most work at run-time: Complex scheduling logic used.   |
