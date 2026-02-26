>[!info]
>[[Linguaggio Kotlin|Kotlin]] è un linguaggio a ***tipizzazione statica***.

> È possibile:
- ***Dichiarare esplicitamente*** il tipo delle variabili.
- Lasciare che sia il compilatore a ***inferire il tipo***.

```kt
val a: Int = 1
val b = 3
```

>[!help] Definizione
>Per la definizione delle variabili ci sono 2 `keyword`
>- `val` e `var`

`val` è usata per dichiarare ***variabili immutabili***.
`var` è usate per dichiarare ***variabili mutabili***.

> Per motivi di performance esiste la keyword `const`, per la creazione di proprietà immutabili il cui *valore è noto a compile-time*.

Una proprietà `const` **DEVE** soddisfare i seguenti requisiti:
- Deve essere inizializzato con valore `String` o un tipo primitivo.
- Non può essere un getter personalizzato
- Deve essere una proprietà top-level, un membro di un object o la dichiarazione di un companion object.

