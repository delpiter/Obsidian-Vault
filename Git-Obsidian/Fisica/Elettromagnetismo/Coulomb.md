## Legge di Coulomb
---
> Condotti esperimenti con una bilancia di torsione.

>[!summary] Concetto
>Simile all'[[Legge di Gravitazione#Esperimento di Cavendish|Esperimento di Cavendish]].
>Se $q_{1}$ e $q_{2}$ sono cariche, la [[Elettromagnetismo#Elettrostatica|forza elettrostatica]] fa ruotare il pendolo di torsione.
>All'equilibrio il *momento meccanico* dovuto alla torsione del filo **bilancia** il momento dovuto alla ***forza elettrostatica***.

>Misuro l'angolo, conosco la costante di torsione $k$ e calcolo $T=k\theta$

$$
|\vec{F}|\propto \displaystyle{\frac{|q_{1}||q_{2}|}{r^2}}
$$
![[EsperimentoCoulomb.jpg|500]]

>[!check] Legge di Coulomb nel Vuoto
>Nel sistema internazionale si scrive:
>$$\vec{F}_{ab}=\frac{1}{4\pi\varepsilon_{0}}\displaystyle{\frac{|q_{1}||q_{2}|}{r^2}} \hat{r}$$

*Dove*:
- $\displaystyle\frac{1}{4\pi\varepsilon_{0}}$ è la costante di proporzionalità.
- La forza è *proporzionale* a $\frac{1}{r^2}$
- Cariche **opposte** si *attraggono* ($q_{a}q_{b}<0\implies \vec{F}_{ab}=F_{ab}(-\hat{r})$)
- Cariche dello **stesso segno** si *respingono* ($q_{a}q_{b}>0\implies \vec{F}_{ab}=F_{ab}(+\hat{r})$)
- Per la [[Leggi di Newton#Terza Legge di Newton|terza legge di Newton]] $\vec{F}_{ab}=-\vec{F}_{ba}$
- $\varepsilon_{0}=8.854\times 10^{-12}\ \  C^2 /Nm^2$ è la ***costante dielettrica del vuoto***.

$$
\displaystyle\frac{1}{4\pi\varepsilon_{0}}=K=8.987\times10^{9}\simeq 9\times 10^9 \ C^2 /Nm^2
$$
> Due oggetti con carica di $1C$ posti a distanza di $1m$ interagiscono con $F=9\times 10^9 N$

>[!hint] Osservazione
>Il fatto è che $1C$ è una quantità di carica enorme, una bacchetta strofinata si carica con $q\simeq 10^{-8}C$

---
> Se non si è nel vuoto, la legge di Coulomb si modifica.

$$\vec{F}_{ab}=\frac{1}{4\pi\varepsilon_{0}\varepsilon_{r}}\displaystyle{\frac{|q_{1}||q_{2}|}{r^2}} \hat{r}$$
Dove $\varepsilon_{r}$ è la *costante dielettrica relativa del mezzo*.
- Sempre $>1$ (forza elettrostatica ***ridotta*** quando esercitata attraverso un mezzo)

>[!example] Esempi

| Mezzo       | Costante Dielettrica |
| ----------- | -------------------- |
| Aria Secca  | $1.00059$            |
| $CO_{2}$    | $1.00098$            |
| Acqua       | $80$                 |
| Teflon      | $2.1$                |
| Vetro Pirex | $5$                  |

### Intensità della Forza Elettrostatica
>[!example] Esempio
>Mettiamo un grammo di protoni al polo nord e uno al polo sud.

- Distanza: $\text{d}\simeq 1.3\times10^{7}m$
- Massa $p$: $1.67 \times10^{-24}g$ 
- Numero $p$: $h\simeq 0.6\times 10 ^{24}$
- Carica $p$: $e\simeq1.6\times 10^{-19}C$
- Carica $1g\ p$: $Q=ne\simeq 10^5 C$

>Calcoliamo la forza di Coulomb

$$
F=k \frac{Q^2}{\text{d}^2}\simeq 5.3\times 10^5 N
$$

Equivalente alla forza peso di $50$ *tonnellate*.
- L'intera terra attira $1g$ di protoni con $F_{a}\simeq10^{-2}N$

Confrontiamo: [[Elettromagnetismo#Elettrostatica|Forza elettrostatica]] e [[Legge di Gravitazione#Legge di Gravitazione Universale|gravitazionale]].
$$
\frac{F_{g}}{F_{em}}=\frac{Gm_{p}^2}{ke^2}\simeq 0.8\times 10^{-36}
$$


>[!done] La Forza Gravitazionale è trascurabile rispetto alla Forza Elettrica.