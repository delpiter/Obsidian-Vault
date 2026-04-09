## Definizioni di Base
---

>[!Def] Prodotto Cartesiano
>Siano $A,B$ insiemi
>$$A\times B=\{ (a,b):a\in A, b\in B \}$$

>Nel caso $A=B$ scriveremo semplicemente $A^2$ al posto di $A\times A$
#### Esempio
>$A=\{ 1,2 \}\quad B=\{ a,3 \}$

$$
A\times B=\{ (1,a),(2,a),(1,3),(2,3) \}
$$
Il *prodotto cartesiano* si può generalizzare al caso di $n$ insiemi
>[!tip] Definizione
>Siano $A_{1},A_{2},\dots,A_{n}$ $n$ insiemi
><u>Allora</u>
>Il loro prodotto cartesiano è dato da:
>$$A_{1}\times\dots A_{n}:=\{ (a_{1},\dots,a_{n}):a_{i}\in A_{i}, \forall i=1,\dots,n \}$$

### Sequenza 
>[!Definizione]
> Ripetendo gli insiemi $A$: $\underbrace{ A\times A\times \dots\times A }_{ n \text{ volte} }$
> Scriveremo anche in questo caso $A^n$
>>[!tip] Sequenza
>>Una ***Sequenza*** finita di lunghezza $n$ di elementi di $A$ è un elemento $(a_{1},a_{2},\dots,a_{n})$ del prodotto cartesiano $A^n$
>
>Gli elementi del prodotto cartesiano $A^n$ si dicono ***sequenze*** in $A$ di ***lunghezza*** $n$

#### Esempio
> $A=\{ 1,3 \}$

- $(1,3,1,1,3)$ sequenza in $A$ di lunghezza $5$
- $(1,1)$ sequenza in $A$ di lunghezza $2$

### Insieme delle Parti
>[!Definizione]
>Sia $A$ un insieme
>Definiamo come ***insieme delle parti*** l'insieme:
>$$\mathcal{P}(A)=\{ B:B\subseteq A \}$$
>È l'insieme i cui elementi sono i sottoinsiemi di $A$, inclusi $\varnothing$ e $A$ stesso

#### Esempio
>Se $A=\{ 1,a,\pi \}$ abbiamo:

$$
\mathcal{P}(A)=\{ \varnothing,\{ 1 \},\{ a \},\{ \pi \},\{  1,a\},\{ 1,\pi \},\{ a,\pi \}, A \}
$$
>[!caution] Osservazione
>Le ***potenze cartesiane*** e ***l'insieme delle parti*** sono correlati

$$
\begin{array}
\ \varnothing \mapsto(0,0,0) \\
\{ 1 \}\mapsto(1,0,0) \\
\{ a \}\mapsto(0,1,0) \\
\{ \pi \}\mapsto(0,0,1) \\
\{  1,a\}\mapsto(1,1,0) \\
\{ 1,\pi \}\mapsto(1,0,1) \\
\{ a,\pi \}\mapsto(0,1,1) \\
A\mapsto(1,1,1)
\end{array}
$$
>*Generalizzando questo argomento:*

>[!info] Proposizione
>Se $A$ è un insieme di $n$ elementi ($|A|=n$)
><u>Allora</u>
>$\exists$ una corrispondenza biunivoca tra:
>$$\mathcal{P}(A) \iff \{ 0,1 \}^n$$
>>[!tip] Osservazione
>>$$|A^n|=|A|^n$$
>>In particolare se $A=\{ 0,1 \} \to |\{ 0,1 \}^n|=|\{ 0,1 \}|^n=2^n$
>>Quindi se $B$ è tale che $|B|=n$ allora $|\mathcal{P}(B)|=|\{ 0,1 \}^n|=2^n$

>[!caution] Osservazioni
>1. Se $A$ e $B$ sono in corrispondenza biunivoca $\implies |A|=|B|$
>2. Sia $f:A\to B$ si dice che $f$ è $k$ a $1$ se:
>	1. $f$ è suriettiva
>	2. $|f^-1(B)|=k$ La *controimmagine* di $B$ ha $k$ elementi
>
>Se esiste $f:A\to B \quad k\text{ a } 1$ allora $|A|=k|B|$

## Prodotto Condizionato
---
>[!Definizione]
>Diciamo che $S$ è un ***prodotto condizionato*** di tipo $(a_{1},a_{2},\dots,a_{n})$ se soddisfa queste condizioni:
>1. La prima coordinata di un elemento di $S$ si può scegliere in $a_{1}$ modi
>2. La seconda coordinata di un elemento di $S$ si può scegliere in $a_{2}$ modi
>3. $\dots$
>4. La $n$-*esima* coordinata di un elemento di $S$ si può scegliere in $a_{n}$
 modi

