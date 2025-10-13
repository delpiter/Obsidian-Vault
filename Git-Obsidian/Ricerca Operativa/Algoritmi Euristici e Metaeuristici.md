> Si consideri un generico [[Definizioni_Algoritmi#Problema di Ottimizzazione|problema di ottimizzazione]].

>[!question] Problema
>$$\min f(x) \qquad x\in X$$

La funzione $f:\mathbb{R}^{n}\to \mathbb{R}$ è detta ***funzione obbiettivo***.
Il vettore delle variabili decisionali è $x=[x_{1},x_{2},\dots,x_{n}]^{T}\in\mathbb{R}^{n}$
- L'insieme $X$ rappresenta le [[Supporto alle Decisioni#Ottimizzazione Vincolata|soluzioni ammissibili]].
- Ogni *soluzione ammissibile* $x\in X$ ha un costo $f(x)$.

> Se esiste una soluzione $x^{*}\in X$ tale che:
$$
f(x^{*})<f(x) \qquad \forall x\in X
$$
- Allora $x^{*}\in X$ è la ***soluzione ottima***.

>[!hint] Obbiettivo
>L'*obbiettivo* è quello di determinare tra le soluzioni ammissibili una ***soluzione ottima*** o una soluzione di ***buona qualità***.

Molti problemi di ottimizzazione sono [[Classi P e NP#NP Completo|NPC]] e spesso le istanze di interesse pratico hanno dimensioni tali da ***rendere proibitivo l'uso di algoritmi esatti***.
- Si possono usare ***algoritmi euristici***.

## Algoritmi Euristici
---
![[Definizioni_Algoritmi#Algoritmi Euristici]]

>In generale:
- Gli algoritmi euristici **non garantiscono l'ottimalità**  della soluzione prodotta.
- Di norma non sono in grado di fornire una *stima della distanza dalla soluzione ottima*.

### Classificazione
> Gli algoritmi euristici possono essere classificati come segue:

>[!hint] Algoritmi costruttivi e di Ricerca Locale
>Sfruttano le proprietà *strutturali* delle soluzioni ammissibili per ottenere rapidamente una ***soluzione di buona qualità***.

>[!quote] Metaeuristiche
>Gestiscono il **trade-off** tra *diversificazione* della ricerca, quando la ricerca è effettuata in regioni dello spazio di ricerca poco promettenti, e *intensificazione* nella regione dello spazio più promettente.

> Tipologie
- *Single Solution Metaheuristic*.
- *Population Based Metaheuristic*.
- *Matheuristic*.

>[!caution] Algoritmi sulla Programmazione Matematica
>Sfruttano alcuni risultati della **programmazione matematica** (*Decomposizione*, *lower*/*upper bound*).
>

- Danno uno *schema generale per un problema*.

#### Ricerca Locale
>[!info] Local Search
>Per ogni soluzione $x\in X$, si definisce l'insieme di vicinanza $N(x)\subset X$, noto anche come ***neighborhood***, che rappresenta le soluzioni vicine alla soluzione $x$.

È possibile scegliere soluzioni **non** ammissibili introducendo una ***penalizzazione adeguata***.

```pseudo
	\begin{algorithm}
	\caption{Local Search}
	\begin{algorithmic}
	\State $ \text{Genera una soluzione iniziale } x\in X $
	\State $ \text{Trova } x'\in N(x), \text{ tale che } f(x')=\min\{f(x''):\forall x'' \in N(x)\}$
	\State $ \text{Se } x'<f(x), \text{ allora } x=x' \text{ e vai allo step }2$
	\State $ \text{La miglior soluzione trovata è }x^* = x $
	\end{algorithmic}
	\end{algorithm}
```

L'aggiornamento della soluzione allo `step 3` è detto ***spostamento***.

#### Tabu Search
>[!info] Tabu Search
>Il ***Tabu Search*** ad ogni iterazione, si muove nella migliore soluzione disponibile nell'*intorno della soluzione corrente*.
>$$f(x')=\min\{ f(x''):\forall x''\in N(x) \}$$

Il *tabu serach* consente di uscire dai minimi locali muovendosi anche in ***soluzioni peggiori di quella corrente***.
- Una struttura in memoria (`tabu list`) impedisce di tornare su soluzioni già visitate.

La ricerca locale si modifica come segue:
$$f(x')=\min\{ f(x''):\forall x''\in N(x) ,x''\notin TL\}$$
- La `tabu list` ha *dimensioni massime*, per cui dopo un certo numero di iterazioni alcune soluzioni **potrebbero essere riconsiderate**.

#### Simulated Annealing
>[!info] Annealing
>Il ***Annealing*** corrisponde al *processo termico* che raggiunge stati di **bassa energia libera** in un materiale solido mediante ripetute fasi di *riscaldamento* e *lento raffreddamento* controllato.

Il *Simulated Annealing* è un algoritmo che imita questo processo termodinamico per **minimizzare una funzione obbiettivo**.
- Parte da una temperatura alta che consente di **peggiorare la soluzione** con alta probabilità, per poi diminuire progressivamente la temperature e ridurre la probabilità di accettare peggioramenti.

#### Quantum Computing

>[!check] Quantum Computing
>Il ***quantum computing*** è un campo che utilizza la *meccanica quantistica* per risolvere problemi troppo complessi per i computer classici.
>Si avvale di fenomeni **quantistici** come la ***superposition*** (un `qubit` che esiste contemporaneamente come $0$ e $1$) e l'***entanglement*** (in cui i `qubit` sono collegati e si *influenzano istantaneamente*, **indipendentemente dalla distanza**) per eseguire calcoli.

Tra i risultati finora ottenuti possiamo citare il ***Quantum Annealing*** che rappresenta una generalizzazione del *Simulated Annealing*.
#### Algoritmi Genetici
>[!tip] Genetic Algorithms
>Gli ***algoritmi genetici*** definiscono un insieme di soluzioni (*individui*) che costituiscono la *popolazione*. che ad ogni iterazione è "aggiornata".

La popolazione è aggiornata ricombinando sottoinsiemi di individui (*parent set*) per ottenere nuove soluzioni.
- Questa operazione è detta ***crossover***.

Al termine di ogni iterazione si **selezionano** gli individui che faranno parte della popolazione nella ***prossima iterazione***.

>[!example] Algoritmo Genetico

1. Genera una popolazione $P$ di soluzioni iniziali.
2. Valuta il costo $f(x), \forall c\in P$ (*funzione di fitness*).
3. *Selezione dei genitori*: Seleziona un sottoinsieme $G\subset P$ di soluzioni.
4. *Crossover*: Costruisci un insieme $P_{G}$ di soluzioni combinando fra loro i genitori in $G$.
5. *Mutazione*: Modifica casualmente alcune soluzioni in $P_{G}$.
6. *Selezione della Popolazione*: La nuova popolazione è selezionata sostituendo alcuni individui di $P$ con gli individui di $P_{G}$.
7. Se la *condizione di terminazione* non è soddisfatta vai allo step $3$.

