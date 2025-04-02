## Modelli dei Dati
---
>Un ***modello dei dati*** è una *collezione* di **concetti** che sono utilizzati per ***descrivere i dati***, le loro associazioni e i vincoli che questi devono rispettare.

>[!tldr] Modelli Logici
>I ***modelli logici*** sono usati nei ***DBMS*** per l'*organizzazione dei dati* e usati dai programmi, ***indipendenti*** dalle ***strutture fisiche***

>[!abstract] Modelli Concettuali
>I [[Definizioni Importanti#Modello Concettuale|modelli concettuali]] permettono di rappresentare i dati in modo *indipendente* da ogni particolare sistema.
>Cercano di descrivere i ***concetti del mondo reale***.
>Sono usati nelle fasi preliminari di progettazione

I modelli concettuali prevedono una ***rappresentazione grafica***
- Utile come strumento di *documentazione* e *comunicazione*

## Modello Entity-Relationship
---
>Caratterizzato da una *rappresentazione grafica intuitiva* che consente di disegnare **schemi** E/R che facilitano la *comprensione* delle ***informazioni*** modellate
### Costrutti del Modello
>[!todo] Concetti Fondamentali
>- ***Entità*** (entity)
>- ***Associazione*** (relationship)
>- ***Attributo*** (attribute)

>[!example] Altri costrutti
>- ***Vincolo di Cardinalità*** (cardinality constraint)
>- ***Identificatore*** (identifier)
>- ***Gerarchia di Generalizzazione*** (generalization)
#### Entità
>[!definizione] Definizione
> Una ***entità*** sono elementi della realtà ***raggruppati in una classe***, avendo caratteristiche comuni.
> Hanno una esistenza "***autonoma***", indipendente dalle *proprietà associate*

Graficamente un'entità si rappresenta con un ***rettangolo*** al cui interno è evidenziato la ***denominazione dell'entità*** stessa

![[Entity.png]]

>[!info] Livello Intensionale
>Il ***livello intensionale*** è lo schema che rappresenta un'entità, ne descrive la *struttura*.

>[!hint] Istanza
>Un'***istanza di un'entità*** è uno specifico oggetto *appartenente all'insieme* che quella ***entità*** rappresenta

##### Denominazione
>[!warning] Importante
>Il nome di un'entità deve essere univoco all'interno di uno schema

***Non esiste*** una convenzione per il nome da assegnare a un'entità
- È preferibile utilizzare un ***sostantivo al singolare***

"***Persona***" è una denominazione preferibile a "***Persone***"
##### Estensione di un'entità
>A ***livello estensionale*** un'entità è un insieme di istanze ammissibili per quella entità.

>[!done] In Breve
> Un'***estensione di un'entità*** a un certo tempo è un ***insieme*** di specifici oggetti

#### Associazione
>[!definizione] Definizione
>Un'***associazione*** o ***relazione*** rappresenta un *legame logico* tra entità, rilevante nella realtà che si sta considerando

>[!hint] Istanza
>Una ***istanza di una associazione*** è una combinazione di *istanze delle entità* che prendono parte all'associazione.
>>[!done] In altre Parole
>>N-upla costituita da *occorrenze di entità*, una per ciascuna delle entità coinvolte.

Graficamente un'*associazione* si rappresenta con un **rombo** al cui interno ne viene evidenziata la ***denominazione***.
![[BinaryRelation.png]]
- Se $p$ è istanza di *Persona* e $c$ è istanza di *Città*, la coppia $(p,c)$ è istanza dell'associazione *Residenza*

> Per definizione:
- L'insieme delle istanze di un'associazione è un ***sottoinsieme del prodotto cartesiano*** degli insiemi delle istanze di entità che partecipano
##### Denominazione
>[!warning] Importante
>Il nome di un'entità deve essere univoco all'interno di uno schema

È preferibile usare un *sostantivo al singolare* per denotare un'associazione, invece di un verbo o di una composizione di nomi di entità.

> Siano "***Persona***" e "***Città***" due entità

***Residenza*** è una denominazione dell'associazione preferibile a ***Risiede*** o ***Persona-Città***

##### Grado delle Associazioni
> Una associazione ***n-aria*** coinvolge $n$ entità, non necessariamente distinte

>[!definizione] Grado di un'associazione
> Il ***grado di un’associazione*** è il numero di istanze di entità che sono coinvolte in un’istanza dell’associazione

***Associazione Binaria***:
- *Grado* 2
- Un'istanza è una ***coppia*** di istanze di entità

***Associazione Ternaria***:
- *Grado* 3
- Un'istanza è una ***terna*** di istanze di entità
##### Associazioni ad Anello
>[!info] Definizione
>Legame fra un’entità e un’***occorrenza di se stessa***
>Un'associazione ricorsiva può essere o meno:
>- *Simmetrica*: $(a,b)\in A \implies (b,a)\in A$
>- *Riflessiva*: $(a,a) \in A$
>- *Transitiva*: $(a,b) \in A, (b,c) \in A \implies (a,c) \in A$

###### Tipi di associazioni ad Anello:

**Simmetrica**
- *Persona* collega di *Persona* (**many to many**)

**Asimmetrica**
- *Persona* erede di *Persona* (**one to many**)
- *Persona* sposata ad una *Persona* (**one to one**)

#### Attributo
>[!definizione] Definizione
>Un ***attributo*** è una *proprietà elementare* di un'entità o di un'associazione

> Denotato con un nome che ***deve essere univoco*** all'interno dell'entità o associazione

Graficamente:
![[Attribute.png]]

Ogni attributo è definito su un ***dominio di valori***.

>[!example] Tipi di attributi
>- **Semplice**
>- [[#^75c92b|Multivalore]] (con cardinalità, es. persona con più numeri di telefono)
>- **Composto**: (Es: indirizzo(via, numero civico, cap))
>	- Attributi *multivalore* che sono ***semanticamente correlati***
#### Vincoli
>In ogni schema E/R sono presenti ***vincoli***

Alcuni vincoli sono *impliciti*:
- Ogni **istanza di un'associazione** deve riferirsi a **istanze di entità**
- La coppia $(a,b)$ ***non*** può essere presente due volte nell'associazione $A\text{\&}B$

>[!note] Vincoli Espliciti
>Altri vincoli sono **espliciti** e sono definiti da chi progetta lo schema **E/R** sulla base della *conoscenza della realtà* che sta modellando

#### Vincoli di Cardinalità
##### Attributi
>[!info] Uso
>Per un attributo è possibile specificare anche il ***numero minimo*** e il ***numero massimo*** di valori che possono essere associati
>

Un attributo è detto:

>[!question] Opzionale

Se la ***cardinalità minima*** è $0$

>[!attention] Monovalore

Se la ***cardinalità massima*** è $1$

>[!summary] Multivalore

^75c92b

Se la ***cardinalità massima*** è $n$

##### Associazioni
>[!definizione] Definizione
>I ***vincoli di cardinalità di associazioni*** sono coppie di valori $(min-card, max-card)$ che vengono specificate per *ogni partecipazione* di entità ad un'associazione e descrivono **numero minimo** e **numero massimo** di occorrenze di relazione a cui una entità può partecipare

>[!example] Esempio

Se i *vincoli di cardinalità* per un’entità $E$ relativamente a un’associazione $A$ sono $(1,n)$ ciò significa che:
- **Ogni istanza** di $E$ partecipa ***almeno a una*** istanza di $A$
- **Ogni istanza** di $E$ può partecipare a ***più istanze*** di $A$.

>Graficamente:

![[RelationCardinality.png]]
###### Tipi di Associazioni

*Associazione*
  - Associazione 1 a 1
  - Associazione 1 a molti
  - Associazione molti a molti

>[!abstract] Sulla base della cardinalità minima
>***Opzionale***
>- Se $min-card(E, A) = 0$
>
>***Obbligatoria***
>- Se $min-card(E, A)>0$

>[!hint] Sulla base della cardinalità massima
>***A valore singolo***
>- Se $max-card(E, A) = 1$
>
>***A valore multiplo***
>- Se $max-card(E, A)>1$


#### Identificatori
>[!definizione] Definizione
> Un ***identificatore*** è un attributo o insieme di attributi che identificano l’occorrenza di un’entità o relazione.
> Un ***vincolo d’identificazione*** per un’entità $E$ definisce un *identificatore* per $E$

> ***Proprietà di Minimalità***
- Per ogni estensione ammissibile di un’entità ***nessun sottoinsieme proprio dell’identificatore*** deve essere a sua volta un *identificatore*

>[!warning] Attenzione
>***Deve*** valere:
>$$min-card(A, B) = max-card(A, B) = 1$$

Ogni entità deve avere ***almeno un identificatore***, ma ne può avere ***più di uno***
- In fase di *progettazione logica*, uno di essi sarà scelto come [[Vincoli di Integrità#Chiavi|chiave primaria]], per gli altri si dovrà comunque imporre un **vincolo di unicità**

Nel caso di *più identificatori* è ammesso che gli attributi o le entità coinvolti in alcune identificazioni, **tranne una**, possano essere ***opzionali***
##### Tipologie
>[!abstract] Interno
>Si usano ***uno o più*** attributi dell'entità $E$

>[!caution] Esterno
>Si usano ***altre*** (una o più) ***entità***, collegate a $E$ da associazioni, più *eventuali attributi propri* di $E$.

>Graficamente:

![[Identifiers.png]]

#### Reificazione
>[!definizione] Definizione
>L'operazione di ***reificazione*** consiste nel "*trasformare*" un'**associazione** in una **Entità**

Nasce dalla necessità di avere identificatori all'*interno di una relazione*.

>Il seguente schema:
![[Reification.png]]

>Verrebbe reificato in questo schema.
![[Example.png]]


#### Generalizzazione
>[!abstract] Definizione
>La ***generalizzazione*** è un *legame logico* tra un’entità $E$ (**entità genitore**) e una o più entità $E_{1},E_{2},\dots$ (**entità figlie**), in cui $E$ è il caso *generale* e $E_{1},E_{2},\dots$ sono i casi *particolari*.

>Medesimo concetto nell'[[UML#Generalizzazione|UML]]

Le proprietà di $E$ sono *ereditate* da $E_{1},E_{2},\dots$
- Ogni $E_{i}$ **possiede** gli attributi di $E$ e **partecipa** alle associazioni definite per $E$
- **Non vale** l'inverso

>[!done] Una entità può essere madre di diverse entità in diverse generalizzazioni

>[!fail] Una gerarchia di generalizzazione impone il vincolo che ciascuna sottoclasse abbia una sola superclasse

>[!Gerarchia di generalizzazione]
>Un’entità ***figlia*** è a sua volta entità ***padre*** di altre entità ***figlie***
##### Proprietà di Copertura
![[Generalization.png]]
##### Subset
>[!summary] Definizione
>Il ***subset*** è un caso particolare di *gerarchia* che si ha quando si evidenzia **una sola classe** specializzata.

![[Subset.png|300]]

## Limiti del Modello E/R
---
>Uno ***schema E/R*** non è *sufficiente* a rappresentare *tutti gli aspetti di interesse*

>[!missing] Limiti Principali
>- I nomi dei vari concetti **possono non essere sufficienti** per comprendere il significato
>- Non tutti i **vincoli di integrità** sono esprimibili in uno schema ***E/R***
>	- Es. Propedeuticità degli esami.

In fase di progettazione bisogna fornire un'ulteriore documentazione appropriata per consentire di affrontare correttamente le fasi successive di sviluppo
## BUSINESS RULES

### 2 Tipi
- **Regole di Vincolo** → `<Concetto> DEVE / NON DEVE <ESPRESSIONE SUL CONCETTO>`
- **Regole di Derivazione** → `<Concetto> SI OTTIENE <ESPRESSIONE SUL CONCETTO>`