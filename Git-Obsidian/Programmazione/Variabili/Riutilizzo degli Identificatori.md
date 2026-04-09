## Introduzione
---
>Tipi di dato che fanno uso di [[../Introduzione Programmazione/Linguaggio C#Identificatore|identificatori]] definiti dal programmatore

- Nomi e parametri di macro
- Nomi di [[Introduzione Variabili|variabili]] e [[../Funzioni/Funzioni in C#|funzioni]]
- Nomi di [[Tipi di Dati Avanzati#Il Tipo `struct`|strutture]], [[Tipi di Dati Avanzati#Il Tipo `union`|unioni]] e [[Tipi di Dati Avanzati#Il Tipo `enum`|enumerazioni]]
- Nomi di campi in strutture e unioni
- Nomi di costanti enumerative
- Nomi di tipi definiti dal programmatore ([[Tipi di Dati Avanzati#L'operatore `typedef`|typedef]])

Vediamo le regole generali che ci permettono di riutilizzare un identificatore in un programma

### Namespace
>[!tldr]
>Il `namespace` è un insieme di classi in cui sono partizionati i tipi di identificatori in un programma C
>> Ci sono 5 classi di `namespace`
>> 1. I *tag* di `struct`, `union` e `enum`
>> 2. I *campi* di `struct` e `union`
>> 3. Le *label* per il costrutto `goto`
>> 4. Tutti gli altri **identificatori** (variabili e costanti enumerative)
>> 5. Un `namespace` a parte per macro e argomenti di macro

È possibile riutilizzare gli stessi identificatori **se appartengono a namespace diversi**