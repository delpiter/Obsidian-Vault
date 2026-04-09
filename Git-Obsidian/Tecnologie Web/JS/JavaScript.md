## JavaScript
---
>[!bug] Linguaggio
> `{js icon} JavaScript` è un linguaggio di scripting interpretato dal browser *orientato* agli ***oggetti*** e agli ***eventi***, utilizzato nella programmazione `web` lato client.

È un linguaggio basato su una logica ***weakly typed*** e ***prototype-based***.
- È una delle core Technologies nella produzione di contenuti web (Insieme a [[../HTML/Markup Language|HTML]] e [[../CSS/Cascading Style Sheets|CSS]]).

>[!fail] Differenze da Java
>- È **interpretato** e non compilato.
>- È ***Object-based*** ma non ***class-based***.
>- È debolmente tipizzato.

### Prototype
>[!info]
>Per poter aggiungere proprietà e/o metodi a molti oggetti, si deve usare l'***oggetto prototype***.

Si usa per creare o riusare librerie di oggetti e metodi.

```js
function Person(name, surname){
	this.firstName = name;
	this.lastName = surname;
}

var foo = new Person("Name", "Surname");
Person.prototype.welcome = function(){
	alert("Welcome, " + this.firstName + "!");
}
// adds a function to the Person prototype

foo.welcome(); // Logs: "Welcome, Name!"
```

### Stack Javascript
>[!summary] MEAN
>`{js icon} MEAN` è un [[../Architettura del Web#Web Solution Stack|solution stack]] con struttura tutta basata su `{JS icon} JS`.

> `M`
- ***MongoDB*** come database (NoSQL).

> `E`
- ***Express.js***, come framework di sviluppo `{js icon} js` lato **server**.

> `A`
- ***Angular***, come framework di sviluppo `{js icon} js` lato **client**.

> `N`
- ***Node.js***, ambiente di esecuzione per applicazioni server-side (esegue `{js icon} js` all'esterno del browser).

`MEAN` si definisce come ***piattaforma javascript fullstack*** per applicazioni web moderne.

>[!caution] Differenze `MEAN` e `XAMP`

- `XAMP` fanno riferimento a uno specifico ***sistema operativo***, `MEAN` nasce multi-piattaforma.
- `MEAN` usa *database* **non** relazionali.
- `MEAN` fornisce due supporti di programmazione (*client*: Angular, *server*: Express).

### Usare JS in HTML
> Per inserire codice `{js icon} JavaScript` in un documento `{html icon} HTML` esistono tre modi.

```html title:"Script Element"
<script type="text/javascript">
	// javascript code
</script>
```

```html title:"Import"
<script src="script.js" type="text/javascript"></script>
```

```html title:"In-Line"
<input type="button" onclick="alert('hello')" />
```