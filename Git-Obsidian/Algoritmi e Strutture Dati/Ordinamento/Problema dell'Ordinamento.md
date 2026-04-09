## Ordinamento
---
>[!Problema] Problema dell' Ordinamento
>>[!abstract] Input
>>Una sequenza di $n$ numeri $<a_{1},a_{2},\dots,a_{n}>$
>
>
>>[!caution] Output
>>I numeri ricevuti in input ***ordinati*** dal più *piccolo* al più *grande*, ovvero:
>>$$<a_{\pi(1)},a_{\pi(2)},\dots,a_{\pi(n)}>\text{ dove } a_{\pi(i)}\leq a_{\pi(i+1)}$$
>>$\pi$ è una opportuna permutazione degli indici $1,\dots,n$

>[!tip] Ordinamento
>Ordinare un insieme di elementi significa identificare una ***opportuna permutazione*** degli indici del vettore tali per cui *riposizionando gli elementi del vettore* in accordo con la ***permutazione*** si ottiene un vettore ordinato

### Ordinamento in Place
>[!info] Definizione
>L'algoritmo permuta gli elementi ***direttamente nell'array originale***, senza utilizzare un secondo array di *appoggio*
>Un algoritmo di ordinamento su array si dice in place **se in ogni istante al più un numero costante di elementi viene memorizzato al di fuori dell'array**

### Ordinamento Stabile
>[!info] Definizione
>L'algoritmo *preserva l'ordine* con cui elementi con la *stessa chiave* compaiono nell'array originale
>>Mantiene l'ordinamento relativo originale

## Limite Inferiore di Complessità
---
>[!tip] Algoritmi Comparison Sort
>Gli algoritmi *comparison sort* sono algoritmi basati su **confronti di coppie di elementi**
>>[!example] Per esempio:
>>- *Insertion-Sort*
>>- *Merge-Sort*
>>- *Heap-Sort*
>>- *Quick-Sort*
>
>Questi metodi calcolano una soluzione che dipende esclusivamente dall'esito di confronti fra numeri

### Teorema
>[!Teorema] Lower Bound for Comparison Sort
>Ogni algoritmo *comparison* *sort* deve avere un tempo di esecuzione asintotico di almeno $\Omega(nlog(n))$ per ottenere un insieme ordinato di elementi.
>Qualsiasi algoritmo di *comparison sort*, nel caso **pessimo** esegue $\Omega(nlog(n))$ confronti
>>[!done] Asymptotically Optimal
>>Si dice dunque che algoritmi come *merge sort* e *heap sort* sono ***asintoticamente ottimali*** e non esiste alcun algoritmo comparison sort che è più veloce di un altro per più di un fattore costante

>[!abstract] Limite inferiore per il caso pessimo
>Possiamo rappresentare un algoritmo di Sorting con un ***albero decisionale***.
>>[!Fact] Arrivati ad una foglia l'algoritmo ha ***stabilito un ordinamento***

Poiché ogni algoritmo di sort "***corretto***" deve essere in grado di produrre qualsiasi *permutazione degli indici del suo input*
- Ciascuna delle $n!$ permutazioni di $n$ elementi ***deve apparire come almeno una delle foglie*** dell'albero decisionale

>[!caution] Lunghezza del cammino più lungo
>La lunghezza del *cammino più lungo* dalla radice a una qualsiasi foglia di un albero decisionale rappresenta il ***numero di confronti nel caso pessimo***. 
#### Dimostrazione
> $n = 3 \implies \{ a_{1},a_{2},a_{3} \}$

![[attachements/Lower Bound for Comparison Sort.png]]
>*Rappresentato tramite un albero binario*

Consideriamo un albero decisionale di altezza $h$ con $l$ foglie *raggiungibili*
- Poiché, come abbiamo detto prima, ciascuna delle $n!$ permutazioni ***deve comparire come una o più foglie***, possiamo assumere:

$$
n!\leq l
$$

>[!question] Quanto deve essere alto un albero per avere $n!$ foglie?

Un [[../Strutture Dati/Grafi/Alberi/Gli Alberi Binari#Albero Binario|albero binario]] alto $h$ ha al massimo $2^h$ foglie
Quindi per quanto detto prima:

$$
n!\leq l\leq2^h
$$

- Dobbiamo avere $2^h\geq n!$
- Per la formula di Stirling: $n! >\left( \frac{n}{e} \right)^n, e=2.17\dots$

$$
h\geq log\left[ \left( \frac{n}{e} \right)^n \right]=nlog(n)-nlog(e) = \Omega(nlog(n))
$$