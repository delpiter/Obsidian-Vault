## Teorema dell'Energia Cinetica
---
>[!info]
>Consideriamo un *caso unidimensionale*. Partendo dalla definizione di lavoro, costruiamo una espressione basata sulle **velocità iniziali** e **finali** del corpo.

$$
\begin{array}
\ \displaystyle\mathscr{L} = \int_{x_i}^{x_f} F \,\text{d}x = \int_{x_i}^{x_f} m a \,\text{d}x = \int_{x_i}^{x_f} m \frac{\text{d}v}{\text{d}t} \,\text{d}x  =\\
\displaystyle= \int_{v_i}^{v_f} m \frac{\text{d}x}{\text{d}t} \,\text{d}v = \int_{v_i}^{v_f} m v \,\text{d}v = \left[ \frac{1}{2} m v^2 \right]_{v_i}^{v_f} = \frac{1}{2} m v_f^2 - \frac{1}{2} m v_i^2
\end{array}
$$
> Conclusione

$$
\mathscr{L}=\frac{1}{2}mv^2_{f}-\frac{1}{2}mv^2_{i}
$$
>[!definizione] Energia Cinetica
>Definiamo l'***energia cinetica***, come:
>$$K=\frac{1}{2}mv^2$$

Quindi la relazione appena ricavata può essere scritta come:
$$
\mathscr{L}=\Delta K
$$
>[!quote] A Parole
>Quando si compie [[Lavoro di una Forza|lavoro]] su un *sistema* ottenendo esclusivamente una 
***variazione della sua velocità***, il lavoro complessivo è uguale alla **variazione** della sua ***energia cinetica***.

>[!hint] Note

$K$ *aumenta* se $\mathscr{L}>0$, *diminuisce* se $\mathscr{L}<0$.

Il teorema consente di considerare solo le *velocità iniziali* e *finali*:
- Utile per capire **come si muoverà un corpo** dopo che è stato fatto un certo lavoro, potendo ignorare quello che succede *durante il moto*.

