![[5 - Matrici di Applicazioni Lineari#Domanda]]

## Teorema del Cambiamento di Base
>[!info] ‎ 
>Sia $V$ uno [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Spazio Vettoriale|spazio vettoriale]] su un [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Campo|campo]] $\mathbb{K}$ e sia $f:V\to V$ una [[1 - Applicazioni Lineari|applicazione lineare]].
>Siano $\mathcal{B}=\{ v_{1},\dots,v_{n} \}$ e $\mathcal{B}'=\{ u_{1},\dots,u_{n} \}$
>Sia $A$ la matrice di $f$ nella [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Base|base]] $\mathcal{B}$
>Sia $M$ la matrice di $f$ nella base $\mathcal{B}'$
>>[!abstract] In altre parole
>>$$f(v_{j})=a_{1j}v_{1}+\dots+a_{nj}v_{n}$$
>>$$f(u_{j})=m_{1j}u_{1}+\dots+m_{nj}u_{n}$$

$$
A=\begin{pmatrix}
a_{1j} \\
\dots \\
a_{nj}
\end{pmatrix},
M=\begin{pmatrix}
m_{1j} \\
\dots \\
m_{nj}
\end{pmatrix}
$$
- Dove $j$ indica la ***colonna***

>[!question] Che legame c'è tra $A$ e $M$?

>[!info] Definizione
>La ***matrice del cambiamento di base*** è $B$, ottenuta esprimendo i vettori di $\mathcal{B}'$ in funzione dei vettori di $\mathcal{B}$
>$$u_{j}=b_{1j}v_{1}+\dots+b_{nj}v_{n}$$

$$
B=\begin{pmatrix}
b_{1j} \\
\dots \\
b_{nj}
\end{pmatrix}
$$
>[!check]
>$$M=B^{-1}\times A \times B$$

### Dimostrazione
>*La dimostrazione si basa su calcoli e sull'osservazione che la matrice del cambiamento di base inverso è $B^{-1}$*

