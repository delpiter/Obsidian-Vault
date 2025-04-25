>Descriviamo il moto di un *grave nello spazio*, di un proiettile che **non** avrà un moto **puramente verticale**. Nel seguito trascureremo l’[[Le Forze#Forze di Attrito|attrito]] con l’aria.

>[!tldr] Idea
>Il proiettile ha un'[[Moto Rettilineo#Accelerazione|accelerazione]] **costante**, di modulo $g$ *diretta verso il basso*.
>La componente orizzontale dell'accelerazione è *nulla*.
>Prendendo un asse $y$ diretto verso l'alto, si avrà:
>$$a_{y}=-g\qquad a_{x}=a_{z}=0$$

Scelto un sistema di riferimento tale che si abbia $\vec{v}_{0}=0$ nel piano $xy$, si considera solo il piano $xy$ nel quale ***giace sempre la traiettoria*** ($v_{z}=0$ per ogni istante).

> Esprimendo la velocità iniziale in componenti cartesiane, utilizzando il modulo della velocità iniziale e l'angolo di lancio:

$$
\vec{v}_{0}=v_{0x}\hat{i}+v_{0x}\hat{j}=v_{0}cos(\phi_{0})\hat{i}+v_{0}sin(\phi_{0})\hat{j}
$$
Con $v_{0}=|\vec{v}_{0}|$

![[MotoProiettile.png]]

Dato che $a_{x}=0$, avremo:
$$
v_{x}(t)=\text{costante}=v_{0x}=v_{0}cos(\phi_{0})
$$
Mentre per il moto lungo $y$, avremo:
$$
v_{y}=v_{y0}+a_{y}t=v_{0}sin(\phi_{0})-gt
$$

>[!done] Passando quindi alle leggi orarie per la posizione, avremo:

$$
\begin{cases}
x(t)=(v_{0}cos(\phi_{0}))t \\
y(t)=(v_{0}sin(\phi_{0}))t-\displaystyle\frac{1}{2}gt^2
\end{cases}
$$
> Possiamo ricavare la traiettoria:

$$
y(x)=tan(\phi_{0})x- \frac{g}{2v_{0}^2cos^2(\phi_{0})}x^2
$$
Che è l'equazione di una parabola che passa per l'origine (*punto di lancio*).
- Trovando la $x$ corrispondente all'altra soluzione di $y=0$ ricaviamo la ***gittata*** ($R$).
$$
R=\frac{2v_{0}^2}{g}sin(\phi_{0})cos(\phi_{0})=\frac{v_{0}^2}{g}sin(2\phi_{0})
$$


>[!caution] L'accelerazione di gravità agisce solamente sulla componente del vettore $\hat{j}$

![[Accelerazioneg.png]]
