## Equivalenza di PDA e CFG
---
>[!summary] Equivalenza
> Un ***linguaggio è generato*** da una [[Grammatiche e Linguaggi Liberi dal contesto|CFG]] $\iff$ è accettato da una `PDA` per pila vuota $\iff$ è accettato da un `PDA` per stato finale.

Sappiamo già andare da pila vuota a stato finale.
![[attachements/PDAGrammarEquivalence.png]]

### Da CFG a PDA
> [!tldr] Idea
> ***Trasformazione a 2 passi*** partendo da un automa con *un unico stato*:
> 1. Prendo tutte le produzioni e le trasformo in autocicli
> 2. Per ciascun carattere terminale, creo una transizione che consuma il carattere sia dall'input che dalla pila (sostituisce con $\epsilon$)

> Esempio:
1. Sia $S\to Sx$ una ***produzione della grammatica***, la transizione equivalente del `PDA` sarà: $\epsilon,S/Sx$
	- Non consumo un carattere, richiedo una variabile $S$ in cima alla pila e lo sostituisco con il risultato della produzione. 
2. Se $x$ è un ***terminale della grammatica***, quando lo incontro sia sulla pila che nell'input, lo consumo e lo rimuovo dalla pila.
	- Devo aggiungere un *autociclo* con transizione $x,x/\epsilon$.

> Data una grammatica $G$ costruiamo un `PDA` che simula una ***derivazione canonica sinistra*** $\overset{*}{\underset{ lm }{ \implies }}$.

Sia $w$ la stringa data in input al `PDA` e $y$ tale che $w=xy$, allora il `PDA` va ***non deterministicamente*** dalla configurazione $(q,y,A\alpha)$ alla configurazione $(q,y,\beta\alpha)$
- Alla configurazione $(q,y,\beta\alpha)$ il `PDA` si comporta come prima, a meno che ci siano terminali nel prefisso di $\beta$.
- In questo caso il `PDA` li elimina se li legge nell'input (fanno *match*).

>[!done] Se tutte le scommesse sono giuste, il `PDA` finisce l'input con la pila vuota
#### Definizione Formale
> [!cite] Definizione
> Sia $G=(V,T,Q,S)$ una `CFG` definiamo $P_{G}$ come:
> $$(\{ q \},T,V\cup T,\delta,q,S)$$

Dove:
- $\delta(q,\epsilon,A)=\{ (q,\beta):A\to \beta \in Q\}$ per $A\in V$
- $\delta(q,a,a)=\{ (q,\epsilon) \}$ per $a\in T$

## Equivalenza da PDA a CFG
---
> Mostriamo ora l'esistenza di una `CFG` il cui linguaggio è lo stesso linguaggio $P$ che accetta per pila vuota.

> [!tldr] Idea
> L'***evento fondamentale*** nella storia del processo di un input in un `PDA` è il ***pop*** di un simbolo dalla pila ***consumando un certo input***.


> [!quote] A parole
> Parto da uno stato $q$ e con $Y$ in cima alla pila, ho una transizione $a,Y/Y_{1}Y_{2}\dots Y_{k}$ che mi porta in $p_{0}$
> L'obbiettivo è quello di ***eliminare interamente*** $Y$ dalla pila.

Per ogni carattere $Y_{i}$ aggiunto dovrò applicare lo stesso ragionamento prede

![[attachements/PDAtoCFG.png]]

La figura suggerisce come possiamo fare il "*pop*" di una sequenza di simboli $Y_{1},\dots,Y_{k}$ dalla pila.
- $x_{1}$ rappresenta l'input consumato dall'automa in un cammino che rimuove completamente $Y_{1}$ dalla pila.

> [!hint] Osservazione
> La rimozione di $Y_{1}$ è l'effetto di ***diverse azioni***.

> Per esempio 
- La prima mossa cambia $Y_{1}$ in un altro simbolo $Z$
- Poi viene rimpiazzato $Z$ con $UV$
- Altre mosse successive hanno l'effetto di rimuovere $U$ e poi $V$
- L'***effetto finale*** è stato sostanzialmente la rimozione di $Y_{1}$.

Osserviamo anche che dopo la rimozione di $Y_{1}$ finiamo nello stato $p_{1}$

Questa computazione continua fino alla rimozione di ciascuno dei simboli dello stack.

La costruzione di una grammatica equivalente usa variabili (*triple*: $[pXq]$) che rappresentano un "***evento***" che consiste in:
1. La rimozione di un simbolo $X$ dallo stack
2. Il cambiamento di stato da uno stato $p$ a uno stato $q$ quando $X$ viene rimpiazzato da $\epsilon$ nello stack.
### Definizione formale
> [!cite] Teorema
> Sia $P=(Q,\Sigma,\Gamma,\delta,q_{0},Z_{0})$ un `PDA`.
> Allora esiste una `CFG` $G$ tale che $L(G)=N(P)$

#### Dimostrazione
> Costruiamo $G=(V,\Sigma,R,S)$ dove l'insieme delle variabili $V$ consiste di:

1. Il simbolo $S$, *simbolo iniziale*
2. Tutti i simboli della forma $[pXq]$, dove $p$ e $q$ sono stati in $Q$ e $X$ è un simbolo dello stack in $\Gamma$

