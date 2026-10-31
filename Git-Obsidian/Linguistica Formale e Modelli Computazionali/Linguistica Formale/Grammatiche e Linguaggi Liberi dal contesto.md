> Molti linguaggi **non** sono [[Linguaggi Regolari|regolari]], consideriamo allora classi più grandi.

> [!quote] Linguaggi Liberi dal contesto
> Le ***context-free languages*** o `CFL` sono state usate nello studio dei linguaggi naturali e nello studio dei generatori di compilatori.

I `CFL` sono importanti anche per `XML`.

Questi linguaggi hanno una notazione ricorsiva naturale, chiamata context-free grammar.

> [!cite] Grammatiche Libere dal contesto
> Le ***context-free grammars*** o `CFG` sono la base della sintassi `BNF` (*Backus-Naur-Form*), usate per i linguaggi di programmazione.

## Context-Free Grammars
---
> Consideriamo $L_{pal}=\{ w\in \Sigma^{*}:w=w^{R}\}$

> [!hint] Linguaggio delle stringhe **palindrome**
> 

Per esempio $otto\in L_{pal}$.

Sia $n$ il numero di stati di un ipotetico DFA $A$ tale che $L(A)=L_{pal}$.
Si ha $0^{n}10^{n} \in L_{pal}$. Nel leggere lo $0^{n}$ iniziale $A$ deve passare per un loop.

Se omettiamo il loop, $A$ accetta una stringa $0^{m}10^{n}$ con $m<n$
> [!fail] Contraddizione
> 

Definiamo $L_{pal}$ induttivamente

> **Base**: $\epsilon,0,1$ sono palindromi

> **Induzione**: Se $w$ è palindroma, anche $0w0$ e $1w1$ lo sono

Nessun altra stringa è palindroma.

### Definizione
> [!cite] Definizione 
> Una ***grammatica libera dal contesto*** è una quadrupla
> $$G=(V,T,P,S)$$

dove
- $V$ è un insieme finito di *variabili* o non-terminal.
- $T$ è un insieme finito di *terminali*.
- $P$ è un insieme finito di *produzioni* della forma $A\to \alpha$ dove $A$ è una variabile e $\alpha \in (V \cup T)^{*}$
- $S$ è una variabile distinta chiamata *variabile iniziale*.

> Le `CFG` sono un modo formale per le definizioni come quella per $L_{pal}=\{ w\in \Sigma^{*}:w=w^{R}\}$

Esempio:
- $L_{pal}=(\{ S \},\{ 0,1 \},P,S)$ dove:
$$
P=\{ S\to \epsilon,S\to 0, S\to 1,S\to 0S0 ,S\to 1S1\}
$$

- $0$ e $1$ sono *terminali*
- $S$ è una *categoria sintattica* (o *variabile*)
- $S$ è in questa grammatica anche la categoria sintattica *iniziale*.
- 1-5 sono *produzioni* o *regole*

A volte raggruppiamo le produzioni con la ***stessa testa***.
$$
P=\{ S\to\epsilon|0|1|0S0|1S1 \}
$$


> [!example] Esempio: Espressioni in un tipico linguaggio di programmazione
> 

Gli operatori sono $+$ e $*$, e gli operandi sono identificatori, cioè stringhe in $L((a+b)(a+b+0+1)^{*})$

Le espressioni sono definite dalla grammatica
$$
G=(\{ E,I \},T,P, E)
$$
Dove:
- $T=\{ +,* ,(,),a,b,0,1\}$ e $P$ è il seguente insieme di produzioni.
1. $E\to I$
2. $E\to E+E$
3. $E\to E* E$
4. $E\to (E)$
5. $I\to a$
6. $I\to b$
7. $I\to Ia$
8. $I\to Ib$
9. $I\to I0$
10. $I\to I1$

### Derivazione usando le grammatiche
> Sia $G=(V,T,P,S)$ una `CFG` $A\in V$, $\{ \alpha,\beta \}\subset (V\cup T)^{*} \text{ e } \quad A\to \gamma\in P$

Allora scriviamo
$$
\alpha A\beta\underset{ G }{ \implies }\alpha\gamma\beta
$$
e diciamo che da $\alpha A\beta$ si deriva $\alpha\gamma\beta$

> [!info] Chiusura
> Definiamo $\overset{*}{\implies}$ la chiusura ***riflessiva*** e ***transitiva*** di $\implies$

