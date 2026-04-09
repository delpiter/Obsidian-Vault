## Alberi: Definizione
---
>[!info] Alberi
>Un *albero* è un [[../I Grafi#Grafo Definizione|grafo]] aciclico, con un numero di nodi uguale al numero di archi più uno.
>$$\left| E \right| = \left| V \right|-1  $$
>>[!done] Alternativa Equivalente
>
>Un albero è un grafo aciclico totalmente connesso
>Può esistere un nodo particolare chiamato *radice*
>- La radice **induce implicitamente** un *ordinamento parziale* fra i nodi

## Definizioni sugli Alberi
---
> Se c'è un nodo radice viene implicitamente definita una relazione di *ordinamento* fra nodi basata sulla *distanza dalla radice*.

### Elenco proprietà Alberi
- Ogni nodo non radice ha un unico ***predecessore/padre***
	- Unico arco *entrante*, che proviene dalla radice
- Un nodo può avere più ***successori/discendenti/figli***
- Un nodo senza successori è detto ***foglia***
- La ***profondità di un nodo*** è la lunghezza del cammino dalla radice al nodo
- L'***altezza di un nodo*** è la massima lunghezza del cammino dal nodo a una foglia discendente del nodo
- L'***altezza di un albero*** è l'altezza del nodo radice
- Un ***livello/strato*** di un albero consiste nell'insieme di tutti i nodi con la stessa *profondità*
- Il ***numero di livelli*** di un albero è pari alla sua *altezza* +1

>[!info] Arborescenza
>Una *arborescenza* è un albero in un grafo orientato
>L'orientamento deve essere sempre diretta verso i nodi foglia