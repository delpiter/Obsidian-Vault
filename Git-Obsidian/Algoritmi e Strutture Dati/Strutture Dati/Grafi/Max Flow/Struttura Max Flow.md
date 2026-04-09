## Definizioni
---
### Rete di Flusso
>[!info] Descrizione
>Una ***rete di flusso*** (*flow network*) è un grafo orientato pesato, $G=(V,A,c)$, con due nodi particolari:
>- Una ***sorgente*** $s$
>- Un ***pozzo*** o ***destinazione*** $t$
>
> $s$ e $t$ sono nodi "***attivi***" che rispettivamente ***generano*** e ***eliminano*** il flusso.
> Tutti gli altri nodi ***conservano il flusso***
>>[!tldr] Archi
>> Ogni arco $(u,v)\in A$ ha associato una ***capacità***, cioè un peso ***non negativo***, $c(u,v)\geq 0$

### Flusso Ammissibile
>[!info] Descrizione
>Un ***flusso ammissibile*** per $G$ è una funzione $f: E\to\mathbb{R}$ tale che:
>>[!abstract] Il ***vincolo di capacità*** è soddisfatto in ogni arco
>>$$0\leq f(u,v)\leq c(u,v)\qquad \quad \forall(u,v)\in E$$
>
>
>>[!tldr] Il ***flusso è conservato*** in ogni nodo interno
>>$$\sum_{v\in V}f(u,v)=\sum_{v\in V}f(v,u)\qquad \quad \forall u\in V\setminus\{s,t\}$$

![[attachements/FlowExample.png]]
*Un esempio di flusso*