## Direttiva Parallel
---
>[!failure] `{c icon} #pragma omp parallel`
>Quando un processo raggiunge la direttiva `{c icon} parallel` ([[OpenMP]]), rea un ***team di thread*** e diventa il *master del team*.

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
