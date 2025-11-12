
![[UML#^8c36fe]]
## Diagrammi di Attività
---
I diagrammi di attività ***modellano un processo*** come un'attività costituita da un insieme di nodi connessi da archi.
- Possono essere usati per *modellare efficacemente* processi di business e workflow.


>[!hint]
>In [[UML]] 2 hanno una nuova semantica basata sulla ***rete di Petri***.
### Attività
>[!help] Activity
>Le ***attività*** sono modellate come redi di nodi connessi da *archi*.


>[!tip] Categorie di Nodi

> ***Nodi di azione***
- Rappresentano compiti atomici all'interno dell'attività.

> ***Nodi di controllo***
- Controllano il flusso all'interno dell'attività.

> ***Nodi di oggetto***
- Rappresentano oggetti usati nell'attività.

>[!summary] Categorie di Archi

> ***Flussi di Controllo***
- Rappresentano i flussi di controllo che attraversano l'attività.

> ***Flussi di Oggetti***
- Rappresentano il flusso di oggetti attraverso l'attività.

#### Nodi Azione
>[!todo] Tipologie

> Nodo azione ***di chiamata***
- Chiama un comportamento, un'attività o un'operazione.

> Nodo di azione ***di accettazione evento temporale***
- Produce un *evento temporale* ogni volta che la condizione temporale diventa vera.
- Diventa attivo **solo quando si attiva l'arco**.
- Rappresentato da un arco con una clessidra.

![[TemporalEvents.svg]]
#### Nodi di Controllo
>[!todo] Tipologie

> Nodo ***Iniziale***
- Indica l'inizio del flusso.

> Nodo ***Finale dell'Attività***
- Indica il termine di un'attività.

> Nodo ***Finale del Flusso***
- Indica il termine di uno specifico flusso.

![[StartEndNodes.svg]]

> Nodo ***Decisionale***
- Divide il flusso in più flussi alternativi.

> Nodo ***Fusione***
- Ricongiunge i flussi a valle di un nodo decisione.

![[DecisionalNode.svg]]

> Nodo ***Biforcazione*** (`fork`)
- Divide il flusso in in più flussi concorrenti.

> Nodo ***Ricongiunzione***
- Sincronizza flussi concorrenti.

![[ForkNode.svg]]
#### Nodi Oggetto
>[!info]
>I ***nodi oggetto*** indicano che sono disponibili istanze di una data classe in un *punto specifico dell'attività*.

Gli archi in entrata e uscita dai nodi oggetto rappresentano ***flussi di oggetti*** *creati* e *consumati* da nodi azione.
- È possibile rappresentare esplicitamente lo [[State Diagram|stato]] di un oggetto.

### Corsie
>[!definizione]
>Le attività possono essere partizionate in ***corsie*** che raggruppano *insiemi di azioni correlate*.

Le corsie possono corrispondere a:
- [[Use Case Diagram|Casi d'Uso]].
- [[Class Diagram|Classi]].
- Componenti.
- Unità organizzative.
- Ruoli.

La semantica di ogni insieme di corsie è descritta da una ***dimensione***.

![[Courses.svg]]