> **Base**: Sia $\alpha\in(V\cup T)^{*}$ allora $\alpha\overset{*}{\implies}\alpha$

> **Induzione**: Se $\alpha\overset{*}{\implies}\beta$ e $\beta \implies\gamma$ allora $\alpha\overset{*}{\implies}\gamma$

Dove $\alpha\overset{*}{\implies}\beta$ significa che **posso derivare** la stringa $\beta$ partendo dalla stinga $\alpha$ *applicando più derivazioni*.
#### Procedimento
> Si espande da un simbolo iniziale usando una delle produzioni.

Se in una stringa ho più di una variabile:
- Scelgo una delle variabili all'interno della stringa.
- Preservo il ***contesto*** a destra e a sinistra della variabile
	- Il contesto sono tutti i caratteri che non sono la variabile scelta
- Applico una delle ***produzioni*** del linguaggio alla variabile selezionata
- Il procedimento si conclude quando la stringa $w$ è fatta solo di *terminali*

> [!hint] Osservazione
> Preservare il contesto al di fuori della variabile durante l'applicazione di una produzione, significa che il linguaggio è ***indipendente dal contesto***.

Al contrario dei `DFA` che hanno un approccio riconoscitivo nella definizione di un linguaggio, i `CFG` hanno un approccio ***generativo***.
##### Esistono alcune tipologie di derivazione
> [!help] Left-most derivation
> La derivazione a sinistra $\underset{ lm }{ \implies }$ ***rimpiazza*** *sempre* la variabile più a sinistra con il corpo di una delle sue regole.

> [!caution] Right-most derivation
> La derivazione a sinistra $\underset{ rm }{ \implies }$ ***rimpiazza*** *sempre* la variabile più a destra con il corpo di una delle sue regole.

È possibile scegliere una qualsiasi variabile e non è obbligatorio scegliere sempre quella più a destra o a sinistra.

> [!Example] Esempio
> Derivazione di $a*(a+b00)$ da $E$ nella grammatica delle espressioni:

$$
\begin{align}
& E\implies E*E \implies I *E \implies a*E \implies a*(E)\implies \\
& \implies a*(E+E) \implies a*(I+E) \implies a*(a+E)\implies \\
& a*(a+I) \implies a*(a+I0)\implies a*(a+I00)\implies a*(a+b00)
\end{align}
$$


> [!hint] Nota
> Ad ogni passo potremmo avere ***varie regole tra cui scegliere***.

Non tutte le scelte portano a derivazioni di una particolare stringa, per esempio:
- $E\implies E+E$ non fa arrivare a $a*(a+b00)$

La derivazione dell'esempio precedente è una ***derivazione a sinistra***, di seguito la derivazione a destra della *stessa stringa*.
$$
\begin{align}
& E\underset{ rm }{ \implies } E*E \underset{ rm }{ \implies } E *(E) \underset{ rm }{ \implies } E*(E+E) \underset{ rm }{ \implies } E*(E+I)\implies \\
& \underset{ rm }{ \implies } E*(E+I0) \underset{ rm }{ \implies } E*(E+I00) \underset{ rm }{ \implies } E*(E+b00)\implies \\
& \underset{ rm }{ \implies } E*(I+b00) \underset{ rm }{ \implies } E*(a+b00)\underset{ rm }{ \implies } I*(a+b00)\underset{ rm }{ \implies } a*(a+b00)
\end{align}
$$


### Il linguaggio di una grammatica
> [!info] 
> Se $G(V,T,P,S)$ è una `CFG`, allora il ***linguaggio*** di $G$ è
> $$L(G)=\{ w\in T^{*}:S\overset{*}{\underset{ G }{ \implies }} w \}$$
>>[!done] Cioè l'insieme delle stringhe su $T^{*}$ ***derivabili*** dal simbolo iniziale.

Se $G$ è una `CFG`, chiameremo $L(G)$ un *linguaggio libero dal contesto*.

> Esempio
- $L(G_{pal})$ è un ***linguaggio libero dal contesto***.

#### Alberi Sintattici
> [!abstract] Definizione
> Se $w\in L(G)$, per una `CFG`, allora $w$ ha un ***albero sintattico***, che dice la *struttura sintattica* di $w$

$w$ potrebbe essere:
- Un sorgente di un programma
- Una query `SQL`
- Un documento `XML`


