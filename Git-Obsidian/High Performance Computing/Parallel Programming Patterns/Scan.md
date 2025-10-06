>[!example] Pattern
>Uno ***scan*** è un [[Parallel Programming Patterns|Pattern di Programmazione parallela]] che calcola tutti i prefissi di un array $[x_{0},x_{1},\dots,x_{n-1}]$ usando un operatore binario associativo (*somma*, *prodotto*, $\min$, $\max$).

> Sia $[x_{0},x_{1},\dots,x_{n-1}]$ l'array su cui applicare uno *scan*.

L'array $[y_{0},y_{1},\dots,y_{n-1}]$ ottenuto tramite un ***inclusive-scan*** ha elementi:
- $y_{0}=x_{0}$
- $y_{1}=x_{0}\text{ op. }x_{1}$
- $y_{2}=x_{0}\text{ op. }x_{1}\text{ op. }x_{2}$
- $\dots$
- $y_{n-1}=x_{0}\text{ op. }x_{1}\text{ op. }\dots\text{ op. }x_{n-1}$


L'array $[y_{0},y_{1},\dots,y_{n-1}]$ ottenuto tramite un ***exclusive-scan*** ha elementi:
- $y_{0}=0$: ***Elemento neutro*** dell'operatore binario
- $y_{1}=x_{0}$
- $y_{2}=x_{0}\text{ op. }x_{1}$
- $\dots$
- $y_{n-1}=x_{0}\text{ op. }x_{1}\text{ op. }\dots\text{ op. }x_{n-2}$

#### Implementazione Seriale
```c title:"serial implementation"
void inclusive_scan(int *x, int *s, int n) // n must be > 0
{
	int i;
	s[0] = x[0];
	for (i=1; i<n; i++) {
		s[i] = s[i-1] + x[i];
	}
}

void exclusive_scan(int *x, int *s, int n) // n must be > 0
{
	int i;
	s[0] = 0;
	for (i=1; i<n; i++) {
		s[i] = s[i-1] + x[i-1];
	}
}
```

#### Implementazione Parallela
>[!caution] Up-Sweep

![[UpSweep.png]]

```c title:Up-Sweep
for ( d=1; d<n/2; d *= 2 ) {
	for ( k=0; k<n; k+=2*d ) {
		x[k+2*d-1] = x[k+d-1] + x[k+2*d-1];
	}
}
```

>[!abstract] Down-Sweep

![[DownSweep.png]]

```c title:Down-Sweep
for ( ; d > 0; d >>= 1 ) {
	for (k=0; k<n; k += 2*d ) {
		float t = x[k+d-1];
		x[k+d-1] = x[k+2*d-1];
		x[k+2*d-1] = t + x[k+2*d-1];
	}
}
```