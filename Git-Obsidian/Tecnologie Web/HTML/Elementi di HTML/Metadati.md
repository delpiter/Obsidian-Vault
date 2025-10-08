![[Elementi e Categorie#^0fa285]]

I metadati sono inclusi nell'head del documento.

## Title
---
>[!info] `{html icon} <title>`
>L'elemento `{html icon} <title>` rappresenta il ***titolo*** o il nome del documento.
>- Deve essere scritto tenendo conto che potrebbe essere usato fuori contesto.

```html title:title
<head>
	<title>Materialedell’insegnamento di 
		Tecnologie Web –CdS ISI Cesena
	</title>
 </head>
```

## Base
---
>[!info] `{html icon} <base>`
>L'elemento `{html icon} <base>` deve essere l'***unico*** all'interno del documento.

Lo scopo principale dell'elemento `{html icon} <base>` è quello di indicare il ***path base*** del documento che servirà per risolvere gli [[URL]] relativi, sia in termini di `href`  che di `target`.

```html title:base
<head>
	<base href="http://www.w3schools.com/images/" target="_blank"/>
</head>
```

## Link
---
>[!info] `{html icon} <link>`
>L'elemento `{html icon} <link>` viene usato per ***creare relazioni*** tra il documento e altri documenti o risorse.

L'utilizzo principale è creare la relazione con il `{css icon} css` e il `{js icon} javascript`.

```html title:link
<head>
	<link rel="stylesheet" type="text/css" href="theme.css"/>
 </head>
```

## Style
---
>[!info] `{html icon} <style>`
>L'elemento `{html icon} <style>` permette di ***includere stili*** all'interno del documento.

Il rendering del documento sarà il risultato dei `{html icon} <link>` a fogli di stile, degli elementi `{html icon} <style>`.

```html title:style
<style>
	 h1 {color:red;}
	 p {color:blue;}
 </style>
```

## Meta
---
>[!info] `{html icon} <meta>`
>I `{html icon} <meta>` vengono usati per aggiungere altri **metadati** al documento.

Sono spesso usati dai motori di ricerca.
Il tipo di metadati è specificato dall'attributo `name`.

```html title:meta
<head>
	<meta charset="UTF-8"/>
	<meta name="description" content="Free Web tutorials"/>
	<meta name="keywords" content="HTML,CSS,XML,JavaScript"/>
	<meta name="author" content="HegeRefsnes"/>
 </head> 
```
