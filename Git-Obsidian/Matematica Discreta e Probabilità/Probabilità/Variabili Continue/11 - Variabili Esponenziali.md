>[!info] Concetto Importante
>$$\int e^{ -at } \, dt =\frac{e^{ -at }}{-a}$$

## Variabile Esponenziale Continua
---
>[!definizione] Definizione
>Consideriamo $a>0$
>$$f(s)=\begin{cases}
ae^{ -as }\quad \ \text{se } s>0 \\
0\qquad\quad\text{se } s<0
\end{cases}$$

![[attachements/Densita Esponenziale.png]]

>Verifichiamo la Correttezza

$$
\int_{-\infty}^\infty f(s) \, ds=\int_{0}^\infty ae^{ -as } \, ds=[-e^{ -as }]_{0}^\infty=0-(-1)=1  
$$

>[!question] $F_{X}(t)$ ?

>Consideriamo $t>0$

$$
F_{X}(t)=\int_{0}^t f(s)\, ds=[-e^{ -as }]_{0}^t =-e^{ -at }+1 = 1-e^{ -at }
$$

![[attachements/F di Ripartizione Esponenziale.png]]

### Mancanza di Memoria
>Ricordiamo la [[../3 - Variabili Aleatorie#Mancanza di Memoria|mancanza di memoria]] fatta in precedenza

>[!info] Controlliamo se vale
>$$\mathcal{P}(X\geq t+m|X\geq m)=\mathcal{P}(X\geq t)$$

##### Dimostrazione
$$
\mathcal{P}(X\geq t)=1-F_{X}(t)=1-(1-e^{ -at })
$$

$$
\displaystyle{\frac{\mathcal{P}(X\geq t+m)}{\mathcal{P}(X\geq m)}}=\displaystyle{\frac{e^{ -a(t+m) }}{e^{ -am }}}=e^{ -at }
$$

#### Utilizzo
>[!info] Se $X$ ha densità ***esponenziale***
>Allora possiamo scrivere:
>$$X\sim Exp(a)$$

>[!question] Quando si usa?

Tipicamente viene usata per ***tempi di attesa*** che per la loro natura hanno *mancanza di memoria*

### Valore Atteso

>[!abstract] Formula
>$$E[X]=\int_{-\infty}^\infty sf_{X}(s) \, ds =\int_{0}^\infty sae^{ -as } \, ds$$

>Utilizziamo l'[[../../../Analisi/Calcolo Integrale/Calcolo Integrale#Integrazione per Parti|Integrazione per Parti]]

- $s=f\quad ae^{ -as }=g'$
	- $g=-e^{ -as }$

$$
=\underbrace{ [-se^{ -as }]_{0}^\infty}_{ 0 }-\int _{0}^\infty  -e^{ -as }\, ds = \int _{0}^\infty e^{ -as }\, ds = \frac{1}{a}\underbrace{ \int _{0}^\infty ae^{ -as }\, ds }_{ 1 }=\frac{1}{a}  
$$

##### Esempio
>Supponiamo che mediamente passa una ***porche*** ogni 4 ore

>[!question] Qual è la probabilità che passi una porche entro 3 ore?

- $X\sim Exp\left( \frac{1}{4} \right)$

$$
\mathcal{P}(X\leq 3) = F_{X}(3)=1-e^{ -3/4 }=0.527
$$

### Varianza 
>[!abstract] Formula
> $$Var(X)=E[X^2]-E[X]^2$$

$$
E[X^2]=\int_{0}^\infty s^2ae^{ -as } \, ds
$$
>Utilizziamo l'[[../../../Analisi/Calcolo Integrale/Calcolo Integrale#Integrazione per Parti|Integrazione per Parti]]

- $s=f\quad ae^{ -as }=g'$
	- $g=-e^{ -as }$

$$
=\underbrace{ [-s^2e^{ -as }]_{0}^\infty }_{ 0 }-\int _{0}^\infty-2se^{ -as } \, ds=\frac{2}{a}\underbrace{ \int _{0}^\infty ase^{ -as }\, ds }_{ 1/a } =\frac{2}{a}\cdot \frac{1}{a}
$$

>Quindi, per concludere:

$$
Var(X)=E[X^2]-E[X]^2=\frac{2}{a^2}-\frac{1}{a^2} = \frac{1}{a^2}
$$

#### Esercizio
>$Z=2x-3$

>[!info] Vogliamo esprimere
>La ***funzione di ripartizione*** e la ***densità*** di $Z$ in funzione di $X$

$$
F_{Z}(t)=\mathcal{P}(Z\leq t)=\mathcal{P}(2x-3\leq t) = \mathcal{P}\left( X\leq \displaystyle{\frac{t+3}{2}} \right)= F_{X}\left( \displaystyle{\frac{t+3}{2}} \right)
$$
- ***Densità***

$$
f_{Z}(s)=F'_{X}\left( \displaystyle{\frac{s+3}{2}} \right)\cdot \frac{1}{2}=\frac{1}{2} \cdot f_{X}\left( \displaystyle{\frac{s+3}{2}} \right)
$$

#### Massimo e Minimo
[[8 - Variabili Aleatorie Continue#Massimo e Minimo| Riprendendo questo concetto.]]
##### Esempio
> $X\sim Exp(3)$

>$Y\sim Exp(4)$

***Densità***:

$$
F_{X}(t)=\begin{cases}
1-e^{ -3t }\quad \text{se } t\geq 0 \\
0\qquad \qquad \text{se } t<0
\end{cases}
$$
$$
F_{Y}(t)=\begin{cases}
1-e^{ -4t }\quad \text{se } t\geq 0 \\
0\qquad \qquad \text{se } t<0
\end{cases}
$$
>Siano $Z=(max(X,Y))$ e $W=(min(X,Y))$

>[!question] $\mathcal{P}(W\leq1)$  e $\mathcal{P}(Z\leq2)$ ?

>[!hint] Osservazione
>Possiamo vedere queste due probabilità come:
>- $Z$: Attendo che accadano ***entrambe***
>- $W$: Attendo il ***primo*** che accade

>$Max$

$$
\mathcal{P}(Z\leq 2)=F_{Z}(2)=(1-e^{ -6 })\cdot (1-e^{ -8 })
$$

>$Min$

$$
1-F_{W}(t)=(1-(1-e^{ -3t }))\cdot(1-(1-e^{ -4t }))=e^{ -3t }\cdot e^{ -4t }=e^{ -7t }
$$
$$
F_{W}(t)=\begin{cases}
1-e^{ -7t }\quad \text{se } t\geq 0 \\
0\qquad \qquad \text{se } t<0
\end{cases}
$$
>[!caution] $W\sim Exp(7)$

$\mathcal{P}(W\leq 1)=1-e^{ -7 }$

>[!hint] Osservazione
>Il ***minimo*** fra due *variabili esponenziali* è anche esso una *variabile esponenziale*.
>Come parametro avrà la ***somma dei parametri*** delle due variabili
