## Trasformazione
---
>Sia $(X,Y)$ una [[4 - Variabili Aleatori Multidimensionali|variabile aleatoria bidimensionale]]  

- $Z=X+Y$ è una trasformazione ***somma***

>[!question] Possiamo calcolare $d_{Z}$ in funzione di $d_{X,Y}$

#### Esempio
>Gara di tiro con l'arco a coppie

$A$ e $B$ fanno 3 tiri ciascuno
- $A$ fa centro con probabilità $3 /4$
- $B$ fa centro con probabilità $1 / 2$

$X=\#$ centri di $A$
$Y=\#$ centri di $B$
$Z=\#$ centri totali della squadra

- $X\sim B(3,3 /4)$
- $Y\sim B(3,1 /2)$

> $Z$ assume valori tra $0$ e $6$

- $d_{Z}(0)=\mathcal{P}(Z=0)=\mathcal{P}(X=0,Y=0)=d_{X,Y}(0,0)$
- $d_{Z}(1)=\mathcal{P}(X=0,Y=1)+\mathcal{P}(X=1,Y=0)=d_{X,Y}(0,1)+d_{X,Y}(1,0)$
- $\dots$
- $d_{Z}(4)=d_{X,Y}(1,3)+d_{X,Y}(2,2)+d_{X,Y}(3,1)$


>[!cite] Quindi
>$$d_{Z}(k)=\sum_{\underset{ l+m=k }{ l,m\  t.c. }}d_{X,Y}(l,m)$$

> Se $Z=XY$

>[!note] Allora
>$$d_{Z}(k)=\sum_{\underset{ l\cdot m=k }{ l,m\  t.c. }}d_{X,Y}(l,m)$$

>Se $Z=F(X,Y)$

>[!cite] Allora
>$$d_{Z}(k)=\sum_{\underset{ F(l,m)=k }{ l,m\  t.c. }}d_{X,Y}(l,m)$$

#### Esempio
>$x\mapsto x^2$

>[!question] Come si ottiene la densità della variabile trasformata?

$$
d_{X}(k)=\begin{cases}
\frac{1}{4} \quad \text{se }k=1 \\
\frac{1}{2} \quad \text{se }k=2 \\
\frac{1}{4} \quad \text{se }k=-2 \\
0 \quad \ \text{altrimenti}
\end{cases}
$$
Diventa:

$$
d_{X^2}(k)=\begin{cases}
\frac{1}{4} \quad \text{se }k=1 \\
\frac{3}{4} \quad \text{se }k=4 \\
0 \quad \ \text{altrimenti}
\end{cases}
$$
### Caso Speciale
>$Z=F(X,Y)=max(X,Y)$

###### Esempio
>Lanciamo un dado e una moneta

Li lanciamo ripetutamente fino ad ottenere almeno un ***6*** e almeno una ***testa***

- $X=\#$ lanci per ottenere il primo ***6***
- $Y=\#$ lanci per ottenere la prima ***testa***
- $Z=\#$ lanci totali $\implies Z=max(X,Y)$

>[!definizione] Funzione di Ripartizione
>$$F_{X}(K)=\mathcal{P}(X\geq k)$$
>$$F_{Z}=\mathcal{P}(Z\geq k)=\mathcal{P}(max(X,Y)\leq k)=\mathcal{P}(X\leq k,Y\leq k)$$

>Se $X$ e $Y$ sono *indipendenti*

$\mathcal{P}(X\leq k)\cdot \mathcal{P}(Y\leq k)=F_{X}(k)\cdot F_{Y}(k)$
>[!cite] Abbiamo quindi che se $X$ e $Y$ sono indipendenti e $Z=max(x,y)$ Allora:


$$
F_{Z}=F_{X}(k)\cdot F_{Y}(k)
$$

>Tornando all'esempio:

$$
\begin{array}
\ X\sim \tilde{G}\left( \frac{1}{6} \right)\quad d_{X}(k)=\frac{1}{6}\cdot\left( \frac{5}{6} \right)^{k-1} \quad \forall k\geq 1 \\
F_{X}(k)=\mathcal{P}(X\leq k)=1-\mathcal{P}(X>k)=1-\left( \frac{5}{6} \right)^k \\
Y\sim \tilde{G}\left( \frac{1}{2} \right)\quad d_{Y}(k)=\frac{1}{2}\cdot\left( \frac{1}{2} \right)^{k-1} \quad \forall k\geq 1 \\
F_{Y}(k)=1-\left( \frac{1}{2} \right)^k 
\end{array}
$$

>[!abstract] Quindi abbiamo:

$F_{Z}(k)=F_{X}(k)\cdot F_{Y}(k)=\left( 1-\left( \frac{5}{6} \right)^k \right)\cdot\left( 1-\frac{1}{2^k} \right)$

>[!done] Conclusione:

$$
d_{Z}=\mathcal{P}(Z=K)=\mathcal{P}(Z\geq k)-\mathcal{P}(Z\leq k-1)=F_{Z}(k)-F_{Z}(k-1)
$$
> Andando a sostituire:

- $\displaystyle\frac{1}{2^k}+\frac{5^{k-1}}{6^k}-\frac{7}{12}\cdot \frac{5^{k-1}}{12^k}$

## Somma di Variabili di Poisson Indipendenti
---
>[!definizione] Definizione
>Siano:
>- $X\sim P(\lambda)$ una [[3 - Variabili Aleatorie#Variabili di Poisson|variabile di Poisson]] di parametro $\lambda$
>- $Y\sim P(\mu)$ una ***variabile di Poisson*** di parametro $\mu$
>>[!question] $X+Y=$ ?
>
>>[!done] In Generale
>>$$X+Y\sim P(\lambda +\mu)$$

