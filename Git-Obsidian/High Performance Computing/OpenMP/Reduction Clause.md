## Clausola Reduction
---
>[!info] `{c icon} reduction(<op>: <variable>)`
> Clausola [[OpenMP]] che ***accumula risultati parziali*** in maniera atomica. 

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
	printf("%d\n",a); // Prints 18 (2 * 3 * 3)
	return 0;
}
```

Segue il pattern [[Reduce|reduction]].

>[!caution] Funzionamento

Una *copia privata* della **variabile reduction** è creata per ciascun thread.
- Inizializzata con il *valore neutro dell'operatore*.

> Ogni thread esegue la regione parallela.

Quando i thread finiscono, viene applicato l'operatore con l'ultimo valore di *ogni riduzione locale* e il valore che la variabile aveva prima della ***regione parallela***.