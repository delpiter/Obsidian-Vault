> La sintassi di [[JavaScript]] è modellata su quella del [[Linguaggio C|C]] con alcune varianti significative.

>[!summary] In Breve

- Linguaggio ***case-sensitive***.
- Le istruzioni sono terminate da `;` o dall'andata a capo.
- Sono ammessi commenti multi linea (`{js icon} /* Comment */`)e mono linea (`{js icon} // Comment`).
- Gli identificatori possono contenere lettere, cifre e i caratteri `_` e `$`, non possono iniziare con una cifra.

> Funzioni

```js
function foo(par1, par2){
	// code
	return value;
}
```

> Operatori relazionali
- Gli operatori relazionali sono i soliti più ***due nuovi***.
- Se i tipi dei due operandi sono diversi, `==` e `!=` applicano la "***type coercion***" secondo *regole molto discutibili*.

>[!danger] Attenzione
>Nella valutazione di condizioni si considera falso non solo `false` ma ogni valore "***falsy***": `null`, `undefined`, `""`, `0` e `NaN`.

```js
(a === b) // no type coercion
(a !== b)
```

> Variabili

Dichiarate usando la parola chiave `var`
- `{js icon} var varName;`
- ***Non hanno un tipo***.

>[!help] Scope
>Esiste lo scope *globale* e *locale*, **non** esiste lo scope di blocco.

***Hoisting***:
- Sistema con cui javascript muove le *dichiarazioni delle variabili in testa al codice*.
	- Una variabile può essere **usata e poi dichiarata**.

> Altre dichiarazioni
- `{js icon} let varname;` Definisce variabili con **scope di blocco**.
- `{js icon} const varname;` Definisce variabili che non ***possono essere riassegnate***.

>[!fail] Strict Mode
>Direttiva che impone regole stringenti in ***fase di dichiarazione di una variabile***.
>- Non è possibile assegnare un valore ad una variabile non dichiarata.

```js
'use strict';

if(a>0){ // error
	console.log("foo");
}
var a = 2;
```

#### Tipi
> Supporto a pochi tipi primitivi

***Numeri***
- Rappresentati in formato floating point a $8$ `byte`.
- Esiste il valore `NaN` per le operazioni ***non ammesse***.
- Esiste il valore `infinite`.

***Boolean***:
- Ammettono i valori `true` e `false`.

##### Array
>[!info]
>Un ***array*** in `{js icon} js` è un'entità in mezzo tra un array classico e una lista.

Gli elementi si numerano da $0$, `length` da la lunghezza dell'array e si usa la notazione parentesi quadre.

A differenza di array normali, `length` da la lunghezza ***dinamica dell'array*** (l'attuale)

```js title:definition
/* Creation */
colors = new Array("red", "green", "blue");
misc = ["hello", 12, Math.sin];

/* Modification */
colors[3] = "yellow";
```
##### String
> Il tipo `string` denota stringhe di caratteri unicode.
- Non esiste il `char`.

È un ***oggetto immutabile*** dotato di:
- proprietà: `length`, ...
- metodi : `{js icon} substring(first, last)`

##### Classi e Oggetti
>[!warning] Non esiste il concetto esplicito di classe

Si usa `function` per definire un costruttore.
```js
function foo(){
	this.a = 0;
	this.bar = () =>{
		console.log("Hello");
	}
}

let b = new foo();
```

I membri di un oggetto possono essere acceduto equivalentemente con:
- `{js icon} object.field`
- `{js icon} obj["field"]`

Possono essere considerati come ***liste non ordinate di proprietà***.

```js
michel = {
	name: 'michel',
	height: 180,
	jump: function(){
		return "hop";
	}
}
```

Nelle ultime versioni è stata introdotta la keyword `class` per la definizione di classi.

```js
class Person{
	constructor(name, height) 
	{
		this.name = nome;
		this.height = altezza;
	}
	
	jump(){
		return 'hop!';
	}
 }
```

>[!danger] È solo a livello di sintassi, non è stato aggiunto il concetto di classe.

###### Oggetti Principali
>[!help] `{js icon} window`
>È l'oggetto top level con le proprietà e i metodi della finestra principale.

```js
/* Positioning */
window.moveBy(x,y);
window.moveTo(x,y);

/* Sizing */
window.resizeBy(x,y);
window.resizeTo(x,y);

/* Other window */
window.open("Url", "windowname",["opt"]);

/* Time and intervals */
window.setTimeout(function (), millis, ["opt"]);
```

>[!caution] `{js icon} navigator`
>È l'oggetto con le proprietà del client come nome, versione, etc...


>[!hint] `{js icon} location`
>Contiene l'[[URL]] del documento corrente.

```js
window.location = "google.com"; // redirect
```

>[!missing] `{js icon} history`
>Contiene l'array degli `URL` acceduti durante la navigazione.

```js
history.back(); // redirect to last page
history.forward(); // next page
```

>[!note] `{js icon} document`
>Rappresenta il [[DOM]], ha proprietà e metodi per accedere ad ogni elemento nella gerarchia.

***Javascript*** implementa i metodi standard per accedere al `DOM` del documento, ma il supporto dei browser non è uniforme.

```js
var c = document.getElementById("c");
c.setAttribute('class', 'test');

var p = document.createElement('p');
var text = document.createTextNode('Hello, World');

p.appendChild(text);
c.appendChild(p);
```

### Exception
> `{js icon} JavaScript` fornisce meccanismi per sollevare e catturare eccezioni.

```js
try {
	throw "Error Thrown"
} catch (error) {
	console.log(error); // Error Thrown
}
```