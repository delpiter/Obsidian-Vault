#reti_2
## Algoritmi Senza Routing Table
---
### Flooding
>[!tldr] Idea
> Ogni nodo ***ritrasmette su tutte le porte di uscita*** del [[Routing#Router|nodo]] ogni pacchetto ricevuto.

Prima o poi il pacchetto viene *ricevuto da tutti i nodi* della rete e quindi anche a quello a cui è effettivamente destinato.
- Il primo pacchetto che arriva a destinazione ha fatto la ***strada più breve possibile***.

La complessità associata è *pressoché nulla*.
- Unico overhead è controllare se il pacchetto è ***stato già trasmesso***.

### Random
>[!question] Idea
>Il ***next hop*** viene scelto a caso fra quelli possibili.

>[!danger] Problemi

**Non garantisce la consegna** in tempi certi.

### Deflection Routing
>[!caution] Hot Potato
>Quando un nodo riceve un pacchetto lo ***ritrasmette sulla linea d'uscita con il minor numero di pacchetti in attesa*** di essere trasmessi.

> Adatto a reti in cui:
- I nodi dispongono di *spazio di memorizzazione limitato*.
- Si vuole minimizzare il tempo di permanenza di un pacchetto nei nodi.
 
>[!danger] Problemi
- I pacchetti possono essere ricevuti fuori sequenza.
- I pacchetti potrebbero percorrere all'**infinito** un certo **ciclo**.