## Energia Potenziale
---
> Per le [[Lavoro di una Forza#Forze Conservative e Non Conservative|forze conservative]] è conveniente definire l'energia potenziale.

>[!definizione]
>Il *lavoro* $\mathscr{L}$ compiuto da una ***forza conservativa*** su un elemento di un sistema quando questo si sposta da un punto ad un altro è uguale alla **differenza** tra l’*energia potenziale* del sistema **iniziale** e quella **finale**.
>$$\mathscr{L}=U_{i}-U_{f}=-\Delta U$$

L'energia potenziale racchiude le informazioni sulla forza corrispondente.

> L'espressione:

$$
\mathscr{L}=\int _{x_{i}}^{x_{f}} F \text{d}x =-\Delta U
$$
Scritta in forma differenziale:
$$
\text{d}U=-F\text{d}x
$$
- *Quindi*
$$
F=-\displaystyle{\frac{\text{d}U}{\text{d}x}}
$$
>[!help] Caso tridimensionale
>Nel caso tridimensionale, si introduce il [[Calcolo Differenziale#Gradiente|gradiente]].
>Indicato dal simbolo $\vec{\nabla}$

$$
\vec{\nabla} = \frac{\partial}{\partial x} \hat{i} + \frac{\partial}{\partial y} \hat{j} + \frac{\partial}{\partial z} \hat{k}
$$
$$
\vec{F} = -\vec{\nabla} U = -\frac{\partial U}{\partial x} \hat{i} - \frac{\partial U}{\partial y} \hat{j} - \frac{\partial U}{\partial z} \hat{k}
$$
### Forza Peso
> Energia Potenziale della [[Le Forze#Forza Peso|forza peso]].

Si ricava che, detta $y$ la coordinata della direzione verticale, si ha:
$$
\mathscr{L}_{\text{peso}}=\vec{P}\cdot\Delta \vec{r}=mg(y_{f}-y_{i})(-1) 
$$
- Scegliendo $y_{i}=0$
$$
U(y)=mgy
$$
$$
-\displaystyle{\frac{\text{d}U}{\text{d}y}}=F_{y,\text{peso}}=-mg
$$
*Quindi*
$$
\vec{P}_{\text{peso}}=\vec{\nabla}U(x,y,z)=-mg\hat{j}
$$
### Energia Potenziale Elastica
$$
\begin{array}
\ F=-kx \\
\mathscr{L}=\displaystyle\int _{x_{i}}^{x_{f}} -kx\, \text{d}x=\frac{1}{2}kx^2_{i}-\frac{1}{2}kx^2 _{f} \\
\displaystyle\Delta U=-\mathscr{L}=\frac{1}{2}kx^2_{f}-\frac{1}{2}kx_{i}^2
\end{array}
$$
> Scegliendo $U(0)=0$, si ottiene:

$$
U(x)=\frac{1}{2}kx^2
$$
e
$$
-\displaystyle{\frac{\text{d}U}{\text{d}x}}=F=-kx
$$
## Energia Meccanica
---
> Consideriamo un sistema sul quale agiscono solo [[Lavoro di una Forza#Forze Conservative e Non Conservative|forze conservative]].

>[!todo] Combinando la definizione di energia potenziale con il teorema dell'energia cinetica, abbiamo:

$$
\mathscr{L}=-\Delta U=U_{i}-U_{f},\qquad \mathscr{L}=\Delta K=K_{f}-K_{i}
$$
*Quindi*
$$
U_{i}-U_{f}=K_{f}-K_{i}\implies U_{i}+K_{i}=U_{f}+K_{f}
$$

>[!definizione]
>Definiamo ***energia meccanica*** la *somma* di energia potenziale e cinetica.
>$$E=U+K: \quad E_{i}=E_{f}=\implies \Delta E=0$$
>>[!quote] Concetto
>>In un sistema in cui agiscono solo forze conservative l'***energia meccanica si conserva***.

## Diagrammi Energetici
---
### Punti di Equilibrio e Inversione del Moto
> Si consideri per un caso *unidimensionale*, una energia potenziale $U(x)$.

![[PuntiEquilibrio.png]]

Nel punto $A$ abbiamo:
- $\displaystyle{\frac{\text{d}U}{\text{d}x}}>0$, ne segue che $F=-\displaystyle{\frac{\text{d}U}{\text{d}x}}<0$, cioè diretta verso *sinistra*.

Nel punto $B$ abbiamo:
- $\displaystyle{\frac{\text{d}U}{\text{d}x}}<0$, ne segue che $F=-\displaystyle{\frac{\text{d}U}{\text{d}x}}>0$, cioè diretta verso *destra*.

>[!hint] Osservazione
>La pendenza del grafico dell'energia potenziale ci dà informazione sul ***segno della forza*** corrispondente.

>Si osservi ora il grafico di $U(x)$

![[PuntiStabiliInstabili.png]]

Nei punti $A$ e $B$ si ha $\displaystyle{\frac{\text{d}U}{\text{d}x}}=0$, quindi in questi punti abbiamo $F=0$.

>[!caution] Punti di Equilibrio
>Se un corpo si trova in un ***punto di equilibrio*** con velocità nulla, *resta fermo* in tale posizione.

> Consideriamo uno spostamento $\varepsilon$ rispetto alla *posizione di equilibrio*.

Caso punto $A$:
- $\displaystyle{\frac{\text{d}U}{\text{d}x}}(A+\varepsilon)>0\implies F<0$; Il punto spostato a destra di $A$ *accelera verso sinistra* (verso $A$).
- $\displaystyle{\frac{\text{d}U}{\text{d}x}}(A-\varepsilon)<0\implies F>0$; Il punto spostato a sinistra di $A$ *accelera verso destra* (verso $A$).

>[!done] $A$ è un punto di equilibrio stabile

Caso punto $B$:
- $\displaystyle{\frac{\text{d}U}{\text{d}x}}(B+\varepsilon)<0\implies F>0$; Il punto spostato a destra di $A$ *accelera verso destra* (Si allontana da $B$).
- $\displaystyle{\frac{\text{d}U}{\text{d}x}}(B-\varepsilon)>0\implies F<0$; Il punto spostato a sinistra di $A$ *accelera verso sinistra* (Si allontana da $B$).

>[!missing] $B$ è un punto di equilibrio instabile

#### Significato Grafico dell'Energia Meccanica
>Nei punti $x_{A}$ e $x_{B}$ si ha $U(x_{A})=U(x_{B})$

![[PuntiInversioneMoto.png]]

Dato che $E=K+U$ si avrà necessariamente che $K(x_{A})=K(x_{B})=0$
- $v_{A}=v_{B}=0$

Se il corpo dotato di energia meccanica $E$ si trova ad un qualsiasi istante in un qualsiasi punto compreso tra $x_{A}$ e $x_{B}$:
- Tale corpo non potrà mai uscire dalla regione $x_{A}\leq x\leq x_{B}$

>[!help] Tali punti sono ***punti di inversione del moto***

### Oscillatore Armonico
> Energia meccanica di un ***oscillatore armonico***.

$$
E=K+U=\frac{1}{2}mv^2+\frac{1}{2}Kx^2
$$
Per la **posizione di equilibrio**
$$
U(0)=0,\qquad K=E
$$
Per la massima elongazione (moto di ampiezza $A$)
$$
U(A)=E,\qquad K=0
$$
