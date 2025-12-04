#reti_2
## Algoritmi e Protocolli
---
> La scelta del percorso spesso significa la **scelta del prossimo router**.

>[!info] Algoritmo di Instradamento
>Un ***algoritmo di instradamento*** è una metodologia di scelta del ***next hop***.

> Ha obbiettivi di *ottimalità*:
- **Semplicità**: In termini di [[Complessità di Algoritmi|complessità computazionale]].
- **Robustezza**.
- **Stabilità**.
- **Efficienza**.

I nodi di commutazione (*router*) per applicare l'algoritmo possono usare informazioni predisposte localmente sotto forma di ***tabelle***.

> Un algoritmo può o meno fare uso delle *routing table*.
- [[Senza Routing Table]].
- [[Con Routing Table]].
### Dinamicità
>[!caution] Routing Statico
>I percorsi sono decisi in momenti specifici e **non cambiano sul breve periodo**.

>[!tip] Routing Dinamico
>I percorsi vengono ***modificati periodicamente*** per adattarsi velocemente ad eventuali cambiamenti della rete.
