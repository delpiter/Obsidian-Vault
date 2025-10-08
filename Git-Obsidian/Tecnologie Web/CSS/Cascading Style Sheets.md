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

#### Valori
>[!info]
>I valori sono ***numeri*** seguiti da una ***unità di misura***.

I numeri possono essere [[Insiemi Numerici#Numeri Interi|interi]] e [[Insiemi Numerici#Numeri Reali|reali]].

##### Unità di misura
> Le unità di misura possono essere relative o assolute

>[!caution] Relative
>`em`
>- Relativa alla ***dimensione del font*** in uso (es. se il font ha corpo `12pt`, `2em` varrà `24pt`).
>
>`px`
>- Relativi al *dispositivo di output* e alle *impostazioni dell'utente*.

>[!abstract] Assolute
>- `in`: *Pollici*.
>- `cm`: *Centimetri*.
>- `mm`: *Millimetri*.
>- `pt`: *Punti Tipografici* ($1/72$ di pollice).
>- `pc`: *Pica* (`12pt`).

>[!info] Percentuali
>***Percentuale del valore*** che assume la proprietà stessa nell'elemento padre.

>[!help] [[URL]]
>Assoluti o relativi (*path*).

>[!todo] Stringhe

>[!hint] Colore
>- [[Rappresentazione di Immagini#Codifica RGB|RGB]] (`#RRGGBB`)
>- [[Luce e Colori#Spazio di Colori|HSI]] (`hsi(0, 10%, 40%)`)

### Ordinamento Regole
>[!fail] Conflitti di Stile
>Nell'applicare `{CSS icon} CSS` possono nascere dei conflitti.
>- Ad uno stesso elemento sono applicate delle regole i cui valori sono in conflitto.

```html title:esempio
<style>
	div#provaID{ background-color: red;}
	div.provaClasse{ background-color: blue;}
	div{background-color: green; }
</style>
<div id=‘provaID’ class=‘provaClasse’></div>
```

>[!question] Di che colore sarà il `{html icon} <div>`?

Le dichiarazioni vengono ordinate in base ai seguenti fattori, ordinati dal più *fino* al **meno importante**.

>[!abstract] Media

>[!important] Importanza di una Dichiarazione

È possibile aggiungere ad una dichiarazione la keyword `{css icon} !important`.
- Una regola con questa keyword avrà precedenza sulle altre.

>[!failure] Origine della Dichiarazione
>Un foglio di stile può avere $3$ origini differenti.

In *ordine di importanza*:
1. **Author**: L'autore delle pagine fornisce i fogli di stile del documento.
2. **User**: L'utente può fornire un ulteriore foglio di stile per indicare regole di proprio piacimento (*funzione tipicamente del browser*).
3. **User Agent**: Il browser definisce le *regole di default* per gli elementi dei documenti.

>[!hint] Specificità
>La specificità di un selettore è data da una ***quadrupla*** `xywz` dove:

- `x`: $1$ se la dichiarazione è nell'attributo `style`, $0$ altrimenti.
- `y`: Il numero di `id` specificati nel [[Selettori|selettore]].
- `w`: Numero di classi, attributi e pseudo-classi specificati nel **selettore**.
- `z`: Numero di elementi e di pseudo-elementi specificati nel **selettore**.

A parità di media, importanza e origine, avrà la precedenza la regola con ***specificità più alta***.

```css
li {}                         /* x=0 y=0 w=0 z=1 */
nav ul li:first-line {}       /* x=0 y=0 w=0 z=4 */
nav.menu ul.sec li {}         /* x=0 y=0 w=2 z=3 */
nav ul li a[href=‘/home’] {}  /* x=0 y=0 w=1 z=4 */
nav#menu ul.sec li#st a {}    /* x=0 y=2 w=1 z=4 */
style="li a" {}               /* x=1 y=0 w=0 z=2 */
```