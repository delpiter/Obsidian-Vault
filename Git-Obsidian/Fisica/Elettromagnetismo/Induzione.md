## Legge dell'Induzione
---
>[!tldr] Idea
>Sperimentazioni con [[Magnetismo|campi magnetici]] e *circuiti* portano a capire che il movimento relativo di un ***magnete***/***circuito*** induce una [[Circuiti/Corrente Elettrica|corrente]].

Faraday conclude che gli effetti sono dovuti alla ***variazione temporale*** del [[Flusso di un Campo Vettoriale|flusso]] magnetico $\vec{B}$.

>[!cite] Legge di Faraday
>$$\mathscr{E}_{ind}=-\displaystyle{\frac{\text{d}\phi(\vec{B})}{\text{d}t}}$$

### Induzione dovuta al Moto
>[!info]
> Il filo si *muove verso destra* a velocità $\vec{v}$.
> Sui portatori di carica in quel tratto agisce una [[../Leggi di Newton e le Forze/Leggi di Newton#Seconda Legge di Newton|forza]] $\vec{F}=q\vec{v}\times\vec{B}$

![[attachements/InduzioneMoto.svg]]

> Ora calcolo il flusso del campo $\vec{B}$

$$
\phi(\vec{B})=BlA
$$
- Dove $A$ è l'area del circuito: $x\cdot l$
 
>[!warning] Attenzione, $x$ è in funzione del tempo

$$
\displaystyle{\frac{\text{d}\phi}{\text{d}t}}=Bl\displaystyle{\frac{\text{d}x}{\text{d}t}}=Blv
$$

> La corrente indotta sarà quindi:

$$
\mathscr{E}_{ind}=Blv \quad [\text{volt}]
$$

### Campi Elettrici Indotti
>[!caution] Situazione
>Pensiamo ad una **spira** di raggio $R$ ferma immersa in un **campo** $\vec{B}$ *variabile*.

$$
|\vec{B}| = B=B(t)
$$
- Possiamo notare che è presente: $\displaystyle{\frac{\text{d}\phi(\vec{B})}{\text{d}t}}$

> È quindi presente anche in questo caso una corrente indotta $\mathscr{E}_{ind}$

$$
\phi(\vec{B})=B(t)S=B(t)\pi R^{2}
$$
Applicando la ***legge di Faraday***:
$$
\mathscr{E}_{ind}=-S\displaystyle{\frac{\text{d}\vec{B}}{\text{d}t}}
$$
>[!example] Esempio

> $B(t)=B_{0}+kt$

La sua derivata rispetto al tempo sarà:
$$
\displaystyle{\frac{\text{d}B}{\text{d}t}}=k
$$
- Quindi:
$\mathscr{E}_{ind}=kS$