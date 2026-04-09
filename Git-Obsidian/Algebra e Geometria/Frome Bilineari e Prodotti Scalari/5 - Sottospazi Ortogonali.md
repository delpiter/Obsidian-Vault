## Sottospazio Ortogonale
---
>[!info] Definizione
>Sia $V$ uno [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Spazio Vettoriale|spazio vettoriale]] su $\mathbb{R}$, sia $U$ un suo [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Sottospazio Vettoriale|sottospazio vettoriale]] e consideriamo un prodotto scalare su $V$
>Definiamo un ***sottospazio ortogonale*** come:
>$$U^{\perp} =\{ v\in V:(v,u)=0 \quad\forall u\in U \}$$

>[!tldr] Osservazione
>Osserviamo che $U^{\perp}$ è un sottospazio vettoriale di $V$ se $v_{1},v_{2}\in U^{\perp}\implies (v_{1},u)=0,(v_{2},u)=0\quad \forall u\in U\implies v_{1}+v_{2}\in U^{\perp}$
>>[!caution] Analogamente
>>Se $a\in\mathbb{R}, \quad v_{1}\in U^{\perp}\implies av_{1}\in U^{\perp}$

>[!abstract] Osservazione
>Osserviamo anche che $U\cap U^{\perp}=\{ \underline{0} \}$
>Infatti se $u\in U, u\in U^{\perp}$ allora $(u,u)=0\implies u=\underline{0}$

### Sottospazio Ortogonale in Somma Diretta
>*Se* $u_{1},\dots,u_{k}$ *è una base* di $U$

- $v\in U^{\perp} \iff (v,u_{1})=0,\dots,(v,u_{k})=0$
Infatti se $u\in U, u=a_{1}u_{1}+\dots+a_{k}u_{k}$
- $(v,u)=a_{1}(v,u_{1})+\dots+a_{k}(v,u_{k})=0+\dots+0 =0$

>[!done] Quindi se $\text{ dim}(U)=k$ e $\text{dim}(V)=n$
>$U^{\perp}$ è descritto da $k$ equazioni cartesiane e quindi $\text{dim}(U^\perp)=n-k$
>E pertanto
>>[!abstract] ‎ 
>>$$V=U\oplus U^\perp$$

#### Esempio
>$V=\mathbb{R}^5\quad U=\{ (x_{1},x_{2},x_{3},x_{4},x_{5})\in V:\begin{cases}x_{1}-2x_{2}=0 \\x_{3}=0 \\x_{4}=x_{2}+x_{5}\end{cases} \}$

- $U=\{ (2t,t,0,t+s,s),t,s\in\mathbb{R} \}$

Una base di $U$ è $u_{1}=(2,1,0,1,0) \quad u_{2}=(0,0,0,1,1)$

Rispetto al [[4 - Prodotto Scalare#Prodotto Scalare Standard|prodotto scalare standard]]:
$U^\perp=\{ v\in V:(v,u)=0 \quad\forall u\in U \}=\{ v\in V:(v,u_{1})=0,(v,u_{2})=0 \}$

$$
\begin{cases}
2x_{1}+x_{2}+0x_{3}+x_{4}=0 \\
0x_{1}+0x_{2}+0x_{3}+x_{4}+x_{5}=0
\end{cases}
$$

### Altri Sottospazi
>[!info] Definizione
>Definiamo [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Sottospazio Affine|sottospazio affine]] ***perpendicolare*** a $U$ passante per $p$ il ***sottospazio affine parallelo*** a $U^\perp$ e passante per $p$


#### Esempio
>*Trovare in $V=\mathbb{R}^2$ la retta perpendicolare a $U=\{ (x,y)\in\mathbb{R}^2:x+2y=0 \}$ e passante per $P=(2,3)$* 


>[!abstract] Rispetto al Prodotto Scalare Standard

$U=<u_{1}=(2,-1)> \implies U^\perp =\{ \underbrace{ (x,y) }_{ v }\in v :(v,u_{1})=0\}$
$U^\perp = \{ (x,y)\in V:2x-y=0 \}$

$r$ è Parallela a $U^\perp \quad\{ 2x-y=a, a\in\mathbb{R} \}$
- Passante per $P$: $(2(2)-3)=a \to a=1$