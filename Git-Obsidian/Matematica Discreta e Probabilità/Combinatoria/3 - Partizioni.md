## Partizioni di un Insieme
---
>[!Definizione]
>Una ***partizione*** di un insieme $A$ è una *suddivisione* di $A$ in sottoinsiemi $A_{1},A_{2},\dots$ detti ***blocchi*** della partizione
>I blocchi devono rispettare le seguenti condizioni:
>- $A_{i} \neq \varnothing \quad \forall i$
>- $A_{i}\ \cap A_{j} = \varnothing \quad \forall i\neq j$
>- $A_{1}\cup A_{2} \cup\dots = A$

![[Pasted image 20241002184937.png]]
>[!warning] L'ordine dei blocchi non è rilevante

#### Esempio

$A:\{ 1,2 \}$
- $A_{1}:\{1  \}\quad A_{2}:\{ 2 \}\implies$ Partizione a 2 ***blocchi***
- $A_{1}:\{ 1,2 \}\implies$ Partizione a 1 ***blocco***


$A:\{ 1,2,3 \}$
- 3 ***blocchi*** da 1: $\{ 1 \},\quad\{ 2 \},\quad\{ 3 \}$
- 1 ***blocco*** da 3: $\{ 1,2,3 \}$
- 3 ***partizioni*** da:
	- 1 ***Blocco*** da 2
		- $\{ 1,2 \},$
	- 1 ***Blocco*** da 1
		- $\{ 3 \}$

>[!done] Per un totale di 5 partizioni

### Generalizzazione
>[!summary] Definizione
>$\forall n \geq 0$ Poniamo:
>$B_{n}= \#$ di partizioni di $\{ 1,\dots,n \}$ se $n>0$
>- $B_{0}=1$
>>[!info] Questi numeri si dicono numeri di ***Bell***

- $B_{0}=1,\quad B_{1}=1,\quad B_{2}=2,\quad B_{3}=5$


>[!Proprietà]
>$\forall n>0 \quad B_{n}=\displaystyle\sum_{h=0}^n-1 \binom{n-1}{h}\cdot B_{h}$
>>[!question] Dove $\displaystyle\binom{n-1}{h}$ indica il numero di *gruppi* con $n$ elementi

### Dimostrazione
>Sia $a_{k}$ il numero di partizioni di $\{ 1,\dots,n \}$ in cui $n$ sta in un blocco con $k$ elementi

##### Esempio
>$n=5\quad k=3$

- $a_{k}$ è il numero di partizioni in cui $5$ sta in un *blocco* con 3 elementi
	- I blocchi contenente il $5$ saranno: $\binom{4}{2}\implies$ Fra i 4 numeri che posso scegliere, ne scelgo 2

>[!tip] Fatta questa scelta
>Rimangono $n-k$ numeri che posso partizionare a piacere: $B_{n-k}$ scelte

- $a_{k}=\displaystyle\binom{n-1}{k-1}\cdot B_{n-k}$

>[!done] $$B_{n}=\sum_{k=1}^n a_{k}=\sum_{k=1}^n\binom{n-1}{k-1}B_{n-k}$$

Con un cambio di variabile posso tornare alla *formula iniziale*
$$
\begin{array} \\
h=n-k \\
B_{n}=\displaystyle\sum_{h=0}^{n-1}\binom{n-1}{n-h-1}B_{h}= \\
=\displaystyle\sum_{h=0}^{n-1}\binom{n-1}{h}B_{h}
\end{array}
$$

#### Esempi
>$B_{4}$

$$
B_{4}=\sum_{h=0}^3\binom{3}{h}B_{h} = 1\cdot \underbrace{ B_{0} }_{ 1 }+3\cdot \underbrace{ B_{1} }_{ 1 }+3\cdot \underbrace{ B_{2} }_{ 2 }+1\cdot \underbrace{ B_{3} }_{ 5 }=1+3+6+5=15
$$
>$B_{5}$

$$
B_{5}=\sum_{h=0}^4\binom{4}{h}B_{h} = 1\cdot \underbrace{ B_{0} }_{ 1 }+4\cdot \underbrace{ B_{1} }_{ 1 }+6\cdot \underbrace{ B_{2} }_{ 2 }+4\cdot \underbrace{ B_{3} }_{ 5 }+1\cdot \underbrace{ B_{4} }_{ 15 }=1+4+12+20+15=52
$$

### Triangolo di Bell
>[!summary] Basato sulla proposizione appena dimostrata

