## Interezione di Sottospazi Vettoriali
---
>[!info] Proprietà
>Siano $U,W$ [[2 - Campi e Spazi Vettoriali#Sottospazio Vettoriale|sottospazi vettoriali]] allora $U\cap W$ è un sottospazio vettoriale
>>[!done] In breve
>>L'intersezione di un sottospazio vettoriale è un sottospazio vettoriale

### Dimostrazione
>Siano $u_{1},u_{2}\in U\cap W$

- $u_{1},u_{2}\in U$, e dato che $U$ è un sottospazio vettoriale $\implies u_{1}+u_{2}\in U$
- $u_{1},u_{2}\in W$, e dato che $W$ è un sottospazio vettoriale $\implies u_{1}+u_{2}\in W$

Nello stesso modo si mostra che
$$
\forall a \in\mathbb{K}, u\in U\cap W \implies au \in U\cap W
$$

#### Osservazione
L'unione di sottospazi vettoriali in generale non è un sottospazio vettoriale
##### Esempio
>[!tip]  Siano $U$ e $W$ sottospazi vettoriali di $V = \mathbb{R}^2$

$U=\{ (x,y)\in\mathbb{R}^2:y=0 \}$
$W=\{ (x,y)\in\mathbb{R}^2:x=0 \}$

- $U$ e $W$ sono gli assi del piano cartesiano
Basta prendere $u_{1}=(1,0)\in U$ e $w_{1}=(0,1)$
- Notiamo subito che $u_{1}+w_{1} \notin U \cup W$
![[attachements/Unione di Sottospazi.png]]
## Sottospazio Somma
---
>[!info] Definizione
>Dati due [[2 - Campi e Spazi Vettoriali#Sottospazio Vettoriale|sottospazi vettoriali]] $U,W$ di $V$
>Definisco il **sottospazio somma** come:
>$$U+W = \{ u+w,u\in U , w \in W \}$$

$U+W$ è un sottospazio vettoriale poiché:
>*Siano*
$$u_{1}+w_{1},u_{2}+w_{2}\in U+W
\begin{pmatrix}
u_{1},u_{2}\in U \\
w_{1},w_{2} \in W
\end{pmatrix}$$

<u>Allora</u>:
- $(u_{1}+w_{1})+(u_{2}+w_{2}) = \underbrace{ (u_{1}+u_{2}) }_{ \in U }+\underbrace{ (w_{1}+w_{2}) }_{ \in W } \in U+W$
- Ragionamento analogo per il prodotto per uno scalare

###  Esempio 1
>[!tip] Considero $\underbrace{ V=\mathbb{R}^4 }_{ \text{ dim} = 4 }$

$U=\{ (x_{1},x_{2},x_{3},x_{4})\in \mathbb{R}^4: x_{3}=0 \wedge x_{4}=0 \} \text{ dim} = 2$
$W=\{ (x_{1},x_{2},x_{3},x_{4})\in \mathbb{R}^4: x_{1}=0 \wedge x_{4}=0 \} \text{ dim} = 2$

Trasformo in forma parametrica
$U=\{ (a,b,0,0), a,b\in \mathbb{R} \}$
$W =\{( 0,t,s,0 ), t,s\in\mathbb{R}\}$

$$
\begin{array}
\ U+W=\{ u+w, u\in W,w\in W \}=\{ (a,b+t,s,0),a,b+t,s\in\mathbb{R} \}= \\
=\{ (x_{1},x_{2},x_{3}x_{4})\in\mathbb{R}^4:x_{4}=0 \} \text{ dim} =3
\end{array}
$$
#### Osservazione
$$
U\cap W=\begin{cases}
x_{3}=0 \\
x_{4}=0 \\
x_{1}=0
\end{cases} = \{ (0,t,0,0),t\in\mathbb{R} \}
$$
Ha come dimensione $\text{dim} (U\cap W)=1$

## Formula di Grassman
---
>[!as] Formula
>Siano $U$ e $W$ [[2 - Campi e Spazi Vettoriali#Sottospazio Vettoriale|sottospazi vettoriali]] di $V$
><u>Allora</u>
>$$\text{dim}(U+W)=\text{dim}(U)+\text{dim}(W)-\text{dim}(U\cap W)$$

- Nell'esempio precedente:
	- $3  = 2+2-1$
### Dimostrazione
>[!tip] Supponiamo che:

>*Dimostrazione Sensata*

- $B_{U}=\{ v_{1},\dots,v_{r} \}$ sia una base di $U$ $\implies \text{dim}(U) = r$
- $B_{W}=\{ v_{1},\dots,v_{s} \}$ sia una base di $W$ $\implies \text{dim}(W) = s$
- $U\cap W=\{ v_{1},\dots,v_{i} \}$ sia una base di $U\cap W$ $\implies \text{dim}(U\cap W) = i$

Possiamo ora **completare** la base di $U\cap W$ a base sia di $U$ che di $W$
- Nel caso di $U$ sarà necessario **aggiungere** $r-i$ vettori
- Nel caso di $W$ sarà necessario **aggiungere** $s-i$ vettori

Consideriamo ora gli insiemi:
- $\{ v_{1},\dots,v_{i},u_{i+1},\dots,u_{r} \}$  base di $U$
- $\{ v_{1},\dots,v_{i},w_{i+1},\dots,w_{s} \}$  base di $W$

Ora prendiamo l'unione di questi insiemi:
$$
B=\{ \underbrace{ \overbrace{ v_{1},\dots,v_{i} }^{\text{Base di } U\cap W  },u_{i+1},\dots,u_{r} }_{ \text{Base di } U },w_{i+1},\dots,w_{s} \}
$$
>[!done] Ora basta dimostrare che $B$ è base di $U+W$

>[!question] Perchè?

Perchè se $B$ è base di $U+W$ allora:
$$
\ \text{dim}(U+W) = \text{dim}(B)=r+s-i
$$
E otterremo che:
$$
\begin{array}
\ \underbrace{  \text{dim}(U) }_{ r }+\underbrace{ \text{dim}(W) }_{ s } = \underbrace{ \text{dim}(U+W) }_{ r+s-i } +\underbrace{ \text{dim}(U\cap W) }_{ i } \\
r+s=r+s\cancel{ -i }\cancel{ +i }
\end{array}
$$

>*Dimostrazione Moci*

Sia $v_{1},\dots,v_{l}$ una base di $U \cap W$
Completiamola a una base di $U$
$$
v_{1},\dots,v_{l},u_{1},\dots,u_{m}
$$
E anche ad una base di $W$
$$
v_{1},\dots,v_{l},w_{1},\dots,w_{n}
$$
Allora:
$$
v_{1},\dots,v_{l},u_{1},\dots,u_{m},w_{1},\dots,w_{n}
$$
 >[!done] Generano $U+W$
 
 E si può verificare che sono [[2 - Campi e Spazi Vettoriali#Dipendenza Lineare|linearmente indeipendenti]] e dunque sono una base
Perciò
- $\text{dim}(U+W)=l+m+n$
- $\text{dim}(U)=l+m$
- $\text{dim}(W)=l+n$
- $\text{dim}(U\cap W)=l$

#### Esempio
Nell'[[#Esempio 1]] una base di $U\cap W$ $\{ e_{2} \}$
- Lo completo ad una base $\{ e_{2},e_{3} \}$ di $W$
- Lo completo ad una base di $\{ e_{1},e_{2} \}$ di $U$

Ottengo così una base:
$$
(e_{1},e_{2},e_{3}) \text{ di }U+W
$$

#### Osservazione
>[!tip] $(2,4,1,0)\in U+W$

$$
\begin{array}
\ \underbrace{ (2,3,0,0) }_{ \in U }+\underbrace{ (0,1,1,0) }_{ \in W } \\
\underbrace{ (2,1,0,0) }_{ \in U }+\underbrace{ (0,3,1,0) }_{ \in W }
\end{array}
$$
- Questa decomposizione non è unica

## Somma Diretta
---
>[!info] Definizione 
>Diciamo che $U,W$ formano una **somma diretta** se $U\cap W=\{ \underline{0} \}$
>In questo caso, $U+W$ è indicato con il simbolo
>$$U\oplus W$$

### Proprietà
>[!tip] $U,W$ Formano somma diretta
>Se e solo Se
>$$\forall v\in U+W$$
>Si scrive in modo unico come somma di un elemento di $U$ e di un elemento di $W$

#### Dimostrazione
Supponiamo che
- $\exists u_{1},u_{2}\in U$
- $\exists w_{1},w_{2}\in W$
Tali che si scriva
$$
v=u_{1}+w_{1} = u_{2}+w_{2}
$$
Allora:
$$
v=\underbrace{ u_{1}-u_{2} }_{ \in U }=\underbrace{ w_{1}-w_{2} }_{ \in W } \in W\cap W
$$
Quindi se $U\cap W=\{ \underline{0} \}$ allora:
- $u_{1}=u_{2},w_{1}=w_{2}$ e la decomposizione è unica
- Altrimenti posso ottenere decomposizioni diverse sommando e sottraendo elementi di $U\cap W$
