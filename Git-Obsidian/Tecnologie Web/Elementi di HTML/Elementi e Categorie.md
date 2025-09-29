> Ogni elemento `{html icon} HTML5` fa parte di una o più **categorie**, definiti per gruppi con caratteristiche simili.

## Categorie
---
![[HTMLCategory.png]]

>[!info] Flow Content
>La maggior parte degli elementi usati nel *body* del documento e delle applicazione è categorizzato come ***flow content***.

>[!tl;dr] Metadati
>I ***metadati*** sono contenuto che identifica la **presentazione** o il **comportamento** del resto del contenuto, o le relazioni del documento con altri documenti, che fornisce informazioni "*fuori banda*".

^0fa285

>[!caution] Interactive
>***Interactive*** è il contenuto che è specificamente inteso per l'interazione con gli utenti.
>- `{html icon} <form><\form>`, `{html icon} <multimedia><\multimedia>`, etc...

>[!bug] Embedded
>La categoria ***embedded*** è contenuto che *importa un'altra risorsa nel documento*, o contenuto espressi in altri vocabolari e inseriti nel documento.

^d97192

>[!quote] Phrasing
>Il ***phrasing*** è il *testo del documento* e anche gli elementi che *marcano il testo* al livello interno al paragrafo.

^874310

>[!example] Heading
>L'***heading*** definisce le intestazioni di sezione.
>Introducono i titoli delle diverse sezioni del documento.

^fa533c

>[!summary] Sectioning
>Gli elementi ***sectioning*** hanno ***funzione strutturale*** dividono il documento in parti con semantica diversa.
>- `{html icon} <nav></nav>` `{html icon} <section></section>` `{html icon}<footer></footer>`.

^6f6250

## Elementi HTML
---
>[!definizione]
>Un elemento `{html icon} HTML` è definito da un *tag di apertura*, un *contenuto* e un *tag di chiusura*.
>- `{html icon} <tagName>Content</tagName>`

I tag sono il *markup* che aggiungiamo al contenute per dare struttura e per definire il ruolo che tale contenuto ricopre all'interno del documento.

I ***tag*** possono essere corredati di uno o più *attributi*.
- Servono per meglio specificare la funzione dell'elemento, memorizzare dati o arricchire di significato il contenuto

Gli ***attributi*** sono coppie *nome-valore* separate dal carattere `=`.
- I valori sono racchiusi tra virgolette `""`.

```html
<a href=“http://www.unibo.it”>Università di Bologna</a>
```

### Elementi di Blocco e Inline
> Tutti i tag si possono distinguere in due categorie.

>[!tip] Elementi di Blocco
>Il comportamento di default degli ***elementi di blocco*** nella finestra del browser è quello di essere preceduti e seguiti da una andata a capo.

Sono nativamente rappresentati come un box.
- Es. tabelle, liste, heading, form, ...

>[!summary] Elementi Inline
>Gli ***elementi Inline*** sono contenuti in un elemento di blocco e *non intaccano il flusso*.

- Es. link ipertestuali, elementi per enfatizzare il testo, ...
