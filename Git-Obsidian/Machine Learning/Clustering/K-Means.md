## K-means
---
> Algoritmo di [[Clustering]] *computazionalmente molto semplice*, spesso è la prima scelta per risolvere.

> [!tldr] Idea
> L'algoritmo minimizza implicitamente le ***distanze dai centroidi***.
> Richiede in input il numero di cluster $s$
>> [!done] Produce buoni risultati a patto di fornire una ragionevole soluzione iniziale e un numero adeguato di classi.

Il tipo di ottimizzazione è **iterativa** e **locale**, pertanto il metodo può convergere a massimi locali della soluzione.
- La convergenza si ottiene solitamente in ***pochi passi*** ($>10$).

Identifica cluster iper-sferici nel caso in cui venga utilizzata la distanza euclidea come misura di distanza tra i pattern.
- Iper-ellissoidali nel caso di ***distanza di Mahalanobis***.

#### Descrizione dell'algoritmo
> Durante l'esecuzione ogni cluster viene rappresentato da un ***vettore detto centroide*** di lunghezza $D$ (dimensione del pattarn)

I vettori dei pattern e i centroidi si possono considerare come punti in uno spazio $D$ dimensionale.


> [!caution] L'algoritmo opera come segue
>
1. Si definiscono $K$ *centroidi iniziali*, ad esempio selezionando $K$ punti casuali nell'insieme $d$.
2. Si assegna ogni punto in $d$ al gruppo rappresentato dal ***centroide più vicino***; Per esempio usando la **distanza Euclidea** tra i vettori che rappresentano le coordinate del punto e del centroide.
3. Si calcola un nuovo centroide per ogni gruppo; le nuove coordinate sono la media aritmetica di quelle dei punti assegnati a quel gruppo.
4. Si ripete dal punto $2$ fino a quando le nuove posizioni dei centroidi (calcolate al punto 3) *differiscono di poco* da quelle precedenti, oppure fino a quando si raggiunge un *numero massimo di iterazioni*.

I cluster sono modificati iterativamente a seguito del ricalcolo del loro centroide.

![[Clustering/attachements/KMeansExecution.png]]


### Soluzione Iniziale e Validazione
> Diverse varianti sono proposte per ***generare buone soluzioni iniziali*** e di *determinare il numero di classi*.

> [!hint] Consiglio
> Per minimizzare il rischio di convergenza verso minimi locali l'algoritmo può essere eseguito più volte a ***partire da soluzioni iniziali diverse***.

Alcuni metodi per trovare una soluzione iniziale sono:
- ***Casuale***
- Prodotte da ***metodo euristico***
- Prodotte da un ***Metodo evoluzionistico*** (algoritmo genetico)


> [!question] In quanti cluster dividere?
> 

Le tecniche di validazione valutano a posteriori la bontà delle soluzioni prodotte per diversi valori di $s$, e a sceglierne una sulla base di un ***criterio di validazione*** che tanga conto sia della ***bontà della soluzione*** sia della *sua complessità*.


> [!warning] Problema
> Considerando il criterio di *minimizzazione delle distanze dai centroidi* e lanciando **K-means** con diversi valori di $s$ è molto più facile ottenere valori ridotti di $J_{e}$ per valori alti di $s$.

> ***Possibile prima soluzione***: Penalizzare le soluzioni con molti cluster

$$
J_{e}^{*} = J_{e} + penalty \cdot s
$$
Questa soluzione sposta solo il problema sulla scelta di *penalty*.

#### Discontinuità nel grafico
> Modo più efficace per determinare il numero ottimale di cluster.

> [!tldr] Idea
> Cerco i ***punti di inflessione*** (*elbow*) nel valore di $J_{e}$ al variare di $s$.

Se i pattern formano raggruppamenti evidenti e ben identificabili, scegliendo il corretto valore di $s$, dovremmo riscontrare una discontinuità nel grafico.

![[Clustering/attachements/GraphDiscontinuity.png]]

#### Silhouette Score
> [!tldr] Idea
> Si calcola il ***silhouette*** score come media dei *silhouette coefficient* di ciascun pattern e scegliere $s$ che lo massimizza.
> $$\text{Silhouette Coefficient}=\frac{b-a}{\max\{ a,b \}}$$

Dove $a$ è la distanza media intra cluster del pattern e $b$ la distanza tra il pattern e i pattern del cluster ad esso più vicino.