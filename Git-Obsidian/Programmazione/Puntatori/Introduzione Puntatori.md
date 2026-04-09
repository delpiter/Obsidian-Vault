## Puntatori
---
Una dichiarazione di [[../Variabili/Introduzione Variabili|variabile]] comporta l'allocazione di un certo numero di **celle contigue di memoria RAM**
- Ad ogni cella è associato un **indirizzo di memoria univoco**

>[!info] Puntatore
>Un **puntatore** è una variabile che permette di memorizzare un indirizzo di memoria
>Diciamo che un puntatore **referenzia** una cella di memoria
>Possiamo accedere al valore del contenuto nella cella di memoria referenziata tramite la **dereferenziazione** del puntatore

Esempi di puntatori nella vita di ogni giorno:
- Pagina di un libro $\to$ Cella di memoria
- Numero di pagina $\to$ Indirizzo della cella
- Indice del libro $\to$ Contiene riferimenti alle pagine del libro

### Dichiarazione
>[!tldr]
>Una dichiarazione di variabile puntatore è una dichiarazione di variabile in cui il nome della variabile è preceduto dal simbolo `*`
>`<type> *<name>;`

- Il tipo del puntatore indica il contenuto dell'indirizzo di memoria puntato

```c
char a;  //char type variable
char *p; //pointer to char type variable

int i;  //int type variable
int *j; //pointer to int type variable
```

- È possibile dichiarare puntatori *generici*, senza specificare il tipo puntato
	- Utilizzando la [[../Introduzione Programmazione/Linguaggio C#Keywords|keyword]] `void`
- Per poterlo utilizzare è necessario un cast al tipo specifico

### Assegnamento
>[!tldr]
>Una variabile di tipo puntatore può contenere solo **indirizzi di memoria** o il valore costante `NULL`
>![[attachements/Pointers.png]]

- Gli indirizzi di memoria ottenuti tramite [[../Espressioni e Operatori/Intro Espressioni e Operatori#Operatori|l'operatore]] `&` possono essere assegnati ad una variabile di tipo puntatore

```c
int x = 1;
int *p = &x;
int *q = NULL;

q = &x;
```

### `NULL`
>[!tldr]
>La costante `NULL` è una macro definita dall'implementazione in `stdlib.h`
>Il valore `NULL` rappresenta un indirizzo di memoria *non accessibile*
>Un puntatore a `NULL` viene inteso come un puntatore che non punta a nulla

- Lo standard C impone una equivalenza tra la costante $0$ e `NULL`
- Le seguenti espressioni di test sono tutte equivalenti

```c
int c, *p = &x;
if(p!= NULL) { x = 1; }

if(p!= 0) { x = 1; }

if(p) { x = 1; }
```

### Tipo del puntatore
I puntatori contengono solamente indirizzi di memoria, è necessario quindi fornire al compilatore il tipo di dato che si trova in quella cella
>[!tldr]
>Questa informazione è **necessaria** per indicare al compilatore:
>1. La dimensione in `byte` dell'oggetto puntato
>2. Come **interpretare il contenuto** della locazione di memoria puntata

- 
>[!bug]
>Assegnamenti di indirizzi di memoria non compatibili **non sono sintatticamente proibiti**
>L'accesso a tale contenuto di memoria tramite il puntatore può causare comportamenti **non definiti**


### Dimensione di Memoria
Esattamente come per gli altri [[../Variabili/Tipi di Dati|tipi di dato]] la dimensione in `byte` di un puntatore può essere determinata utilizzando l'operatore `sizeof()`

>[!tldr]
>Lo standard non impone vincoli sulla dimensione del tipo di dato puntatore
>Non impone che i puntatori di tipi differenti abbiano tutti la stessa dimensione
>>[!example] Eccezione
>>Come unica restrizione, lo standard impone la seguente proprietà
>>> Possiamo convertire un qualsiasi dato puntatore in tipo `void *` e poi riconvertirlo al tipo originale, il **valore originale deve essere invariato**

### Dereferenziazione

>[!tldr]
>Per poter *accedere* al contenuto dell'oggetto puntato dal puntatore utilizziamo l'operatore di **dereferenziazione** `*`

- Il risultato dell'applicazione dell'operatore `*` è **l'oggetto puntato**
- È possibile modificare il valore di una variabile tramite la dereferenziazione

```C
int x = 1;
int *p = &x;

*p = 2;   // x = 2
*p += 1;  // x = 3
*p *= *p; // x = 9
(*p)++;   // x = 10
```

Dereferenziare puntatori non inizializzati o inizializzati non correttamente, causa un comportamento *non definito*

```C
int *p; // not initialized

*p = -1;

printf("%d \n", *p); //undefined operation
```

- Dereferenziare un puntatore inizializzato a `NULL` causa un comportamento *non definito*
	-  Il programma andrà quasi sicuramente in **crash**

## Puntatori a `const`
Puntatori a valori `const` (read-only) sono puntatori di cui **non è possibile modificare il contenuto**

```C
int x = 1;
const int *p = &x;

x = 2; // OK
*p = 3;// Syntax Error
```

- In perfetta simmetria:

```C
const int x = 1;
int *p = &x;

x = 2; // Syntax Error
*p = 3;// OK
```