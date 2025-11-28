>[!info]
>La ***fase di verifica*** ha lo scopo di controllare se il sistema realizzato risponde alle specifiche di progetto.

La verifica non coinvolge solo il prodotto finale ma segue passo passo il progetto e lo sviluppo.

> Le tecniche di verifica del **software** possono essere classificate come:
- Dinamiche o di Testing
- Statiche o di Analisi

## Verifica Dinamica
---
>[!tldr] Idea
>Nella ***verifica dinamica del software***, si mette in esecuzione il software per il controllo del corretto funzionamento.

Basato su prove sperimentali che ne verificano il comportamento in un ***insieme rappresentativo di situazioni***.

### Testing
>[!quote] Testing
>Le operazioni di testing possono individuare la presenza di errori nel software ma ***non possono dimostrarne la correttezza***.
>- [[Algoritmo di Dijkstra|Dijkstra 1972]].

Lo ***scopo del testing*** è quello di verificare il comportamento del sistema in un insieme di casi sufficientemente ampio da rendere plausibile che il suo comportamento sia analogo anche nelle restanti situazioni.

> Data l'impossibilità pratica di verificare tutte le possibili circostanze:
- Occorre individuare dei criteri per la ***selezione dei casi significativi***.

>[!todo] Creazione dei Test
>I test dovrebbero essere fatti da ***utenti esterni*** a quelli che hanno scritto il codice.
#### Testing in the Small
>[!info]
>La tecnica di "***testing in the small***" è una tecnica [[Definizioni_Ingegneria-del-Software#White-Box|white-box]], valuta il corretto funzionamento di una porzione di codice analizzando in modo approfondito il suo comportamento in relazione all'input.

##### Grafi di Controllo
![[ControlGraph.png]]

##### Criteri di Copertura
> Guardando il [[I Grafi|grafo]] di controllo del codice analizzato, uso i ***criteri di copertura*** per eseguire una ***serie di test***.

Esistono una serie di criteri, sempre più stringenti:
- *Statement Test* $\subseteq$ *Branch Test* $\subseteq$ *Decision Test*

>[!hint] Complessità
>Più si complicano i criteri, *più sono difficili* da trovare gli **insiemi di input** per i test.
###### Statement Test
>[!quote] Criterio di Copertura delle Istruzioni
>Selezionare un insieme di test $T$ tali che, a seguito dell'esecuzione del programma $P$ su tutti i casi di $T$, ***ogni istruzione elementare*** viene eseguita *almeno una volta*.

>[!warning] Non assicura la correttezza del codice

```c title:example
read(x);
read(y);
if(x!=0)
	x = x + 10;
y = y / x;

// the test {(x=20,y=30)} satisfies the statement test but does not spot the bug
```

> Guardando il grafo di controllo:
- Voglio "*visitare*" tutti i nodi.
###### Branch Test
>[!quote] Criterio di Copertura delle Decisioni
>Selezionare un insieme di test $T$ tale che, a seguito dell'esecuzione del programma $P$ su tutti i casi di $T$, ***ogni arco del grafo di controllo*** di $P$ sia attraversato *almeno una volta*.

Il criterio richiede che per ogni condizione presente nel codice, sia utilizzato un test che produca il risultato `true` e uno che produca `false`.

>[!warning] Non assicura la correttezza del codice

> Guardando il grafo di controllo:
- Voglio "*visitare*" tutti gli archi.

###### Decision Test
>[!quote] Criterio di Copertura delle Decisioni e delle Condizioni
>Selezionare un insieme di test $T$ tale che, a seguito dell'esecuzione del programma $P$ su tutti i casi di $T$, **ogni arco del grafo di controllo** di $P$ sia attraversato e **tutti i possibili valori** delle *condizioni composte* siano valutati *almeno una volta*.

Il criterio richiede che per ***ogni porzione di condizione composta*** presente nel codice, sia utilizzato un test che produca il risultato `true` e uno che produca il risultato `false`.

#### Testing in the Large
>[!info]
>La tecnica di "***testing in the large***" è una tecnica [[Definizioni_Ingegneria-del-Software#Black-Box|black-box]], valuta il corretto funzionamento del sistema sulla base delle corrispondenze *input-output*.

L'insieme di test da utilizzare viene selezionato sulla base delle specifiche di progetto che permettono di definire i diversi valori di input e i corrispondenti valori di output.
- Molto legato allo [[State Diagram]].

##### Tipi di Test
>[!tip] Test di Modulo
>Verifica se un ***modulo*** è stato implementato correttamente in base al suo *comportamento esterno*.

>[!caution] Test di Integrazione
>Verifica il comportamento di sottoparti del sistema  sulla base del loro *comportamento esterno*.

Solitamente svolto ***simulando il comportamento dei moduli*** che producono l'input del sottosistema in analisi.

>[!help] Test di Sistema
>Verifica il ***comportamento dell'intero sistema*** sulla base del suo comportamento esterno.


## Verifica Statica
---
### Analisi del Software
>[!definizione]
>Analizzare un software significa *ispezionare il codice* per capirne le caratteristiche e le funzionalità.

Può essere effettuata sul codice o su pseudocodice.

I due principali approcci all'analisi del software sono:
- Code inspection.
- Code Walk-through.

#### Code WalkThrough
>[!info]
>Il ***Code WalkThrough*** è un tipo di analisi informale eseguita da un team di persone che, dopo aver selezionato alcune porzioni di codice e opportuni valori di input, ***ne simulano il comportamento***.

- Il numero di persone coinvolte *deve essere ridotto* ($3-5$).
- Il progettista deve fornire in anticipo la **documentazione scritta del codice**.
- L'analisi non deve durare più di **alcune ore**.
- L'analisi deve essere indirizzata **solo** alla *ricerca dei problemi* e non alla soluzione.

#### Code Inspection
>[!info]
>L'analisi eseguita da un team di persone organizzata come nel caso del [[#Code WalkThrough]], mira a ricercare ***classi specifiche di errori***.

Si controlla solo la presenza di una particolare categoria di errore.
- Uso di variabili **non inizializzate**.
- **Loop infiniti**.
- Letture di dati **non allocati**.
- **Deallocazioni improprie** di memoria.

##### Analisi del Flusso dei Dati
> Si lavora su una variabile alla volta

>[!tldr] Idea
>Si vuole trovare l'***uso improprio di variabili***.
>Si analizza l'*evoluzione del valore associato alle variabili* durante l'esecuzione di un programma.

Ad ogni comando è possibile *associare staticamente* il tipo di operazioni eseguite sulle variabili:
- Definizioni: `d`.
- Usi: `u`.
- Annullamenti: `a`.

> Sequenze di comandi, corrispondenti a possibili esecuzioni, sono riducibili staticamente a **sequenze di tali operazioni**.

```c title:example
void swap(int *x1, int *x2)
{
	int *x;
	x2 = x;
	x2 = x1;
	x1 = x;
}
```

Per la variabile `x` la sequenza può essere ridotta a:
- `auu`.
Per la variabile `x1` la sequenza può essere ridotta a:
- `dud`.
Per la variabile `x2` la sequenza può essere ridotta a:
- `ddd`.

>[!attention] Rilevazione di Anomalie

- Ogni sequenza contenente un uso (`u`) non preceduto da una definizione (`d`) senza annullamenti (`a`) intermedi è ***sintomo di una possibile anomalia***.
- Ogni sequenza contenente ***due definizioni consecutive*** è sintomo di possibile anomalia.

> Regole Generali
- L'**uso** di una variabile deve essere **sempre preceduto** in ogni sequenza da una **definizione** della stessa, **senza annullamenti intermedi**.
- Una **definizione** di una variabile deve essere **sempre seguita** da un **uso** della variabile, **prima** di un'altra **definizione** o **annullamento**.