> [!done] Gli alberi sintattici sono una rappresentazione alternativa alle derivazioni
>

Ci possono essere diversi alberi per la stessa stringa.
- Idealmente ci dovrebbe essere un solo albero sintattico, cioè la `CFG` dovrebbe essere ***non ambigua***.
- Non sempre è possibile rimuovere l'ambiguità

#### Costruzione di un albero sintattico
> [!caution] Procedimento
> Sia $G=(V,T,P,S)$ una `CFG`. Un albero è un ***albero sintattico*** per $G$ se:

1. Ogni ***nodo interno*** è etichettato con una variabile in $V$.
2. Ogni ***foglia*** è etichettata con un simbolo in $V\cup T \cup \{ \epsilon \}$
	- Ogni foglia etichettata con $\{ \epsilon \}$ è l'***unico figlio*** del suo nodo padre. 
3. Se un ***nodo interno*** è etichettato $A$, e i suoi *figli* sono etichettati $X_{1},X_{2},\dots,X_{k}$ (in ordine da sinistra a destra) allora $A\to X_{1}X_{2} \dots X_{k}\in P$
	- Nella relazione padre-figli leggo una produzione della grammatica

> Esempio: nella grammatica
4. $E\to I$
5. $E\to E+E$
6. $E\to E* E$
7. $E\to (E)$

Il seguente ***è un albero sintattico***.
![[attachements/SyntacticTree.png]]

Questo albero sintattico mostra la derivazione $E\overset{*}\implies I+E$

> [!todo] Prodotto
> Il ***prodotto*** di un albero sintattico è la *stringa di foglie* lette da sinistra a destra.

Importanti sono gli alberi sintattici dove:
- Il prodotto è una ***stringa terminale***.
- La radice è etichettata dal ***simbolo iniziale***.

> [!done] L'insieme dei prodotti di questi alberi è il ***linguaggio della grammatica***.


#### Equivalenza tra Left-Most e Right-Most Derivation
> [!cite] Teorema
> Sia $G=(V,T,P,S)$ una `CFG` e $A\in V$. I seguenti sono equivalenti
> 1. $A\overset{*}{\implies}w$
> 2. $A\overset{*}{\underset{ lm }{ \implies }}w$ e $A\overset{*}{\underset{ \mathrm{} }{ \implies }}w$
> 3. Un **albero sintattico** di $G$ con radice $A$ e prodotto $w$.

Per provare l'equivalenza, usiamo il seguente piano
- Dagli alberi alle derivazioni a sinistra (o destra), visto l'albero da sinistra a destra (o da destra a sinistra) $3\implies 2$
- Una derivazione sinistra (o destra) è anche una derivazione $2 \implies 1$
- Leggendo la derivazione costruisco l'albero $1 \implies 3$

##### Dimostrazione
> Dimostriamo il primo punto ($3\implies 2$) poiché le altre due sono banali.

Costruiamo la derivazione a sinistra per il seguente albero:
![[attachements/LeftMostDerivation.png]]

Supponiamo di aver induttivamente costruito la ***derivazione a sinistra***.
$$
E\implies I \implies a
$$
corrispondente al sottoalbero più a sinistra, e la derivazione a sinistra
$$
\begin{align}
& E\implies(E)\implies(E+E)\implies (I+E) \implies (a+E) \implies \\
& \implies (a+I) \implies (a+I0) \implies (a+I00) \implies (a+b00)
\end{align}
$$
corrispondente al sottoalbero più a destra.

Per la ***derivazione corrispondente all'interno albero***
- iniziamo con $E\implies E* E$ 
- espandiamo la prima $E$ con la prima derivazione e la seconda $E$ con la seconda derivazione.

$$
\begin{align}
& E\implies E*E \implies \\
& I* E\implies \\
& a*E \implies \\
& a*(E)\implies \\
& a*(E+E)\implies \\
& a*(I+E)\implies \\
& a*(a+E)\implies \\
& a*(a+I)\implies \\
& a*(a+I0)\implies \\
& a*(a+I00)\implies \\
& a*(a+b00)
\end{align}
$$

#### Ambiguità in grammatiche e linguaggi
> Nella grammatica

1. $E\to I$
2. $E\to E+E$
3. $E\to E* E$
4. $E\to(E)$
5. $\dots$

