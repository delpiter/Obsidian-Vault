## Linguaggi Regolari
---
![[Linguistica#Linguaggio Formale]]

### Operazioni sui Linguaggi
> [!help] Unione

$$
L\cup M = \{ w:w\in L, \ w \in M \}
$$
- Tutte le stringhe dei linguaggi $L$ e $M$.

> [!caution] Concatenazione
> 

$$
L.M=\{ w:w=xy, x\in L, y\in M \}
$$
- Tutte le stringhe che si possono ottenere dalla concatenazione di una qualsiasi stringa di $L$ e una qualsiasi stringa di $M$.


> [!hint] Potenze
> 

$$
L^{0}=\{ \epsilon \},\ L^{1}=L,\ L^{k+1}=L.L^{k}
$$
- Concateno un linguaggio con se stesso un numero $k$ di volte.


> [!end] Chiusura di Kleene

$$
L^{*} =\bigcup_{i\geq 0} L^{i}
$$
- Tutte le stringhe che posso ottenere concatenando un numero arbitrario di volte una qualsiasi stringa di $L$.


> [!tip] Chiusura Positiva
> 

$$
L^{+}=LL^{*}=L^{*}L\qquad L^{*}=L^{+}\cup\{ \epsilon \}
$$
### Leggi algebriche per i Linguaggi
> [!todo] Unione
> L'unione è ***commutativa*** e ***associativa***

- $L\cup M=M\cup L$
- $(L\cup M) \cup N = L\cup(M\cup N)$

> $\emptyset$ è l'***identità*** (*elemento neutro*) per l'unione

> [!caution] Concatenazione
> La concatenazione è ***solo associativa***

- $(LM)N=L(MN)$

> $\{ \epsilon \}$ è l'identità sinistra e destra per la concatenazione

> $\emptyset$ è l'***annihilator*** sinistro e destro per la concatenazione.


> [!done] Proprietà comuni

- La concatenazione è distributiva a *sinistra* e *destra* sull'unione.
	- $L(M\cup N)=LM \cup LN$
	- $(M\cup N)L=ML \cup NL$
