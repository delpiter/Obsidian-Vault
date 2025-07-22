>[!definizione] Definizione
>Il moto rettilineo si svolge ***lungo una retta*** sulla quale fissiamo un'*origine* e un *verso*
>Può essere descritto tramite una unica **coordinata scalare**: $x(t)$
>- Chiamata ***legge oraria***

![[LeggeOraria.png]]

>Chiameremo diagramma orario un grafico che riporta il tempo ($t$) in ascissa e la posizione ($x$) in ordinata

![[DiagrammaOrario.png]]
## Velocità
---
>[!info] Definizione
>Definiamo la ***velocità media*** il rapporto tra lo *spazio percorso* e il *tempo necessario* a percorrerlo.
>$$v_{m}=\displaystyle{\frac{\Delta x}{\Delta t}}=\displaystyle{\frac{x_{2}-x_{1}}{t_{2}-t_{1}}}$$

Se ora rendo sempre più piccoli gli intervalli temporali $\Delta t$, giungo alla definizione di ***velocità istantanea***.

$$
\lim\limits_{\Delta t\to 0} \displaystyle{\frac{\Delta x}{\Delta t}}=\displaystyle{\frac{\text{d}x}{\text{d}t}}=v
$$

>Il segno della velocità indica la **direzione del moto**

Se è nota la legge oraria $x(t)$, tramite l'operazione di derivazione, si *ricava la velocità*

## Accelerazione
---
> In generale la velocità è in funzione del tempo $v=v(t)$

>[!abstract] Definizione
>Possiamo descrivere le variazioni di $v$, come in [[#Velocità|precedenza]].
>Se la **velocità** varia di $\Delta v$ in un $\Delta t$, avremo la definizione di ***accelerazione media***.
>$$a_{m}=\displaystyle{\frac{\Delta v}{\Delta t}}$$

> E come per la velocità, scegliendo $\Delta t$ sempre più piccoli
- Si ottiene la definizione di ***accelerazione istantanea***

$$
a = \displaystyle{\frac{\text{d}v}{\text{d}}}=\displaystyle{\frac{\text{d}^{2}x}{\text{d}t^{2}}}
$$

## Riassunto
---
>[!summary] Nota la $x(t)$
>$$x(t) \underset{ \text{Derivo} }{ \to } v(t) \underset{ \text{Derivo} }{ \to } a(t)$$

>[!example] Nota la $a(t)$
>$$a(t) \underset{ \text{Integro } (v_{0}) }{ \to } v(t) \underset{ \text{Integro } (x_{0})}{ \to } x(t)$$

## Unità di Misura

| Quantità      | Unità di Misura             | Simbolo  |
| ------------- | --------------------------- | -------- |
| Posizione     | *Metri*                     | $m$      |
| Velocità      | *Metri al secondo*          | $m /s$   |
| Accelerazione | *Metri al secondo quadrato* | $m /s^2$ |
| Tempo         | *Secondi*                   | $s$      |

>[!caution] Conversione
>La misura delle velocità è **frequentemente** espressa in $km / h$, la conversione in $m / s$ è semplice
>$$1 \frac{km}{h} = \displaystyle{\frac{10^3m}{3600s}}=0.278 \frac{m}{s}$$
><u>Quindi</u>
>$$1\frac{m}{s}=3.6 \frac{km}{h}$$

### Formule
> Con l'*accelerazione costante*

$$
\begin{cases}
x(t) = x_{0} +v_{0}t+\frac{1}{2}at^2 \\
v(t) =v_{0} +at \\
v^2(x) = v_{0}^2 +2a(x-x_{0})
\end{cases}
$$

- $t_{0} = 0,\quad x_{0} = x(0),\quad v_{0}=v(0)$

L'ultima *formula* rappresenta la **velocità** in ***funzione della posizione***
## Tipi di Moto
---

| Moto                       | Condizioni            |
| -------------------------- | --------------------- |
| *Quiete*                   | $v(t)=0$              |
| *Uniforme*                 | $v(t)=k,\quad a(t)=0$ |
| *Uniformemente Accelerato* | $a(t)=k$              |
| *Vario*                    | $a(t)\neq k$          |

## Caduta Verticale dei Gravi
---
> Trascurando l'attrito con l'aria:

>[!quote] Caduta del Grave
>***Qualunque corpo*** lasciato libero di cadere, in prossimità della superficie terrestre, si muove verso il basso con accelerazione costante che vale in modulo $g=9.81\ m/s^2$.

Fissato un asse diretto verso l'alto:
- $a=-g=-9.81\ m /s^2$

> Un corpo cade da un'altezza $h$ con $v_{0}=0$

Con le condizioni iniziali: $x_{0}=h\quad v_{0}=0\quad t_{0}=0$, sono valide le seguenti espressioni
$$
\begin{cases}
v=-gt \\
x=h-\frac{1}{2}gt^2
\end{cases}
$$
$$
\begin{cases}
v(x)=\sqrt{ 2g(h-x) } \\
t(x)=\sqrt{ \displaystyle{\frac{2(h-x)}{g}} }
\end{cases}
$$
Da queste espressioni si ottiene, ponendo $x=0$:
- Il tempo di caduta $t_{c}=\sqrt{ \frac{2h}{g} }$
- La velocità al suolo $v_{c}=\sqrt{ 2gh }$

