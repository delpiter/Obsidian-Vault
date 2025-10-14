>[!info] 
>Ogni *elemento* è definito da una **scatola** (`box`) all'interno della quale si trova il contenuto.
>

La visualizzazione di un documento [[Cascading Style Sheets|CSS]] avviene identificando lo spazio di visualizzazione di ciascun ***box*** presente nella pagina.

La `box` ha alcune proprietà:
- `{CSS} box-shadow`
	- Permette di specificare l'ombra del `box`.
- `{CSS} resize`
	- Permette all'utente di ridimensionare i `box`.
- `{CSS} box-sizing`
	- Permette di far rientrare le dimensioni di [[#Padding]] e [[#Border]] nel computo di `width` e `height`, di default ha valore `{cSS} content-box`.

```css
div {
	border-radius: 0px 30px; 
	border: 3px blue solid;
	box-shadow: grey 15px 15px 10px;
	background-color: rgba(0, 0, 255, 0.2);
	color: blue;
}
```
## Componenti
---
>[!abstract] Componenti
>Il ***box model*** è composto di 4 livelli di "*scatole*":
>- *Content*.
>- *Padding*.
>- *Border*.
>- *Margin*.

![[BoxModel.png]]

### Content
>[!tldr] Idea
>Elemento più interno del ***box model***.
>È possibile definire le ***dimensioni del contenuto*** con le proprietà `width` e `height`.

È possibile anche definire una dimensione minima e massima con le proprietà:
- `min-width`, `min-height`.
- `max-width`, `max-height`.

Solitamente si *specifica solo la larghezza*.
- In questo modo l'altezza di un elemento viene ***determinata dal suo contenuto***.

Se il contenuto richiede *più spazio di quanto è stato specificato* è possibile gestire la situazione con la proprietà `overflow`.
- `visible`: Il contenuto eccedente viene *mostrato*.
- `hidden`: Il contenuto eccedente viene *nascosto*.
- `scroll`: Vengono mostrate le ***barre di scorrimento*** per visualizzare il contenuto eccedente.
- `auto`: Il contenuto viene mostrato in base alle *impostazioni del browser*.

### Margin
>[!tldr] Idea
>Il ***margin*** permette di impostare lo ***spazio tra un elemento e gli altri*** elementi della pagina.

Modificabile tramite quattro proprietà singole:
- `margin-top`, `margin-right`, `margin-bottom`, `margin-left`.
- Con valori possibili: ***Valore numerico*** con unità di misura o valore ***in percentuale***.

Esiste una proprietà abbreviata `margin`:
```css
p{margin: 5px 7px 8px 10px} /*top rightbottom left*/
p{margin: 5px 7px 6px } /*top right-leftbottom*/
p{margin: 5px 10%} /*top/bottom right-left*/
p{margin: 5px } /*all*/
```

La distanza di due elementi ***allineati orizzontalmente***, è data dalla somma dei due margini.
La distanza di due elementi ***allineati verticalmente***, invece, è data dal *margin collapsing*: valore massimo fra i due margini.

### Padding
>[!tldr] Idea
>Il ***padding*** permette di impostare lo spazio fra il contenuto e il bordo.
>Al contrario dei margini, il *padding* ha lo stesso colore di sfondo dell'elemento.

Come *margin* ha quattro proprietà singole:
- `padding-top`, `padding-right`, `padding-bottom`, `padding-left`.
- Con o valori e unità di misura o percentuali.

Anche padding ha la proprietà abbreviata
```css
p{padding: 5px 7px 8px 10px} /*top rightbottom left*/
p{padding: 5px 7px 6px } /*top right-leftbottom*/
p{padding: 5px 10%} /*top/bottom right-left*/
p{padding: 5px } /*all*/
```

### Border
>[!tldr] Idea
>Permette di impostare lo spessore, lo stile e il colore di ognuno dei ***quattro bordi***.

Esistono tre proprietà singole per **ognuno dei quattro bordi** (12 in totale):
- `{CSS icon} border-pos-width`
	- *Valori*: tramite keyword: `thin`, `medium`, `thick`; Tramite *valore numerico* con unità di misura.
- `{CSS icon} border-pos-style`
	- *Valori possibili*: `none` o `hidden` (nessun bordo), `solid` (bordo continuo), `dotted` (a puntini), `dashed` (tratteggiato), `double` (doppio), `groove` `ridge` `inset` `outset` (effetti tridimensionali).
- `{CSS icon} border-pos-color`.
- `{css icon} border-image`
	- Permette di specificare una immagine che viene usata come bordo.
- `{CSS icon} border-radius`
	- Permette di specificare *bordi arrotondati*, ha delle proprietà estese:
		- `{css} border-top-left-radius`.
		- `{css} border-top-right-radius`.
		- `{css} border-bottom-right-radius`.
		- `{css} border-bottom-left-radius`.

Dove `pos` può essere `top`, `right`, `bottom`, `left`.
