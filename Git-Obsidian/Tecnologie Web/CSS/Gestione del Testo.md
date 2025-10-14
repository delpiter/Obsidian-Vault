> Esistono diverse proprietà per la gestione del testo.

## Aspetto dei Caratteri
---
>[!info] Font
>Un ***font*** è un insieme completi di caratteri contraddistinti da un particolare disegno.

È possibile specificare le seguenti ***proprietà***:
- `{css} font-family`: specifica il nome di uno o più font (es: `Verdana`, `Helvetica`) o un font generico (`serif`, `sans-serif`, `monospace`, `cursive`, `fantasy`).
- `{css} font-style`: specifica lo stile del testo. Valori possibili:
	- `normal`
	- `italic`
	- `oblique`
- `{css} font-variant`: applica l'effetto maiuscoletto. Valori:
	- `normal` (default)
	- `small-caps`
- `{css} font-weight`: specifica il peso del carattere. Valori:
	- **Numerici**: da `100` a `900`
	- **Parole chiave**:
		- Assolute: `normal`, `bold`
	    - Relative: `bolder`, `lighter`
- `{css} font-size`: specifica la dimensione del testo. Può essere espressa in:
	- **Dimensione assoluta**:
		- Unità: `px`, `pt`
	    - Keyword: `xx-small`, `x-small`, `small`, `medium`, `large`, `x-large`, `xx-large`
	- **Dimensione relativa**:
	    - Unità: `em`, `ex`, `%`
	    - Keyword: `smaller`, `larger`

## Formattazione
---
- `{css} color`: specifica il colore del testo. Può essere espresso come:
	- Nome del colore (es: `red`)
	- Valore **esadecimale** (es: `#rrggbb`)
	- Valore in *codifica* (es: `rgb(0, 255, 2)`, `hsl(20, 3%, 40%)`)
- `{css} letter-spacing`: definisce lo spazio tra le lettere. Valori possibili:
	- `normal`
	- Valore in unità di lunghezza (es: `2px`)
- `{css} line-height`: specifica l’interlinea. Può essere espresso come:
	- Valore numerico (es: `1.5`)
	- Lunghezza (es: `20px`)
	- Percentuale (es: `120%`)
- `{css} text-align`: allinea il testo. Valori possibili:
	- `left`, `right`, `center`, `justify`.
- `{css} text-decoration`: applica effetti decorativi al testo. Valori:
	- `none`, `underline`, `overline`, `line-through`.
- `{css} direction`: direzione del testo. Valori:
	- `ltr` (da sinistra a destra)
	- `rtl` (da destra a sinistra)
- `{css} text-indent`: imposta l'indentazione della prima riga del testo. Può essere espressa in:
	- Lunghezza (es: `20px`)
	- Percentuale (es: `5%`)
- `{css} text-overflow`: definisce il comportamento del testo quando supera i limiti del contenitore. Esempi:
	- `clip`.
	- `ellipsis`.
- `{css} text-shadow`: applica un'ombreggiatura al testo. Sintassi:
	- `h-shadow v-shadow blur-radius color` (es: `2px 2px 5px black`).
- `{css} text-transform`: controlla la trasformazione del testo. Valori:
	- `none`, `capitalize`, `uppercase`, `lowercase`.
- `{css} white-space`
	- Specifica come sono gestiti spazi bianchi e andate a capo. Valori:
		- `normal`, `nowrap`, `pre`, `pre-line`, `pre-wrap`.
- `{CSS} word-wrap`
	-  Permette di forzare l'*andata a capo* per le parole molto lunghe che non rispettano i bordi dell'elemento contenitore.
- `{CSS} vertical-align`
	- *Allineamento* degli elementi inline.