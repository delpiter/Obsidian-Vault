## Prove di $NP$ Completezza
---
>[!attention] Tentativo Facile
>Mostrare che una *funzione* $f$ è in $NP$, quindi mostrare che $g\leq_{p}f$ per ***qualche problema*** $g$ che è già noto essere $NP$-***Completo***

### Circuit-SAT

>[!info] Problema
>Trovare un assegnamento alle variabili di ingresso, che rende vera l'uscita
>>[!done] Intuitivamente
>>È più o meno come dire che è possibile rappresentare il problema con un circuito elettrico binario

#### Esempi di Prove
>*Dati un grafo $G$ e un intero $n$ stabilire se esiste un sottografo completo di $G$ di $n$ vertici*

>[!caution] Prova di $NP$-*Completezza*

Si parte da [[../../Definizioni/Definizioni_Algoritmi#Conjunctive Normal Form|SAT]] e si assume di sapere già che ***SAT*** è $NP$-***Completo***
##### Clique
>[!info] Problema
>Dato un grafo $G=(V,E)$, un sottoinsieme $S$ dei suoi vertici forma una ***clique*** se ogni coppia di vertici $S$ è connessa

###### 3-SAT $\leq_{p}$ Clique
>[!abstract] Parametri
>Formula $\phi=C_{1}\wedge C_{2}\wedge\dots\wedge C_{k}$, $k$ clausole
>***3 Disgiunti*** per ogni clausola: $(x_{1}\vee x_{2}\vee ¬x_{3})\wedge\dots$
>*Grafo*:
>- Un ***vertice per ogni letterale*** di ogni clausola
>- Un arco fra due vertici se corrispondenti a:
>	- Letterali di ***clausole diverse***
>	- Variabili ***Compatibili***

![[attachements/3sat-Clique.png]]
>[!Teorema]
>$\phi$ è soddisfacibile $\iff G$ ha una clique di $k$ vertici
>>[!abstract] Dimostrazione
>>>$\phi$ è soddisfacibile $\implies$
>>
>>Se $\phi$ è soddisfacibile, allora $\forall C_{r},\exists \mathcal{l}_{i}^r$, un letterale che vale $1$
>>Il letterale $\mathcal{l}_{i}^r$ corrisponde a un vertice $v_{i}^r$
>><u>Allora</u>
>>$V'=\{ v_{i}^r \}$ è una clique
>>- Per $r\neq s$, $\mathcal{l}_{i}^r$ è compatibile con $\mathcal{l}_{i}^s$
>>
>>>$G$ ha una clique di $k$ vertici $\impliedby$
>>
>>Nessun arco in $G$ connette vertici di una tripla.
>>$V'$ ha un vertice per tripla, $v_i^r$
>>Si può porre $\mathcal{l}_{i}^r=1$


#### Riduzione Clique $\leq_{p}$ Vertex Cover
>[!info] Complemento di un Grado
>Dato un grafo $G$, se $G'$ è il grafo complementare di $G$, allora ogni coppia di nodi è connessa in $G'\iff$ non è connessa in $G$
>- $G'=(V,E')$ è complemento di $G=(V,E)\implies (u,v)\in E'\iff(u,v)\notin E$

>[!abstract] Problema: Vertex Cover
>$$min|S|,\quad S\subseteq V : \forall(u,v)\in E \to u\in S \text{ e/o } v\in S$$
>>[!done] Ogni arco  del grafo ha almeno un estremo in $S$
>
>>[!caution] Input 
>>$<G,k>$ di una ***Clique***
>
>>[!todo] Output
>>Sia $G'$ il complemento di $G$
>>$<G',|V|-k>$ di ***vertex Cover***
>
>>[!done] Teorema
>>$G$ ha una clique di dimensione $k$ $\iff$ $G'$ ha una copertura di dimensione $|V|-k$

>***Problema***

Dato un grafo non orientato $G=(V,E)$ e un intero $k$:
>[!question] C'è un sotto insieme di vertici $S\subseteq V$ tale che $|S|\leq k$ e per cui se $(v,w)\in E$ allora $v\in S$ oppure $w\in S$ oppure entrambi?

![[attachements/VertexCover1.png|500]]
>*C'è un vertex cover di dimensione 4?*
>- *Si*

![[attachements/VertexCover2.png|500]]

##### Riduzione a Clique
>[!abstract] Clique $\leq_{p}$ Vertex Cover
>Dato un grafo non orientato $G=(V,E)$, e il suo complemento $G'=(V',E')$, dove $E'=\{ (v,w):(v,w)\notin E \}$
>>[!done] $G$ ha una clique di dimensione $k\iff G'$ ha un vertex cover di dimensione $|V|-k$

![[attachements/Clique-VertexCover.png]]

###### Dimostrazione
>$\implies$

Ipotesi: $G$ ha una clique $S$ con $|S|=k$
- Consideriamo $S'=V-S$
- $|S'|=|V|-k$

>[!abstract] Per dimostrare che $S'$ è un *vertex cover*:

Consideriamo un qualunque arco $(v,w)\in E'$
- Almeno uno fra $v$ e $w$ non è in $S$, dato che $S$ è una clique
- Almeno uno fra $v$ e $w$ è in $S'$
>[!done] $(v,w)$ è coperto da $S'$


>$\impliedby$

Ipotesi: $G'$ ha una cover $S'$ con $|S'|=|V|-k$
- Consideriamo $S=V-S'$
- Chiaramente $|S|=k$
>[!abstract] Per mostrare che $S$ è una *clique*:

Consideriamo un arco $(v,w)\in E'$
- Se $(v,w)\in E'$ allora $v\in S'$ e/o $w\in S'$
- Se $v\notin S'$ e $w\notin S'$, allora $(v,w)\in E$

>[!done] $S$ è una *clique* in $G$