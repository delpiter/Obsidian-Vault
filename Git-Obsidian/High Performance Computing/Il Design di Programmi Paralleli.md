> Iniziamo con le ipotesi di un ***architettura a memoria condivisa***.

>[!tldr] Idea
>Una prima idea è quella di iniziare con una soluzione sequenziale e ***parallelizzarla***.

Questa non è sempre una buona idea
- Alcuni *algoritmi paralleli* non hanno nulla a che fare con le ***controparti sequenziali***.
###### Concetti Chiave
> Architetture Parallele
- Le architetture parallele richiedono dei ***paradigmi di programmazione parallela***.

- Scrivere programmi *paralleli* è ***più difficile*** di scrivere programmi *sequenziali*.
## Sum-Reduction
---
>[!caution] Problema
>Vogliamo calcolare la ***somma degli elementi*** di un array $A$ di $n$ elementi.

```c title:"sequential algorithm"
float seq_sum(const float* v, int n)
{
	int i;
	float sum=0.0;
	for (i=0; i<n; i++)
	{
		sum+=v[i];
	}
	return sum;
}
```

> Proviamo una prima parallelizzazione

```c title:"parallel algorithm_v1"
float par_sum_v1(const float* v, int n)
{
	float sum = 0.0;
	do in parallel {
		int my_start = my_id*my_block_len;
		int my_end = my_start + my_block_end;
		for (my_i=my_start; my_i<my_end; my_i++)
		{
			sum+=v[my_i];
		}
	}
	return sum;
}
```

>[!hint] Standard
>Assumiamo che le variabili che iniziano con `my_` sono ***variabili locali***, tutte le altre sono *condivise*.

>[!danger] Sbagliato

Il programma è sbagliato per 3 motivazioni:
1. Non c'è alcun meccanismo di protezione della ***mutua esclusione***.
	- Il risultato ritornato potrebbe essere sbagliato.
2. Se ci fosse la protezione, l'*efficienza guadagnata* dal parallelismo è *trascurabile*.
3. L'array $A$ potrebbe **non** essere **perfettamente divisibile** per il numero di "*processori*" usati per la parallelizzazione.
	- Gli ultimi valori dell'array ***non verranno iterati***.

>[!done] Soluzioni

> Problema *divisione dell'array*
- Basta seguire il seguente "***pattern***".

```c title:"array division"
int my_start = (n * my_id) / P;
int my_end = (n * (my_id + 1)) / P;
```

**Dove**:
- `n` è la lunghezza dell'array
- `my_id` è il *numero sequenziale* del thread che lavora alla porzione di codice, si ipotizza che partano da $0$.
- `P` è il numero di *thread disponibili*.

> Problema *troppo utilizzo della mutua esclusione*
- Ogni processore accumula una **somma parziale** in una ***variabile privata***.
- Comunque **molto lento**.

> Proviamo una **seconda versione**.

Utilizziamo un *array pubblico* `psum[]` dove ogni processore è in grado di salvare la ***propria somma locale***.
- Alla fine un processore *calcola la somma globale*.

```c title:"parallel algorithm_v2"
float par_sum_v2(const float* v, int n)
{
	float *psum[0..P-1]=0.0;
	float sum = 0.0;
	do in parallel {
		int my_start = (n * my_id) / P;
		int my_end = (n * (my_id + 1)) / P;
		for (my_i=my_start; my_i<my_end; my_i++)
		{
			psum[my_id]+=v[my_i];
		}
	}
	if(0 == my_id) // only the master executes this
	{
		for(my_i=0; my_i<P; my_i++)
			sum+=psum[my_i];
	}
	return sum;
}
```

>[!danger] Problema

Il processore `0` potrebbe iniziare la computazione della *somma globale* **prima** che gli altri processori abbiano *calcolato la propria locale*.

>[!done] Soluzione

- Utilizzare una `barrier synchronization`.

### Versione con Memoria Distribuita
>[!example] Idea

- Il numero di processori `P` è molto più piccolo della lunghezza dell'array `n`.
- Tutte le variabili sono *private*.
- Ogni processore calcola una *somma locale*.
- Ogni processore invia la somma locale al processore "*master*".

>[!warning] Bottleneck

Questa soluzione provoca un bottleneck quando il "*master*" deve processare tanti sotto processi.

>[!done] Soluzione

- Ogni *processore* invia il risultato parziale ad un altro *processore*.

![[attachements/ParallelReduction.png]]

$P-1$ somme sono comunque eseguite, ma il processo $0$ riceve $\log_{2}P$ messaggi ed esegue $\log_{2}P$ somme.

## Task Parallelism e Data Parallelism
---
>[!check] Task Parallelism
>Il ***Task Parallelism*** distribuisce i *tasks* (possibilmente diversi) ai singoli processori.

>[!caution] Data Parallelism
>Il ***Data Parallelism*** distribuisce i dati ai processori e ciascuno esegue lo stesso *task* con dati differenti.

