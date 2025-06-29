## Resistenze
---
> Se agli estremi di un conduttore applico una differenza di potenziale $V$, ottengo una intensità di corrente $I$.

>[!definizione]
>Si definisce ***resistenza***:
>$$R=\frac{V}{I}$$

Si trova che $I\propto V^{*}$ quindi $R$ non dipende da $V$ o $I$.
-  \* con buona approssimazione
> Unità di Misura

$$
[R]=\Omega=\frac{\text{Volt}}{\text{Ampere}}=\text{Ohm}
$$

>[!cite] Legge di Ohm
>$$V=RI$$

#### Resistenze in Serie
> La stessa corrente $I$ in ciascuna $R$.

![[ResistenzeSerie.svg]]

>[!caution] Resistenza Equivalente

$$
V=V_{1}+V_{2}=IR_{1}+IR_{2}=(R_{1}+R_{2})I
$$

$$
R_{tot}=\sum_{i}R_{i}
$$

#### Resistenze in Parallelo
> Stesso potenziale $V$ per le due *resistenze*.
![[ResistenzeParallelo.svg]]

>[!caution] Resistenza Equivalente

$$
I=I_{1}+I_{2}
$$
$$
V=I_{1}R_{1}\qquad V=I_{2}R_{2}
$$
$$
I_{1}=\frac{V}{R_{1}}\qquad I_{2}=\frac{V}{R_{2}}\implies I=\frac{V}{R_{1}}+\frac{V}{R_{2}}= \frac{R_{1}R_{2}}{R_{2}+R_{1}}V
$$
> Quindi

$$
V=\frac{R_{1}R_{2}}{R_{1}+R_{2}}I
$$
- Ovvero

$$
R_{tot}=\frac{R_{1}R_{2}}{R_{1}+R_{2}} \qquad \frac{1}{R_{tot}}=\sum_{i} \frac{1}{R_{i}}
$$

#### Potenza Dissipata in una Resistenza
>[!tldr] Effetto Joule
>In una *resistenza* $R$ percorsa da corrente $I$ la differenza di potenziale ai capi di $R$ è $V$.
>In un intervallo di tempo $\Delta t$, una quantità di carica $\Delta Q$ passa nella resistenza, e il suo ***potenziale cala*** di $V$.

Subisce una ***variazione di energia potenziale***.
$$
\Delta U (V_{b}-V_{a})\Delta Q=-V\Delta Q
$$
- Negativo perché il potenziale *cala*.

![[PotenzaDissipata.png|550]]

>La *rapidità* con cui sarà dissipata l'energia sarà:

$$
P=-\frac{\Delta U}{\Delta t}=\frac{V\Delta Q}{\Delta t}=VI
$$
>[!info] Legge di Joule
>$$P=VI\qquad P=RI^{2}\qquad P=\frac{V^{2}}{R}$$
>

>Unità di Misura:

 $[P]=\frac{J}{s}=Watt=W$

>[!Check] Energia Dissipata
>L'energia viene dissipata tramite urti, che causano un *aumento della temperatura*.
### Resistività
> Sia $l$ la lunghezza di un conduttore e $S$ l'area della sezione dello stesso. 

>[!info]
>Data una [[Potenziale Elettrico#Differenza di Potenziale|differenza di potenziale]] $V$, si osserva:
>- Se raddoppio $l$, $I$ si dimezza. $\implies R\propto l$
>- Se raddoppio $S$, $I$ raddoppia. $\implies R\propto \frac{1}{S}$

> Introduco una resistività $\rho$, caratteristica del materiale.

$$
R=\rho\frac{r}{S} \implies [\rho]=\Omega\cdot m
$$

$\rho$ varia *linearmente* su ampi **intervalli di temperatura**.
- A basse temperature il comportamento è molto meno lineare.
- Alcuni materiali mostrano ***superconduttività***.
$$
\rho\simeq \rho_{0}(1+\alpha(T-T_{0}))
$$

### Legge di Ohm con la Densità di Corrente
> La densità di corrente è ***proporzionale al campo elettrico***.

$$
\vec{J}=\sigma\vec{E}
$$

- $\sigma$ è la *conducibilità elettrica*.

>[!abstract] Ohm
>Se $\sigma$ non dipende da $\vec{E}$ siamo in presenza di un ***conduttore ohmico***.
>Supponiamo $\vec{J}$ ed $\vec{E}$ uniformi in questo conduttore.
>Abbiamo:
>$$I=JS$$
>e
>$$V=El$$
>- $V=RI$ diventa quindi: $El=RJS$

Di conseguenza:

$$
J=\frac{El}{RS} \implies\sigma=\frac{l}{SR}
$$
- Ovvero $\sigma=\frac{1}{\rho}$
$$
\vec{E}=\rho\vec{J}
$$