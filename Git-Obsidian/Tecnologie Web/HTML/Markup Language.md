>[!definizione]
>Un ***linguaggio di markup*** è un linguaggio con una specifica *sintassi*, che consente di **annotare** un documento, fornendone una interpretazione delle sue parti.

Il termine deriva dal contesto della *tipografia*, dove si usava marcare le parti del testo che andavano **evidenziate** o **corrette**.

> ***Tipi di Markup***

>[!abstract] Procedurale
>I linguaggi di markup di tipo ***procedurale*** indicano le *procedure di trattamento del testo*.

Specifica le istruzioni che devono essere eseguite per visualizzare il testo referenziato.

>[!cite] Descrittivo
>I linguaggi ***descrittivi*** identificano strutturalmente il tipo di ogni elemento del contenuto.

Individuano il ruolo all'interno del documento, specificando che un elemento è un titolo, un paragrafo o una citazione, etc...
- Es: `{html icon} HTML`, `{xml icon} XML`,  `SGML`.

## Metamarkup e XML
---
>[!info]
>Il ***metamarkup*** consiste nel fornire regole di interpretazione del markup.
>- Permette di definire *nuovi linguaggi di markup*.

Fornisce una *sintassi* per definire le regole da applicare nella marcatura.
- Ne descrive la ***grammatica***.

>[!help] ***XML***
>***Extensible Markup Language*** è un linguaggio di markup, progettato per lo *scambio e la interusabilità di documenti strutturati su internet*.

`{xml icon} XML` è ideale come linguaggio per ***definire documenti strutturati***, e per esprimerli in maniera indipendente dalla destinazione finale.
- Uno stesso documento può essere trasformato per l'**editing**, la **stampa**, il **web**, ...

>[!check] DTD
> Usando `{xml icon} XML` è possibile creare un modello chiamato ***Document Type Definition***, che descrive la struttura e il contenuto di una classe di documenti.

Lo stesso `{xml icon} XML` ha un proprio `DTD` in cui vengono elencate le regole della specifica del linguaggio.

```xml title:DTD
 <!—Dichiarazione della DTD -- >
 <!ELEMENT tesi (titolotesi, autore, relatore, correlatore?, capitolo+)>
 <!ATTLIST tesi sessione (‘I’|’II’|’III’) #REQUIRED>
 <!ELEMENT autore (#PCDATA)>
 <!ELEMENT relatore (#PCDATA)>
 <!ELEMENT correlatore (#PCDATA)>
 <!ELEMENT capitolo (numero, titolo, paragrafo+)>
 <!ELEMENT paragrafo (#PCDATA|sottoparagrafo+)>
 <!ELEMENT sottoparagrafo(numero, titolo, paragrafo+)>
```

Nella definizione dei possibili ***attributi***:
- `?` indica che l'attributo può essere presente $0$ o $1$ volta.
- `+` indica che l'attributo può essere presente $1$ o *più* volte.
- `*` indica che l'attributo può essere presente $0$ o *più* volte.
### Well-Formed vs Valid
> In `{xml icon} XML` si possono generare documenti ***well-formed*** e ***validi***.

>[!todo] Well-Formed
>Sono ***documenti conformi alle generiche specifiche*** `{xml icon} XML`.
>- Occorre solo definire un file `{xml icon} XML` che le rispetti.

>[!done] Validi
>Sono documenti conformi ad una specifica `DTD`.
>Occorre definire un file `{xml icon} XML` e la sua `DTD`.

La `DTD` può essere sia *interna* che *esterna*.
- Un documento valido deve essere ***sempre e comunque ben formato***.

```xml title:Esempio
< !--Intestazione -- >
< ?xml version="1.0" ?>
< !--DTD -- >
< !DOCTYPE tesi SYSTEM ”tesi.dtd">

<tesi sessione="II">
	<titolotesi> Linguaggi di Markup </titolotesi>
	<autore> Mario Rossi </autore>
	<capitolo>
		<numero>1</numero>
		<titolo> introduzione </titolo>
		<paragrafo> 
			...
		</paragrafo>
	</capitolo>
</tesi>
```

## Storia di HTML
---
>[!info]
>Il ***web*** nasce dai ricercatori del `CERN` che ne definiscono il funzionamento.

I ricercatori mandano all'[[Enti Importanti#Internet Engineering Task Force|IETF]] le specifiche del protocollo di [[Protocolli Applicativi|livello applicazione]] ([[HTTP]]).

***Mosaic*** è il primo prototipo di browser presentato dalla `NCSA`.
- Primo browser a ottenere successo su larga scala.
- Poi rinominato ***Netscape***.

#### Guerre dei Browser

>[!help] Prima "Guerra"
>Combattuta tra ***Netscape*** e ***Internet Explorer*** (*Microsoft*).
>- Le due aziende introducono piccole modifiche su `{html icon} HTML` per migliorare l'esperienza dell'utente e *diffondere il proprio browser*.

Prevale ***IE***, poiché *Microsoft* decide di distribuire il proprio browser con il sistema operativo.
- Netscape rilascia il codice sorgente in ***open source***, nasce ***Mozzilla Firefox***.

>[!missing] Seconda "Guerra"
>Avvenuta con l'introduzione di ***Google Chrome***.

*Google Chrome* prevarrà sugli altri browser.

### W3C e HTML
>[!info]
>Nel 2004, *Firefox* e *Opera* proposero al `W3C` la riapertura del Working Group su `{html icon} HTML` per lo sviluppo di nuove versioni del linguaggio.

L'idea venne **bocciata** dal `W3C`.

Venne formato un gruppo chiuso e finanziato dalle società di software.
- Il *Web Hypertext Application Technology Working Group* (***WHAT WG***).
- Svilupparono proposte che vennero implementate dai vari browser, che riguardavano `{html icon} HTML`, `{css icon} CSS`, `{js icon} Javascript`, `DOM`

Nel 2007 il `W3C` riapre il ***Working Group***, per creare una versione di `HTML`, `{html icon} HTML5`

## Accessibilità
---
>[!definizione]
>L'***accessibilità*** è la capacità dei *sistemi informatici*, nelle forme e nei limiti consentiti dalle conoscenze tecnologiche, di *erogare servizi* e fornire informazioni fruibili, ***senza discriminazioni***, anche da parte di coloro che a causa di **disabilità** necessitano di tecnologie assistive o configurazioni particolari.
