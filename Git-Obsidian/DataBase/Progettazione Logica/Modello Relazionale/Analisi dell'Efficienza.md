>Per confrontare tra loro diverse alternative bisogna conoscere, almeno in maniera *approssimativa*, il ***carico di lavoro***.

È necessario conoscere:
- Le principali **operazioni** che la *base di dati* dovrà supportare.
- I ***volumi*** dei dati in gioco.

>[!help] Gli indicatori che derivano considerano due aspetti:
>***Spazio***
>- Numero di istanze *previste*.
>
>***Tempo***
>- Numero di istanze *visitate* durante un'operazione.

## Analisi delle Operazioni
---
> Prendiamo come riferimento il seguente [[Modello Entity-Relationship|schema]].

![[ExampleER.png]]

### Tavola dei Volumi
>[!def] Definizione
>La ***tavola dei volumi*** specifica il numero stimato di istanze per ogni entità $E$ e associazione $R$ dello schema.

I valori sono necessariamente **approssimati** ma **indicativi**.

| Concetto       | Costrutto | Volume |
| -------------- | --------- | ------ |
| Sede           | $E$       | $10$   |
| Dipartimento   | $E$       | $80$   |
| Impiegato      | $E$       | $2000$ |
| Progetto       | $E$       | $500$  |
| Composizione   | $A$       | $80$   |
| Afferenza      | $A$       | $1900$ |
| Direzione      | $A$       | $80$   |
| Partecipazione | $A$       | $6000$ |
### Descrizione delle Operazioni
L'*analisi delle operazioni* richiede la codifica di:
- **Tipo** dell'operazione.
- **Frequenza** dell'operazione.
- **Schema di navigazione** (frammento dello *schema E/R* evidenziando il *cammino logico*)

Per ogni operazione, si costruisce una ***tavola degli accessi***, basata sullo *schema di navigazione*, con i seguenti campi:
- **Costrutto**: Specifica il tipo di concetto.
- **Accessi**: Conta il numero degli accessi.
- **Tipo**: Riferito al tipo di operazione (*lettura*/*scrittura*).

Il costo degli ***accessi in scrittura*** è in generale considerato **doppio** rispetto a quello delle ***letture***.

>[!example] Esempio
>Visualizzare tutti i dati di un impiegato, del dipartimento nel quale lavora e dei progetti ai quali partecipa.

![[EfficiencyEstimate.png]]

*Valutazione di costo*

![[AccessTable.png]]

*Tavola degli Accessi*


| Concetto       | Costrutto | Accessi | Tipo    |
| -------------- | --------- | ------- | ------- |
| Impiegato      | $E$       | $1$     | Lettura |
| Afferenza      | $A$       | $1$     | Lettura |
| Dipartimento   | $E$       | $1$     | Lettura |
| Partecipazione | $A$       | $3$     | Lettura |
| Progetto       | $E$       | $3$     | Lettura |
#### Analisi delle Ridondanze
>[!info] Ridondanza
>Una ridondanza in uno [[Modello Entity-Relationship|schema E/R]] è un'informazione significativa ma ***derivabile da altre***.


>[!done] Pro:
- Operazioni sui dati spesso ***più efficienti***.

>[!fail] Contro
- Maggiore *occupazione di memoria*.
- Maggiore *complessità degli aggiornamenti*.

In questa fase si decide se *eliminare* o *meno* le ***ridondanze***.

Se si mantiene una *ridondanza*:
- Si **semplificano** alcune *interrogazioni*.
- Si **appesantiscono** gli aggiornamenti.
- Si **occupa** maggior spazio.

>[!summary] Possibili Ridondanze
>***Attributi Derivabili***
>- Attributi che si possono derivare da altri attributi.
>
>***Associazioni Derivabili***
>- Associazioni derivabili dalla composizione di altre associazioni.
>

![[RedundantAttribute.png]]

*Attributo Derivabile*

![[RedundantAssociation.png|300]]


>[!question] Mantenere la Ridondanza?

È importante considerare la ***frequenza delle operazioni***

*Solitamente*:
- Si decide di mantenere la *ridondanza* privilegiando l'**efficienza**.
- In generale si devono fare anche considerazioni sullo spazio in più richiesto.