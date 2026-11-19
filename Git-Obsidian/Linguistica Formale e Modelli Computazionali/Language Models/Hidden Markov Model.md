## Introduzione
---
> Un terminating `HMM` è strettamente più espressivo di un mixture of `BoW` model e strettamente meno espressivo di una `PCFG`.

Un `HMM` è un generative probabilistic finite state automata equivalente alle [[Grammatiche Probabilistiche#Grammatiche Regolari Probabilistiche|grammatiche probabilistiche regolari]].
- È possibile trasformare una `PRG` in una `THMM` e vice versa ***preservando il linguaggio probabilistico generato***.

### Probabilistic Finite State Automata
> [!cite] Definizione
> Un ***automa a stati finiti probabilistico*** (`PFA`) è una quintupla $(Q,\Sigma,\delta,\pi,F)$ dove:
> - $Q$ è un insieme finito di ***stati***
> - $\Sigma$ è un ***alfabeto*** finito
> - $\delta$ è una funzione di transizione parziale da $Q\times\Sigma$ a distribuzioni di probabilità in $Q$
> - $\pi$ distribuzione di probabilità iniziale di stati $Q$.
> - $F\subseteq Q$ è un insieme di *stati finali*.

Le transizioni $\delta$ hanno il seguente vincolo:
- Per ogni stato $q$ e simbolo $a$ la somma delle probabilità in uscita deve essere $1$
$$
\forall a\in\Sigma, \forall q \in Q \\ \delta(q, a, q′) = 1
$$
> Esempio:

![[attachements/ProbabilisticFiniteStateAutomata.png]]

I `PFA` ***non sono*** modelli probabilistici generativi.
- Non dicono qual è la probabilità di eseguire una transizione $a$ o $b$ dallo stato $s_{0}$.

I `PFA` ***sono*** modelli probabilistici *reattivi*
- Nel reinforcement learning ***modellano il comportamento ambientale***.

### Markov Decision Process
> [!cite] Definizione
> Un ***Markov Decision Process*** è una sestupla $(Q,\Sigma,\delta,R,\pi,F)$ dove $(Q,\Sigma.\delta,\pi,F)$ è un `PFA` e $R$ è una ***funzione reward*** che da una transizione di un `PFA` $Q\times\Sigma\times Q$ porta a un numero reale $\mathbb{R}$.

Assegnano una **ricompensa positiva**, **nulla** o **negativa** $r$ ad ogni transizione del `PFA`.

Un agente interagisce con il `MDP` selezionando una azione ***secondo una policy***.
Il `MDP` riceve in input l'azione scelta e reagisce spostandosi in un altro stato e ***fornendo una ricompensa per l'azione***.

> Per esempio nel [[Grammatiche Probabilistiche#Esempio|wumpus world]]:
- Gold $\to +1000$
- Death $\to -1000$
- Step $\to -1$
- Arrow $\to -10$

### Markov Chains 
> Una ***Markov chain*** non è altro che un automa a stati finiti probabilistico senza label di transizioni e senza stati finali.

Per ogni stato c'è una ***distribuzione di probabilità sulle transizioni in uscita***.

> [!cite] Definizione
> Una ***Markov Chain*** è una tripla $(Q,\delta,\pi)$ dove:
> - $Q$ è un insieme finito di stati.
> - $\delta$ è una funzione di transizione da stati $Q$ a distribuzione di probabilità su $Q$.
> - $\pi$ distribuzione di probabilità iniziale di stati $Q$.
##### Esempio Pioggia/Sole
> Di seguito la ***Markov Chain*** *Sunny/Rainy day*

- $Q=\{ Sunny, Rainy \}$
- $\delta$ e $\pi$ sono definiti come segue
![[attachements/MarkovChain.png]]

> Calcoliamo la probabilità della seguente sequenza di stati:

- $Seq=\text{Sunny}\to\text{Sunny}\to\text{Rainy}\to \text{Rainy}$

$$
P(Seq)=0.7\cdot 0.8\cdot 0.2\cdot 0.6= 0.0672
$$


> [!hint] Osservazione
> Se ***fissiamo una lunghezza*** $k$ di sequenze, $P(Seq)$ è una *distribuzione di probabilità* su tutte le sequenze $Seq$ di lunghezza $k$.

#### Aggiunta dell'alfabeto
> Una ***catena di Markov*** è definita da un insieme di stati e dalle probabilità di passare da uno stato all’altro.

Ti dice *come evolve il sistema*, ma gli stati sono solo "***etichette interne***": la catena si muove da uno stato all'altro *senza produrre nulla di osservabile*.

> [!quote] Alfabeto
> Se vogliamo "***generi informazione***", serve che a ogni passo *emetta qualcosa*, ad esempio una *lettera*, una *parola*, un *bit*. 
> Per questo si introduce un **alfabeto** $\Sigma$, cioè l’insieme finito dei simboli che il modello può emettere

> Esempio
- $\Sigma = \{a, b\}$ oppure $\Sigma = \{0, 1\}$

### Hidden Markov Model
> [!cite] Definizione
> Un ***Hidden Markov Model*** è una quintupla $(Q,\Sigma,\delta,E, \pi)$ dove:
> - $(Q,\delta,\pi)$ è una *Markov Chain*
> - $\Sigma$ è l'alfabeto i cui simboli sono chiamate ***osservazioni***
> - $E$ è una funzioni di emissione, dagli stati $Q$ a una distribuzione di probabilità.

Il termine "*nascosto*" deriva dall'assunzione che non possiamo osservare gli stati direttamente, ma solamente i loro effetti **attraverso le osservazioni**.
 
Per permettere di rappresentare una [[Grammatiche Probabilistiche#Probabilistic Formal Language|probabilistic formal language]], richiediamo anche la generazione del token `<EOS>`, come per [[Language Models#Mixture of Bag Of Words Model|Mixture of BoW]].
- Chiamiamo questi modelli ***Terminating Hidden Markov Models***

Come per le `PCFG` non tutti i `THMM` rappresentano un *linguaggio formale probabilistico*.
- Per esempio una `THMM` con uno stato iniziale $Categ : \pi(Categ)> 0$ da cui non c'è uno ***stato di terminazione raggiungibile***.
	- Da $Categ$ non c'è un percorso di transizioni che porta ad uno stato $Categ'\mid P(\text{<EOS>} \mid Categ')>0$.


> [!check] Terminating Hidden Markov Models consistenti
> Una `THMM` è ***consistente*** se la somma delle probabilità di tutte le $w\in\Sigma^{*}$ è $1$:
> $$\sum_{w\in\Sigma^{*}}P(w)=1$$ 

Una `THMM` *consistente* rappresenta un ***linguaggio formale probabilistico***. 
###### Esempio Sunny Rainy
> All'esempio di prima aggiungiamo $\Sigma=\{ true, false \}$ che indica l'osservazione di una persona con un ombrello.

![[attachements/HiddenMarkovModel.png]]

Una `HMM` genera ***sequenze di osservazioni***.
- L'[[Problema dell'Inferenza|inferenza]] è il problema che ***determina la probabilità*** di una sequenza di stati nascosti *data una sequenza di osservazioni*.

#### Probabilità di una sequenza di osservazioni
> [!abstract] Info
> La ***probabilità di generazione*** di una stringa $w=o_{1},o_{2},\dots,o_{n}$ attraverso una *sequenza di stati* $Seq$ è calcolata tramite la seguente formula:
> $$P(Seq,w)=P(Seq)P(w\mid Seq)=P(Seq)\prod_{i=1}^{N(w)}P(o_{i}\mid Categ_{i})$$

Dove $N(w)=|w|=N$ è il numero di osservazioni necessarie per generare $w$.

Ogni stringa $w$ può essere generata attraverso una quantità esponenziale di sequenze di stato $Seq$.

> [!summary] Probabilità totale
> La ***probabilità di generazione totale*** di una stringa $w$ è:
> $$P(w)=\sum_{Seq\in Seq(w)} P(Seq,w)$$

Dove $Seq(w)$ è l'***insieme di sequenze di stati*** $Seq$ che possono generare $w$ tali che $|Seq|=N(w)$.
- Come per le ***Markov Chains*** se fissiamo una lunghezza $k$, $P(w)$ è una *distribuzione di probabilità* su tutte le stringhe di lunghezza $k$.
	- Per ottenere una distribuzione di probabilità dobbiamo evitare stringhe che sono uno il prefisso di un'altra.

#### Terminating Hidden Markov model come Language Model
> Si possono usare le `THMM` come [[Language Models|Language model]].

L'idea utilizza il concetto di [[Grammatiche Probabilistiche#Grammatiche Probabilistiche Libere dal Contesto|PCFG]].

> [!tldr] Idea
> Una frase è una sequenza di parole (*token*).
> A ogni parola corrisponde una **categoria lessicale** (nome, verbo, articolo, ...), che nel modello è lo ***stato nascosto***.

Noi vediamo solo le parole, non le categorie.

> Esempio: "***il gatto dorme***"
- stati nascosti: $ART \to NOME \to VERBO$
- osservazioni (simboli di $\Sigma$): $il, \ gatto,\  dorme$

Quindi gli stati del `THMM` rappresentano le ***categorie lessicali*** di una `PCFG` che sono rappresentate attraverso una *Markov Chain*.

Infine le osservazioni sono le produzioni da *categoria lessicale* a *token*.

#### Mixture of BoW come Terminating HMM
> Una Mixture of BoW non è altro che una terminating `HMM` dove:


> [!hint] Gli stati sono le possibili categorie

- Ogni stato ha un ***solo autociclo*** con probabilità $1$.
- Le osservazioni possibili in ogni stato sono le probabilità condizionali sui token di ogni categoria della mixture of BoW.