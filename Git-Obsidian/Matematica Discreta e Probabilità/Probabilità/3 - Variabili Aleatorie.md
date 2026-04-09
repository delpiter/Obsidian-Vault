>[!info] Definizioni
>>[!example] Non Formale
>>Una *variabile aleatoria* è una quantità che dipende dal risultato del [[1 - Spazi di Probabilità#Fenomeni Aleatori|fenomeno aleatorio]]
>>Cioè, è una funzione $X:\Omega\to\mathbb{R}$
>
>>[!note] Formale
>>Una *variabile aleatoria* è una funzione $X:\Omega\to\mathbb{R}$ t.c.
>>$\forall a \in\mathbb{R}$
>>$\{ r\in\Omega:X(r)\leq a \}$ è un [[1 - Spazi di Probabilità#Evento|evento]]

#### Esempio 1
>Consideriamo il lancio di una dado 6 volte

- $X=\#$ di volte in cui esce $6$
- $Y=\#$ di volte in cui otteniamo un risultato $>$ del precedente

Se i risultati sono:
- $2\quad6\quad 3 \quad6\quad 4\quad 5$

- $X=2$
- $Y=3$

#### Esempio 2
>Sia $\Omega=\mathbb{Z}$
>Con *eventi* $=\{ \varnothing,\ \mathbb{Z},\ ,2\mathbb{Z},\ 2\mathbb{Z}+1 \}$

>[!question] $X(n)=n$ e $Y(n)=(-1)^n$ sono variabili aleatorie?

>Vediamo $X$

Scelgo $a=0$
- $\{ r\in\mathbb{R}:X(r)\leq 0 \}=\{ n\in\mathbb{Z}:n\leq0 \}=\mathbb{Z}_{\geq0}$

>[!fail] Conlcusione
>$\mathbb{Z}_{\geq 0}$ non è un *evento*, quindi $X$ non è una variabile aleatoria

>Vediamo $Y$

Scelgo $a=0$
- $\{ r\in\mathbb{R}:X(r)\leq 0 \}=\{ n\in\mathbb{Z}:(-1)^n\leq0 \}=2\mathbb{Z}+1$

Scelgo $a\geq 1$
- $\{ n\in\mathbb{Z}:(-1)^n\leq a \}=\mathbb{Z}$

Scelgo $-1 \leq a <1$
- $\{ n\in\mathbb{Z}:(-1)^n\leq a \}=2\mathbb{Z}+1$

Scelgo $a< -1$
- $\{ n\in\mathbb{Z}:(-1)^n\leq a \}=\varnothing$

>[!done] Conclusione
>$\forall a$ vale la condizione, $Y$ è una variabile aleatoria


### Abbreviazione
>Sia $X$ una *variabile aleatoria*

>[!note] $\forall t\in \mathbb{R}$
>$$\{ r\in\mathbb{R}:X(r)\leq t \}=\{ X\leq t \}$$

- Posso calcolare $\mathcal{P}(X\leq t)$ poiché è un *evento*

>[!example] $F_{X}(t)=\mathcal{P}(X\leq t)$
>È una funzione  $\mathbb{R}\to[0,1]$ che chiamiamo funzione di ripartizione

#### Versioni Equivalenti

>[!question] Sappiamo che $X\leq t$ è un evento $\forall t$, anche $X> t$ è un evento?

$X>t$
- È un *evento* perché è il **complementare** di $X\leq t$

$X<t$
- È un *evento* perché è **unione** di eventi
	- $X<t=\bigcup\limits_{n>0}X\leq t-\displaystyle\frac{1}{n}$

$X\geq t$
- È un *evento* perché è **complementare** del precedente

$X=t$
- È un *evento* perché è **intersezione** di eventi: "$X\geq t\cap X\leq t$"

$X\neq t$
- È un *evento* perché è **complementare** del precedente

>[!done] Conclusione 
>È Sempre *evento*


## Variabili Aleatorie Discrete
---
>[!info] Definizione
>Una *variabile aleatoria* si dice ***discreta*** se assume una quantità di valori *finita* o *numerabile*

#### Esempio
>Compriamo uno smartphone e lo usiamo finché si rompe

$X=$ Tempo trascorso
- **Non discreto**

$Y=$ Numero di messaggi inviati
- *Numerabile* e quindi *discreto*

$Z$:
- $Z=1$ se sono state effettuate almeno $5$ chiamate al giorno
- $Z=0$ altrimenti
- *Numerabile* e quindi *discreto*

### Variabili Discrete
>Lanciamo un dado 2 volte

$X=\#$ di volte che esce $6$
- $X$ può assumere i valori: $\{ 0,1,2 \}$

$\mathcal{P}(X=0)=\displaystyle\frac{5}{6}\cdot \frac{5}{6}=\frac{25}{36}$
$\mathcal{P}(X=1)=\displaystyle2\cdot \frac{5}{6}\cdot \frac{1}{6}$
$\mathcal{P}(X=2)=\displaystyle\frac{1}{6} \cdot \frac{1}{6}=\frac{1}{36}$

>[!note] Osservazione
>La somma dei 3 risultati è $1$


#### Densità
>[!info] Definizione
>La ***densità*** di una *variabile aleatoria* **discreta** è una funzione:
>$$\begin{array}\ d_{X}:\mathbb{R}\to[0,1] \\k\mapsto \mathcal{P}(X=k)\end{array}$$

>Dall'esempio di prima

$$
d_{X}(k)=\begin{cases}
\displaystyle{\frac{25}{36}}\quad \text{ se }k=0 \\
\displaystyle{\frac{10}{36}}\quad \text{ se }k=1 \\
\displaystyle{\frac{1}{36}}\quad \text{ se }k=2
\end{cases}
$$

>[!note] Osservazione
>Se $d_{X}$ è la ***densità*** di $X$
><u>Allora</u>
>- $d_{X}(k)\geq 0$
>- $d_{X}(k)>0$ per una quantità discreta di valori $k$
>- $\displaystyle\sum_{k}d_{X}(k)=1$


##### Densità Discreta Astratta
>[!abstract] Definizione
>Una funzione $d:\mathbb{R}\to\mathbb{R}$ si dice ***densità discreta astratta*** se:
>- $d(k)\geq 0$
>- $d(k)>0$ per una quantità discreta di valori $k$
>- $\displaystyle\sum_{k}d(k)=1$

###### Esempio
>Insieme finito
$$
d(k)=\begin{cases}
\displaystyle{\frac{1}{4}}\quad \text{se }k=\{ -1,3 \} \\
\displaystyle{\frac{1}{2}}\quad \text{se } k=10 \\
\ 0 \ \quad \text{altrimenti}
\end{cases}
$$
>Esempio di ***densità discreta astratta***


###### Esempio
>Insieme Numerabile

$$
d(k)=\begin{cases}
2^{-k}\quad \text{ se } k=\{ 1,2,3,\dots \}\\
0 \qquad \text{ altrimenti}
\end{cases}
$$

>[!done] 1\) $d(k)\geq 0$

>[!done] 2\) $d(k)> 0$
>Solo se $k$ è intero positivo

>[!done] 3\) $\frac{1}{2}+\frac{1}{4}+\frac{1}{8}+\dots$
>Serie che converge verso $1$


### Variabili Discrete e Densità Uniforme
>[!info] Definizione
>Dato un insieme $A=\{ a_{1},a_{2},\dots,a_{n} \}\subseteq \mathbb{R}$, consideriamo la funzione:
>$$d(k)=\begin{cases}\displaystyle{\frac{1}{n}}\quad \text{ se } k=a_{1},a_{2},\dots,a_{n} \\\ 0 \quad \ \text{ altrimenti}\end{cases}$$
>Una funzione di ***densità astratta uniforme*** su $A$
>>[!note] Notazione
>>Se $X$ è una variabile aleatoria t.c. $dx=d$
>>Diciamo che $X$ è uniforme su $A$ e scriviamo
>>$$X \sim U(A)$$

##### Esempio
>Consideriamo il lancio di un dado

$X=$ Il *risultato*

$$
dx(k)=\begin{cases}
\frac{1}{6}\quad \text{ se } k=\{ 1,\dots,6 \} \\
\ 0 \quad \text{ altrimenti}
\end{cases}
$$

- $X\sim U(\{ 1,2,3,4,5,6 \})$

#### Variabili e Densità di Bernoulli
>([Bernoulli](https://pixarcars.fandom.com/wiki/Francesco_Bernoulli))

>[!info] Definizione
>Una variabile aleatoria $X$ è di Bernoulli se assume solo valori $0$ e $1$
>$$d_{X}(k)=\begin{cases}p \qquad \quad\text{ se } k=1 \\1-p \quad \ \text{ se } k=0 \\0 \qquad \quad \text{ altrimenti}\end{cases}$$
>>[!Note] Notazione
>>Scriviamo in questo caso:
>>$$X \sim B(1,p)$$

>Se $E$ è un *evento*

La funzione indicatrice di $E$ è:
$$
X_{E}=\begin{cases}
1 \quad \text{se }\ E \ \text{ accade} \\
0 \quad \text{se }\ E \ \text{ non accade}
\end{cases}
$$
- $X_{E}\sim B(1,\mathcal{P}(E))$
##### Esempio
>Consideriamo il lancio di un dado

$$
X=\begin{cases}
1 \quad \text{se il risultato } \geq 5 \\
0 \quad \text{se il risultato } < 5 
\end{cases}
$$
- $\mathcal{P}(X=1)=\displaystyle{\frac{1}{3}}$
- $\mathcal{P}(X=0)=\displaystyle{\frac{2}{3}}$

$$
X\sim B(1,3)
$$


### Variabili Binomiali
##### Esempio Introduttivo
>Roulette con 3 puntate sul ***rosso*** (18 rossi, 18 neri, 1 verde)

- $X=\#$ di vittorie

$\mathcal{P}(X=0)=\left( \displaystyle{\frac{19}{37}} \right)^3$
- $\frac{19}{37}\to$ Possibili permutazioni delle *non vincite*
$\mathcal{P}(X=1)=3\cdot \displaystyle{\frac{18}{37}}\cdot\left( \displaystyle{\frac{19}{37}} \right)^2$
- $3\to$ *Vincita* di ***una*** delle 3 puntate, $\frac{18}{37}\to$Probabilità di *vincita*
$\mathcal{P}(X=2)=\displaystyle\binom{3}{2}\cdot \left(\displaystyle{\frac{18}{37}}\right)^2\cdot\displaystyle{\frac{19}{37}}$
$\mathcal{P}(X=3)=\left(\displaystyle{\frac{18}{37}}\right)^3$

### Schema Successo-Insuccesso a Prove Indipendenti
>[!definizione] Definizione
>Effettuiamo $n$ *prove* o *tentativi*, ognuna delle quali può dare ***successo*** o ***insuccesso***, **indipendente** l'uno dall'altro
>Ogni prova ha probabilità $p$ di avare *successo*
>>[!note] Variabile Binomiale
>>Tale variabile $X$ si dice ***binomiale*** di parametri $n$ e $p$
>>$$X\sim B(n,p)$$

$$
dx(k)=\begin{cases}
\displaystyle\binom{n}{k}\cdot p^k\cdot (1-p)^{n-k} \quad \text{se } k=0,1,\dots,n \\
0 \qquad\qquad\qquad\qquad\quad\  \text{altrimenti}
\end{cases}
$$
- Il *coefficiente binomiale* indica i modi di scegliere le $k$ prove che danno successo fra le $n$ disponibili

#### Esempio
>10 studenti ad un esame

Ognuno ha la probabilità di passare l'esame $=\displaystyle\frac{2}{3}$

>[!question] Qual è la probabilità che esattamente $7$ di loro passino l'esame?

$X=\#$ di studenti che *passano* l'esame

$$
\mathcal{P}(X=7)=\binom{10}{7}\left( \displaystyle{\frac{2}{3}} \right)^7\left( \displaystyle{\frac{1}{3}} \right)^3 
$$

### Schema Successo-Insuccesso senza Rimpiazzo
>[!definizione] Definizione
>Effettuiamo $n$ *prove* o *tentativi*, ognuna delle quali può dare ***successo*** o ***insuccesso***
>
>>[!caution] Nota Bene
>>Le prove sono ***dipendenti*** anche se ciascuna ha la *stessa probabilità* di dare successo
>
>>[!note] Variabile Ipergeometrica
>>$$X\sim H(b,r;n)$$
>>$b\to$ Successi
>>$r\to$ Insuccessi

$$
dx(k)=\begin{cases}
\displaystyle{\frac{\displaystyle\binom{b}{k}\binom{r}{n-k}}{\displaystyle{\binom{b+r}{n}}}}\quad \text{se }k=0,1,2,\dots,n \\
0 \qquad\qquad\qquad\  \text{ altrimenti}
\end{cases}
$$
- Numeratore -> Casi *Favorevoli*
- Denominatore -> Casi *Possibili*

#### Esempio
>$b=5$ palline blu, $r=4$ palline rosse, $n=6$ estrazioni

$X=\#$ ***successi*** $=\#$ palline blu estratte

>[!question] Qual è la probabilità di estrarre $3$ palline blu?

$$
\mathcal{P}(X=3)=\displaystyle{\frac{\displaystyle\binom{5}{3}\binom{4}{6-3}}{\displaystyle\binom{5+4}{6}}}=\frac{10}{21}
$$
#### Doppio Esempio
>[!note] Problema 1
>Ho delle confezioni da $3$ bulloni, ogni bullone ha il $20$% di probabilità di essere difettoso
>>[!question] Qual è la probabilità che una confezione contenga ***al più*** 1 bullone difettoso

>[!note] Problema 2
>Un'urna contiene $8$ palline rosse e 2 bianche. Ne estraiamo $3$ senza rimpiazzo.
>>[!question] Qual è la probabilità di estrarre al più una bianca?

>[!done] In entrambi i casi ho al massimo $1$ ***insuccesso***

1. $X=\#$ di bulloni buoni

$X\sim B(3,0.8)$
- $\mathcal{P}(X\geq 2)=\mathcal{P}(X=2)+\mathcal{P}(X=3)=\displaystyle\binom{3}{2}\cdot 0.8 * 0.2 +0.8^3=0.896$

2. $Y=\#$ Palline rosse estratte

$Y\sim H(8,2,3)$
- $\mathcal{P}(Y\geq2)=\mathcal{P}(Y=2)+\mathcal{P}(Y=3)=$
$$
\displaystyle{\frac{\displaystyle\binom{2}{8}\cdot \displaystyle\binom{2}{1}}{\displaystyle\binom{10}{3}}}+\displaystyle{\frac{\displaystyle\binom{3}{8}\cdot \displaystyle\binom{2}{0}}{\displaystyle\binom{10}{3}}}=0,933
$$

### Schema Successo-Insuccesso a Prove Indipendenti Consecutive
>[!definizione] Densità Geometrica
>Fissiamo il numero di Prove e procediamo finché otteniamo un successo
>$X=\#$ di *insuccessi* prima di un *successo*
>$p=$ probabilità do avere successo in *ogni tentativo*
>>[!note] Notazione
>>$$X\sim G(p)$$

>Prova: Lancio di un dado

***Successo***= uscita del numero 6

- $\mathcal{P}(X=0)=\frac{1}{6}$
- $\mathcal{P}(X=1)=\frac{1}{6}\cdot \frac{5}{6}$
- $\mathcal{P}(X=2)=\frac{1}{6}\cdot \left( \frac{5}{6} \right)^2$
- $\dots$
- $\mathcal{P}(X=k)=\frac{1}{6}\cdot (\frac{5}{6})^k$


$$
dx(k)=\begin{cases}
(1-p)^k\cdot p \quad \text{se } k=0,1,2,\dots \\
0 \qquad\qquad \quad \text{altrimenti}
\end{cases}
$$

>[!hint] Osservazione
>Osserviamo che assume infiniti valori, abbiamo:
> $$\sum_{k=0}^\infty(1-p)^k\cdot p=1$$

##### Dimostrazione
>Verifichiamo:

$$
\begin{array}
\ 1-a^{n+1}=(1-a)(1+a+a^2+a^3+\dots+a^n)= \\
=1\cancel{ +a }\cancel{ -a }\cancel{ +a^2 }\cancel{ -a^2 }+\dots\cancel{ +a^n }\cancel{ -a^n }-a^{n+1}
\end{array}
$$
Quindi:
$$
\sum_{k=0}^na^k=\frac{1-a^{n+1}}{1-a}
$$
>Se $0<a<1$ e $n\to \infty$

$$
\sum_{k=0}^\infty a^k=\frac{1}{1-a}
$$
- Poniamo $a=1-p$

>[!done] Abbiamo verificato che la densità geometrica è una densità *discreta*

#### Variabile Geometrica Modificata
>Talvolta consideriamo la variabile $T=$"***Tempo di primo successo***" data dal numero di tentativi per ottenere il primo successo

>[!hint] Osservazione
>$$T-1\sim G(p)$$
>$T$ si dice "***Geometrica Modificata***"

$$
T\sim\tilde{G}(p)
$$
$$
d_{T}(k)=\begin{cases}
(1-p)^{k-1}\cdot p \quad \text{se } k=1,2,3,\dots \\
0 \qquad \qquad \qquad \text{altrimenti}
\end{cases}
$$
#####  Esempio
>Lanciamo un dado tante volte fino ad ottenere 6

>[!question] Qual è la probabilità di fare 4 lanci?

$X=\#$ di lanci $\sim\tilde{G}\left( \frac{1}{6} \right)$
$$
\mathcal{P}(X=4)=\left( \displaystyle{\frac{5}{6}} \right)^3\cdot \frac{1}{6} 
$$
###### Esempio più complesso
>Lanciamo 2 dadi ripetutamente fino ad ottenere due 6

$X=\#$ di lanci per ottenere il primo 6 con il primo dado
$Y=\#$ di lanci per ottenere il primo 6 con il secondo dado
$Z=\#$ di lanci totale

>[!question] Determinare: La densità di $X,Y,Z$; La probabilità $\mathcal{P}(X<Y)$
>

1. $X\sim \tilde{G}\left( \frac{1}{6} \right)$
2. $Y\sim \tilde{G}\left( \frac{1}{6} \right)$
3. $Z\sim \tilde{G}\left( \frac{1}{36} \right)$

$$
\begin{array}
\ \mathcal{P}(X<Y) + \mathcal{P}(X>Y)+\mathcal{P}(X=Y)=1 \\
2\mathcal{P}(X<Y) +\mathcal{P}(X=Y)=1
\end{array}
$$
- Calcoliamo $\mathcal{P}(X=Y)$

$$
\begin{array}
\ \mathcal{P}(X=Y)=\displaystyle\sum_{k=1}^\infty\mathcal{P}(X=Y=k)=\displaystyle\sum_{k=1}^\infty\mathcal{P}(X=k)\cdot\mathcal{P}(Y=k) =\\
=\displaystyle\sum_{k=1}^\infty\left( \frac{5}{6} \right)^{k-1}\cdot \frac{1}{6}\cdot\left( \frac{5}{6} \right)^{k-1}\cdot \frac{1}{6}= \\
\displaystyle\sum_{k=1}^\infty\left( \frac{25}{36} \right)^{k-1}\cdot \frac{1}{36}=\frac{1}{36}\cdot\displaystyle\sum_{h=0}^\infty\left( \frac{25}{36} \right)^h= \\
=\displaystyle\frac{36}{11}\cdot \frac{1}{36}=\frac{1}{11}
\end{array}
$$
>Quindi

$\mathcal{P}(X<Y)=\frac{1-\mathcal{P}(X=Y)}{2}=\frac{5}{11}$

#### Mancanza di Memoria
>[!note] Problema
>Se ho ottenuto $k$ ***insuccessi***, la probabilità di ottenerne altri $m$ è uguale alla probabilità di avere $m$ ***insuccessi*** dall'inizio

##### Dimostrazione
$$
\mathcal{P}(X\geq k+m|X\geq k)=\mathcal{P}(X\geq m)
$$

$$
\frac{\mathcal{P}(X\geq k+m)}{\mathcal{P}(X\geq k)}=\frac{(1-p)^{k+m}}{(1-p)^{k}}=(1-p)^m=\mathcal{P}(X\geq m)
$$

### Variabili di Poisson
>In *Italia* nascono 1 milione di ***bambini l'anno***, una ***malattia*** colpisce un bambino ogni ***200.000***

>[!question] Qual è la probabilità che in un anno nascano più di ***5*** bambini ***malati***?

$X=\#$ di bambini malati $\sim B\left( 10^6, \displaystyle{\frac{1}{200.000}} \right)$

>[!warning] I calcoli sono fatti su numeri talmente grandi che neanche la *calcolatrice* è in grado di farli
 
>[!definizione] Definizione
>Le ***variabili di Poisson*** vengono usate quando il numero degli *insuccessi* è **molto più grande** del numero dei *successi*
>Consideriamo
>$$d(k)=\begin{cases}e^{ -\lambda }\cdot \displaystyle{\frac{\lambda^k}{k!}} \quad \text{se }k=0,1,2,\dots \\0 \qquad\qquad \text{altrimenti}\end{cases}$$
>Dove $\lambda>0$ è un parametro in $\mathbb{R}$
>>[!question] È una densità astratta?

##### Verifica
> 1. È Sempre maggiore di $0$?

$e^{ -\lambda }\cdot \displaystyle{\frac{\lambda^k}{k!}}>0 \quad \forall k\in\mathbb{R}$

> 2. 

$d(k)\neq 0$ Per una ***quantità discreta*** di valori

> 3. $\displaystyle\sum_{k=0}^\infty e^{ -\lambda }\cdot \displaystyle{\frac{\lambda^k}{k!}}=1$? 

- Per la [[../../Analisi/Taylor/Formule di Taylor di Funzioni Elementari|formula di Taylor]]:
$e^x=\displaystyle\sum_{k=0}^\infty \frac{x^k}{k!}$

Quindi:
$$
e^{-\lambda}\sum_{k=0}^\infty \frac{\lambda^k}{k!}=e^{ -\lambda }\cdot e^{ \lambda }=1
$$
>[!done] È una densità astratta

#### Applicazione
>Consideriamo una variabile ***binomiale*** con $n$ grande e $p$ piccolo

$p=\frac{\lambda}{n}$

$$
X\sim B\left( n, \frac{\lambda}{n} \right)
$$
$\mathcal{P}(X=k)=\displaystyle\binom{n}{k}\cdot \left( \frac{\lambda}{n} \right)^k\cdot \left( 1- \frac{\lambda}{n} \right)^{n-k}$
- $=\displaystyle{\frac{n(n-1)\dots(n-k+1)}{k!}}\cdot \frac{\lambda^k}{n^k}\cdot\left( 1- \frac{\lambda}{n} \right)^n\cdot\left( 1- \frac{\lambda}{n} \right)^k=$
- $=\displaystyle\frac{\lambda^k}{k!}\cdot\underbrace{ \frac{n(n-1)\dots(n-k+1)}{n^k} }_{ \text{ tende a 1 per }n\to\infty }\cdot\underbrace{ \left( 1- \frac{\lambda}{n} \right)^n }_{ e^-\lambda }\cdot\underbrace{ \left( 1- \frac{\lambda}{n} \right)^k }_{ 1 }$

>Tornando all'esempio iniziale:

$X\sim B\left( 10^6, \displaystyle{\frac{1}{200.000}} \right)$
- Può essere approssimato con una ***variabile di Poisson***
	- Con $\lambda=10^6\cdot \frac{1}{200000}=5$

Quindi:
$$
\mathcal{P}(X>5)=1-\mathcal{P}(X\leq 5)=1-e^{-5}\left( \frac{5^0}{0!}+\frac{5^1}{1!}+\frac{5^2}{2!}+\frac{5^3}{3!}+\frac{5^4}{4!}+\frac{5^5}{5!} \right)=0,384
$$
>Usando la binomiale:

$$
\mathcal{P}(X=5)=\binom{1000000}{5}\cdot\left( \frac{1}{200000} \right)^5\cdot\left( \frac{199999}{200000} \right)^{9999995}
$$