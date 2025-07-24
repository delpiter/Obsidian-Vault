## Conduttori in Condizioni Elettrostatiche
---
> Le [[Elettromagnetismo#Cariche Elettriche|cariche]] stanno solo sulla ***superficie esterna***.

>[!info]
> Il [[Campi Elettrostatici#Campo Elettrostatico|campo elettrico]] è **nullo** all'*interno*, mentre all'*esterno* vicino alla superficie è **ortogonale** alla stessa e **proporzionale** alla densità locale di carica.
> $$\vec{E}=\frac{\sigma}{\varepsilon_{0}}\hat{n}$$

Il [[Potenziale Elettrico|potenziale]] assume lo stesso valore su ***tutto il conduttore***, sulla *superficie* e all'*interno*.

Messa una carica su un conduttore qualunque, questo va ad un potenziale definito
- Rispetto a $V=0$ a distanza $\infty$
che è *proporzionale* alla ***quantità di carica***.

> Definisco la ***capacità elettrica***:

$$
Q=CV
$$

- $[C]=\text{ farad } \implies 1 \text{ farad }=1\frac{C}{V}$
- Proprietà *intrinseca* dell'oggetto

>[!tldr] Intuitivamente
>Se un oggetto ha una *grande capacità elettrica*, e ci metto sopra delle cariche, il suo potenziale aumenta **poco**.

### Condensatore
>[!info] Induzione Totale
>Due [[Induzione Elettrostatica#^dc307d|conduttori]] in configurazione tale per cui ***tutte le linee di forza*** partono da uno e finiscono sull'altro.

>[!definizione]
>Un ***condensatore*** sono *due conduttori* isolati tra loro posti in configurazione per cui vi sia *induzione totale*.

![[Condensatore.png]]

- Le due "***armature***" posseggono sempre carica di *uguale modulo e segno opposto*.

Posso "*caricare*" il condensatore con una batteria
![[Condensatore.svg]]
- Chiamo $V$ la $\Delta V$ tra le armature.
- Chiamo $Q$ la *carica*.

#### Capacità di un Condensatore
> Come per un conduttore isolato: $C=\frac{Q}{V}$.

- Capacità grande $\iff$ Contiene più carica a parità di $\Delta V$

> *Assumo* la distanza delle armature $d\ll A$ (*area* delle armature), allora:

1. $\displaystyle\mid\sigma\mid=\frac{Q}{A}$ *uniforme*
2. $\displaystyle E=\frac{\mid\sigma\mid}{\varepsilon_{0}}=\frac{Q}{\varepsilon_{0}A}$
3. $V$ lineare in $x$

![[CondensatorePiano.png|550]]

$$
V=Ed=\frac{Qd}{\varepsilon_{0}A}
$$
$$
C=\frac{Q}{V}=\frac{Q\varepsilon_{0}A}{Qd}\implies C=\frac{\varepsilon_{0}A}{d}
$$
##### Condensatori in Serie
![[Condensatori in Serie.svg]]

>[!info]
>- $V=V_{b}-V_{a}=V_{1}+V_{2}$.
>- Tutti i condensatori hanno la ***stessa carica***.
>- $Q_{1}=Q_{2}=Q$.

![[CondensatoriSerie.png|550]]

> Troviamo la ***Capacità equivalente*** del sistema di due condensatori:

$$
\begin{cases}
\displaystyle C=\frac{Q}{V} \\
\displaystyle V_{1}=\frac{Q}{C_{1}} \\
\displaystyle V_{2}=\frac{Q}{C_{2}} \\
V_{1}+V_{2}=V
\end{cases}\implies \frac{Q}{C}=\frac{Q}{C_{1}}+\frac{Q}{C_{2}}\implies \frac{1}{C}=\frac{1}{C_{1}}+\frac{1}{C_{2}}
$$

In **generale**:
$$
\frac{1}{C_{eq}}=\sum_{i} \frac{1}{C_{i}}
$$

##### Condensatori in Parallelo
> La [[Potenziale Elettrico#Differenza di Potenziale|differenza di potenziale]] ai **capi dei condensatori** è la stessa.

![[CondensatoriParalleli.svg]]

>[!caution] Capacità Equivalente

$$
C=\frac{Q}{V}=\frac{Q_{1}+Q_{2}}{V}=\frac{Q_{1}}{V}+\frac{Q_{2}}{V}
$$
- Ma $C_{1}=\frac{Q_{1}}{V_{1}}$ (uguale per $C_{2}$)

> *Quindi*

$$
C=C_{1}+C_{2}
$$
In Generale
$$
C_{eq}=\sum_{i}C_{i}
$$

##### Energia in un Condensatore
>[!info]
>Se in un certo istante il *condensatore* è al **potenziale** $V'$ e io aggiungo carica $\text{d}Q'$, l'energia potenziale aumenta.
>$$\text{d}U'=V'\text{d}Q'$$

Quindi per mettere una carica $Q$ ***partendo da scarico***
$$
U=\int _{0}^{Q}V' \, \text{d}Q' 
$$
- Ma $V'=\displaystyle{\frac{Q'}{C}}$
$$
U=\int _{0}^{Q} \frac{Q'}{C} \, \text{d}Q'=\frac{1}{C}\int _{0}^{Q}Q' \, \text{d}Q'
$$
> *Quindi*

$$
U=\frac{1}{2} \frac{Q^{2}}{C} \iff U=\frac{1}{2}CV^{2}\iff U=\frac{QV}{2}
$$

>[!tldr] Densità di Energia del Campo Elettrico
>Supponiamo che l'energia appena trovata è nel campo elettrico presente tra le armature.
>$$E=\frac{V}{d}$$
>Usando $C=\displaystyle\varepsilon_{0} \frac{A}{d}\implies U=\frac{1}{2} CV^{2}=\frac{1}{2}\left( \frac{\varepsilon_{0}A}{d} \right)(Ed)^{2}$

> Quindi

$$
U=\frac{1}{2}\varepsilon_{0}E^{2}(Ad)
$$
- Dove $Ad$ non è altro che il ***volume del condensatore***.

<u>Allora</u>
- La ***densità di energia del campo elettrico***:
$$
u=\frac{U}{Ad}=\frac{1}{2}\varepsilon_{0}E^{2}
$$
>[!warning] Ha validità Generale!
>Ovunque nello spazio sia presenta un campo elettrico di modulo $E$, c'è densità di energia:
>$$u=\frac{1}{2}\varepsilon_{0}E^{2}$$

#### Carica e Scarica di un Condensatore
##### Carica
> Siano $R,S,C$ rispettivamente: resistenza, interruttore e condensatore.
 
![[CaricaCondensatore.svg]]

>[!hint]
>Quando chiudo l'interruttore $S$, la ***corrente circola*** e *carica* $C$.

Se in un dato istante su $C$ c'è carica $Q$, la sua [[Potenziale Elettrico#Differenza di Potenziale|differenza di potenziale]] è: $V_{c}=\frac{Q}{C}$.

> La [[Leggi di Kirchhoff#Seconda Legge di Kirchhoff|seconda legge di Kirchhoff]] per il circuito allora:

$$
V_{B}-\frac{Q}{C}-IR=0\implies V_{B}-\frac{Q}{C}=R\displaystyle{\frac{\text{d}Q}{\text{d}t}}\implies \displaystyle{\frac{\text{d}Q}{V_{B}C-Q}}=\displaystyle{\frac{\text{d}t}{RC}}
$$
$$
\begin{array}
\ \displaystyle Q(t)=V_{B}C(1-e^{-t/RC}) \\
\displaystyle I(t)=\frac{V_{B}}{R}e^{-t/RC} \\
\displaystyle V(t)=V_{B}(1-e^{-t/RC})
\end{array}
$$

>[!done] Conclusioni

- La corrente tende a zero ***esponenzialmente***.
- La potenza ($V$) tende al valore $V_{B}$ ***esponenzialmente***.

```functionplot
---
title: Carica Condensatore
xLabel: 
yLabel: 
bounds: [0,10,-1,9]
disableZoom: true
grid: true
---
f(x)=4*(1-exp(-x))
g(x)=4*exp(-x)
h(x)=4
```

##### Scarica
> Siano $R,S,C$ rispettivamente: resistenza, interruttore e condensatore.

![[ScaricaCondensatore.svg]]

>[!hint]
>Quando chiudo l'interruttore $S$, la ***corrente circola*** e *scarica* $C$.

$$
-V_{R}+V_{C}=0\qquad -RI+\frac{Q}{C}=0
$$
- Con $I=\displaystyle{-\frac{\text{d}Q}{\text{d}t}}$
$$
\displaystyle{\frac{\text{d}Q}{\text{d}t}}+\frac{Q}{RC}=0
$$
> Che ha soluzione:

$$
Q(t)=Ae^{-t/RC}
$$
La condizione iniziale sarà: $Q(0)=CV_{0}$
- $V_{0}=$ Differenza di Potenziale su $C$.

$$
Q(t)=CV_{0}e^{-t/RC} \qquad I(t)=-\frac{V_{0}}{R}e^{-t/RC}\qquad V_{c}(t)=V_{0}e^{-t/RC}
$$
#### Proprietà dei Materiali Dielettrici
> Se inserisco un materiale *isolante* tra le armatura di un condensatore:

- Osservo una **diminuzione della differenza di potenziale** tra le armature.

>[!info] Costante dielettrica Relativa
>Inserendo un materiale isolante, la capacità del condensatore aumenta:
>Chiamiamo:
>$$\varepsilon_{r}=\frac{V_{0}}{V}>1$$
>> Costante Dielettrica Relativa
>
>- $V_{0}$ Differenza di potenziale con vuoto.
>- $V$ Differenza di potenziale relativa.

>[!example] Esempi

- $\varepsilon_{r}$ aria $\simeq 1$
- $\varepsilon_{r}$ acqua $\simeq 80$

Dato che $V=Ed$ e $V_{0}=E_{0}d$, $\varepsilon_{r}=\frac{E_{0}}{E}$
- Inoltre $V=\frac{Q}{C}$ e $V_{0}=\frac{Q}{C_{0}}$, $C=\varepsilon_{r}C_{0}$

> Con un generatore collegato, $V$ resta la stessa ***con o senza materiale***.

- Dato che con il materiale $C$ è maggiore, allora $Q$ è maggiore

Le molecole polari o polarizzate, del materiale dielettrico si orientano e *creano un campo opposto* a quello creato dalle **armature**.

> Quindi il ***campo elettrico all'interno diminuisce***.

$$
E=\frac{\sigma}{\varepsilon_{0}}-\frac{\sigma_{ind}}{\varepsilon_{0}}=E_{vuoto}\left( 1-\frac{\sigma_{ind}}{\sigma} \right)\equiv \frac{E_{vuoto}}{\varepsilon_{r}}
$$

- $E=\frac{\sigma}{\varepsilon_{0}\varepsilon_{r}}$
- $C=\varepsilon_{0}\varepsilon_{r} \frac{A}{d}$
- $\sigma_{ind}=\sigma\left( 1-\frac{1}{\varepsilon_{r}} \right)$
- $u=\varepsilon_{0}\varepsilon_{r} \frac{E^{2}}{2}$