## Introduzione
---
>[!definizione]
>`OpenMP` è un modello per ***programmazione parallela*** su architetture a [[Git-Obsidian/Architettura degli Elaboratori/Architetture a Confronto/Architetture Parallele#Multiprocessori|architetture a memoria condivisa]].

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
- Garantisce [[Valutazione delle Performance#Speedup|speedup]].
- Evita *data races*.

### Modello di Esecuzione
>[!info]
>Un programma `OMP` inizia come un ***programma seriale*** con uno dei core della macchina.
>Possono essere presenti nel codice delle **regioni parallele**.
>- All'inizio delle regioni parallele viene creato un "***team***" di *thread* e il corpo della regione parallela viene **clonato** e i thread eseguono in maniera parallela.

Alla termine della regione parallela il team di thread "collassa" (join).

![[OMPExecutionModel.png]]
#### Pragmas
>[!note] `{c icon} #pragma`
>I `{c icon} #pragma` sono ***direttive del preprocessore*** che permettono comportamenti che non sono parte delle specifiche del [[Linguaggio C]].

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

##### Direttiva Parallel
>[!failure] `{c icon} #pragma omp parallel`
>Quando un processo raggiunge la direttiva `{c icon} parallel`, rea un ***team di thread*** e diventa il *master del team*.

Il master ha il `threadID=0`.

La ***dimensione del team*** dipende dall'implementazione.

> Il codice verrà **duplicato** e ogni thread *eseguirà la regione*.

>[!summary] Barriera
>C'è una ***barriera implicita*** alla fine di una sezione parallela.
>- Solo il master continua l'esecuzione.

```c title:example
#include <stdio.h>
#include <omp.h>
void say_hello( void )
{
	int my_rank = omp_get_thread_num();
	/* returns the id of the thread executing the code */
	int thread_count = omp_get_num_threads();
	/* returns the number of threads in the currently active team */
	printf("Hello from thread %d of %d\n", 
	my_rank, thread_count);
}
int main( int argc, char* argv[] )
{
	int x = omp_get_max_threads()
	/* returns the default dimension of the thread team */
	omp_set_num_threads(4);
	/* Sets the number of threads in the team */
#pragma omp parallel
	say_hello();
	return 0;
}
```

##### Direttiva For
>[!failure] `{c icon} #pragma omp parallel`
>La direttiva `for` è utilizzata in un ***blocco parallelo***.
>Le iterazioni del `loop` sono assegnate ai *thread del team corrente*.

La variabile del loop è resa ***privata di default***.

```c
double trap( double a, double b, int n)
{
	double result = 0;
	const double h = (b - a) / n;
#pragma omp parallel for reduction(+: result)
	for ( int i = 0; i < n - 1; i++)
	{
		result += h * (f (a + i * h)) + f(a + (i + 1) * h) / 2;
	}
	return result;
}
```

La variabile `index` ***deve*** essere una *variabile intera* (**non** può essere *floating point*).
- L'*espressione booleana* del `loop` deve avere un tipo **compatibile**.
- L'*espressione booleana* **non** deve cambiare durante l'esecuzione.
- La variabile `index` può essere ***solo modificata*** dall'espressione di incremento.

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
> Nella Programmazione seriale lo [[Visibilità e Tempo di Vita|scope]] di una variabile consiste nella sezione di un programma dove la variabile può essere usata.

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
> È possibile definire delle regioni di codice che verranno eseguiti in maniera [[9 - Condivisione di Risorse#Azioni Atomiche|atomica]].

> `omp atomic`
- Protegge gli ***aggiornamenti*** a una *variabile condivisa*.

> `omp critical`
- Protegge gli accessi a una [[10 - Sezioni Critiche|sezione critica]].
- Tutti i thread prima o poi eseguiranno la ***sezione critica***.

>[!danger] Attenzione
>Le direttive `critical` e `atomic` **non** proteggono contro le [[8 - Concorrenza#Race Condition|race condition]] causate dagli accessi alle *variabili condivise*.

#### Clausola Reduction
>[!info] `{c icon} reduction(<op>: <variable>)`
> Clausola che ***accumula risultati parziali*** in maniera atomica. 

> `{c icon} <op>`
- Può essere: `+` `-` `|` `*` `^` `&` `&&` `||` `min` `max`.

> `{c icon} <variable>`
- È la variabile dove verrà ***accumulato il risultato finale***.

```c
/* omp-reduction.c */
#include <stdio.h>
int main( void )
{
	int a = 2;
#pragma omp parallel reduction(*:a)
	{
	/* implicit initialization a = 1 */
		a += 2;
	}
	printf("%d\n",a);
	return 0;
}
```

Segue il pattern [[Reduce|reduction]].

>[!caution] Funzionamento

Una *copia privata* della **variabile reduction** è creata per ciascun thread.
- Inizializzata con il *valore neutro dell'operatore*.

> Ogni thread esegue la regione parallela.

Quando i thread finiscono, viene applicato l'operatore con l'ultimo valore di *ogni riduzione locale* e il valore che la variabile aveva prima della ***regione parallela***.
