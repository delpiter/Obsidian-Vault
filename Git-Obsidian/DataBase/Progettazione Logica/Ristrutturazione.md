## Fase di Ristrutturazione
---
>[!def] Definizione
>La ***ristrutturazione*** è una fase della [[Progettazione Logica]] che consiste nell'eliminazione dallo [[Modello Entity-Relationship|schema E/R]] dei *costrutti* che **non possono** essere direttamente rappresentati nel ***modello logico target*** ([[Modello Relazionale]]).

Si pone l'obbiettivo di *semplificare* la traduzione e [[Analisi dell'Efficienza|ottimizzare le prestazioni]]

## Eliminazione delle Generalizzazioni
---
>Il modello relazionale non può rappresentare direttamente le [[Modello Entity-Relationship#Generalizzazione|gerarchie di generalizzazione]].

>[!done] Soluzione
>Si eliminano le **gerarchie**, sostituendole con entità *e* *relazioni*.

Ci sono 3 possibilità:
- **Collasso** sul *padre*.
- **Collasso** sui *figli*.
- **Sostituzione** con *relazioni*.

![[HirearchyElimination.png]]

### Collasso sull’entità padre
>[!info] Concetto
>Il ***collasso sull'entità padre*** consiste nell'*eliminazione delle entità figlie*, "spostando" gli attributi e le relazioni delle entità figlie sull'**entità padre**.

![[BottomUpCollapse.png]]

>Attributo "***Tipo***":
- Viene introdotto un attributo "**selettore**" aggiuntivo che indica di quale entità figlia si tratta

>[!help] Copertura
>Se la copertura è ***Totale-Esclusiva***:
>- "***Tipo***" assume $n$ valori, quante sono le *sotto entità*.
>
>***Parziale-Esclusiva***:
>- "***Tipo***" assume $n+1$ valori, il valore in più serve per istanze che non appartengono a sotto entità.
>
>***Sovrapposta***:
>- Occorrono tanti **selettori** quante sono le sotto-entità, ciascuno con un valore booleano.
>- Se *parziale* i selettori possono essere **tutti falsi**.

Eventuali **relazioni  connesse** alle *sotto entità*, si trasportano sull'***entità padre***.

>[!done] Pro

Accesso contestuale agli attributi del padre e della figlia.

>[!fail] Contro

**Spreco di memoria** per valori [[Informazione Incompleta#Null|Null]].

### Collasso sulle entità figlie
>[!info] Concetto
>Il ***collasso sulle entità figlie*** consiste nell'*eliminazione dell'entità padre*, "**duplicando**" gli attributi e le relazioni dell'entità padre sulle **entità figlie**.

![[TopDownCollapse.png]]

>[!done] Pro
- ***Conveniente*** quando si fanno operazioni che coinvolgono le *singole entità figlie*.
- **Non** introduce valori [[Informazione Incompleta#Null|Null]].

>[!fail] Contro

- Possibile **solo** se la generalizzazione è ***totale***.
- La copertura *non esclusiva* introduce ***ridondanza***.

### Sostituzione con Relazioni

![[SubstitutionWithRelation.png]]

>Tutte le **entità** vengono mantenute
- Instaurate relazioni tra la entità **padre** e le entità **figlie**
- Le entità figlie sono ***identificate esternamente*** dall'entità padre.

La sostituzione con associazioni è ***sempre possibile***, indipendentemente dalla copertura della gerarchia.

>[!done] Pro

- Conviene se gli *accessi* alle **entità figlie** sono **separati** dagli accessi al **padre**.
- **Non** si introducono valori [[Informazione Incompleta#Null|null]].
- Genera entità con pochi attributi.

>[!fail] Contro

 - **Aumenta** il numero di *accessi* per mantenere i vincoli introdotti.

## Attributi Multi-Valore
---
>[!hint] Obbiettivo
>***Eliminazione*** degli *attributi multivalore*, che non sono presenti nel [[Modello Relazionale|Modello Logico]].

> **Possibilità**:

- Possono essere sostituiti introducendo una relazione **uno a molti**.
	- Aggiungendo *opportuni identificatori*.

>[!warning] Metodo Possibile (*sconsigliato*)

Se è nota la cardinalità massima $K$ di un attributo multivalore, allora è possibile prevedere $K$ attributi a singolo valore.
## Partizionamento e accorpamento di concetti
---
>[!hint] Obbiettivo
> L'**obbiettivo** del ***partizionamento*** e ***accorpamento*** di concetti è quello di *ridurre il numero di accessi*.
>>[!caution] È necessario conoscere il volume dei dati.

### Partizionamento
>[!tldr] Idea
>**Separazione** degli attributi di un concetto che vengono ***acceduti separatamente***.

***Partizionamento Verticale***
- Separazione di un’*entità* sulla base dei suoi attributi.

***Partizionamento Orizzontale***
- Separazione di una *relazione* sulla base dei suoi attributi.
### Accorpamento
>[!tldr] Idea
>**Raggruppamento** di attributi di concetti diversi che vengono ***acceduti insieme***.

Generalmente riguarda associazioni **uno a uno**.
## Scelta degli identificatori

In caso di entità con più identificatori:
- **Necessario sceglierne uno.**
- Evitare attributi con valori nulli.
- Scegliere l’identificatore minimale.
- Preferire identificatori interni.
- Preferire identificatori utilizzati da molte operazioni.