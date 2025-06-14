## Modello Logico-Relazionale
---
>[!note] Note
>Il ***modello relazionale*** è un [[Definizioni Importanti#Modello Logico|modello logico]] , nel senso che risponde al requisito di **indipendenza** dalla particolare *rappresentazione dei dati* a livello fisico.

>[!tip] Progettazione Logica
>La fase di ***progettazione logica*** consiste nella **traduzione** dello [[Definizioni Importanti#Modello Concettuale|schema concettuale]] in uno schema logico.

## Modello Relazionale
---
>[!info] Concetto
>Nel ***Modello Relazionale*** i dati sono *divisi in record* di dimensione fissa e **organizzati in tabelle**.

### Relazione nel Modello Relazionale
#### Attributo
>[!todo] Definizione
>Ad ogni occorrenza di **dominio**, si associa un nome univoco nella **relazione**.
>- Specifica il ruolo che quel dominio ***svolge nella relazione***
>

>[!example] Esempio.

| TeamCasa         | TeamOspite           | PuntiCasa | PuntiOspite |
| ---------------- | -------------------- | --------- | ----------- |
| Enel Brindisi    | Sidigas Avellino     | $92$      | $88$        |
| MIA Cantù        | Virtus Bologna       | $94$      | $87$        |
| Fiat Torino      | Vanoli Cremona       | $88$      | $80$        |
| The Flex Pistoia | Consultinvest Pesaro | $86$      | $83$        |
> La struttura non è più ***posizionale***
- L'***ordine*** degli attributi **non ha più rilevanza**
	- Si supera il problema della non commutatività del [[Concetti Matematici#Prodotto Cartesiano|prodotto cartesiano]]

##### Dominio di un attributo
>[!done] Definizione
>Ogni attributo dispone di un ***dominio*** che definisce l'insieme dei valori *validi per quell'attributo*

#### Relazione
>Si indichi con $dom(A)$ il ***dominio*** dell'attributo $A$ e si consideri un insieme di attributi $X=\{ A_{1},A_{2},\dots,A_{n} \}$

>[!summary] Tupla
>Una **tupla** su $X$ è una *funzione* che associa a ogni $A_{i}\in X$ un valore di $dom(A_{i})$

>[!example] Schema di Relazione
>Uno schema di relazione $R(X)$ è definito da un nome della relazione $R$ e dall'insieme di attributi $X=\{ A_{1},A_{2},\dots,A_{n} \}$
>- Lo schema $R(X)$ definisce a livello [[Modello Entity-Relationship#Entità|intensionale]] una relazione

**Scelta del nome**:
- È importante che la scelta dei nomi diano **immediatamente** il significato di "*cosa contiene*"
- Per questo motivo si preferisce avere come nome di uno schema un nome al **plurale**
	- *Persona* -> *Persone*

>[!abstract] Istanza di Relazione $R(X)$
>Una ***istanza*** (o ***stato***/***estensione***) di *relazione* su $X$ è l'insieme $r$ di *tuple* su $X$
>- L'istanza di una Relazione definisce a livello [[Modello Entity-Relationship#Entità|estensionale]] una relazione

![[RelationTable.png]]
#### Tabelle
>Le tabelle sono formate da diverse parti e devono seguire alcune regole.

- ***Intestazione* della tabella**
	- **Schema della relazione** (nome tabella + attributi)
- **Colonne**
	- *Attributi*
- **Righe**
	- *Tuple* della relazione

>[!important] Regole
>- ***NON*** possono esistere *attributi uguali*.
>- ***NON*** possono esistere *righe uguali*.
>- I dati di una colonna **devono essere omogenei** (di un solo tipo).

### Data Base Relazionale
>[!example] Schema di un *DB*
>Lo ***schema*** di un *database* relazionale è un insieme di schemi di relazioni con nomi distinti.
>$$R=\{ R_{1}(X_{1}),R_{2}(X_{2}),\dots,R_{m}(X_{m}) \}$$

>[!abstract] Istanza di un *DB*
>Una ***istanza*** (o ***stato***/***estensione***) di un *database*: $R=\{ R_{1}(X_{1}),R_{2}(X_{2}),\dots,R_{m}(X_{m}) \}$ 
> è un insieme di ***istanze di relazioni***:
> $$r=\{ r_{1},r_{2},\dots,r_{n} \}$$
> con $r_{i}$ istanza di relazione su $R_{i}(X_{i})$

## Forme Normali

Le relazioni devono rispettare determinate proprietà matematiche per garantire coerenza e minimizzazione della ridondanza.
