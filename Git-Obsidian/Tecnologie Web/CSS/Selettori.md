## Selettore
---
>[!info]
>Un ***selettore*** consente di specificare un elemento o un insieme di elementi dell'albero `{html icon} HTML` al fine di associarvi delle caratteristiche.

Selettori diversi possono usare lo stesso blocco se ***separati da virgola***.
```css
a, p, div { font-family: Arial; }
```
### Tipologie

>[!help] Selettore Universale
>Fa un match con ***qualsiasi elemento***.

```css
*{ font-family: Arial; }
```

>[!check] Selettore di Tipo
>Il ***selettore di tipo*** fa match con un elemento specificato `E`.

```css
body{ font-family: Arial; font-size: 12 pt; }
header{ font-size: 18 pt; }
section{ font-size: 10 pt; }
```

>[!summary] Selettori di Prossimità
>I ***selettori di prossimità*** fanno match con elementi `F` in base alla relazione con un elemento `E`.

> `E F`
- Elemento `F` **discendente** di `F`.

> `E>F`
- Elemento `F` ***figlio diretto*** di `E`.

> `E+F`
- Elemento `F` ***immediatamente seguente*** a `E` che condivide lo stesso *parde*.

> `E~F`
- Elementi `F` "***fratelli immediati***" di `E` (allo stesso livello `{xml icon} HTML`).

```css
section p { font-size: 10 pt; }
p>strong { color: red; }
header+h1 { font-size: 11 pt; }
```

>[!tl;dr] Selettori di Attributi
>Fanno match con gli elementi `E` che ***possiedono l'attributo specificato*** o che ha un *valore particolare*.

`E[attr]`, `E[attr="value"]`, `E[attr~="value"]`, `E[attr^="bar"]`.

```css
a[name] { color: red; }
```

- Funzionano anche nel caso in cui l'***attributo dichiarato non sia valido***.

```html
<style>
	div[attributo-inesistente] { background-color: yellow;}
</style>
<div attributo-inesistente>
	<p>Questo con attributo non valido.</p>
</div>
```

>[!tip] Selettori di Classe
>Seleziona gli elementi che possiedono una ***classe o un id specifico***.
>- È equivalente a scrivere `E[class="value"]`, `E[id="value"]`.

```css
h1.spiegazione { font-size: 24 px; }
.spiegazione { font-size: 12 px; }
p#note1 { font-size: 9 px; }
#note5 { color: red; }
```

>[!bug] Selettori di Pseudoclassi
>Definisce uno stile per uno ***stato speciale di un elemento***.
>- `{css icon} E:hover`

> `link`, `visited`
- Vero se l'elemento `E` è un `{html icon} <a>` (*link*) non ancora visitato o un link già visitato.

> `hover`, `active`, `focus`
- Vero se sull'elemento `E` passa sopra il mouse, il mouse è premuto o il [[../HTML/Elementi di HTML/Interactive|controllo]] è selezionato per accettare *input*.

> `enabled`, `checked`
- Vero se elemento `E` è *abilitato* o *checked*

> `lang(c)`
- Vero se l'elemento ha ***selezionata la lingua*** `c`.

>[!missing] Selettori di Pseudo-Classi strutturali

> `first-child`
- Elemento `E` che è il ***primo figlio*** di suo padre.

> `nth-child(n)`
- Elemento E che è l’$n$-***esimo figlio*** di suo padre.

> `nth-last-child(n)`
- elemento `E` che è l’$n$-***esimo figlio*** di suo padre a partire dall'*ultimo*.

> `first-of-type`
- Elemento `E` che è il ***primo figlio*** di suo padre di *quel tipo*.

> `nth-of-type(n)`
- Elemento `E` che è l’$n$-***esimo figlio*** di suo padre di *quel tipo*.

> `only-of-type`
- Elemento `E` che è l’***unico figlio*** di suo padre di *quel tipo*.

> `empty`
- Elemento `E` che è ***vuoto***.

>[!todo] Selettori di Pseudo-Elementi
>Uno ***pseudo-elemento*** è una *keyword* che può essere aggiunta ad un selettore, per aggiungere stile ad una parte specifica di un elemento.

> `before`, `after`
- Vero prima e dopo il contenuto dell'elemento `E`.

> `first-line`
- Vero per la prima riga dell'elemento `E`.

> `first-letter`
- Vero per la prima lettera di un elemento.

```css
p:first-letter { 
	font-size: 300%; 
	float: left;
}
```