## Task
---
>[!question] Programmi complessi
>Non tutti i programmi hanno dei semplici `loop` che [[OpenMP]] può *parallelizzare*.

> ***Esempio***: [[Linked Lists]] traversal.

```c
ListNode *p = head;
while(p){
	process(p);
	p = p->next;
}
```

Ogni nodo della lista è "***processato***" in maniera *diversa*.

>[!info] Task
>I ***task*** sono unità di lavoro indipendenti.
>Si compongono di:
>- ***Codice*** da eseguire.
>- ***Dati*** da elaborare.

L'unica *garanzia* presente è che al termine della [[Parallel Directive|regione parallela]] tutti i task create all'interno **sono stati eseguiti**.
- Una volta creati, i ***task*** vengono *eseguiti dal team di thread*, non necessariamente in ordine di creazione.
>[!failure] Nested Task
>È possibile *creare* dei **task** all'interno di un **task**.

```c
#pragma omp parallel
{
	#pragma omp single
	{
		#pragma omp task
		fred();
		#pragma omp task
		barney();
		#pragma omp task
		wilma();
	}
}
```

Il `{c icon} #pragma omp single` è fondamentale per non creare un task per thread.
### Scoping
> Lo scope delle variabili all'interno di un task è leggermente differente da quello della [[OpenMP#Scope|direttiva parallel]].

>[!summary] `{c icon} shared`
>Se una variabile è `shared` in un ***task***, la variabile fa riferimento alla locazione di memoria condivisa con quel nome, al punto dove il task era stato incontrato.

>[!hint] `{c icon} private`
>Se una variabile è `private` in un ***task***, fa riferimento a una *nuova porzione di memoria* ***non inizializzata***, creata quando il task è eseguito.

>[!tldr] `{c icon} firstprivate`
>Se una variabile è `firstprivate` in un ***task***, fa riferimento a una *nuova porzione di memoria* ***inizializzata*** con il valore della variabile esistente, creata quando il task è creato.

Il comportamento voluto per i task è, solitamente, `{c icon} firstprivate` poiché il task potrebbe non essere eseguito immediatamente.
- Variabili che sono private quando si incontra il costrutto task sono `{c icon} firstprivate` di *defaut*.

```c
int a = 1;

void foo( void )
{
	int b = 2, c = 3;
#pragma omp parallel private(b)
	{
		int d = 4; // a,c shared; b private, d private
#pragma omp task
		{
			int e = 5;
			// Scope of a: shared, value 1
			// Scope of b: firstprivate, uninitialized
			// Scope of c: shared, value 3
			// Scope of d: private => firstprivate, value 4
			// Scope of e: private, value 5
		}
	}
}
```

##### Esempio
> Linked List Traversal

```c title:"wrong outcome"
ListNode *p; // p shared
#pragma omp parallel
{
#pragma omp single
	{
		p = head; 
		while (p) {
#pragma omp task
			process(p);
			p = p->next;
		}
	}
}
```

>[!danger] Attenzione!
>Secondo le *regole della visibilità*, `p` è `shared` ad ogni task.

Se i **task** verranno eseguiti con il valore di `p` corrente durante l'esecuzione.
- Se ho creato 3 task, `p` punta al terzo elemento dell'array in tutti i task.

```c title:solution
#pragma omp parallel
{
#pragma omp single
	{
		ListNode *p = head; // p private
		while (p) {
#pragma omp task
			processwork(p);
			p = p->next;
		}
	}
}
```

In questo modo ***ogni task*** alla creazione, si crea una copia del valore di `p` *corrente*.

### Barriere dei Task
>[!question] Quando un task è sicuramente terminato?

> A una ***barriera dei thread*** (implicita o esplicita)
- La fine di un blocco `{c icon} #pragma omp parallel`

> Con una direttiva `{c icon} taskawait`
- Aspetta finché *tutti i task* definiti nel task corrente (**non i discendenti**) sono completati.
- `{c icon} #pragma omp taskwait`
- Il codice eseguito da un thread in una regione parallela ***è considerato un task***.
