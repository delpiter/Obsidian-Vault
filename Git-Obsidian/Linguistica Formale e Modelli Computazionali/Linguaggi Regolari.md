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

### Proprietà dei Linguaggi Regolari
#### Proprietà di Chiusura
> [!quote] Idea
> Se certi linguaggi sono regolari e il linguaggio $L$ è formato dal linguaggio regolare usando certi operatori, allora $L$ è un ***linguaggio regolare***.

Siano $L$ e $M$ due ***linguaggi regolari***, allora i seguenti linguaggi sono a loro volta linguaggi regolari:
- Unione $L\cup M$
- Intersezione $L\cap M$
- Complemento $\overline{N}$
- Differenza $L \backslash M$
- Inversione $L^{R}=\{ w^{R}: w\in L \}$
- Chiusura: $L^{*}$
- Concatenazione $L.M$

##### Unione
> [!cite] Teorema 4.4
> Per ogni coppia di linguaggi regolari $L$ e $M$, l'***unione*** $L\cup M$ è regolare

> Dimostrazione

Sia $L=L(E)$ e $M=L(F)$ allora $L(E+F)=L\cup M$ per *definizione*.

##### Complementare
> [!cite] Teorema 4.5
> Se $L$ è un linguaggio regolare su $\Sigma$, allora anche il ***complementare*** $\overline{L}=\Sigma^{*}\backslash L$  è regolare.

> Dimostrazione

Sia $L$ riconosciuto da un [[Automi a Stati Finiti Deterministici|DFA]]
$$
A=(Q,\Sigma,\delta,q_{0},F)
$$
Sia $B=(Q,\Sigma,\delta,q_{0},Q\backslash F)$ allora $L(B)=\overline{L}$

##### Intersezione
> [!cite] Teorema 4.8
> Se $L$ e $M$ sono regolari, allora anche l'***intersezione*** $L \cap M$ è regolare.

> Dimostrazioni

Per la [[../Architettura degli Elaboratori/Algebra di Bool e Logica Digitale/Algebra di Bool|legge di DeMorgan]] $L\cap M = \overline{\overline{L}\cup\overline{M}}$ e sappiamo già che i linguaggi regolari sono chiusi rispetto al complemento e all'unione.

> Oppure


> [!tldr] Simulazione Parallela
> Per calcolare l'*intersezione* di due `DFA`, ***eseguo in parallelo*** il processo dell'automa data una stringa del linguaggio.
> Se entrambi gli automi, finita la stringa si trovano in uno stato di accettazione, allora la stringa *fa parte dell'intersezione*.

***Formalmente***
Sia $L$ il linguaggio di:
$$
A_{L}=(Q_{L},\Sigma, \delta_{L},q_{L},F_{L})
$$
e $M$ il linguaggio di:
$$
A_{M}=(Q_{M},\Sigma, \delta_{M},q_{M},F_{M})
$$
Assumiamo *senza perdita di generalità* che entrambi gli automi siano ***deterministici***.
Costruiamo un automa che simula $A_{L}$ e $A_{M}$ in ***parallelo*** e accetta *se e solo se* sia $A_{L}$ che $A_{M}$ accettano.
![[attachements/LanguageIntersection.png]]

Se $A_{L}$ va dallo stato $p$ allo stato $s$ leggendo $a$, e $A_{M}$ va dallo stato $q$ allo stato $t$ leggendo $a$ allora $A_{L\cap M}$ andrà dallo stato $(p,q)$ allo stato $(s,t)$ leggendo $a$.
$$
A_{L\cap M}=(Q_{L}\times Q_{M},\Sigma,\delta_{L\cap M},(q_{L},q_{M}),F_{L})
$$
dove:
- $\delta_{L\cap M}((p,q),a)=(\delta_{L}(p,a),\delta_{M}(q,a))$

Si può mostrare per induzione su $\mid w\mid$ che:
$$
\hat{\delta}_{L\cap M}((q_{L},q_{M}),w)=(\hat{\delta}_{L}(q_{L},w),\hat{\delta}_{M}(q_{M},w))
$$
Gli stati di accettazione sono gli stati rappresentati da una ***coppia di due stati accettazione***.

