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
### Esecuzione Parallela
>[!info]
>Per l'esecuzione in parallelo, si usa la ***chiamata al kernel***.
>- `{c} function<<<nB, nT>>>();`

> Dove:
- `nB` è il numero di ***blocchi*** che verranno eseguiti.
- `nT` è il numero di ***thread per blocco***.

Ogni thread ha accesso alle seguenti variabili per ***riconoscere la sua posizione***:
- `{c} blockIdx`: indica in quale blocco il thread si trova (`x`, `y` o `z`).
- `{c} threadIdx`: indica in quale indice del blocco il thread si trova (`x`, `y` o `z`).

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

![[attachements/CUDAMultithreading.png]]

### Esecuzione con Blocchi Multidimensionali
>[!example] Esempio: Moltiplicazione Matrice $\times$ Matrice

![[attachements/MatrixMultiplication.png]]

Decomponiamo la matrice risultato `r` in blocchi quadrati.
- Assegniamo ciascun blocco ad un ***blocco di thread***.

#### Impostare i Blocchi di Thread con più Dimensioni
>[!abstract] `{c icon} dim3`
>Il tipo di dato `{c icon} dim3` è usato per definire una struttura a una, due o tre dimensioni, per i [[CUDA#Anatomia di una GPU|blocchi]] o per la [[CUDA#Anatomia di una GPU|griglia]].

```c title:"Multidimensional Blocks"
dim3 grid1(3);
// Defines a variable "grid" representing a 3x1x1 block.
dim3 grid2(3,4);
// Defines a variable "grid2" representing a 3x4x1 block.
dim3 blk(3,4,7);
// Defines a variable "blk" representing a 3x4x7 block.

dim block(16);
myKernel<<<grid1,block>>>();
// Lanch 3 blocks, 16 threads per block (1D)

myKernel<<<grid2, blk>>>();
// Launch 3x4 blocks (3x4x7) threads per block (3D)
```

>[!example] Prodotto Matrice $\times$ Matrice

```c++
#define BLKDIM 32

int main (void) 
{
	...
	dim3 block(BLKDIM, BLKDIM);
	dim3 grid((N+BLKDIM-1)/BLKDIM, (N+BLKDIM-1)/BLKDIM);
	
	matmul<<<grid, block>>>(d_p, d_q, d_r, N);
	...
}
```

Ogni thread calcola un elemento $r[i][j]$ della matrice $r$.
```c
const int i = blockIdx.y * blockDim.y + threadIdx.y;
const int j = blockIdx.x * blockDim.x + threadIdx.x;
```

>[!fail] Inefficienza
>Un elemento di ciascuna matrice viene letto $N$ volte per calcolare il prodotto.

Per ridurre il numero di letture dalla memoria globale possiamo usare la ***memoria condivisa*** per mantenere i dati necessari alla computazione.
>[!missing] Problema
>Questo richiederebbe $2\times BLKDIM \times n$ elementi memorizzati nella memoria condivisa, che potrebbe eccedere il *massimo del device*.

> Soluzione:
- Possiamo dividere le "*strisce*" di matrice in *piccoli blocchi* di dimensione $BLKDIM \times BLKDIM$ elementi ciascuno.

Si opera su due blocchi alla volta (uno di $q$ e uno di $p$).
$$
R = P_{1}\times Q_{1} + P_{2}\times Q_{2} +P_{3} \times Q_{3}
$$
>[!done] Per ogni blocco
>1. Copia gli elementi dei piccoli quadrati da $p$ e $q$ nella *memoria condivisa*.
>2. Calcola il prodotto matrice per matrice `local_p`$\times$`local_q` in ***parallelo***.
>3. Passa al blocco successivo.

![[attachements/MatrixProductShared.png]]

```c title:"Matmul Kernel"
__global__ void matmul( float *p, float *q, float *r, int n )
{
	__shared__ float local_p[BLKDIM][BLKDIM];
	__shared__ float local_q[BLKDIM][BLKDIM];
	
	const int bx = blockIdx.x; const int by = blockIdx.y;
	const int tx = threadIdx.x; const int ty = threadIdx.y;
	const int i = by * BLKDIM + ty; 
	const int j = bx * BLKDIM + tx; 
	
	float v = 0.0;
	
	for (int m = 0; m < n; m += BLKDIM) { 
		local_p[ty][tx] = p[i*n + (m + tx)];
		local_q[ty][tx] = q[(m + ty)*n + j];
		__syncthreads();
		
		for (int k = 0; k < BLKDIM; k++) { 
			v += local_p[ty][k] * local_q[k][tx];
		}
		__syncthreads();
	}
	r[i*n + j] = v;
}
```

### Chiamate a Funzione
>[!help] Il qualificatore `{c icon} __device__`
>Il qualificatore `{c icon} __device__` comunica al compilatore che la funzione definita deve essere compilata per la `GPU`.

La funzione potrà essere chiamata solamente da ***codice device***.

>[!warning] Attenzione
>In alcune versioni (*vecchie*) di `CUDA` il compilatore non supporta le *chiamate a funzione*.

`{c} __device__` può essere usato anche con le variabili per allocare staticamente delle variabili nel ***device***.
- Per trasferire informazioni da/a variabili `{c} __device__` bisogna usare:
	- `{c} cudaMemcpyToSymbol(d_buf, buf, BLKDIM*sizeof(float));`
	- `{c} cudaMemcpyFromSymbol(buf, d_buf, BLKDIM*sizeof(float));`

Il compilatore si comporta come un preprocessore ***copiando l'intero corpo della funzione***.
>[!danger] `CUDA` **NON** supporta algoritmi ricorsivi

Analogamente il qualificatore `{c icon} __host__` definisce una funzione che viene eseguita sull'***host***.
- Può essere solo chiamata da ***codice host***.
- È il comportamento di default quando nè `{c icon} __global__` nè `{c icon} __device__` è specificato.

>[!done] Si possono usare entrambi `__host__` e `__device__` nella stessa funzione

Il compilatore produrrà *due versioni* della funzione.

### Errori
>[!bug] Info
> Tutte le chiamate **API** `CUDA` ritornano un codice di errore (`{c} cudaError_t`) che può indicare:
> - Un errore nella chiamata **API**.
> - Un errore in una **operazione asincrona precedente**.

`{c} cudaSuccess` significa che non c'è stato errore.

Per recuperare l'*ultimo error code*, si usa la funzione:
- `{c icon} cudaError_t cudaGetLastError(void);`
