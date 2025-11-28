![[UML#^f4a071]]

## Diagramma dei Casi d'Uso
---
>[!info]
>Rappresentano i ruoli di utilizzo del sistema da parte di uno o più utilizzatori (*attori*).
>- Esseri umani, organizzazioni, enti, altre applicazioni.
>Mostra in che modo gli **attori** *interagiscono* con il **sistema**.

**Non** mostra la logica interna della funzione né la struttura del sistema.

Sono espressi in forma testuale, comprensibile anche per i ***non*** "*addetti ai lavori*".
- Unico diagramma ***abbastanza semplice*** per essere usato con l'**utente**.
- Rappresenta le *specifiche funzionali*.

### Attore vs Caso d'Uso
>[!important] Actor
>Un ***attore*** identifica il ruolo che un'entità esterna assume quando *interagisce con il sistema*.
>- Sintatticamente è una classe [[UML#^f653b6|stereotipata]] ad "*actor*".

- È sempre **esterno al sistema**, anche se il sistema ne può mantenere una rappresentazione interna.
- Spedisce o riceve messaggi dal sistema, o scambia informazioni con esso.
- ***Esegue i casi d'uso***.

>[!info] Use Case
>Un ***caso d'uso*** è la specifica di una sequenza di azioni che un sistema, sottosistema o classe, può *eseguire interagendo* con attori esterni.

- È una ***funzionalità***.
- Produce un *risultato osservabile*, utile all'attore.
- Sempre attivato da un attore.

### Graficamente
> Graficamente gli attori e i casi d'uso sono rappresentati nel seguente modo.

![[UseCaseComponents.svg]]
#### Relazioni nel Diagramma
> Generalizzazione tra Attori

![[ActorGeneralization.svg]]

> Comunicazione Unidirezionale

![[UnilateralCommunication.svg]]

> Inclusione e Generalizzazione tra Casi d'Uso

![[UseCaseInclusionGeneralization.svg]]

> Estensione di Casi d'Uso

![[UseCaseExtention.svg]]

### Ruolo dei Casi d'Uso
>[!abstract] Fasi iniziali
>Nelle fasi iniziali della progettazione servono per chiarire ***cosa dovrà fare il sistema***.

Ragionare sui *casi d’uso* con il **committente** è uno dei modi più ***efficaci ed efficienti*** per scoprire ed analizzare i requisiti ai quali il sistema dovrà fornire un’implementazione.
- Spesso si usa come "[[Analisi dei Requisiti#^e7b16b|milestone]]" contrattuale.

> I casi d’uso ***guidano l’intero progetto di sviluppo***.
- Costituiscono il punto di partenza per la *progettazione del sistema*
- Sono il riferimento primario per la definizione, progettazione e esecuzione dei ***test***.

#### Identificare i Casi d'Uso
>[!failure] Processo a Step

1. Individuare i ***confini del sistema***.
2. Identificare tutti gli utilizzatori del sistema (*attori*).
3. Per ogni tipologia di attore, rilevare in *quale modo userà il sistema*.
	- Ad ogni modalità di utilizzo corrisponde un Caso d'Uso.
4. Per ogni caso d'uso descrivere lo ***scenario di base*** e le principali varianti.

>[!summary] Scenario
>Ogni specifica esecuzione di un caso d'uso è uno ***scenario***.

Uno ***scenario di base*** è la sequenza di passi più semplice possibile che conduce al *successo* del caso d'uso.
- Esistono scenari di *successo* e scenari di *fallimento*.

>[!example] Esempio

> Caso d'Uso: ***Apri Conto Corrente Bancario***.

**Scenario di Base**:
1.  Il cliente si presenta in banca per aprire un nuovo c/c.
2. L’addetto riceve il cliente e fornisce spiegazioni.
3. Se il cliente accetta fornisce i propri dati.
4. L’addetto verifica se il cliente è censito in anagrafica.
5. L’addetto crea il nuovo conto corrente.
6. L’addetto segnala il numero di conto al cliente.

*Varianti*
$3.a)$  Se il cliente non accetta il caso d'uso termina. 
$3.b)$ Se il conto va intestato a più persone vanno forniti i dati di tutte.
$4.a)$ Se il cliente non è censito l'addetto provvede a registrarlo.

#### Specifiche del Caso d'Uso
>[!info]
>L'`UML` non suggerisce il modo per *specificare un caso d'uso*, lasciando spazio libero a tutte le possibili forme di ***documentazione testuale***.

La specifica ha un ruolo centrale nella comunicazione tra diversi soggetti coinvolti nello sviluppo di un sistema.

***Specifiche***:
> Nome, Identificatore.

> Breve descrizione.
- Fissa l'obbiettivo del caso.

> Attori Primari e Secondari.
- Coloro che ***avviano il caso*** e coloro che ***interagiscono*** dopo l'avvio.

> Precondizioni.
- *Condizione* che devono essere eseguite ***prima*** che il caso possa essere eseguito.

> Sequenza principale degli eventi
- I ***passi*** che costituiscono il caso d'uso.

>  Postcondizioni.
- *Condizioni* che devono essere vere ***dopo la conclusione*** del caso.

> Sequenze alternative degli eventi.
- Elenco di alternative alla sequenza principale.