- $1= B_{1}$
- $1\quad 2=B_{2}$
- $2\quad 3\quad 5 = B_{3}$
- $5 \quad 7\quad 10 \quad 15=B_{4}$
- $15\quad 20\quad 27 \quad 37 \quad 52= B_{5}$
- $\vdots$

>[!caution] Funzionamento
>Per ottenere un nuovo numero, basta ***sommare*** l'ultimo numero con quello che gli sta ***al di sopra***, e si inserire il risultato a ***destra***
>Quando non c'è più un numero "sopra" da sommare, si riporta l'ultimo numero come ***primo numero della nuova riga***.

### Numeri di Stirling
>[!question] Vogliamo calcolare il numero di partizioni di un insieme in un ***numero di blocchi prefissato***

#### Esempio
>$A=\{ 1,2,3,4,5 \}$

>[!question] Quante partizioni con 2 blocchi?

Fissato $5$ in uno dei due *blocchi*, gli altri numeri dello stesso blocco li posso scegliere fra:
- Un qualunque sottoinsieme di $\{ 1,2,3,4 \}$ tranne $\{ 1,2,3,4 \}$ stesso: $2^4-1=15$
- L'altro *blocco* sarà il ***complementare del sottoinsieme scelto***

>[!info] Definizione Numeri di Stirling
>$S_{n,k}$ è il numero di partizioni di $\{ 1,\dots,n \}$ in $k$ *blocchi*

#### Alcuni Valori
>$S_{5,2}=15, \quad S_{4,3} = 6$
>$S_{1,1}=1\quad S_{3,3}=1$
>$S_{n,1}=1$

>[!summary] Proposizione
>$S_{n,k}=k\cdot S_{n-1,k}+S_{n-1,k-1}$

##### Dimostrazione
>Se $n$ sta da solo

Devo partizionare gli altri $n-1$ numeri in $k-1$ blocchi:
- Ho $S_{n-1,k-1}$ scelte

>Se $n$ *non* è da solo

Partiamo da una partizione dei numeri $\{ 1,\dots,n-1 \}$ in $k$ *blocchi*
- Poi aggiungiamo $n$ ad uno dei $k$ blocchi
- Ho $S_{n-1,k}\cdot k$ scelte

#### Esempio
>$k=3 \quad n=10$

Scegliamo una partizione di $\{ 1,\dots,9 \}$ in $3$ *blocchi*
- $\{ 1,5,6,7 \},\{ 2,3 \},\{ 8,9,4 \}$
Il numero 10 può essere inserito in qualsiasi dei 3 ***blocchi***

>$S_{6,3}$

- $S_{6,3}=3\cdot S_{5,3}+\underbrace{ S_{5,2} }_{ 15 }$
- $S_{5,3}=3\cdot \underbrace{ S_{4,3} }_{ 6 }+\underbrace{ S_{4,2} }_{ 2^3-1 }=6\cdot3+7=25$
- $S_{6,3}=3\cdot25+15 = 90$


### Relazioni fra sequenze $k$-piene e partizioni
>[!info] Relazione
>Esiste una ***relazione*** fra le  [[2 - Principio di inclusione-esclusione#Sequenze $k-$piene|sequenze k-piene]] di lunghezza $n$e partizioni di $\{ 1,\dots,n \}$ in $k$ *blocchi*
>Una funzione che associa una sequenza $k$-piena

#### Esempio
>$n=6\quad k=3$

- $(1,2,3,1,2,3)\to \{ 1,4 \},\{ 2,5 \},\{ 3,6 \}$
- $\vdots$
- $(1,2,2,3,1,1)\to\{ 1,5,6 \},\{ 2,3 \},\{ 4 \}$
- $(2,1,1,3,2,2)\to \{ 1,5,6 \},\{ 2,3 \},\{ 4 \}$

>[!hint] Ogni *blocco* corrisponde agli indici di un numero nella sequenza $k$-piena
>>[!caution] Associazione $k!$ a $1$
>>A ciascuna delle partizioni corrispondono $k!$ sequenze $k$-piene
>>- $k!$ perché posso [[1 - Combinatoria Elementare#Permutazioni|permutare]] le cifre in una qualsiasi sequenza $k$-piena $(2\to3,\quad 1\to 2,\quad 3\to1)$ e ottenere un'altra sequenza $k$-piena associata alla ***stessa partizione***

>[!done] Questa funzione è $(k!$ a $1)$ e quindi:
>$$S_{n,k}=\displaystyle{\frac{\# \text{ numero di sequenze lunghe }n\ k\text{-piene}}{k!}}=\displaystyle{\frac{\sum_{i=0}^k(-1)^i\binom{k}{i}(k-i)^n}{k!}}$$
