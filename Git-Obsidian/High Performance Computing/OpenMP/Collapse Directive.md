## Direttiva Collapse
---
>[!info] `{c icon} #pragma omp parallel for collapse(x)`
>La direttiva `collapse` di [[OpenMP]] specifica quanti `loop` in un ***loop innestato*** possono essere collassati  in uno unico loop e diviso secondo la [[Schedule Clause]].

`collapse` offre un ulteriore modo di controllare la [[../Parallel Programming Patterns/Partition#In base alla Dimensione|granularità del problema]].

```c title:example
#pragma omp parallel for num_threads(5) collapse(2)
for (int i=0; i<4; i++)
{
	for (int j=0; j<5; j++)
	{
		do_work(i,j);
	}
}
```

La clausola `collapse(2)` rende entrambi le variabili $i$ e $j$ **private**.

![[attachements/CollapseClause.png]]

>[!warning] Attenzione
>La direttiva `collapse` potrebbe introdurre un ***grande overhead***.

```c title:example
#pragma omp parallel for collapse(3)
for (int i=0; i<n; i++)
	for (int j=0; j<m; j++)
		for (int k=0; k<p; k++)
			foo(i, j, k);
```

Diventa:

```c
#pragma omp parallel for
for (int idx=0; idx < n*m*p; idx++)
{
	int tmp = idx;
	/* tmp = k + p × (j + i × m) */
	int k = tmp % p;
	tmp / = p;
	/* tmp = j + i × m */
	int j = tmp % m;
	tmp / = m;
	/* tmp = i */
	int i = tmp;
	foo(i, j, k);
}
```

Un `loop` potrebbe essere molto più complesso.
- ***Upper e lower bound*** potrebbero essere arbitrari.
- I `loop` potrebbero iterare all'indietro (`{c icon} i--`).
- Bisogna gestire `>`, `<`, `<=`, `>=`.
- Step ***non unitari***.
