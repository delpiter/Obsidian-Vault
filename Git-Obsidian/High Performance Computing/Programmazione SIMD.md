## Single Instruction Multiple Data
---
> Nel modello [[Istruzioni IA-32 Speciali#Istruzioni MMX|SIMD]] la stessa operazione è applicata a più dati.

Solitamente questo è fatto attraverso delle istruzioni speciali che lavorano con array di dimensione piccola e fissa.

![[SIMDInstruction.png]]

>[!abstract] Programmazione `SIMD` livelli

> Dall'alto livello al basso:

1. Compiler Auto-vectorization.
2. **Optimized** `SIMD` libraries (`ATLAS`, per algebra lineare; `FFTW` per trasformazioni di Fourier).
3. **Domain specific** languages for `SIMD` programming (Mini linguaggi specifici per la programmazione `SIMD`).
4. Compiler dependent ***vector data types***.
	1. Estensioni prioritarie dei diversi compilatori.
5. Compiler `SIMD` [[Istruzioni IA-32 Speciali#Intrinsics|Intrinsics]].
6. [[Istruzioni IA-32|Assembly]] Language.

### Estensioni SIMD
![[Istruzioni IA-32 Speciali#Istruzioni MMX]]

Per ogni tipo di dato ci sono **istruzioni apposite**.

>[!fail] Questo provoca un'esplosione del numero di funzioni totale

![[Istruzioni IA-32 Speciali#Evoluzioni SIMD]]

### Speedup Superlineare
> La programmazione `SIMD` può essere causa di [[Valutazione delle Performance#Speedup|speedup superlineare]].

```c title:example
for (int i = 0; i < n; i++)
{
	compute(i);
}
```

Eseguendo questo codice possiamo vedere che una porzione di tempo viene usata per l'incremento e il controllo del ciclo `for`

>[!failure] Loop Unrolling
>Consiste nella rimozione di una ***porzione dell'overhead*** eseguendo più esecuzioni in un *solo loop del ciclo*, modificando lo "step" del ciclo stesso.

```c title:loop-unrolling
for (int i = 0; i < n; i+=4)
{
	compute(i);
	compute(i + 1);
	compute(i + 2);
	compute(i + 3);			
}
/* Handle leftovers */
```

Infine possiamo usare le istruzioni `SIMD` per il singolo ciclo del loop.

```c title:SIMD
for (int i = 0; i < n; i+=4)
{
	SIMD_compute(i,...,i + 3);		
}
/* Handle leftovers */
```

>[!done] Speedup
>Oltre a fare una sola operazione al posto di $4$, viene ridotto altamente l'overhead dovuto dal ciclo [[La CPU#Fetch Decode Execute|Fetch Decode Execute]] dei dati e delle istruzioni.

![[SuperlinearSpeedup.png]]

### Opportunità di Vettorizzazione
> Esempio: [[Reduce|Riduzione]] di un array.

>[!tldr] Idea
>Possiamo dividere il *vettore* in piccoli vettori e usare le istruzioni `SIMD` per fare somme su **più valori contemporaneamente**.

Alla fine dovrà essere sommato il vettore di supporto per ottenere il risultato.

![[VectorizationOpportunities.png]]

```c
float vsum(float *v, int n)
{
	float vs[4] = {0.0, 0.0, 0.0, 0.0};
	float s = 0.0;
	
	for(int i = 0; i< n-3; i+=4)
	{
		vs[0:3] += v[i:i+3]; // SIMD operation
	}
	
	s=vs[0] + vs[1] + vs[2] + vs[3];
	/* Handle leftovers */
}
```

>[!warning] Attenzione
>Bisogna prestare attenzione se la **lunghezza** dell'array non è un multiplo della dimensione del vettore `SIMD`.

> *Soluzioni*
- Aggiunta di **Padding**.
- Gestione dei resti con **operazioni scalari**.

### Vector Data Types
>[!info]
>Alcuni compilatori supportano ***vector data types***, estensioni specifiche ad un compilatore.
>>[!fail] Non portabile

Sono piccoli vettori di tipi numerici, tipicamente `char`, `int`, `float` o `double`.
- È possibile eseguire ***operazioni aritmetiche di base***.

>Il compilatore:
- Crea un eseguibile con istruzioni `SIMD` appropriate, se disponibili.
- Altrimenti crea **codice scalare equivalente**.

```c title:definition
/* Vector of 4 int elements, occupies 16 bytes of contiguous memory */
typedef int v4i __atribute__((vector_size(16)));

/* To know the length divide the size of the vector with the size of the type*/
#define VLEN (sizeof(v4f)/sizeof(float))
```

> Si possono usare vettori di lunghezza "*arbitraria*".
- Se l'architettura non lo supporta il compilatore userà più istruzioni `SIMD` su **vettori più piccoli**.

```c title:usage
typedef float v4f __attribute__((vector_size(16)));
#define VLEN (sizeof(v4f)/sizeof(float))

float vsum(float *v, int n)
{
	v4f vs = {0.0f, 0.0f, 0.0f, 0.0f};
	v4f *vv = (v4f*)v;
	int i; float s = 0.0f;
	for (i=0; i<n-VLEN+1; i += VLEN) {
		vs += *vv; // compiler will generate SIMD instruction for this
		vv++;
	}
	s = vs[0] + vs[1] + vs[2] + vs[3];
	// can be treated as standard arrays
	
	for ( ; i<n; i++) {
		s += v[i];
	}
	return s;
}
```

>[!hint] Operazioni permesse (`GCC`)
>`+`, `-`, `*`, `/`, `^`, `|`, `&`, `~`, `%`.

Sono supportati anche gli operatori di confronto standard:
- `==`, `!=`, `<`, `>`, `>=`, `<=`.

I vettori `SIMD` sono confrontati ***elemento per elemento***.
- Ritorna `0` se il confronto è falso.
- Ritorna `-1` se il confronto è vero.
>[!question] Perché `-1`?

#### Vettorizzazione di Branch
> I branch (`if-else`) sono notoriamente difficili da vettorizzare.

Vogliamo vettorizzare il seguente codice:
```c
int a[4] = {12, -7, 2, 3};

for(int i = 0; i < 4; i++){
	if(a[i] > 0)
		a[i] = 2;
	else
		a[i] = 1;
}
```

>[!done] Section and Masking
>Basta utilizzare dei vettori "*maschere*" per le ***condizioni***.

```c
v4i a = {12, -7, 2, 3};
v4i vtrue = {2, 2, 2, 2};
v4i vfalse = {1, 1, 1, 1};

v4i mask = (a>0); /* Mask = {-1, 0 ,-1, -1} */
a = (vtrue & mask) | (vfalse & ~mask); 
```

![[SectionAndMask.png]]

- Si sfruttano i *bitwise operator*.

### Note sull'Allineamento della Memoria
> Alcune versioni `GCC` emettono codice assembly per la dereferenziazione di un puntatore a *vector data type* che funziona solo se l'indirizzo è ***allineato*** a $16$ `bit`.

La `{c icon} malloc()` potrebbe non ritornare un pointer che è *propriamente allineato*.

>[!abstract] Soluzione

```c title:"Data on Stack"
float v[1024] __attribute__ ((aligned(__BIGGEST_ALIGNEMENT__)));
/* biggest alignement is 16 for SSE, 32 for AVX */
```

```c title:"Data on Heap"
#define _XOPEN_SOURCE 600
#include <stdlib.h>

float *v;
posix_memalign(&v, __BIGGEST_ALIGNEMENT__, 1024);
/* Similar to CUDA malloc */
```