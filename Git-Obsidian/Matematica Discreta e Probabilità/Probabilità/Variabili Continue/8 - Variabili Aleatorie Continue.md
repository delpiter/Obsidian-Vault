>[!info] Concetto
>Le [[3 - Variabili Aleatorie|Variabili Aleatorie]] ***Continue*** assumono valori *reali* e non semplicemente *interi* ( o *numerabili*)
>Tipicamente si usano in ***caso di misurazioni***
>>[!example] Esempi
>>Peso, Lunghezza, Tempo, Soldi, etc...

#### Esempi
>Persona a dieta per $8$ settimane

$X=$ Peso alla fine della dieta

>Bambino nato oggi

$Y=$ Altezza in un anno

>Alla fermate del Bus

$T=$ Tempo di attesa

>Investiamo $100$€ in azioni

$Z=$ Valore tra un anno

## Funzione di Ripartizione
---
>Riprendiamo il concetto di [[5 - Trasformazioni di Variabili Aleatorie#Caso Speciale|Funzione di Ripartizione]] fatto in *precedenza*

>[!definizione] Definizione
>Sia $X$ una [[3 - Variabili Aleatorie|Variabile Aleatoria]] qualunque
>$$\begin{array}\ F_{X}:\mathbb{R}\to[0,1] \\F_{X}(t)=\mathcal{P}(X\leq t)\end{array}$$

#### Esempio Discreto
>$\displaystyle X\sim B\left( 2, \frac{1}{2} \right)$

- $\displaystyle\mathcal{P}(X=0)=\frac{1}{4}\quad \mathcal{P}(X=1)=\frac{1}{2}\quad \mathcal{P}(X=2)=\frac{1}{4}$
>[!question] Chi è la funzione di ripartizione?

![[FxDiscreta.png]]

- $F_{X}(1.1)=\mathcal{P}(X\leq 1.1)=\mathcal{P}(X=0)+\mathcal{P}(X= 1)=\displaystyle \frac{1}{4}+\frac{1}{2} = \frac{3}{4}$

## Variabile Aleatoria Continua
---
>[!definizione] Definizione
>Una [[3 - Variabili Aleatorie|Variabile Aleatoria]] $X$ si dice ***Continua*** se $F_{X}(t)$ è *continua*

![[Funzione di Ripartizione Continua.png]]

- $\mathcal{P}(X\leq -1)=F_{X}(-1) = 0$
- $\mathcal{P}\left( X> \frac{3}{2} \right)=1-\mathcal{P}\left( X\leq \frac{3}{2} \right)=1-F_{X}\left( \frac{3}{2} \right)=1-\frac{3}{4}=\frac{1}{4}$
- $\mathcal{P}(X\leq 3)=F_{X}(3)=1$
- $\mathcal{P}(X\leq1)=F_{X}(1)=\frac{1}{2}$

>Caso Speciale

>[!question] $\mathcal{P}(X=1)$ ?

$$
\mathcal{P}(X=1)\leq \mathcal{P}\left( 1-\frac{1}{n}<X\leq1 \right)=\mathcal{P}(X< 1)-\mathcal{P}\left( X\leq 1- \frac{1}{n} \right)=
$$
- Per $n \longrightarrow \infty$
$$
= F_{X}(1)-F_{X}\underbrace{ \left( 1- \frac{1}{n} \right) }_{ \to 1 } = 0
$$
>[!caution] Questo ragionamento vale più in generale
>Se $X$ è una ***variabile aleatoria continua***
><u> Allora</u>
>$$\mathcal{P}(X=t)=0\quad \forall t$$

>[!hint] Osservazione
>Siccome $\mathcal{P}(X=t)=0$
><u>Allora</u>
>- $\mathcal{P}(X\leq t)=\mathcal{P}(X< t)$
>- $\mathcal{P}(X\geq t)=\mathcal{P}(X> t)$

>Quello che avrà più interesse chiedersi è piuttosto:

>[!tldr] $\mathcal{P}(a<X<b)$ per opportuni $a$ e $b$
>Oppure:
>- $\mathcal{P}(X> a)$
>- $\mathcal{P}(X< b)$

$\mathcal{P}(a<X<b)=F_{X}(b)-F_{X}(a)$

## Densità Continua
---
>[!definizione] Definizione
>La ***densità continua*** di una *variabile aleatoria continua* $X$ è una funzione $f_{X}:\mathbb{R}\to\mathbb{R}$ **tale che**
>$$\forall a<b \quad \mathcal{P}(a<X<b)=\int_{a}^b f_{X}(s)\, ds $$


#### Esempio
![[DensitaContinua.png]]

$\displaystyle\mathcal{P}\left( \frac{1}{3}<X<1 \right)=\int_{1}^{1/3} f_{X}(s)\, ds=\frac{2}{3}$
$\displaystyle\mathcal{P}\left( \frac{1}{2}<X<2 \right)=\int_{1}^{1/2} f_{X}(s)\, ds+\underbrace{ \int_{2}^{1} f_{X}(s) }_{ 0 }\, ds=\frac{1}{2}$


### Funzione di Ripartizione e Densità Astratte 
>[!definizione] Definizione
>Una $f:\mathbb{R}\to\mathbb{R}$ è una ***funzione di ripartizione astratta*** se:
>1. $\lim\limits_{t\to -\infty}f(t)=0\quad \lim\limits_{t\to \infty}f(t)=1$
>2. $f(t)$ ***deve*** essere continua
>3. $f(t)$ è ***debolmente crescente***

>[!tl;dr] Definizione
>Una $f:\mathbb{R}\to\mathbb{R}$ è una ***densità continua astratta*** se:
>1. $f(s)\geq 0\quad \forall s$
>2. $\displaystyle \int_{+\infty}^{-\infty}f(s)  \, ds=1$
>
>>[!warning] Attenzione
>>La densità ***non*** è necessariamente una *funzione continua*

>[!question] Chi è $F_{X}(t)$ ?

- $F_{X}(2)=\mathcal{P}(X\leq 2)=\displaystyle\int_{-\infty}^2 f(s)\, ds=1$
>Sia $0<t<1$

- $F_{X}(t)=\mathcal{P}(X\leq t)=\displaystyle\int_{0}^t f(s)\, ds=t$

***Quindi***:

$$
F_{X}(t)=\begin{cases}
0 \quad \text{se }t\leq0 \\
t \quad \text{se } 0\leq t \leq 1 \\
1 \quad \text{se } t\geq 1
\end{cases}
$$
![[FX data la Densità.png]]

### Legame fra i due Concetti
>Calcoliamo la Probabilità che $a\leq X\leq b$

>[!note] Legame
>$$\int_{a}^b f_{X}(s)\, ds = F_{X}(b)-F_{X}(a)$$

>***Conseguenza***:

$$
F'_{X} =f_{X}
$$
- *Viceversa*

$$
F_{X}(t)=\int_{-\infty}^t f_{X}(s)\, ds 
$$
#### Esercizio
>Data la seguente ***densità***

$$
f(s)=\begin{cases}
0 \quad \text{se }s\leq 0  \ \vee \ s\geq 2 \\
s^2 \quad \text{se } 0\leq s \leq 1 \\
\frac{2}{3}\quad \text{se } 1\leq s\leq 2
\end{cases}
$$

![[EsempioRelazione.png]]

>[!question] È una ***densità continua***?


1. $f(s)\geq 0$
>[!done] Si 

2. $$\int_{-\infty}^{+\infty}f(s)  \, ds =1$$

>Controlliamo

$$
\int_{0}^1 s^2 \, ds+\int_{1}^2 \frac{2}{3}\, ds = \left[ \frac{s^3}{3} \right]_{0}^1 +\frac{2}{3}=1 
$$
>[!done] Verificato

>[!question] Chi è la ***funzione di ripartizione***?

>Per $t\geq2$

Abbiamo appena calcolato che:
$$
\int_{-\infty}^{t} f(s)\, ds=1 
$$
>Per $0<t<1$

$$
F_{X}(t)=\mathcal{P}(X\leq t)=\int_{-\infty}^t f(s)\, ds =\int_{0}^t s^2\, ds = \frac{t^3}{3} 
$$

>Per $1<t<2$

$$
F_{X}(t)=\mathcal{P}(X\leq t)=\int_{-\infty}^t f(s)\, ds =\underbrace{ \int_{0}^1 f(s)\, ds }_{ \frac{1}{3} }+\underbrace{ \int_{1}^t f(s)\, ds }_{ (t-1) \frac{2}{3} }  = \frac{2}{3}t-\frac{1}{3}
$$

![[FunzioneRipartizioneEsercizio.png]]


## Trasformazione di Variabile Continua
---
>[!definizione] Concetti
>Sia $Z=\Phi(X)$
>Per calcolare $F_{Z}(t)$:
>$$F_{Z}(t)=\mathcal{P}(Z\leq t)=\mathcal{P}(\Phi(X)\leq t)$$
>>[!abstract] Bisogna scrivere $\Phi(X)\leq t$ in funzione di $F_{X}(t)$

#### Esempio
>[!caution] $\Phi(X)=X^2=Z$

- $F_{Z}(t)=\mathcal{P}(X^2\leq t)$

>Se $t < 0$

$F_{Z}(t)=0$

>Se $t\geq 0$

$$
\mathcal{P}(X^2\leq t)=\mathcal{P}(-\sqrt{ t }\leq X \leq \sqrt{ t })=F_{X}(\sqrt{ t })-F_{X}(-\sqrt{ t })
$$
>[!note] Prendiamo $X\sim U([-1,2])$
>>[!question] Che densità ha $X^2$ ?

$X^2$ assume valori in $[0,4]$

![[Esempio Trasformazione.png]]

>[!tl;dr] Sia $t$ tra $0$ e $4$

$$
F_{X^2}=\mathcal{P}(X^2\leq t)=F_{X}(\sqrt{ t })-F_{X}(-\sqrt{ t }) 
$$
- Ricordiamo $F_{X}$:
$$
F_{X}(t)=\begin{cases}
\displaystyle{\frac{t+1}{3}}\quad \text{se } -1<t<2 \\
0 \qquad\quad \text{altrimenti} 
\end{cases}
$$

>Se $0<t<1$

$$
\begin{array}
\ F_{X^2}(t)=F_{X}(\sqrt{ t })-F_{X}(-\sqrt{ t })= \\
= \displaystyle{\frac{\sqrt{ t }+1}{3}}-\displaystyle{\frac{-\sqrt{ t }+1}{3}}= \frac{2}{3}\sqrt{ t }
\end{array}
$$
>Se $1<t<4$

$$
F_{X^2}(t)=F_{X}(\sqrt{ t })=\frac{\sqrt{ t}+1}{3}
$$
>[!done] Quindi:

$$
F_{X^2}(t)=\begin{cases}
0\qquad\quad \text{se }t\leq0 \\
\displaystyle\frac{2}{3}\sqrt{ t }\quad \text{ se }0\leq t\leq 1 \\
\displaystyle{\frac{\sqrt{ t }+1}{3}} \text{ se } 1\leq t \leq 4\\
1 \qquad \quad \text{ se } t\geq 4
\end{cases}
$$

![[Esempio Fine Trasformazione.png]]

#### Esempio
>[!caution] $X\sim U([1,2])$

$Z=log(x)$

- $Z$, siccome $log$ è una funzione *crescente*, assume valori tra $\underbrace{ log(1) }_{ 0 }$ e $log(2)$

>Sia $0\leq t \leq log(2)$

$$
F_{log_{X}}(t)=\mathcal{P}(log(X)\leq t) = \mathcal{P}(X\leq e^{ t })=\displaystyle{\frac{e^{ t -1}}{2-1}}=e^{ t }-1
$$
![[Esempio Trasformazione 2.png]]
### Massimo e Minimo
>[!info] Massimo
>Siano $X$ e $Y$ variabili aleatorie ***indipendenti***


$Z=max(X,Y)$
$$F_{Z}(t)=\mathcal{P}(Z\leq t)=\mathcal{P}(max(X,Y)\leq t)=\mathcal{P}(X \leq t, Y\leq t)$$

>[!note] Siccome $X,Y$ sono *indipendenti*
>$\mathcal{P}(X\leq t)\cdot\mathcal{P}(Y\leq t)=F_{X}(t)\cdot F_{Y}(t)$

$W=min(X,Y)$
$$1 -F_{W}(t)=\mathcal{P}(W>t)=\mathcal{P}(min(X,Y)> t)=\mathcal{P}(X> t,Y>t)$$

>[!note] Siccome $X,Y$ sono *indipendenti*
>$\mathcal{P}(X> t)\cdot\mathcal{P}(Y> t)=(1-F_{X}(t))\cdot (1-F_{Y}(t))$
