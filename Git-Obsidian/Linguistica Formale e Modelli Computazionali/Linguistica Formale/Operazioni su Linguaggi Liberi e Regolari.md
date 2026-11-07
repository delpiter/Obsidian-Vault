## Operazioni sui Linguaggi liberi e regolari
---
### Intersezione
> [!cite] Teorema
> Se $L$ è [[Grammatiche e Linguaggi Liberi dal contesto#Il linguaggio di una grammatica|CFL]] e $R$ è [[Linguaggi Regolari|regolare]] allora $L\cap R$ è `CLF`.

> ***Dimostrazione***

Sia $L$ accettato dal [[Automi a Pila|PDA]]:
- $P=(Q_{P},\Sigma,\Gamma,\delta_{P},q_{P},Z_{0},F_{P})$ per ***stato finale***

e sia $R$ accettato dal [[Automi a Stati Finiti Deterministici|DFA]]:
- $A=(Q_{A},\Sigma,\delta_{A},q_{A},F_{A})$

Costruiamo un `PDA` per $L\cap R$ secondo la figura:
![[attachements/PDA-FAIntersection.png]]

Formalmente definiamo:
$$
P'=(Q_{P}\times Q_{A},\Sigma,\Gamma,\delta,(q_{P},q_{A}),Z_{0},F_{P}\times F_{A})
$$
Dove:
$$
\delta((q,p),a, X)=\{ ((r,\hat{\delta}_{A}(p,a)),\gamma):(r,\gamma\in\delta_{P}(q,a,X)) \}
$$

### Differenza e Negazione
> [!cite] Teorema
> Siano $L,L_{1},L_{2}$  [[Grammatiche e Linguaggi Liberi dal contesto#Context-Free Grammars|CLF]] e $R$ [[Linguaggi Regolari|regolare]], *allora*:
> 1. $L\setminus R$ è una `CLF`
> 2. $\overline{L}$ non è necessariamente `CLF`
> 3. $L_{1}\setminus L_{2}$ non è necessariamente `CLF`

> ***Dimostrazione***

1. ***Differenza***

$\overline{R}$ è regolare, $L\cap \overline{R}$ è `CLF` e $L\cap \overline{R}= L\setminus R$.

2. ***Complementazione***

Se $\overline{L}$ fosse sempre `CLF`, seguirebbe che per la [[../../Architettura degli Elaboratori/Algebra di Bool e Logica Digitale/Algebra di Bool#Proprietà|legge di De Morgan]]
$$
L_{1}\cap L_{2}= \overline{\overline{L_{1}}\cup\overline{L_{2}}}
$$
sarebbe sempre `CLF`.

3. ***Differenza tra liberi***

Notare che $\Sigma^{*}$ è `CFL`, quindi se $L_{1}\setminus L_{2}$ fosse sempre `CLF` allora lo sarebbe sempre anche $\Sigma^{*}\setminus L = \overline{L}$

## Problemi Indecidibili per CLF
---
> I seguenti problemi ***sono indecidibili***
1. Una data [[Grammatiche e Linguaggi Liberi dal contesto#Context-Free Grammars|CFG]] $G$ è **ambigua**?
2. Un dato `CFL` $L$ è **inerentemente ambiguo**?
3. L'intersezione di due `CFL` è **vuota**?
4. Due `CFL` sono **uguali**?
5. Un `CFL` è **universale**? (uguale a $\Sigma^{*}$)

### Problemi indecidibili sui CFL: versione semplice
> [!info] Idea comune  
> Non serve ripartire da zero: **basta ridurre un problema indecidibile a un altro**. Se so che il problema di partenza non si può decidere, e posso trasformarlo nel nuovo problema, allora anche il nuovo non si può decidere.

#### 3. Intersezione vuota
> [!quote] In breve  
> È il problema "**base**" da cui partono gli altri: sapere se due `CFL` hanno qualcosa in comune è già **troppo difficile**.

I `CFL` ***non sono chiusi per intersezione***, e in generale non c'è modo di controllare algoritmicamente se due `CFL` *condividono una stringa*.
- Questo problema è indecidibile, e lo si usa come punto di partenza per gli altri.

> [!question] Perhcé?

Nei linguaggi regolari viene utilizzata la tecnica della [[Linguaggi Regolari#Intersezione|simulazione parallela]].
- Con i [[Automi a Pila|PDA]] questa tecnica non è possibile in quanto si dovrebbe poter utilizzare una pila sola per due automi.
#### 1. Ambiguità di una CFG
> [!quote] In breve  
> Se **unisco due grammatiche**, l'ambiguità appare *esattamente* quando hanno una ***stringa in comune***.

Date due grammatiche non ambigue $G_1$ e $G_2$, costruisco $S \to S_1 \mid S_2$.
- Una stringa ha *due derivazioni diverse* solo se è **generata da entrambe**.
- Quindi la nuova grammatica è ambigua se e solo se $L(G_1) \cap L(G_2) \neq \emptyset$.

>[!hint] Se sapessi decidere l'ambiguità, saprei decidere l'intersezione vuota.
#### 2. Ambiguità inerente
> [!quote] In breve  
> Stessa costruzione dell'ambiguità, ma ora l'ambiguità ***non può essere eliminata*** riscrivendo la grammatica.

> Si considera $L = L_1 \cup L_2$.

Se i due linguaggi ***sono disgiunti***, la grammatica $S \to S_1 \mid S_2$ è non ambigua, quindi $L$ non è inerentemente ambiguo.
- Se hanno stringhe in comune (in modo "robusto"), nessuna grammatica può evitare le doppie derivazioni.

>[!hint] Decidere l'ambiguità inerente permetterebbe di decidere l'intersezione vuota.
#### 5. Universalità
> [!quote] In breve  
> Il complemento trasforma "**intersezione vuota**" in "**contiene tutto**".

Si usano linguaggi deterministici, che sono chiusi per complemento.
- Considero $L' = \overline{L_1} \cup \overline{L_2}$.
- Per De Morgan, $L' = \Sigma^*$ se e solo se $L_1 \cap L_2 = \emptyset$.

>[!hint] Quindi decidere l'universalità permetterebbe di decidere l'intersezione vuota.
#### 4. Uguaglianza
> [!quote] In breve  
> L'uguaglianza ***contiene l'universalità*** come caso particolare.

Dato un `CFL` $L$, chiedo se $L = \Sigma^*$.
- Ma $\Sigma^*$ è un `CFL` (anzi **regolare**), quindi questa è una ***domanda di uguaglianza*** tra due CFL.

>[!hint] Se l'uguaglianza fosse decidibile, lo sarebbe anche l'universalità.