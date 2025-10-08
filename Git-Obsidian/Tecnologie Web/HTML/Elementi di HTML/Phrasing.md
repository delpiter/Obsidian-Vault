![[Elementi e Categorie#^874310]]

## P
---
>[!info] `{html icon} <p>`
>Elemento che inserisce un ***paragrafo testuale***.

Va usato solo quando non esiste un elemento più specifico o semanticamente più idoneo per descrivere quel testo.

```html title:example
<section>
	<p> First paragraph </p>
	<p> Second paragraph </p>
	<p> Third paragraph </p>
 </section>
```

## Br
---
>[!info] `{html icon} <br/>`
>Elemento che rappresenta una ***interruzione di linea***.
>- È un elemento vuoto, va scritto con `/`.

Deve essere usato solo per interruzioni che sono parte del contenuto, **non** per ottenere *effetti grafici*.

```html title:example
<p>Nel mezzo del cammin di nostra vita<br/>
 mi ritrovai per una selva oscura<br/>
 ché la diritta via era smarrita.</p>
```

## Div
---
>[!info] `{html icon} <div>`
>L'elemento `{html icon} <div>` ***non ha alcun significato proprio***, ma ha lo scopo di rappresentare gli elementi in esso annidati e specificare per loro gli *attributi* `class`, `lang` e `title`.

Viene usato principalmente per definire l'attributo `class`
- Per dare a un gruppo di elementi consecutivi uno stesso ***stile di presentazione***.
- La caratteristica presentazionale non ***deve avere una connotazione semantica***.

## Span
---
>[!info] `{html icon} <span>`
>Elemento che opera in modo simile al `{hrml icon} <div>` ma a **livello di testo** (elemento [[Elementi e Categorie#Elementi di Blocco e Inline|inline]]).

## Main
---
>[!info] `{html icon} <main>`
>Elemento che ***raggruppa gli elementi di struttura*** che rappresentano il contenuto principale del documento.

Nel contenuto vanno **esclusi** i contenuti che sono ripetuti in diverse pagine, come le *barre di navigazione*.

## Ruolo del Testo
---
> Di seguito alcuni elementi che attribuiscono ***ruoli*** al testo

`{html icon} <i>`, `{html icon} <b>` e `{html icon} <small>`
- Rispettivamente testo in **voce alternativa** (*italics*), **offset text** (**bold**) e *note a margine*.
	- Elementi deprecati poiché davano solo ***resa presentazionale***.


`{html icon} <em>`
- ***Stress Emphasis***, un testo o una frase che si pronuncia in modo differente dal resto.

`{html icon} <strong>`
- ***Strong importance***, testo importante.

`{html icon} <abbr>`
- ***Abbreviazioni o acronimi***, l'attributo `title` è usato per inserire la versione espansa del termine
- `{html icon} <abbr title="Hypertext Markup Language">HTML<abbr>`

`{html icon} <var>`
- ***Variabili o costanti*** usate in documenti a *carattere scientifico*.

`{html icon} <dfn>`
- ***Definizione di un termine***, deve contenere un attributo `title` che assume il valore della definizione o un elemento `{html icon} <abbr>` con un attributo `title`.

`{html icon} <code>`
- ***Porzioni di Codice***.

`{html icon} <sub>` e `{html icon} <sup>`
- Corrispondono ad ***apice*** e ***pedice***.

#### Citazioni
> Ci sono vari elementi per inserire ***citazioni***.

`{html icon} <blockquote>`
- Per parti di contenuto che vengono citate da una *sorgente esterna* specificabile con l'attributo opzionale `cite`.

`{html icon} <q>`
- Simile a ***blockquote*** ma agisce su un *breve testo*.

`{html icon} <cite>`
- Per citare i riferimenti ad un lavoro creativo. Deve includere il *titolo del lavoro* o il nome dell'*autore* o l'*URL* di riferimento.

## Mappe
---
>[!info] `{html icon} <map>`
>Una mappa è una [[Embedded#Figure|immagine]] in cui alcune aree sono ***interattive***, attivano un link o altre azioni.
>Può essere realizzata:
>- ***Client-Side***.
>- ***Server-Side***.

```html title:example
<img src="workplace.jpg" alt="Workplace" usemap="#workmap">
<map name="workmap">
<area shape="rect" coords="34,44,270,350" alt="Computer" href="computer.htm">	<area shape="rect" coords="290,172,333,250" alt="Phone" href="phone.htm">
<area shape="circle" coords="337,300,44" alt="Coffee" href="coffee.htm">
</map>
```