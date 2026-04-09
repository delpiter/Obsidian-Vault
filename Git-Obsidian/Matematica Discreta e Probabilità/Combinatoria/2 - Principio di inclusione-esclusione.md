## Principio di Inclusione-Esclusione
---
>[!Info] Utilizzo
>Serve per calcolare la cardinalità di unione di insiemi

### Unione di insiemi
>Siano $A$ e $B$ due insiemi, la cardinalità di $|A\cup B|$ sarà:

$$
\mid A\cup B \mid=|A|+|B|-|A\cap B|
$$
![[attachements/Pasted image 20240928101710.png|200]]
- *L'intersezione è contata due volte, quindi viene rimossa alla fine*

>[!question] Proviamo con 3 insiemi

![[attachements/Pasted image 20240928101829.png|200]]
Eseguendo semplicemente la somma delle cardinalità otteniamo che:
$$
|A\cup B\cup C|=|A|+|B|+|C|
$$
- Le intersezioni $A\cap C$, $A\cap B$ e $B\cap C$ sono contate due volte
- L'intersezione $A\cap B \cap C$ è contata tre volte

>[!tip] Sistemiamo passo per passo

Togliamo le intersezioni fra due insiemi:
$$
|A\cup B\cup C|=|A|+|B|+|C|-|A\cap B|-|A\cap C|-|C\cap B|
$$
- Facendo così abbiamo rimosso tre volte l'intersezione centrale

Per concludere si riaggiunge l'intersezione:
$$
|A\cup B\cup C|=|A|+|B|+|C|-|A\cap B|-|A\cap C|-|C\cap B|+|A\cap B \cap C|
$$

>[!tldr] Con 4 insiemi

>Siano $A_{1},A_{2},A_{3},A_{4}$ gli insiemi

$|A_{1}\cup A_{2}\cup A_{3} \cup A_{4}|=$
- $|A_{1}|+|A_{2}|+|A_{3}|+|A_{4}|$
- $-|A_{1}\cap A_{2}|-|A_{1}\cap A_{3}|-|A_{1}\cap A_{4}|-|A_{2}\cap A_{3}|-|A_{2}\cap A_{4}|-|A_{3}\cap A_{4}|$
- $+|A_{1}\cap A_{2}\cap A_{3}|+|A_{1}\cap A_{2}\cap A_{4}|+|A_{1}\cap A_{3}\cap A_{4}|+|A_{2}\cap A_{3}\cap A_{4}|$
- $-|A_{1}\cap A_{2} \cap A_{3}\cap A_{4}|$

>[!question] Come possiamo scriverlo in generale?

### Formula
>[!done] $$\mid A_{1}\cup A_{2} \cup\dots\cup A_{n}\mid=\left| \bigcup\limits_{i=1}^{n} A_{i} \right| =\sum_{\varnothing\neq I\subseteq\{ 1,\dots,n \}}(-1)^{|I|-1}\cdot \left| \bigcap\limits_{j\in I}A_{j} \right|$$

>*$\{ 1,\dots,n \}$ sono gli indici degli insiemi*

>[!summary] A parole
>- Se il numero di insiemi in intersezione è ***dispari*** allora si **somma** la loro cardinalità
>- Se il numero di insiemi in intersezione è ***pari*** allora si ***sottrae*** la loro cardinalità

#### Esempio
>$I=\{ 2,4 \}$

$$
(-1)^{\mid\{ 2,4 \}|-1}\cdot \left|\bigcap\limits_{j\in \{ 2,4 \}}A_{j} \right|=(-1)^1\cdot|A_{2}\cap A_{4}|
$$
### Caso con Cardinalità Uguali
>Supponiamo che $\forall I\subseteq\{ 1,2,3,\dots,n \}$, $\left| \bigcap\limits_{j\in I}A_{j} \right|$ abbiano sempre la stessa cardinalità

$\left| \bigcap\limits_{j\in I}A_{j} \right|$ dipende solo dalla cardinalità di $I$, quindi diciamo che:

$$
\left| \bigcap\limits_{j\in I}A_{j} \right|=a_{|I|}
$$
>[!summary] Cioè:
>Tutti gli addendi della "***prima riga***" valgono $a_{1}$, tutti quelli della "***seconda riga***" valgono $a_{2}$ e così via

Tornando all'esempio con 4 insiemi:

$|A_{1}\cup A_{2}\cup A_{3} \cup A_{4}|=4a_{1}-6a_{2}+4a_{3}-1a_{4}$
- $=\displaystyle\binom{4}{1}a_{1}-\displaystyle\binom{4}{2}a_{2}+\displaystyle\binom{4}{3}a_{4}-\displaystyle\binom{4}{4}a_{4}$

#### Formula di principio di inclusione-esclusione con cardinalità uguali

>[!done] In generale 
>Se abbiamo $n$ insiemi $A_{1},\dots,A_{n}:\forall I  \ t.c.|I|=k$
>abbiamo:$\left| \bigcap\limits_{j\in I}A_{j} \right|=a_{k}$
>Allora
>>[!caution] $$\left| \bigcup\limits_{i=1}^{n} A_{i} \right| =\sum_{k=1}^n(-1)^{k-1}\cdot \binom{n}{k}a_{k}$$

