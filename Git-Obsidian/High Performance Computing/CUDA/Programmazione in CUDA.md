## Device Code
---
>[!info]
> Un file `.cu` non è altro che uno standard file `{c icon} C` che viene eseguito sull'[[CUDA#Terminologia|host]].

Il compilatore **NVIDIA** (`nvcc`) può essere usato per compilare programmi anche senza "***device code***".

```c title:"cuda-hello.cu"
#include <stdio.h>
int main(void)
{
	printf("Hello, World!\n");
	return 0;
}
/* To compile */
/* 
	nvcc cuda-hello.cu
	By default it compiles a file named a.out
	A name can be specified with -o
*/
```

>[!failure] Scrivere Device Code
>Per scrivere ***device code*** è necessario introdurre due nuovi elementi sintattici.

> `{c} __global__ void funcName() {...}`
- Indica al compilatore che il codice verrà *chiamato* dalla `CPU` e *eseguito* sulla `GPU`.
>[!danger] Le funzioni `__global__` ***DEVONO*** avere come tipo di ritorno `{c icon} void`
>Eventuali valori di ritorno devono essere specificati tra i parametri.

`nvcc` separa il codice sorgente in **host** e **device**.
- Le *funzioni del device* (`funcName()`) sono processate dal compilatore **NVIDIA**.
- Le *funzioni dell'host* (`main()`) sono processate dal compilatore dell'*host* (`gcc`).

> `{c} funcName<<<1,1>>>();`
- Le triple parentesi angolari segnano una chiamata da **host** a **device code**.
- Anche chiamato "***kernel launch***".

### Gestione della Memoria
>[!info]
>Le memorie di ***device*** e di ***host*** sono entità *completamente separate*.

Puntatori alla *memoria di device* possono essere passati da/a **codice host**.
>[!fail] I puntatori alla **memoria device** ***non*** possono essere dereferenziati dal codice host

`CUDA` mette a disposizione delle `API` per la gestione della ***device memory***:
- `{c icon} cudaMalloc()`, `{c icon} cudaFree()`, `{c icon} cudaMemcpy()`.
- Sono simili agli equivalenti di `{C icon} C`: `{c icon} Malloc()`, `{c icon} free()`, `{c icon} memcpy()`.
- Le chiamate sono bloccanti ma sono presenti delle ***routine asincrone***.
	- Per la sincronizzazione dopo l'uso di una funzione asincrona:
		- `cudaDeviceSynchronize()`.

```c title:"CUDA memory Management"
int *buffer, *d_buffer;
const int SIZE = n * sizeof(buffer);

buffer = (int *) malloc(SIZE);
cudaMalloc((void **)&d_buffer, SIZE);

cudaMemcpy(buffer, d_buffer, SIZE, cudaMemcpyHostToDevice);

/* Computations */

cudaMemcpy(d_buffer, buffer, SIZE, cudaMemcpyDeviceToHost);

cudaFree(d_buffer);

/* Elaborate Output */

free(buffer);
```

### Esecuzione Parallela
>[!info]
>Per l'esecuzione in parallelo, si usa la ***chiamata al kernel***.
>- `{c} function<<<nB, nT>>>();`

> Dove:
- `nB` è il numero di ***blocchi*** che verranno eseguiti.
- `nT` è il numero di ***thread per blocco***.

Ogni thread ha accesso alle seguenti variabili per ***riconoscere la sua posizione***:
- `{c} blockIdx`: indica in quale blocco il thread si trova (`x`, `y` o `z`).
- `{c} threadIdx`: indica in quale blocco il thread si trova (`x`, `y` o `z`).

>[!summary] Indicizzazione di Array con Blocchi e Thread
>`{c} int index = threadIdx.x + blockIdx.x * blockDim.x;`

### Esempio
>[!question] Problema Somma di due Vettori

Creiamo un semplice ***kernel*** per la somma di due interi.
```c
__global__ void add(int *a, int *b, int *c)
{
	*c = *a + *b;
}
```

>[!note] Nota
>`a`, `b` e `c` sono puntatori alla ***memoria di device***.

