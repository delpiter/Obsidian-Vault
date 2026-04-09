## Algoritmo
---
>[!definizione] Algoritmo
>Un ***algoritmo***, che indichiamo con $\Psi$, è una sequenza di operazioni di macchina che devono essere eseguite al fine di ottenere, in un *numero finito di passi*, da un vettore di numeri macchina $\tilde{x}$, un ***output*** $\Psi(\tilde{x})=\tilde{y}$.

### Stabilità
>[!hint] Proprietà
>La ***stabilità*** esprime il *comportamento* dell'algoritmo considerato rispetto alla *propagazione degli errori*.
>>[!done] In Altre Parole
>>La ***stabilità*** di un algoritmo valuta la reazione dell'algoritmo all'introduzione di *perturbazioni nei dati iniziali*.

Dato l'algoritmo $\Psi$ vogliamo vedere come la sequenza di operazioni di macchina eseguite sui numeri macchina $\tilde{x}$ ***propaga l'errore iniziale***.

> Confrontiamo il **risultato** prodotto dall'*algoritmo* con il risultato che si otterrebbe applicando la funzione originale $f$ ai dati perturbati.

Definiamo l'***Errore Algoritmico***:
$$
E_{alg}=\displaystyle{\frac{\Psi(\tilde{x})-f(\tilde{x})}{f(\tilde{x})}}
$$

