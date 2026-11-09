## Forma normale di Chomsky
---
> [!cite] Teorema
> Ogni `CFL` *non vuota* che *non include la stringa* $\epsilon$ è generato da una `CFG` dove ***tutte le produzioni*** sono della forma:
> $$A\to BC \qquad A\to a$$

> Con:
- $\{ A,B,C \}\subseteq V$
- $a \in T$

Per ottenerla si effettuano le seguenti trasformazioni su una qualsiasi grammatica per la `CFL`:
1. [[Grammatiche e Linguaggi Liberi dal contesto#Pulizia di un Linguaggio|Pulire la grammatica]]
2. ***Modificare le produzioni*** con $2$ o più simboli in modo tale che *siano tutte variabili*.
3. ***Ridurre il corpo delle regole*** di lunghezza superiore a $2$ in cascate di produzioni con corpi da $2$ variabili.

> [!summary] Passo 2
> Per il passo $2$ per ogni terminale $a$ che compare in un corpo di lunghezza $\geq 2$ creo una ***nuova variabile*** (es $A$) e *sostituisco* $a$ con $A$ in tutti i corpi e *aggiungo la nuova produzione* $A\to a$.

> [!caution] Passo 3
> Per il passo $3$ per ogni produzione nella forma $A\to B_{1}B_{2}\dots B_{k}$ con $k\geq 3$, ***introduciamo le nuove variabili*** $C_{1}, C_{2},\dots,C_{k-2}$ e sostituisco la regola con la seguente:

$$
A \to B_1C_1 \\
C_1\to B_2C_2 \\
C_2\to B_3C_3 \\
\dots \\
C_{k-3}\to B_{k-2}C_{k-2} \\
C_{k-2}\to B_{k-1}B_{k} \\
$$
Illustrazione dell'effetto del passo $3$:
![[attachements/ProductionBodyReduction.png]]

##### Esempio
> Iniziamo dalla grammatica ***già pulita*** in precedenza:

$$
\begin{align}{}
& E \to a\mid b\mid Ia\mid Ib\mid I0\mid I1\mid (E)\mid T*F\mid E+T \\
& T \to a\mid b\mid Ia\mid Ib\mid I0\mid I1\mid (E)\mid T*F \\
& F \to a\mid b\mid Ia\mid Ib\mid I0\mid I1\mid (E) \\
& I \to a\mid b\mid Ia\mid Ib\mid I0\mid I1 \\
\end{align}
$$


> [!todo] Per il passo $2$ usiamo le regole:

$$
\begin{matrix}
A\to a & P\to + \\
B\to b  & M\to * \\
Z\to 0  & L\to (\\
O\to 1  & R\to )\\
\end{matrix}
$$

E ***otteniamo la grammatica***:
$$
\begin{aligned}
&E\to EPT\mid TMF\mid LER\mid a\mid b\mid IA\mid IB\mid IZ\mid IO \\
&T\to TMF\mid LER\mid a\mid b\mid IA\mid IB\mid IZ\mid IO \\
&F\to LER\mid a\mid b\mid IA\mid IB\mid IZ\mid IO \\
&I\to a\mid b\mid IA\mid IB\mid IZ\mid IO \\
&A\to a \\
& B\to b \\
&Z\to0 \\
&O\to1 \\
&P\to+ \\
&M\to* \\
&L\to( \\
&R\to) \\
\end{aligned}
$$


> [!todo] Per il passo $3$ rimpiazziamo:

$$
E\to EPT \implies E \to EC_1,\,C_1\to PT \\
\\
E\to TMF,\,T\to TMF \implies E \to TC_2,\,T\to TC_2,\,C_2\to MF \\
\\
E\to LER,\,T\to LER,\,F\to LER \implies E \to LC_3,\,T\to LC_3,\,LC_3\to ER \\
$$

> [!done] La grammatica finale sarà:
> 

$$
\begin{aligned}
&E\to EC_1\mid TC_2\mid LC_3\mid a\mid b\mid IA\mid IB\mid IZ\mid IO \\
&T\to TC_2\mid LC_3\mid a\mid b\mid IA\mid IB\mid IZ\mid IO \\
&F\to LC_3\mid a\mid b\mid IA\mid IB\mid IZ\mid IO \\
&I\to a\mid b\mid IA\mid IB\mid IZ\mid IO \\
&C_1\to PT,\,C_2\to MF,\,C_3\to ER \\
&A\to a,\,B\to b,\,Z\to0,\,O\to1 \\
&P\to+,\,M\to*,\,L\to(,\,R\to)
\end{aligned}
$$

## Gerarchia delle grammatiche di Chomsky
---
> Chomsky ha definito una gerarchia di 4 grammatiche con restrizioni sempre più stringenti.
###### \* Produzioni Epsilon
> [!eccezione] 
> Viene permessa una possibile produzione $S\to \epsilon$ per il simbolo iniziale $S$ a patto che non ci sia una produzione $\alpha\to\beta$ con $S$ che appare in $\beta$  

Questo serve per rappresentare tutti i linguaggi che contengono la stringa $\epsilon$.
- Deve essere usabile solo all'inizio e non in mezzo alle altre derivazioni.

Una qualsiasi grammatica $G'$ che accetta $L(G')=L(G)\cup \{  \epsilon \}$ è ottenuta aggiungendo un nuovo simbolo iniziale $S'$ e le produzioni:
- $S'\to \epsilon$ e $S'\to S$

### Senza Restrizioni
> [!abstract] Unrestricted
> Una [[Grammatiche e Linguaggi Liberi dal contesto|Grammatica]] $G=(V,T,P,S)$ senza restrizioni nella forma delle produzioni, anche detta di ***Tipo 0***.

Le produzioni $P$ sono del tipo:
$$
\alpha \to \beta \in P, \qquad \alpha\in (V\cup T)^{+}, \ \beta \in (V\cup T)^{*}
$$
#### Metodo Riconoscitivo
> Il metodo riconoscitivo per i linguaggi generati da queste grammatiche sono le ***procedure***

> [!done] Procedura
> Una procedura ***termina*** e ***accetta*** se l'input appartiene al linguaggio.

Altrimenti *rifiuta* o *non termina*.
### Dipendenti dal Contesto
> [!attention] Context-Sensitive
> Le grammatiche ***dipendenti dal contesto*** (***Tipo 1***) restringono le produzioni a $\alpha \to \beta$ con $|\beta| \geq |\alpha|$ (\*)

In una grammatica dipendente dal contesto, facendo una qualsiasi produzione, la lunghezza della stringa ***non può diminuire***.

Una produzione dipendente dal contesto è del tipo:
- $\alpha_{1}A\alpha_{2} \to \alpha_{1}\beta\alpha_{2}$ con $A\in V$ e $\beta\in (V\cup T)^{+}$ e $\alpha_{1},\alpha_{2}\in(V\cup T)^{*}$

> **Esempio**: $L(G)=\{ a^{n}b^{n}c^{n}\mid n\geq 1 \}$

$$
\begin{align}
& S\to aSBc \mid aBC \\
& cB \to Bc \\
& aB \to ab \\
& bB\to bb
\end{align}
$$
Dove, in ordine le produzioni:
1. Genera le stringhe $a^{n}(Bc)^{n}$
2. Permette alle $B$ di essere spostate prima delle $c$
3. Cambia la $B$ più a sinistra in una $b$
4. Cambia tutte le altre $B$ in $b$ solo se sono adiacenti.
#### Metodo Riconoscitivo
> Il metodo riconoscitivo per i linguaggi generati da queste grammatiche sono gli ***algoritmi non deterministici***.

> [!done] Algoritmo non deterministico
> È una ***procedura che termina sempre*** con una complessità spaziale ***lineare***.
### Libere dal Contesto
>[!tip] Context-Free
> In una [[Grammatiche e Linguaggi Liberi dal contesto|grammatica libera dal contesto]] le produzioni sono del tipo:
> $A\to\beta$ con $A\in V$ e $\beta\in(V\cup T)^{+}$ (\*)

#### Metodo Riconoscitivo
> Il metodo riconoscitivo per i linguaggi generati da queste grammatiche sono gli [[Automi a Pila]] ***non deterministici***.
### Regolari
> [!help] Regular
> Le ***grammatiche*** [[Linguaggi Regolari|regolari]] hanno le produzioni del tipo:
> $A\to a$ oppure $A\to aB$ con $A,B\in V$ e $a \in T$ (\*)

#### Metodo Riconoscitivo
> Il metodo riconoscitivo per i linguaggi generati da queste grammatiche sono gli Automi a stati finiti [[Automi a Stati Finiti Deterministici|deterministici]] o [[Automi a Stati Finiti non Deterministici|non deterministici]].
