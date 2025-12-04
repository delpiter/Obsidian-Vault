![[Elementi e Categorie#^6f6250]]

![[Sectioning.png]]

## Section
---
>[!info] `{html icon} <section>`
>Tag che definisce una *sezione del documento*.
>- "*A section is a thematic grouping of content, typically with a heading*".

```html title:example
<section>
	<h1>WWF</h1>
	<p>The World Wide Fund for Nature (WWF) is an international organization working on issues regarding the conservation, research and restoration of the environment.</p>
</section>
```

## Article
---
>[!info] `{html icon} <article>`
>Definisce informazioni *indipendenti* e ***auto-contenute***.

```html title:example
<article>
  <h2>Google Chrome</h2>
  <p>Google Chrome is a web browser developed by Google, released in 2008. Chrome is the world's most popular web browser today!</p>
</article>
```

## Header
---
>[!info] `{html icon} <header>`
>Definisce l'***intestazione*** di un documento o di una sua sezione.

Può essere usato come contenitore di un contenuto di tipo introduttivo.

```html title:example
<article>
  <header>
    <h1>What Does WWF Do?</h1>
    <p>WWF's mission:</p>
  </header>
  <p>WWF's mission is to stop the degradation of our planet's natural environment, and build a future in which humans live in harmony with nature.</p>
</article>
```

## Footer
---
>[!info] `{html icon} <footer>`
>Definisce il ***footer*** di un documento o di una sua sezione.

Solitamente un footer contiene le *informazioni* sull'autore del documenti, di *copyright*, link ai *termini d'uso*, info sui *contatti*.

```html title:example
<footer>
  <p>Author: Hege Refsnes</p>
  <p><a href="mailto:hege@example.com">hege@example.com</a></p>
</footer>
```

## Nav
---
>[!info] `{html icon} <nav>`
>Elemento che definisce un ***insieme di link di navigazione***, menù o toolbar di altri set.

```html title:example
<!DOCTYPE html>
<html>
	<body>
		<nav>
			<a href="/html/">HTML</a> |
			<a href="/css/">CSS</a> |
			<a href="/js/">JavaScript</a> |
			<a href="/jquery/">jQuery</a>
		</nav>
	</body>
</html>
```

## Aside
---
>[!info] `{html icon} <aside>`
>Definisce un ***contenuto laterale*** rispetto a quelli principali, ma comunque correlati.

Può essere usato per contenere ***contenuti di una barra laterale***, ma anche per contenuti che sono collaterali, ma non si posizionano necessariamente a lato.
- Es. Citazioni o *banner pubblicitari*.

```html title:example
<body>
	<p>My family and I visited The Epcot center this summer. The weather was nice, and Epcot was amazing! I had a great summer together with my family!</p>
	
	<aside>
		<h4>Epcot Center</h4>
		<p>Epcot is a theme park at Walt Disney World Resort featuring exciting attractions, international pavilions, award-winning fireworks and seasonal special events.</p>
	</aside>
	
</body>
```

