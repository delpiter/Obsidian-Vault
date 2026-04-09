*Vogliamo chiarire i legami fra tre concetti*
## Teorema 1
---
>[!inf] Teorema $T_{1}$
>Sia $v_{1},\dots,v_{n}$ un [[../Frome Bilineari e Prodotti Scalari/4 - Prodotto Scalare#Base Ortonormale|BON]] di $V$
><u>Allora</u>
>Una base $w_{1},\dots,w_{n}$ di $V$ è ***ortonormale*** $\iff$ la [[../Frome Bilineari e Prodotti Scalari/1 - Forme Bilineari#Matrici Congruenti|matrice del cambiamento di base]] è [[1 - Introduzione Isometrie#Matrice Ortogonale|Ortogonale]]

^b26be9


### Dimostrazione

Poiché $v_{1},\dots,v_{n}$ è *BON*, cioé:
$$
(v_{i},v_{j})=\begin{cases}
1 \quad \text{ se } i=j \\
0 \quad \text{ se } i\neq j
\end{cases}
$$
La matrice di ***tale prodotto scalare*** in $v_{1},\dots,v_{n}$ è $I_{n}$, la *matrice identità*

Quindi se $\mathcal{B}$ è la matrice del cambiamento di base
- La matrice del ***prodotto scalare in base*** $w_{1},\dots,w_{n}$ è:

$$
B^TI_{n}B=B^TB
$$
>[!done] $w_{1},\dots,w_{n}$ è *BON* $\iff B^TB=I_{n}\iff B$ è **ortogonale**


## Teorema 2
---
>*Stesso concetto del [[../Applicazioni/4 - Isomorfismo#Teorema Isomorfismo-Basi|Teorema Isomorfismo-Basi]]*


>[!inf] Teorema $T_{2}$
>Una applicazione $f:V\to V$ è una [[1 - Introduzione Isometrie#Isometria|Isometria]] $\iff$ manda *[[../Frome Bilineari e Prodotti Scalari/4 - Prodotto Scalare#Base Ortonormale|BON]]* in *BON*

### Dimostrazione
>$\implies$

Sia $f$ una ***isometria*** e $v_{1},\dots,v_{n}$ una *BON*
<u>Allora</u>

$$
(f(v_{i}),f(v_{j}))\underset{ isometria }{ = }(v_{i},v_{j})\underset{ BON }{ = }\begin{cases}
1 \quad \text{ se } i=j \\
0 \quad \text{ se } i\neq j
\end{cases}\implies f(v_{1}),\dots,f(v_{n}) \to\text{ BON}
$$

>$\impliedby$

Sia $f:V\to V$ una ***applicazione lineare***
- Sia $\mathcal{B}_{1}=v_{1},\dots,v_{n}$ una *BON* tale che $\mathcal{B}_{2}=f(v_{1}),\dots,f(v_{n})$ è anche essa una *BON*

>[!abstract] Vogliamo mostrare che $f$ è una *isometria*

- Dati due vettori $v,u\in V$ scriviamoli nella base $\mathcal{B_{1}}$

$\begin{array} \ v=a_{1}v_{1}+\dots+a_{n}v_{n} \\ u=b_{1}v_{1}+\dots+b_{n}v_{n} \end{array}$

$$
f(v)=a_{1}f(v_{1})+\dots+a_{n}f(v_{n})\qquad
f(u)=b_{1}f(v_{1})+\dots+b_{n}f(v_{n})
$$

>Ma abbiamo [[../Frome Bilineari e Prodotti Scalari/4 - Prodotto Scalare#Legame tra Prodotto Scalare e Prodotto Scalare Standard|dimostrato]] che in una ***BON*** il ***prodotto scalare di due vettori*** è uguale al ***prodotto scalare standard*** delle loro coordinate

Quindi:
$$
(v,u)=(a_{1},\dots,a_{n})\begin{pmatrix}
b_{1} \\
\dots \\
b_{n}
\end{pmatrix}=a_{1}b_{1}+\dots+a_{n}b_{n}=(f(v),f(u))
$$

>[!done] Cioè: $\forall v,u \in V$ $f$ è una ***isometria***

## Teorema 3
---
>[!inf] Teorema $T_{3}$
>Una *applicazione lineare* $f:V\to V$ è una [[1 - Introduzione Isometrie#Isometria|isometria]] $\iff$ la sua matrice in una qualsiasi [[../Frome Bilineari e Prodotti Scalari/4 - Prodotto Scalare#Base Ortonormale|BON]] è una matrice [[1 - Introduzione Isometrie#Matrice Ortogonale|ortogonale]]

### Dimostrazione

Sia $v_{1},\dots,v_{n}$ una *BON* e sia $A$ la matrice di $f$ rispetto a tale base:
- $f(v_{1})=a_{11}v_{1}+\dots+a_{n1}v_{n}$
- $\dots$
- $f(v_{n})=a_{1n}v_{1}+\dots+a_{nn}v_{n}$

$$
A=\begin{pmatrix}
a_{11} & \dots & a_{1n} \\
\dots & \dots & \dots \\
a_{n_{1}} & \dots & a_{nn}
\end{pmatrix}
$$

Quindi:
$$
(f(v_{i}),f(v_{j}))=(a_{1i}v_{1}+\dots+a_{ni}v_{n},a_{1j}v_{1}+\dots+a_{nj}v_{n})
$$

>[!caution] Ricorda
>In una *BON*: $\quad(v_{i},v_{j})=\begin{cases} 1 \quad \text{ se } i=j \\ 0 \quad \text{ se } i\neq j \end{cases}$
>Quindi:
>>$a_{ki}a_{bj}(v_{k},v_{b})=0 \qquad k\neq b$

- Che per la ***proprietà della linearità***
$$
=a_{1i}a_{1j}(v_{1},v_{1})+\dots+a_{ni}a_{nj}(v_{n},v_{n})=(AA^T)_{ij}
$$
Dove $(AA^T)_{ij}$ è il prodotto riga per colonna
- ($i$-*esima* colonna di $A$)$\times$($j$-*esima* colonna di $A$)


>[!done] Ricapitolando
>$(f(v_{i}),f(v_{j}))=(A A^T)_{ij}$
>Quindi $f$ è *isometria* $\underbrace{ \iff }_{ T_{2} } f(v_{1}),\dots,f(v_{n})$ è una *BON*$\iff$
>$\iff(f(v_{i}),f(v_{j}))=(v_{i},v_{j})=\begin{cases} 1 \quad \text{ se } i=j \\ 0 \quad \text{ se } i\neq j \end{cases}\iff$
>$\iff(A A^T)_{ij}=(v_{i},v_{j})=\begin{cases} 1 \quad \text{ se } i=j \\ 0 \quad \text{ se } i\neq j \end{cases}\iff A A^T=I_{n}\iff A$ è *ortogonale*


## Osservazioni
---
>[!abstract] Osservazione 1
>Le nozioni di *BON* e ***isometria*** dipendono dal prodotto scalare scelto su $V$

### Determinante di Isometrie
>[!info] Proposizione
>Sia $f$ una [[1 - Introduzione Isometrie#Isometria|isometria]]
><u>Allora</u>
>$\det(f)=\pm 1$

>[!fail] Non Vale l'inverso

#### Dimostrazione
> *Fissiamo una BON di $V$*

In tale base la matrice $A$ di $f$ è ***ortogonale***, cioè $A A^T=I_{n}$

Quindi:
$$
1=\det(I_{n})=\det(A\cdot A^T)=\det(A)\cdot\underbrace{ \det(A^T) }_{ \det(A) }\implies(\det(A))^2=1 \implies \det(A)=\pm1
$$
### Autovalori di Isometrie
>[!info] Proposizione
>Sia $f:V\to V$ una ***isometria*** e $\lambda$ un suo [[../Applicazioni/9 - Matrici Diagonali#Autovettore e Autovalore|autovalore]]
>Se $\lambda\in\mathbb{R}$
><u>Allora</u>
>$\lambda=1$ o $\lambda=-1$

#### Dimostrazione
Se $\lambda$ è un ***autovalore***
- $\exists v\in V,v\neq \underline{0}:f(v)=\lambda v$
E quindi $\mid\mid f(v)\mid\mid=\mid\mid\lambda v\mid\mid=\mid\lambda\mid \cdot\mid\mid v\mid\mid$

Poiché $f$ è *isometria*
- $\mid\mid v\mid\mid=\mid\lambda\mid\cdot\mid\mid v\mid\mid$
 Quindi $\mid\lambda\mid = 1$

>[!abstract] Osservazione
>Può succedere che una ***isometria*** $f:V\to V$ abbia ***autovalori non reali***

##### Esempio
Sia $f:\mathbb{R}^2\to\mathbb{R}^2$
- $f(x,y)=(y,x)$

>[!tldr] Isometria rispetto al prodotto scalare standard

Ha autovalori $i,-i \in \mathbb{C}$