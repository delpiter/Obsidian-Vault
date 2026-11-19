## Tipologie di Grammatiche Probabilistiche
---
> Esistono varie tipologie di ***grammatiche probabilistiche***.

- [[#Grammatiche Regolari Probabilistiche]]
- [[#Grammatiche Probabilistiche Libere dal Contesto]]

Ovviamente 
## Grammatiche Probabilistiche Libere dal Contesto
---
> [!info] Probabilistic Context-Free Grammar
> Una `PCFG` è una ***quintupla*** $G=(V,\Sigma, P,S,D)$ dove $(V,\Sigma,P,S)$ è una [[../Linguistica Formale/Grammatiche e Linguaggi Liberi dal contesto#Context-Free Grammars|CFG]] e $D$ è una funzione che assegna una probabilità $p$ ad ogni produzione in $P$.

Per ciascuna variabile $A\in V$, la somma delle probabilità delle produzioni $A$ ***deve essere*** $1$.

Denotiamo la produzione probabilistica con:
$$
A\to \beta [p]
$$
> [!quote] A parole
> Data una variabile $A$ , $A$ viene espansa ad una sequenza $\beta$ con una ***probabilità*** $p$.

> Esempio: produzioni di una variabile $Adjs$ in una `PCFG`:

$$
\begin{align}
& Adjs \to Adjective \qquad \ \ [0.80] \\
& \qquad \ \ \mid Adjective \ \ Adjs \ [0.20]
\end{align}
$$
La somma delle probabilità di $Adjs$ deve arrivare a $1$.


> [!help] Lessico del Linguaggio
> Il ***lessico del linguaggio*** è specificato da un insieme finito $\Sigma$ di **simboli terminali della grammatica**, come parole del vocabolario, punteggiatura, etc...

Le produzioni indicano per ogni categoria lessicale quali [[Grammatiche a Struttura di Frasi#Tokenization|token]] appartengono a quella categoria.
- $C\to t[p]$ significa che quando genero un token di categoria $C$, scelgo $t$ con probabilità $p$.

### Derivazioni
> [!cite] Definizione
> Una ***derivazione*** $S\overset{*}{\implies} \alpha$ di una stringa $\alpha\in (V\cup\Sigma)^{*}$ in una `PCFG` è definita come per le [[../Linguistica Formale/Grammatiche e Linguaggi Liberi dal contesto#Context-Free Grammars|CFG]].

La probabilità $P_{G}(S\overset{*}{\implies} \alpha)$ di una derivazione è definita come il ***prodotto delle probabilità applicate***.
- Ogni produzione si considera una scelta indipendente dalle altre.

###### Esempio
> Il *linguaggio* di [Wumpus world](https://en.wikipedia.org/wiki/Wumpus_world)

$$
\begin{matrix}{}
S & \to  & NP \ \ VP  &  [0.90] \\
 & \mid  & S \ \ Conj \ \ S & [0.10] \\
NP  &  \to  & Pronoun  & [0.25] \\
 & \mid  & Name  & [0.10]  \\
& \mid  & Noun  & [0.10]  \\
& \mid  & Article \ \ Noun & [0.25] \\
& \mid  & Article \ \ Adjs \ \ Noun & [0.05] \\
& \mid  & Digit \ \ Digit  & [0.05] \\
& \mid  & NP \ \ PP  & [0.10] \\
& \mid  & NP \ \ RelClause  & [0.05] \\
& \mid  & NP \ \ Conj \ \ NP  & [0.05] \\
VP & \to  & Verb  & [0.40] \\
 & \mid  & VP \ \ NP  & [0.35] \\
 & \mid  & VP \ \ Adjective  & [0.05] \\
 & \mid  & VP \ \ PP  & [0.10] \\
 & \mid  & VP \ \ Adverb  & [0.10] \\
 \end{matrix}
$$
$$
\begin{align}{}
& Noun \to \text{stench}[0.05] \mid \text{breeze}[0.10] \mid \text{wumpus}[0.15] \mid \dots \\
& Verb \to \text{is}[0.10] \mid \text{feel}[0.10] \mid \text{smell}[0.10] \mid \dots \\
& Article \to \text{the}[0.40] \mid \text{a}[0.30] \mid \text{an}[0.10] \mid \dots \\
& \dots
\end{align}
$$

Una derivazione della frase $w=\text{ every wumpus smells}$ è la seguente
$$
S \Rightarrow NP \ \ VP \Rightarrow Article\ \ Noun\ \ VP \Rightarrow  every\ \ Noun \ \ VP \Rightarrow \\
\Rightarrow every \ \ wumpus \ \ VP \Rightarrow every \ \ wumpus\ \ Verb \Rightarrow w
$$

La probabilità della derivazione è il prodotto delle probabilità delle derivazioni utilizzate:
- $0.9\cdot 0.25\cdot 0.05\cdot 0.15\cdot 0.4\cdot 0.1 = 0.0000675$

#### Albero Sintattico
> [!cite] Parse Tree
> Gli [[../Linguistica Formale/Grammatiche e Linguaggi Liberi dal contesto#Alberi Sintattici|alberi sintattici]] di una `PCFG` m$G=(V,\Sigma, P,S,D)$ sono chiamati ***parse tree*** in *natural language processing* e sono definiti come gli alberi sintattici nelle `CFG`.

Sono quelli che generano una stringa $w\in \Sigma^{*}$ e hanno $S$ come ***radice***.

La probabilità $P_{G}(T)$ di un albero sintattico $T$ è la probabilità di una qualsiasi derivazione usata per generarlo usando le `PCFG` $G$.

### Ambiguità
> In generale i linguaggi naturali sono ***ambigui***.

> [!cite] Definizione
> Le ambiguità nelle `PCFG` sono definite  come per le [[../Linguistica Formale/Grammatiche e Linguaggi Liberi dal contesto#Ambiguità in grammatiche e linguaggi|CFG]].

In una `PCFG` si potrebbero avere delle stringhe $w\in\Sigma^{*}$ tali che $w$ ha diverse ***derivazioni canoniche*** **destre** o **sinistre**.
- Questo implica la presenza di diversi *alberi sintattici*.-------ilkukjukjyjky 

> [!cite] Probabilità
> La probabilità di generare $w\in \Sigma^{*}$ è la ***somma delle probabilità***:
> - di tutte le sue derivazioni *sinistre* (o *destre*) oppure
> - di tutti gli alberi sintattici che la generano.

#### Gestire le Ambiguità
> [!info] 
> La probabilità $P_{G}(w)$ di generare $w\in \Sigma^{*}$ con una `PCFG` $G$ è
> $$P_{G}(w)=\sum_{T\in Tree_{G}(w)} P_{G}(T)$$

Dove $Tree_{G}(w)$ è l'insieme degli alberi sintattici $T$ della `PCFG` $G$ che ***generano*** $w$.

Assumiamo che la somma da come risultato $0$ se $w$ ***non ha alberi sintattici che la genenerano*** ($Tree_{G}(w)=\emptyset$).

###### Esempio
> Con $w=\text{I can fish}$ con la seguente *grammatica probabilistica*:

$$
\begin{align}
& S\to NP \ \ VP \ \ [1]\\
& NP \to \text{Noun} \ \ [0.6]\mid \text{Pronoun}\ \ [0.4] \\
& VP \to \text{Verb }NP\ \ [0.8] \mid \text{Modal Verb}\ \ [0.2]  \\
&  \\
& \text{Noun} \to [fish]\ \ [0.3] \mid \dots \\
& \text{Pronoun} \to [I] \ \ [0.4]\mid [they]\ \ [0.3] \mid \dots \\
& \text{Verb} \to [can] \ \ [0.01]\mid[fish]\ \ [0.1]\mid\dots \\
& \text{Modal}\to[can]\ \ [0.3] \mid \dots
\end{align}
$$

La funzione $Tree_{G}(w)=\{ T_{1},T_{2} \}$ dove $T_{1}$ e $T_{2}$ sono i seguenti:
![[attachements/AmbiguousSyntaxTree.png]]

Aggiungendo le probabilità:
- $P(T_{1})=1\cdot 0.4\cdot 0.4\cdot 0.2\cdot 0.3\cdot 0.1=0.00096$ (***albero più probabile***)
- $P(T_{2})=1 \cdot 0.4 \cdot 0.4 \cdot 0.8 \cdot 0.01 \cdot 0.6 \cdot 0.3 = 0.0002304$

La probabilità $P(\text{"I can fish"})=0.00096+0.0002304 = 0.0011904$

### Probabilistic Formal Language
> [!cite] Definizione
> Dato un alfabeto $\Sigma$, una ***Probabilistic Formal Language*** è una distribuzione probabilistica $P$ su $\Sigma^{*}$.

Per esempio è una funzione probabilistica $P:\Sigma^{*}\mapsto [0,1]$ tale che $\sum_{w\in\Sigma^{*}}P(w)=1$

> Dato un alfabeto $\Sigma=\{ [hello],[bye] \}$.

La funzione di probabilità $P$ è tale che:
- $P([hello][bye])=0.9$
- $P([hello][hello][bye])=0.1$
- $P(w)=0\qquad \forall w \notin \{ [hello][bye],[hello][hello][bye] \}$

$P$ è un ***linguaggio formale probabilistico***

> [!abstract] Underlying Formal Language
> Il supporto di un linguaggio formale probabilistico $P$ chiamato ***linguaggio sottostante*** (*underlying language*) è il linguaggio formale $L=\{ w\mid P(w)> 0 \}$

Cioè l'insieme di tutte le stringhe $w$ a cui $P$ assegna probabilità ***strettamente positiva***.
### PCFG Problematiche
> Non tutte le `PCFG` rappresentano un *linguaggio formale*.

> [!warning] Contro Esempio

Consideriamo la `PCFG` $G$:
- $S\to a[0.4]$
- $S\to A[0.6]$
- $A\to A[1]$

$G$ può generare *solo* la stringa $a$ attraverso ***solo un albero sintattico***.
- Ottenuto applicando immediatamente la produzione $S\to a$

Quindi $\sum_{w\in\Sigma^{*}} P_{G}(w)=0.4$

> [!quote] Nelle `PCFG` so chiama probabilità di terminazione

In generale alcuni tipi di regole ricorsive causano una perdita di ***massa di probabilità*** data dalle derivazioni che non terminano mai.

#### Probabilità di Terminazione
> [!cite] Definizione
> La ***probabilità di terminazione*** $P_{G}$  di una `PCFG` $G$ è la probabilità totale di generare con $G$ una stringa terminale.
> $$P_{G}=\sum_{w\in\Sigma^{*}}P_{G}(w)$$

Possiamo valutare $P_{G}$ direttamente dagli *alberi sintattici*:
$$
P_{G}=\sum_{T\in Tree_{G}} P_{G}(T)
$$
Dove $Tree_{G}$ è l'insieme di tutti gli alberi sintattici di una `PCFG` $G$.

È la probabilità totale che il processo di derivazione dell'albero sintattico *termini con successo*, ritornando un albero sintattico $T$ **effettivo**.
- Un albero sintattico che sia finito e genera la stringa $w$.

### Consistenza
> [!cite] Definizione
> Una `PCFG` $G$ si dice ***consistente*** se la sua probabilità di terminazione è $1$.
> $$P_{G}=\sum_{w\in\Sigma^{*}}P_{G}(w)=1$$

Una `PCFG` consistente rappresenta:
- un *linguaggio formale probabilistico*.
- una distribuzione probabilistica $P_{G}(T)$ su $T\in Tree_{G}$

#### Condizioni Necessarie
> [!help] Info
> Una condizione *necessaria* ***ma non*** *sufficiente* per ottenere la consistenza è la seguente:
> Ogni *variabile raggiungibile* di una `PCFG` deve essere [[../Linguistica Formale/Grammatiche e Linguaggi Liberi dal contesto#Eliminazione dei simboli inutili|generante]].

In aggiunta alle definizioni di raggiungibile e generante delle `CFG`, aggiungiamo le seguenti condizioni per non considerare le  produzioni che potrebbero avere *probabilità zero*:
- ***Raggiungibile***: $P_{G}(S \overset{*}{{\Rightarrow}} \alpha X\beta) > 0$
- ***Generante***: $P_{G}(V\overset{*}{\Rightarrow}w)>0$


> [!attention] Nota bene
> Nelle `PCFG` **non** possiamo semplicemente *eliminare* variabili non generanti come si faceva nelle `CFG`, poiché eliminare una variabile potrebbe causare una violazione del ***vincolo della somma delle probabilità di una variabile***.

Possiamo però eliminare le variabili ***non raggiungibili***.

##### Esempio
> Esempio di una `PCFG` $G$ non consistente dove *tutte le variabili raggiungibili sono generanti*.

$$
\begin{align}
& S\to s[0.4] \\
& S\to S \ \ S[0.6]
\end{align}
$$

$$
P_{G}=0.4 + 0.6\cdot P_{G}\cdot P_{G}
$$
Dove:
- $0.4$ è la probabilità di scegliere la prima produzione.
- $0.6$ è quella di scegliere la seconda.
- I due $P_{G}$ sono le due variabili $S$ che dovranno essere sviluppate.


> [!warning] La variabile si riproduce troppo velocemente rispetto a quanto si elimina
> 

> [!tl;dr] Caratterizzazione della Consistenza
> Sia $G$ una `PCFG` dove ogni *variabile raggiungibile* è **generante**.
> $\mu_{g}^{rec}(A)\leq 1$ per ogni variabile ricorsiva $A$ in $G$ è una condizione che ***caratterizza la consistenza***.
> Dove:
> - $\mu$ è il numero medio di repliche di $A$ che $A$ *genera* in diversi alberi sintattici.

Nell'esempio precedente, dopo ogni *ciclo ricorsivo* $S$ genera $0.6\cdot 2$ repliche di se stesso, quindi $\mu_{g}^{rec}(S)=1.2 > 1$.
- La grammatica ***non è consistente***.

## Grammatiche Regolari Probabilistiche
---
> [!cite] Definizione
> Una ***grammatica regolare probabilistica*** è una `PCFG` dove le produzioni sono quelle di una [[../Linguistica Formale/Linguaggi Regolari|Grammatica Regolare]].

### Consistenza
> In una `PRG` la condizione necessaria delle `PCFG` è anche sufficiente.

È ovvio che se $G$ è regolare allora soddisfa la caratterizzazione di consistenza delle `PCFG`.

> [!summary] Prova
> Poiché nel corpo di una produzione è presente al più una variabile, una variabile ricorsiva $A$ non può generare repliche di se stessa in più di un ramo.
>> [!done] Può solo generare al più una replica di se stesso.
>