>[[3 - Variabili Aleatorie#Variabili Discrete e Densità Uniforme|Variabile Uniforme]]
---

>[!definizione] Concetto
>$$U\sim([a,b])$$
>La *variabile* ha [[8 - Variabili Aleatorie Continue#Densità Continua|densità]] ***costante*** in $[a,b]$ e ***nulla*** fuori

$$
f_{X}(s)=\begin{cases}
0\qquad\ \text{se } s<a \vee s>b \\
\frac{1}{b-a}\quad \text{se } a<s<b
\end{cases}
$$

![[Var Continua Uniforme.png]]
#### Esempio
>Un tram passa ogni $10$ minuti

Andiamo in fermata in un ***istante qualunque***

- $X=$ tempo di attesa

$$
\begin{array}
\ \mathcal{P}(0<X< 1)=\displaystyle\frac{1}{10} \\
\mathcal{P}(1<X< 2)=\displaystyle\frac{1}{10} \\
\vdots \\
\mathcal{P}(9<X< 10)=\displaystyle\frac{1}{10}
\end{array}
$$

![[Densità Uniforme Esempio.png]]

>[!question] $F_{X}(t)$ ?

>Consideriamo $0<t<10$

- $F_{X}(t)=\mathcal{P}(X\leq t)=(t-0)\cdot \frac{1}{10}$

>[!hint] Caso Generale
>>$a<t<b$
>
>$$\mathcal{P}(X\leq t)= \displaystyle{\frac{(t-a)}{(b-a)}}$$

![[VariabileUniforme-CasoGenerale.png]]

### Valore Atteso
>[!info] Valore Atteso di Variabili Uniformi
>$$E[X]=\int_{a}^b s\cdot \frac{1}{b-a} \, ds $$

$$
\frac{1}{b-a}\cdot\left[ \frac{s^2}{2} \right]_{a}^b=\frac{1}{b-a}\left( \frac{b^2}{2}-\frac{a^2}{2} \right)=\frac{1}{\cancel{ b-a }}\cdot \displaystyle{\frac{\cancel{ (b-a) }(b+a)}{2}}=\displaystyle{\frac{b+a}{2}}
$$
### Varianza
>[!abstract] Varianza di Variabili Uniformi
>$$Var(X)=E[X^2]-E[X]^2$$

$$
E[X^2]=\int_{a}^bs^2 \frac{1}{b-a} \, ds=\frac{1}{b-a}\cdot \frac{1}{3}[s^3]_{a}^b=\frac{1}{3(b-a)}\cdot(b^3-a^3)=
$$
$$
=\frac{1}{3\cancel{ (b-a) }}\cdot\cancel{ (b-a) }(b^2+ab+a^2)
$$


Ora calcoliamo la ***varianza***:
$$
Var(X)=\frac{(b^2+ab+a^2)}{3}-\frac{(b+a)^2}{4}=\displaystyle{\frac{4b^2+4ab+4a^2-3a^2-3b^2-6ab}{12}}=
$$
$$
=\displaystyle{\frac{b^2+a^2-2ab}{12}}=\frac{(b-a)^2}{12}
$$
