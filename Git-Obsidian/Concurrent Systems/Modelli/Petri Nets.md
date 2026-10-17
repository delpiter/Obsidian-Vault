## Reti di Petri
---
>[!tl;dr] Definizione
> Le ***petri nets*** sono un modello formale *astratto* per descrivere il flusso dell'informazione.

Non modella secondo l'*interleaving*

> [!warning] Non determinismo
> Le ***reti di petri*** modellano comportamenti non deterministici.
> 

Una `PN` è vista come una sequenza di eventi discreti il cui ordine di esecuzione è uno dei possibili permessi dalla struttura.

### Il grafo
>[!info]
>Il [[../../Algoritmi e Strutture Dati/Strutture Dati/Grafi/I Grafi|grafo]] di una ***rete di petri*** è composto da $2$ tipi di *nodi*:
>- I ***places***, rappresentati dai *cerchi*.
>- Le ***transitions*** rappresentati da *barre*.

I *places* possono essere connessi **solo** con le *transition* e ***viceversa***.

Il grafo di una ***rete di petri*** modella le ***proprietà statiche*** di un sistema.

![[attachements/PetriNets.png]]
#### Token e Marking
> In aggiunta alle *proprietà statiche* rappresentate dal grafo, una *rete di Petri* ha delle proprietà dinamiche che sono il risultato dall'esecuzione.

>[!caution] Esecuzione
>L'esecuzione di una rete è controllata dalla posizione e movimento dei *marcher* chiamati ***token***

I **token** possono rappresentare molte cose.

>[!example] Regole di esecuzione

- I **token** sono rimossi eseguendo (*firing*) la *transizione* della rete.
- Una *transizione* deve essere **attiva** per essere eseguita.
- Una *transizione* è attiva quando **tutti i places in input** hanno un *token* al loro interno.
- Una *transizione* viene eseguita **rimuovendo i token** dai places in input e **generando nuovi token** depositati nell'output place della transizione.

Su un *arco* (da **place** a **transition**) si possono specificare dei *pesi* che indicano ***quanti token sono necessari*** per l'esecuzione.
- Una transizione $t$ è abilitata se ogni place $p$ in input di $t$ è marcata con almeno $w(p,t)$ token, dove $w(p,t)$ è il peso dell'arco da $p$ a $t$.
- Eseguire una transizione $t$ rimuove $w(p,t)$ token da ciascun place in input e aggiunge $w_{1}$ token ad ogni place in output $p$ di $t$, dove $w(t,p)$ è il peso dell'arco da $t$ a $p$.
	- Può *generare* o *rimuovere* token.

##### Transizioni ai bordi
>[!important] Source Transition

Senza un ***place*** in input, usato per *generare* i token.

> [!help] Sink Transition

Senza un ***place*** in output, usato per *consumare* token.

### Modellare con le Petri Net
>[!abstract]
>Le ***reti di Petri*** possono essere usate per modellare naturalmente sistemi concorrenti.

I sistemi vengono modellati in termini di:
- **Eventi** e **condizioni**.
- Le relazioni tra eventi e transizioni.

#### Interpretazioni
> Ci sono numerose ***possibili interpretazioni*** di places e transitions.

| Input Places      | Transition                          | Output Places      |
| ----------------- | ----------------------------------- | ------------------ |
| Pre-condizione    | Evento                              | Post-condizione    |
| Input Data        | Passo computazionale                | Output data        |
| Segnale in input  | Esecuzione del processo del segnale | Segnale di output  |
| Risorsa richiesta | Task o job                          | Risorsa rilasciata |
| Condizione        | Clausola nella logica               | Conclusione        |
| Buffer            | Processore                          | Buffer             |
#### Modellare la concorrenza e il parallelismo
> [!tldr] Idea
> Le ***reti di Petri*** sono ideali per modellare sistemi con controllo distribuito, con multipli processi eseguiti in maniera concorrente.

![[attachements/PetriNetSyncronization.png]]

- Il primo grafo modella ***due attività parallele***.
- Il secondo grafo modella *due attività parallele* ***con sincronizzazione***.

#### Modellare i conflitti
> [!fail] Conflitto
> Due eventi $e_{1}$ e $e_{2}$ sono in ***conflitto*** se solo uno dei due eventi possono accadere ma non entrambi.

> [!caution] Concorrenza
> Due eventi $e_{1}$ e $e_{2}$ sono ***concorrenti*** se entrambi gli eventi possono accadere in qualsiasi ordine *senza conflitti*.

Una situazione dove conflitti e concorrenza sono mischiati viene chiamata una ***confusione***.

