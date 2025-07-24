## La Mela e la Luna
---
>Distanza ***terra-luna***:$D_{TL}\simeq 384000km$

> Periodo di ***rivoluzione lunare***: $T\simeq 28d$

- $\omega=\displaystyle\frac{2\pi}{T}\simeq 2.59\times 10^{-6}s^{-1}$

Dalla cinematica del [[Moto Circolare|moto circolare uniforme]], sappiamo che è presente una ***accelerazione centripeta*** di modulo:
$$
a_{L}=\omega^2D_{TL}\simeq 2.6\times 10^{-3} m/s^{2}
$$
Accelerazione molto più piccola di $g$

>[!tldr] Idea
>Si può ipotizzare  che la massa di tutta la terra sia concentrata nel suo centro e che la forza agente "***sulla mela***" e "***sulla luna***" fosse la *stessa forza* originata da tale centro ma avente una **intensità decrescente con la distanza**.

Quindi le accelerazioni per l'oggetto sulla superficie terreste e per la luna si devono poter scrivere come:
$$
g\propto \frac{M_{T}}{R_{T}^?}\qquad a_{L}\propto \frac{M_{T}}{D_{TL}^?}
$$
- Dove $?$ sta ad indicare che non si conosce a priori la ***dipendenza dalla distanza***.

>[!todo] Deve esistere una costante di proporzionalità.

Costante che indicheremo con $G_{N}$ che ***deve essere la stessa*** per i due oggetti.
$$
\text{Mela: }F_{M}=m_{M}\left( \frac{G_{N}M_{T}}{R_{T}^?} \right)\qquad \text{Luna: }=m_{L}\left( \frac{G_{N}M_{T}}{D_{TL}^?} \right) 
$$
> Riducendo le relazioni alle sole accelerazioni abbiamo:

$$
g=\left( \frac{G_{N}M_{T}}{R_{T}^?} \right)\qquad a_{L}=\left( \frac{G_{N}M_{T}}{D_{TL}^?} \right) 
$$
- Ovvero
$$
gR_{T}^?=a_{L}D_{TL}^?\implies \left( \frac{g}{a_{L}} \right)=\left( \frac{D_{TL}}{R_{T}} \right)^?  
$$
> Si ha che

$$
\left( \frac{g}{a_{L}} \right)\simeq \frac{9.8}{2.6\times10^{-3}}\simeq 3790
$$
*Mentre*:
$$
\left( \frac{D_{TL}}{R_{T}} \right)\simeq 60.9
$$
Quindi, se $?=2$, si ha:
$$
\left( \frac{D_{TL}}{R_{T}} \right)^2\simeq (60.9^2)\simeq 3800
$$
>[!todo] Usando un esponente pari a $2$ si ha:
>$$F=G_{N} \displaystyle{\frac{mM_{T}}{r^2}}$$
>Che predice correttamente sia ***l'accelerazione della mela*** sia ***l'accelerazione centripeta*** compiuta dalla luna.

## Legge di Gravitazione Universale
---
>[!quote] Legge
>Ogni *particella* nell'universo ***attrae*** ogni altra particella con una forza che è *direttamente proporzionale* al prodotto delle loro **masse** e *inversamente proporzionale* al quadrato della loro **distanza**.
>La [[Leggi di Newton#Seconda Legge di Newton|forza]] è diretta lungo la linea **congiungente** le due particelle.

In termini vettoriali possiamo scrivere:
$$
\vec{F}_{12}=-G \displaystyle{\frac{m_{1}m_{2}}{r^2}}\hat{r}
$$
Dove:
- $\vec{F}_{12}$ è la ***forza*** che la particella 1 esercita sulla particella 2.
- $m_{1}$ e $m_{2}$ sono le ***masse*** delle due particelle.
- $r$ la ***distanza*** fra le due.

Il versore $\hat{r}=\displaystyle{\frac{\vec{r}_{12}}{r_{12}}}$ indica la ***direzione*** che va dalla particella $1$ alla particella $2$
- Il segno meno indica che la forza è ***attrattiva*** (La particella 2 sente una forza diretta verso la particella 1).

>[!note] Un altro modo di scrivere la relazione
>$$\vec{F}_{12}=-G \displaystyle{\frac{m_{1}m_{2}}{r^3}}\vec{r}_{12}$$

> Si può calcolare la ***forza di gravitazione*** esercitata da una distribuzione estesa di massa.

- Per distribuzioni *sferiche* di massa, la forza esercitata all'**esterno** di esse equivale a quella esercitata da un ***punto materiale situato al centro*** della distribuzione sferica.

Se considero un corpo sulla superficie terrestre:
$$
F=G \displaystyle{\frac{M_{T}m}{R_{T}^2}}\quad\implies\quad a=G\displaystyle{\frac{M_{T}}{R_{T}^2}}=g
$$
>[!hint] Ricavare $G$
>Conoscendo $g,M_{T}$ e $R_{T}$ potrei calcolare il valore di $G$.
>>[!missing] Al tempo non era nota la massa della terra

#### Esperimento di Cavendish
> Esperimento effettuato per determinare il valore di $G$.

>[!caution] Esperimento
>L'esperimento consiste in una ***bilancia di torsione***.
>Un **filo** sottile sostiene un **manubrio** leggero, alle cui estremità sono attaccate due ***piccole masse***.
>A *terra*, due **grandi masse** uguali sono posizionate in modo da provocare la *torsione* del filo per effetto dell’***attrazione gravitazionale*** esercitata sulle masse sospese.

![[EsperimentoCavendish.png]]

> *Cavendish* dichiarò che con la sua bilancia era stato in grado di ***pesare la terra***.

$$
mg=G\frac{mM_{T}}{R_{T}^2}\quad\implies\quad M_{T}=\frac{gR_{T}^2}{G}
$$
Il valore oggi accettato della costante $G$ è:
$$
G=6.67\times 10^{-11} \ Nm^2/kg^2
$$

### Orbite Geostazionarie
>Affinché l’orbita di un *satellite terrestre* sia ***geostazionaria***, esso deve compiere una intera **rivoluzione** intorno alla terra in $24h$.

Possiamo calcolare il raggio di questa orbita, sapendo che:
- $T=24h=86400s$

Utilizzando la [[Leggi di Keplero#Terza Legge|terza Legge di Keplero]], dove consideriamo la *terra* come sorgente della ***forza gravitazionale***:
$$
\frac{T^2}{R^3}=\frac{4\pi^{2}}{GM_{T}} \quad\implies\quad R=\sqrt[3]{ \frac{GM_{T}T^2}{4\pi^2} }\simeq 42160km
$$
Dato che il raggio medio della terra è circa $6370 km$, il satellite si trova a circa $36000km$ sopra la superficie terrestre.
