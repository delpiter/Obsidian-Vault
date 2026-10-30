## Non Deterministic Finite Automaton
---
> [!hint] Definizione
> Un ***automa a stati finiti non deterministici*** (`NFA`) è un automa a stati finiti dove per ogni coppia di stato e simbolo in ingresso ci possono essere da $0$ a $n$ transizioni allo stato successivo.

Un `NFA` accetta una [[Linguistica#Stringa|stringa]] se tra i tanti possibili, ***esiste un cammino*** che conduce ad uno stato finale.

> Esempio: un `NFA` che accetta tutte le stringhe che finiscono con $01$.

![[attachements/NFA.png]]

Data una stringa si possono trovare diverse strade distinte.

> [!question] Che percorso prende la stringa?

L'automa calcola ***tutti i possibili percorsi*** per trovarne almeno una che consenta di:
- *Consumare* tutta la stringa
- Finire in uno *stato di accettazione*

> Esempio: $00101$

![[attachements/NFAPaths.png]]

### Definizione Formale
>[!abstract] Una `DFA` è una ***quintupla***.
> $$A=(Q,\Sigma,\delta,q_{0},F)$$

> Dove:
- $Q$ è un insieme finito di **stati**
- $\Sigma$ è un [[Linguistica#Alfabeto|alfabeto]] finito
- $\delta$ è una *funzione di transizione* da $Q\times \Sigma$ all'insieme dei sottoinsiemi di $Q$, cioè $(q,a)\mapsto Q'$ con $Q' \subseteq Q$.
- $q_{0}\in Q$ è lo **stato iniziale**
- $F\subseteq Q$ è un insieme di **stati finali** (o *stati di accettazione*)

> ***Esempio***

Dato l'`NFA` precedente:
$(\{ q_{0},q_{1},q_{2} \}, \{ 0,1 \}, \delta, q_{0}, \{ q_{2} \})$

Dove $\delta$ è la seguente *funzione di transizione*.
![[attachements/TransitionFunction.png]]

#### Dimostrazione
> [!help] Ragionamento induttivo
>

> **Base**
- $\hat{\delta}(q,\epsilon)=q$

> **Induzione**

$$
\hat{\delta}(q,xa)=\bigcup_{p\in\hat{\delta}(q,x)}\delta(p,a) 
$$


> [!abstract] Formalmente
> Il ***linguaggio accettato*** da un automa a stati finiti non deterministico $A$ è:
> $$L(A)=\{ w:\hat{\delta}(q_{0},w) \cap F\neq \emptyset\ \}$$

> [!example] Esempio

Dato il seguente diagramma di transizione:
![[attachements/NFA.png]]

Calcoliamo $\hat{\delta}(q_{0},0010)$
$$
\begin{aligned}
&\hat{\delta}(q_{0},\epsilon) = \{ \textcolor{red}{q_{0}} \} \\
&\hat{\delta}(q_{0},\textcolor{red}{\epsilon} 0) = \delta(\textcolor{red}{q_{0}},0) = \{ \textcolor{red}{q_{0}},\textcolor{red}{q_{1}} \}\\
&\hat{\delta}(q_{0},\textcolor{red}{0}0)=\delta(\textcolor{red}{q_{0}},0) \cup \delta(\textcolor{red}{q_{1}},0) =\{ q_{0},q_{1} \} \cup \emptyset = \{ \textcolor{red}{q_{0}},\textcolor{red}{q_{1}} \} \\
&\hat{\delta}(q_{0},\textcolor{red}{00}1)=\delta(\textcolor{red}{q_{0}},1) \cup \delta(\textcolor{red}{q_{1}},1) = \{ q_{0} \} \cup\{ q_{2} \} = \{ \textcolor{red}{q_{0}},\textcolor{red}{q_{2}} \}\\
&\hat{\delta}(q_{0},\textcolor{red}{001}0)=\delta(\textcolor{red}{q_{0}},0) \cup \delta(\textcolor{red}{q_{2}},0) = \{ q_{0},q_{1} \} \cup \emptyset = \{ \textcolor{red}{q_{0}},\textcolor{red}{q_{1}} \}
\end{aligned}
$$

L'insieme finale non è l'insieme vuoto, questo significa che la stringa ***non è accettata***.

## Equivalenza di DFA e NFA
---
> [!hint] Osservazione
> Per ogni `NFA` $N$ esiste un [[Automi a Stati Finiti Deterministici|DFA]] $D$, tale che $L(D)=L(N)$ e viceversa.

Uno stato di un `NFA` rappresenta un insieme di stati del `DFA` equivalenti.

> Dato un `NFA`

$$
N = (Q_{N}\Sigma,\delta_{N},q_{0},F_{N})
$$
si può costruire
$$
D = (Q_{D}\Sigma,\delta_{D},\{ q_{0} \},F_{D})
$$
tali che $L(D)\equiv L(N)$

> [!help] Dettagli della costruzione a sottoinsiemi

-  $Q_{D} = \{ S:S\subseteq Q_{N} \}$

> [!nota]
> $|Q_{D}|=2^{|Q_{N}|}$ anche se la maggior parte degli stati in $Q_{D}$ non sono raggiungibili dallo stato iniziale.

- $F_{D}=\{ S\subseteq Q_{N}:S\cap F_{N} \neq \emptyset \}$
- Per ogni $S\subseteq Q_{N}$ e $a\in \Sigma$
$$
\delta_{D}(S,a)=\bigcup_{p\in S}\hat{\delta}(p,a)
$$

> Esempio

Dato il seguente `NFA`:
![[attachements/NFA.png]]

costruiamo $\delta_{D}$ e otteniamo questa tabella delle transizioni:
![[attachements/NFAtoDFA.png]]

Possiamo notare che molti stati sono irraggiungibili, quindi possiamo scartarli.

Disegnando il diagramma:

> [!tldr] Idea
> Il prossimo stato del `DFA` è definito dall'*insieme* dato dall'***unione degli stati raggiungibili*** con una transizione del `NFA`.

1. Partendo dallo stato iniziale, creo gli stati per ciascuna delle transizioni necessarie al `DFA`.
2. Una volta elencati tutti gli stati raggiungibili, ho ottenuto il `DFA` è sufficiente rinominare i singoli stati con una qualsiasi sigla.
![[attachements/NFAtoDFAdiagram.png]]

>[!question] Come capire qual è lo stato finale?

Se in uno degli insiemi all'interno dello stato è presente uno degli stati finali dell'`NFA`.

> [!danger] Transizione non esistente
> Se da uno stato una transizione non esiste (finisce nell'insieme vuoto), allora si traduce in uno [[Automi a Stati Finiti Deterministici#Stato Pozzo|stato pozzo]].


>[!cite] Teorema 2.11
>Sia $D$ il `DFA` ottenuto da un `NFA` $N$ con la costruzione a sottoinsiemi. Allora $L(D)\equiv L(N)$

>[!cite] Teorema 2.12
>Un linguaggio $L$ è accettato da un `DFA` se e solo se $L$ è accettato da un `NFA`.

- Il numero di stati del `DFA` equivalente ad un `NFA` con $n$ stati è, nel caso peggiore pari a $2^{n}$ stati.

## Transizioni Epsilon
---
> [!abstract] Idea
> Le ***transizioni epsilon*** consentono di passare da uno stato ad un altro *senza consumare il carattere* della stringa.

Utilizzabile come una ***transizione opzionale***.

> Esempio

Un $\epsilon$-`NFA`  che ***accetta numeri decimali*** consiste di:
1. Un segno $\pm$ opzionale
2. una stringa di cifre decimali
3. Un punto decimale
4. un'altra stringa di cifre decimali

![[attachements/EpsilonTransition.png]]

> [!danger] Attenzione
> **Non è corretto** dire che viene consumato un carattere "*vuoto*" dell'alfabeto, significa precisamente che il carattere non viene consumato.

Un automa che contiene transizioni epsilon viene chiamato $\epsilon$-`NFA`.
### Definizione Formale

> [!abstract] Info
> Un $\epsilon$-`NFA` è una **quintupla** $(Q,\Sigma, \delta, q_{0},F)$ dove $\delta$ è una funzione da $Q\times (\Sigma \cup \{ \epsilon \})$ all'insieme dei sottoinsiemi di $Q$.

> Esempio
$$
E = (\{ q_{0},q_{1},\dots,q_{5} \}, \{ .,+,-,0,1,\dots,9 \},\delta,q_{0},\{ q_{5} \})
$$
![[attachements/EpsilonTransitionTable.png]]

### Epsilon Closure
> [!info] Definizione
> Le ***epsilon closure*** sono *tutti i cammini possibili* partendo da uno **stato**, utilizzando **solo transizioni epsilon**.

Chiudiamo uno stato aggiungendo tutti gli stati raggiungibili da lui tramite una sequenza $\epsilon\epsilon\dots\epsilon$.

#### Definizione Induttiva
> **Base**
- $q\in \text{ECLOSE}(q)$

> **Induzione**
- $p \in \text{ECLOSE}(q) \text{ and } r \in\delta(p,\epsilon)\implies r\in ECLOSE(q)$


>[!todo] ***Definizione induttiva*** di $\hat{\delta}$ per automi $\epsilon$-`NFA`

> **Base**
- $\hat{\delta}(q,\epsilon)=q$

> **Induzione**
$$
\hat{\delta}(q,xa)=\bigcup_{p\in\hat{\delta}(q,x)}\left( \bigcup_{t\in\hat{\delta}(p,a)}\text{ECLOSE}(t) \right)  
$$

Il linguaggio $L$ accettato è ancora definito come $\{ w:\hat{\delta}(q_{0}, w) \cap F\neq \emptyset\}$

### Equivalenza di DFA e epsilon DFA
> Dato un $\epsilon$-`NFA`

$$E=(Q_{E},\Sigma,\delta_{E},q_{0},F_{E})$$
- Costruiremo un `DFA`

$$D=(Q_{D},\Sigma,\delta_{D},q_{0},F_{D})$$
tale che $L(D)=L(E)$


> [!hint] Dettagli della costruzione
> 

- $Q_{D}=\{ S:S\subseteq Q_{E} \text{ e } S =\bigcup_{t\in\hat{\delta}(p,a)}\text{ECLOSE}(t)\}$
- $F_{D}=\{ S:S\in Q_{D} \text{ e } S \cap F_{E} \neq \emptyset\}$
- $\delta_{D}(S,a)= \bigcup_{t\in S}\left( \bigcup_{p\in\hat{\delta}(t,a)}\text{ECLOSE}(p) \right)$ 

>[!done] In breve
>

- Oltre ad avere l'*unione degli insiemi degli stati raggiungibili*, devo aggiungere anche la ***epsilon closure dello stato corrente***.

> Esempio con 

![[attachements/DecimalENFAtoDFA.png]]