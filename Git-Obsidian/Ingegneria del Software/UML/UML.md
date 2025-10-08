## Unified Modeling Language
---
>[!info]
>`UML` è un **linguaggio** che definisce una *notazione standard* basata su un ***metamodello*** integrato deggli "**oggetti**" che compongono un *sistema software*.
>- **Non** descrive una *sequenza di processo*.
>- È usato da persone e gruppi che *seguono metodi diversi*.

`UML` è uno *standard* [OMG](https://www.omg.org/about/omg-standards-introduction.htm).

> L'`UML` fornisce i costrutti per le seguenti fasi dello sviluppo dei sistemi software.
- [[Analisi dei Requisiti]] tramite i ***casi d'uso***.
- Analisi e progetto [[Paradigma ad Oggetti|object oriented]].
- **Modellazione** dei *componenti*.
- **Modellazione** della *struttura* e della configurazione.

Il modello `OOA/OOD` (Object Oriented **Analysis**/**Design**) viene espresso tramite dei ***diagrammi grafici***.
- Ogni entità del modello può comparire in uno o più diagrammi.

>[!check] Diagramma vs. Modello
>In `UML` c'è distinzione tra i concetti di **modello** e di **diagramma**.
>- Un ***modello*** contiene *elementi di informazione* circa il sistema sotto osservazione.
>- Un ***diagramma*** è una *particolare visualizzazione* di alcuni tipi di elementi di un modello.

Un certo **elemento** può comparire in *più diagrammi*, ma è ***univoca*** la sua definizione all'interno del *modello*.

### Struttura UML
> La struttura di `UML` è composta da:

>[!todo] Costituenti Fondamentali
>Gli ***elementi di base***.

- *Entità*, *Relazioni* e *diagrammi*.

>[!caution] Meccanismi Comuni
>***Tecniche*** comuni per raggiungere specifici obbiettivi.

- *Specifiche*, *Ornamenti*, *Distinzioni Comuni* e *Meccanismi di Estendibilità*.

>[!tip] Architettura
>L'espressione dell'***architettura del sistema***.

#### Costituenti Fondamentali
##### Entità
> Sono gli elementi di modellazione.

>[!abstract] Strutture

- **Classe**
![[Class.svg]]
- **Interfaccia**
![[Interface.svg]]
- **Collaborazione**
![[Collaboration.svg]]
- **Caso d'uso**
![[UseCase.svg]]
- **Componente**
![[Component.svg]]
- **Nodo**
![[Node.svg]]

>[!failure] Comportamenti

- **Interazione**
![[Interaction.svg|150]]
- **Stato**
![[State.svg|150]]

>[!help] Raggruppamenti

- **Package**
![[Package.svg|150]]

>[!info] Informazioni

- **Annotazione**
![[Annotation.svg|150]]

##### Relazioni
> Legano tra loro le entità.

- **Dipendenza**
	- Un'entità $B$ dipende da una entità $A$ se una variazione di $A$ *può* causare una variazione in $B$.
[[Normalizzazione#Dipendenze Funzionali|Ripasso Dipendenze Funzionali]].

![[Dependency.svg|150]]
- **Associazione**: linea *senza punte*.
- **Aggregazione**
![[Aggregation.svg|150]]
- **Contenimento**
![[Containment.svg|150]]
- **Generalizzazione**
![[Generalization.svg|150]]
- **Realizzazione**
![[Implementation.svg|150]]
- **Composizione**
![[Composition.svg|150]]

##### Diagrammi
> Sono viste sul modello `UML`

###### Statici
>[!tip] Class Diagram
>Descrive la ***struttura dei dati degli oggetti*** del sistema e le loro relazioni.
>- È il diagramma più importante, da cui si può generare il codice.

>[!help] Object Diagram
>Mostra un ***insieme di oggetti di interesse*** e le loro relazioni.
>- È un'**istanza** del diagramma delle classi.

>[!abstract] Package Diagram
>Mostra i **package** e le loro *relazioni di dipendenza*, *contenimento* e *specializzazione*.

>[!summary] Component Diagram
>Descrive l'***architettura software*** di sistema.
>- Descrive interfacce esposte e relazioni tra di esse.

>[!missing] Deployment Diagram
>Descrive la ***struttura del sistema hardware*** e l'allocazione dei vari moduli software.

>[!tip] Composite Structure Diagram
>Mostra la ***struttura interna*** di classificatori strutturati.

###### Dinamici
>[!todo] Use Case Diagram
>Elenca i ***casi d'uso del sistema*** e le loro relazioni.
>- Normalmente *disegnato per primo*.

^f4a071

Unico diagramma ***abbastanza semplice*** per essere usato con l'**utente**.
- Rappresenta le *specifiche funzionali*.

>[!failure] State Diagram
>Usa la notazione degli automi di Harel per ***descrivere gli stati degli oggetti*** di una classe.
>- Descrive **stati** e **transizioni di stati** (Ambito: *Una sola classe*).

>[!info] Activity Diagram
>Descrive le ***sequenze eventi-azioni-transazioni*** di una funzione.
>- Ha il *focus* su una funzione del sistema.
>- Ha caratteristiche sia *funzionali* che *dinamiche*.
>- Viene usato per rappresentare un "***workflow***".

>[!check] Sequence Diagram
>Mostra le ***interazioni tra gli oggetti*** durante *scenari di funzionamento* del sistema.

#### Meccanismi Comuni
##### Specifiche
> Sono la descrizione testuale della semantica di un elemento.

![[Specifics.svg]]

##### Ornamenti
> Rendono visibili gli aspetti particolari della specifica dell'elemento.

![[Ornaments.svg]]
##### Distinzioni Comuni
>[!hint] Classificatore e Istanza
>Separa la ***notazione astratta*** di un'entità dalle sue ***concrete istanze***.
>- Un'*istanza* ha di solito la stessa forma del classificatore, ma con il nome <u>sottolineato</u>.

>[!example] Interfaccia e Implementazione
>Separa "**cosa**" un oggetto fa da "**come**" lo fa.
>- Un'interfaccia definisce un "***contratto***" che ciascuna sua implementazione garantisce di rispettare.

##### Meccanismi di Estendibilità
>[!bug] Stereotipo
>Uno ***stereotipo*** rappresenta una variazione di un elemento di modellazione esistente, con la *stessa forma ma diverso scopo*.
>- Permette di introdurre nuovi elementi di modellazione a partire da quelli esistenti.

^f653b6

![[Stereotype.svg]]

>[!proprietà]
>Una ***proprietà*** è un valore associato a un elemento del modello, espresso da una stringa associata all'elemento.

```
{ author = "Joe Smith", status = analysis } { abstract }
```

>[!missing] Vincolo
>Un ***vincolo*** è una *frase di testo che definisce una condizione* o una regola che riguarda un elemento del modello e ***deve risultare sempre vera***.

```
{ disjoint, complete } { subset }
```

L'insieme di questi 3 meccanismi è chiamato ***profilo***.
- È usato per personalizzare `UML`.

#### Architettura
> Vista dei casi d’uso

- Descrive le ***funzionalità del sistema*** come vengono percepite dagli utenti, dagli analisti e dagli esecutori del testing.
- **Non** specifica l’*organizzazione del software* ma è la base per le altre viste.

> Vista logica

- Stabilisce la ***terminologia del dominio*** del problema sotto forma di classi e oggetti, illustrando come essi implementano il comportamento richiesto.
 
> Vista dei processi

- È una ***variante orientata ai processi*** della vista logica; modella i *thread* e i *processi* sotto forma di classi attive.

> Vista di implementazione

- Descrive i ***moduli implementativi*** e le loro dipendenze, illustrandone la configurazione così da definire il concetto di versione del sistema.
 
 > Vista di deployment
 
 - Mostra la ***distribuzione fisica del sistema*** software sull'architettura hardware.