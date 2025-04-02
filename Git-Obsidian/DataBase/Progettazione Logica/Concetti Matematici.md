>Nella progettazione logica vengono utilizzati diversi concetti matematici.
## Prodotto Cartesiano
---
>[!definizione] Definizione
>Si considerino due insiemi $A$ e $B$, non vuoti e non necessariamente distinti.
>Si definisce ***prodotto cartesiano*** $A\times B$ come l'insieme delle coppie ordinate $(a,b)$ con $a\in A$ e $b\in B$.

Per definizione $A\times \varnothing = \varnothing\times A = \varnothing$

>Se $A$ e $B$ sono *insiemi distinti* il prodotto cartesiano $A\times B$ è formalmente diverso da $B\times A$ anche se i due prodotti sono in [[Definizioni_Analisi#Corrispondenza biunivoca|corrispondenza biunivoca]].

>[!example] Esempio
>$A=\{ x,y,z \},\quad B=\{ 1,2 \}$
>$A\times B=\{ (x,1),(x,2),(y,1),(y,2),(z,1),(z,2) \}$

La **definizione** può essere estesa considerando $n>0$ insiemi $D_{1},D_{2},\dots,D_{n}$, non necessariamente distinti.

>[!info] Definizione Generale
>Il ***prodotto cartesiano*** $D_{1}\times D_{2} \times\dots\times D_{n}$ è l'insieme di tutte le *ennuple* ordinate $(d_{1},d_{2},\dots,d_{n})$ tali che:
>- $d_{1}\in D_{1},\ d_{2}\in D_{2}, \dots, d_{n}\in D_{n}$

## Relazione Matematica
---
>[!definizione] Definizione
>Si considerino due insiemi $A$ e $B$, *non vuoti e non necessariamente distinti*.
>Ogni ***sottoinsieme non vuoto*** del  [[1 - Combinatoria Elementare#Definizioni di Base|prodotto cartesiano]] $A\times B$ è detto:
>- Relazione da $A$ a $B$.

>Data una relazione $r\subseteq A\times B$:

Si dice che l'elemento $a\in A$ è in **relazione** con l'elemento $b\in B$ se la coppia $(a,b)\in r$

>Se consideriamo $n>0$ insiemi $D_{1},D_{2},\dots,D_{n}$, **non necessariamente distinti**.

>[!info] Definizione Generale
>Una ***relazione matematica*** su $D_{1},D_{2},\dots,D_{n}$ è un qualunque sottoinsieme del prodotto cartesiano $D_{1}\times D_{2}\times\dots \times D_{n}$

- $D_{1},D_{2},\dots,D_{n}$ sono i ***domini*** della *relazione*.
- Il valore di $n$ è detto ***grado*** della *relazione*.
- Il numero di $n$-*uple* di una relazione è la sua ***cardinalità***

### Proprietà
>In una relazione $r$:

>[!abstract] Tutte le $n$-uple sono distinte tra di loro
>Non è definito alcun **ordinamento** tra le $n$-*uple*
>$D_{1}=\{ a,b,c \},\ D_{2}=\{ 1,2,3 \}$
>$$\{ (a,1),(b,2),(c,1),(c,2) \}=\{ (a,1),(b,2),(c,2),(c,1) \}=\{ (b,2),(c,2),(c,1),(a,1) \}$$

>[!caution] Ogni $n$-upla è ordinata rispetto ai domini.
>L'ordine in cui si considerano i ***domini*** è rilevante.
>- $(D_{1}\times D_{2})\neq (D_{2}\times D_{1})$
>$$\{ (a,1),(c,1),(c,2) \}\neq\{ (1,a),(1,c),(2,c) \}$$

