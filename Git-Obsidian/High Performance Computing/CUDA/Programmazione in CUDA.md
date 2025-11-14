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
- Sono simili agli equivalenti di `{C icon} C`: `{c icon} Malloc()`, `{c icon} free()`, `{c icon} memcpy()`


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
