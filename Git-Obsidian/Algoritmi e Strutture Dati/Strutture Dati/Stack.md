## Lo Stack - *Pile*
---
>[!info] Descrizione
>>[!tip] Dati
>>I dati sono un *insieme* $S$ di *elementi*
>
>>[!example] Operazioni
>>Uno ***stack*** ha le seguenti operazioni possibili:
>>- ***PUSH***
>>	- *Inserimento* di un elemento in $S$
>>- ***POP***
>>	- *Rimozione e restituzione* dell'**ultimo elemento** inserito in $S$
>
>>[!done] Politica
>>Lo *stack* ha una politica **LIFO**
>>- ***L***ast ***I***n ***F***irst ***O***ut

![[attachements/Stack.webp]]
### Push
```java
void Push(S,o)
{
	S.top = S.top+1;
	S[S.top] = o;
}
```

### Pop
```Java
int Pop(S)
{
	o = S[S.top];
	S.top = S.top-1;
	return o;
}
```