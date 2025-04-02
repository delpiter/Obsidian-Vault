## Disuguaglianza di Chebyshev
---
>Sia $X$ una ***variabile aleatoria discreta***

>[!info] $\forall\varepsilon>0$
>$$\mathcal{P}(|X-E[X]| >\varepsilon)\leq \displaystyle{\frac{Var(X)}{\varepsilon^2}}$$

##### Esempio
>$X\quad E[X]=2\quad Var(X)=\frac{1}{100}$

Scelgo $\varepsilon=1$

$$
\mathcal{P}(|X-2| >1)\leq \frac{1}{100}
$$
Scelgo $\varepsilon=\frac{1}{2}$

$$
\mathcal{P}\left( |X-2| > \frac{1}{2} \right)\leq \frac{\frac{1}{100}}{\frac{1}{4}}=\frac{4}{100}
$$
### Dimostrazione
>$A=\{ \mid X-E[X]\mid> \varepsilon \}$

$$
\chi_{A}=\begin{cases}
1 \quad \text{se } A \text{ accade} \\
0 \quad \text{se } A \text{ non accade}
\end{cases}
$$
- $\chi_{A}=B(1,\mathcal{P}(A))$

>[!abstract] Ora considero

$Y=\varepsilon^2 \chi_{A}$ e $Z=(X-E[X])^2$

>Confrontiamo $Y$ e $Z$, in particolare, *mostriamo* che $Y\leq Z$

>[!example] Due Casi
>>[!note] $A$ ***non*** accade
>>$Y=\varepsilon^2\cdot 0 = 0$
>>$Z\geq 0$, poiché un qualsiasi valore$^2$ è $\geq 0$
>
>>[!asd] $A$ ***accade***
>>$Y=\varepsilon^2$
>>$Z\geq \varepsilon^2$

>Deduciamo quindi, che:

$$
E[Y]\leq E[Z]
$$
$$
\varepsilon^2\cdot\mathcal{P}(A)\leq Var(X)
$$

### Esempio
>Lanciamo una moneta "***tante volte***"

- $n=\#$ ***lanci della moneta***

$$
X\sim B\left( n, \frac{1}{2} \right)
$$
- $X=\#$ teste su $n$ *lanci*

>[!question] Cosa possiamo dire sulla quantità: $\frac{X}{n}$ ?

>[!attention] Ad intuito
>$$\begin{array}\ n\to \infty \\\displaystyle\frac{X}{n}\to \frac{1}{2}\end{array}$$
>Ci aspettiamo che per $n$ *grandi* si avvicini ad $\frac{1}{2}$


>Fissiamo $0.51$ (un po' più di $\frac{1}{2}$)

>[!question] Con $n=10$, $\mathcal{P}\left( \displaystyle\frac{x}{10}>0.51 \right)$ ?

>[!question] Con $n=100$, $\mathcal{P}\left( \displaystyle\frac{x}{10}>0.51 \right)$ ?

>[!question] Con $n=1000$, $\mathcal{P}\left( \displaystyle\frac{x}{10}>0.51 \right)$ ?

- $\dots$

>[!note] Ci aspettiamo che questa probabilità tenda a $0$

>[!definizione] Definizione
>Sia $Y_{1},Y_{2},Y_{3},\dots$ una *successione* di ***variabili aleatorie***.
>Diciamo che questa successione tende ad una costante $a$ se:
>$\forall \varepsilon > 0$
>***Vale***
>$$\mathcal{P}(\mid Y_{n}-a\mid >\varepsilon)\underset{n \mapsto \infty}{ \longrightarrow } 0$$

## Legge dei Grandi Numeri
---
>[!definizione] Definizione
>Siano $X_{1},X_{2},X_{3},\dots$ [[3 - Variabili Aleatorie|variabili aleatorie]] *indipendenti* che abbiano tutte la ***stessa densità*** con [[6 - Valore Atteso|valore atteso]] $\mu$ e [[3 - Varianza|varianza]] $\sigma^2$
><u>Allora</u>
>La *successione*
>$$Y_{1} = X_{1}\qquad Y_{2}= \displaystyle{\frac{X_{1}+X_{2}}{2}}\qquad Y_{3}= \displaystyle{\frac{X_{1}+X_{2}+X_{3}}{3}}$$
>Converge a $\mu$


##### Dimostrazione
>$Y_{n}= \frac{1}{n}(X_{1}+\dots+X_{n})$

$$
\begin{array}
\ E[Y_{n}]= \displaystyle{\frac{1}{n}}(\underbrace{ E[X_{1}]+\dots+E[X_{n}] }_{ \displaystyle n\cdot\mu })= \\
=\displaystyle\frac{1}{\cancel{ n }}\cdot \cancel{ n }\cdot \mu
\end{array}
$$
$$
\begin{array}
\ Var(Y_{n})=Var\left( \displaystyle \frac{1}{n}(X_{1}+\dots+X_{n}) \right)=\\
=\displaystyle \frac{1}{n^2}\cdot n\cdot \sigma^2
\end{array}
$$

>[!caution] Applichiamo ora la ***disuguaglianza di Chebyshev*** a $Y_{n}$

$$
\mathcal{P}(\mid Y_{n}-\mu \mid > \varepsilon)\leq \underbrace{ \displaystyle{\frac{\sigma^2}{n \varepsilon^2}} }_{ \displaystyle \underset{ n \mapsto \infty }{ \longrightarrow 0 }}
$$

