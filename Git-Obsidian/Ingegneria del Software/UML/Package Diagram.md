## Diagramma dei Pacchetti
---
>[!info]
>Un ***package*** è un raggruppamento di elementi di modello *semanticamente correlati*.

Il numero ideale di classi per package è tra 4 e 10.

Si possono rappresentare ***relazioni di contenimento***.
- Si consiglia di mostrare al *massimo due livelli*.
- I package annidati vedono il ***namespace*** dei package che li contengono.

![[PackageDiagram.svg]]


> Esiste una ***generalizzazione tra due package***
- Quando il *package specifico* si deve conformare all'interfaccia del *package generale*.

### Dipendenze
>[!question] Tipi di Dipendenze
>Esistono vari tipi di ***dipendenze*** nei *diagrammi dei pacchetti*, i più usati sono:
>- Use
>- Trace

> `<<use>>` (*default*)
- Quando un elemento del *package client* ***usa*** in qualche modo un elemento del *package fornitore*.

> `<<trace>>`
- Rappresenta l'evoluzione di un elemento in un ***altro elemento più dettagliato***.

![[PackageDependece.svg]]

Conviene ***dipendenze circolari***.

### Package di Analisi
>[!info]
>I ***package di analisi*** sono gruppi di elementi del modello accomunati da forti correlazioni semantiche.

La fonte migliore per individuarli è il [[Class Diagram]], i migliori candidati sono:
- Le classi appartenenti a ***gerarchie di composizione***.
- Le classi appartenenti a ***gerarchie di specializzazione***.

Anche lo [[Use Case Diagram]] può servire:
- *Uno o più casi d'uso* che supportano un processo o un attore **potrebbero** indicare un package.