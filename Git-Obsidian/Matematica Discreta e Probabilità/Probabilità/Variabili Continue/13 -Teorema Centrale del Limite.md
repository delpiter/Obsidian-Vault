>Sia $X\sim U([-1,1])$

![[attachements/TeoremaCentrale1.png]]

Il "***centro***" della funzione è composto da *un segmento di grado* $0$

>Siano $X_{1},X_{2}\sim U([-1,1])$ ***indipendenti***

>[!question] $X_{1}+X_{2}$ ?

Come già detto prima, ***non*** abbiamo strumenti adatti per fare la *somma di due variabili continue*
- Ma ci possiamo immaginare il *grafico*

>[!caution] Grafico
>Sappiamo che assumerà valori compresi tra $-2$ e $2$
>Sappiamo, inoltre che sarà *più probabile* che assumerà valori vicini allo $0$

![[attachements/TeoremaCentrale2.png]]

Funzione composta da $2$ *segmenti di grado* $1$

>Siano $X_{1},X_{2},X_{3}\sim U([-1,1])$ ***indipendenti***

>[!question] $X_{1}+X_{2}+X_{3}$ ?

>[!caution] Grafico
>Sappiamo che assumerà valori compresi tra $-3$ e $3$
>Sarà formata da $3$ *segmenti di grado* $2$
>- $[-3,-1],\quad [-1,1]\quad [1,3]$

