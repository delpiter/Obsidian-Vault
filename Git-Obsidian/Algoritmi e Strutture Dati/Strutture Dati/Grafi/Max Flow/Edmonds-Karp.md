## Algoritmo di Edmonds-Karp
---
>[!info] Algoritmo
>L'algoritmo di ***Edmonds-Karp*** è un algoritmo che risolve il problema dei [[Problema|flussi massimi]]
>A differenza dell'algoritmo di [[Ford-Fulkersron]], questo algoritmo aggiunge una ***forte condizione*** nella scelta del [[Problema#Cammino Aumentante|cammino aumentante]]
>>[!tldr] Concetto
>>1. *Set* $f(u,v)=0\qquad \forall(u,v)\in A$
>>2. $P=BFS(G_{f})$
>>3. *Aumenta il flusso su* $P$ *e aggiorna* $G_{f}$
>>4. *Ripeti 2-4 finché possibile*
>
>>[!done] In breve
>>Il flusso aumentante non è più scelto in modo "*casuale*" ma viene preso sempre un cammino aumentante con il numero minimo di archi, lo si può sempre trovare tramite [[../Algoritmi di Ricerca su Grafo#Breadth First Search|Breadth First Search]]

### Complessità
>[!abstract] Lemma
>Se *Edmonds-Karp* è applicato ad una rete $G=(V,E)$ con sorgente $s$ e destinazione $t$, allora *per tutti i vertici*  $v\in V$ ([[../Algoritmi di Ricerca su Grafo#Breadth First Search]]) ***cresce monotonicamante*** ad ogni aumento di flusso.

>[!Teorema]
>Se *Edmonds-Karp* è applicato ad una rete $G=(V,E)$ con sorgente $s$ e destinazione $t$, allora il ***numero totale di aumenti di flusso*** effettuati dall'algoritmo è:
>$$O(VE)$$

Dato che una [[../Algoritmi di Ricerca su Grafo#Breadth First Search|BFS]] può essere implementata con complessità $O(E)$, la complessità dell'algoritmo è complessivamente:
$$O(VE \cdot E)=O(VE^2)$$