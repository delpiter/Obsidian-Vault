>Scelto un sistema di riferimento con origine nel centro della traiettoria circolare e piano $xy$ nel piano della circonferenza, si avrà

![[attachements/MotoCircolare.png|400]]

$$
\begin{cases}
x=Rcos(\theta) \\
y=Rsin(\theta) \\
z=0
\end{cases}
$$
>[!help] Vettore Posizione
>Il ***vettore posizione*** è determinato univocamente dal raggio della circonferenza, $R$, e dall'angolo compreso tra l'asse $x$ e la semiretta uscente dal centro $O$ passante per il punto $P$
>$$\vec{r}=Rcos(\theta)\hat{i}+Rsin(\theta)\hat{j}$$

## Moto Circolare Uniforme
---
>La velocità $v_{s}$, cioè la quantità di spazio percorso lungo la circonferenza per unità di tempo è costante.

$$
v_{s}=\frac{\text{d}}{\text{d}t}(R\theta)=R \frac{\text{d}\theta}{\text{d}t} = R\omega
$$
- Chiamiamo $\omega=\displaystyle\frac{\text{d}\theta}{\text{d}t}=\frac{v_{s}}{R}$  la ***velocità angolare***.

>[!todo] Legge Oraria
>La legge oraria per l’angolo $\theta$ sarà:
>$$\theta(t)=\theta_{0}+\omega(t-t_{0})$$

> Vettore *posizione*, *velocità* e *accelerazione*.

Passiamo a notazione cartesiana:
- $t_{0}=0$ e $\theta_{0}=0$, sicché $\theta(t)=\omega t$

$$
\begin{cases}
\vec{r}(t)=R\cos(\omega t)\hat{i}+R\sin(\omega t)\hat{j} \\
\vec{v}(t)=\displaystyle{\frac{\text{d}\vec{r}}{\text{d}t}}=-\omega R\sin(\omega t)\hat{i}+\omega R\cos(\omega t)\hat{j} \\
\vec{a}(t)=\displaystyle{\frac{\text{d}\vec{v}}{\text{d}t}}=-\omega^2R\cos(\omega t)\hat{i}-\omega^2 R\sin(\omega t)\hat{j}=-\omega^2\vec{r}(t)
\end{cases}
$$

>[!hint] Osservazione
>Nel moto circolare uniforme l'accelerazione è **diversa da zero**, è **centripeta** e **costante in modulo**.

La direzione di $\vec{a}$ è la *stessa* di $\vec{r}$, il verso è *opposto*
- Si tratta di un vettore che dalla circonferenza va all'origine $O$.
- Da qui la denominazione "*centripeta*".

Il modulo dell'accelerazione, solitamente denominato $a_{c}$ si calcola:
$$
a_{c}=|\vec{a}(t)|=\sqrt{ \omega^4R^2\cos^2(\omega t)+\omega^4R^2\sin^2(\omega t) }=\omega^2R=\frac{v_{s}^2}{R}
$$
>[!done] È costante in modulo e proporzionale al quadrato della velocità angolare.

È spesso comodo esprimere l'accelerazione in *funzione della velocità scalare*:
- Dato che $\omega=\displaystyle\frac{v_{s}}{R}$
$$
a_{c}=v_{s}^2=R
$$
> In un moto circolare **non uniforme** la velocità scalare e angolare **non sono costanti**.

In questo caso l'accelerazione non è soltanto centripeta ma anche ***tangenziale***.
- L'accelerazione totale si può ottenere come somma vettoriale di *due accelerazioni perpendicolari*.
- Definita come l'*accelerazione angolare*.
$$
\alpha=\frac{\text{d}\omega}{\text{d}t}
$$
Il modulo dell'accelerazione tangenziale:
- $a_{t}=\alpha R$
E l'accelerazione totale avrà modulo:
$$
a=\sqrt{ a_{c}^2+a_{t}^2 }=R\sqrt{ \omega^4 +\alpha^2 }
$$