> Esempio

![[attachements/IntersectionExample.png]]

##### Differenza
> [!cite] Teorema 4.10
> Se $L$ e $M$  sono linguaggi regolari, allora anche la ***differenza*** $L\backslash M$ è regolare.

> Dimostrazione

Osserviamo che $L\backslash M=L\cap\overline{M}$, e sappiamo già che i linguaggi regolari sono chiusi rispetto al complemento e l'intersezione.

##### Inversione
> [!cite] Teorema 4.11
> Se $L$ è un linguaggio regolare, allora anche l'***inversione*** $L^{R}$ (le stringhe $w^{R}$, cioè $w$ lette all'indietro, con $w\in L$) è regolare.

> Dimostrazione

Sia $L$ riconosciuto da un **FA** $A$. Modifichiamo $A$ per renderlo un **FA** per $L^{R}$
1. Giriamo tutti gli archi
2. Rendiamo il vecchio stato iniziale l'unico stato finale
3. Creiamo un nuovo stato iniziale $p_{0}$ con $\delta(p_{0},\epsilon)=F$.

#### Proprietà di Decisione
##### Testare se un linguaggio è vuoto
> [!cite] Teorema
> $L(A)=\emptyset$ per **FA** $A$ ***se e solo se*** uno stato finale è raggiungibile dallo stato iniziale in $A$.

Totale: $O(n^{2})$ passi.

> Oppure

Possiamo guardare un'[[Espressioni Regolari|espressione regolare]] $E$ di lunghezza $s$ e vedere se $L(E)=\emptyset$ in $O(s)$ passi.
Usiamo il seguente metodo:
- $E=F+G$ allora $L(E)$ è vuoto *se e solo se* sia $L(F)$ che $L(G)$ sono **vuoti**.
- $E=F.G$ allora $L(E)$ è vuoto *se e solo se* $L(F)$ e $L(G)$ sono vuoti
- $E=F^{*}$ allora $L(E)$ non è mai vuoto perché $\epsilon \in L(E)$
- $E=\epsilon$ allora $L(E)$ non è vuoto
- $E=a$ allora $L(E)$ non è vuoto
- $E=\emptyset$ allora $L(E)$ è vuoto

##### Controllare l'appartenenza
> [!abstract] Per DFA
> Per controllare se $w\in L(A)$ per `DFA` $A$, simuliamo $A$ su $w$. Se $|w|=n$ questo prende $O(n)$ passi.

> [!caution] Per NFA
> Se $A$ è un `NFA` e ha $s$ stati, simulare $A$ su $w$ prende $O(ns^{2})$ passi.

Lo stesso vale per $\epsilon$-NFA calcolando preventivamente le $\text{ECLOSE}$ di tutti gli stati.

> [!todo] Per espressione regolare
> Se $L=L(E)$ per l'espressione regolare $E$ di lunghezza $s$ prima convertiamo $E$ in un $\epsilon$-NFA con $2s$ stati, poi simuliamo $w$ su questo automa in $O(ns^{2})$ 

#### Proprietà Equivalenza e Minimizzazione
##### Equivalenza
> [!tldr] Idea
> Due stati sono ***equivalenti*** se e solo se per ogni stringa dell'alfabeto, partendo dai due stati *si raggiunge uno stato di accettazione*. 

Sia $A=(Q,\Sigma,\delta,q_{0},F)$ un [[Automi a Stati Finiti Deterministici|DFA]] e $\{ p,q \}\subseteq Q$.

Definiamo:
$$
p\equiv q \iff \forall w\in\Sigma^{*}:\hat{\delta}(p,w)\in F \iff \hat{\delta}(q,w)\in F
$$

> [!summary] Se $p\equiv q$ diciamo che $p$ e $q$ sono ***equivalenti***

> [!fail] Se $p\not\equiv q$ diciamo che $p$ e $q$ sono ***distinguibili***

In altre parole $p$ e $q$ sono **distinguibili** *se e solo se*
$$
\exists w:\hat{\delta}(p,w)\in F \text{ e } \hat{\delta}(q,w)\notin F
$$
o viceversa.

