>[!definizione] Definizione
>La ***topologia di*** [[Git-Obsidian/Reti/Introduzione/Introduzione|rete]] è il modello geometrico finalizzato a rappresentare le *relazioni di connettività*.

È possibile descrivere una rete utilizzando un [[I Grafi|grafo]] 

***Componenti***:
- ***Rami*** (*archi*): **Linee di collegamento** fra due nodi della rete
- ***Nodi***: Punti che si trovano agli estremi dei collegamenti.

## Topologie
---
### Topologia a Bus
>[!info] Definizione
>Nella ***topologia a bus*** tutti nodi sono *collegati* tra di loro per mezzo di un **unico ramo condiviso**

![[BusTopology.png]]


>[!fail] Contro

- Poco resistente ai guasti

### Topologia ad Anello
>[!definizione] Definizione
>Una ***topologia ad anello*** è una topologia lineare di tipo *chiuso*, in cui a **tutti i nodi** fanno capo due rami.
>


![[RingTopology.png]]

***Anelli Monodirezionali***:
- L'informazione si propaga solamente in ***una direzione***
- Se un collegamento si *interrompe* la rete si guasta.

***Anelli Bidirezionali***:
- L'informazione può essere trasmessa in ***ambedue le direzioni***
- Maggiore *complessità* di gestione.
- Maggiore *resistenza ai guasti*

### Topologia ad Stella
>[!summary] Definizione
> Le ***reti a stella*** sono le più comuni topologie.
> Consiste in un *centro stella* a cui ogni nodo è collegato, che ha il compito di smistare le informazioni.

>[!tip] Proprietà

- **Costo basso** di creazione
- **Minimizza** i collegamenti
- **Bassa** resistenza ai *guasti*

![[StarTopology.png]]

### Topologia a Maglia
>[!definizione] Definizione
>Nella ***topologia a maglia completa*** (***fully connected***) ogni nodo è *connesso direttamente* ad ogni altro nodo.
>È presente un collegamento per **ogni coppia di nodi**

$n$ nodi implicano: $\displaystyle{\frac{n(n-1)}{2}}$ collegamenti.

>[!hint] Proprietà

- **Grande** resistenza ai *guasti*
- **Alta** *complessità* e costi
- **Massimizza** i collegamenti

>[!tldr] Mesh
>La ***mesh*** è una *topologia* a ***maglia parzialmente connessa*** dove, dati $n$ nodi, utilizza solo un **sottoinsieme di tutti i collegamenti** diretti definibili tra i nodi

$n$ nodi implicano: $(n-1)<R< \displaystyle\frac{n(n-1)}{2}$

>[!done] Pro

- Costi *inferiori* di installazione e mantenimento

>[!fail] Contro

- Minore *fault tollerance*

![[Mesh.png]]
## Rete Gerarchica
---
>[!info]
> Una ***rete gerarchica*** è una rete *organizzata su più livelli*
> I **terminali** sono connessi ai **nodi periferici**.
> I *nodi periferici* sono connessi tramite **nodi intermedi**

Consente una *interconnessione a lunga distanza* con **nodi di transito** tipicamente interconnessi a ***maglia completa***