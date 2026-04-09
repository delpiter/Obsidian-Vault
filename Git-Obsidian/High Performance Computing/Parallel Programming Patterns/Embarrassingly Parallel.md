>[!summary] Pattern
>[[Parallel Programming Patterns|Pattern di Programmazione parallela]] che si applica quando la computazione può essere decomposta in ***task indipendenti*** che richiedono *poca o nessuna comunicazione*.

> Esempi
- *Vector Sum*.
- *Mandelbrot Set*.
- [[../../Computer Graphics/Rendering Pipeline/Rendering Graphics Pipeline|3D Rendering]].
- ***Brute Force*** password cracking.

>[!abstract] Scatter-Gather
> ***Scatter-Gather*** è una applicazione pratica dell'*Embarrassingly Parallel pattern*.

Ogni *processo* elabora una porzione di input ("*dati locali*") per ottenere un risultato parziale.
- Alla fine **combino** i risultati parziali per ottenere il *risultato finale*.

![[attachements/Scatter-Gather.png]]

