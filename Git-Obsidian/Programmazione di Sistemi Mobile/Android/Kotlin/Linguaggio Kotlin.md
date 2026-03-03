## Introduzione
---
> Linguaggio sviluppato da **JetBrains**

>[!info]
>`{kt icon} Kotlin` è un linguaggio coinciso, elegante ed espressivo, progettato per ridurre la quantità di boilerplate rispetto a `{java icon} Java`.
>>[!note] Boilerplate
>>Codice boilerplate è una ***porzione di codice ripetuta*** in più sezioni con *poca alterazione*, usata per creare la struttura del programma.

Linguaggio preferito da Google come **linguaggio per sviluppo di app android** dal 2019.

>[!question] Perché Kotlin?
- Supporto allo sviluppo multipiattaforma.
- Maggiore leggibilità.
- Interoperabilità con Java.
- Sicurezza.
- Facilità di apprendimento.
- Community.

## Linguaggio
---
> Kotlin è un linguaggio molto semplice...

```kt
fun main(){
	val name = "stranger"
	println("Hello, $name!")
	print("Counting...")
	for (i in 0..10) {
		print(" $i")
	}
}
```

> ... Kotlin è asincrono ...

```kt
import kotlinx.coroutines.*
suspend fun main() {                         
	val start = System.currentTimeMillis()
	coroutineScope {                         
		for (i in 1..10) {
			launch {                         
				delay(3000L- i * 300)       
				log(start, "Countdown: $i")
			}
		}
	}
	log(start, "Liftoff!")
}

fun log(start: Long, msg: String) {
	println(
	"$msg " +
	"(on ${Thread.currentThread().name}) " +
	"after ${(System.currentTimeMillis() - start)/1000F}s")
}
```

> ... Object Oriented ...

```kt
abstract class Person(val name: String) { abstract fun greet() }

interface FoodConsumer {
	fun eat()
	fun pay(amount: Int) = println("Delicious! Here's $amount bucks!")
}

class RestaurantCustomer(name: String, val dish: String) :
Person(name), FoodConsumer {
	fun order() = println("$dish, please!")
	override fun eat() = println("*Eats $dish*")
	override fun greet() = println("It's me, $name.")
}
```

> ... Funzionale ...

```kt
fun main() {
	val frequentSender = messages
		.groupBy(Message::sender)
		.maxByOrNull { (_, messages) -> messages.size }
		?.key                                           
	println(frequentSender)
	
	val senders = messages
		.asSequence()                                   
		// Get their names
		// Make operations lazy (for a long call chain)
		.filter { it.body.isNotBlank() && !it.isRead }  
		.map(Message::sender)                           
		.distinct()
		.sorted()
		.toList()
	println(senders)
}

data class Message(                                     
	val sender: String,
	val body: String,
	val isRead: Boolean = false,                        
)
val messages = listOf(                                  
	Message("Ma", "Hey! Where are you?"),
	Message("Adam", "Everything going according to plan today?"),
	Message("Ma", "Please reply. I've lost you!"),
)
```

## Null Safety
---
> `{kt icon} Kotlin` offre un supporto sintattico per la gestione dei tipi nullable.

>[!info] Nullable
>Le [[Variabili in Kotlin]] non consentono l'assegnazione del valore `null` a meno che non siano ***dichiarate come nullable***.

```kt
var neverNull: String = "This can't be null"
var nullable: String? = "This can be null"
```

### Lavorare con variabili nullable
> Per lavorare con valori nullable, ci sono 2 possibilità.

>[!tldr] Smart cast

```kt
fun describeString(str: String?) = 
	if(str != null && str.length > 0){
		"String of length ${str.length}"
	} else {
		"Empty or null string"
	}
```

>[!help] Operatori Appositi
- `{kt icon} ?.` **safe call**.
- `{kt icon} !!` **non null assertion**.
- `{kt icon} ?:` **elvis**.


```kt
fun describeString(str: String?) = 
	"String of length ${str?.length ?: 0}"
```