>Osserviamo che se $S$ è un prodotto condizionato di tipo $(m,n,r)$ allora la [[../0 - Introduzione#Cardinalità|cardinalità]] di $S$: $\mid S\mid = m\cdot n\cdot r$

#### Esempio
>Consideriamo $S=\{ (a,b,c):a,b,c\in \mathbb{N},\quad a\leq 10 ,\ 0\leq b-a\leq 10,\ 0\leq c-a-b\leq 10\}$

Posso scegliere la coordinata $a$ in $11$ modi
- da $0$ a $10$

Posso scegliere la coordinata $b$ in $11$ modi
- In base al valore di $a$: se $a=2 \implies 2\leq b\leq 12$

Posso scegliere la coordinata $c$ in $11$ modi
- In base ai valori di $a$ e $b$

>[!done] $S$ è un prodotto condizionato di tipo $(11,11,11)$
>$|S|=11^3=1331$

## Disposizioni
---
>[!Definizione]
>Sia $A$ un insieme, una ***disposizione*** in $A$ di ***lunghezza*** $n$ $(a_{1},\dots,a_{n})$ è una [[#Sequenza|sequenza]] in $A$ di ***lunghezza*** $n$ se gli elementi $a_{1},\dots,a_{n}$ sono tutti distinti tra di loro
>>[!done] In altre Parole
>>$$a_{i}\neq a_{j} \quad\forall i\neq j$$

#### Esempio
>$A=\{ 1,2,3,4,5 \}$

- $(1,5,4)\implies$ È disposizione in $A$ di lunghezza $3$
- $(1,5,1)\implies$ Non è disposizione, ma è sequenza in $A$
### Domanda
>[!question] Quante sono le disposizioni di lunghezza $n$?

>Sia $|A| = m$

$$(a_{1},a_{2},\dots,a_{n})$$
1. Posso scegliere $a_{1}$ in $m$ modi
2. Posso scegliere $a_{1}$ in $m-1$ modi
3. $\vdots$
4. Posso scegliere $a_{n}$ in $m-n+1$ modi

>[!done] Conclusione
>Le disposizioni di lunghezza $n$ in $A$ con $|A|=m$ formano un ***prodotto condizionato*** di tipo $(m,m-1,m-2,\dots,m-n+1)$
>Quindi tali disposizioni sono $m\cdot(m-1)\cdot(m-2)\cdot \dots \ \cdot (m-n+1)$
>Questo prodotto si chiama fattoriale discendente e si indica:
>$$(m)_{n}=m\cdot(m-1)\cdot(m-2)\cdot \dots \ \cdot (m-n+1)$$


#### Esempio
$(12)_{5}=12\cdot 11\cdot 10\cdot 9\cdot 8$

## Permutazioni
---
>[!Definizione]
>Una ***permutazione*** è una *particolare disposizione* di lunghezza $|A|$ in $A$
>>[!tip] Le permutazioni di $A$, se $|A|=n$ sono:
>>$$(n)_{n}=n\cdot(n-1)\cdot(n-2)\cdot \dots \ \cdot 2\cdot1=n! $$

#### Esempio
- $A=\{ 1,2,3,4,5 \}$

$$
\text{ Sono due Permutazioni}
\begin{cases}
(1,4,5,3,2) \\
(5,3,1,2,4)
\end{cases}
$$

## Combinazioni
---
>[!Definizione]
>Una combinazione di lunghezza $a$ in $A$ è un sottoinsieme di $a$ elementi
>>[!question] Sia $|A|=n$, quanti sono i sottoinsiemi con $a$ elementi?
>
>>[!tip] Proposizione
>>Siano $a,b>0:a+b=n$ Allora abbiamo una corrispondenza biunivoca tra:
>>- Sottoinsiemi di $\{ 1,2,\dots,n \}$ con $a$ elementi
>>- Sequenze binarie con $a$ volte $1$ e $b$ volte $0$
>>- Sequenze binarie con $a$ volte $0$ e $b$ volte $1$
>>- Sottoinsiemi di $\{ 1,2,\dots,n \}$ con $b$ elementi
>>Questi insiemi hanno:
>>$$\displaystyle{\frac{(n)_{a}}{a!}}=\displaystyle{\frac{(n)_{b}}{b!}}=\displaystyle{\frac{n!}{a!b!}}$$

### Dimostrazione
$$
\begin{array}
\ \{ 1,2,3 \} \iff (1,1,1,0,0) \iff (0,0,0,1,1)\iff\{ 4,5 \} \\
\vdots \\
\{ 2,3,5 \}\iff(0,1,1,0,1)\iff(1,0,0,1,0)\iff\{ 1,4 \} \\
\vdots
\end{array}
$$
>[!tip] Osservazione
>Osserviamo che esiste una funzione che va dalle [[#Disposizioni]] di lunghezza $a$ ai sottoinsiemi con $a$ elementi
>- La funzione $f$ è $a! \text{ a }1$ perché ad ogni sottoinsieme con $a$ elementi *corrispondono le permutazioni* dei suoi elementi

Quindi il numero di sottoinsiemi con $a$ elementi è uguale al numero di disposizioni di lunghezza $a$ diviso $a!$
$$
\displaystyle{\frac{(n)_{a}}{a!}}
$$
>Inoltre

$$
\displaystyle{\frac{(n)_{a}}{a!}}=\displaystyle{\frac{n\cdot(n-1)\cdot\ \dots\ \cdot(n-a+1)}{a!}}=\displaystyle{\frac{n\cdot(n-1)\cdot\ \dots\ \cdot(b+1)}{a!}}\cdot \displaystyle{\frac{b(b-1)\cdot \ \dots \ \cdot1}{b(b-1)\cdot \ \dots \ \cdot1}}=\displaystyle{\frac{n!}{a!b!}}
$$

>[!caution] Coefficiente Binomiale
>Questo numero: $\displaystyle{\frac{(n)_{a}}{a!}}=\displaystyle{\frac{(n)_{b}}{b!}}=\displaystyle{\frac{n!}{a!b!}}$ si indica con: $\displaystyle\binom{n}{a}=\displaystyle\binom{n}{b}=\displaystyle\binom{n}{a\ b}$
>[[../../Definizioni/Definizioni_Analisi#Coefficiente Binomiale|Coefficiente Binomiale]]
>>[!done] Interpretazione Letterale
>>$\displaystyle\binom{n}{m}$ sarebbe come dire, scelgo $m$ elementi, scelti da un insieme di $n$ elementi

### Tipi di Combinazione
>[!Definizioni]
>>[!tip] $(a,b)$
>>Una combinazione di tipo $(a,b)$ in $A$, con $|A|=n=a+b$ è una coppia ordinata di sottoinsiemi di $A$ $(S,T)$ con $|S|=a\quad|T|=b$
>>$$S\cup T=A$$
>
>>[!hint] $(a,b,c)$
>>Una combinazione di tipo $(a,b,c)$ in $A$, con $|A|=n=a+b+c$ è una coppia ordinata di sottoinsiemi di $A$ $(S,T,U)$ con $|S|=a\quad|T|=b\quad |U|=c$
>>$$S\cup T \cup U=A$$
>>>[!done] Formula
>>>Le combinazioni di tipo $(a,b,c)$ sono:
>>>$$\binom{n}{a \ b\ c}= \displaystyle{\frac{n!}{a!b!c!}}$$

#### Dimostrazione
>Sfruttando il concetto di [[#Prodotto Condizionato]]

$S$ è un qualunque sottoinsieme con $a$ elementi $\implies \displaystyle\binom{n}{a}$  *scelte possibili*
- Una volta scelto $S$, l'insieme $T$ è un sottoinsieme con $b$ elementi dei rimanenti $n-a \implies \displaystyle\binom{n-a}{b}$ *scelte possibili*
- Una volta scelti $S$ e $T$, $U$ a questo punto è ***univocamente determinato***

>[!done] Complessivamente Abbiamo:
>$$\binom{n}{a}\cdot\binom{n-a}{b}=\displaystyle{\frac{n!}{a!\cancel{ (n-a)! }}}\cdot \displaystyle{\frac{\cancel{ (n-a)! }}{b!\underbrace{ (n-a-b)! }_{ c }}}=\displaystyle{\frac{n!}{a!b!c!}}$$
#### Esempio
> ***Gianluca*** deve distribuire 10 biglietti (3 in un  concerto, 4 in un secondo e 3 in un terzo) ai suoi 10 amici

>[!question] In quanti modi può fare le scelte??

$A=\{ 1,2,3,\dots,10 \}$

- $(\{ 1,3,6 \},\{ 2,5,8,9 \},\{ 4,7,10 \})$ è una combinazione di tipo $(3,4,3)$

Tutte le combinazioni di tipo $(3,4,3)$ sono:
$$
\binom{10}{3 \ 4\ 3}= \displaystyle{\frac{10!}{3!4!3!}}=10\cdot2 \cdot 7\cdot 6 \cdot 5
$$

>[!tldr] Osservazione
>Le combinazioni di tipo $(a,b,c)$ sono in biezione con le sequenze ternarie, cioè con coefficiente $0,1,2$ in cui $2$ compare $a$ volte, $1$ compare $b$ volte e $0$ compare $c$ volte

#### Esempio
>Sia $A=\{ 1,2,3,\dots,9 \}$ e siano $a=2 \quad b=3\quad c=4$

Una combinazione può essere:
$$
(\{ 1,8 \},\{ 2,6,9 \},\{ 3,4,5,7 \}) \iff(2,1,0,0,0,1,0,2,1)
$$

>[!hint] Questa corrispondenza ci permette di calcolare il numero di anagrammi di una parola data

##### Esempio
>Sia "***ATTATTOTTOA***" una parola data

>[!question] Quanti anagrammi ha?

- $3$ A
- $6$ T
- $2$ 0

>[!done] Gli anagrammi sono $$\binom{11}{3\ 6\ 2}$$


#### Proprietà
>Siano $a,b,c: a+b+c = n$

$$
\binom{n}{a\ b\ c}=\binom{n-1}{a-1\ \ \ b\ \ \ c} +\binom{n-1}{a\ \ \ b-1\ \ \ c}+\binom{n-1}{a\ \ \ b\ \ \ c-1} 
$$
##### Dimostrazione
- $A=\{ 1,2,3,\dots,n \}$

>[!question] Quante sono le combinazioni $(S,T,U)$ di tipo $(a,b,c):n\in S$?

Fissando un valore in uno dei $3$ insiemi
- $\displaystyle\binom{n-1}{a-1 \ \ \ b\ \ \ c}$

---
Se abbiamo 2 indici:
$$
\binom{n}{a\ b}=\binom{n-1}{a-1 \ \ \ b}+\binom{n-1}{a \ \ \ b-1} = \binom{n}{a}=\binom{n-1}{a-1}+\binom{n-1}{a}
$$

### Numeri di Fibonacci

>[!info] Definizione
>$F_{n}=$ è il numero di sequenze binarie di lunghezza $n$ in cui non ci sono due "$1$" consecutivi

- $F_{1}=2\implies \quad 0\quad 1$
- $F_{2}=3\implies\quad 00\quad 01 \quad 10 \quad \cancel{ 11 }$
- $\vdots$
#### Formule per $F_{n}$

>[!tip] Definizione
>$F_{n,k}=$ numero di sequenze binarie di lunghezza $n$ senza "$1$" consecutivi e con esattamente $k$ volte "$1$"

##### Esempio
- $F_{4,2}=3: \quad 0101 \quad 1001\quad 1010$
- $F_{4,3} = 0:\quad\cancel{  }$

>[!caution] Osservazione
>$$F_{n}=\sum_{k\geq 0}F_{n,k}$$

Adesso vogliamo trovare una formula per $F_{n,k}$

##### Esempio
Dopo il primo $1$ c'è sempre uno $0$
- Così anche per il secondo $1$

Dopo il terzo $1$ non sappiamo cosa segue
- $0010101$
- $1001001$
- $0100101$
- $1010100$
- $\vdots$

Sostituiamo le prime due coppie di $10$ e otteniamo:
- $00111$
- $10101$
- $01011$
- $11100$
- $\vdots$

Possiamo notare che è possibile tornare indietro alla sequenza originale:
- $11010 \iff 1010010$

>[!hint] Osservazione
>Abbiamo trovato una corrispondenza biunivoca:
>- $11010 \iff 1010010$
>- Sequenze binarie lunghe $5$ con $3$ uno e $F_{7,3}$

>[!done] In generale
>$$F_{n,k}=\binom{n-k+1}{k}$$
>- Quindi
>$$F_{n}=\sum_{k\geq 0} F_{n,k}=\sum_{k\geq 0}\binom{n-k+1}{k}$$

###### Esempio
$$
F_{8}=\sum_{k\geq 0}\binom{8-k+1}{k}=\binom{9}{0}+\binom{8}{1}+\binom{7}{2}+\binom{6}{3}+\binom{5}{4}=55
$$

>[!question] Quante sono le sequenze binarie lunghe $n$ senza $1$ consecutivi che finiscono con $0$?

- $\underbrace{ \_\ \_\ \_\ \_\ \_\ \_\ \_\ \_\ \_\ \_\ \_\ \_ }_{ F_{n-1} } \underline{0}$

>[!question] Quante sono quelle che finiscono con $1$?

- $\underbrace{ \_\ \_\ \_\ \_\ \_\ \_\ \_\ \_\ \_\ \_\ \_ }_{ F_{n-2} } \underline{0}\ \underline{1}$

>[!done] In conclusione $F_{n}=F_{n-1}+F_{n-2}$

