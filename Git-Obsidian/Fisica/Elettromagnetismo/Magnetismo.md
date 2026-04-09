> Fin dal $V$ secolo si conoscono le proprietà della ***magnetite***, capace di *attirare alcuni materiali*.

>[!summary] Magnetismo
>Il ***magnetismo*** è quel fenomeno per cui alcuni *materiali* sono in grado di attrarre altri *materiali ferrosi* nonché **trasmettere** tale **capacità** ad altri materiali.

Nel $1750$ misura la forza esercitata tra le estremità di due aghi, che va come:
$$\frac{1}{r^{2}}$$
>[!hint]
>I ***magneti*** hanno sempre due poli, detti $N$ e $S$
>- Poli *uguali* si **respingono** e poli *opposti* si **attraggono**.

Introdurremo un ***campo magnetico*** $\vec{B}$ per descrivere le cose.
Le linee di campo sono chiuse, dal polo $N$ al polo $S$.

*Spezzando un magnete*, nel tentativo di separare i poli, si ottengono **due magneti**, ciascuno con due poli.
- L'impossibilità di separare i poli equivale all'***assenza di carica magnetica***.

## Magnetismo e Corrente Elettrica
---
>[!info]
> Il ***campo magnetico*** è una manifestazione del *movimento* delle [[Elettromagnetismo#Cariche Elettriche|cariche elettriche]].

Quando una carica si muove, genera intorno a sé un ***campo magnetico***.
- I fenomeni magnetici ***non sono*** di natura *elettrostatica*.

> Biot e Savart Trovano che il campo generato da un filo percorso da corrente:

$$
B\propto \frac{i}{r}
$$
- $i:$ Corrente del Filo
- $r:$ Distanza dal Filo

### Forza di Lorentz
> Assumendo di determinare presenza e direzione di $\vec{B}$ con un *ago magnetico*, osserviamo l'***effetto su una particella carica***.

>[!info]
>- Se $\vec{v}=0$, non subisce forze.
>- Se $\vec{v}\parallel \vec{B}$, non subisce forze.
>- $\mid\vec{F}\mid$ Aumenta con angolo tra $\vec{v}$ e $\vec{B}$ ed è massima per $\vec{v}\perp \vec{B}$

>[!cite] Legge di Lorentz
>Con queste osservazioni si giunge alla ***legge di Lorentz***.
>$$\vec{F}=q\vec{v}\times\vec{B}$$

> Unità di misura

$[B]=\displaystyle\frac{N}{A\cdot m}$
## Moto delle Cariche nei Campi
---
> In presenza di entrambi i [[Campi Elettrostatici#^32aa5b|campi]] $\vec{E}$ e $\vec{B}$:

$$
\vec{F}=q\vec{E}+q(\vec{v}\times\vec{B})=q(\vec{E}+\vec{v}\times\vec{B})
$$
>[!hint]
>Se $\vec{E}=0$ e $\vec{B}$ è uniforme e ho $\vec{v}_{i}\perp \vec{B}$.
>- Ottengo un ***moto circolare*** nel piano $\perp \vec{B}$.
>$$\vec{F}\perp \vec{v} \implies \vec{a}\perp \vec{v} \implies |\vec{v}|=\text{cost}$$

> Accelerazione centripeta:

- $a=\displaystyle\frac{v^{2}}{r}$

$$
m \frac{v^{2}}{r}=\mid q \vec{v}\times \vec{B}\mid=\mid q\mid vB\sin(90^{\circ})
$$
- Se $q>0$ allora $=qvB$

$$
r=\frac{mv}{qB}
$$
> E si ottiene

$$
\omega=\frac{v}{r}=\frac{qB}{m}
$$
- Significa che la frequenza angolare dipende da $B$ e da $\frac{q}{m}$ ed è detta "***Frequenza di Ciclotrone***".

### Campo Magnetico e Quantità di Moto
>[!info]
>Negli esperimenti di particelle si può *misurare la loro traiettoria*.
>Inserendo un **campo magnetico** si determina la ***quantità di moto***.

> Visto che:

$$
r=\frac{mv}{qB}=\frac{p}{qB}\implies p=qBr
$$

#### Ciclotrone
>[!caution] Acceleratore di Particelle
>Strumento formato da:
>- Due elettrodi a forma di "***D***".
>- ***Campo Magnetico***.
>- Generatore di $\Delta$ di potenziale *alternato*.

Dentro le "***D***" la particella non sente il ***campo elettrico*** $\vec{E}$, in mezzo alle "***D***" $\vec{E}$ accelera le particelle.
- Dovunque, il campo magnetico $\vec{B}$ viene usato per ***curvare la traiettoria***.
Per poter accelerare la particella, quando la particella è dentro un elettrodo:
- Il generatore di *D.D.P* alternato inverte che scambia la polarità degli elettrodi.
![[attachements/Ciclotrone.png|450]]

La particella entra dal centro e compie una ***traiettoria a spirale***.
- $r$ aumenta con $v$ *fino ad uscire*.

Ogni giro completo, la particella viene ***accelerata due volte*** dal campo elettrico $\vec{E}$ fra i due elettrodi.

> Trovare la frequenza del generatore è molto semplice:

Poiché la velocità angolare rimane costante.
$$
\omega_{c}=\frac{qB}{m}
$$
- La frequenza dell'alternatore sarà:
$$
\nu=\frac{\omega_{c}}{2\pi}
$$
#### Selettore di Velocità
>[!tldr] Idea
>Prendo una specie di *condensatore* a facce piane e lo uso per produrre un ***campo elettrico*** $\vec{E}$.
>- In modo da *accelerare* la particella carica verso la faccia caricata negativamente.
>
>Ora applichiamo un ***campo magnetico*** $\vec{B}$ perpendicolare a $\vec{E}$.
>- Seguendo la regola della mano destra, la forza applicata da $\vec{B}$ è opposta a quella applicata a $\vec{E}$.


![[attachements/SelettoreVelocità.png]]

> Se la particella esce dal "***buco***", significa:

- La forza applicata da $\vec{E}$ è uguale alla forza applicata da $\vec{B}$.

$$
\cancel{ q }E=\cancel{ q }vB \implies v =\frac{E}{B}
$$
 