> Il concetto di [[../Valutazione delle Performance#Speedup|speedup]] non può essere usato

>[[CUDA|!fail]] cores usati.

> Servono ***metriche diverse***:

>[!caution] Throughput.
> Il ***throughput*** è il numero di operazioni al secondo in ***funzione della grandezza dell'input***.
- Si eseguono una serie di test con ***input sempre più grandi***.

$$
\text{Throughput}=\displaystyle{\frac{\text{\# of operation}}{\text{ex. Time}}}
$$
Il numero di operazioni è approssimabile con il *costo asintotico dell'algoritmo*.
- Il throughput è calcolato in `ops/sec` o `mlnops/sec`.


>[!abstract] Speedup vs Efficient `CPU` implementation.
> Per lo **speedup** si confrontano i programmi per `CPU` e `GPU`.
> Bisogna avere *hardware di simile performance* e *software ottimizzato* per entrambi i programmi.

$$\text{Speedup}=\frac{T_{CPU}}{T_{GPU}}$$