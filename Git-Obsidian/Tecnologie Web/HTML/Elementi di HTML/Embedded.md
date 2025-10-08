![[Elementi e Categorie#^d97192]]

Alcuni elementi *embedded* prevedono un contenuto ***fallback***, che viene usato quando la risorsa esterna non può essere usata (*formato non supportato*).

## Figure
---
>[!info] `{html icon} <figure>`
>Elemento che ***raggruppa l'immagine e la sua didascalia***.
>- `{html icon} <figcapture>` definisce la *didascalia*.

Le immagini inline sono definite attraverso l'elemento `{html icon} <img>`.
Gli ***attributi obbligatori*** sono:
- `src`: specifica l'*URL* del file contenente l'immagine.
- `alt`: ***testo alternativo***, usato nel caso il browser non riesca a mostrare l'immagine, se l'immagine è per puro abbellimento si *lascia vuoto*.

Altri attributi opzionali sono:
- `usemap`: specifica che l'immagine è una ***mappa lato client***.
- `ismap`: specifica che l'immagine è una ***mappa lato server***.
- `width` e `height`: specificano **larghezza** e **altezza** in `pixel`.
- `longdesc`: *URL* che porta alla descrizione lunga per l'*accessibilità* (deprecato ma non ancora rimpiazzato).

```html title:example
<figure>
  <img src="pic_trulli.jpg" alt="Trulli" style="width:100%">
  <figcaption>Fig.1 - Trulli, Puglia, Italy.</figcaption>
</figure>
```

## Video
---
>[!info] `{html icon} <video>`
>Elemento che definisce un modo standard per ***includere un video*** in una pagina `web`.

Gli attributi principali sono:
- `controls`: aggiunge i ***controlli per il video*** (play, pausa, volume, etc...).
- `width` e `height`: calcolati mantenendo le proporzioni originali del video.
- `autoplay`: fa partire ***automaticamente*** il video.
Il testo contenuto in `{html icon} <video></video>` viene mostrato in caso in cui il browser non supporti l'elemento.

```html title:example
<video width="320" height="240" controls>  
	<source src="movie.mp4" type="video/mp4">  
	<source src="movie.ogg" type="video/ogg">  
	Your browser does not support the video tag.  
</video>
```

## Audio
---
>[!info] `{html icon} <audio>`
>Elemento che definisce un modo per ***includere un audio*** in una pagina.

Simile a `{html icon} <video>`.

```html title:example
<audio controls>  
	<source src="music.mp3" type="audio/mp3">    
	Your browser does not support the audio tag.  
</video>
```

## Object
---
>[!info] `{html icon} <object>`
>Definisce un oggetto incluso in un documento `HTML`.

Usato per includere audio, video, animazioni e ***plug-in***, nelle pagine `web`.
- Ammette versioni alternative dell'oggetto con `{html icon} <bject>` *annidati*.

## Canvas
---
>[!info] `{html icon} <canvas>`
>Elemento che fornisce le `API` necessarie per la ***generazione*** e il ***rendering dinamico*** di grafica, diagrammi, immagini e animazioni.

Definisce un'area rettangolare in cui disegnare direttamente immagini bidimensionali e modificarle in relazione a ***eventi*** tramite funzioni `{js icon} javascript`.
- Le coordinate $(0,0)$ corrisponde all'angolo in alto a sinistra.
