>[!hint] Equality Check
>***Kotlin*** utilizza $==$ per il confronto strutturale e $===$ per il confronto referenziale.

```kt
val authors = setOf("Shakespeare", "Hemingway", "Twain")
val writers = setOf("Twain", "Shakespeare", "Hemingway")

println(authors == writers)   // true
println(authors === writers)  // false
```
## When
---
> Al posto dello switch, [[Linguaggio Kotlin|Kotlin]] ha una versione più flessibile.

>[!info] Pattern Matching
>La struttura `{kt icon} when` può essere utilizzato sia come statement che come espressione.

```kt
// Statement
fun whenStatement(obj: Any){
	when (obj) {
		1 -> println("one")
		"Hello" -> println("Greeting")
		is Long -> println("Long")
		!is String -> println("Not a string")
		else -> println("Unknown")
	}
}

// Expression
fun whereAssignment(obj: Any) {
	val result = when (obj) {
		1 -> "one"
		"Hello" -> 1
		is Long -> false
		else -> 42	
	}
}
```

## Cicli
---
>[!failure] Possibilità
>`{kt icon} Kotlin` mette a disposizione 3 costrutti: `for`, `while` e `do-while`

```kt
val cakes = listOf("carrot", "cheese", "chocolate")
for (cake in cakes) {
	println("Yummy, it's a $cake cake!")
}

fun eatACake() = println("Eat a Cake")
fun bakeACake() = println("Bake a Cake")

fun main(args: Array<String>) {
	var cakesEaten = 0
	var cakesBaked = 0
	while (cakesEaten < 5) { 
		eatACake()
		cakesEaten ++
	}
	
	do { 
		bakeACake()
		cakesBaked++
	} while (cakesBaked < cakesEaten)
}
```

### Iteratori
> È possibile definire iteratori nelle classi implementando l'operatore `iterator`

```kt
class Animal(val name: String)

class Zoo(val animals: List<Animal>) {
	operator fun iterator(): Iterator<Animal>{
		return animals.iterator()
	}
}

fun main() {
	val zoo = Zoo(listOf(Animal("Zebra"), Animal("Lion")))
	
	for (animal in zoo){
		println("$animal")
	}
}
```

### Range
> `{kt icon} Kotlin` mette a disposizione diverse strutture per definire dei range:

```kt
for(i in 0..3) {   // Equals to for(i=0; i<=3; i++) 
	print(i)
}
print(" ")

for(i in 0 until 3) {   // for(i=0; i<3; i++)
	print(i)
}
print(" ")

for(i in 2..8 step 2) { // for(i=2; i<=8; i=i+2)
	print(i)
}
print(" ")

for (i in 3 downTo 0) { // for(i=3; i>=0; i--)
	print(i)
}
print(" ")
```

>[!tldr] È possibile usare i range anche per i `char`

>[!question] È possibile usare i range per controllare se un valore è in un certo intervallo.

