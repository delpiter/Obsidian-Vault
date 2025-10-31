>[!tip] Pattern
>Il è un [[Parallel Programming Patterns|pattern]] ***partition*** consiste nel dividere il *dominio dei dati* in regioni solitamente 
>[[Insiemi Numerici#Insiemi Separati|disgiunte]] (potrebbe essere necessario avere insiemi **non disgiunti**) chiamate ***partizioni*** (*partition*).

Ogni *processore* opera su una singola partizione.

Questo pattern è particolarmente utile quanto l'applicazione esibisce la "***locality of reference***":
- Quando i processori necessitano di poca o nessuna comunicazione con gli altri e utilizzano solo i *dati locali*.

## Modalità di Partizionamento
---
### In base al Tipo
>[!tip] Regolare
>Nel ***partizionamento regolare*** il dominio è diviso in partizioni più o meno della *stessa dimensione e forma*.

>[!note] Irregolare
>Le partizioni **non** sono necessariamente della ***stessa dimensione o forma***.

### In base alla Dimensione
>[!summary] Fine Grained
>Il dominio è diviso in ***tante piccole partizioni***.

>[!todo] Coarse Grained
>Il dominio è diviso in ***alcune grandi partizioni***.

#### Differenze
> ***Fine-Grained***
- Miglior ***bilanciamento del carico***, soprattutto se combinato con il pattern  [[#Master-Worker Paradigm|Master-Worker]].
- Se la granularità è *troppo fine*, la computazione potrebbe diventare lenta.

> ***Coarse-Grained***
- Generalmente migliora il rapporto *computazione*$/$*comunicazione*.
- Potrebbe causare sbilanciamento del carico.

>[!todo] Dimensione della Partizione
>La granularità "***ottimale***" dipende, a volte, dal problema analizzato.
>In altri casi l'utente deve scegliere la *granularità*.

La ***dimensione ottimale*** del partizionamento dipende generalmente dal sistema e dall'applicazione.
- Viene stimata tramite misurazioni e test.

>[!missing] Partizionamento Troppo Fine
- ***Alto overhead*** dello scheduling.

>[!danger] Partizionamento Troppo Grande
- ***Workload sbilanciato***.
### Esempi
#### Partizionamento a una Dimensione
> A blocchi

![[UnidimentionalBlockPartition.png]]

> Ciclico

![[UnidimentionalCyclicPartition.png]]

#### Partizionamento Bidimensionale
> A blocchi *orizzontali*.

![[BidimensionalHBlockPartitioning.png]]

> A blocchi *verticali*.

![[BidimensionalVBlockPartition.png]]

> Partizionamento *blocco, blocco*
![[Block-BlockPartitioning.png]]

> Ciclici

![[BidimensionalCyclicPartition.png]]

![[Cyclic-CyclicPartition.png]]

##### Esempio: Mandelbrot Set
>[!definizione]
>Il ***Mandelbrot Set*** è l'insieme di punti $c$ nel piano dei [[Numeri Complessi]] tale che la sequenza $z_{n}(c)$ definita come:
>$$z_{n}(c)=\begin{cases} 0\qquad \qquad \ \ \ \text{ if } n=0\\ z_{n-1}^{2}(c)+c \ \text{ Otherwise} \end{cases}$$
>Non *diverge* quando $n\to +\infty$.

[Mandelbrot Set](https://mandel.gart.nz/)

Se $\mid z_{n}(c)\mid$ non eccede $2$ dopo `maxit` iterazioni ($\approx 1000$), il `pixel` viene disegnato **nero**.
- Si assume che il punto *faccia parte dell'insieme*.

Altrimenti il colore dipende dal *numero di iterazioni richieste* per ottenere $|z_{n}(c)| >2$.

```c
maxit = 1000; 
for each point (cx, cy) { 
	x = y = 0; it = 0;
	while ( it < maxit AND x*x + y*y ≤ 2*2 ) { 
		xnew = x*x - y*y + cx;
		ynew = 2*x*y + cy;
		x = xnew;
		y = ynew;
		it = it + 1;
	} 
	plot(cx, cy, it);
}
```

>[!danger] Problema
>Un partizionamento regolare può risultare in una ***distribuzione irregolare del carico di lavoro***.
>- I `pixel` **neri** richiedono `maxit` iterazioni.

Necessità di [[#Load Balancing]]
#### Partizionamento Irregolare
> Esempio

![[IrregularPartitioning.png]]

La superficie di un lago di può approssimare con una ***mesh di triangoli***.
- I colori indicano le *partizioni* date a ciascun processore.

### Index Mapping
> Gli elementi hanno sia un indice sia **locale** che **globale**.

>[!tldr] Collegamento
>Assumendo che tutti i blocchi sono della stessa lunghezza, l'indice globale si può trovare secondo la seguente formula:
>$$\text{GlobalIndex}=\text{LocalIndex}+\text{BlockId}\times\text{BlockLength}$$

### Load Balancing
>[!check] Load Balancing
>Idealmente ogni processore dovrebbe eseguire la ***stessa quantità di lavoro***.
>- Se i *task* si sincronizzano alla fine della computazione, il *tempo di esecuzione* sarà quello del ***task più lento***.

![[LoadBalancing.png]]

>[!done] Come Risolvere il Problema

Il workload è bilanciato se ogni processore esegue più o meno la ***stessa quantità di lavoro***.
> Modi di realizzare il *load balancing*.
- Utilizzo di partizionamento [[#In base alla Dimensione|fine-grained]].
- Utilizzo di ***allocazione dinamica dei task*** (*master-worker* paradigm).

#### Master-Worker Paradigm
>[!tldr] Idea
> Si inseriscono tutti i *task* in una coda, ad ogni unità di esecuzione viene assegnato un *task* secondo la **coda**.

Quando l'esecuzione del *task* termina, si assegna all'unità un nuovo *task*.
- Ci deve essere un ***meccanismo di coordinamento*** tra i task.