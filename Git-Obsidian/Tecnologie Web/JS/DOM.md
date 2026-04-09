## Document Object Model
---
>[!info]
>Il `DOM` è la ***rappresentazione dei documenti strutturati*** come modello orientato agli oggetti.

Ogni documento caricato dal browser genera un `DOM` che specifica, sotto forma di gerarchia di oggetti tutti gli elementi del documenti.

Il `DOM` definisce un'`API` per documenti [[../HTML/Markup Language|HTML e XML]].
- Utilizzando il `DOM` i programmatori possono costruire, navigare, aggiungere, modificare o cancellare elementi.
- Ogni componente di un documento può essere letto, modificato, cancellato o aggiunto usando il `DOM`.

> Il `DOM HTML` è un modello a oggetti per `{html icon} HTML`.
- Definisce gli **elementi come oggetti**.
- **Proprietà**, **metodi** e **eventi** per tutti gli elementi.

> Per [[JavaScript]] Il `DOM HTML` è una `API`.
- Permette la aggiunta, rimozione e modifica di:
	- Elementi e Attributi `{html icon} HTML`.
	- Stili [[../CSS/Cascading Style Sheets|CSS]].
	- Eventi `{html icon} HTML`
- Può reagire a eventi `{html icon} HTML`

### DOMDocument
>[!check] Info
>Il `{js icon} DOMDocument` specifica i metodi per ***accedere al documento*** principale.

```js title:Example
// elements
docType;
documentElement;

//method
document.createElement();
document.createAttribute();
document.createTextNode();
document.getElementsByTagName();
document.getElementById();
```
### DOMNode
>[!help] Info
>Il `{js icon} DOMNode` specifica i metodi per ***accedere agli elementi di un nodo*** di un documento.

```js title:Example
// elements
nodeName;
nodeValue;
nodeType;
parentNode;
childNodes;
attributes;

//method
node.insertBefore();
node.replaceChild();
node.removeChild();
node.appendChild();
node.hasChildNodes();
node.hasAttributes();
```

### DOMElement
>[!summary] Info
>Un `{js icon} DOMElement` specifica i metodi e i membri per accedere a qualunque elemento del documento.

Un elemento è ***specifico*** [[../HTML/Elementi di HTML/Elementi e Categorie|elemento]] `{html icon} HTML` del documento.

```js title:Example
// elements
tagName

//method
element.getAttribute();
element.setAttribute();
element.removeAttribute();
element.getElementsByTagName();
element.getElementById();
```