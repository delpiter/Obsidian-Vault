## Espressioni Regolari
--- 
> Un ***Finite Automaton*** ([[Automi a Stati Finiti Deterministici|DFA]] o [[Automi a Stati Finiti non Deterministici|NFA]]) è un metodo per costruire una macchina che riconosce [[Linguaggi Regolari|linguaggio regolare]].

> [!abstract] Espressioni Regolari
> Una ***espressione regolare*** è un modo dichiarativo per descrivere un linguaggio regolare.

> Esempio
- $01^{*}+10^{*}$

Usate in contesti come:
- Comandi `UNIX` (`{sh icon} grep`).
- Strumenti per l'analisi lessicale dei linguaggi.

### Costruire le espressioni regolari

> [!abstract] Definizione induttiva

> ***Base***: $\epsilon$ e $\emptyset$ sono espressioni regolari
- Se $a\in\Sigma$, allora $a$ è un'espressione regolare $L(a)=\{ a \}$

> ***Induzione***:

- Se $E$ è un'espressione regolare allora $(E)$ è un'espressione regolare
$L((E))=L(E)$

- Se $E$ e $F$ sono espressioni regolari. allora $E+F$ è un'espressione regolare
$L(E+F)=L(E)\cup L(F)$

- Se $E$ e $F$ sono espressioni regolari allora $E.F$ è una un'espressione regolare
$L(E.F)=L(E).L(F)$

- Se $E$ è un'espressione regolare allora $E^{*}$ è un'espressione regolare
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
> Abbiamo già mostrato che `DFA`, `NFA` e $\epsilon$-`NFA` sono tutti equivalenti.

![[attachements/LanguageEquivalence.png]]


> [!hint] Per mostrare che gli ***FA*** sono equivalenti alle espressioni regolari dobbiamo stabilire che:

1. Per ogni `DFA` $A$ possiamo trovare un'***espressione regolare*** $R$ tale che $L(R)=L(A)$.
2. Per  ogni ***espressione regolare*** $R$ esiste un $\epsilon$-`NFA` $A$, tale che $L(A)=L(R)$.

##### Da DFA a espressioni regolari
> [!tldr] Idea
> Partendo da **espressioni semplici**, *archi* o *nodi singoli*, e via via per induzione si **costruiscono le espressioni** che fanno passare i cammini attraverso insiemi di stati via via più grandi.

Alla fine i cammini possono passare attraverso qualunque stato, in modo che le *espressioni generate* rappresentino ***tutti i cammini possibili***.

> [!cite] Teorema
> Per ogni `DFA` $A=(Q,\Sigma,\delta,q_{0},F)$ esiste una espressione regolare $R$ tale che $L(R)=L(A)$.

> Eliminazione iterativa degli stati

La figura mostra un generico stato $s$ che sta per essere ***rimosso***.
![[attachements/DFAtoRE.png]]

Tutti gli archi che comprendono lo stato $s$ vengono **rimossi** e per compensare, viene *introdotta* per ogni predecessore ($q_{i}$) di $s$ e ogni successore $(p_{j})$ una ***espressione regolare*** che rappresenta *tutti i percorsi* che partono da $q_{i}$, passano da $s$ e finiscono in $p_{j}$.
- L'espressione per questi percorsi è $Q_{i}S^{*}P_{j}$.

Questa espressione è aggiunta con l'operatore di unione all'arco da $q_{i}$ a $p_{j}$.
![[attachements/DFAtoREstep.png]]

> [!caution] Una volta rimossi tutti i nodi non di accettazione:

La strategia per costruire l'***espressione regolare*** è la seguente:
- Per ogni stato di accettazione $q$ applicare il processo di riduzione per creare un automa equivalente con espressioni regolari negli archi, eliminando tutti gli stati eccetto $q$ e lo stato iniziale $q_{0}$.
- Se $q\neq q_{0}$ allora si ha un automa con due stati come definito in figura.
- Se lo *stato iniziale* è uno ***stato di accettazione*** allora va fatto una ulteriore riduzione, mantenendo lo stato iniziale.
	- Una volta fatto questo, rimane uno *stato unico* con un **autociclo** che come etichetta contiene l'espressione regolare dell'automa.

![[attachements/DFAtoREfinal.png]]

L'automa corrisponde all'espressione regolare $E_{q}=(R+SU^{*}T)^{*}SU^{*}$

> Esempio

Dato il seguente `DFA` che rappresenta tutte le stringhe che **non** terminano con $01$, trasformiamolo in una ***espressione regolare***.

![[attachements/DFAtoREexample.png]]


> [!fail] Eliminazione

Iniziamo a eliminare tutti i nodi che **non sono di accettazione** ($q_{2}$).
- Prendiamo tutte le transizioni passanti per $q_{2}$ entranti e uscenti
	- **Predecessori**: $\{ q_{1} \}$
	- **Successori**: $\{ q_{0},q_{1} \}$

Analizziamo tutte le *combinazioni* che partono dai **predecessori** e arrivano ai **successori**.

| Predecessore | Successore | Espressione                      |
| ------------ | ---------- | -------------------------------- |
| $q_{1}$      | $q_{0}$    | $\emptyset + 1\emptyset^{*}1=11$ |
| $q_{1}$      | $q_{1}$    | $0+1\emptyset^{*}0=0+10$         |
Sostituendo le espressioni regolari ottenute ed eliminando il nodo $q_{2}$ si ottiene il seguente *automa*.

![[attachements/DFAtoREexample2.png]]

> [!hint] Sono tutti nodi di accettazione
> 

Fisso $q_{1}$, lo chiamo $A_{q1}$ e calcolo l'espressione regolare del `DFA` risultante.
- Non posso rimuovere $q_{0}$ poiché è nodo iniziale.
![[attachements/DFAtoREexample3.png]]

Usando la formula descritta in precedenza:
$$
E_{q1}=(1+0(0+10)^{*}11)^{*}.0(0+10)^{*}
$$

Ora fisso $q_{0}$ e lo chiamo $A_{q0}$

![[attachements/DFAtoREexample4.png]]

***Elimino*** il nodo $q_{1}$.
- **Predecessori**: $\{ q_{0} \}$
- **Successori**: $\{ q_{0}\}$

| Predecessore | Successore | Espressione         |
| ------------ | ---------- | ------------------- |
| $q_{0}$      | $q_{0}$    | $1 + 0(0+10)^{*}11$ |
L'automa diventa il seguente:

![[attachements/DFAtoREexample5.png]]

$$
E_{q0}=(1+0(0+10)^{*})^{*}
$$

> [!done] Espressione regolare finale
> L'espressione regolare del `DFA` dato è la seguente:
> $$ E_{fin}= E_{q0} + E_{q1} = (1+0(0+10)^{*})^{*}+(1+0(0+10)^{*}11)^{*}.0(0+10)^{*}$$