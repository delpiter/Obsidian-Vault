## Multi-classificatori
---
> [!tldr] Idea
> Un ***multi-classificatore*** è un approccio dove diversi classificatori sono utilizzati in *parallelo*, in *cascata* o in *modo gerarchico* per eseguire la classificazione dei pattern.

Le decisioni dei singoli classificatori sono *fuse* ad un certo livello del processo di classificazione.

È stato dimostrato (in teoria e anche in pratica) che l'utilizzo di combinazioni di classificatori (o *classifier fusion*/*ensemble learning*) può migliorare anche molto le prestazioni.
- Nella pratica investire tempo nell'ottimizzazione di un singolo classificatore è in genere meno conveniente rispetto all'affiancamento di altri classificatori.

> [!caution] Efficacia
> La combinazione è *efficace* solo quando i singoli classificatori sono (almeno parzialmente) ***indipendenti tra loro***.
>> [!hint] Sono indipendenti quando non commettono gli stessi errori

L'indipendenza è normalmente ottenuta:
- Utilizzando ***feature diverse***: feature non o poco correlate.
- Utilizzando ***algoritmi diversi*** per l'estrazione delle *feature*.
- Utilizzando ***diversi algoritmi*** di *classificazione*.
- Addestrando lo ***stesso algoritmo*** di classificazione su *porzioni diverse* del training set (*bagging*).
- Insistendo con l'***addestramento sugli errori*** commessi dai predecessori (*boosting*).

## Fusione dei risultati
---
> [!question] Come posso unire i risultati di un insieme dei classificatori?

La combinazione può essere eseguita a livello di *decisione* o a livello di *confidenza*.
### Fusione a livello di decisione
> [!info] 
> Ogni singolo classificatore fornisce in output la *propria decisione* che consiste nella ***classe*** di cui ha assegnato il pattern.

Le decisioni possono essere combinate in vari modi.
#### Majority Vote Rule
> [!hint] Regola del voto
> Uno dei più noti e semplici metodi di fusione.
> Ogni classificatore vota per una classe, il pattern viene assegnato alla ***classe maggiormente votata***.

Se $\{ C_{1},C_{2},\dots,C_{nc} \}$ è un insieme di $nc$ classificatori e:
$$
\theta_{ij} = \begin{cases}
1\qquad \text{se }i \text{ è la classe votata da } C_{i} \\
0\qquad \text{altrimenti}
\end{cases}
$$
Con:
- $1\leq i \leq s$ e $s$ numero di classi del problema
- $1\leq j \leq nc$

Allora il pattern è assegnato alla classe $t$ tale che:
$$
t = \arg\max_{i=1,\dots,s}\left\{  \sum_{j=1,\dots,nc} \theta_{ij} \right\}
$$

#### Borda Count
> Variante di ***Majority Vote Rule***

> [!info] 
> Ogni classificatore invece di una singola classe, ***produce una classifica*** o ranking delle classi a seconda della *probabilità* che a ciascuna di esse appartenga il pattern da classificare.

I ranking sono convertiti in punteggi e poi sommati.
- La classe con il più elevato punteggio finale è quella scelta dal multi-classificatore.
- Rispetto a `MRV` considera anche i risultati "***non primi***" di ogni classificatore.
#### Prestazioni Teoriche
> [!cite] Teorema
> Dato un problema di ***classificazione binario*** e un *multiclassificatore* costruito da $nc$ classificatori, la majority rule vote classifica il pattern come appartenete alla classe che ha ottenuto almeno $k=\frac{nc+1}{2}$ voti.
> 

Sia $P$ la probabilità che ogni singolo classificatore esegua la classificazione correttamente.
La probabilità $P_{multi}(nc)$ che la decisione del multi-classificatore sia corretta è esprimibile attraverso la [[../../Matematica Discreta e Probabilità/Probabilità/3 - Variabili Aleatorie#Variabili Binomiali|distribuzione binomiale]].
$$
P_{multi}(nc)=\sum_{m=k}^{nc}\binom{nc}{m}p^{m}(1-P)^{nc-m}
$$
> Esempio

Se $P=0.8$ (ogni classificatore commette il $20\%$ di errore di classificazione) stando alla formula per un *multiclassificatore* con $nc$ componenti:
- $P_{multi}(3)=0.896$
- $P_{multi}(7)=0.966$
- $P_{multi}(15)=0.995$
- $P_{multi}(21)=0.999$


> [!warning] Attenzione
> La formula è basata sull'***indipendenza totale dei classificatori***, difficilmente ottenibile in pratica.

#### One Against One
> [!tldr] Idea
> L'approccio ***one against one*** consente di risolvere un problema di classificazione multi-classe, attraverso *classificatori binari*.

Se $s$ sono le classi del problema, si addestrano $s\times \frac{s-1}{2}$ classificatori binari.

Durante la classificazione il pattern $x$ viene classificato da ogni classificatore binario, che assegna un voto alla classe più probabile (una classe e tutte le altre).
- Al termine il pattern $x$ è assegnato alla classe che ricevuto più voti.

È in genere più accurato di [[Support Vector Machines#Estensione Multiclasse|one against all]] anche se meno efficiente in quanto richiede l'addestramento di un numero maggiore di classificatori.
### Fusione a livello di Confidenza
> [!abstract] Info
> Ogni ***singolo classificatore*** $C_{j}$ fornisce in output la *confidenza* di classificazione del pattern rispetto a ciascuna delle classi, ovvero un vettore $\text{conf}_{j}=[\text{conf}_{j1},\text{conf}_{j2},\dots,\text{conf}_{js}]$ in cui l'$i$-esimo elemento indica il grado di appartenenza del pattern alla classe $i$-esima.

Diversi metodi di fusione sono possibili tra cui:
> ***Somma***

$$
\sum_{j=1,\dots,nc}\text{conf}_{j} \qquad\qquad t=\arg\max_{i=1,\dots,s}\{ \text{sum}_{j} \}
$$
Metodo più **stabile** e **robusto** fra i $4$.
Una variante efficace è quella della ***somma pesata***
- La somma dei vettori confidenza è eseguita ***pesando i diversi classificatori*** in base al loro grado di abilità $g_{j}$
$$
\text{avgsum}=\sum_{j=1,\dots,nc} g_{j}\cdot\text{conf}_{j} \qquad\qquad t=\arg\max_{i=1,\dots,s}\{ \text{avgsum}_{i} \}
$$
I gradi di abilità possono essere definiti in base alle singole prestazioni dei classificatori.

> ***Prodotto***

$$
\prod_{j=1,\dots,nc}\text{conf}_{j} \qquad\qquad t=\arg\max_{i=1,\dots,s}\{ \text{prod}_{j} \}
$$


> [!hint] Osservazione
> 

- In termini probabilistici è più preciso, poiché la probabilità congiunta si calcola come prodotti di probabilità, **ma** solo nel caso di perfetta indipendenza.
- Un voto molto basso di un classificatore rischia di annullare i voti degli altri.

> ***Massimo***

$$
\max_{j=1,\dots,nc}\{ \text{conf}_{ji} \} \qquad\qquad t=\arg\max_{i=1,\dots,s}\{ \text{max}_{i} \}
$$

> ***Minimo***

$$
\min_{j=1,\dots,nc}\{ \text{conf}_{ji} \} \qquad\qquad t=\arg\max_{i=1,\dots,s}\{ \text{min}_{i} \}
$$

Può sembrare illogico:
- Viene scelta la classe che ***non ha ricevuto confidenza troppo bassa*** da nessun classificatore.