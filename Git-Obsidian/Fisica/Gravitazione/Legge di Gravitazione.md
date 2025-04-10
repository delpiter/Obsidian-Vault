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
>Ogni *particella* nell'universo ***attrae*** ogni altra particella con una forza che è *direttamente proporzionale* al quadrato della loro reciproca distanza.
>La [[Leggi di Newton#Seconda Legge di Newton|forza]] è diretta lungo la linea **congiungente** le due particelle.

In termini vettoriali possiamo scrivere:
$$
\vec{F}_{12}=-G \displaystyle{\frac{m_{1}m_{2}}{r^2}}\hat{r}
$$
- Dove $\hat{r}=\displaystyle{\frac{\vec{r}_{12}}{r_{12}}}$
