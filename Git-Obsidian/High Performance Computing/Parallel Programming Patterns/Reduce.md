>[!caution] Pattern
>Una ***reduction*** è un [[Parallel Programming Patterns|Pattern di Programmazione parallela]] che implica l'applicazione di un operatore binario associativo (*somma*, *prodotto*, $\min$, $\max$). agli elementi di un array $[x_{0}, x_{1},x_{2},\dots,x_{n-1}]$.

- ***Sum Reduce***$([x_{0}, x_{1},x_{2},\dots,x_{n-1}])=x_{0}+x_{1}+x_{2}+\dots+x_{n-1}$
- ***Min Reduce***$([x_{0}, x_{1},x_{2},\dots,x_{n-1}])=\min\{ x_{0},x_{1},x_{2},\dots,x_{1} \}$.

Una **reduction** può essere fatta in $O(\log_{2}n)$ *step paralleli*.

![[SumReduce.png]]

```c
int n2;
do
{
	n2=(n+1)/2;
	for(int i=0; i<n2; i++)
	{
		if(i+n2<n) x[i]+=x[i+n2];
	}
	n=n2;
} while(n2>1);

return x[0];
```

## Work Efficiency
---
>[!definizione]
>***Work efficiency*** indica il grado in cui il lavoro viene svolto in *modo efficace*, utilizzando le **risorse** (tempo, energia, materiali) nel modo migliore per ottenere un certo risultato.

> Quante somme sono calcolate dall'algoritmo di [[Reduce|parallel reduction]]?

- $\displaystyle\frac{n}{2}$ somme al primo livello.
- $\displaystyle\frac{n}{4}$ somme al secondo livello.
- $\dots$
- $\displaystyle\frac{n}{2^{j}}$ somme al livello $j$-*esimo*.
- $\dots$
- $1$ somma al livello $\log_{2}n$.

***Totale***: $O(n)$ *somme*.
>[!done] Conclusione

L'algoritmo di riduzione strutturato ad albero è ***work efficient***.
- Esegue la stessa quantità di lavoro che l'*algoritmo seriale ottimale esegue*.