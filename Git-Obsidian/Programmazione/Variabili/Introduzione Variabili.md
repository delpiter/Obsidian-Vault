## Variabile
---
>[!info] Definizione
>Una **Variabile** è una porzione di memoria contenente dati che possono eventualmente essere modificati durante l'esecuzione del programma

- Ogni variabile deve essere **dichiarata** prima di essere utilizzata

Lo standard C fa una precisa distinzione tra concetti di  _dichiarazione_ e _definizione_
### Dichiarazione
>[!tldr]
>Specifica l'interpretazione e gli attributi di un identificatore
>La _dichiarazione_ di variabile è una istruzione che permette di associare alla variabile:
>1. Un identificativo, che rappresenta il nome della variabile
>2. Un tipo, che definisce la dimensione della variabile in termini di occupazione di memoria
>>[!example] Sintassi
>>`<Tipo> <Identificatore>;`

```c
char symbol;
float height;
int X;
int x;
double temperature, pressure;
```

### Definizione
>[!tldr]
>Dichiara un identificatore e riserva lo spazio in memoria per tale identificatore
>Consente al compilatore di individuare un'area di memoria da riservare alla variabile
>Ogni riferimento al nome della variabile all'interno del codice è un riferimento al contenuto di tale locazione di memoria
>>[!note] Nota Bene
>>Al momento dedlla definizione/dichiarazione, ad una variabile non viene assegnato nessun valore:
>>Non possiamo fare nessuna assunzione sul contenuto della locazione di memoria, diciamo che il valore della variabile è **_non definito_**

- È possibile inizializzare il contenuto di una variabile al momento della definizione untilizzando **l'operatore di assegnamento** `=`

```c
char symbol = 'A';
float height = 1.75;
int X = -1;
int x;
double temperature = 100, pressure = 1.5;
```

### Dichiarazione vs Definizione
Citiamo direttamente lo standard [[../../Definizioni/Definizioni_Programmazione#ISO|ISO C89]] per la differenza nel linguaggio C
>[!quote]
>*A declaration specifies the interpretation and attributes of a set of identifiers.*
>*A declaration that also causes storage to be reserved for an object or function named by an identifier is a definition*