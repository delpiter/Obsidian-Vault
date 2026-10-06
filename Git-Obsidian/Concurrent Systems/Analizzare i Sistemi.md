## Verification e Testing
---
> [!info] Testing
> Attività di ***ricerca dei fallimenti***, rileva i problemi.

Un difetto è la ***manifestazione di un errore***
- un *errore* è l'azione che produce un risultato incorretto

Incontrare un difetto, potrebbe risultare in un fallimento.

L'obbiettivo del testing è quello di verificare che una proprietà di correttezza è mantenuta per uno specifico scenario.
> [!warning] Rileva la presenza di errori e non l'assenza


> [!info] Verification
> Controlla che il sistema ***soddisfi le specifiche***.
> > [!question] Abbiamo costruito bene il sistema?

L'obbiettivo della verifica è quello di verificare che una *proprietà* è mantenuta per tutti gli scenari possibili (traces).
- Necessita delle tecniche formali.

> [!info] Validation
> Controlla se il sistema ***soddisfa le aspettative*** del cliente.
> >[!question] Abbiamo costruito il corretto sistema?
### Proprietà dei sistemi concorrenti
> Una ***proprietà*** è un *attributo* di un sistema che è vera per tutti gli scenari possibili.

> [!done] [[../../Sistemi Operativi/Teoria/8 - Concorrenza#Proprietà dei Programmi Concorrenti|Safety]]
> La proprietà ***safety*** richiede che una certa condizione sia sempre vera in ogni singolo stato di computazione.

Il "***test of safety***" verifica che il comportamento di una classe o sistema sia conforme alle sue specifiche.

> [!caution] [[../../Sistemi Operativi/Teoria/8 - Concorrenza#Proprietà dei Programmi Concorrenti|Liveness]]
> La proprietà ***liveness*** richiede che una certa condizione sia prima o poi vera in ogni computazione.

### Metodi formali di verifica

> [!abstract] [[Model Checking]]
> La verifica tramite ***model checking*** è fatta generando uno per uno *tutti gli stati del sistema* e controllando le proprietà per ciascuno stato.

Il *model checking* è la tecnica più usata e importante per controllare **automaticamente** la ***correttezza di un sistema concorrente***.

> [!tldr] Idea
> Questo modello si basa nel ***cercare esaustivamente*** l'intero spazio di un sistema e verificare che certe proprietà sono *soddisfatte*.

>[!Danger] Il numero di stati può aumentare molto rapidamente (miliardi di stati diversi)

Le tecniche allo stato dell'arte applicano regole per ridurre il numero di stati.

> [!caution] Dimostrazione induttiva delle invarianti
> Nella verifica tramite questo modello le ***proprietà invarianti*** sono *dimostrate* con l'induzione sugli stati del sistema.

Può essere automatizzato da strumenti chiamati ***sistemi deduttivi***.

Entrambe le tecniche si basano su una specie di [[../../Linguistica Formale e Modelli Computazionali/Linguistica#Linguaggio Formale|linguaggio formale]]per specificare le proprietà di correttezza.

## Descrizione logica delle proprietà
---
> [!abstract] Descrizione Logica
> Una descrizione logica è una espressione composta di proposizioni da operatori come `AND` `OR` o `NOT`.

Una proposizione è una affermazione che è o **vera** o **falsa**.

Il calcolo proposizionale non basta:
> Esempio:
- Il costrutto `{java icon} assert` in java ci permette di specificare una proposizione sullo stato delle variabili selezionate che deve essere vera in un punto particolare del programma.

In questo modello si vogliono specificare proposizioni che sono vere per ***tutte le possibili esecuzione del programma***.
- Senza un riferimento esplicito ad un particolare punto nell'esecuzione.

Una logica che permette di fare questo è il ***Linear Temporal Logic***
### Linear Temporal Logic
> [!abstract] Definizione
> La **logica temporale** è una logica formale ottenuta aggiungendo **operatori temporali** alla logica proposizionale o a quella dei predicati.

#### Famiglie di logiche temporali

| Logica                                         | Cosa permette di esprimere                                                                       | Modello del tempo  |
| ---------------------------------------------- | ------------------------------------------------------------------------------------------------ | ------------------ |
| **LTL** (*Linear Temporal Logic*)              | Proprietà che devono essere vere (in uno stato) per **ogni** scenario possibile                  | Lineare e discreto |
| **Logiche temporali ramificate** (*branching*) | Proprietà che devono essere vere in **alcuni** o in **tutti** gli scenari a partire da uno stato | Ad albero          |

> [!example] Esempio di logica ramificata
> **CTL** (*Computational Tree Logic*).

#### LTL: operatori temporali
#### Always: $\Box$ (globalmente)
> [!abstract] Definizione
> La formula $\Box p$ è vera in uno stato $s$ **se e solo se** $p$ è vera in **tutti** gli stati che seguono $s$.

> **Sinonimo:** $G\,p$ (*globally p*)

L'operatore *always* si usa per specificare le proprietà di sicurezza *safety*, perché indica ciò che deve essere **sempre** vero.
### Eventually: $\Diamond$ (prima o poi)
> [!abstract] Definizione
> La formula $\Diamond p$ è vera in uno stato $s$ di un'esecuzione **se e solo se** $p$ è vera in **almeno uno** degli stati che seguono $s$.

> **Sinonimo:** $F\,p$ (*finally p*)

L'operatore *eventually* si usa per specificare le proprietà di *liveness*, perché indica qualcosa che **prima o poi** deve diventare vero.

#### Proprietà di base
> [!caution] Riflessività

- $\Box p \to p$
- $p \to \Diamond p$

> [!summary] Dualità

- $\neg\Box p \leftrightarrow \Diamond \neg p$
- $\Box p \leftrightarrow \neg \Diamond \neg p$
- $\neg \Diamond p \leftrightarrow \Box \neg p$

> [!check] Combinazioni
- $\Box\Diamond p$
- $\Diamond\Box p$
> [!tip] Intuitivamente
- $\Box\Diamond p$: $p$ è vera **infinite volte** (da ogni stato, prima o poi si ritorna a $p$).
	- Spesso usato per rappresentare *cicli*.
- $\Diamond\Box p$: **da un certo punto in poi**, $p$ è vera **per sempre** (persistenza).

> Esempio di teorema

$$
(\Diamond\Box p \wedge \Diamond\Box q) \to \Diamond\Box (p\wedge q)
$$