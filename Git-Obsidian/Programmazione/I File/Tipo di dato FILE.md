## La Struttura `FILE`
---
>[!info] Definizione
>Il tipo di dato `FILE` è una struttura che contiene una lista di campi che permettono di gestire le operazioni di **apertura**, **chiusura**, **lettura** e **scrittura** del [[Introduzione ai Files|file]]

- Il programmatore dovrebbe utilizzare il [[../Variabili/Tipi di Dati|tipo di dato]] `FILE` soltatnto tramite le [[../Funzioni/Funzioni in C|funzioni]]  di libreria fornite, senza accedere direttamente ai campi interni della struttura
- La cosa importante da capire è che non si lavora realmente su un file, ma sul suo puntatore
	- Il [[../Puntatori/Introduzione Puntatori|puntatore]] è riferito al file preso in considerazione

### I File *standard*
Il C gestisce tutti i *device* tramite l'interfaccia unica `FILE`
>[!info]
>Esistono tre *stream standard* che sono aperti di default in un programma in esecuzione per poter comunicare con tastiera e monitor

| Tipo | Nome | Device |
| ---- | ---- | ---- |
| Standard Input | `stdin` | Tastiera |
| Standard Output | `stdout` | Monitor |
| Standard Error | `stderr` | Monitor |
- Le variabile `stdin`, `stdout` e `stderr` sono di tipo puntatore alla struttura `FILE`

## Apertura e Chiusura
---
### Apertura di un FILE
>[!tldr]
>Per potere lavorare con un file su memoria di massa è necessario creare uno stream associato al file

```c
FILE *fopen (const char *filename, const char *mode);
```
- La funzione `fopen` apre e associa uno stream con il file il cui nome è specificato nella stringa `filename`
- Restituisce un puntatore all'oggetto che controlla lo stream, oppure `NULL` se l'operazione non è stata possibile

Le modalità di apertura sono specificate nella stringa `mode`

| Mode | String | Description |
| ---- | ---- | ---- |
| Read | `"r"` | Opens an existing file in read-only mode and sets the pointer at the start of the file |
| Write | `"w"` | Opens an existing file in writing mode. If the file exists, its cleared of its content otherwise it creates the file |
| Append | `"a"` | Opens an existing file in writing mode. If the file does not exists its created otherwise it sets the pointer to the end of the file so the old data remains |
| Read and Write | `"r+"` | Opens a file in read and write mode, without clearing its content |
| Write and Read | `"w+"` | Opens a file in write and read mode, clearing its content |
| Read and Append | `"a+"` | Opens a file in read mode from the start of the file and write mode eat the end of the file |
- Per aprire uno stream binario è sufficiente aggiungere il carattere `b` nella stringa `mode`

```c
char *file = "data.txt";
FILE *fp   = fopen(file, "r");

if(fp == NULL)
	printf("%s: file does not exists or cannot be opened\n", file);
else
	printf("%s: file succesfuly opened\n", file);
```

```c
char *file = "data.txt";
FILE *fp   = fopen(file, "w");

if(fp == NULL)
	printf("%s: file cannot be created or cannot be opened\n", file);
else
	printf("%s: file succesfuly opened\n", file);
```

### Chiusura di un FILE
>[!tldr]
>Ad eccezione degli *stream standard*, tutti gli stream aperti dovrebbero essere chiusi **prima della terminazione del programma**
>Nel caso di stream di scrittura, chiusura assicura che tutte le operazioni di scrittura siano concluse

```c
int fclose(FILE *stream);
```

- La funzione `fclose()` ritorna `0` se l'operazione di chiusura è andata a buon fine oppure `EOF` se ci sono stati dei problemi

```c
char *file = "data.txt";
FILE *fp   = fopen(file, "w");

if(fclose(fp) != EOF)
	printf("%s: file succesfully closed\n", file);
else
	printf("%s: something went wrong while closing the file\n", file);
```

## Lettura e Scrittura
---
### Scrittura
>[!tldr]
>Per poter stampare dati in formato testuale su un file possiamo utilizzare le seguenti funzioni delal libreria `stdio.h`

```c
int fprintf(FILE *stream, const char *format, ...);

int fputc(int c, FILE *stream);

int fputs(const char *s, FILE *stream);
```

Le funzioni sono interamente equivalenti alle funzioni `printf()`, `putc()` e `puts()`
- Per poterle utilizzare come stream di output è sufficiente passare `stdout` o `stderr` come argomento `stream`

### Lettura
>[!tldr]
>Per poter leggere il contenuto di un file possiamo utilizzare le seguenti funzioni della libreria `stdio.h`

```c
int fscanf(FILE *stream, const char *format, ...);

int fgetc(FILE *stream);

char *fgets(char *s, int n, FILE *stream);
```

Le funzioni sono *quasi* equivalento aòòe funzioni `scanf()`, `getc()` e `gets()`
- Per poterle utilizzare come stream di output è sufficiente passare `stdout` o `stderr` come argomento `stream`

## Esempi
---
```c
// lc.c: line count
#include <stdio.h>

int lc( char * filename ) {
	int c, n = 0;
	FILE *in;
	
	if (( in = fopen ( filename ,"r")) != NULL )
	while ((c = fgetc (in )) != EOF )
	n += c == ’\n’; // increment counter if the character is a new line
	
	fclose (in);
	return n;
}
```

```c
// cc.c: character count
#include <stdio .h>

int cc( char * filename ) {
	int c, n = 0;
	FILE *in;
	
	if ((in = fopen(filename ,"r")) != NULL)
	while ((c = fgetc(in)) != EOF)
	n ++; // increment counter for every character
	
	fclose (in);
	return n;
}
```