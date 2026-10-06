## Linguistica formale
Compilatore: 
- Parser + code generation
- Il parser trasforma il codice sorgente in un albero sintattico (errori lessicali/sintattici se presenti)
- Dall'albero si genererà poi l'oggetto eseguibile.

## Espressioni Regolari
--- 
> Un ***Finite Automaton*** (NFA o DFA) è un metodo per costruire una macchina che riconosce *linguaggi regolari*.


> [!abstract] Espressioni Regolari
> Una ***espressione regolare*** è un modo dichiarativo per descrivere un linguaggio regolare.

> Esempio
- $01^{*}+10^{*}$

Usate in contesti come:
- Comandi `UNIX` (`{sh icon} grep`).
- Strumenti per l'analisi lessicale dei linguaggi.

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


### Costruire le espressioni regolari

> [!abstract] Definizione induttiva

> ***Base***: $\epsilon$ e $\emptyset$ sono espressioni regolari
- Se $a\in\Sigma$, allora $a$ è un'espressione regolare $L(a)=\{ a \}$

> ***Induzione***:

- Se $E$ è una espr. reg. allora $(E)$ è una espr. reg.
$L((E))=L(E)$

- Se $E$ e $F$ sono espr. reg. allora $E+F$ è una espr. reg.
$L(E+F)=L(E)\cup L(F)$

- Se $E$ e $F$ sono espr. reg. allora $E.F$ è una espr. reg.
$L(E.F)=L(E).L(F)$

- Se $E$ è una espr. reg. allora $E^{*}$ è una espr. reg.
$L(E^{*})=(L(E))^{*}$


> [!example] Esempio
> 

Le espressioni regolari per $L=\{ w\in \{ 0,1 \}^{*} :0,1 \text{ alternati in } w\}$
$$
(01)^{*}+(10)^{*}+0(10)^{*}+1(01)^{*}
$$
o *equivalentemente*
$$
(\epsilon + 1)(01)^{*}(\epsilon+0) 
$$

> [!summary] Ordine di precedenza degli operatori
> 1. Chiusura ($^{*}$)
> 2. Concatenazione ($.$)
> 3. Più ($+$)

### Equivalenza di FA e espressioni regolari
Abbiamo già mostrato che DFA, NFA e $\epsilon$-NFA sono tutti equivalenti.
![[attachements/Pasted image 20261006172117.png]]

Per mostrare che gli FA sono equivalenti alle espressioni regolari dobbiamo stabilire che
1. Per ogni `DFA` $A$ possiamo trovare un'espressione regolare $R$ tale che $L(R)=L(A)$.
2. Per  ogni espressione regolare $R$ esiste un $\epsilon$-NFA $A$, tale che $L(A)=L(R)$

##### Da DFA a espressioni regolari
Il procedimento è ***molto complesso***, si devono formare *espressioni* che descrivano insiemi di stringhe che etichettano certi cammini nel diagramma di transizione del `DFA`, considerando però solo cammini che attraversano un sottoinsieme limitato degli stati.

Partendo da **espressioni semplici**, *archi* o *nodi singoli*, e via via per induzione si **costruiscono le espressioni** che fanno passare i cammini attraverso insiemi di stati via via più grandi. 
Alla fine i cammini possono passare attraverso qualunque stato, in modo che le *espressioni generate* rappresentino ***tutti i cammini possibili***.

> [!cite] Teorema
> Per ogni `DFA` $A=(Q,\Sigma,\delta,q_{0},F)$ esiste una espressione regolare $R$ tale che $L(R)=L(A)$.

> Eliminazione iterativa degli stati

La figura mostra un generico stato $s$ che sta per essere ***rimosso***.
![[attachements/Pasted image 20261006174245.png]]

Tutti gli archi che comprendono lo stato $s$ vengono **rimossi** e per compensare, viene *introdotta* per ogni predecessore ($q_{i}$) di $s$ e ogni successore $(p_{j})$ una ***espressione regolare*** che rappresenta *tutti i percorsi* che partono da $q_{i}$, passano da $s$ e finiscono in $p_{j}$.
- L'espressione per questi percorsi è $Q_{i}S^{*}P_{j}$.

Questa espressione è aggiunta con l'operatore di unione all'arco da $q_{i}$ a $p_{j}$.
![[attachements/Pasted image 20261006174304.png]]



> [!caution] La strategia per costruire una ***espressione regolare*** è la seguente:

- Per ogni stato di accettazione $q$ applicare il processo di riduzione per creare un automa equivalente con espressioni regolari negli archi, eliminando tutti gli stati eccetto $q$ e lo stato iniziale $q_{0}$.
- Se $q\neq q_{0}$ allora si ha un automata con due stati come definito in figura.
- Se lo *stato iniziale* è uno ***stato di accettazione*** allora va fatto una ulteriore riduzione, mantenendo lo stato iniziale.

![[attachements/Pasted image 20261006180409.png]]

L'automata corrisponde all'espressione regolare $E_{q}=(R+SU^{*}T)^{*}SU^{*}$

Una volta fatto questo, rimane uno stato unico con un autociclo che come etichetta contiene l'espressione regolare dell'automata.

> Esempio

![[attachements/Pasted image 20261006183244.png]]

![[attachements/Pasted image 20261006183441.png]]

![[attachements/Pasted image 20261006183513.png]]

![[attachements/Pasted image 20261006183553.png]]

![[attachements/Pasted image 20261006183621.png]]