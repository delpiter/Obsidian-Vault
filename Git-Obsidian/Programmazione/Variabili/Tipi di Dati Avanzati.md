![[../../Definizioni/Definizioni_Programmazione#Classificazione dei Tipi di Dati in C]] 


Il Tipo `enum`
---
>[!info] Definizione
>Il tipo **enumerativo** è un tipo di dato che consiste in un insieme ristretto di valori
>La caratteristica principale dei tipi enumerativi è che **ogni elemento** appartenente al tipo ha un **proprio nome**

- I nomi associati agli elementi del tipo sono trattati come **valori costanti**
	- Chiamati *costanti enumerative*

>[!done] Quando usarlo
>In C le **enumerazioni** hanno come unica funzione quella di rendere più leggibile il codice (*syntactic sugar*): possiamo simulare le costanti enumerative con le **macro**.

### Dichiarazione
>[!tldr]
>Per poter dichiarare un tipo di dato *enumerativo* facciamo uso della parola chiave `enum` seguita da una lista di costanti enumerative (**identificatori**).

```c
enum Tag{
	Name1 = constExpr1, //Assignement is Optional
	Name2 = constExpr2,
	...
	NameN = ConstExprN
};
```

- Per convenzione gli identificatori delle costanti enumerative sono in **maiuscolo**
- Il nome del tipo enumerativo (il `tag`) è opzionale

```c
#include<stdio.h>

enum bool {FALSE, TRUE};
```

>[!warning]
>Ogni costante enumerativa può assumere **solo** valori di tipo intero

- Se non specificato, di *default* il primo elemento nella lista ha valore $0$
- Gli elementi successivi sono associati con il **valore dell'elemento precedente** incrementato di $1$

```c
enum days {
	MON = -6 , // -6
	TUE , // -5
	WED , // -4
	THU , // -3
	FRI , // -2
	SAT , // -1
	SUN // 0
};
```

- È possibile avere costanti enumerative con lo **stesso valore** (Poco elegante e sconsigliato)
- Ogni **assegnamento esplicito** viene utilizzato come punto di partenza per gli assegnamenti successivi.
>[!bug] Errore comune
>Gli identificatori in una lista di enumerazioni devono essere **distinti** da altri identificatori di enumerazioni nello **stesso scope**, anche se assumono lo stesso valore.

>[!tldr] Definizione e Dichiarazione
>La **dichiarazione di un tipo** `enum` *dichiara* un nuovo tipo di dato, non riserva la memoria.
>Una **dichiarazione di variabile** di tipo `enum`, riserva memoria e deve essere preceduta, come di consueto, dal nome del tipo enumerativo

```c
enum bool { FALSE , TRUE }; /* definizione */

enum bool flag ; /* dichiarazione */
```
- Il tipo della variabile `flag` è `enum bool`
### Operazioni con `enum`
In C, le variabili di tipo `enum` sono effettivamente variabili di **tipo intero**.
- Possiamo quindi assegnare ad una variabile di tipo `enum` qualsiasi valore di tipo intero, non solo quelli **specificati nella enumerazione**

```c
enum bool { FALSE , TRUE } flag1 = 10 , flag2 = -1;
```

- Possiamo utilizzare le variabili di tipo `enum` con tutti gli operatori applicabili con i tipi di dato interi.
```c
enum bool { FALSE , TRUE } flag1 , flag2 , flag3;
flag1 = FALSE +1; // 1
flag2 = flag1 * TRUE + 10; // 11
flag3 = flag1 / flag2 ; // 0 ( int divison )
```

## Il Tipo `struct`
---
>[!info] Definizione
>Le *strutture* sono tipi di dato che permettono di **raggruppare** una o più variabili di uno o più **tipi differenti**.
>Le strutture aiutano ad **organizzare dati complessi**.
>Permettono di trattare come **un’entità unica** insiemi di variabili logicamente correlate tra di loro
>Nel linguaggio C, possiamo definire strutture utilizzando la parola chiave `struct`

### Dichiarazione di Tipi `struct`
>[!tldr]
>In C una **dichiarazione di struttura** è definita com una **collezione di dichiarazioni** di variabili (chiamate campi o membri), racchiusa tra parentesi graffe e preceduta dalla parola chiave `struct`

```c
struct Tag{
	Type1 Name1;
	Type2 Name2;
	...
	TypeN NameN;
};
```

- Il nome della struttura (`tag`) è opzionale
```c
struct point {
	int x; // x- axis coord
	int y; // y- axis coord
};
```
- Come per i tipi `enum`, la dichiarazione **non riserva memoria**, ma dichiara semplicemente l’esistenza di un nuovo tipo di dato.
- È possibile **annidare** strutture all'interno di strutture

```c
struct point {
	int x; // x- axis coord
	int y; // y- axis coord
};
	
struct line {
	struct point coord1;
	struct point coord2 ;
	} line1 , line2 ;
```

- Limiti dello standard [[../../Definizioni/Definizioni_Programmazione#ISO|ISO C89]]
	- Massimo 15 i **livelli di annidamento** in una singola dichiarazione di struttura;
	- Massimo 127 **membri** in una singola dichiarazione di struttura.

A differenza del tipo `enum`, le dichiarazioni vuote di un tipo `struct` possono essere utilizzate per **dichiarare la struttura** prima della sua **definizione** (forward declaration).
- Parliamo di ***dichiarazione opaca di struttura***.

```c
struct point p1; // forward declaration

struct point { int x; int y; }; // struct declaration
```

- Concetto simile ai [[../Funzioni/Funzioni in C#Dichiarazione|prototipi]] per le funzioni
- Permette anche di definire strutture ***autoreferenziali***
	- Strutture che contengono campi il cui **tipo è la struttura stessa**
	- La *limitazione* che ci impone il linguaggio C è che tali campi debbano essere di tipo [[../Puntatori/Introduzione Puntatori|puntatore]] ***alla struttura***
### Spazio di Allineamento del tipo `struct`
>[!example] Memoria
>In memoria i campi di una struttura sono allocati in **modo contiguo** e nello **stesso ordine** definito dalla dichiarazione.
>A seconda del calcolatore, ***tra un campo e il successivo*** possono essere inseriti degli spazi di memoria di allineamento. Tali **bit di padding** non possono essere utilizzati.
>Serve per rendere la dimensione di memoria della struttura un **multiplo di byte**

```c
struct s {
	char x;
	int y;
};
```
- Tipicamente, `sizeof(struct s)`  $>$  `sizeof(char)+sizeof(int)`
- E’ possibile inizializzare una variabile di tipo struct facendo seguire alla propria dichiarazione un’istruzione di assegnamento con:
	- Una lista di valori tra parentesi graffe
	- Una variabile dello stesso tipo

```c
struct point {
	int x;
	int y;
};

struct line {
	struct point coord1 ;
	struct point coord2 ;
};

struct line l1 = {1}; //(1 ,0) & (0 ,0)
struct line l2 = {1 ,0}; //(1 ,0) & (0 ,0)
```

>[!bug]
>1. Non possiamo inizializzare i membri di una struttura **nella sua dichiarazione**
>2. Possiamo inizializzare con lista di valori una variabile di tipo struct solo al **momento della sua definizione**.
>3. Strutture (anche anonime) dichiarate con gli stessi campi, **sono tipi di dato differente**

```c
struct point {
	int x = 0; // Syntax Error
	int y = 0; // Syntax Error
};
```

```c
struct point { int x; int y ;};

struct point p1 = {0 ,0}; // OK

struct point p2;
p2 = {0 ,0}; // Syntax Error
```

```c
struct { int x; int y;} p1;
struct { int x; int y;} p2 = p1; // Error
struct S1 { int x; int y;} p3 = p1; // Error
struct S2 { int x; int y;} p4 = p3; // Error
```

### Operazioni
>[!tldr]
>Per accedere ai campi di un tipo di dato struct, usiamo l’operatore `.`

- Possiamo assegnare ad un variabile di tipo struct il contenuto di una **variabile dello stesso tipo**
- Non è possibile utilizzare gli altri **operatori** con un tipo di dato `struct`, ma possiamo farlo con i **campi della struttura**.

```c
struct point { int x; int y; } p1 = {0 ,1} , p2 = {1 ,0};

p1 = p2; // OK
p1 = p1 + p2; // Syntax Error
p1.x = p1.x + p2.x; // OK

p1.y = p1.y + p2.y; // OK
if(p1 == p2) // Syntax Error
	printf (" Same coord \n");
if(p1.x== p2.x && p1.y== p2.y) // OK
	printf (" Same coord \n");
```

#### Bit-Field
>[!tldr]
>I **bit-field** sono locazioni di memoria contigue di bit

- Possono rappresentare valori di tipo int (`signed` o  `unsigned`).
- Utilizzati per *salvare spazio di memoria* quando l'insieme di valori da rappresentare è di **molto inferiore** al numero di **valori rappresentabili** con un dato intero
- Possiamo definire *bit-field* in strutture, specificando dopo il nome del campo il simbolo `:` seguito dai numero di bit da utilizzare

```c
struct card_bf {
	unsigned int value : 4; // 13 cards
	unsigned int seed : 2; // 4 seeds
	unsigned int color : 1; // 2 colors
};

struct card {
	unsigned int value ; // cards
	unsigned int seed ; // seeds
	unsigned int color ; // colors
};
```

- La prima struttura avrà tipicamente dimensione `sizeof(int)` mentre la seconda `3*sizeof(int)`

## Il Tipo `union`
>[!info] Definizione
>Nei linguaggi di programmazione una *unione* è un tipo di dato che permette di contenere tipi di dato differenti nella stessa **locazione di memoria**
>Un tipo di dato `union` può essere dichiarato con diversi campi differenti ma solo uno di questi campi può **contenere un valore in un dato momento**

- Nel linguaggio C possiamo dicharare unioni con la parola chiave `union`
- La sintassi è praticamente uguale a quella del costrutto `struct`

```c
union Tag{
	Type1 Name1;
	Type2 Name2;
	...
	TypeN NameN;
};
```

- Come per `enum` e `struct` il `tag` delle `union` è opzionale e la dichiarazione del tipo non riserva memoria
- La dimensione di memoria del tipo di dat union sarà grande a sufficienza per poter contenere **il più grande dei tipi specificati**

```c
union xtype{
	char ctype;
	int itype;
	float ftype
	double dtype;
};
```

Tipicamente, in questo esempio `sizeof(type)` sarà uguale la `sizeof(double)`

### Operazioni
Gli operatori utilizzabili con le `union` sono gli stessi visti per le `struct`
- Valgono gli stessi limiti di annidamento e numero di campi
- La dichiarazione di tipi `union` segue le regole dei tipi `enum` e `struct`
- È possibilie inizializzare **solo il primo membro** nella dichiarazione di variabile
- Il programmatore deve avere cura di ricordare quale campo sta utilizzando

## L'operatore `typedef`
>[!info] Definizione
>L'operatore `typedef` (keyword) permette di creare **nuovi nomi** per i tipi di dato
>La dichiarazione del nuovo tipo è identica alla dichiarazione di una variabile, tranne per il fatto che la dichiarazione è preceduta dalla parola chiave `typedef`
>Il nome dichiarato diventa un *sinonimo* per il tipo di dato dichiarato

```c
typedef double length; // new type length synonym of double
typedef double weight; // new type weight synonym of double
```

- I nuovi tipi sono trattati dal compilatore come **equivalenti ai tipi originali**

L'operatore `typedef` cambia completamente la **semantica delle dichiarazioni**

```c
struct {
	int x;
	int y;
} point1, point2; // variables
```

```c
typedef struct {
	int x;
	int y;
} point1, point2; // types
```