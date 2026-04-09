## Algoritmo di Ford-Fulkerson
---
>[!info] Algoritmo
>L'algoritmo di ***Ford-Fulkerson*** è un [[../../../Greedy/Gli Algoritmi Greedy|algoritmo greedy]] che risolve il problema dei [[Problema|flussi massimi]]
>>[!example] Funzionamento
>>1. *Set* $f(u,v)=0\qquad \forall (u,v)\in A$
>>2. Trova un ***cammino aumentante*** $P$ nel grafo residuo $G_{f}$
>>3. Aumenta il flusso su $P$ e aggiorna $G_{f}$
>>4. Ripeti 2-4 finchè possibile

>[!warning] Problema

È possibile, usando questo algoritmo, che ad un qualsiasi step venga scelto un cammino "*sbagliato*", da cui da quel punto in poi non è più possibile trovare la soluzione migliore
- Per risolvere questo problema è necessario ampliare la definizione di [[Problema#Grafo Residuo|capacità residua]]

>[!abstract] Capacità Residua, Ampliamento
>Ridefiniamo la ***Capacità Residua***:
>La capacità residua è definita sia ***riducendo la capacità del flusso***, sia ***aumentando la capacità del flusso nell'arco opposto***
>$$c_{f}(u,v)=\begin{cases}c(u,v)-f(u,v)\quad \text{ direzione }u\to v \\c(u,v)+f(u,v)\quad \text{ direzione }v\to u\end{cases}$$
>
>>[!done] Conlusione
>>Questo ampliamento della definizione permette di fare "*correzioni*", *cancellando* il flusso nella direzione *sbagliata*
### Pseudocodice
>[!abstract] Concetto
>L'algoritmo si sviluppa in due passi
>1. Trovare un [[Problema#Cammino Aumentante|cammino aumentante]] (senza condizioni di ricerca)
>2. Controllo l'ottimità della soluzione


```pseudo
	\begin{algorithm}
	\caption{Ford Fulkerson's Algorithm}
	\begin{algorithmic}
\Procedure{Ford-Fulkerson}{$ G,s,t $}
\State $  $
\Comment{Initialization}
\ForAll{$\text{edge }(u,v)\in E[G] $}
\State $ f[u,v]=0 $
\State $ f[v,u]=c[v,u]=0 $
\EndFor
\While{$\exist \text{ a path }p\text{ from }s \text{ to }t\text{ in the residual network } G_f$}
\State $ c_f(p) =min\{c_f(u,v):(u,v)\in p\}$
\ForAll{$\text{edge }(u,v)\in p$}
\State $ f[u,v]=f[u,v]+c_f(p) $
\State $ c[v,u]=c[v,u]+c_f(p) $
\EndFor
\EndWhile
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```
#### Esempio
![[attachements/Ford-Fulkerson1.png]]
![[attachements/Ford-Fulkerson2.png]]

### Complessità
>[!tldr] Se ogni capacità è intera
>La complessità è $O(|E|f^*)$
>- Dove $f^*$ è il valore del flusso massimo
>
>>[!done] Motivazione
>>Ad ogni iterazione il flusso aumenta almeno di $1$
>>>[!fail] L'algoritmo potrebbe quindi essere non polinomiale

#### Inefficienza
>*Senza alcun criterio per la scelta del cammino aumentante si potrebbero avere delle situazioni sgradevoli*

![[attachements/Revisited.png]]
- *$+1.000.000$ di iterazioni per un grafo di 4 vertici!*

