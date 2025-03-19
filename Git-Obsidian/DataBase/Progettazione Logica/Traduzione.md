> Si mappano i costrutti residui in elementi del [[Modello Relazionale]]
## Traduzione Schema E/R
---
>Si crea la necessità di ***tradurre*** i costrutti del [[Modello Entity-Relationship|modello E/R]] in costrutti del modello *relazionale* per garantire l’equivalenza.

### Traduzione delle Entità
>[!tldr] Idea
>Ogni **entità** è *tradotta* con una **relazione** con gli stessi attributi.

La [[Vincoli di Integrità#Chiavi|chiave primaria]] coincide con l'identificatore principale dell'*entità*.

### Traduzione delle Associazioni
>[!tldr] Idea
>Ogni **associazione** è *tradotta* con una **relazione** con gli stessi attributi, a cui si aggiungono gli identificatori di ***tutte le entità che essa collega***.
>

Gli identificatori delle entità collegate costituiscono una [[Vincoli di Integrità#Superchiave|Superchiave]].
- Dipende dalle **cardinalità massime** delle entità nella *associazione*.
- Le **cardinalità minime** determinano la presenza o meno di [[Informazione Incompleta#Null|valori nulli]].

#### Traduzione di Relazioni $n$-arie Molti a Molti
>[!tldr] Idea
>La *relazione* diventa una **tabella** con la [[Vincoli di Integrità#Chiavi|chiave]] costruita dalle *chiavi delle entità coinvolte*, più gli attributi della relazione.

> Lo schema:

![[N_NRelationTraslation.png]]

Diventa:
- ***FORNITORI***(<u>PartitaIVA</u>, Nome)
- ***PRODOTTI***(<u>Codice</u>, Genere)
- ***DIPARTIMENTI***(<u>Nome</u>, Telefono)
- ***FORNITURE***(<u>Fornitore</u>, <u>Prodotto</u>, <u>Dipartimento</u>, Quantità)

### Traduzione di Relazioni Uno a Molti
>[!info] Possibilità
> Tradurre la relazione come una ***tabella separata*** (come nel caso *molti a molti*).
> <u>Oppure </u>
> **Inglobare** la relazione nell’*entità* con **cardinalità massima** $1$.

### Traduzione di relazioni uno a uno
>[!help] Possibilità diverse in base alla cardinalità minima

1. **Partecipazione obbligatoria per entrambe le entità:**
   - Si traduce *inglobando* la relazione in una delle due entità.
2. **Partecipazione obbligatoria per una sola entità:**
   - Si traduce *inglobando* la relazione nell’entità con *partecipazione obbligatoria*.
3. **Partecipazione facoltativa per entrambe le entità:**
   - Analogamente al caso **uno a molti**.

### Traduzione con identificatore esterno
>[!tldr] Idea
> Le entità con ***identificatore esterno*** si traducono in una *tabella* che include tra le [[Vincoli di Integrità#Chiavi|chiavi]] gli **identificatori** dell’entità esterna.

> Lo schema:

![[ForeignIdentifier.png]]

Diventerebbe:
- ***STUDENTI***(<u>Matricola</u>,<u>Università</u>, Cognome, Nome, AnnoDiCorso)
- ***UNIVERSITA***(<u>Nome</u>, Città, Indirizzo)

>[!caution] Precisazione
> È possibile avere ***identificazioni esterne in cascata***.
> Per operare correttamente occorre partire dalle entità **non identificate esternamente** e propagare gli identificatori.

