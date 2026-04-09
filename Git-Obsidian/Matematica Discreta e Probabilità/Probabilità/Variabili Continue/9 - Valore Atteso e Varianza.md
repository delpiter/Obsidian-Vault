>***Valore Atteso e Varianza di Variabili aleatorie Continue***

## Formule
---
>[[../6 - Valore Atteso|!Valore Atteso]]
>$$E[X]=\int_{-\infty}^\infty sf_{X}(s) \, ds $$

>[[../7 - La Varianza|!Varianza]]
>$$Var(X)=E[(X-E[X])^2]$$

### Proprietà
>[!hint] Osservazione 
>Annotiamo che le proprietà di ***valore atteso*** e ***varianza*** che conosciamo *continuano a valere*

- $E[X+Y]=E[X]+E[Y]$
- $E[cX]=cE[X]$
- $E[XY]=E[X]\cdot E[Y]\quad$ se $X$ e $Y$ sono *indipendenti*
- $Var(X)=E[X^2]-E[X]^2$
- $Var(cX)=c^2Var(X)$
- $Var(X+Y)=Var(X)+Var(Y)\quad$ se $X$ e $Y$ sono *indipendenti*
- $Z-\Phi(X)\quad E[Z]-\displaystyle\int_{-\infty}^{\infty}\Phi(s)f_{X}(s)  \, ds$

##### Esercizio
>Riprendendo la [[8 - Variabili Aleatorie Continue#Densità Continua|Densità Continua]] dal [[8 - Variabili Aleatorie Continue#Esercizio|precedente esercizio]]

>[!question] Calcolare il ***Valore Atteso***

$$
E[X]=\int_{-\infty}^\infty sf(s) \, ds=\int_{0}^1 s\cdot s^2\, ds+\int_{1}^2 s \frac{2}{3} \, ds = \left[ \frac{s^4}{4} \right]_{0}^1+\left[ \frac{s^2}{3} \right]_{1}^2=\frac{1}{4}+\frac{4}{3}-\frac{1}{3}=\frac{5}{4}
$$

