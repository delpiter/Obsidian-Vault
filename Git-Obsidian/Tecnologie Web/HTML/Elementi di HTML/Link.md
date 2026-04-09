>[!info] `{html icon} <a>`
>Elemento che consente di inserire ***ancore*** nel documento.
>- Le ancore sono punti di partenza di un *link*.

La destinazione si specifica con un [[../../Architettura del Web#URI|URI]] attraverso l'attributo `href`.
- È possibile collegare un altro pezzo del documento, tramite l'uso dell'`ID`.

```html
<nav>
	<ul>
		<li> <a href="/">Home</a> </li>
		<li> <a href="/news">News</a> </li>
		<li> <a href="http://www.google.it">Google</a> </li>
		<li> <a href="#articolo">Articolo</a> </li>
	</ul>
</nav>
<articleid="articolo">
	 <p> testo dell'articolo .... </p>
 </article>
```