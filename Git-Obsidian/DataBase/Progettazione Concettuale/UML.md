## Analisi Orientata agli Oggetti
---
>[!info] Idea
> L'enfasi è posta sull'***identificazione degli oggetti***, sulla loro ***classificazione*** e sulle ***interrelazioni*** tra oggetti

> Nel tempo le proprietà strutturali degli oggetti restano stabili
- L'uso che si fa degli oggetti può mutare in modo sensibile
## Analisi Orientata alle Funzioni
---
>[!abstract] Idea
>L'obbiettivo è rappresentare un *sistema* come:
>- Una ***rete di processi*** o un ***insieme di flussi informativi*** tra processi

> Nella modellazione funzionale si è fatto ricorso alla rappresentazione con ***DFD***
- ***D***ata ***F***low ***D***iagram
## Analisi Orientata agli Stati
---
>[!info] Idea
>Per alcune categorie di applicazioni può essere utile pensare fin dall'inizio in termini di ***stati operativi*** e ***transizioni di stato***

## Meccanismi di Astrazione
---
>L'analista deve far ricorso a tecniche che consentono di ***organizzare e interrogare la conoscenza*** via via acquisita

>[!summary] Meccanismi di Astrazione
>- Classificazione
>- Generalizzazione
>- Aggregazione
>- Proiezione

### Classificazione
>[!definizione] Definizione
>Raggruppa gli oggetti in ***classi*** in base alle loro ***proprietà***
### Generalizzazione
>Cattura le relazioni di tipo ***<<È un>>*** ovvero permette di *astrarre* le *caratteristiche comuni* fra più classi definendo ***superclassi***

>[!caution] Specializzazione
>La specializzazione è il processo inverso della generalizzazione
#### Copertura delle Generalizzazioni
##### Specializzazione e Classe Generalizzata
>[!todo] Totale
>La classe *generalizzata* è l'***unione delle specializzazioni***
>>[!done] In altre parole
>> Ogni istanza della *classe generalizzata* è istanza di ***almeno una specializzazione***

>[!hint] Parziale
>La classe *generalizzata* ***contiene l'unione*** delle specializzazione
>>[!done] In altre parole
>> Qualche *istanza* della classe generalizzata ***potrebbe non essere*** una ***specializzazione***


##### Confronto fra le Classi Specializzate

>[!todo] Esclusiva
>Gli insiemi delle *generalizzazioni* sono fra loro ***disgiunti***
>>[!done] In altre parole
>> Ogni istanza della classe generale può essere di ***una sola specializzazione***

>[!hint] Sovrapposta
>Può esistere un'***intersezione non vuota*** fra insiemi delle *specializzazioni*
>>[!done] In altre parole
>> Una istanza della classe generale può essere di ***più specializzazioni***

### Aggregazione
>L'aggregazione esprime le relazioni ***<< Parte di >>*** che sussistono tra oggetti, tra funzioni o fra stati

>[!example] Un computer
>Un computer è composto da più componenti:
>- `CPU`
>- `RAM`
>- *Hard Disk*
>- etc...

### Associazioni
>È importante modellare le ***associazioni*** che sussistono *fra le varie classi*

Dal punto di vista della modellazione è importante caratterizzare queste corrispondenze in termini di ***vincoli di cardinalità***

#### Vincoli di Cardinalità
>Sia $A$ un'associazione fra $C_{1}$ e $C_{2}$

>[!help] $min-card(C_{1}, A)$
>Cardinalità minima di $C_{1}$ in $A$
>È il ***numero minimo di corrispondenze*** nell'associazione $A$ alle quali ogni istanza di $C_{1}$ deve partecipare

>[!help] $max-card(C_{1}, A)$
>Cardinalità massima di $C_{1}$ in $A$
>È il ***numero massimo di corrispondenze*** nell'associazione $A$ alle quali ogni istanza di $C_{1}$ può partecipare

###### Vincoli di Cardinalità Minima
>[!hint] Partecipazione Opzionale
>$min-card(C_{1}, A)=0$
>Alcuni elementi di $C_{1}$ ***possono non essere associati*** tramite $A$ a elementi di $C_{2}$

>[!abstract] Partecipazione Obbligatoria
>$min-card(C_{1}, A)>0$
>Ad ogni elemento di $C_{1}$ ***deve essere associato*** tramite $A$, almeno un elemento di $C_{2}$

##### Tipi di Associazioni
>[!summary] One-to-One
>$max-card(C_{1}, A) = 1$
>$max-card(C_{2}, A) = 1$

>[!example] One-to-Many
>$max-card(C_{1}, A) = n$
>$max-card(C_{2}, A) = 1$
><u>oppure</u>
>$max-card(C_{1}, A) = 1$
>$max-card(C_{2}, A) = n$

>[!tip] Many-to-Many
>$max-card(C_{1}, A) = n$
>$max-card(C_{2}, A) = m$