$$
v_{j}=c_{1j}u_{1}+\dots+c_{nj}u_{n}
$$
$$
B^{-1}=\begin{pmatrix}
c_{1j} \\
\dots \\
c_{nj}
\end{pmatrix}
$$
#### Esempio
[[4 - Isomorfismo#Esempio Cambio di Base|Esercizio di Riferimento]]

>$V=\mathbb{R}^2, v_{1}=(2,1),v_{2}=(1,-1), u_{1}=e_{1},u_{2}=e_{2}$

Sia $f:V\to V$ tale che $f(v_{1})=v_{1}+v_{2},f(v_{2})=3v_{1}-2v_{2}$

- Consideriamo la matrice nella base $v_{1},v_{2}$
$$
A=\begin{pmatrix}
1 & 3 \\
1 & -2
\end{pmatrix}
$$

Calcoliamo la matrice di $f$ nella base $u_{1},u_{2}$
$$
M=\begin{pmatrix}
\frac{7}{3} & -\frac{5}{3} \\
\frac{5}{3} & -\frac{10}{3}
\end{pmatrix}
$$

Scriviamo la ***matrice del cambiamento di base***

$$
\begin{array}
\ u_{1}=\frac{1}{3}v_{1}+\frac{1}{3}v_{2} \\
u_{2}= \frac{1}{3}v_{1}-\frac{2}{3}v_{2}
\end{array}
, \ \ \ \ B=\begin{pmatrix}
\frac{1}{3} & \frac{1}{3} \\
\frac{1}{3}  & -\frac{2}{3}
\end{pmatrix}

$$
$$
\begin{array}
\ v_{1}=2u_{1}+1u_{2} \\
v_{2}=1u_{1}-1u_{2}
\end{array}
\ \ \ \ B^{-1}=\begin{pmatrix}
2 & 1 \\
1 & -1
\end{pmatrix}
$$

>[!abstract] Verifichiamo $BB^{-1}=I_{2}=B^{-1}B$

$$
\begin{pmatrix}
\frac{1}{3} & \frac{1}{3} \\
\frac{1}{3}  & -\frac{2}{3}
\end{pmatrix}\times
\begin{pmatrix}
2 & 1 \\
1 & -1
\end{pmatrix}=\begin{pmatrix}
1 & 0 \\
0 & 1
\end{pmatrix}=\begin{pmatrix}
2 & 1 \\
1 & -1
\end{pmatrix}\times 
\begin{pmatrix}
\frac{1}{3} & \frac{1}{3} \\
\frac{1}{3}  & -\frac{2}{3}
\end{pmatrix}
$$

Verifichiamo anche che $B^{-1}\times A \times B=M$
$$
\underbrace{ \begin{pmatrix}
2 & 1 \\
1 & -1
\end{pmatrix} }_{ B^{-1} }\times
\underbrace{ \begin{pmatrix}
1 & 3 \\
1 & -2
\end{pmatrix} }_{ A } \times
\underbrace{ \begin{pmatrix}
\frac{1}{3}  & \frac{1}{3} \\
\frac{1}{3}  & -\frac{2}{3}
\end{pmatrix} }_{ B }=
\begin{pmatrix}
3 & 4 \\
0 & 5
\end{pmatrix}
\times
\begin{pmatrix}
\frac{1}{3} & \frac{1}{3} \\
\frac{1}{3}  & -\frac{2}{3}
\end{pmatrix}=
\begin{pmatrix}
\frac{7}{3} &  -\frac{5}{3}  \\
\frac{5}{3} & -\frac{10}{3}
\end{pmatrix}=M
$$

## Matrici Simili
---
>[!info] Definizione
>Due matrici $A,M$ sono ***simili*** se esiste una matrice invertibile $B$ tale che
>$$M=B^{-1}\times A \times B$$

>[!tldr] Osservazione
>Per il teorema precedente, due matrici sono ***simili*** $\iff$ rappresentano la ***stessa applicazione lineare*** in basi diverse

#### Esempio
$$
A=\begin{pmatrix}
1 & 3 \\
1 & -2
\end{pmatrix}
,\ \ \ \ M=\begin{pmatrix}
\frac{7}{3} & -\frac{5}{3} \\
\frac{5}{3} & -\frac{10}{3}
\end{pmatrix}
$$
***Sono simili***

#### Esempio
$M$ e $I_{2}$ non sono ***simili***, perché
$$
\forall B, B^{-1}\times I_{2}\times B= B^{-1}\times B = I_{2} \neq M
$$

### Proprietà
>*Essere "Simili" è una relazione di equivalenza tra matrici*

#### Dimostrazione
>*Riflessiva*

Ogni matrice $A$ è ***simile*** a se stessa
$$
I_{n}^{-1}\times A \times I_{n} = A
$$

>*Simmetrica*

Se $A$ è ***simile*** a $M$ allora $M$ è ***simile*** ad $A$
$$
\exists B\text{ invertibile}: M=B^{-1}\times A \times B
$$

$$
B\times M=\underbrace{ \cancel{ B\times B^{-1} } }_{ I_{n} }\times A\times B \Leftrightarrow B\times M \times B^{-1}=A\times \underbrace{ \cancel{ B\times B^{-1} } }_{ I_{n} }
$$
$$
B\times M\times B^{-1}=A
$$

>*Transitiva*

Se $A$ è simile a $M$, cioè $\exists B$ *invertibile* $:M=B^{-1}\times A\times B$
E se $M$ è simile ad $N$, cioè $\exists C$ *invertibile* $: N=C^{-1}\times M \times C$

- Sostituendo $M$ ottengo

$$
N=C^{-1}\times(B^{-1}\times A\times B)\times C = (B\times C)^{-1}\times A \times (B\times C)
$$
Cioè $A$ è simile ad $N$


## Matrici Quadrate Invertibili
---
>[!question] Come si fa a capire se una matrice quadrata $A$ è invertibile?

>[!check]
>Una ***matrice quadrata*** $A$ è invertibile $\iff$ i suoi vettori colonna sono [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Dipendenza Lineare|linearmente indipendenti]]

### Dimostrazione
>*Siano* $v_{1},\dots,v_{n}$ *i vettori colonna di* $A\in\mathcal{M}_{n\times n}$

Consideriamo l'applicazione lineare $f:\mathbb{K}^n\to\mathbb{K}^n$ tale che:
$$
f(e_{1})=v_{1},f(e_{2})=v_{2},\dots,f(e_{n})=v_{n}
$$
$f$ esiste ed è unica per il [[3 - Estensione Lineare|teorema dell'estensione lineare]]

>[!done] La matrice di $f$ nella base canonica è proprio $A$

$$
f(e_{j})=v_{j}=x_{1}e_{1}+\dots+x_{n}e_{n}
$$

- Dove 

$$
v_{j}=\begin{pmatrix}
x_{1} \\
\dots \\
x_{n}
\end{pmatrix}
$$
Notiamo che la funzione è ***invertibile***
- Quindi per il [[4 - Isomorfismo#Teorema Isomorfismo-Basi|teorema isomorfismo-basi]] 

$f$ è un isomorfismo $\iff$ $v_{1},\dots,v_{n}$ è una [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Base|base]] di $\mathbb{K}^n$

Poiché in $\mathbb{K}^n$ ogni insieme di $n$ ***vettori linearmente indipendenti è una base***
$$
A \text{ è invertibile } \iff f \text{ è un isomorfismo}\iff v_{1},\dots, v_{n} \text{ sono lin. indipendenti}
$$

#### Esempio
>*Consideriamo la matrice $A$*

$$
A=\begin{pmatrix}
2 & 5 \\
1 & 3
\end{pmatrix}
$$
I vettori $v_{1}=(2,1),v_{2}=(5,3)$ sono linearmente indipendenti
- perché di $av_{1}=(2a,a)\neq (5,3)$

Per il teorema precedente $A$ è ***invertibile***
- In effetti:
$$
\exists! \text{ appl. lineare }f:\mathbb{R}^2\to \mathbb{R}^2: f(e_{1})=v_{1},f(e_{2})=v_{2}
$$
- E la sua matrice è $A$

Se $v\in \mathbb{R}^2, v=(x,y)=xe_{1}+ye_{2}$
$$
f(v)=xf(e_{1})+yf(e_{2})=xv_{1}+yv_{2}=(2x+5y,x+3y)
$$
Vediamo che in effetti $f(x,y)=(2x+5y,x+3y)$ è ***invertibile***

Sia $u=(a,b)\in\mathbb{R}^2:u=f(v)$

$$
\begin{cases}
2x+5y=a \\
x+3y = b
\end{cases} \iff
\begin{cases}
x=3a-5b \\
y=2b-a
\end{cases}
$$

Quindi è vero che $\forall=(a,b)\exists! v=(x,y):f(v)=u$
- Precisamente $f^{-1}(a,b)=(3a-5b,2b-a)$

Quindi la matrice di $f^{-1}$ è:
$$
A^{-1}=\begin{pmatrix}
3 & -5 \\
-1 & 2
\end{pmatrix}
$$

#### Esempio
>*Consideriamo la matrice $A$*

$$
A=\begin{pmatrix}
-1 & 2 \\
3 & -6
\end{pmatrix}
$$

$v_{1}=(-1,3)$ e $v_{2}=(2,-6)$ ***non sono linearmente dipendenti***
- Quindi per il teorema appena visto $A$ ***non è invertibile***

In effetti l'unica ***applicazione lineare*** tale che $f(e_{1})=v_{1},f(e_{2})=v_{2}$ è:

$$
\begin{array}
\ f(e_{1})=-e_{1}+3e_{2} \\
f(e_{2})=2e_{1}-6e_{2}
\end{array} \implies f(x,y)=(-x+2y,3x-6y)
$$

In effetti $$\mathrm{ker}f=\{ (x,y):\begin{cases}
-x+2y=0 \\
3x-6y=0
\end{cases}\implies \begin{cases}
-x+2y=0 \\
0=0
\end{cases} \}$$

Cioè
$$
\mathrm{ker}f=\{ (x,y):x=2y \}
$$
- Quindi $\text{dim}(\mathrm{ker}f)=1$ 

>[!fail] $f$ *non* è iniettiva

Di conseguenza $f$ non è invertibile

>[!fail] Non esiste una matrice $A^{-1}$ tale che
>$$A\times A^{-1}=I_{2}=A^{-1}\times A$$


## Rango di una Matrice
---
>[!info] Definizione
>Il ***rango di una matrice*** è il *massimo numero* di vettori colonna [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Dipendenza Lineare|linearmente indipendenti]]
>>[!done] ‎ 
>>Possiamo allora riformulare il teorema precedente:
>>Una matrice $n\times n$ è ***invertibile*** $\iff$ ha ***rango*** $n$

