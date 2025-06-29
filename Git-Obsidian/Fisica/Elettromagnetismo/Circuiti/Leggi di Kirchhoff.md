## Prima Legge di Kirchhoff
---
>[!cite] $I$
>La *somma algebrica* delle **correnti entranti** in un nodo è ***zero***.

## Seconda Legge di Kirchhoff
---
>[!cite] $II$
>La *somma algebrica* delle differenze di potenziale **lungo una maglia chiusa** è ***zero***.

## Esempio
---
> Siano $R=1100\Omega$, calcolare $I_{1},I_{2}$ ,correnti Entranti in $a$, e $I_{3}$ corrente uscente da $a$.

![[Esempio.svg]]

>[!abstract] Semplifico il parallelo tra le resistenze $2R$

Le due resistenze in parallelo $2R$ equivalgono ad una resistenza $R$:
$$
\frac{2R\cdot2R}{2R+2R}=R
$$

>[!summary] Ora metto a sistema

- Nodo $a:I_{1}+I_{2}=I_{3}$
- Maglia Sinistra: $(9V)-RI_{1}-RI_{3}=0$
- Maglia Destra: $(5V)-RI_{3}-RI_{2}=0$

> Ricavo:

$$
I_{1}=\frac{13V}{3R}\simeq 3.9mA\quad
I_{2}=\frac{1V}{3R}\simeq 0.3mA\quad
I_{3}=I_{1}+I_{2}\simeq 4.2 mA
$$