## Deterministic Finite Automaton
---
> [!hint] Definizione
>  Un ***automa a stati finiti deterministico*** (`ASFD`) o *deterministic finite automaton* (`DFA`) è un *automa* a stati finiti dove per ogni coppia di stato e simbolo in ingresso c'è una ed una sola transizione allo stato successivo.

Si dice deterministico se e solo se da ogni stato c'è una e una sola transizione uscente con ciascuno dei caratteri dell'alfabeto.

Una `DFA` è una ***quintupla***.
$$
A=(Q,\Sigma,\delta,q_{0},F)
$$
> Dove:
- $Q$ è un insieme finito di **stati**
- $\Sigma$ è un [[Linguistica#Alfabeto|alfabeto]] finito
- $\delta$ è una *funzione di transizione* da $Q\times \Sigma$ a $Q$ cioè $(q,a)\mapsto p$
- $q_{0}\in Q$ è lo **stato iniziale**
- $F\subseteq Q$ è un insieme di **stati finali** (o *stati di accettazione*)


> [!tldr] Idea
> Un ***automa a stati finiti*** accetta una stringa $w=a_{1}a_{2}\dots a_{n}$ se esiste un cammino nel diagramma di transizione che:
> - Inizia nello *stato iniziale*
> - Finisce in uno *stato finale*
> - Ha una *sequenza di etichette* $a_{1}a_{2}\dots a_{n}$

> [!done] A parole
> Data una qualsiasi stringa di un alfabeto $\Sigma$, l'automa "*cammina*" nel grafo degli stati.
> Se una volta percorsa tutta la stringa termina in uno *stato di accettazione*, la stringa è considerata valida. 

> Esempio
- Un automa $A$ che accetta $L=\{ x 01y:x,y\in\{ 0,1 \}^{*} \}$
- L'automa $A=(\{ q_{0},q_{1},q_{2} \},\{ 0,1 \},\delta, q_{0},\{ q_{1} \})$, definito tramite la **tabella di transizione**:
![[attachements/TransitionTable.png]]


O più semplicemente definito dal seguente **diagramma di transizione**:
![[attachements/TransitionDiagram.png]]

### Dimostrazione
> [!help] Ragionamento Induttivo
> La ***funzione di transizione*** $\delta$ può essere estesa a $\hat{\delta}$ che opera su stati e stringhe. 

> **Base**
- $\hat{\delta}(q,\epsilon)=q$
> **Induzione**
- $\hat{\delta}(q,xa)=\delta(\hat{\delta}(q,x)a)$

> [!abstract] Formalmente
> Il ***linguaggio accettato*** da un automa a stati finiti deterministico $A$ è
> $$L(A)=\{ w:\hat{\delta}(q_{0},w)\in F \}$$

I linguaggi accettati da automi a stati finiti sono detti *linguaggi regolari*.


> [!example] Esempio
>

Dato il seguente diagramma di transizione:
![[attachements/TransitionDiagram.png]]

Calcoliamo $\hat{\delta}(q_{0},0110)$:

$$
\begin{aligned}
	&\hat\delta\left(q_0,\epsilon\right) = q_0 \\
	&\hat\delta\left(q_0, \textcolor{red}{\epsilon}0\right) = \delta\left(\underbrace{\hat\delta{(q_0,\epsilon)}}_{\textcolor{red}{q_0}}, 0\right) = \delta\left(q_0, 0\right) = \textcolor{red}{q_2} \\
	&\hat\delta\left(q_0, \textcolor{red}{0}1\right) = \delta\left(\underbrace{\hat\delta\left(q_0,0\right)}_{\textcolor{red}{q_2}}, 1\right) = \delta\left(q_2, 1\right) = \textcolor{red}{q_1} \\
	&\hat\delta\left(q_0, \textcolor{red}{01}1\right) = \delta\left(\underbrace{\hat\delta\left(q_0,01\right)}_{\textcolor{red}{q_1}}, 1\right) = \delta\left(q_1, 1\right) = \textcolor{red}{q_1} \\
	&\hat\delta\left(q_0, \textcolor{red}{011}0\right) = \delta\left(\underbrace{\hat\delta\left(q_0,011\right)}_{\textcolor{red}{q_1}}, 0\right) = \delta\left(q_1, 0\right) = \textcolor{red}{q_1} \\
\end{aligned}
$$
