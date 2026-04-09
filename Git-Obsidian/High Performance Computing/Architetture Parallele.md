> A differenza della programmazione sequenziale, dove esiste un modello astratto di [[../Architettura degli Elaboratori/Architettura del Calcolatore/Organizzazione del Calcolatore|architettura sequenziale]], nel caso delle architetture parallele, questa ***astrazione non esiste***.

>[!question] Come è gestito il parallelismo?

Non ci sono computer paralleli "*tipici*".
- Ogni venditore, usa ***architetture diverse***.

>[!warning] Non esiste un paradigma universale
>I programmi paralleli devono essere ***fatti apposta*** in base all'architettura utilizzata nel calcolatore.

>[!hint] Performance Portability
> È l'idea di riuscire a scrivere un ***programma parallelo una volta sola*** in maniera sufficientemente *astratta* e poi avere più compilatori che lo adatta in base all'architettura. 

## Architettura di Von Neumann
---
![[../Architettura degli Elaboratori/Architettura del Calcolatore/Organizzazione del Calcolatore]]

### Tempi di CPU comparati con il Mondo Reale

| Action               | `CPU`         | Real World     |
| -------------------- | ------------- | -------------- |
| 1 `CPU` cycle        | $0.3ns$       | $1s$           |
| Level 1 cache access | $0.9ns$       | $3s$           |
| Level 2 cache access | $2.8ns$       | $9s$           |
| Level 3 cache access | $12.9ns$      | $43s$          |
| Main memory access   | $120ns$       | $6min$         |
| Solid State disk I/O | $50-150\mu s$ | $2-6\ days$    |
| Rotational disk I/O  | $1-10ms$      | $1-12\ months$ |
>[!fail] Ci sono grandi problemi di ***bottleneck***

> ***Soluzioni possibili***:

- *Riduzione della latenza* per gli accessi in memoria.
	- Utilizzo di cache e registri di `CPU` quando possibile.
- *Nascondi la latenza* .
	- Tramite multithreading e [[../Sistemi Operativi/Teoria/6 - Processi, Schedule e Thread#Mode Switching e Context Switching|context-switch]] durante gli accessi in memoria.
- *Esegui multiple istruzioni* allo stesso tempo.
	- [[../Architettura degli Elaboratori/Architetture a Confronto/Pipelining]]
	- [[../Architettura degli Elaboratori/Architetture a Confronto/Predizione di Salto|Branch Prediction]]
	- [[../Architettura degli Elaboratori/Architetture a Confronto/Predizione di Salto#Esecuzione Speculativa|Speculative Execution]]
	- `SIMD` extensions.

>[!check] Rules of Thumb
>- **Computation is Fast**
>- **Communication is Slow**
>- ***Input/Output is incredibly Slow***
#### Cache
> Memoria di piccole dimensioni usata per "*abbattere*" il muro di performance tra il processore e la memoria.

![[../Architettura degli Elaboratori/Architettura del Calcolatore/Cache]]

##### Esempio
>[!fail] Prodotto Matrice $\times$ Matrice

```c title:"Matrix Product"
void matmul( double *p, double* q, double *r, int n) 
{ 
	int i, j, k;
	for (i=0; i<n; i++)
	{
		for(j=0;j<n;j++)
		{
			double s = 0.0;
			for (k=0;k<n;k++) {s+=p[i*n*+k] * q[k*n+j]; }
			r[i*n+j] = s;
		}
	}
}
```

> Analizziamo il seguente codice.
- Le matrici in `{c icon}‎ ` sono memorizzate in ordine ***row-majior***
	- Gli elementi di ciascuna riga sono salvati in ***aree contigue di memoria***.
	- *Righe adiacenti* sono blocchi contigui di memoria.

![[attachements/RowMajorOrder.png]]

Accedere la memoria in modalità ***row-wise*** è efficiente in quanto i dati sono in una *area contigua di memoria*.
- La **cache** aumenta le performance ([[../Architettura degli Elaboratori/Architettura del Calcolatore/Cache#Principi della Cache|Spartial Locality]]).

![[attachements/Row_Wise_Access.png]]


Nel caso di accesso ***column-wise***, gli elementi non sono contenuti in blocchi contigui.
- La cache **non ha effetto**.

![[attachements/Column_Wise_Access.png]]

> Per ottimizzare gli accessi in memoria è possibile calcolare la ***matrice trasposta*** della seconda matrice del prodotto.
- In maniera tale da fare accesso alla memoria con soli blocchi contigui.

## Hardware Multithreading
---
>[!tldr] Idea
>Il ***multithreading a livello hardware*** permette alla [[../Architettura degli Elaboratori/Architettura del Calcolatore/La CPU|CPU]] di cambiare *task* quando quello corrente è in una *situazione di stallo*.

*Tipologie*:
> ***Fine-Grained Multithreading***:
- Il **context-switch** avviene a costo zero (*performance*).
- La `CPU` cambia il *task* anche per brevi stalli come una operazione in memoria.

> ***Coarse-Grained Multithreading***:
- Il ***context-switch*** ha un costo non trascurabile.
- Appropriato per l'attesa di operazioni di *I/O*.

>[!hint] SMT
>Il ***Simultaneous Multithreading*** è una implementazione del ***fine-grained multithreading*** che concede a due flussi di esecuzione di utilizzare le stesse risorse hardware per migliorare l'efficienza.

L'[**Hyperthreading**](https://www.intel.com/content/www/us/en/gaming/resources/hyper-threading.html) è l'implementazione di ***Intel*** dell'`SMT`.
- Gli stadi della *pipeline* sono **separati da due buffer**, uno per ciascun thread.
- Se un thread è bloccato, l'altro riempie lo slot della *pipeline*, migliorando l'utilizzazione del processore.

## Architetture Parallele
---
![[../Architettura degli Elaboratori/Architetture a Confronto/Architetture Parallele#Classificazione di sistemi Paralleli]]

### Architetture MIMD

>[!caution] Sistemi a Memoria Condivisa

![[../Architettura degli Elaboratori/Architetture a Confronto/Architetture Parallele#Multiprocessori]]

>[!abstract] Sistemi a Memoria Distribuita

![[../Architettura degli Elaboratori/Architetture a Confronto/Architetture Parallele#Multicomputer]]

#### Architetture Ibride
> Molti ***High Performance Computers***, sono basati su una architettura *ibrida*.
- Ogni nodo è un computer con *architettura a memoria condivisa*.
- I nodi sono connessi tramite una *rete di interconnessioni*.

![[attachements/HybridArchitecture.png]]

#### Pro e Contro
> ***Architettura a Memoria Condivisa***.

>[!done] Pro
- Più *facili* da programmare
- Utili per applicazioni con ***accessi irregolari ai dati***.

>[!fail] Contro
- Il programmatore deve tenere conto delle [[../Sistemi Operativi/Teoria/8 - Concorrenza#Race Condition|race conditions]].
- Memory Bandwidth *limitata*.

> ***Architettura a Memoria Distribuita***.

>[!done] Pro
- ***Altamente scalabile***, basta aggiungere più nodi.
- Utile per applicazioni con un alto ***Computation/Communication*** *rate*.

>[!fail] Contro
- I programmatori devono tenere conto dei [[../Sistemi Operativi/Teoria/9 - Condivisione di Risorse#Deadlock|deadlock]].
- **Latenza** nella rete di interconnessione.
- *Difficili* da programmare.