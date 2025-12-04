#reti_2
## Algoritmi con Routing Table
---
### Store and Forward
>[!tldr] Idea
>Il pacchetto entrante è *verificato e memorizzato*, si estraggono le informazioni di instradamento dall'intestazione e si confrontano con le informazioni con la [[Routing#Tabella di Routing IP|routing table]].

Il pacchetto viene prima **memorizzato interamente** nel nodo e quindi ritrasmesso nella direzione opportuna.

### Shortest Path Routing
>[!tldr] Idea
>Si assume che ad ogni collegamento della rete possa essere attribuita una ***lunghezza***, l'algoritmo cerca la strada di lunghezza minima fra ogni mittente e destinatario.

La lunghezza è un numero che serve a caratterizzare il *peso del collegamento* nel determinare la ***funzione di costo del percorso*** totale di trasmissione.

Vengono applicati algoritmi di calcolo dello shortest path.
- [[Algoritmo di Dijkstra]].
- [[Algoritmo di Bellman-Ford]].

> L'implementazione può avvenire in modalità:
- ***Centralizzata***
	- Un solo nodo esegue i calcoli.
- ***Distribuita***
	- Ogni nodo esegue i calcoli per se.
	- *Sincrona*: I nodi eseguono gli stessi passi dell'algoritmo nello **stesso istante**.
	- *Asincrona*: I nodi eseguono gli stessi passi dell'algoritmo **istanti diversi**.

#### Riempimento della Routing Table
>Per implementare l'algoritmo verso una qualunque destinazione si devono usare:

>[!summary] Protocolli
>Dei ***protocolli di routing*** per scambiarsi informazioni e apprendere la [[Topologie di Rete|topologia]] della rete.

>[!todo] Algoritmi
>Degli ***algoritmi*** per il calcolo dei **shortest path** sulla base delle informazioni ottenute.

##### Routing Distance Vector
> Algoritmo Basato su [[Algoritmo di Bellman-Ford|Bellman-Ford]] in versione dinamica e distribuita proposta da [[Ford-Fulkersron]].

>[!tldr] Idea
> Implementa meccanismi di dialogo per:
> - Far ***scoprire ad ogni nodo i suoi vicini*** e ne calcola la distanza da se stesso.

Ad ogni passo, ogni nodo invia ai propri vicini un ***vettore*** contenente la stima della sua distanza da tutti gli altri nodi della rete.

>[!note] Cold Start e Tempo di Convergenza

1. Allo start-up le tabelle dei nodi contengono l'indicazione delle ***distanze dei vicini***.
2. Si *scambiano i distance vector* per la creazione di ***tabelle più complete***.

L'algoritmo ***converge*** al più dopo un numero di passi pari al *numero di nodi* della rete.
- Se la rete è grande può essere molto lungo il tempo di convergenza.

#### Bouncing Effect
>[!fail] Il link tra due nodi `A` e `B` cade

`A` e `B` impostano *immediatamente* la loro distanza a $\infty$.
- Se altri nodi hanno inviato i loro vettori delle distanze, si possono verificare delle **incongruenze temporanee**.

Queste incongruenze ***possono dare luogo a cicli***.

#### Counting to Infinity
> Situazione Iniziale: $D_{ab}=1, D_{bc}=1, D_{ac}=2$

Se il link `BC` salta:
- `B` riceve il ***distance vector*** di `A` che contiene l'informazione $D_{ac}=2$
	- Calcola una nuova distanza: $D'_{bc}=D_{ba}+D_{ac}=3$.
- `B` comunica ad `A` la sua nuova distanza da `C`.
	- Calcola la nuova distanza: $D'_{ac}=D_{ab}+D'_{bc}=4$.
- ...

>[!fail] La cosa può andare all'infinito
- Si può interrompere imponendo che una distanza non può assumere un valore $>D_{\max}$

>[!done] Meccanismi Migliorativi

Tecnica per ***migliorare i tempi di convergenza***.

> ***Split Horizon***
- Se `A` instrada pacchetti verso `X` tramite `B`, non ha senso per `B` cercare di raggiungere `X` tramite `A`.
- Non ha senso che `A` renda nota a `B` la sua distanza da `X`.

*Forma Semplice*:
- `A` omette la sua distanza da `X` nel ***distance vector*** che invia a `B`.

*Poisonous Reverse*:
- `A` inserisce tutte le destinazioni nel ***distance vector*** diretto a `B`, ma pone la distanza da `X` uguale ad infinito.

> ***Triggered Update***
- Un nodo *deve inviare immediatamente* le informazioni a **tutti i vicini** qualora si verifichi una modifica della propria tabella di instradamento.

#### Routing Link State
> Protocollo con il quale ogni nodo si costruisce un'***immagine del grafo della rete***.

>[!todo] Raccolta delle informazioni

1. Ogni router comunica con i propri vicini per ***imparare i loro indirizzi*** (`hello packet`).
2. Ogni router misura la ***distanza dai vicini*** (`echo packet`).
3. Ogni router costruisce un pacchetto con lo stato delle linee (***Link State Packet***) che contiene:
	- Lista dei vicini e le lunghezze dei collegamenti per raggiungerli.

>[!caution] Diffusione delle informazioni

1. I pacchetti `LSP` vengono trasmessi da tutti i [[Routing#Router|router]] a tutti i router.
	- Step che utilizza il [[Senza Routing Table#Flooding|flooding]].
2. Una volta ricevuti tutti gli `LSP` ogni router riesce a costruire l'*immagine della rete*.
3. Ogni router calcola i cammini minimi tramite l'[[Algoritmo di Dijkstra]].