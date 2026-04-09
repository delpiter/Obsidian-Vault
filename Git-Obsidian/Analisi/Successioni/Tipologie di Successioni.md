## Successioni esponenziali
- - -
### $a>1$
$$
\lim\limits_{n\to+\infty}a^n = +\infty
$$
![[attatchements/successioneExp.png]]

#### Dimostrazione
Voglio dimostrare che $\lim\limits_{n\to+\infty}a^n=+\infty, \ \ \ a>1$
- Utilizzo la disugualianza di bernoulli
	- Poichè $a$ è maggiore di $1$ lo posso scrivere come $a=1+h$ con $h>1$
	- $(1+h)^n\geq 1+nh$
		- Conosco già il limite di $1+nh$ e quindi per il teorema del confronto $a^n$ con $a>1$ tende a $+\infty$
### $0<a<1$
$$
\lim\limits_{n\to+\infty}a^n=0
$$
![[attatchements/successioneExpInv.png]]

#### Dimostrazione


### $-1<a<0$
$$
\lim\limits_{n\to+\infty}a^n=0
$$
![[attatchements/Dimostrazione Successione.png]]

#### Dimostrazione
Voglio dimostrare che $\lim\limits_{n\to+\infty}a^n=0, \ \ \ -1<a<0$
- $|a^n|=|a|^n$
	- Sappiamo già che $|a|^n, 0<a<1$ tende a $0$
	- Quindi anche $|a^n|$ deve tendere a $0$
### $a<-1$
$$
\nexists\lim\limits_{n\to+\infty}
$$
- poichè il valore di $a^n$ con $a<-1$ oscilla costantemente fra $\pm\infty$
- L'insieme dei termini è
$$
\{|a|^{2n}|n\in\mathbb{N}\}\cup\{-|a|^{2n+1}|n\in\mathbb{N}\}
$$
### Riassumendo
$$
\lim\limits_{n\to+\infty}a^n \begin{cases}
+\infty\text{ se }a>1 \\
0 \text{ se }0<a<1 \\
1 \text{ se } a=1 \\
\nexists \text{ se } a\leq-1
\end{cases}
$$
## Ordini di Grandezza
---
>[!tldr] Condizioni
>Siano $p>0$ e $a>1$
>Esistono i seguenti ordini di grandezza:
>$$n^p<a^n<n!<n^n$$

![[../Taylor/Resto di Peano#Successioni Trascurabili]]