>[!hint] Osservazione
>La ***densità*** della somma $X_{1}+\dots+X_{n}$ di $n$ variabili $U([[12 - Variabile Normale o Gaussiana|-1,1]] $N(\mu,\sigma^2)$, dove:
>- $\mu=E[X_{1}+\dots+X_{n}]=0$
>- $\sigma^2=Var(X_{1}+\dots+X_{n})=n\cdot Var(X_{1})=n\cdot \frac{2^2}{12}=\frac{n}{3}$
>
>>[!done] $X_{1}+X_{2}+\dots+X_{n}\sim N\left( 0, \frac{n}{3} \right)$

##### Esempio
>Dati dieci numeri casuali compresi tra $-1$ e $1$

>[!question] Qual è la probabilità che la somma dei dieci numeri sia $>7$ ?

$\mathcal{P}(X_{1}+\dots+X_{n}>7)$

Come abbiamo appena visto:
- $\underbrace{ X_{1}+\dots+X_{n} }_{ \zeta }\sim N\left( 0, \frac{10}{3} \right)$
$\mathcal{P}(\zeta>7)=\mathcal{P}\left( \zeta_{0}> \displaystyle\frac{7}{\sqrt{ \frac{10}{3} }} \right)=\mathcal{P}(\zeta_{0}>3.85)\simeq 0$

### Generalizzazione
>[!abstract] Sia $X$ qualunque
>$X_{1},X_{2}$ con la ***stessa densità*** e ***indipendenti***
>La *densità* di $X_{1}+X_{2}$ viene "*smussata*" dalle compensazioni
>
>>[!note] Osservazione
>>Più è *regolare* la ***densità*** meno variabili sono necessarie per avere una ***buona approssimazione***
>

## Teorema Centrale del Limite
---
>[!definizione] Definizione
>Siano $X_{1},\dots,X_{n}$ [[../3 - Variabili Aleatorie|Variabili aleatorie]] ($n\geq20$) *indipendenti*, aventi tutte la ***stessa densità***
>Sia $\mu=E[X_{1}]$ e $\sigma^2=Var(X_{1})$
><u>Allora</u>
>$$X_{1}+X_{2}+\dots+X_{n}\sim N(n\mu,n\sigma^2)$$
>>[!done] Con "***Buona Approssimazione***"

La somma $X_{1}+X_{2}+\dots+X_{n}$ si scrive anche come:
$$
S_{n}
$$
###### Alternativa
>[!info] Versione Equivalente
>$S_{n}=X_{1}+\dots+x_{n}\sim N(n\mu,n\sigma^2)$
>

$$\overline{X_{n}}=\frac{S_{n}}{n}=\frac{X_{1}+\dots+X_{n}}{n}\sim N\left( \frac{\cancel{ n }\mu}{\cancel{ n }}, \frac{\cancel{ n }\sigma^2}{n^\cancel{ 2 }} \right)=N\left( \mu, \frac{\sigma^2}{n} \right)$$

#### Esempio
>Un componente elettronico ha un tempo di vita [[11 - Variabili Esponenziali|esponenziale]] di media $10$ giorni

Ne abbiamo $40$

>[!question] Qual è la probabilità che bastino per un anno?

- $X_{1},X_{2},\dots,X_{40}$: *Tempi di vita* dei componenti

$X_{i}\sim Exp\left( \frac{1}{10} \right)$ e $X_{i}$ sono tutte *indipendenti*

$$
\zeta = X_{1}+X_{2}+\dots+X_{40}\sim N(40\cdot10, 40\cdot 100)
$$
$\mathcal{P}(\zeta>365)=\mathcal{P}\left( \zeta_{0}> \displaystyle{\frac{365-400}{\sqrt{ 4000 }}} \right)=\mathcal{P}(\zeta_{0}>-0.55)=\Phi(0.55)=0.7088$

###### Procedimento inverso
>[!question] Quanti componenti mi servono per avere la probabilità del $90$% che bastino per un anno?
>$\mathcal{P}(S_{n}>365)\geq 90$ %

$S_{n}\sim N(10n,100n)$
- $S_{n}=10\sqrt{ n }\zeta_{0}+10n$
>[!caution] Standardizzo

$\mathcal{P}\left( \zeta_{0}> \displaystyle{\frac{365-10n}{10\sqrt{ n }}} \right)\geq 0.9$

Cerchiamo dentro la ***tabella*** il valore $0.9$:
- $\Phi(1,28)=0,9$
![[attachements/InversoTCL.png]]

Quindi:
$$
\displaystyle{\frac{365-10n}{10\sqrt{ n }}} \leq -1.28
$$
Risolvendo la *disequazione*:
$$
n\geq 46
$$
##### Con Variabili Discrete
>[!question] Il teorema vale anche per le variabili discrete?

>[!done] Si
>Ma bisogna applicare qualche trucchetto per ***trasformare*** la densità *discreta* in densità *continua*

>Sia $X$ una variabile con la seguente densità:

$$
d_{X}(k)=\begin{cases}
\displaystyle\frac{1}{2} \quad \text{se }k=0 \\
\displaystyle\frac{1}{3} \quad \text{se }k=1 \\
\displaystyle\frac{1}{6} \quad \text{se }k=2 \\
0 \quad \text{ altrimenti}
\end{cases}
$$
>Dobbiamo "*estendere*" la densità in modo che risulti come continua

![[attachements/TeoremaCentraleDiscreto.png]]

La nuova densità "*estende*" ogni punto di $d_{X}$, tenendolo come centro.

>Consideriamo ora $30$ variabili $X_{1},X_{2},\dots,X_{30}$ aventi la densità appena descritta

$\mathcal{P}(X_{1}+\dots+X_{30}\geq 15)=\mathcal{P}(X_{1}+\dots+X_{30}\geq 14.5)$

- $E[X_{1}]=\frac{1}{3}+2\cdot \frac{1}{6}=\frac{2}{3}$
- $E[X_{1}^2]=1\cdot \frac{1}{3} + 4\cdot \frac{1}{6}=1$
- $Var(X_{1})= 1-\frac{4}{9}= \frac{5}{9}$

$$
\zeta=X_{1}+\dots+X_{30}\sim N\left( 20,30\cdot \frac{5}{9} \right)
$$
$\mathcal{P}(\zeta\geq 14.5) = \mathcal{P}\left( \zeta_{0}> \displaystyle{\frac{14.5-20}{\sqrt{ \frac{50}{3} }}} \right)=\Phi(1.35)=0.9115$

>[!hint] Osservazione
>$\mathcal{P}(X_{1}+\dots+X_{30}=15)=\mathcal{P}(14.5<\zeta<15.5)$

#### Eserczio
>$55$% di voti ad un partito

Scelti 100 votanti a caso

>[!question] Qual è la probabilità che almeno la metà abbia votato quel partito?

$$
X_{i}=\begin{cases}
1 \quad \text{se } i \text{ ha votato il partito} \\
0 \quad \text{altrimenti}
\end{cases}
$$
- $X_{i}\sim B(1,0.55)$

$$
\mathcal{P}(X_{1}+\dots+x_{100}\geq 50)
$$

>[!hint] Osservazione
>$X_{1}+\dots+X_{100}\sim B(100, 0.55)$
>
>Si ***potrebbe*** calcolare come una [[../3 - Variabili Aleatorie#Variabili Binomiali|variabile binomiale]] ma verrebbe un calcolo *inutilmente complesso*

>Approssimiamo con il ***teorema centrale del limite***

$$
X_{1}+\dots+X_{100}\sim N(55,100\cdot 0.55 \cdot0.45)
$$

- $\mathcal{P}(X_{1}+\dots+x_{100}\geq 50)=\mathcal{P}(\zeta>49)$

#### Esercizio
>Vogliamo organizzare una gita
>- Abbiamo 24 posti disponibili
>- Ogni persona che compra il biglietto non si presenta con probabilità del $30$%

>[!question] Quanti biglietti possiamo vendere accettando un rischio del $10$% che qualcuno si presenti e non trovi posto?

$n=\#$ biglietti venduti

Siano $X_{1},\dots,X_{n}$ tali che:
- $X_{i}\sim B(1,0.7)$
	- $1$ se la persona si *presenta*
	- $0$ se la persona ***non*** si *presenta*

$$
X_{1}+\dots+X_{n}\sim N(n\cdot 0.7,n\cdot 0.7\cdot 0.3)
$$

$\mathcal{P}(S_{n}>24)\leq0.1$
- $\mathcal{P}\left( \zeta_{0}> \displaystyle{\frac{24.5-n\cdot 0.7}{\sqrt{ n\cdot 0.7\cdot 0.3 }}} \right)\leq 0.1$

![[attachements/EsercizioVacanze.png]]

$$
\begin{array}
\ \displaystyle{\frac{24.5-n\cdot 0.7}{\sqrt{ n \cdot 0.7\cdot 0.3 }}}\geq 1.28 \\
n\leq 30
\end{array}

$$