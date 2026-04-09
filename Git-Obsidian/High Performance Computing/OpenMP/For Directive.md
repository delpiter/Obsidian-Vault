## Direttiva For
---
>[!failure] `{c icon} #pragma omp parallel`
>La direttiva `for`  di [[OpenMP]] è utilizzata in un ***blocco parallelo***.
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

### Transposition Sort Example
> Il transposition sort è una variante del bubble [[../../Algoritmi e Strutture Dati/Ordinamento/Problema dell'Ordinamento|sort]].

>[!tldr] Idea
>Consiste nel *confrontare* tutte le coppie (***pari-dispari***) di elementi adiacenti, e scambiarli se nell'ordine sbagliato.
>Successivamente *confrontare* le coppie (***dispari-pari***).

```c title:serial
for (int phase = 0; phase < n; phase++)
{
    if (phase % 2 == 0)
    {
        for (int i = 0; i < n - 1; i += 2)
        {
            if (v[i] > v[i + 1])
                swap(&v[i], &v[i + 1]);
        }
    }
    else
    {
        for (int i = 1; i < n - 1; i += 2)
        {
            if (v[i] > v[i + 1])
                swap(&v[i], &v[i + 1]);
        }
    }
}
```

Una prima parallelizzazione tramite ***OpenMP*** potrebbe essere la seguente:
```c title:"first parallel"
for (int phase = 0; phase < n; phase++)
{
    if (phase % 2 == 0)
    {
#pragma omp parallel for default(none) shared(v, n)
        for (int i = 0; i < n - 1; i += 2)
        {
            if (v[i] > v[i + 1])
                swap(&v[i], &v[i + 1]);
        }
    }
    else
    {
#pragma omp parallel for default(none) shared(v, n)
        for (int i = 1; i < n - 1; i += 2)
        {
            if (v[i] > v[i + 1])
                swap(&v[i], &v[i + 1]);
        }
    }
}
```

>[!warning] Attenzione!
>Il `loop` esterno, ad *ogni iterazione* ***crea*** e ***distrugge*** un team di thread in ciascuna regione.

Questo produce overhead, in base all'implementazione di OpenMP.

> Soluzione
- Innestare la direttiva `for` in una direttiva `{c icon} #pragma omp parallel` per ***riciclare lo stesso team di thread***.

```c title:"efficient parallel implementation"
/* Create a team */
#pragma omp parallel default(none) shared(v, n) private(phase)
for (int phase = 0; phase < n; phase++)
{
    if (phase % 2 == 0)
    {
/* Use the thread from the team created before */
#pragma omp for
        for (int i = 0; i < n - 1; i += 2)
        {
            if (v[i] > v[i + 1])
                swap(&v[i], &v[i + 1]);
        }
    }
    else
    {
#pragma omp for
        for (int i = 1; i < n - 1; i += 2)
        {
            if (v[i] > v[i + 1])
                swap(&v[i], &v[i + 1]);
        }
    }
}
```