## CSS
---
>[!tldr] Idea
>Il `{css icon} CSS` risponde all'esigenza di una ***tecnologia per la resa grafica***.
>Hanno lo scopo di *separare contenuto* ([[Markup Language|HTML]]) e *presentazione* nelle pagine `web`.
>- Indica come il contenuto **deve essere presentato**.

Lo stesso contenuto può essere presentato in modi diversi:
- [CSS Zen Garden: The Beauty of CSS Design 1](https://www.csszengarden.com/219/)
- [CSS Zen Garden: The Beauty of CSS Design 2](https://www.csszengarden.com/221/)

Lo stesso contenuto può essere presentato ***correttamente*** su dispositivi diversi:
- `PC`, **tablet** e **smartphone**.

### Usare CSS con HTML
> HTML prevede l'uso di stili `{CSS icon} CSS` in quattro modi diversi.

1. Posizionato presso il tag di riferimento (foglio di stile ***inline***, attraverso l'attributo `style`).

```html
<html>
	<head>
		<title>Monstersand Co.</title>
	</head>
	<body>
		<header style="color:blue;">
			<h1>Monsters and Co.</h1>
		</header>
		<section>
			<p>
				Monstersand Co. (Monsters, Inc.) &egrave; un film 
				d'animazione della Pixar, del 2001 diretto
				da Pete Docter, Lee Unkriche David Silverman.
			</p>
		</section>
	</body>
</html>
```

 2. Posizionato nel tag`{html icon} <style>` (foglio di stile *interno*, nell’header del documento).

```html
<html>
	<head>
		<title>Monsters and Co.</title>
	<style type="text/css">
		header { color: blue; }
	</style>
	</head>
	<body>
		<header>
			<h1>Monsters and Co.</h1>
		</header>
		<section>
			<p>
				Monsters and Co. (Monsters, Inc.) &egrave; un film 
				d'animazione della Pixar, del 2001 diretto da 
				Pete Docter, Lee Unkrich e David Silverman.
			</p>
		</section>
	</body>
</html>
```

 3. Importato dal tag `{html icon} <style>` (foglio di stile *esterno* importato, nell’header del documento).

```html
<html>
	<head>
		<title>Monsters and Co.</title>
		<style type="text/css">
			@import url(style.css);
		</style>
	</head>
	<body>
		<header>
			<h1>Monsters and Co.</h1>
		</header>
		<section>
			<p>
				Monsters and Co. (Monsters, Inc.) &egrave; un film 
				d'animazione della Pixar, del 2001 diretto da 
				Pete Docter, Lee Unkrich e David Silverman.
			</p>
		</section>
	</body>
</html>
```

 4. Indicato dal tag `{html icon} <link>` (foglio di stile *esterno*, nell’header del documento)

```html
<html>
	<head>
		<title>Monstersand Co.</title>
		<link type ="text/css" rel ="stylesheet" href="style.css"/>
	</head>
	<body>
		<header>
			<h1>Monsters and Co.</h1>
		</header>
		<section>
			<p>
				Monsters and Co. (Monsters, Inc.) &egrave; un 
				film d'animazione della Pixar, del 2001
				diretto da Pete Docter, Lee Unkriche David Silverman.
			</p>
		</section>
	</body>
</html>
```

### Sintassi
>[!help] Sintassi Principale
>Una regola `{CSS icon} CSS` ha la seguente forma:
>`Selettore { proprietà: valore; }`

> [[Selettori]]
- Consente di specificare un elemento o un insieme di elementi dell'albero `{html icon} HTML` al fine di associarvi delle caratteristiche.

> ***Proprietà***
- *Caratteristica di stile* assegnabile ad un elemento.

> **Valori**
- Dipendono dalla proprietà.
