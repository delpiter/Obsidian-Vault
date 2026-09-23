## Linguistica Formale
---
> Un linguaggio naturale/di programmazione è un insieme di lessico e sintassi.

> [!help] Lessico
> Il ***lessico*** è un insieme di regole per formare le singole parole di un linguaggio.

> [!caution] Sintassi
> La ***sintassi*** è un insieme di regole da seguire per creare una frase completa e ammissibile.

### Concetti di Base
#### Alfabeto
> [!hint] Definizione
> Un ***alfabeto*** è un insieme finito e non vuoto di simboli e viene indicato con il simbolo $\Sigma$.

> Esempi
- $\Sigma = \{ 0,1 \}$  è un **alfabeto binario**.
- $\Sigma = \{ a,b,c, \dots, z \}$ insieme di tutte le **lettere minuscole**.

#### Stringa
> [!abstract] Definizione
> Una ***stringa*** è una sequenza finita di simboli da un *alfabeto* $\Sigma$.

In qualsiasi alfabeto esiste la ***stringa vuota***
- Una stringa con *zero occorrenze* di simboli da $\Sigma$, la stringa vuota si denota con $\epsilon$

> Esempio
- $100101001$ è una stringa su alfabeto $\{ 0,1 \}$

##### Lunghezza di una stringa
> [!caution] Definizione
> La ***lunghezza di una stringa*** è il numero di posizioni per i simboli dell'alfabeto nella stringa.

Si indica la lunghezza di una stringa $w$ come: $|w|$

> Esempio
- $\mid0110\mid=4, \mid\epsilon\mid = 0$

##### Potenza di un Alfabeto
> [!todo] Definizione
> La ***potenza di un alfabeto*** $\Sigma^{k}$ è l'insieme delle stringhe di lunghezza $k$ con simboli da $\Sigma$.

> Esempio
- $\Sigma=\{ 0,1 \} \quad\Sigma^{2}=\{ 00,01,10,11 \}$
- $\Sigma^{0}=\{ \epsilon \}$

L'insieme di tutte le stringhe su $\Sigma$ si indica con $\Sigma^{*}$.
$$\Sigma^{*}=\Sigma^{0} \cup \Sigma^{1} \cup \Sigma^{2} \cup\dots$$
Si può definire anche come:
$$\Sigma^{+}=\Sigma^{1} \cup \Sigma^{2} \cup \Sigma^{3} \cup\dots=\Sigma^{*}=\Sigma^{+}\cup \{ \epsilon \}$$

#### Concatenazione
> [!info] Definizione
> Se $x$ e $y$ sono stringhe, allora la ***concatenazione*** $xy$ è la stringa ottenuta collocando una copia di $y$ subito dopo una copia di $x$.

Se
$$
x=a_{1}a_{2}\dots a_{i}, \quad y=b_{1}b_{2}\dots b_{j}
$$
<u>Allora</u>
$$
xy=a_{1}a_{2}\dots a_{i}b_{1}b_{2}\dots b_{j}
$$

### Linguaggio Formale
> [!cite] Definizione
> Se $\Sigma$ è un *alfabeto* e $L \subseteq \Sigma^{*}$ allora $L$ è un ***linguaggio formale***.

> ***In altre parole***
- Con ***linguaggio formale*** si intende un insieme di stringhe costruito sopra un alfabeto $\Sigma$.

Un esempio di linguaggio formale è l'insieme delle ***parole italiane legali***.