## Scombussolamento
---
>[!Definizione]
>Uno ***scombussolamento*** è una permutazione dei numeri $\{ 1,\dots,n \}$ in cui ***nessun numero rimane al suo posto***
>>[!caution] Come calcolarlo
>>Per calcolare gli *scombussolamenti*, calcoliamo i ***non*** *scombussolamenti* e poi togliamo il risultato ottenuto a tutte le possibili permutazioni ($n!$)

>Siano:

- $A_{1}=\{$Permutazioni con $1$ al suo posto$\}$
- $A_{2}=\{$Permutazioni con $2$ al suo posto$\}$
- $\vdots$

>[!tldr] Osservazione
>Gli scombussolamenti sono il complementare di: $|A_{1}\cup A_{2}\cup \dots\cup A_{n}|$

Utilizzando la [[#Formula di principio di inclusione-esclusione con cardinalità uguali|formula]] di prima:
- $a_{1}=(n-1)! =|A_{i}| \forall i$

- $A_{1}\cap A_{2}=\{$Permutazioni con $1$ e $2$ al suo posto$\}$
- $\vdots$

$|A_{1}\cap A_{2}|=(n-2)!=|A_{3}\cap A_{6}| =\dots$

>[!done] In conclusione i non scombussolamenti sono:
>

$$\sum_{k=1}^n(-1)^{k-1}\cdot\binom{n}{k}\cdot(n-k)! =\sum_{k=1}^n(-1)^{k-1}\cdot \displaystyle{\frac{n!}{k!}}$$
>[!caution] Quindi gli scombussolamenti sono:

$$
n!-\sum_{k=1}^n(-1)^{k-1}\cdot \displaystyle{\frac{n!}{k!}}=\displaystyle{\frac{n!}{0!}}+\sum_{k=1}^n(-1)^{k\cancel{ -1 }}\cdot \displaystyle{\frac{n!}{k!}}=
$$
>[!done] Formula Semplificata
>$$\sum_{k=0}^n(-1)^{k}\cdot \displaystyle{\frac{n!}{k!}}$$

#### Esempio
> Per $n=4$

$$
\sum_{k=0}^4(-1)^k \displaystyle{\frac{4!}{k!}}=\displaystyle{\frac{4!}{0!}}-\displaystyle{\frac{4!}{1!}}+\displaystyle{\frac{4!}{2!}}-\displaystyle{\frac{4!}{3!}}+\displaystyle{\frac{4!}{4!}}=24-24+12-4+1=9
$$
>[!hint] Osservazione
>I primi due addendi saranno sempre opposti fra di loro, quindi si potrebbe semplificare ulteriormente facendo partire $k$ da $2$

## Sequenze $k-$piene
---
>[!Definizione]
>Le ***sequenze $k-$piene*** sono le sequenze in cui compaiono tutti i numeri da $1$ a $k$ almeno una volta

>[!question] Fissiamo la lunghezza $n\geq k$, quante sono le ***sequenze $k-$piene***?

### Procedimento
>Consideriamo come universo l'insieme delle sequenze lunghe $n$ in $\{ 1,\dots,k \}$

In totale sono $k^n$ sequenze:
Chiamiamo:

- $A_{1}=\{$Sequenze in cui non appare $1$$\}$
- $A_{2}=\{$Sequenze in cui non appare $2$$\}$
- $\vdots$
- $A_{k}=\{$Sequenze in cui non appare $k$$\}$

>[!tldr] Osservazione
>Le sequenze $k-$piene sono il complementare di $A_{1}\cup A_{2} \cup\dots\cup A_{k}$

- $|A_{1}|=(k-1)^n=|A_{2}|=\dots=|A_{k}|$

Chiamiamo:
- $A_{1}\cap A_{2}=\{$Sequenze in cui non appare ne $1$ ne $2$$\}$
- $\vdots$

- $|A_{1}\cap A_{2}| = (k-2)^n$

>[!done] Conclusione
>Le sequenze $k-$piene sono:

$$
k^n-\sum_{j=1}^k(-1)^{j-1}\cdot \binom{k}{j}(k-j)^n=k^n+\sum_{j=1}^k(-1)^{j\cancel{ -1 }}\cdot \binom{k}{j}(k-j)^n
$$
$$
=\sum_{j=0}^k(-1)^{j}\cdot \binom{k}{j}(k-j)^n
$$
#### Esempio
>Sequenze di lunghezza $4$, $3-$ piene

$$
\begin{array}
\ \displaystyle\sum_{j=0}^3(-1)^j\cdot\binom{3}{j}\cdot(3-j)^4= \\
=\displaystyle\binom{3}{0}3^4-\binom{3}{1}2^4+\binom{3}{2}1^4-\binom{3}{3}0^4= \\
=81-48+3-0=36
\end{array}
$$