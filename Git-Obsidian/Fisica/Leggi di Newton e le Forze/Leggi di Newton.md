## Prima Legge di Newton
---
>[!cite] Legge di Inerzia
>Se un corpo non interagisce (applica forze) con altri corpi, si può trovare un *sistema di riferimento* nel quale la sua [[Moto Rettilineo#Accelerazione|accelerazione]] è nulla.
>- Tale sistema di riferimento è detto ***inerziale***.
>
>>[!quote] Formulazione Alternativa
>>In *assenza di forze esterne* e se osservato da un **sistema di riferimento inerziale**, un corpo in quiete *resta in quiete* e un corpo in moto *continua* con [[Moto Rettilineo#|moto rettilineo uniforme]].

>[!done] La forza è ciò che provoca la variazione di moto di un corpo.

La *prima legge di Newton* è fondamentale esattamente per definire i ***sistemi di riferimento inerziali***.

>[!hint] Sistema di Riferimento Inerziale
>Un sistema di riferimento è ***inerziale*** quando un corpo non soggetto a forze esterne *non ha accelerazione* in tale sistema di riferimento.

Le successive *leggi di Newton* sono formulate **considerando sistemi di riferimento inerziali**.
## Seconda Legge di Newton
---
### La Massa
>[!definizione] Definizione
>La ***massa*** è la proprietà di un corpo che rappresenta quanta resistenza esso oppone ai *cambiamenti di velocità*.

Se applico la stessa forza a due corpi $1$ e $2$ e se misuriamo le accelerazioni $a_{1}$ e $a_{2}$, si definisce:
$$
\frac{m_{1}}{m_{2}}=\frac{a_{2}}{a_{1}}
$$
>[!Help] Rapporto
>Le **masse** sono *inversamente proporzionali* rispetto all'*accelerazione*.
>>[!quote] Significato
>>"Più il corpo ha **massa** meno sarà la sua **accelerazione** a fronte di un'applicazione di una forza"

La *massa* di un corpo è una sua ***proprietà intrinseca***.
### Legge
>[!question] Cosa succede ad un corpo se su di esso agiscono forze?

> In base alle osservazioni vediamo che:

$$
\vec{F}\propto \vec{a}
$$
Discutendo la *massa* si è osservato che:
- $|\vec{a}|\propto \displaystyle\frac{1}{m}$

Quindi possiamo concludere che:
$$
\vec{a}\propto \frac{\sum\vec{F}}{m}
$$
- $\sum\vec{F}$ rappresenta la somma di tutte le forze che agiscono sul corpo e si chiama ***forza risultante***.

> Scegliamo la costante di proporzionalità pari all'unità.

>[!cite] Principio di Proporzionalità
>La *forza risultante* che agisce su un corpo è ***direttamente proporzionale*** alla massa del corpo e all'accelerazione che esso subisce.
>$$\sum\vec{F}=m\vec{a}$$

> Usando le componenti cartesiane:

$$
\begin{cases}
\sum\vec{F}_{x}=ma_{x} \\
\sum\vec{F}_{y}=ma_{y} \\
\sum\vec{F}_{z}=ma_{z}
\end{cases}
$$

>[!help] Unità di Misura
>L'unità di misura della forza è il ***Newton***.
>$$1N=1\ kg\ m/s^2$$
>$$[F]=MLT^{-2}$$

## Terza Legge di Newton
---
> Le forze sono *interazioni tra due corpi*.

>[!cite] Legge di Azione e Reazione
>A ogni ***azione*** corrisponde una ***reazione*** uguale e contraria.
>>[!quote] Conservazione della quantità di Moto

Se due corpi interagiscono tra loro, la forza $\vec{F}_{12}$ esercitata dal corpo $1$ sul corpo $2$ è ***uguale in intensità*** e ***direzione***, ed ***opposta in verso***  alle forze $\vec{F}_{21}$ esercitate dal corpo $2$ sul corpo $1$
$$
\vec{F}_{12}=-\vec{F}_{21}
$$

>[!example] Esempi

Un proiettile in volo sente la ***forza gravitazionale della terra*** ed è accelerato verso il *basso*, mentre la terra sente la ***forza gravitazionale del proiettile*** ed è accelerata verso l'*alto* (Spostamento praticamente nullo).

### Quantità di Moto
> Introduciamo la ***quantità di moto***.

$$
\vec{p}=m\vec{v}
$$
>[!info]
>Considerando la massa di un punto materiale una **quantità costante**:
>$$\frac{\text{d}\vec{p}}{\text{d}t}=m\frac{\text{d}\vec{v}}{\text{d}t}=m\vec{a}$$

La seconda legge di Newton può essere scritta come:
$$
\sum\vec{F}=m\frac{\text{d}\vec{v}}{\text{d}t}
$$
> Se consideriamo una coppia di corpi interagenti, per la terza legge di Newton:

$$
\vec{F}_{12}=-\vec{F}_{21} \implies \frac{\text{d}\vec{p}_{2}}{\text{d}t}=-\frac{\text{d}\vec{p}_{1}}{\text{d}t}
$$
- Che può essere riorganizzato come:
$$
\frac{\text{d}\vec{p}_{2}}{\text{d}t}+\frac{\text{d}\vec{p}_{1}}{\text{d}t}=0\implies \displaystyle{\frac{\text{d}}{\text{d}t}(\vec{p}_{1}+\vec{p}_{2})}=0
$$
> Che significa che la quantità:

$$
\vec{P}=\vec{p}_{1}+\vec{p}_{2}=\text{costante}
$$
La chiameremo ***quantità di moto totale*** e resta *costante* a seguito di interazioni tra i due corpi.

>[!hint] Conclusione
>Se ci sono solo interazioni *interne* al sistema, cioè ciascun corpo del sistema risente **esclusivamente** di forze causate da altri corpi dello *stesso sistema*, la ***quantità di moto totale si conserva***.

La conservazione della quantità di moto, *implicita nelle leggi di Newton*, è una delle ***leggi fondamentali di conservazione della natura***.
