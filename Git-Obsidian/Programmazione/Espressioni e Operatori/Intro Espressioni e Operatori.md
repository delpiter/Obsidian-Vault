## Espressioni e Operatori
---
>[!info] Operatori e Operandi
>Gli ***Operatori e Operandi*** sono _elementi sintattici_ del linguaggio C

>[!tip] Espressione
>Una espressione è una combinazione di operandi e operatori

```c
int x;
// operatore: =, operandi: x e 0
x = 0;

// operatore: +, operandi: x e 1
// operatore: =, operandi: x e x+1
x = x + 1;
```

### Valore e Risultato
>[!info]
>Ad ogni espressione è associato un **tipo** e di conseguenza anche in **valore**
- Distinguiamo due tipi differenti di **valutazioni** che possono essere effettuate dal compilatore per ogni espressione
##### Calcolo del Valore
>[!tldr]
>Calcolo del valore dell'espressione
>>[!example]
>>`x + 1;` calcola un valore
>>Il valore associato all'espressione è il risultato della somma

##### Side-Effect
>[!tldr]
>Modifica del valore di un oggetto nell'espressione
>>[!example]
>>`x = 0;` modifica il contenuto della variabile `x`
>>Il valore associato all'espressione è il valore assegnato ad `x`

### Operatori
>[!info]
>Il linguaggio C mette a disposizione un vasto numero di operatori:

>[!example]
>1. Operatori Aritmetici
>2. Operatori Relazionali
>3. Operatori Logici
>4. Operatori di Assegnamento
>5. Operatori _Bitwise_
>6. Operatori di Accesso e [[../Puntatori/Introduzione Puntatori|puntatori]]

- Gli operatori in C possono essere:
	- **Unari**, solo un operando
	- **Binari**, due operandi
	- **Ternari**, tre operandi
- Gli operatori sono soggetti a regole, precedenze e ordini di valutazione

![[../../Definizioni/Definizioni_Programmazione#Precedenze e Associatività]]