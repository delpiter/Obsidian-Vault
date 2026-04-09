## Insieme
>[!tip] Definizione
>Collezione di elementi finita o infinita
> - Deve essere possibile descrivere un criterio che permette di decidere senza alcun dubbio se un qualunque elemento fa o no parte del raggruppamento.
- Rappresentati con lettere maiuscole
	- $A, B, C, ...$
- Elementi
 - Oggetti dell'insieme
	- Rappresentati con le lettere minuscole
		- $a, b, c,...$
- Gli [[Insiemi/Insiemi Numerici]] sono particolari insiemi infiniti
#### Modi per identificare insiemi
###### Se è finito...
È possibile scriverlo tutto
$$A=\{1, 27, -5, 2\}$$
###### ... altrimenti
È possibile identificarlo scrivendo la proprietà che descrive l'insieme
- Che soddisfa la condizione
$$A=\{2,3,4\} = \{n\in \mathbb{N} | 2\leq n\leq4\}$$
- Permette di descrivere insiemi infiniti
$$A=\{2,3,4\} = \{n\in \mathbb{N} | n\geq 2\}$$

#### Simboli
###### Insieme vuoto
- $\varnothing$
###### Appartenenza
- $\in$
- fra elemento e insieme
	- $a \in A$
###### Non Appartenenza
- $\notin$
###### Inclusione
- Dati due insiemi $A$ e $B$ dico che $A\subseteq B$ (è incluso) se tutti gli elementi di $A$ sono inclusi anche in $B$
	- Strettamente incluso
	- $\subsetneq$
###### Differenza fra insiemi
- $A\setminus B$  contiene tutti gli elementi in $A$ che non appartengono a $B$
 $$A\setminus B=\{a\in A | a\notin B\}$$
 - $A\setminus B \neq B\setminus A$
###### Unione
- Dati due insiemi $A$ e $B$ l'unione fra i due è un insieme che contiene tutti gli elementi sia in $A$ che in $B$ 
$$A\cup B = \{c\in A \vee c\in B\}$$
###### Intersezione
- Dati due insiemi $A$ e $B$ l'intersezione fra i due è un insieme che contiene solamente gli elementi comuni
$$A\cap B = \{c\in A \wedge c\in B\}$$
###### Insiemi disgiunti
- Sono insiemi disgiunti due insiemi con intersezione vuota
$$A,B\space insiemi\space disgiunti \iff A\cap B = \varnothing$$
###### Differenza Simmetrica
- Insieme che contiene tutti gli elementi che non sono comuni ai due insiemi
$$A\triangle B=(A\setminus B) \cup (B\setminus A)$$
$$A\triangle B=(A\cup B) \setminus (B\cap A)$$
###### Prodotto
- Dati due insiemi $A$ e $B$ il prodotto fra i due è l'insieme delle coppie ordinate
$$A\times B = \{(a,b)|a\in A \wedge b\in B\}$$
$$A\times B \neq B\times A$$
## Quantificatori
- - -
- Per ogni
	- $\forall$
- Esiste
	- $\exists$
- Non esiste
	- $\nexists$
- Esiste ed è unico
	- $\exists !$
###### Es
$$\forall \space x \in \mathbb{N}, \exists \space y \in \mathbb{N} : y>x$$
$$\forall \space x \in \mathbb{N}, \exists !\space y \in \mathbb{N} : y=2x$$
## Definizioni e Proposizioni
- - -
#### Definizione
- Quando si introduce un concetto nuovo
#### Proposizione
- Affermazione della quale si può dire se è vera o falsa
###### Relazione di implicazione
$$p\Rightarrow q$$
- $q$ e $p$ sono proposizioni
	- Il fatto che la proposizione $p$ è vera implica che anche $q$ è vera
	- se $q$ è vera non posso dire nulla su $p$
	- se $q$ è falsa allora $p$ è sicuramente falsa
	- se $p$ è falsa non posso dire nulla su $q$
- Nel caso in cui contemporaneamente $p \Rightarrow q$ e $q \Rightarrow p$  diciamo che $p$ e $q$ sono equivalenti
	- $p$ è vera ***se e solo se*** $q$ è vera
$$p \Leftrightarrow q$$
## Teorema
- - -
#### Enunciato
- Fatto da 2 parti
###### Ipotesi
- Quello che assumo che sia vero
###### Tesi
- Quello che voglio verificare che sia vero

#### Dimostrazione
- Processo di deduzione che, partendo da premesse assunte come valide (ipotesi), determina la necessaria validità di una nuova proposizione in virtù della correttezza formale del ragionamento

[[Tipologie di Dimostrazioni]]