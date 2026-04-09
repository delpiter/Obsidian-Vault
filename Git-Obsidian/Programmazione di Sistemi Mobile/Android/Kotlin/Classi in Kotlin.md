> Il [[Linguaggio Kotlin]] è un linguaggio ***orientato agli oggetti***.
## Classi
---
>[!info] Dichiarazione
>La dichiarazione di una classe è composta dal ***nome della classe***, dalla sua ***intestazione*** e dal ***corpo***.

Sia l'intestazione che il corpo sono facoltativi.

```kt
class Customer

class Contact(val id: Int, var email: String)

fun main() {
	val customer = Customer()
	val contract = Contract(1, "mary@gmail.com")
	println(contact.id)
	contact.email = "jane@gmail.com"
}
```

### Ereditarietà
> `{kt icon} Kotlin` supporta pienamente il tradizionale meccanismo di [[../../../Ingegneria del Software/Paradigma ad Oggetti#Ereditarietà|ereditarietà]] object-oriented.

>[!info] `open`
>Le classi e i metodi in **Kotlin** sono `final` di default, se si desidera consentire l'ereditarietà e l'override, è necessario contrassegnare la classe/metodo con `open`.

```kt
open class Dog {               
	open fun sayHello() {      
		println("wow wow!")
	}
}
class Yorkshire : Dog() {      
	override fun sayHello() {
		println("wif wif!")
	}
}
fun main() {
	val dog: Dog = Yorkshire()
	dog.sayHello()
}
```

> È possibile definire delle proprietà private:

```kt
class C {
	private val _elementList = mutableListOf<Element>()
}
```

### Special Classes
#### Data Classes
>[!info]
>Le ***data classes*** semplificano la creazione di classi usate per modellare dati.

Una *data class* implementa automaticamente i metodi:
- `equals()` e `hashCode()`
- `toString()` nella forma `"ClassName(prop1=value, prop2=value)"`
- `componentN()` per il *desctructuring*.
- `copy()`

Il costruttore deve avere ***almeno un elemento***.
- Tutti i parametri devono essere assegnati come `val` o `var`, diventando proprietà della classe.

Il compilatore usa solo le **proprietà definite nel costruttore** per le *funzioni autogenerate*.
- Per escludere una proprietà dalle implementazioni generate, va dichiarata all'interno del corpo della classe.
- È comunque possibile fare l'override dei metodi auto implementati.

#### Enum
>[!info]
>Gli `enum` sono classi usate per modellare tipi che rappresentano un ***set finito di valori distinti***.

```kt
enum class State {
	IDLE, RUNNING, FINISHED
}

fun main() {
	val state = State.RUNNING
	val message = when (state) {
		State.IDLE -> "Idle"
		State.RUNNING -> "Running"
		State.FINISHED -> "Finished"
	}
	println(message)
}
```

Anche gli enum possono accettare parametri nel costruttore e contenere funzioni.

```kt
enum class Color(val rgb: Int) {
	RED(0xFF0000),
	GREEN(0x00FF00),
	BLUE(0x0000FF),
	YELLOW(0xFFFF00);
	fun containsRed() = (this.rgb and 0xFF0000 != 0)
}
```

#### Sealed Classes
>[!info]
>Una classe ***sealed*** è considerata abstract e può avere sottoclassi *solo all'interno dello stesso package in cui è dichiarata*.

```kt
sealed class Mammal(val name: String)
class Cat(val catName: String) : Mammal(catName)
class Human(val humanName: String, val job: String) : Mammal(humanName)

fun greetMammal(mammal: Mammal): String {
	when (mammal) {
		is Human->
		return "Hello ${mammal.name}; Work: ${mammal.job}"
		is Cat-> return "Hello ${mammal.name}"
	}
}

fun main() = println(greetMammal(Cat("Snowy")))
```

### Properties
> `{kt icon} Kotlin` offre varie funzionalità per la definizione delle proprietà di una classe:

>[!info] Proprietà Semplice
- `{kt icon} var height: Int = 2`

>[!abstract] Proprietà Read only con Getter
- `{kt icon} val area get() = this.side * this.side`

>[!caution] Proprietà con Setter Privato

```kt
class Counter {
	var count: Int = 0
		private set
	fun inc() = count++
	fun dec() = count--
}
```

>[!hint] Proprietà con backing field

```kt
var rating: Int? = null
	get() {
		if (field == 5) {
			println("This is an amazing book!")
		}	
		return field
	}
	
	set(value) {
		if (value != null && value !in 1..5) {
			throw IllegalArgumentException()
		}
		field = value
	}
```

### Delegates
> `{kt icon} Kotlin` supporta il pattern delegate a livello di linguaggio tramite la keyword `by`

>[!example] Esempio
>Supponiamo di voler creare una proprietà lazy, che non viene inizializzata alla creazione di un oggetto, ma solo al primo accesso alla proprietà stessa.

Potremmo usare un *delegate* per rendere la funzionalità riutilizzabile.

```kt
class MyLazy<T>(val initializer: () -> T) {
	var instance: T? = null
	
	operator fun getValue(thisRef: Any?, prop: KProperty<*>): T { 
		if (instance == null) instance = initializer()
			return instance!!
	}
}

class LazyProperty(val initializer: () -> Int) {
	val lazyValue by MyLazy(initializer)
}
```

>[!hint] Questa funzionalità è già fornita dalla standard library di `{kt icon} kotlin` tramite la funzione `lazy`

#### Object
>[!info]
>La keyword `object` identifica un tipo di dato con una singola implementazione, similmente al ***pattern singleton***, garantisce che venga creata *una sola istanza* di una certa classe.

```kt
fun rentPrice(
	standardDays: Int, 
	festivityDays: Int, 
	specialDays: Int
	): Unit {
		val dayRates = object {
			var standard: Int = 30 * standardDays
			var festivity: Int = 50 * festivityDays
			var special: Int = 100 * specialDays
		}
	val total = dayRates.standard + dayRates.festivity + dayRates.special
	print("Total price: $$total")
}

fun main() {
	rentPrice(10, 2, 1)
}
```

##### Companion Objects
> La dichiarazione di un `object` in una classe ha un caso speciale.

>[!hint] Companion Object
>Il funzionamento è simile a quello dei *metodi statici* in `{java icon} Java`: È possibile richiamare i membri del companion object usando il nome della classe.

```kt
class BigBen { 
	companion object Bonger { 
		fun getBongs(nTimes: Int) { 
			for (i in 1 .. nTimes) {
				print("BONG ")
			}
		}
	}
}
```

#### High-Order Functions
> Funzione che accetta un'altra funzione come parametro e/o restituisce una funzione.

```kt
fun calculate(x: Int, y: Int, operation: (Int, Int) -> Int): Int {
	return operation(x, y)
}

fun sum(x: Int, y: Int) = x + y

fun main() {
	val sumResult = calculate(4, 5, ::sum) // short syntax
	val mulResult = calculate(4, 5) { a, b -> a * b } // lambda syntax
	println("sumResult $sumResult, mulResult $mulResult")
}
```

##### Lambdas
>[!tldr] Definizione
>Le ***lambda*** sono *funzioni anonime*, concise e spesso monoriga, usate per definire rapidamente logiche temporanee senza una dichiarazione formale.

```kt title:Sintassi
val upperCase: (String) -> String = { str: String -> str.uppercase() }
val upperCase2: (String) -> String = String::uppercase
val upperCase3: (String) -> String = { it.uppercase() }
```

#### Scope Functions
>[!info]
>Le ***scope functions*** sono funzioni in grado di eseguire un blocco di codice nel contesto di un oggetto.

##### Let
>La funzione let può essere usata per ***scoping e null-checks***.

```kt
fun printNonNull(str: String?) {
	str?.let {
		println(it)
	}
}
```

L'oggetto è accessibile all'interno del blocco tramite `it` o un nome personalizzato passato alla lambda.

##### Run
> Analogo a `let` ma si accede all'oggetto tramite `this` (anche *implicito*).

##### With
> Può accedere ai membri del suo parametro in modo conciso, omettendo il nome dell'istanza.

```kt
class Configuration(var host:String, var port:Int) 

fun main() {
	val configuration = Configuration(host ="127.0.0.1", port =9000) 
	with(configuration) { println("$host:$port") }
	// instead of:
	println("${configuration.host}:${configuration.port}")    
}
```

##### Apply
> Esegue un blocco di codice su un oggetto e restituisce l'oggetto.

```kt
data class Person(var name: String, var age: Int = 0, var about: String = "")

fun main() {
	val jake = Person("Jake")
	val stringDescription = jake.apply {
		age = 30
		about = "Android developer"
	}.toString()
	println(stringDescription)
}
```

##### Also
> Funziona come `apply` ma all'interno l'oggetto è referenziato con `it`.