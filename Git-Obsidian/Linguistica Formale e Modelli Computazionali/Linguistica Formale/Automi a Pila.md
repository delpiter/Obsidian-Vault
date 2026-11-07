## Pushdown Automaton
---
> [!abstract] Definizione
> Un automa a pila (***Pushdown Automaton*** `PDA`) è un $\epsilon$-[[Automi a Stati Finiti non Deterministici#Definizione Induttiva|NFA]] con una pila.

In una transizione un `PDA`:
1. Consuma un simbolo di input o esegue una transizione $\epsilon$.
2. Va in un nuovo stato (o rimane nello stesso).
3. Rimpiazza la cima della pila con una stringa
	- Consuma il carattere in cima e mette al suo posto una stringa.

![[attachements/StackAutomata.png]]

Il ***pushdown automaton*** è un automa a stati finiti non deterministico con transizioni $\epsilon$ ammesse e una *capacità aggiuntiva*
- una pila su cui può memorizzare una stringa di simboli.

> [!help] Osservazione
> La ***presenza di una pila*** significa che, a differenza dell'automa a stati finiti, l'automa a pila può "*ricordare*" una quantità infinita di informazioni.

Abbiamo un controllo a stati finiti e una serie di comandi per gestire la pila.
##### Esempio
> Sia

$$
L_{wwr}=\{ ww^{R}:w\in\{ 0,1 \}^{*} \}
$$
Con grammatica:
- $P\to 0P0\mid 1P1 \mid \epsilon$
un `PDA` per $L_{wwr}$ ha ***tre stati*** e funziona come segue:
1. Legge $w$ un simbolo alla volta, rimanendo nello stato $q_{0}$ e aggiungendo il simbolo di input alla pila.
2. Decide ***non deterministicamente*** che sta nel mezzo di $ww^{R}$ e va nello stato $q_{1}$
3. Legge $w^{R}$ un simbolo alla volta e lo paragona con il simbolo nella cima della pila.
	1. Se sono uguali esegue un `pop` e rimane nello stato $q_{1}$ altrimenti si blocca.
4. Se la pila non ha più simboli ($0$ o $1$) va nello stato $q_{2}$ e *accetta*.

Il `PDA` per $L_{wwr}$ come diagramma di transizione è il seguente.

![[attachements/PalindromeAutomata.png]]

Cosa rappresenta la transizione $0, Z_{0}/ 0Z_{0}$:
- Prima della "$,$" è il carattere di input ($0$), se uso la transizione lo "*consumo*"
- Chiedo che $Z_{0}$ sia nella cima della pila (e lo rimuovo $Z_{0}$)
	- Se $Z_{0}$ è nella pila significa che l'a transizione era "*attiva*" eseguo il push di $Z_{0}$ e $0$ nella pila.
	- Altrimenti non posso usare la transizione.

> [!attention] A parole
> Sia una ***transizione*** $(w, A/B)$ richiedo che in cima alla pila ci sia il carattere $A$, lo rimuovo e al suo posto inserisco la stringa $B$, eseguendo i singoli push dei caratteri partendo da destra a sinistra.
### Definizione Formale
> [!cite] Pushdown Automaton
> Un `PDA` è una tupla di $7$ elementi:
> $$P=(Q,\Sigma, \Gamma, \delta, q_{0},Z_{0},F)$$

> Dove:
- $Q$ è un insieme finito di ***stati***
- $\Sigma$ è un alfabeto finito di ***input***
- $\Gamma$ è un alfabeto finito di ***pila***
- $\delta$ è una **funzione di transizione** da $Q\times (\Sigma\cup\{ \epsilon \})\times \Gamma$ a sottoinsiemi di $Q\times\Gamma^{*}$
	- $\delta(q,a,Z_{0})=\{ (q,X_{0}\dots X_{n} )\}$ significa parto da $q$, consumo il carattere in input $a$, richiedo il carattere $Z_{0}$ sulla cima della pila, arrivo in uno stato $q$ aggiungendo sulla pila i caratteri $X_{0}\dots X_{n}$ con $n\geq 0$ ($n=0 \implies X_{0}\dots X_{n}=\epsilon$)
- $q_{0}$ è lo **stato iniziale**
- $Z_{0}\in\Gamma$ è il **simbolo iniziale** per la pila
- $F\subseteq Q$ è l'insieme di **stati di accettazione**

##### Esempio
> Il `PDA`

![[attachements/PalindromeAutomata.png]]

è la $7$-tupla
$$
P=(\{ q_{0},q_{1},q_{2} \}, \{ 0,1 \},\{ 0,1,Z_{0} \},\delta, Z_{0},\{ q_{2} \})
$$
Dove $\delta$ è la tabella seguente:
![[attachements/DeltaFunctionTablePDA.png]]

### Descrizioni Istantanee
> Un `PDA` passa da una configurazione ad un'altra:
- Consumando un simbolo di input (o tramite transizione $\epsilon$)
- Consumando la cima dello stack sostituendo con una stringa (eventualmente vuota).

> [!abstract] Definizione
> Per ragionare sulle computazioni dei `PDA`, usiamo delle ***descrizioni istantanee*** (`ID`) del `PDA`.

Una `ID` è una tripla $(q,w,\gamma)$ dove:
- $q$ è lo stato
- $w$ l'input rimanente
- $\gamma$ il contenuto intero della pila

> Sia $P=(Q,\Sigma,\Gamma,\delta,q_{0},Z_{0},F)$ un `PDA`, allora $\forall w\in\Sigma^{*},\beta\in\Gamma^{*}$:

$$
(p,\alpha)\in\delta(q,a,X)\implies (q,aw,X\beta) \vdash (p,w,\alpha\beta)
$$

Definiamo $\vdash^{*}$ la chiusura riflessiva e transitiva di $\vdash$

##### Esempio
> Prendiamo l'input $1111$ sul seguente `PDA`

![[attachements/PalindromeAutomata.png]]


> [!hint] Osservazione
> La stringa ha le seguenti ***sequenze di computazioni***.

![[attachements/PDAExampleComputations.png]]

> Ora prendiamo l'input $0110$ sul seguente `PDA`

>[!help] Osserviamo l'evoluzione dello stack mentre viene consumata la stringa

![[attachements/IsstantaneousDescriptions.png]]
### Tipologie di Accettazione
#### Accettazione per stato finale
> [!info] 
> Sia $P=(Q,\Sigma,\Gamma,\delta,q_{0},Z_{0},F)$ un `PDA`, il linguaggio accettato da $P$ per stato finale è:
> $$ L(P)=\{ w:(q_{0},w,Z_{0}) \vdash^{*}(q,\epsilon,\alpha), q\in F \}$$
> >

Una stringa appartiene al linguaggio quando partendo da uno stato iniziale, con un numero $\geq 0$  di descrizioni istantanee, ***arrivo ad uno stato finale***.
- La stringa deve essere *completamente consumata*
#### Accettazione per Pila Vuota
> [!info] 
> Sia $P=(Q,\Sigma,\Gamma,\delta,q_{0},Z_{0})$ un `PDA`, il linguaggio accettato da $P$ per pila vuota è:
> $$ L(P)=\{ w:(q_{0},w,Z_{0}) \vdash^{*}(q,\epsilon,\epsilon)\}$$

Una stringa appartiene al linguaggio quando partendo da uno stato iniziale, con un numero $\geq 0$  di descrizioni istantanee, ***svuoto la pila***.
- La stringa deve essere *completamente consumata*

> [!hint] Osservazione
> $q$ può essere uno stato qualunque, non esistono stati di accettazione.
> $P$ è una $6$***-tupla***, senza l'insieme degli stati finali.
#### Equivalenze
> Chiamiamo
- $P_{F}$ un `PDA` che accetta $L$ a ***stato finale***.
- $P_{D}$ un `PDA` che accetta $L$ a ***pila vuota***.
##### Da pila vuota a stato finale
> [!cite] Teorema
> Se $L=N(P_{N})$ per un `PDA` $P_{N}=(Q,\Sigma,\Gamma,\delta_{N},q_{0},Z_{0})$ allora $\exists \text{ PDA } P_{F}$ tale che $L=L(P_{F})$

> Idea:

Introduco un ***marcatore di fondo*** $X_{0}$.
Aggiungo uno stato di accettazione collegato a tutti gli stati del `PDA` a pila vuota e uno iniziale collegato allo stato iniziale originale.
- Alla prima transazione aggiungo il ***marcatore di fondo*** (diverso dai caratteri $\in\Sigma$) alla pila.
	- $\epsilon,X_{0}/Z_{0}X_{0}$
	- In realtà la pila inizia con $X_{0}$ a cui viene aggiunto il ***carattere iniziale*** in cima.
- Tutte le transizioni allo stato finale rimuoveranno il *marcatore*.
	- $\epsilon, X_{0}/\epsilon$

![[attachements/EmptyStackToFinalState.png]]

###### Dimostrazione
> Sia $P_{F}=(Q\cup \{ p_{0},p_{f} \},\Sigma,\Gamma\cup \{ X_{0} \},\delta_{F},p_{0},X_{0},\{ p_{f} \})$

Dove
- $\delta_{F}(p_{0},\epsilon,X_{0})=\{ (q_{0},Z_{0}X_{0}) \}$, In questo stato iniziale, $P_{F}$ esegue una transizione spontanea allo stato iniziale di $P_{N}$, inserendo il carattere $X_{0}$ all'inizio della pila.
- Per ogni stato $q\in Q$, input $a\in\Sigma\cup\{ \epsilon \}$ e simboli di stack $Y\in\Gamma$, $\delta_{F}(q,a,Y)$ contiene tutte le coppie $\delta_{N}(q,a,Y)$.
	- Significa che $P_{F}$ simula le mosse di $P_{N}$ finché in cima alla pila c'è un simbolo di $\Gamma$.
- In aggiunta alla regola precedente $(p_{f},\epsilon)\in\delta_{F}(q,\epsilon,X_{0})$
	- Da qualunque stato $q$ se in cima alla pila c'è $X_{0}$ posso spostarmi senza legger input in $p_{f}$
##### Da stato finale a pila vuota
> Idea simile a quella precedente

> [!cite] Teorema
> Sia $L=L(P_{F})$ per un `PDA` $P_{F}=(Q,\Sigma,\Gamma,\delta_F,q_{0},Z_{0},F)$
> Allora $\exists$ un `PDA` tale che $L=N(P_{N})$

> Idea

Devo "*pulire*" la pila una volta che sono arrivato in uno stato di accettazione senza altri caratteri da consumare.

Come per la transizione da pila vuota a stato finale:
- Aggiungo inizialmente un ***carattere marcatore*** $X_{0}$ che non permette l'accettazione di stringhe nel caso che la pila si svuoti per caso.
	- $\epsilon,X_{0}/Z_{0}X_{0}$
- Aggiungo transizioni dagli stati finali ad uno **stato aggiuntivo** che accetta qualsiasi carattere (anche il marcatore) senza consumare input.
	- Questo stato avrà un autociclo "*svuotatore della pila*" $\epsilon, \text{any}/\epsilon$

![[attachements/FinalStateToEmptyStack.png]]
###### Dimostrazione
> Sia $P_{N}=(Q\cup \{ p_{0},p \},\Sigma,\Gamma\cup \{ X_{0} \},\delta_{N},p_{0},X_{0})$

Dove
- $\delta_{N}(p_{0},\epsilon,X_{0})=\{ (q_{0},Z_{0}X_{0}) \}$, iniziamo inserendo il carattere iniziale di $P_{F}$ nella pila e passare allo stato iniziale di $P_{F}$.
- Per ogni stato $q\in Q$, simboli di input $a\in\Sigma\cup\{ \epsilon \}$ e simboli di stack $Y\in\Gamma$, $\delta_{N}(q,a,Y)$ contiene tutte le coppie $\delta_{F}(q,a,Y)$.
	- Significa che $P_{N}$ simula le mosse di $P_{F}$.
- Per ciascun stato di accettazione $q\in F$ e per ogni simbolo dello stack $Y\in\Gamma\cup X_{0}$, $\delta_{N}(q,\epsilon,Y)$ contiene $(p,\epsilon)$.
	- Con questa regola, quando $P_{F}$ accetta una stringa, $P_{N}$ può iniziare a ***svuotare lo stack senza consumare altri input***.
- Per ciascun simbolo dello stack $Y\in\Gamma\cup X_{0}$, $\delta_{N}(p,\epsilon,Y)=\{ (p,\epsilon) \}$, una volta nello stato $p$, che succede solo quando $P_{F}$ ha accettato la stringa, $P_{N}$ rimuove tutti i simboli dallo stack, finché la pila è vuota.

## Deterministic Push Down Automaton
---
> [!abstract] Definizione
> Un [[#Pushdown Automaton|PDA]] $P=(Q,\Sigma,\Gamma,\delta,q_{0},Z_{0},F)$ è ***deterministico*** se e solo se:
> 1. Ogni $\delta(q,a,X)$ con $a\in \Sigma\cup\{ \epsilon \}$ contiene al più un elemento.
> 2. Se $\delta(q,a,X)$ non vuoto per un $a\in \Sigma$ allora $\delta(q,\epsilon,X)$ è vuoto.

> A parole
1. In ogni situazione l'automa ha al massimo una *mossa* possibile.
2. Partendo da uno ***stesso stato***, richiedendo uno ***stesso carattere*** nella pila, se ho una transizione, non posso averne un'altra con $\epsilon$ al posto di $a$.
### DPDA che accetta per stato finale
> Mostriamo che i linguaggi regolari $\subset L(DPDA) \subset CFL$ 

> [!cite] Teorema
> Se $L$ è regolare, allora $L=L(P)$ per qualche `DPDA` $P$

> ***Dimostrazione***

Dato che $L$ è regolare, esiste un DFA $A$ tale che $L=L(A)$
Sia
$$
A=(Q,\Sigma,\delta_{A},q_{0},F)
$$
Definiamo il `DPDA`
$$
P=(Q,\Sigma,\{ Z_{0} \},\delta_{P}, q_{0},Z_{0},F)
$$
dove $\delta_{P}(q,a,Z_{0})=\{ (\delta_{A}(q,a),Z_{0}) \}$ per tutti i $p,q \in Q$ e $a\in\Sigma$

### DPDA che accetta per pila vuota
> [!warning] Attenzione
> I `DPDA` che accettano per pila vuota ***riconoscono meno linguaggi***.

> [!cite] Teorema
> Dato un `DPDA` $P$ che accetta un linguaggio $L$ per **pila vuota**, esiste un `PDPA` $P'$ che accetta $L$ ***per stato finale***.

Basta applicare la trasformazione vista in precedenza #addLink, poiché preserva il determinismo.

Il viceversa però non vale.


> [!cite] Teorema
> Dato un `DPDA` $P$ che accetta $L$ per stato finale, esiste un `DPDA` $P'$ su $\Sigma \cup \{ \$ \}$ che accetta $L\{ \$ \}$ per pila vuota con $\$ \notin \Sigma$

Il simbolo speciale $\$$ dice che la stringa è finita e deve accettare ***svuotando la pila***.
- Nelle implementazioni dei parser/compilatori si usa il carattere speciale `EOF` che è **sempre in fondo ai files**.

### DPDA e non ambiguità
> Relazione tra riconoscimento deterministico e non ambigutià

> [!cite] Teorema
> Se $L=L(P)$ per qualche `DPDA` $P$ con accettazione per stato finale, allora $L$ ha una `CFG` $G$ ***non ambigua***

> Dimostrazione

Esiste un `DPDA` $P'$ che accetta $L\{ \$ \}$ con $\$ \notin \Sigma$ per pila vuota.
- Applico a $P'$ la costruzione vista da `PDA` a `CFG`
- Essendo $P'$ deterministico, mi da' una `CFG` $G'$ con **derivazioni a sinistra uniche per ogni stringa**.

Ora modifico $G'$ in $G$ tale che $L(G)=L$ aggiungendo la produzione $\$\to\epsilon$ e considero $\$$ una variabile iniziale anziché terminale.


> [!warning] Il viceversa non vale

Il linguaggio delle stringhe palindrome con alfabeto $\{ 0,1 \}$ ha una grammatica non ambigua ma non appartiene $L(DPDA)$.
- $L(DPDA)$ è una sottoclasse stretta dei `CFL` aventi grammatiche non ambigue.