###### Algoritmo
> [!caution] Table-filling algorithm
> Possiamo ***calcolare coppie di stati distinguibili*** con il seguente metodo induttivo.

> ***Base***
- Se $p\in F$ e $q\notin F$ allora $p\not\equiv q$

> ***Induzione***
- Se $\exists a\in \Sigma :\delta(p,a) \not\equiv \delta(q,a)$ allora $p\not\equiv q$.

> [!example] Esempio

![[attachements/EquivalenceExample.png]]

Inizio contrassegnando come distinte tutte le coppie di stati ***accettazione***/***non accettazione*** (*passo base*).

Successivamente scorro tutte le coppie di nodi:
- Controllo gli archi uscenti dalla coppia con lo stesso simbolo e controllo la coppia di stati che raggiungono.
- Se la coppia di stati è già stata segnata, allora segno nella tabella anche quella corrente.


> [!done] Fine dell'algoritmo
> L'algoritmo finisce quando passo tutte le coppie di stati ancora non segnati, ***senza modificare la tabella***.

La tabella finale dell'esempio è la seguente:
![[attachements/TableFillingAlgo.png]]

> Stati equivalenti:
- $(A,E)$
- $(B,H)$
- $(D,F)$

> [!cite] Teorema
> Se $p$ e $q$ **non sono distinti** dall'algoritmo, allora $p \equiv q$

###### Testare l'equivalenza di linguaggi regolari
> Il ***table-filling algorithm*** da una procedura facile per testare se due linguaggi regolari sono equivalenti.

> [!hint] Test
> Siano $L$ e $M$ ***linguaggi regolari*** descritti in qualche forma.

Per testare se $L=M$
1. Converto sia $L$ che $M$ in `DFA`
2. Immaginiamo il `DFA` che è l'unione dei due `DFA`
3. Se l'algoritmo dice che i due stati iniziali sono ***distinguibili*** allora $L\neq M$ altrimenti $L=M$

> Esempio di `DFA` equivalenti

![[attachements/EquivalentDFA.png]]

![[attachements/EquivalentDFATable.png]]

#### Minimizzazione di DFA
> [!cite] Algoritmo
> Per minimizzare un `DFA` mettiamo insieme tutti gli ***stati equivalenti*** considerando poi come stati le ***classi di equivalenza*** $p/_{\equiv}$ al posto di $p$ ed eliminando eventuali stati non raggiungibili dallo stato iniziale.

> Esempio

![[attachements/EquivalenceExample.png]]

Dal seguente `DFA`, dopo aver applicato il *table-filling algorithm*, possiamo trovare le seguenti classi di equivalenza:
$$
\{ \{ A,E \},\{ B,H \}, \{ C \}, \{ D,F \}, \{ G \} \}
$$

> [!nota]
> $p /_{\equiv}$ è classe di equivalenza della [[../Algebra e Geometria/Basi dell'algebra/1 - Introduzione#Relazione di Equivalenza|relazione di equivalenza]], cioè una relazione *riflessiva*, *simmetrica* e *transitiva*.

Per minimizzare un `DFA` $A=(Q,\Sigma,\delta,q_{0},F)$ dove assumiamo di aver già eliminato tutti gli stati non raggiungibili dallo stato iniziale.

Costruiamo ora un `DFA` $B=(Q /_{\equiv},\Sigma /_{\equiv},\gamma /_{\equiv},q_{0} /_{\equiv},F/_{\equiv})$ dove:
- $\gamma(p/_{\equiv}, a)=\delta(p,a)/_{\equiv}$
- $Q/_{\equiv}$ è l'insieme delle classi di equivalenza degli stati di $Q$
- $F/_{\equiv}$ è l'insieme di quelle degli **stati accettanti**.

Affinché $B$ sia ben definito, dobbiamo mostrare che:
- Se
$$
p\equiv q
$$
allora
$$
\delta(p,a) \equiv \delta(q,a)
$$
Ma se $\delta(p,a) \not\equiv \delta(q,a)$ allora l'algoritmo concluderebbe $p\not\equiv q$, quindi $B$ è ***ben definito***.

Di seguito l'automa equivalente a quello in esempio:
![[attachements/EquivalentAutomata.png]]