> La [[Legge di Gravitazione|forza gravitazionale]] è una [[Lavoro di una Forza#Forze Conservative e Non Conservative|forza conservativa]]. 

Si dimostra che ***qualsiasi traiettoria*** chiusa può essere *suddivisa* in spostamenti infinitesimi che sono sempre o *radiali* o *perpendicolari* alla **direzione radiale**.
$$
\delta\mathscr{L}=\vec{F}\cdot\text{d}\vec{s}=-G \frac{m_{1}m_{2}}{r^2}\hat{r}\cdot\text{d}\vec{s}
$$
- Ma $\hat{r}\cdot\text{d}\vec{s}$ è pari alla proiezione di $\text{d}\vec{s}$ su $\hat{r}$ è pari a $\text{d}r$

La variazione tra i due corpi a seguito dello ***spostamento*** $\text{d}\vec{s}$.

*Quindi*
$$
\mathscr{L}=\int _{A}^B\delta\mathscr{L}= \int _{r_A}^{r_B}-G \frac{m_{1}m_{2}}{r^2}\text{d}r=-Gm_{1}m_{2}\left( -\frac{1}{r_{B}}+\frac{1}{r_{A}} \right) 
$$

Definiamo quindi
$$
U(r)=-G \frac{m_{1}m_{2}}{r}
$$
Dove $U\to 0$ per $r\to \infty$

Con questa convenzione, possiamo distinguere ***tre situazioni***:

>[!help] $E>0$
>Il corpo si può portare a *qualunque distanza* dal sole.
>- Si può dimostrare che in questo caso la traiettoria è un ***iperbole***.

>[!caution] $E=0$
>Non ci sono limiti alla distanza dal sole che il *corpo può raggiungere*, anche se **raggiungerebbe** distanza ***infinita*** con *velocità nulla*.
>- Si può dimostrare che in questo caso la traiettoria è una ***parabola***.

>[!abstract] $E<0$
>Esiste una ***distanza massima*** a cui il corpo può portarsi.
>- Si può dimostrare che in questo caso la traiettoria è una ***ellissi***.


```functionplot
---
title: 
xLabel: 
yLabel: 
bounds: [0,10,-8,2]
disableZoom: true
grid: true
---
f(x)=-1/x
u(r)=-1
```

## Velocità di Fuga
---
>Per mezzo dell’energia potenziale gravitazionale è molto semplice calcolare la velocità di ***fuga di un oggetto***.

>[!tldr] Velocità di Fuga
>Con ***velocità di fuga*** si intende la *velocità minima* che un corpo deve avere, partendo da un certo punto di un campo di [[Legge di Gravitazione|forza gravitazionale]], per riuscire a “*liberarsi*” dal campo.

Dato che la forza di gravità ha un ***raggio d'azione infinito***, singnifica riuscire a portarsi a ***distanza infinita***.

> Consideriamo un corpo lanciato dalla superficie terrestre

>[!question] Qual è la velocità minima per cui tale corpo non ricadrà sulla terra?

È sufficiente che il corpo abbia un'[[Energia#Energia Meccanica|energia meccanica]] ***positiva o uguale a zero***.
$$
\frac{1}{2}mv_{f}^2-G \frac{mM_{T}}{R_{T}}=0\quad\implies\quad v_{f}=\sqrt{  2G \frac{M_{T}}{R_{T}}}
$$
- Inserendo i valori noti per la *terra* si ottiene $v_{f}\simeq 11.2\  km/s$

>[!hint] Osservazione
>All'*aumentare* di $M$ e al *diminuire* di $R$ si ottengono valori di via via ***più grandi***.
>>[!danger] Sappiamo che in natura esiste una ***velocità limite***.

La [[Misurazione#Sistema Internazionale|velocità della luce]] nel vuoto $c\simeq 3\times 10^{8} m/s$

Esistono combinazioni di $M$ e $R$ che producono una velocità di fuga teorica maggiore di $c$, con la conseguenza che ***nessun corpo*** che si *trovi* a $r<R$ può effettivamente **fuggire dal campo gravitazionale**.

>[!help] Raggio di Schwartzchild
>Il raggio corrispondente a $v_{f}=c$ per una data massa $M$ si chiama ***Raggio di Schwartzchild*** e si ottiene sostituendo $v_{f}=c$ e ricavando $R$
>$$R_{c}=\frac{2GM}{c^2}$$

Se un oggetto di massa $M$ si trasforma in un *buco nero*, l'***orizzonte degli eventi*** di tale buco nero avrà raggio $R_{c}$.

>[!example] Esempi

> Per un oggetto di massa pari a quella del **sole**:
- Il *Raggio di Schwartzchild* è pari a circa $3 \ km$

> Per un oggetto di massa pari alla **terra**:
- Il *Raggio di Schwartzchild* è pari a circa $9 \ mm$

> Per un oggetto di massa $70\ kg$ (persona media):
- Il *Raggio di Schwartzchild* è pari a circa $10^-25 \ m$

## Massa Inerziale e Massa Gravitazionale
>La ***massa gravitazionale***, $mg$ , può essere *diversa* dalla ***massa inerziale*** che compare nella [[Leggi di Newton#Seconda Legge di Newton|seconda legge di Newton]].

>[!summary] Massa Inerziale
>La *massa* $m_{i}$ usata nella ***legge di Newton***.
>È la **resistenza** che un corpo oppone al cambiamento della velocità.

>[!help] Massa Gravitazionale
>Massa $m_{g}$ usata nella ***legge di gravitazione universale***.
>Rappresenta la quantità di materia *sorgente della forza gravitazionale*.

>[!danger] Sono due concetti separati!

Dovremmo aggiungere un pedice "$i$" per ricordare che questo è valore dell’***inerzia del corpo***.
$$
\vec{F}=m_{i}\vec{a}
$$
>[!question] Il problema della possibile differenza tra mg mi e non è di natura filosofica, ma sperimentale.

Supponiamo di avere realizzato un pendolo usando il ***campione di massa di platino-iridio di Sevres***.
- Scriviamo l'*equazione del moto*.

$$
\begin{array}
\ \vec{P}=m_{g}\vec{a} \\
m_{g}^{Pl}g\sin\theta=-m_{i}^{Pl}l \displaystyle{\frac{\text{d}^2\theta}{\text{d}t^2}}
\end{array}
$$
con *soluzione*:
$$
T^{Pl}=2\pi\sqrt{ \frac{m_{i}^{Pl}}{m_{g}^{Pl}}\cdot \displaystyle{\frac{l}{g}} }
$$
Supponiamo che per questo campione si abbia $m_{i}^{Pl} \equiv m_{g}^{Pl}$.
- Ora utilizzo per realizzare il pendolo un secondo oggetto che abbia la ***stessa massa gravitazionale*** ma costituito di *ferro*.

In generale, potrebbe essere che:
$$
\frac{m_{g}^{Fe}}{m_{i}^{Fe}}\neq \frac{m_{g}^{Pl}}{m_{i}^{Pl}}
$$
Quindi il [[Le Forze#Il Pendolo Semplice|periodo di oscillazione]] di un ***pendolo di ferro sarebbe***:
$$
T^{Fe}=2\pi\sqrt{ \frac{m_{i}^{Fe}}{m_{g}^{Fe}}\cdot \displaystyle{\frac{l}{g}} }\neq T^{Pl}
$$
>[!todo] È possibile realizzare esperimenti di questo tipo usando diversi pendoli campione.

Oggi si continua a fare esperimenti raggiungendo limiti del tipo $R\lesssim 10^{-12}$

>[!summary] Principio di Equivalenza
>Il fatto che $m_{g}=m_{i}$ è uno dei ***pilastri fondamentali della teoria di Einstein*** della gravità, detto ***principio di equivalenza***.

Finora *mai smentito*.