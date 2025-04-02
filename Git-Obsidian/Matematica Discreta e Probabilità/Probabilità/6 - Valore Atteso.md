## Valore Atteso di una Variabile Aleatoria Discreta
---
>[!definizione] Definizione
>Se $X$ è [[3 - Variabili Aleatorie#Variabili Aleatorie Discrete|variabile aleatoria discreta]]:
>$$E[X]=\sum_{k}k\cdot d_{X}(k)$$

>Esempio

$X\sim B\left( 2, \displaystyle{\frac{2}{3}} \right)$

- $E[X]=\sum_{k}k\cdot d_{X}(k)$

>$d_{X}(k)=\displaystyle\binom{2}{k}\left( \frac{2}{3} \right)^k\left( \frac{1}{3} \right)^{2-k}$

- $E[X]=\displaystyle\underbrace{ 1\cdot 2\cdot \frac{2}{3 } \cdot \frac{1}{3} }_{ k=1 }+\underbrace{ 2\cdot 1\cdot\left( \frac{2}{3} \right)^2\cdot\left( \frac{1}{3} \right)^0 }_{ k=2 }= \frac{4}{3}$

>[!cite] In Generale
>Se $X\sim B(n,p)$
>$$E[X]=n\cdot p$$


### Proprietà del Valore Atteso

>Problema principale:
>- Studiare $E[X+Y]$

>[!abstract] Proprietà
>Siano $X$ e $Y$ sue variabili e $Z=F(X,Y)$
><u>Allora</u>
>$$E[Z]=\sum_{h,k}F(h,k)\cdot d_{x,y}(h,k)$$

^3cc60c

^prop
##### Corollario
>[!hint] Se $X$ e $Y$ sono ***variabili aleatorie discrete***
>$$E[X+Y]=E[X]+E[Y]$$

###### Dimostrazione
>Per la proprietà appena enunciata:

$$
\begin{array}
\ \displaystyle E[X+Y]=\sum_{h,k}(h+k)d_{X,Y}(h,k) \\
=\displaystyle\sum_{h,k}h\cdot d_{X,Y}(h,k)+\sum_{h,k}k\cdot d_{X,Y}(h,k)= \\
=\displaystyle\sum_{h}h\underbrace{ \sum_{k}d_{X,Y}(h,k) }_{ \text{ densità marginale}}+\sum_{k}k\sum_{h}d_{X,Y}(h,k)= \\
=\displaystyle\sum_{h}h\cdot d_{X}(h)+\sum_{k}k\cdot d_{Y}(k)= E[X]+E[Y]
\end{array}
$$

#### Valore atteso di una Variabile Binomiale
>Calcoliamo, ora, il ***valore atteso*** di $X\sim B(n,p)$: [[3 - Variabili Aleatorie#Variabili Binomiali|variabile binomiale]]

Utilizzando la definizione *avremmo*:
- $E[X]=\displaystyle\sum_{k=0}^nk\binom{n}{k}p^k(1-p)^{n-k}$

>[!fail] Calcolo inutilmente complicato

>[!hint] Osservazione
>$X=X_{1}+X_{2}+\dots+X_{n}$
>Dove $X_{i}$ è:
>- $=1$ se l'$i$-esimo tentativo da ***successo***
>- $=0$ se l'$i$-esimo tentativo da ***insuccesso***
>
>>[!done] $X\sim B(1,p)\quad \forall i=1,\dots n$
>>$$E[X]=E[X_{1}+X_{2}+\dots+X_{n}]=E[X_{1}]+\dots+E[X_{n}]=p+p+\dots+p = np$$

#### Valore Atteso di Variabili Ipergeometriche
>Calcoliamo, ora, il ***valore atteso*** di $X\sim H(b,r;n)$: [[3 - Variabili Aleatorie#Schema Successo-Insuccesso senza Rimpiazzo|variabile Ipergeometrica]]

$$
E[X]=\sum_{k=0}^n k \displaystyle{\frac{\binom{b}{k}\binom{r}{n-k}}{\binom{b+r}{n}}}
$$

>[!fail] Calcolo inutilmente complicato

>[!hint] Osservazione
>$X=X_{1}+X_{2}+\dots+X_{n}$
>Dove $X_{i}$ è:
>- $=1$ se l'$i$-esimo tentativo da ***successo***
>- $=0$ se l'$i$-esimo tentativo da ***insuccesso***
>
>>[!done] $X\sim B\left( 1, \displaystyle{\frac{b}{b+r}} \right)\quad \forall i=1,\dots n$
>>$$E[X]=E[X_{1}+X_{2}+\dots+X_{n}]=E[X_{1}]+\dots+E[X_{n}]=$$
>>$$=\displaystyle{\frac{b}{b+r}}+\dots+\displaystyle{\frac{b}{b+r}} = \displaystyle{\frac{nb}{b+r}}$$

##### Esercizio
>$10$ amici, $6$ vaschette di gelato

- $3$ gusti scelti con probabilità: $\displaystyle{\frac{2}{9}}$
- $3$ gusti scelti con probabilità: $\displaystyle{\frac{1}{9}}$

$$
X_{i}=\begin{cases}
1 \quad \text{se il gusto } i
 \text{ è stato scelto da qualcuno} \\
0 \quad \text{se il gusto } i
 \text{ è stato scelto da nessuno}
\end{cases}
$$
$i=1,2,3,4,5,6$

>[!question] Domande
>1. Densità delle $X_{i}$
>2. Le $X_{i}$ sono variabili indipendenti?
>3. Quante vaschette mi devo aspettare di aprire?

>2.

Le variabili $X_{i}$ sono ***dipendenti***:
- Se *nessuno* sceglie la prima scatola, è *più probabile* che le altre vengano scelte

>1. 

$X_{i}\sim B(1,p)$
- $\mathcal{P}(X_{1}=1)=1-\mathcal{P}(X_{1}=0)=1-\left( \frac{7}{9} \right)^{10}=1-0.08=0.92$
- $\mathcal{P}(X_{4}=1)=1-\mathcal{P}(X_{4}=0)=1-\left( \frac{8}{9} \right)^{10}=1-0.31=0.69$


>3. Alternativa:

>[!question] Qual è il valore atteso del numero di vaschette da aprire?

$X=\#$ vaschette da aprire

- $X=X_{1}+X_{2}+\dots+X_{6}$

>[!done] $E[X]=E[X_{1}]+\dots+E[X_{6}]=3\cdot0.92+3\cdot 0.69=4.83$

#### Valore Atteso di una Variabile Uniforme
>Calcoliamo, ora, il ***valore atteso*** di $X\sim U(\{ a_{1},a_{2},\dots,a_{n} \})$: [[3 - Variabili Aleatorie#Variabili Discrete e Densità Uniforme|variabile uniforme]]

$$
E[X]=\sum_{k}a_{k}d_{X}(a_{k})=\frac{\sum_{k}a_{k}}{n}
$$
>[!done] Semplicemente: La media dei valori che assume

#### Valore Atteso di una Variabile Geometrica
##### Geometrica Modificata
>Calcoliamo, ora, il ***valore atteso*** di $X\sim\tilde{G}(p)$

$X=$ Primo tentativo che da ***successo***

$$
d_{X}=\begin{cases}
(1-p)^{k-1}\cdot p \quad k=1,2,3,\dots \\
0 \qquad\qquad\qquad \text{altrimenti}
\end{cases}
$$

>[!example] Esempio

>Lancio di un Dado, ***successo*** $=$ uscita del numero 6

>[!question] Quanti lanci ci aspettiamo di fare prima di ottenere un 6?

***Risposta***: $6$

>Perché?

$X\sim\tilde{G}\left( \frac{1}{6} \right)$

$$
E[X]=\sum_{k=1}^\infty k\left( \frac{5}{6} \right)^{k-1}\cdot \frac{1}{6}
$$
>[!question] Come si Calcola?

>Ricordiamo la ***serie geometrica***

$$
\sum_{i=0}^\infty x^i = \frac{1}{1-x}\quad 0<x<1
$$
***Deriviamo:***
$$
\sum_{i=1}^\infty ix^{i-1}=\frac{1}{(1-x)^2}
$$
- "La $i$ può partire da 1 poiché la derivata del termine con $0$ è $0$"

>[!note] Abbiamo ottenuto quello che volevamo

$x=\displaystyle\frac{5}{6}$, e otteniamo:

$$
\sum_{k=1}^\infty k\left( \frac{5}{6} \right)^{k-1}\cdot \frac{1}{6}=\frac{1}{\left( 1-\frac{5}{6} \right)^2}\cdot \frac{1}{6}=\frac{1}{\frac{1}{6^2}}\cdot \frac{1}{6} = 6
$$
>[!definizione] In Generale
>$X\sim\tilde{G}(p)$
>$$E[X]=\frac{1}{p}$$

###### Variabile Geometrica
>[!question] E se $X$ fosse una variabile Geometrica "normale"?

$$
\begin{array} 
\ Y\sim G(p) \\
Y+1\sim\tilde{G}(p)
\end{array}
$$
***Quindi***:

$$
E[Y+1]=\frac{1}{p}=E[Y]+\underbrace{ E[1] }_{ 1 } \implies E[Y]=\frac{1}{p}-1
$$

#### Esempio
>Lanciamo un dado fino ad ottenere $6$ due volte
- "Tempo di ***secondo*** successo"

$X=\#$ ***lanci***
>[!question] $E[X]$?

- $X_{1}=\#$ lanci per ottenere il *primo* 6
	- $X_{1}\sim\tilde{G}\left( \frac{1}{6} \right)$
- $X_{2}=\#$ lanci per ottenere il *secondo* 6 ***dopo*** avere ottenuto il *primo*
	- $X_{2}\sim\tilde{G}(p)$

$$
E[X]=E[X_{1}+X_{2}]=E[X_{1}]+E[X_{2}]=6+6=12
$$
Proviamo a calcolare la densità di $x$

$\mathcal{P}(X=k)=\mathcal{P}(2^\circ$ sei esce al $k$-esimo tentativo $)=$
$=\mathcal{P(1^\circ}$ sei esce nei primi $k-1$ tentativi e uno nel $k$-esimo$)=$
$=\displaystyle\binom{k-1}{1}\cdot \frac{1}{6}\cdot\left( \frac{5}{6} \right)^{k-2}\cdot \frac{1}{6}=(k-1)\cdot \frac{1}{6^2}\cdot\left( \frac{5}{6} \right)^{k-2}$

### Valore Atteso del Prodotto
>Che cosa possiamo dire del *valore atteso* del ***prodotto di variabili***?
$$
E[XY]
$$
##### Esempio
>2 Estrazioni *senza rimpiazzo*

- 2 palline rosse
- 3 blu

$$
X_{i}=\begin{cases}
1\quad \text{se la }i \text{-esima è blu} \\
0\quad \text{se è rossa}
\end{cases}
$$

- $X_{1}\sim B\left( 1, \frac{3}{5} \right)$
- $X_{2}\sim B\left( 1, \frac{3}{5} \right)$

$$
X_{1}X_{2}\sim B(1,p)
$$
- $\displaystyle p=\mathcal{P}(X_{1}X_{2}=1)=\mathcal{P}(X_{1}=1,X_{2}=1)=\frac{3}{5 }\cdot \frac{1}{2}=\frac{3}{10}$

Confrontiamo $\frac{3}{10}$ con il ***valore atteso***

$\displaystyle\frac{3}{10}=E[X]\neq E[X_{1}]\cdot E[X_{2}]=\frac{9}{25}$


#### Valore Atteso del Quadrato
>Sia $X\sim B(1,p)$

>[!hint] Formula
>$$E[X^2]=E[X]=p$$
- $X^2=X$ poiché $X$ assume valori $0$ e $1$ $\implies 0^2 = 0,\quad1^2=1$

#### Esempio
>Estrazioni ***con Rimpiazzo***

- $X_{1} \sim B\left( 1, \frac{3}{5} \right)$
- $X_{2} \sim B\left( 1, \frac{3}{5} \right)$

$$
X_{1}X_{2} \sim B\left( 1, \frac{9}{25} \right)
$$
>Controlliamo:

$\mathcal{P}(X_{1}X_{2}=1)=\mathcal{P}(X_{1}=1,X_{2}=1)$
E poiché gli eventi sono ***Indipendenti***:
$$
\mathcal{P}(X_{1}=1)\cdot\mathcal{P}(X_{2}=1)=\frac{9}{25}
$$
>[!done] E abbiamo:
>$$E[X_{1}X_{2}]=E[X_{1}]\cdot E[X_{2}]$$

###### Prodotto di Valori Attesi
>[!info] Proposizione
>Se $X$ e $Y$ sono ***indipendenti***
><u>Allora</u>
>$$E[XY]=E[X]\cdot E[Y]$$

###### Dimostrazione
>Ricordiamo la [[#^3cc60c|Formula]] per calcolare il ***valore atteso***

$$
\sum_{h,k}h\cdot k\cdot d_{X,Y}(h,k)
$$
Siccome le variabili sono ***indipendenti***:
- $d_{X,Y}(h,k)=d_{X}(h)\cdot d_{Y}(k)$

Quindi otteniamo:
$$
\sum_{h,k}h\cdot k\cdot d_{X}(h)\cdot d_{Y}(k)=\underbrace{ \sum_{h}h\cdot d_{X}(h) }_{ E[X] }\cdot\underbrace{ \sum_{k}k\cdot d_{Y}(k) }_{ E[Y] }
$$

>[!warning] ***Non*** è detto l'inverso