**Influiscono** sull'errore algoritmico:
- Il **numero** di operazioni eseguite.
- L'**ordine** delle operazioni.
- Il **tipo** di operazioni eseguite.
### Accuratezza della Soluzione Numerica
>[!missing] Errore Inerente
>Definiamo ***Errore Inerente***, quello che deriva dalla [[../Numeri Finiti/Floating Point|rappresentazione finita]] dei numeri nel sistema di calcolo ed è legato al [[#Condizionamento di un Problema|condizionamento]] del problema.
>$$E_{in}=\displaystyle{\frac{f(\tilde{x})-f(x)}{f(x)}}$$

>[!help] Errore Algoritmico
>Definiamo ***Errore Algoritmico***, l'errore introdotto dalle [[../Numeri Finiti/Aritmetica in Virgola Mobile|operazioni aritmetiche in aritmetica finita]] durante l'esecuzione di un algoritmo.
>$$E_{alg}=\displaystyle{\frac{\Psi(\tilde{x})-f(\tilde{x})}{f(\tilde{x})}}$$

Nel calcolo di una funzione ***dati-risultato*** $f(x)$, l'*accuratezza della soluzione numerica*:

>[[Condizionamento|!done]] del problema che dalla ***stabilità algoritmica***

$$
E_{tot}=\displaystyle{\frac{\Psi(\tilde{x})-f(x)}{f(x)}}
$$

> Verifichiamo che $E_{tot}\approx E_{in} + E_{alg}$

$$
\begin{array}
\ \displaystyle{\frac{\Psi(\tilde{x})-f(x)}{f(x)}} = \displaystyle{\frac{\Psi(\tilde{x})}{f(x)}}-1= \\
=\displaystyle{\frac{\Psi(\tilde{x})}{f(\tilde{x})}} \displaystyle{\frac{f(\tilde{x})}{f(x)}}-1= \\
=\displaystyle\frac{\Psi(\tilde{x}) - f(\tilde{x}) + f(\tilde{x})}{f(\tilde{x})} \cdot \frac{f(\tilde{x}) - f(x) + f(x)}{f(x)} - 1= \\
= \displaystyle\left( \frac{\Psi(\tilde{x}) - f(\tilde{x})}{f(\tilde{x})} + 1 \right) \left( \frac{f(\tilde{x}) - f(x)}{f(x)} + 1 \right) - 1 = \\
=\displaystyle \frac{\Psi(\tilde{x}) - f(\tilde{x})}{f(\tilde{x})} \frac{f(\tilde{x}) - f(x)}{f(x)} + \frac{\Psi(\tilde{x}) - f(\tilde{x})}{f(\tilde{x})} + \frac{f(\tilde{x}) - f(x)}{f(x)} + 1 - 1= \\
=\displaystyle \frac{\Psi(\tilde{x}) - f(\tilde{x})}{f(\tilde{x})} \frac{f(\tilde{x}) - f(x)}{f(x)} + \frac{\Psi(\tilde{x}) - f(\tilde{x})}{f(\tilde{x})} + \frac{f(\tilde{x}) - f(x)}{f(x)}
\end{array}
$$

Quindi:
$$
E_{tot}=E_{alg}\cdot E_{in} + E_{alg} +E_{in}
$$
- Trascurando i prodotti degli errori relativi $E_{alg}\cdot E_{in}$

$$
E_{tot}\approx E_{in} + E_{alg}
$$
$\#$

>[!hint] Osservazione
>La ***bassa accuratezza*** dei risultati prodotti da un processo numerico può essere imputabile ad:
>- Alto [[Condizionamento#Condizionamento di un Problema|mal condizionamento]] del problema.
>- ***Instabilità*** dell'algoritmo usato.

>[!warning] Osservazione
>La ***stabilità*** dell'algoritmo **non garantisce** che il risultato calcolato sia accurato.

Per un problema *mal condizionato*, la distinzione tra algoritmo **stabile** e **instabile** non è molto significativa.
- L'*errore totale* risulta dominato dall'errore inerente.

### Stabilità Numerica

>Si parla di ***stabilità*** (o ***instabilità***) numerica intendendo che gli *errori* sui dati **non sono** (o **sono**) amplificati durante lo sviluppo dell'algoritmo.
$$\mid E_{alg}\mid\approx g(n)\cdot\varepsilon\quad \mid \varepsilon\mid \leq u$$


- $n$ -> numero di operazioni.
- $g(n)=c\cdot n, \ c>0$ -> crescita dell'errore lineare.
- $g(n)=c^n, \ c>1$ -> crescita dell'errore esponenziale.

>[!definizione] Definizione
> Un algoritmo è detto ***stabile*** se $g(n)$ è lineare, cioè l'errore algoritmico è dell'*ordine di grandezza della precisione di macchina*, instabile altrimenti.

## Bontà di un Algoritmo
---
>[!info]
> Un algoritmo per essere definito "***buono***" oltre ad essere *generale*, *robusto* e *stabile*, deve anche richiedere il ***numero di operazioni minimo*** possibile per ottenere il risultato e allocare la ***quantità di memoria minima*** possibile.

Si definisce [[../../Algoritmi e Strutture Dati/Confronto fra Algoritmi/Complessità di Algoritmi|complessità computazionale]] di un *algoritmo*, il numero di operazioni aritmetiche floating point richieste per la sua esecuzione.
- Unità di misura: [[../../Architettura degli Elaboratori/Architetture a Confronto/Prestazioni dei Calcolatori#Benchmark|FLOP]]-> $1$ *FLOP* ($1$ operazione elementare $+,-,*,/$)

### Esempio
>La soluzione di un sistema lineare di ordine $n$.

>[[../../Algebra e Geometria/Risoluzione di Sistemi#Metodo di Cramer|Metodo di Cramer]]
>L'algoritmo ha una complessità dell'ordine di $O((n+1)!)$

>[[../../Algebra e Geometria/Risoluzione di Sistemi#Metodo di Gauss|Metodo di Gauss]]
>L'algoritmo ha una complessità dell'ordine di $O(n^3)$.


| n    | Metodo di Cramer | Metodo di Gauss              |
| ---- | ---------------- | ---------------------------- |
| $10$ | $4$ secondi      | $3.3\times 10 ^{-5}$ secondi |
| $14$ | $36$ ore         | $9.1\times 10 ^{-5}$ secondi |
| $18$ | $386$ anni       | $1.9\times 10 ^{-4}$ secondi |
