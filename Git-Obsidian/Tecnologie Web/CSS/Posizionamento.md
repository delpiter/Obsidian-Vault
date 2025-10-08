> Identifichiamo 2 comportamenti diversi.

## Comportamento 1
---
>[!tldr] Idea
>Comportamento relativo agli *elementi*, [[Heading#H1-6|h1]], [[Phrasing#P|p]] e [[Phrasing#Div|div]].

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
>Comportamento relativo agli *elementi*, [[Link|a]], [[Phrasing#Ruolo del Testo|strong]], [[Phrasing#Ruolo del Testo|em]] e [[Phrasing#Ruolo del Testo|span]].

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
- `none`: L'elemento scompare dal DOM #addLink, e non viene visualizzato.
- `inline-block`: L'elemento può assumere *dimensioni esplicite*, ma si disporrà **orizzontalmente** e non **verticalmente**.
- `list-item`: Per fare in modo che un elemento si comporti come un [[Flow#List|li]].
- `grid`: Trasforma un elemento in un *grid container*.
- `flex`: Trasforma un elemento in un *flex container*.

Esistono anche valori per trasformare elementi in parti di una [[Flow#Table|tabella]].

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

