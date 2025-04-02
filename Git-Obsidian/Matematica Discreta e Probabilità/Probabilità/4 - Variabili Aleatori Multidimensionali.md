## Introduzione
---
>[!definizione] Definizione
>Una [[3 - Variabili Aleatorie|variabile aleatoria]] ***bidimensionale*** è una *coppia ordinata* $\underline{X}(X_{1},X_{2})$ di ***variabili aleatorie***, definite sullo stesso *spazio* $\Omega$
>>[!note] Densità
>>Sia $\underline{X}(X_{1},X_{2})$, la sua densità è:
>>$$d_{\underline{X}}=d_{X_{1},X_{2}}(h,k)=\mathcal{P}(X_{1}=h,X_{2}=k)$$
>>La densità di $(X,Y)$ si dice ***densità congiunta*** di $X$ e $Y$

#### Esempio
>Una urna contiene 2 palline *rosse*, 2 *verdi* e 2 *gialle*

>[!cite] Estraiamo 2 palline senza rimpiazzo

$X_{1}=\#$ di verdi estratti
$X_{2}=\#$ di rossi estratti

>[!question] Determina la densità della coppia $X_{1},X_{2}$

Le coppie di valori possibili sono:
- $\underbrace{ (0,0),(2,0),(0,2) }_{ \text{Stessa densità} }$
- $\underbrace{ (1,0),(0,1),(1,1) }_{ \text{Stessa densità} }$

$d(0,0)=\displaystyle\frac{1}{\binom{6}{2}}=\frac{1}{15}$
$d(1,0)=\displaystyle\frac{4}{15}$

$$
d_{X_{1},X_{2}}(h,k)=\begin{cases}
\frac{1}{15} \quad \text{ se }(h,k)=(0,0),(2,0),(0,2) \\
\frac{4}{15} \quad \text{ se }(h,k)=(1,0),(1,1),(0,1) \\
0 \qquad \text{altrimenti }
\end{cases}
$$

#### Densità forma Tabella
>La densità $d_{X_{1},X_{2}}$ in forma di tabella:


| $X / Y$                 | $0$                                   | $1$                                   | $2$                                   | ***Densità Marginale***               |
| ----------------------- | ------------------------------------- | ------------------------------------- | ------------------------------------- | ------------------------------------- |
| $0$                     | $\displaystyle\frac{1}{15}$           | $\displaystyle\frac{4}{15}$           | $\displaystyle\frac{1}{15}$           | $\displaystyle \frac{6}{15}=d_{X}(0)$ |
| $1$                     | $\displaystyle\frac{4}{15}$           | $\displaystyle\frac{4}{15}$           | $0$                                   | $\displaystyle \frac{8}{15}=d_{X}(1)$ |
| $2$                     | $\displaystyle\frac{1}{15}$           | $0$                                   | $0$                                   | $\displaystyle \frac{1}{15}=d_{X}(2)$ |
| ***Densità Marginale*** | $\displaystyle \frac{6}{15}=d_{X}(0)$ | $\displaystyle \frac{8}{15}=d_{X}(1)$ | $\displaystyle \frac{1}{15}=d_{X}(2)$ |                                       |
>[!example] Quindi, abbiamo:
>$$\displaystyle d_{X}(h)=\sum_{k}d_{X,Y}(h,k)\quad \forall h$$
>$$\displaystyle d_{Y}(k)=\sum_{h}d_{X,Y}(h,k)\quad \forall k$$

###### Caso Tridimensionale
>Supponiamo di avere 3 variabili $X,Y$ e $Z$ e la relativa densità: $d_{X.Y,Z}$

- $\displaystyle d_{X}(h)=\sum_{k,l}d_{X,Y,Z}(h,k,l)\quad \forall h$
- $\displaystyle d_{Y}(k)=\sum_{h,l}d_{X,Y,Z}(h,k,l)\quad \forall k$
- $\displaystyle d_{Z}(l)=\sum_{k,h}d_{X,Y,Z}(h,k,l)\quad \forall l$

#### Inverso
>[!question] Dalla ***densità congiunta*** si può ottenere le ***densità marginali***, è vero il contrario?

>[!fail] Risposta breve: No, Infatti:

>Una urna contiene 2 palline rosse e 3 blu

- Facciamo due estrazioni ***con rimpiazzo***

$$X_{i}=\begin{cases}
1 \quad \text{se la }i\text{-esima estratta è rossa} \\
0 \quad \text{se è blu }
\end{cases}$$
| $X / Y$                 | $0$                         | $1$                          | ***Densità Marginali***      |
| ----------------------- | --------------------------- | ---------------------------- | ---------------------------- |
| $0$                     | $\displaystyle\frac{9}{25}$ | $\displaystyle\frac{6}{25}$  | $\displaystyle\frac{3}{5}$   |
| $1$                     | $\displaystyle\frac{6}{25}$ | $\displaystyle\frac{4}{25}$  | $\displaystyle{\frac{2}{5}}$ |
| ***Densità Marginali*** | $\displaystyle\frac{3}{5}$  | $\displaystyle{\frac{2}{5}}$ |                              |

- Ora facciamo due estrazioni ***senza rimpiazzo***

$$X_{i}=\begin{cases}
1 \quad \text{se la }i\text{-esima estratta è rossa} \\
0 \quad \text{se è blu }
\end{cases}$$
| $X / Y$                 | $0$                         | $1$                          | ***Densità Marginali***      |
| ----------------------- | --------------------------- | ---------------------------- | ---------------------------- |
| $0$                     | $\displaystyle\frac{3}{10}$ | $\displaystyle\frac{3}{10}$  | $\displaystyle\frac{3}{5}$   |
| $1$                     | $\displaystyle\frac{3}{10}$ | $\displaystyle\frac{1}{10}$  | $\displaystyle{\frac{2}{5}}$ |
| ***Densità Marginali*** | $\displaystyle\frac{3}{5}$  | $\displaystyle{\frac{2}{5}}$ |                              |

$\mathcal{P}(X_{1}=1,X_{2}=0)=\mathcal{P}(X_{1}=1)\cdot\mathcal{P}(X_{2}=0\mid X_{1}=1)=\frac{2}{5}\cdot \frac{3}{4}=\frac{3}{10}$

>[!cite] Conclusione
>Date le densità marginali, posso ottenere diverse ***densità congiunte***

##### Osservazione
>[!definizione] Ridefinizione di [[2 - Unione di Eventi#Eventi Indipendenti|variabili indipendenti]]
>Due variabili $X,Y$ si dicono ***indipendenti*** se $\forall h,k$ gli eventi $X=h$ e $Y=k$ sono indipendenti
>>[!note] Cioè
>>$$\underbrace{ \mathcal{P}(X=h,Y=k) }_{ d_{X,Y}(h,k) }=\underbrace{ \mathcal{P}(X=h)\cdot\mathcal{P}(Y=k) }_{ d_{X}(h)\cdot d_{Y}(k) }$$

