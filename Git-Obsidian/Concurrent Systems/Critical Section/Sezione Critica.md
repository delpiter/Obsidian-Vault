## Il problema della sezione critica
---
> Introdotto inizialmente da [[../../Algoritmi e Strutture Dati/Strutture Dati/Grafi/Cammini Minimi/Algoritmo di Dijkstra|Dijkstra]] nel $1965$.

Il problema della sezione critica può essere considerato uno dei problemi della programmazione concorrente più importanti e più studiati. 

> [!cite] Definizione
> $N$ processi, ciascuno esegue in un loop infinito una sequenza di istruzioni che possono essere divisi in due sottosezioni:
> - La ***sezione critica*** (`CS`)
> - e la ***sezione non critica*** (`NCS`)

```
P[1..n]:
loop {
	<non-critical section>
	entry protocol
	<critical section>
	exit protocol
	<non-critical section>
}
```

I protocolli garantiscono rispettivamente:
- Che un processo prima o poi entrerà nella sezione critica
- Che il processo dentro la sezione critica esca.

Ogni sezione critica tipicamente è una sequenza di statement che possono accedere ad un oggetto condiviso.

#### Requisiti
>[!abstract] In una ***Critical Section*** devono valere le seguenti proprietà: 

1. [[../../Sistemi Operativi/Teoria/9 - Condivisione di Risorse#Mutua Esclusione|Mutua Esclusione]]
	- Solo *un processo alla volta* deve essere all'interno della ***critical section***
2. Assenza di [[../Concorrenza nei sistemi#Deadlock|deadlock]]
	- Uno scenario dove tutti i processi **rimangono bloccati** definitivamente *non è ammissibile*
	- Se alcuni processi stanno cercando di entrare la sezione critica, uno deve prima o poi riuscirci. 
3. Assenza di ***delay*** non necessari
	- Un *processo* appena uscito dalla ***critical section*** non deve ritardare l'ingresso nella ***critical section*** da parte di un *altro processo*
4. ***Eventual Entry*** (Assenza di [[../Concorrenza nei sistemi#Starvation|starvation]])
	- Ogni processo che lo richiede, prima o poi entra nella ***critical section***

Una qualsiasi soluzione deve soddisfare la [[Modelli/Finite State Processes#Check delle proprietà del sistema|progress property]] per la sezione critica.
- Una volta iniziata l'esecuzione di una sezione critica deve prima o poi finire.

La sezione non critica *non deve necessariamente soddisfare questa proprietà*.

### Soluzioni: algoritmi vs meccanismi
>[!caution] [[Soluzioni Hardware|Meccanismi]]
> Il problema della sezione critica può essere risolto usando ***meccanismi basici*** come i semafori o i lock che devono essere forniti dalla macchina concorrente.

> [!tl;dr] [[Soluzioni Software|Algoritmi]]
> Il problema può essere risolto anche attraverso algoritmi  specifici, senza l'utilizzo di meccanismi hardware.