```c title:"first version"
/* cuda-vecadd0.cu */
int main(void) {
	int a, b, c;            /* host copies of a, b, c */
	int *d_a, *d_b, *d_c;  /* device copies of a, b, c */
	const size_t size = sizeof(int);
	
	/* Allocate space for device copies of a, b, c */
	cudaMalloc((void **)&d_a, size);
	cudaMalloc((void **)&d_b, size);
	cudaMalloc((void **)&d_c, size);
	
	/* Setup input values */
	a = 2; b = 7;
	
	/* Copy inputs to device */
	cudaMemcpy(d_a, &a, size, cudaMemcpyHostToDevice);
	cudaMemcpy(d_b, &b, size, cudaMemcpyHostToDevice);
	
	/* Launch add() kernel on GPU */
	add<<<1,1>>>(d_a, d_b, d_c);
	
	/* Copy result back to host */
	cudaMemcpy(&c, d_c, size, cudaMemcpyDeviceToHost);
	
	/* Cleanup */
	cudaFree(d_a); cudaFree(d_b); cudaFree(d_c);
	return 0;
}
```

>[!hint] Osservazioni
- I nomi `d_*` e `h_*` sono convenzioni per rappresentare una variabile che risiede in memoria ***device*** (`d_`) o in memoria ***host*** (`h_`).
- La funzione `cudaMemcpy()` ha internamente una *barriera di sincronizzazione*.

>[!caution] Il codice attuale esegue una sola somma all'interno della `GPU`.

> Ora, modifichiamo la funzione `add()` per gestire array e non valori

```c
__global__ void add(int *a, int *b, int *c, int n)
{
	int index = threadIdx.x + blockIdx.x * blockDim.x;
	if(index<n)
		c[index] = a[index] + b[index];
}
```

- Differenze nel main
```c title:cuda-vecadd0.cu
#define BLKDIM 1024

/* const size_t SIZE = sizeof(int)  */
const size_t SIZE = N * sizeof(int);

/* add<<<1,1>>>(d_a, d_b, d_c); */
add<<<(N + BLKDIM - 1)/BLKDIM,BLKDIM>>>(d_a, d_b, d_c, N);
```

Il codice lancia ***kernel paralleli***.
- Lancia `{c} (N + BLKDIM - 1)/BLKDIM` *blocchi* di dimensione `{c} BLKDIM`.

![[CUDAMultithreading.png]]
### Specifiche dei Thread
>[!question] Perché aggiungere la complessità dei thread?

Al contrario dei *blocchi paralleli* i threads hanno dei meccanismi in più:

>[!done] Meccanismi di sincronizzazione e condivisione di informazioni

#### Esempio
> Consideriamo una applicazione di uno [[Stencil]] ad un array `1D` di elementi.

>[!abstract] Consideriamo un raggio dello stencil di $3$.
>Ogni elemento in output è la somma di $7$ *elementi in input*.
>- Per semplicità non verranno calcolati i primi e gli ultimi *radius* elementi.

Ogni thread processa un elemento dell'**output**.
- In questo modo ogni elemento in input viene letto $7$ ***volte*** ($2R + 1$).

>[!danger] Gli accessi alla memoria globale sono causa di bottleneck
- A causa della ***bandwidth limitata***.

#### Condivisione della Memoria
>[!info]
> All'interno di un *blocco* i thread possono condividere i dati attraverso la ***memoria condivisa***.

La memoria del blocco è ***estremamente veloce*** e *gestita dall'utente*.
- Tipo una [[Cache]] ma gestita dal programmatore.

> `{c} __shared__`
- Le variabili vengono dichiarate tramite il costrutto `{c} __shared__ int var[1024];`
- Queste variabili non saranno visibili ai ***thread*** in altri ***blocchi***.

```c title:"stencil"
__shared__ int temp[BLKDIM + 2 * RADIUS];
const int gindex = threadIdx.x + blockIdx.x * blockDim.x + RADIUS;
const int lindex = threadIdx.x + RADIUS;
/* ... */
temp[lindex] = in[gindex]; /* Copies blockDim.x elements in one line */
if(threadIdx.x < RADIUS){
	/* Copies the ghost area  */
	temp[lindex - RADIUS] = in[gindex - RADIUS];
	temp[lindex + BLKDIM] = in[gindex + BLKDIM];
}
```