La stringa $E+E*E$ ha ***due derivazioni***.
- $E\implies E+E \implies E+E*E$
- $E\implies E*E \implies E+E*E$
![[attachements/SyntacticTreeAmbiguity.png]]

L'esistenza di varie derivazioni di per se non è pericolosa, è l'esistenza di vari alberi sintattici che rovina la grammatica.

Nella stessa grammatica:
4. $\dots$
5. $I\to a$
6. $I\to b$
7. $I\to Ia$
8. $I\to Ib$
9. $I\to I0$
10. $I\to I1$

la stringa $a+b$ ha varie derivazioni:
- $E\implies E+E\implies I+E\implies a+E \implies a+I \implies a+b$
- $E\implies E+E\implies E+I\implies I+I \implies a+I \implies a+b$

Però il loro albero sintattico è lo stesso: la struttura di $a+b$ è quindi non ambigua.

> [!cite] Definizione
> Sia $G=(V,T,P,S)$ una `CFG`.
> Diciamo che $G$ è ***ambigua*** se esiste una stringa in $T^{*}$ che ha *più di un albero sintattico*.

Se ogni stringa in $L(G)$ ha un unico albero sintattico, $G$ è detta ***non-ambigua***.
> Esempio: La stringa terminale $a+a*a$ ha due alberi sintattici.

![[attachements/AmbiguityExample.png]]

#### Derivazioni a sinistra e ambiguità
> I due alberi sintattici per $a+a*a$: danno luogo a due derivazioni:

$$
\begin{align}
& E\implies E+E \implies I+E\implies a+E\implies a+E*E \\
& \implies a+I*E \implies a+a*E \implies a+a*I \implies a+a*a 
\end{align}
$$
e
$$
\begin{align}
& E\implies E*E \implies E+E*E\implies I+E*E\implies a+E*E \\
& \implies a+I*E \implies a+a*E \implies a+a*I \implies a+a*a 
\end{align}
$$

> [!help] In generale
 - Ad un ***albero sintattico*** corrispondono *molte derivazioni*, ma
 - Ad ogni ***diverso albero sintattico*** corrisponde un'*unica diversa derivazione a sinistra*.
 - Ad ogni ***diverso albero sintattico*** corrisponde un'*unica derivazione a destra*.

> [!cite] Teorema
> Data una `CFG` $G$, una stringa terminale $w$ ha ***due distinti alberi sintattici*** <u>se e solo se</u> $w$ ha due distinte derivazioni a sinistra dal simbolo iniziale.

#### Rimozione delle ambiguità dalle grammatiche
> A volte è possibile rimuovere le ambiguità dalla grammatica

> [!fail] Ma...
> ***Non c'è nessun algoritmo*** per farlo in maniera sistematica.

Addirittura, alcuni `CFL` hanno solo `CFG` ambigue:
- Un linguaggio che non può essere disambiguato si dice ***inerentemente ambiguo***.

> Studiamo la grammatica:

$$
\begin{align}
& E\to I\mid E+E\mid E*E\mid(E) \\
& I\to a\mid b\mid Ia\mid Ib\mid I0\mid I1
\end{align}
$$
Bisogna modificarla in modo da stabilire:
1. Chi ha precedenza tra $*$ e $+$
2. Come si raggruppano sequenze di uno stesso operatore:
	-  $E+E+E$ è inteso come $E+(E+E)$ (*associatività destra*) o come $(E+E)+E$ (*associatività sinistra*)?


> [!question] È possibile renderlo non ambiguo?

Soluzione: Introduciamo una ***gerarchia di variabili*** che stabilisca un ordine di precedenza tra gli operatori.
1. *Espressioni* $E$: composizioni di uno o più termini $T$ tramite $+$
2. *Termini* $T$: composizioni di uno o più fattori $F$ tramite $*$
3. *Fattori* $F$:
	1. *Identificatori* $I$
	2. *Espressioni* $E$ racchiuse tra parentesi.

I termini $T$ non possono generare $+$ che siano fuori da parentesi
- Questa gerarchia stabilisce che $*$ ***ha la precedenza rispetto a*** $+$.
- L'unico modo di generare $a+a*a$ è considerando $a*a$ come un termine $T$.

> Formalmente
1. $E\to T\mid E+E$
2. $T\to F\mid T* T$
3. $F\to I\mid (E)$
4. $I\to a\mid b\mid Ia\mid Ib\mid I0\mid I1$

