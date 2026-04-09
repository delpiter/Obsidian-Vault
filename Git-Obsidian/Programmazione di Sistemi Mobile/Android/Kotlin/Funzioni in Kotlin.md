> Il [[Linguaggio Kotlin]] ha la seguente sintassi per le funzioni:

```kt
fun printMessage(message: String): Unit {
	println(message)
}
```
- Una semplice funzione che accetta un parametro `string` e restituisce un `Unit` (`void`).

```kt
fun printWithPrefix(message: String, prefix: String="Info"): Unit{
	println("[$prefix] $message")
}

/* How to Invoke */
printWithPrefix("Hello", "Log")
printWithPrefix("Hello")
printWithPrefix(prefix = "Hello", message: "Log")
```
- Funzione che accetta un parametro ***con un valore di default***.

>[!hint] Se il corpo di una funzione è composto da una singola istruzione, può essere sepmlificato

```kt
fun sum(x: Int, y: Int) = x + y
```

#### Extension Functions
> Kotlin permette di ***estendere classi o interfacce esistenti*** tramite le extension.

```kt
fun Int.pow(exp: Int): Int = if(exp == 0) 1 else this * pow(exp - 1)

fun main() {
	println(2.pow(3)) // 8
}
```

#### Infix Functions
> Le funzioni con ***un solo parametro*** possono essere trasformate in ***infix functions***.

>[!hint] Una infix function può essere richiamata come un operatore

```kt
infix func Int.pow(exp: Int): Int =
	if(exp == 0) 1 else this * pow(exp - 1)
	
fun main(){
	println(2 pow 3) // 8
}
```

#### Operator Functions
> Alcune funzioni possono essere promosse a operatori, tramite la keyword `operator`.

>[!hint] Consente di invocarle con il simbolo dell'operatore corrispondente

```kt
operator fun Int.times(str: String) = str.repeat(this)
println(3 * "Bye ") // Bye Bye Bye

operator fun String.get(range: IntRange) = substring(range)
val str = "Always forgive your enemies;"
println(str[0..14]) // Always Forgive
```

#### Funzioni Variadiche
> È possibile avere un numero arbitrario di parametri di input ([[../../../Programmazione/Funzioni/Funzioni in C#Funzioni variadiche|Funzioni variadiche]])

Funzioni con parametri definiti con la keyword `vararg`.

```kt
fun printAll(vararg messages: String){
	for(m in messages) println(m)
}

fun log(vararg entries: String) {
	printAll(*entries) // Spread operator
}

log("Str1", "Str2", "Str3", "Str4")
```

