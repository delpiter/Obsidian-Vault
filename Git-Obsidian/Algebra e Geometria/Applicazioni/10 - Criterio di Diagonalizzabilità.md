## Criterio di Diagonalizzabilità
---
>[!Teorema]
>Sia $f$ un [[4 - Isomorfismo#Endomorfismo|endomorfismo]] di $V$ e siano $\lambda_{1},\dots,\lambda_{t}$ i suoi [[9 - Matrici Diagonali#Autovettore e Autovalore|autovalori]] ***distinti***
><u>Allora</u>
>$f$ si diagonalizza $\iff$ valgono ***entrambe queste condizioni***
>1. $\lambda_{i}\in\mathbb{K}, \forall i=1,\dots,t$, Tutti gli ***autovalori*** sono nel [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Campo|campo]]
>2. $ma(\lambda_{i})=mg(\lambda_{i}), \forall i=1,\dots,t$ La [[9 - Matrici Diagonali#Molteplicità|molteplicità algebrica e geometrica]] di tutti gli ***autovalori coincidono***

### Dimostrazione
>*Supponiamo che valga la condizione 1)*

Cioè $\lambda_{1},\dots,\lambda_{t}\in\mathbb{K}$ e consideriamo gli ***autospazi***
$$
V\lambda_{1},\dots,V\lambda_{t}
$$
Sia $U=V\lambda_{1}\oplus\dots\oplus V\lambda_{t}$
- $U$ è una [[../Basi dell'algebra/5 - Intersezione e Somma di Sottospazi#Somma Diretta|somma diretta]], perché, come abbiamo mostrato [[9 - Matrici Diagonali#Autospazio|prima]]:
	- $V\lambda_{i}\cap V\lambda_{j}=\{ \underline{0} \} \text{ per }\lambda_{i}\neq \lambda_{j}$

Sia $\mathcal{B}1$ una base di $V\lambda_{1},\dots,\mathcal{B_{t}}$ una base di $V\lambda_{t}$ 
- Quindi, poiché $U$ è una ***somma diretta***
$$
\mathcal{B}=\mathcal{B}_{1}\cup\mathcal{B}_{2}\cup\dots\cup\mathcal{B}_{t}
$$
- È una base di $U$

Quindi $\text{dim}(U)=\text{dim}(V\lambda_{1})+\dots+\text{dim}(V\lambda_{t})=mg(\lambda_{1})+\dots+mg(\lambda_{t})$

D'altra parte, $\text{dim}(V)=$ grado di $p(\lambda)=ma(\lambda_{1})+\dots+ma(\lambda_{t})$

>*Se vale la condizione 2) allora:*

$$
\text{dim}(U)=\text{dim}(V)
$$
- Ovvero: $U=V$ ovvero $\mathcal{B}$ è una base di $V$ composta da ***autovettori***

>[!done] Quindi in tale base la matrice di $f$ è *diagonale*

>*Se non vale la condizione 2)*

$$
\text{dim}(U)=mg(\lambda_{1})+\dots+mg(\lambda_{t})<ma(\lambda_{1})+\dots+ma(\lambda_{t})=\text{dim}(V)
$$

Quindi $\mathcal{B}$ non è una base di $V$
- Posso completare $\mathcal{B}$ ad una *base* di $V$, ma i vettori che aggiungo **non** sono ***autovettori***

>[!fail] La matrice di $f$ non è diagonale

>[!tldr] Osservazione
>Se valgono 1) e 2), la dimostrazione ci fornisce un algoritmo esplicito per trovare la base di autovettori di $V$
>Basta unire le basi degli ***autospazi***

#### Esempio
>*Consideriamo* $\mathbb{K}=\mathbb{R}, V=\mathbb{R}^3, f:V\to V$

$$
f(x,y,z)=(x-3y+3z,3x-5y+3z,6x-6y+4z)
$$
>[!question] Trovare, se possibile, una base la cui matrice di $f$ è *diagonale*

Nella ***base canonica***, la matrice di $f$:
$$
A=\begin{pmatrix}
1 & -3 & 3 \\
3 & -5 & 3 \\
6 & -6 & 4
\end{pmatrix}
$$
- Quindi

$$
p(\lambda)=\det\begin{pmatrix}
1-\lambda & -3 & 3 \\
3 & -5-\lambda & 3 \\
6 & -6 & 4-\lambda
\end{pmatrix}=(\lambda+2)(-\lambda^2+2\lambda+8)
$$
- $\underset{ ma(\lambda_{1})=2 }{ \lambda_{1}=-2 }$ e $\underset{ ma(\lambda_{1})=1 }{ \lambda_{2}=4 }$

>[!abstract] $V\lambda_{1}=\{ (x,y,z)\in\mathbb{R}^3:f(x,y,z)=-2(x,y,z) \}$

$$
\begin{cases}
x-3y+3z=-2x \\
3x-5y+3z=-2y \\
6x-6y+4z=-2z
\end{cases} \iff\begin{cases}
x+z=y
\end{cases}\implies mg(\lambda_{1})=2
$$

- $\mathcal{B}_{1}=\{ v_{1}=(1,1,0),v_{2}=(0,1,1) \}=\{ (t,t+s,s),t,s\in \mathbb{R}\}$ base di $V\lambda_{1}$

>[!abstract] $V\lambda_{2}=\{ (x,y,z)\in\mathbb{R}^3:f(x,y,z)=4(x,y,z) \}$

$$
\begin{cases}
x-3y+3z=4x \\
3x-5y+3z=4y \\
6x-6y+4z=4z
\end{cases} \iff\begin{cases}
2x=z \\
x=y
\end{cases}\implies mg(\lambda_{2})=1
$$

- $\mathcal{B}_{2}=\{ v_{3}=(1,1,2) \}=\{ (t,t,2t),t\in \mathbb{R}\}$ base di $V\lambda_{1}$

>[!done] $mg$ e $ma$ coincidono e quindi $f$ è diagonalizzabile

Per il teorema precedente, poiché gli autovalori $\in\mathbb{K}$ e $ma=mg$, $f$ si diagonalizza
- Una base di autovettori è $\mathcal{B}=\mathcal{B}_{1}\cup\mathcal{B}_{2}$

- $f(v_{1})=-2v_{1}$
- $f(v_{2})=-2v_{2}$
- $f(v_{3})=4v_{3}$

$$
D=\begin{pmatrix}
-2 & 0 & 0 \\
0 & -2 & 0 \\
0 & 0 & 4
\end{pmatrix}
$$