> [!warning] Non è ancora non-ambiguo 
> Abbiamo solo risolto la ***precedenza della moltiplicazione***

Dobbiamo ancora imporre un ordine per il raggruppamento degli operatori allo stesso livello.
- Come l'associativa a sinistra.

1. $E\to T\mid E+T$
2. $T\to F\mid T* E$
3. $F\to I\mid (E)$
4. $I\to a\mid b\mid Ia\mid Ib\mid I0\mid I1$

#### Ambiguità Inerente
> [!info] Definizione
> Un `CFL` $L$ è ***inerentemente ambiguo*** se *tutte* le grammatiche per $L$ sono ambigue.

> Esempio

$$
L=\{ a^{n}b^{n}c^{m}d^{m}:n\geq 1, m\geq 1 \}\cup \{ a^{n}b^{m}c^{m}d^{n}:n\geq 1, m\geq 1 \}
$$
Una grammatica per $L$ è 
$$
\begin{align}
& S\to AB\mid C \\
& A\to aAb\mid ab \\
& B\to cBd\mid cd \\
& C\to aCd\mid aDd \\
& D\to bDc\mid bc 
\end{align}
$$

Guardando la struttura sintattica della stringa $aabbccdd$
![[attachements/InherentAmbiguity.png]]

Vediamo che ci sono due left-most derivation:
$$
S\implies AB\implies aAbB\implies aabbB \implies aabbcBd\implies aabbccdd
$$
e
$$
S\implies C\implies aCd\implies aaDdd \implies aabDcdd\implies aabbccdd
$$

> [!hint] Info
> Può essere provato che ***ogni grammatica*** per $L$ si comporta come questa.

## Pulizia di un Linguaggio
---
> La [[Forma Normale di Chomsky]] richiede per essere applicata la ***pulizia della grammatica***

"***Pulire***" la grammatica significa:
1. Eliminare le ***produzioni*** $\epsilon$.
2. Eliminare le ***produzioni unità***.
3. Eliminare i ***simboli inutili***.

> [!hint] Osservazione
> Per pulire correttamente la grammatica è ***necessario seguire l'ordine*** di operazioni descritto.

