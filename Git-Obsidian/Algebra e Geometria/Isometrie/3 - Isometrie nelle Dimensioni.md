>[!question] Che cosa possiamo dire nei casi $\text{dim}=1,2,3$?

## $\text{dim}(V)=1$
>*Sia $f:\mathbb{R}\to\mathbb{R}$*

$f(v)=av$

Se $f$ è ***isometria***:
- $(v,v)=(av,av)=a^2(v,v)$

Quindi $a=\pm 1\implies$ ci sono solamente due isometrie:
- $id$ e $-id$

## $\text{dim}(V)=2$
>*Sia* $f:\mathbb{R}^2\to\mathbb{R}^2$

Fissiamo una *[[../Frome Bilineari e Prodotti Scalari/4 - Prodotto Scalare#Base Ortonormale|BON]]* di $V$

Poiché $f$ è una *isometria*, la matrice di $f$
$$
A=\begin{pmatrix}
a & b \\
c & d
\end{pmatrix}
$$ 
- È una [[1 - Introduzione Isometrie#Matrice Ortogonale|matrice ortogonale]]

$$
\begin{pmatrix}
a & b \\
c & d
\end{pmatrix}\cdot\begin{pmatrix}
a & c \\
b & d
\end{pmatrix}
=\begin{pmatrix}
1 & 0 \\
0 & 1
\end{pmatrix}$$
$$
\begin{cases}
a^2+b^2=1 \\
ac+bd = 0 \\
c^2+d^2=1
\end{cases}
$$

>[!abstract] Osservazione
>Per ogni coppia  $a,b\in\mathbb{R}:a^2+b^2=1$
>Esiste $t\in[0,2\pi]:a=\cos(t),b=\sin(t)$

Analogamente posso scrivere:
- $c=\sin(s),\quad d=\cos(s)$

Le nostre equazioni diventano:
$$
\begin{cases}
\cancel{ \cos^2(t)+\sin^2(t)=1 } \\
\cancel{ \cos^2(s)+\sin^2(s)=1 } \\
\cos(t)\sin(s)+\sin(t)\cos(s)=0
\end{cases}\implies \sin(t+s)=0
$$

>[!tldr] $\sin(t+s)=0\iff t+s=0$ oppure $t+s=\pi$

Quindi
- $s=-t$
- $s=\pi-t$

### Casi
>*Se $s=-t$*

$$
A=\begin{pmatrix}
a & b \\
c & d
\end{pmatrix}
=\begin{pmatrix}
\cos(t) & \sin(t) \\
-\sin(t) &  \cos(t)
\end{pmatrix}=S_{t}$$

>*Se $s=\pi-t$*

$$
A=\begin{pmatrix}
a & b \\
c & d
\end{pmatrix}
=\begin{pmatrix}
\cos(t) & \sin(t) \\
\sin(t) &  -\cos(t)
\end{pmatrix}=R_{t}$$

>[!done] Abbiamo mostrato che ogni matrice ortogonale $2\times 2$ è del tipo $S_{t}$ o $R_{t}$
>Per qualche $t\in[0,2\pi]$


>[!abstract] Osservazione
>Osserviamo che
>- $\det(R_{t})=\cos^2(t)+\sin^2(t)=1$
>- $\det(S_{t})=-(\cos^2(t)+\sin^2(t))=-1$

### Significato Geometrico
>[!question] Che significato geometrico hanno queste matrici?

#### $R_{t}$

$$
R_{t}(e_{1})=\begin{pmatrix}
\cos(t) & \sin(t) \\
-\sin(t) & \cos(t)
\end{pmatrix}\begin{pmatrix}
1 \\
0
\end{pmatrix}
=\begin{pmatrix}
\cos(t) \\
-\sin(t)
\end{pmatrix}$$

$$
R_{t}(e_{2})=\begin{pmatrix}
\cos(t) & \sin(t) \\
-\sin(t) & \cos(t)
\end{pmatrix}\begin{pmatrix}
0 \\
1
\end{pmatrix}
=\begin{pmatrix}
\sin(t) \\
\cos(t)
\end{pmatrix}$$

>[!done] $R_{t}$ è la rotazione di centro l'origine e di angolo $-t$

#### $S_{t}$

>[!abstract] Proviamo a diagonalizzarla

$$
S_{t}=\begin{pmatrix}
\cos(t) & \sin(t) \\
\sin(t) & -\cos(t)
\end{pmatrix}
$$

$$
p(\lambda)=\det\begin{pmatrix}
\cos(t)-\lambda & \sin(t) \\
\sin(t) & -\cos(t)-\lambda
\end{pmatrix}=-\cos^2(t)+\lambda^2-\sin^2(t)=\lambda^2-(\sin^2(t)+\cos^2(t))
$$
- $p(\lambda)=\lambda^2-1\implies \lambda_{1}=1 \quad \lambda_{2}=-1$

- $m_{a}(\lambda_{1})=1\quad m_{a}(\lambda_{2})=1$

Quindi se si diagonalizzerebbe
- Esistono $v_{1},v_{2}\in\mathbb{R}^2:S_{t}(v_{1})=v_{1},\quad S_{t}(v_{2})=-v_{2}$

>[!done] Quindi $S_{t}$ è la simmetria rispetto alla retta generata da $v_{1}$

### Conclusione
>[!Teorema]
>Abbiamo dimostrato che le *uniche* ***isometrie*** di ***un piano reale*** sono:
>- Le ***rotazioni*** di centro all'origine e angolo $t$: $R_{t}$
>- Le ***simmetrie*** rispetto a una retta passante per l'origine: $S_{t}$

