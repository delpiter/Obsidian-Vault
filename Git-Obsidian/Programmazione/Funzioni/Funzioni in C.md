### Le Funzioni in C
>[!tldr]
>Un programma in C è costituito da un insieme di [[Introduzione Funzioni]]
>>[!done] Main
>>Il `main()` è una funzione, ogni programma deve contenere esattamente una funzione `main()`
>>In particolare, la funzione `main()` è il punto di ingresso di ogni programma C

- Le funzioni hanno diverse regole sintattiche che ci permettono di *costruire* funzioni

#### Dichiarazione
>[!tldr]
>Una ***dichiarazione*** di una funzione, detta anche **prototipo**, specifica:
>1. Il [[../Variabili/Tipi di Dati#Tipizzazione|tipo di dato]] *restituito* dalla funzione
>2. Il *nome* (identificatore) della funzione
>3. I tipi e i nomi degli eventuali *argomenti* della funzione
>`<type> <func name>(<type1> [<Arg1>],...,<typeN> [<ArgN>]);`
-  Esempio
```c
int square(int x);

void print_square(int x);

int seconds(int h,int m, int s);
```


- La dichiarazione ci permette di capire unicamente come **invocarla**
	- Specifica ***quali e quanti*** argomenti prende in input, oltre al tipo del valore di ritorno

- La dichiarazione di funzione permette al compilatore di verificare che la funzione venga invocata correttamente
	- Scopo: evitare comportamenti semanticamente **indefiniti**

#### Definizione
>[!tldr]
>Una **definizione** di una funzione è costituita da due parti
>>[!info] **Dichiarazione della funzione**
>>Come per i prototipi è necessario specificare:
>>1. Tipo di dato restituito
>>2. Nome della funzione
>>3. Argomenti della funzione
>
>>[!info] **Corpo della funzione**
>>Porzione di codice racchiusa tra parentesi graffe che comprende le seguenti componenti opzionali
>>1. Dichiarazione di variabili locali
>>2. Istruzioni
>>3. Istruzione return con eventuale valore di ritorno
>>```
>><type> <func name>(<type1> [<Arg1>],...,<typeN> [<ArgN>]){
>>	[<local variables>]
>>	[<instruction block>]
>>	[return [<expression>];]
>>}
>>```

##### Funzioni variadiche
>[!tldr]
>Il linguaggio C permette di definire funzioni ***variadiche***:
>Funzioni che hanno un numero variabile di argomenti
>>[!example]
>>Le funzioni `printf()` e `scanf()` sono esempi di funzioni variadiche
>
>I prototipi delle funzioni variadiche sono definiti utilizzando la notazione **ellissi**
>`<type> <FuncName>(type1 <Arg1>, ...)`
>L'**ellissi** (`...`) indica che la funzione è variadica
>

- È necessario specificare almeno **un argomento fisso** (il primo)
	- La funzione può essere definita con altri argomenti fissi
- L'ellissi deve essere specificata come ultimo argomento nella lista

#### Invocazione
>[!tldr]
>L'**invocazione** o **chiamata** di funzione è un'istruzione che permette l'esecuzione della funzione
>>[!done] Semantica
>>Quando una funzione `F()` viene invocata nel corpo di una funzione `G()`,
>>l'esecuzione di `G()` è sospesa e si passa ad eseguire le istruzioni contenute in `F()`
>>Quando `F()` termina la sua esecuzione, si prosegue con le istruzioni di `G()` successive al punto in cui `F()` è stata chiamata

##### Valore di Ritorno
Una funzione **ritorna** (o **restituisce**) un valore tramite il costrutto `return`
- `return [<espression>]`
- L'esecuzione dell'istruzione `return` causa la terminazione della funzione e il **ritorno** del controllo al chiamante

##### Visibilità
La **Visibilità** di una funzione dipende dal punto in cui è dichiarata/definita
- Una funzione è visibile da tutte le funzioni nello stesso file che ***seguono*** la sua dichiarazione/definizione
- In caso di assenza di prototipo la funzione sarà visibile unicamente alle funzioni definite **"dopo"** la definizione della funzione

##### Passaggio dei Parametri
Una funzione può fare uso di **parametri** (o **argomenti**) per svolgere il proprio compito
1. **Parametri Formali**: Parametri dichiarati nella definizione/dichiarazione
2. **Parametri Attuali**: Parametri passati al momento della chiamata
- In C il **passagio dei parametri** avviene secondo la modalità del [[../../Definizioni/Definizioni_Programmazione#Passaggio per Valore e per Riferimento|passaggio per valore]]

##### Ordine di Valutazione
Lo standard [[../../Definizioni/Definizioni_Programmazione#ISO|ISO]] non impone nessuna regola sull'ordine di valutazione dei parametri attuali di una funzione
- L'ordine di valutazione degli argomenti **non è specificato**
