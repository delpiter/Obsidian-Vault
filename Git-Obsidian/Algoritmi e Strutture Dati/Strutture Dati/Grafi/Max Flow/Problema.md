## Problema del Max Flow
---
>[!abstract] Problema
>Il problema del ***flusso massimo*** (*max flow*) chiede di determinare il valore del massimo flusso ammissibile inviabile da $s$ a $t$
>>[!example] Problema applicabile in ***tantissime situazioni***
>>- Liquidi nelle tubature
>>- Veicoli in reti stradali
>>- Materiali in reti logistiche
>>- Orari di personale
>>- etc...

Introduciamo ora alcune definizioni che ci serviranno per risolvere il problema
### Circolazioni
>[!info] Definizione
>Una [[Struttura Max Flow#Rete di Flusso|rete di flusso]] può diventare una ***rete di circolazione*** aggiungendo un arco $(t,s)$ con capacità infinita e richiedendo che il flusso $f(t,s)$ sia il più grande possibile

### Tagli
>[!info] Definizione
>Un ***taglio*** $(A,B)$ di una rete di flusso $G=(V,E)$ è una partizione di $V$ tale per cui $s \in A$ e $t\in B$
>>[!done] A parole
>>*Un taglio* è una partizione dei nodi di in modo di avere la *sorgente* e la *destinazione* in ***sottoinsiemi differenti***
>
>>[!tldr] Capacità
>>La ***capacità di un taglio***, $c(A,B)$ è pari alla somma delle capacità degli archi con il primo estremo in $A$ e il secondo estremo in $B$

![[attachements/Cut.png|500]]

### Legame Max Flow - Min Cut
>[!info] Lemma
>Il valore di qualunque flusso $f(A,B)$ è ***limitato superiormente*** dalla capacità di un qualunque taglio di $G$
>>[!example] Dimostrazione
>$f(A,B)$
>$$\sum_{u\in A}\sum_{v\in B}f(u,v)\leq \sum_{u\in A}\sum_{v\in B}c(u,v)=c(A,B)\qquad \forall(A,B)$$

>[!tldr] Teorema
>Il ***flusso massimo di una rete*** $G=(V,A)$ è pari alla capacità del taglio di $G$ di ***capacità minima***

![[attachements/Screenshot 2024-06-10 111745.png]]

### Grafo Residuo
>[!info] Definizione
>La capacità residua $c_{f}(u,v)$ di un arco $(u,v)\in A$ su cui circola un flusso $f(u,v)$ è pari a:
>$$c_{f}(u,v)=c(u,v)-f(u,v)\qquad c_{f}(u,v)>0$$
>Data una rete $G(V,A)$ su cui circola un flusso $f$ il ***grafo residuo*** $G_{f}(V,A_{f})$ è un sottografo di $G$ contenente solo gli archi di $A$ con ***capacità residua strettamente positiva***

>[!tldr] Taglio Nullo
>All'interno di un ***grafo residuo*** è possibile trovare un taglio di capacità nulla
>Un taglio di capacità nulla esiste quando ***non c'è nessun arco*** che va da $A$ a $B$, ovvero ***non ci sono cammini*** che collegano la sorgente $s$ e la destinazione $t$

### Cammino Aumentante
>[!info] Definizione
>Un ***cammino aumentante*** nella rete $G$ in cui circola un flusso $f$, *eventualmente nullo* è un cammino da $s$ a $t$ nel suo ***grafo residuo***
>È quindi possibile aumentare il flusso negli archi del cammino aumentante
>>[!abstract] Incremento Limite
>>Il flusso lungo un *cammino aumentante* può essere aumentato al massimo di un quantitativo pari alla ***minima capacità residua*** $c_{f}$ degli archi del cammino

![[attachements/Grafo Residuo.png|450]]
### Casi diversi del Problema
>*Poiché il problema ha una vasta applicazione nella realtà, possono esistere diversi casi dove ci si deve ricondurre al caso base prima di potere procedere con la risoluzione*

>[!example] Esempio
>>[!question] Ho più sorgenti e destinazioni?
>
>Collego tutte le sorgenti $s_{1},\dots,s_{t}$ ad una unica sorgente $S$ e analogamente collego tutte le destinazioni $t_{1},\dots,t_{n}$ ad una unica destinazione $T$

>[!example] Esempio
>>[!question] Ho la capacità sui nodi?
>
>Creo due nodi adiacenti e l'arco in mezzo prende la capacità del nodo che avevo prima