Le ***produzioni*** di $G$ si definiscono come di seguito:
1. Per tutti gli stati $p$, $G$ ha una produzione $S\to[q_{0},Z_{0},p]$ che genera tutte le stringhe $w$ che causano la rimozione di $Z_{0}$ dalla pila mentre passa dallo stato $q_{0}$ allo stato $p$.

> [!hint] Formalmente: $(q_{0},w,Z_{0})\vdash^{*}(p,\epsilon,\epsilon)$.
> Queste produzioni indicano che il simbolo iniziale $S$ ***genera tutte le stringhe*** $w$ che portano $P$ a ***svuotare la pila*** partendo dalla sua `ID` iniziale.

2. Sia $(r,Y_{1}Y_{2}\dots Y_{k})\in\delta(q,a,X)$ dove:
	- $a\in\Sigma\cup\{ \epsilon \}$
	- $k$ può essere un qualsiasi numero, anche $0$.

Allora per tutte le liste di stati $r_{1},r_{2},\dots,r_{k}$, $G$ ha la **produzione**:
- $[qXr_{k}]\to a[rY_{1}r_{1}][r_{1}Y_{2}r_{2}]\dots[r_{k-1}Y_{k}r_{k}]$

> [!hint] Idea
> Questa produzione indica che ***un modo di rimuovere*** $X$ e passare da uno stato $q$ a uno stato $r_{k}$ è quello di **leggere** $a$, e usare un input per **rimuovere** $Y_{1}$ dalla pila **passando dallo stato** $r$ allo **stato** $r_{1}$ e poi leggere un altro input che rimuove $Y_{2}$ dallo stack e passare da $r_{1}$ a $r_{2}$ e così via.

##### Esempio
> Convertiamo $P=(\{ p,q \}, \{ 0,1 \}, \{ X,Z_{0} \}, \delta,q,Z_{0})$  in una `CFG`dove $\delta$ è:

1. $\delta(q,1,Z_{0})=\{ (q,XZ_{0}) \}$
2. $\delta(q,1,X)=\{ (q,XX) \}$
3. $\delta(q,0,X)=\{ (p,X) \}$
4. $\delta(q,\epsilon,X)=\{ (q,\epsilon) \}$
5. $\delta(p,1,X)=\{ (p,\epsilon) \}$
6. $\delta(p,0,Z_{0})=\{ (q,Z_{0}) \}$

Otteniamo $G=(V,\{ 0,1 \},R,S)$ dove:
$$
V=\{ [qZ_{0}q],[pZ_{0}q],[qZ_{0}p],[pZ_{0}p],[qXq],[pXq],[qXp],[pXp],S \}
$$
E le produzioni in $R$ sono:
$$
S\to [qZ_{0}q]\mid [qZ_{0}p]
$$
Dalla transizione $\delta(\textcolor{blue}{q},1,Z_{0})=\{ (\textcolor{green}{q},XZ_{0}) \}$ si ha, con due generici $\textcolor{red}{p_{1}}$ e $\textcolor{red}{p_{2}}$:
$$
[\textcolor{blue}{q}Z_{0}\textcolor{red}{p_{2}}] \to 1[\textcolor{green}{q}X\textcolor{red}{p_{1}}][\textcolor{red}{p_{1}}Z_{0}\textcolor{red}{p_{2}}]\qquad \forall p_{1},p_{2}
\in Q$$
- ***Quindi***:
$$
\begin{align}{}
&[qZ_{0}q] \to 1[qXq][qZ_{0}q] \mid 1[qXp][pZ_{0}q]\\
&[qZ_{0}p] \to 1[qXq][qZ_{0}p] \mid 1[qXp][pZ_{0}p]
\end{align}
$$
Dalla transizione $\delta(q,1,X)=\{ (q,XZ_{0}) \}$ si ha:
$$
\begin{align}{}
&[qXq] \to 1[qXq][qXq] \mid 1[qXp][pXq]\\
&[qXp] \to 1[qXq][qXp] \mid 1[qXp][pXp]
\end{align}
$$

Dalla transizione $\delta(\textcolor{blue}{q},0,X)=\{ (\textcolor{green}{p},X) \}$ si ha con un generico $\textcolor{red}{p_{1}}$:
$$
[\textcolor{blue}{q}X\textcolor{red}{p_{1}}]\to 0[\textcolor{green}{p}X\textcolor{red}{p_{1}}] \qquad \forall p_{1}\in Q
$$
- ***Quindi***:
$$
\begin{align}{}
&[qXq] \to 0[pXq] \\
&[qXp] \to 0[pXp]
\end{align}
$$
Dalla transizione $\delta(q,\epsilon,X)=\{ (q,\epsilon) \}$ si ha:
$$
\begin{align}{}
&[qXq] \to \epsilon
\end{align}
$$

Dalla transizione $\delta(p,1,X)=\{ (q,\epsilon) \}$ si ha:
$$
\begin{align}{}
&[pXp] \to 1
\end{align}
$$
Dalla transizione $\delta(p,0,Z_{0})=\{ (q,Z_{0}) \}$ si ha:
$$
\begin{align}{}
&[pZ_{0}q] \to 0[qZ_{0}q] \\
&[pZ_{0}p] \to 0[qZ_{0}p]
\end{align}
$$