### Eliminazione dei simboli inutili
> [!cite] Definizione
> Un simbolo $X$ è ***utile per una*** [[#Context-Free Grammars|grammatica]] $G=(V,T,P,S)$ se esiste una derivazione:
> $$S\overset{*}{\underset{G}{\Rightarrow}} \alpha X\beta \overset{*}{\underset{G}{\Rightarrow}} w$$
> per una stringa di terminali $w$.

I simboli che non sono utili sono detti ***inutili***.

> Simboli ***generanti***
- Un simbolo $X$ è generante se $X \overset{*}{\underset{G}{\Rightarrow}} w$ per qualche $w \in T^{*}$

> Simboli ***raggiungibili***
- Un simbolo $X$ è raggiungibile se $S \overset{*}{\underset{G}{\Rightarrow}} \alpha X\beta$ per qualche $\{ \alpha,\beta \}\subseteq (V\cup T)^{*}$


> [!hint] Ordine delle operazioni
> Se in $G$ con $L(G)\neq \emptyset$ eliminiamo prima i simboli *non generanti* poi quelli *non raggiungibili*, rimarranno solamente ***simboli utili***.

###### Esempio
> Sia $G$ la grammatica: $S \to AB|a, \ A\to b$

Il linguaggio $L(G)=\{  a \}$ poiché per definizione una stringa del linguaggio deve contenere solo ***simboli terminali*** e il terminale $b$ lo si può raggiungere solo se scelgo $AB$.

$S$ e $A$ sono generanti, $B$ non lo è.
- Se eliminiamo $B$ dobbiamo eliminare $S\to AB$ ***riducendo la grammatica***.

Ora solo la variabile $S$ è raggiungibile.
- Eliminando $A$ rimane solo $S\to a$ con *linguaggio equivalente all'originale*.

> [!warning] Importanza dell'ordine delle operazioni
> Se eliminiamo prima i simboli *non raggiungibili*:
> - Tutti i simboli ($A$ e $B$) sono raggiungibili\
> - Eliminiamo poi $B$ in quanto *non generante*
>
> Rimane la grammatica $S\to a, \ A\to b$ che contiene ancora ***simboli inutili***.

### Eliminazione delle produzioni epsilon
> Si ha che se $L$ è una `CFL` allora $L\setminus \{ \epsilon \}$ ha una grammatica priva di produzioni $\epsilon$.

> [!cite] Variabile Annullabile
> Una variabile $A$ è ***annullabile*** se $A\overset{*}{\implies} \epsilon$
> Sia $A$ annullabile, rimpiazziamo una regola del tipo $B\to \alpha A\beta$ con:
> $$B\to \alpha A\beta, \ B\to \alpha\beta$$

Rimpiazzando anche le nuove regole via via ottenute e cancellando tutte le regole con corpo $\epsilon$.

> Indichiamo con $n(G)$ l'insieme dei *simboli annullabili* di una grammatica $G=(V,T,P,S)$

> [!warning] Attenzione
> Questa trasformazione ***non mantiene lo stesso linguaggio***, in quanto non sarò più in grado di generare le stringhe $\epsilon$

###### Esempio
> Sia $G$ la grammatica: $S\to AB, \ A\to aAA \mid\epsilon, \ B\to bBB\mid\epsilon$

Identifico le variabili *nullable*:
- $n(G)=\{ A,B,S \}$

Applico quindi la ***regola di eliminazione*** per ciascuna variabile:
- $S\to AB\mid A\mid B$
- $A\to aAA\mid aA\mid aA\mid a$
- $B\to bBB\mid bB\mid bB\mid b$

Eliminiamo le regole con corpo $\epsilon$ e otteniamo la grammatica $G_{1}$:
$$
\begin{align}{}
& S\to AB\mid A\mid B \\
& A\to aAA \mid aA \mid a \\
& B\to bBB\mid bB\mid b
\end{align}
$$

### Eliminazione delle produzioni unità
> [!info] Produzione unità
> $A\to B$ è una produzione unità, nel caso in cui $A$ e $B$ siano ***variabili***.

Le produzioni unità possono essere eliminate ***senza cambiare il linguaggio***.

Si consideri la seguente [[#Context-Free Grammars|grammatica]]:
$$
\begin{aligned}
&E\to T\mid E+T \\
&T\to F\mid T*F \\
&F\to I\mid (E) \\
&I\to a\mid b\mid Ia\mid Ib\mid I0\mid I1
\end{aligned}
$$
- Ha le seguenti produzioni unità $E\to T,\ T\to F$ e $F\to I$

Consideriamo la produzione $E\to T$.
- Si trasforma tale produzione con il seguente ***procedimento a espansione***.

1. Si espande $E\to T$ ottenendo le produzioni:
$$
E\to F\mid T*F\mid E+T
$$
2. Con l'espansione ho ottenuto un'altra produzione unità, continuo a espandere:
$$
E\to I \mid (E)\mid E\to T*F\mid E+T
$$
3. Infine espando $E\to I$
$$
E\to a \mid b\mid Ia \mid Ib \mid I0 \mid I1 \mid (E) \mid T*F\mid E+T
$$

Ora si considerano le altre produzioni unità della grammatica ($T\to F$ e $F\to I$) e applichiamo lo stesso procedimento.

La ***nuova grammatica*** è la seguente:
$$
\begin{align}{}
& E \to a\mid b\mid Ia\mid Ib\mid I0\mid I1\mid (E)\mid T*F\mid E+T \\
& T \to a\mid b\mid Ia\mid Ib\mid I0\mid I1\mid (E)\mid T*F \\
& F \to a\mid b\mid Ia\mid Ib\mid I0\mid I1\mid (E) \\
& I \to a\mid b\mid Ia\mid Ib\mid I0\mid I1 \\
\end{align}
$$

> [!question] Questo procedimento funzione per qualsiasi grammatica?
>> [!fail] ***No!***
>
>Se ci sono cicli il procedimento non consente di giungere alla rimozione delle produzioni che ***continuano a generarsi***.

Ad esempio la grammatica: $A\to B,\ B\to C,\ C\to A$

> Serve una condizione di terminazione in *caso di cicli*.
- Se durante il procedimento si genera una produzione unità che sia ha già espanso ***la si può semplicemente rimuovere***.

###### Esempio
> Consideriamo la grammatica:

$$
\begin{align}
A\to B|a \\
B\to C|b \\
C\to A|c
\end{align}
$$
Espando $A\to B$ e ottengo le seguenti produzioni in successione:
$$
\begin{align}{}
&A\to C \mid b\\
&A\to A \mid c\mid b\\
&A\to B\mid a\mid c\mid b
\end{align}
$$
Mi posso fermare e eliminare $A\to B$ che ho ***già incontrato***.

> Eliminando anche le altre produzioni unità ottengo:

$$
\begin{align}
&A\to a\mid b\mid c \\
&B\to a\mid b\mid c \\
&C\to a\mid b\mid c \\
\end{align}
$$
- Dove $B$ e $C$ ***non sono raggiungibili*** e dunque possono essere rimosse.

## Proprietà di Decisione per CFL
---
> Di seguito analizzeremo i seguenti problemi decidibili:

> [!question] Se ho una grammatica libera $G$, riesco a decidere se una stringa $w$ appartiene al linguaggio $L(G)$?

> [!question] Riesco a verificare se il linguaggio $L(G)$ non è vuoto? 

### Appartenenza al linguaggio
> [!tldr] Prima tecnica inefficiente
> Supponiamo che $G$ sia in [[Forma Normale di Chomsky]] e che la stringa $w$ abbia lunghezza $|w|= n$.
> Visto che il suo albero sintattico è [[../../Algoritmi e Strutture Dati/Strutture Dati/Grafi/Alberi/Gli Alberi Binari|binaro]], ci sono $2n-1$ nodi interni.

Basta quindi generare *tutti* gli alberi sintattici di $G$ con $2n-1$ nodi interni e controllare poi se almeno uno genera $w$.

> [!fail] Problema
> Il numero di alberi possibili e quindi la [[../../Algoritmi e Strutture Dati/Confronto fra Algoritmi/Complessità di Algoritmi|complessità computazionale]] è ***esponenziale***.
#### Algoritmo CYK

> [!cite] Algoritmo Cocke Younger, Kasami
> L'algoritmo `CYK` permette di ***controllare l'appartenenza*** di una stringa $w$ a una grammatica e di ***trovare un suo albero sintattico*** in *tempo polinomiale*.
>> [!tldr] Si basa sulla costruzione induttiva di una tabella

> Assumiamo $G$ in `CNF` e che $w=a_{1}a_{2}\dots a_{n}$

Costruiamo una tabella triangolare, dove $X_{ij}$ è l'insieme delle variabili $A$ che permettono la ***generazione di un pezzo della stringa*** dal simbolo $i$ al simbolo $j$.
$$A\overset{*}{\underset{G}{\Rightarrow}} a_{i}a_{i^{1}}\dots a_{j}$$

![[attachements/CYKALgorithm.png]]

> Si riempie la tabella riga per riga, partendo dal basso verso l'alto

La prima riga è calcolata la ***passo base***, le successive tramite il ***passo induttivo***.

> ***Passo Base***
- $X_{ii}=\{ A:A\to a_{i} \in G\}$

> [!quote] In altre parole
> Tutte le variabili che mi portano ***direttamente*** al terminale $a_{i}$

> ***Passo Induttivo***
- Calcoliamo $X_{ij}$ (riga $j-i+1$)

Abbiamo che $A\in X_{ij}$  ***se e solo se***:
- $A \overset{*}{\Rightarrow} a_{i}a_{i+1}\dots a_{j}$, che equivale a dire che $A\to BC$ e per qualche $i\leq k < j$ abbiamo:
	- $B \overset{*}{\Rightarrow} a_{i}a_{i+1}\dots a_{k}$
	- $C \overset{*}{\Rightarrow} a_{k}a_{k+1}\dots a_{j}$

Questo equivale a controllare se esiste una produzione $A\to BC$ e un $i\leq k <j$ tale che $B\in X_{ik}$ e $C\in X_{(k+1)j}$

> [!quote] In altre parole
> Considero la stringa $w_{14}$ come la stringa che va dal carattere $1$ al $4$.
> Per derivare $w_{14}$ devo considerare ***tutti i modi di spezzarla*** in $2$:
> - $w_{11}$ e $w_{24}$
> - $w_{12}$ e $w_{34}$
> - $w_{13}$ e $w_{44}$
> Per ciascuna di queste combinazioni $w_{1x}$ e $w_{(x+1)4}$ devo controllare se ho una produzione $A\to BC$ con $B\in w_{1x}$ e $C\in w_{(x+1)4}$.
> Se ho una produzione che rispetta queste condizioni, *aggiungo* $A\in X_{14}$.

> [!check] L'obbiettivo è quello di calcolare $X_{1n}$
> Si ha $w\in L(G)\iff S\in X_{1n}$

#### Coppie di Insiemi
> Per calcolare $X_{ij}$ dobbiamo analizzare al più $n$ coppie di insiemi ***precedentemente calcolati***

$$
(X_{ii}, X_{(i+1)j}),(X_{i(i+1)}, X_{(i+2)j}),\dots,(X_{i(j-1)}, X_{jj})
$$

> [!quote] In altre parole
> Come suggerito dalla seguente immagine, per controllare tutte le divisioni possibili della string
> "***Salgo sulla verticale e scendo sulla diagonale***"

![[attachements/CYKDivisionTrick.png]]

Per $w=a_{1}\dots a_{n}$ ci sono $O(n^{2})$ insiemi $X_{ij}$ da calcolare.
- E visto che per calcolare ogni insieme bisogna analizzare $n$ coppie di insiemi:


> [!caution] Costo computazionale
> Il ***costo computazionale*** totale è quindi $O(n^{3})$

###### Esempio
> Consideriamo la grammatica $G$ con le seguenti produzioni
$$
\begin{aligned}
S&\to AB\mid BC \\
A&\to BA\mid a \\
B&\to CC\mid b \\
C&\to AB\mid a
\end{aligned}
$$


> [!summary] Passo Base
> Aggiungo alla riga $0$ gli insiemi di produzioni che mi generano il carattere "***sottostante***"

$$
\begin{array}{|lllll}
* & & & & \\ 
* & * & & & \\ 
* & * & * & & \\ 
* & * & * & * & \\ 
\{B\} & \{A,C\} & \{A,C\} & \{B\} & \{A,C\} \\ 
\hline
b & a & a & b & a
\end{array}
$$

> [!caution] Passo Induttivo
> Ora calcoliamo $X_{12}$

Posso dividere la stringa $ba$ in un solo modo:
- $b\mid a$

Gli insiemi corrispondenti sono $\{ B \}$ e $\{ A,C \}$
- Formo tutte le possibili coppie con $B$ a *sinistra* e $A$ o $C$ a *destra* 
- Controllo tutte le produzioni per vedere se ne ho una del tipo $P \to BA$ o $P\to BC$

Eseguo questo procedimento per ciascun insieme nella prima riga e ottengo:
$$
\begin{array}{|lllll}
* & & & & \\ 
* & * & & & \\ 
* & * & * & & \\ 
\{S,A\} & \{B\} & \{S,C\} & \{S,A\} & \\ 
\{B\} & \{A,C\} & \{A,C\} & \{B\} & \{A,C\} \\ 
\hline
b & a & a & b & a
\end{array}
$$

> Ora proviamo a completare $X_{25}$

$$
\begin{array}{|lllll}
* & & & & \\ 
* & * & & & \\ 
- & \{B\} & \{B\} & & \\ 
\{S,A\} & \{B\} & \{S,C\} & \{S,A\} & \\ 
\{B\} & \{A,C\} & \{A,C\} & \{B\} & \{A,C\} \\ 
\hline
b & a & a & b & a
\end{array}
$$
Ho $3$ modi di dividere la stringa $aaba$:
- $a\mid aba$ cioè gli insiemi già calcolati: $X_{22}$ e $X_{35}$
- $aa\mid ba$ : $X_{23}$ e $X_{45}$ 
- $aab\mid a$: $X_{24}$ e $X_{55}$

Per ogni coppia di insiemi trovati controllo le coppie di variabili $JK$ con $J\in X_{2x}$ e $K \in X_{(x+1)5}$ con $2\leq x < 5$.
Controllo se esistono le ***produzioni che generano***:
- $AB$ o $CB$
- $BS$ o $BA$
- $BA$ o $BC$

L'insieme $X_{25}$ sarà quindi: $\{ S,A,C \}$

> [!done] Procedo fino a $X_{15}$
> La ***tabella completa*** è la seguente

$$
\begin{array}{|lllll}
\{S,A,C\} & & & & \\ 
- & \{S,A,C\} & & & \\ 
- & \{B\} & \{B\} & & \\ 
\{S,A\} & \{B\} & \{S,C\} & \{S,A\} & \\ 
\{B\} & \{A,C\} & \{A,C\} & \{B\} & \{A,C\} \\ 
\hline
b & a & a & b & a
\end{array}
$$


