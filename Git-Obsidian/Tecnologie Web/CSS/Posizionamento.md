> Identifichiamo 2 comportamenti diversi.

## Comportamento 1
---
>[!tldr] Idea
>Comportamento relativo agli *elementi*, [[../HTML/Elementi di HTML/Heading#H1-6|h1]], [[../HTML/Elementi di HTML/Phrasing#P|p]] e [[../HTML/Elementi di HTML/Phrasing#Div|div]].

> ***Larghezza***
- Se non specificata occupano il `100%` di quella del padre.
- È possibile specificare un valore con la proprietà `width`.

> ***Altezza***
- L'altezza dipende dal *contenuto dell'elemento*.
- È possibile specificare un valore con la proprietà `height`.

A prescindere dalla larghezza, gli eventi sono disposti ***verticalmente***, *formando una nuova riga*.
- Questi elementi sono chiamati ***elementi di blocco***.

## Comportamento 2
---
>[!tldr] Idea
>Comportamento relativo agli *elementi*, [[../HTML/Elementi di HTML/Link|a]], [[../HTML/Elementi di HTML/Phrasing#Ruolo del Testo|strong]], [[../HTML/Elementi di HTML/Phrasing#Ruolo del Testo|em]] e [[../HTML/Elementi di HTML/Phrasing#Ruolo del Testo|span]].

> ***Larghezza***
- Dipende dal *contenuto* dell'elemento.
- **Non** è possibile specificare un valore con la proprietà `width`.

> ***Altezza***
- L'altezza dipende dal *contenuto dell'elemento*.
- **Non** è possibile specificare un valore con la proprietà `height`.
- È possibile specificare l'altezza della linea con la proprietà `line-height`.

Gli elementi adiacenti sono ***disposti orizzontalmente***.
- Questi elementi sono chiamati ***elementi di linea***.

## Posizionamento
### Display
>[!info] `{CSS icon} display`
>La proprietà `display` determina il tipo di elemento e il *relativo comportamento*.

Oltre a `inline` e `block` questa proprietà può assumere i valori:
- `none`: L'elemento scompare dal [[../JS/DOM|DOM]], e non viene visualizzato.
- `inline-block`: L'elemento può assumere *dimensioni esplicite*, ma si disporrà **orizzontalmente** e non **verticalmente**.
- `list-item`: Per fare in modo che un elemento si comporti come un [[../HTML/Elementi di HTML/Flow#List|li]].
- `grid`: Trasforma un elemento in un *grid container*.
- `flex`: Trasforma un elemento in un *flex container*.

Esistono anche valori per trasformare elementi in parti di una [[../HTML/Elementi di HTML/Flow#Table|tabella]].

### Float
>[!info] `{CSS icon} float`
>La *proprietà* `float` consente di estrarre un elemento dal ***normale flusso del documento***, e lo sposta su un lato, a destra o a sinistra.

Gli elementi appartenenti al normale flusso del documento circonderanno gli elementi "***floating***".

#### Clear
La proprietà `{CSS icon} clear` serve a disattivare l'effetto di `float` sugli elementi che lo seguono.
- Impedisce che al fianco di un elemento ***floating*** compaiano altri elementi.

>***Valori***:
- `none`: `float` consentito su *entrambi i lati*.
- `left`: **impedisce** il posizionamento a *sinistra*.
- `right`: **impedisce** il posizionamento a *destra*.
- `both`: **impedisce** il posizionamento su *entrambi i lati*.

### Layout Multi-colonna Liquido
>[!example] Responsiveness
>Un ***layout responsive*** è un layout in cui la *grandezza della pagina* dipende dalla *finestra del browser*, adattandosi a tutte le risoluzioni.

> Esempio
- La colonna di sinistra *contiene il menu*, occupa il `15%` della pagina.
- La colonna di destra è una *sidebar*, occupa il `20%`.
- La colonna centrale contiene un *articolo* e deve occupare il `65%`.
#### Con Display
Può essere realizzato usando la proprietà `{CSS icon} display` rendendo i contenitori delle $3$ colonne di tipo `inline-block` e definendo la **larghezza delle colonne in percentuale**.

 Le colonne devono essere elementi ibridi `inline-block`.
 - Gli elementi di linea sono solitamente allineati in basso. Se le colonne sono di altezze diverse è necessario specificare un allineamento a partire dall’alto usando la proprietà `{css icon}vertical-align="top"`.
 - Le tre colonne devono occupare in totale al massimo `100%` tra `width`, [[Box Model#Margin|margin]] e [[Box Model#Padding|padding]], altrimenti l’ultima andrà a capo.
 - **NON** devono esserci spazi nel codice `{html icon} HTML` tra una sezione e  l’altra. Altrimenti l’ultima colonna andrà a capo.
 - I [[Box Model#Border|bordi]] **non** possono essere specificati in percentuale, è necessario usare la proprietà `{css icon} box-sizing=border-box` per fare in modo che la grandezza del bordo sia inclusa nella larghezza.

#### Con Float
Può essere realizzato usando la proprietà `{CSS icon} float` e definendo la *larghezza delle colonne in percentuale*.

Le colonne **laterali** devono essere `float`, la centrale **no**.
- La colonna centrale deve avere *margini laterali* almeno delle ***dimensioni delle colonne laterali***.
- Le tre colonne devono occupare al massimo `100%`, altrimenti ci saranno ***sovrapposizioni***.

### Position
>[!attention] `{CSS icon} position`  
>La proprietà `position` consente di specificare il posizionamento dell'elemento ***rispetto al flusso del documento***.

> ***Valori possibili*** (spesso usati):
- `static`: Valore di *default*, l'elemento segue il normale flusso del documento.
- `fixed`: Il [[Box Model|box]] dell'elemento viene sottratto al normale flusso, ***rimane fisso***.

> ***Valori possibili*** (da evitare):
- `relative`.
- `absolute`.

In caso di *elementi sovrapposti*, è possibile gestire quale elemento deve essere visualizzato "***sopra***" con la proprietà `z-index`.
- Verrà visualizzato l'elemento con `z-index` maggiore.
- Funziona **solo** con elementi che non hanno `position="static"`.

## Layout
---
>[!warning] Attenzione
>**Non** è sufficiente impostare un "***layout liquido***", gli elementi si restringeranno in maniera appropriata **fino ad un certo punto**.

Oltre a questo punto è necessario ***cambiare la disposizione degli elementi*** all'interno della pagina.
- Può essere fatto tramite le ***media query***.

### Media Query
>[!info]
>Le ***media query*** permettono di applicare delle regole `{CSS icon} CSS` in base al tipo e alle caratteristiche del **dispositivo su cui si visualizza**.

Si può specificare in due modi:
- Direttamente nell'attributo `{css icon} media` nel tag [[../HTML/Elementi di HTML/Metadati#Link|link]] che [[Cascading Style Sheets#Usare CSS con HTML|importa il foglio di stile]].
- Con il costrutto `{CSS icon} @media`, direttamente nel `{CSS icon} CSS`.

```html
 <link rel="stylesheet" media="media-query" href="style.css"/>
```


```css title:sintax
@media only/not screen and (max-width: 600px) {
	body {
		background-color: lightblue;
	}
}
```

#### Media Type
>Indica il tipo di dispositivo su cui deve essere utilizzato lo stile.

> `{CSS icon} all`
- Indica tutti i *media type* per tutti i tipi di dispositivi.

> `{CSS icon} print`
- Serve per specificare le ***stampanti***.

> `{CSS icon} screen`
- Specifica uno ***schermo generico***.

> `{CSS icon} speech`
- Specifica gli ***screen reader***.

#### Media Features
> Usati per applicare stili in base alla capacità del dispositivo.

> `{CSS icon} width`
- Indica la ***larghezza della finestra*** del browser.

> `{CSS icon} orientation`
- Indica l'***orientamento*** del dispositivo.

> `{CSS icon} resolution`
- Indica la [[../../Computer Graphics/Il Sistema Grafico#Raster Devices|risoluzione dello schermo]] in `DPI` o `DPCM`.

#### Breakpoints
>[!info]
>Dimensioni "*standard*" utilizzati generalmente per identificare smartphone, tablet e pc.

> I ***range*** più comuni sono:
- `<768` per *smartphone*.
- `768 <= x < 1024` per *tablet*.
- `>= 1024` per *desktop*.

Ma si possono essere usati anche ***altri range***.

```css
@media print{ }
@media screen and (min-width: 480px) { }
/* Applicate se il dispositivo è uno schermo di dimensione almeno 480px */
@media screen and (max-width: 699px) and (min-width: 520px) {}
/* Applicate se il dispositivo è uno schermo, la sua dimensione è almeno 520px ma minore di 700px */
@media screen and (max-width: 699px) and (min-width: 520px), (min-width: 1151px) { }
/* Applicate se il dispositivo è uno schermo, la sua dimensione è almeno 520px ma minore di 700px OPPURE la sua dimensione è almeno 1151px */
@media only screen and (orientation: landscape) { }
/* Applicate se il dispositivo è uno schermo e la larghezza è maggiore dell'altezza */
```

### Viewport
>[!info]
> La ***viewport*** è l'area visibile di una pagina `web` in uno schermo.

In alcuni casi, i dispositivi con schermo piccolo renderizzano la pagina in una ***viewport più grande*** dello schermo e poi *restringono il risultato*.

> Il [[../HTML/Elementi di HTML/Metadati#Meta|meta tag]] `viewport` risolve questo problema.
- Un sito ottimizzato per mobile, ha solitamente il seguente contenuto:

```html
 <meta name="viewport" content="width=device-width,initial-scale=1.0"/>
```

**Dove**:
- `width`: Imposta la larghezza del viewport in modo che *segua la larghezza del display*.
- `initial-scale`: Imposta il *livello di zoom iniziale* quando la pagina viene caricata.
