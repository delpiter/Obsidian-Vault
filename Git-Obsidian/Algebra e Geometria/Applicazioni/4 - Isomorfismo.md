## Isomorfismo
---
>[!info] Definizione
>Un ***isomorfismo*** è una [[../Basi dell'algebra/1 - Introduzione#Funzione o Applicazione|applicazione]] [[1 - Applicazioni Lineari#Applicazione Lineare|lineare]] e [[../../Analisi/Funzioni/Introduzione Funzioni#Funzione Biunivoca|biunivoca]]

#### Esempio 1
>$f:\mathbb{R}^2\to \mathbb{R}^2, f(x,y)=(x+y,x-y)$

>[!question] $f$ è un isomorfismo?
- Devo controllare se è lineare e se è biunivoca
>[!question] $f$ è lineare?
- $v_{1}=(x,y)$
- $v_{2}=(x',y')$

$$
\begin{array}
\ f((x,y)+(x',y'))=f(x,y)+f(x',y') \\
f(x+x',y+y')=(x+x'+y+y',x+x'-y-y') \\
f(x,y)+f(x',y')=(x+y,x-y)+(x'+y',x'-y')=(x+x'+y+y',x+x'-y-y')
\end{array}
$$
$$
\begin{array}
\ f(a(x,y))=af(x,y) \\
f(a(x,y))=(ax+ay,ax-ay) \\
af(x,y)=a(x+y,x-y)=(ax+ay,ax-ay)
\end{array}
$$

>[!done] $f$ è lineare

>[!question] $f$ è *biunivoca*?


$\mathrm{ker}f=\{ \underline{0} \}\implies f$ è iniettiva $\implies f$ è biunivoca
- (Vedi [[2 - Teorema del Rango#Conseguenze del Teorema del Rango|conseguenze del teorema del Rango]])
Quindi $f$ è lineare e biunivoca

>[!done] $f$ è un isomorfismo tra $\mathbb{R}^2$ e se stesso

#### Esempio 2
>Sia $V=\mathbb{R}[x]_{\leq n-1}=\{ \text{polinomi di grado }\leq n-1 \}=\{ p(x)=a_{0}+a_{1}x+a_{2}x^2+\dots+a_{n-1}x^{n-1} \}$
>E sia $U=\mathbb{R}^n$

Sia $f:V\to U$, $a_{0}+a_{1}x+a_{2}x^2+\dots+a_{n-1}x^{n-1}\mapsto(a_{0},a_{1},a_{2},\dots,a_{n-1})$

- $f$ è iniettiva perche $f(p(x))=\underline{0}\Leftrightarrow p=0$
	- E dunque $\mathrm{ker}=\{ \underline{0} \}$
- $f$ è suriettiva

>[!done] $f$ è un ***isomorfismo*** tra $V$ e $U$

### Spazi Isomorfi
>[!info] Definizione
>Due [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Spazio Vettoriale|spazi vettoriali]] $V,U$ su uno stesso [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Campo|campo]] $\mathbb{K}$, sono ***Isomorfi*** se esiste un isomorfismo da $V\to U$
>>[!tip] Proprietà
>>Essere Isomorfi è una [[../Basi dell'algebra/1 - Introduzione#Relazione di Equivalenza|relazione di equivalenza]]

#### Dimostrazione
>[!abstract] Proprietà Riflessiva

Uno spazio vettoriale è un ***isomorfismo*** *rispetto a se stesso*
- Prendo la [[../../Analisi/Funzioni/Introduzione Funzioni#Funzione Identità|funzione identità]]
$$
\begin{array}
\ f:V\to V \\
v\mapsto v
\end{array}
$$
- È un ***isomorfismo***

>[!abstract] Proprietà Simmetrica

##### Proprietà
>L'***inverso*** di un isomorfismo è un isomorfismo

###### Dimostrazione
>Sia $f:V\to U$ un *isomorfismo* di [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Spazio Vettoriale|spazi vettoriali]]

Poiché $f$ è biunivoca, esiste $f^{-1}:U\to V$

>[!question] $f$ è lineare?

Siano $u_{1},u_{2}\in U$
- Poiché $f$ è [[../../Analisi/Funzioni/Introduzione Funzioni#Funzione Biunivoca|biunivoca]], cioè
$$
\exists! v_{1},v_{2}\in V :f(v_{1})=u_{1},f(v_{2}) =u_{2}
$$

Possiamo dire che :
$$
f^{-1}(u_{1}+u_{2})=f^{-1}(f(v_{1})+f(v_{2}))
$$
E poiché $f$ è lineare:
$$
f^{-1}(f(v_{1}+v_{2})) = v_{1}+v_{2}=f^{-1}(u_{1})+f^{-1}(u_{2})
$$

Quindi $f^{-1}$ è un ***isomorfismo***

>[!abstract] Proprietà Transitiva

##### Proprietà
>La ***composizione*** di [[1 - Applicazioni Lineari#Applicazione Lineare|applicazioni lineari]] è lineare
>- *In particolare la composizione di isomorfismi è un isomorfismo*

###### Dimostrazione
>Siano $V,U,W$ [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Spazio Vettoriale|spazi vettoriali]] e $f,g$ *applicazioni lineari*
$$
V\underbrace{ \to }_{ f } U \underbrace{ \to }_{ g } W
$$

>[!abstract] Somma

Siano $v_{1},v_{2}\in V$
- Allora $(g_{o}f)(v_{1}+v_{2})=g(f(v_{1}+v_{2}))$

Quindi poiché $f$ è *lineare*, possiamo dire che:
- $g(f(v_{1})+f(v_{2}))$
Di nuovo, poiché $g$ è *lineare*
- $g(f(v_{1}))+g(f(v_{2}))=(g_{o}f)(v_{1})+(g_{o}f)(v_{2})$


>[!abstract] Prodotto

>Analogamente il *prodotto per scalare*:

$$
g(f(av)) = g(af(v))=ag(f(v))
$$

Inoltre se $f$ e $g$ sono [[../../Analisi/Funzioni/Introduzione Funzioni#Funzione Biunivoca|biunivoche]], cioè esistono le *inverse* $f^{-1},g^{-1}$
- Allora anche $g_{o}f$ è ***biunivoca***, perché la sua inversa è:
$$
(g_{o}f)^{-1} =f^{-1}_{o}g^{-1}
$$
>[!done] Conclusione

Quindi $g_{o}f$ è un'applicazione lineare biunivoca
- $g_{o}f$ è un ***isomorfismo***

### Endomorfismo
>[!info] Definizione
>Sia $\mathbb{K}$ un [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Campo|campo]], $V$ un [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Spazio Vettoriale|spazio vettoriale]] su $\mathbb{K}$
>Un ***endomorfismo*** di $V$ è un'[[1 - Applicazioni Lineari#Applicazione Lineare|applicazione lineare]] $f:V\to V$

## Teorema Isomorfismo-Basi
---
>Ora vogliamo legare il concetto di isomorfismo a quello di [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Base|base]]

>[!info] Teorema
> Un'[[1 - Applicazioni Lineari#Applicazione Lineare|applicazione lineare]] $f:V\to U$
> È un ***isomorfismo*** $\iff$ Manda *basi* di $V$ in *basi* di $U$

### Dimostrazione
>$\implies$

Sia $f:V\to U$ un isomorfismo e sia $v_{1},\dots,v_{n}$ una base di $v$

>*Vogliamo dimostrare che $f(v_{1}),\dots,f(v_{n})$ è base di $U$* 

>[[../Basi dell'algebra/3 - Teoremi su Spazi Vettoriali#Teorema delle Coordinate|teorema delle coordinate]] 

>*Sia $u\in U$*

Poiché $f$ è [[../../Analisi/Funzioni/Introduzione Funzioni#Funzione Biunivoca|biunivoca]]:
$$
\exists! a_{1},\dots,a_{n}\in \mathbb{K}:v=a_{1}v_{1}+\dots+a_{n}v_{n}:f(v)=u
$$
Poiché $f$ è ***lineare***
$$
u=f(v)=a_{1}f(v_{1})+\dots+a_{n}f(v_{n})
$$
Quindi ogni $u$ si scrive in **modo univoco** come [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Combinazioni Lineari|combinazione lineare]] di $f(v_{1}),\dots,f(v_{n})$

>[!done] $f(v_{1}),\dots,f(v_{n})$ sono una ***base*** di $u$

>$\impliedby$

Sia $v_{1},\dots,v_{n}$ una base di $V$ e sia $f:V\to U$ una applicazione lineare tale che $f(v_{1}),\dots,f(v_{n})$ è una base di $U$

>*Vogliamo dimostrare che $f$ è un isomorfismo*

Sia $u\in U$, poiché $f(v_{1}),\dots,f(v_{n})$ è una ***base*** 
$$
\exists! a_{1},\dots,a_{n}\in\mathbb{K}:u=a_{1}f(v_{1})+\dots+a_{n}f(v_{n})
$$
Ma dato che $f$ è ***lineare***
- $f(a_{1}v_{1}+\dots+a_{n}v_{n})$

Quindi $\forall u \in U,\exists!v\in V$ *precisamente* $v=a_{1}v_{1}+\dots+a_{n}v_{n}:f(v)=u$

>[!done] $f$ è biunivoca $\implies f$ è un isomorfismo

### Osservazioni
>[!abstract] Osservazione 1

Il [[3 - Estensione Lineare#Teorema dell'Estensione Lineare|Teorema dell'Estensione Lineare]]
- Data una base $v_{1},\dots,v_{n}$ di $V$
- Dati vettori $u_{1},\dots,u_{n}\in U$
Esiste un'unica [[1 - Applicazioni Lineari#Applicazione Lineare|applicazione lineare]] tale che
$$
f(v_{1})=u_{1},\dots,f(v_{n})=u_{n}
$$
Il teorema di oggi "*completa*" questa informazione:
$$
f\text{ Isomorfismo }\Leftrightarrow u_{1},\dots,u_{n} \text{ sono base di }U
$$

>[!abstract] Osservazione 2

Nello stesso modo con cui abbiamo dimostrato il ***teorema precedente***, si può *dimostrare* che:
- Un'***applicazione iniettiva*** manda insiemi *linearmente indipendenti* in insiemi *linearmente indipendenti*
- Un'***applicazione suriettiva*** manda insiemi che *generano* $V$ in insiemi che *generano* $U$

#### Esercizio
>[!question] Dire se esiste un'applicazione $f:\mathbb{R}^2\to\mathbb{R}^2$ tale che

$$
f(v_{1})=u_{1},f(v_{2})=u_{2}
$$
- Dove:
$$
\begin{array}
\ v_{1}=(1,1),v_{2} = (1,-1) \\
u_{1}=(0,2), u_{2}=(-1,0)
\end{array}
$$

>[!question] Se esiste dire se è un ***isomorfismo***

>[!question] Dire se $f(e_{1}),f(e_{2})$ è una *base*

##### Soluzione

>*Poiché $v_{1},v_{2}$ è  una base*

>[!done] Esiste ed è unica una tale $f$

>*Poiché $u_{1},u_{2}$ è una base*

>[!done] $f$ è un *isomorfismo*

>*Poiché $e_{1}=(1,0),e_{2}=(0,1)$ è una base, e poiché sappiamo che $f$ è un isomorfismo*

>[!done] $f(e_{1}),f(e_{2})$ è una *base*

#### Esercizio
>[!question] Dire se esiste ed è unica $f:\mathbb{R}^2\to\mathbb{R}^2$ tale che

$$
f(v_{1}) = w_{1},f(v_{2})=w_{2}
$$
- Dove
$$
\begin{array}
\ v_{1}=(1,1),v_{2}=(1,-1) \\
w_{1}=(-1,2),w_{2}=(2,-4)
\end{array}
$$
>[!question] In tal caso, dire se $f$ è un isomorfismo

>[!question] Trovare $\mathrm{Im}f$ e $\mathrm{ker}f$

##### Soluzione
>*Poiché $v_{1},v_{2}$ è una* ***base***

>[!done] Esiste ed è unica tale $f$

>*Poiché $w_{2}=-2w_{1}$ tali vettori non formano una base*

>[!fail] $f$ NON è un *isomorfismo*

>*Sia $v\in\mathbb{R}^2$*

Poiché $v_{1},v_{2}$ sono base $\implies \exists!a_{1},a_{2}\in\mathbb{K}:v=a_{1}v_{1}+a_{2}v_{2}$

Quindi $f(v)=a_{1}f(v_{1})+a_{2}f(v_{2})=a_{1}w_{1}+a_{2}w_{2}$
- $a_{1}(-1,2)+a_{2}(2,-4) =(-a_{1}+2a_{2},2a_{1}-4a_{2})$

$\mathrm{Im}f=\{ f(v),v\in V \}$
- $=\{ (-a_{1}+2a_{2},2a_{1}-4a_{2}),a_{1},a_{2}\in\mathbb{K}=\mathbb{R} \}=\{ (t-2t),t\in\mathbb{R} \}$

Poiché $\text{dim }\mathrm{Im}f=1$, per il [[2 - Teorema del Rango|teorema del rango]]:
- $\text{dim }\mathrm{ker}f=2-1=1$

Quindi $\mathrm{ker}f$ è dato da una equazione cartesiana in $\mathbb{R}^2$

Poiché $w_{2}=-2w_{1}$, cioè $2w_{1}+w_{2}=\underline{0}$ allora $f(2v_{1}+v_{2})=2w_{1}+w_{2}=\underline{0}$
- Quindi $2v_{1}+v_{2}=(3,1)\in\mathrm{ker}f$

### Corollario
>*Teorema la cui dimostrazione è conseguenza di un altro teorema*

>[!info]
>Due [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Spazio Vettoriale|spazi vettoriali]] sullo stesso campo $\mathbb{K}$ con la stessa dimensione sono tra loro *isomorfi*

#### Dimostrazione
>*Siano $U,V$ spazi vettoriali su $\mathbb{K}$ di dimensione $n$*

Dunque $V$ ha una *base* $v_{1},\dots,v_{n}$
- $U$ ha una *base* $u_{1},\dots, u_{n}$

<u>Allora</u>

Per il teorema dell'[[3 - Estensione Lineare#Teorema dell'Estensione Lineare|estensione lineare]]:

$$
\exists! f:V\to U \text{ lineare }:f(v_{1})=u_{1},\dots,f(v_{n})=u_{n}
$$
Per il teorema isomorfismo-basi $f$ è un ***isomorfismo***

#### Esempio
>*Sia $V=\mathbb{R}^n$ $U=\mathbb{R}[x]_{<n}=\mathbb{R}[x]_{\leq n-1}$ polinomi di grado $<n$* 

Base di $V=e_{1},\dots,e_{n}$

Base di $U=1,\dots,x^{n-1}$

Esiste un'unica $f:V\to U:f(e_{1})=1,\dots,f(e_{n})=x^{n-1}$ e tale $f$ è un *isomorfismo*
- Esplicitamente $f((a_{0},\dots,a_{n-1}))=a_{0}+\dots+a_{n-1}x^{n-1}$

#### Esempio
##### Spazio Vettoriale di Matrici
>*Sia $\mathcal{M}_{m,n}(\mathbb{K})=\{ \text{matrici }m\times n\text{ a coefficiente in }\mathbb{K} \}$*

Esso è uno ***spazio vettoriale*** su $\mathbb{K}$ che ha per *base*
$$
\left\{ E_{ij},\begin{array}
\ i\in\{ 1,\dots,n \} \\
j\in\{ 1,\dots,m \}
\end{array} \right\}
$$
$$
\begin{pmatrix}
0 & \dots & 0 \\
\dots & 1 & \dots \\
0 & \dots & 0
\end{pmatrix}
$$
- $1$ nella $i$-esima ***riga*** e $j$-esima ***colonna***
$E_{ij}$ sono dette le "***matrici elementari***" o la base canonica di $\mathcal{M}_{m,n}(\mathbb{K})$

###### Esempio
>*Sia $V=\{ \text{matrici }2\times3 \text{ a coefficiente}\in\mathbb{R}\}=\mathcal{M}_{2,3}(\mathbb{R})$*

$$
\left\{   
\begin{pmatrix}
a & c & e \\
b & d & f
\end{pmatrix},a,b,c,d,e,f\in\mathbb{R} \right\}
$$

$V$ è uno spazio vettoriale rispetto alle operazioni
- ***Somma*** fra matrici
- ***Prodotto*** per scalare

$$
\begin{pmatrix}
2 & 0 & 11 \\
1 & 3 & 4
\end{pmatrix}+
\begin{pmatrix}
3 & \frac{1}{2}  & 0 \\
0 & 0 & 3
\end{pmatrix}=\begin{pmatrix}
5 & \frac{1}{2} & 11 \\
1 & 3 & 4
\end{pmatrix}
$$
$$
3\begin{pmatrix}
2 & 0 & 11 \\
1 & 3 & 4
\end{pmatrix}=\begin{pmatrix}
6 & 0 & 33 \\
3 & 9 & 12
\end{pmatrix}
$$
>[!question] Qual'è la dimensione di $V$?

>*Cerchiamo una base*

$$
\begin{array}
\ \\
E_{11}=\begin{pmatrix}
1 & 0 & 0  \\
0 & 0 & 0
\end{pmatrix},E_{21}=
\begin{pmatrix}
0 & 0 & 0 \\
1 & 0 & 0
\end{pmatrix},
E_{12}=\begin{pmatrix}
0 & 1 & 0 \\
0 & 0 & 0
\end{pmatrix}, \\

E_{22}=\begin{pmatrix}
0 & 0 & 0 \\
0 & 1 & 0
\end{pmatrix},
E_{13}=\begin{pmatrix}
0 & 0 & 1 \\
0 & 0 & 0
\end{pmatrix},
E_{23}=\begin{pmatrix}
0 & 0 & 0 \\
0 & 0 & 1
\end{pmatrix}
\end{array}
$$
- Formano una base di $V$ perché
$$
\forall \begin{pmatrix}
a & c & e \\
b & d & f
\end{pmatrix}\in V,\exists!(a,b,c,d,e,f)\in\mathbb{R}^6:
$$
$$
\begin{pmatrix}
a & c & e \\
b & d & f
\end{pmatrix}=aE_{11}+bE_{21}+cE_{12}+dE_{22}+eE_{13}+fE_{23}
$$
Quindi, $\text{dim}(v)=6$ e $V$ è isomorfo a $\mathbb{R}^6$

#### Esempio
>*Sia* $V=\mathbb{R}^3, U=\mathbb{R}^2$
- $\text{Hom}\to$ Homorphism
$$
\text{Hom}(V,U)=\{ \text{applicazioni lineari }V\to U \}
$$
È uno spazio vettoriale su $\mathbb{R}$ rispetto alle operazioni:
$$
\begin{array}
\ \forall f,g\in \text{Hom}(V,U),\forall a \in\mathbb{R} \\
(f+g)(v)=f(v)+g(v) \\
(af)(v)=af(v)
\end{array}
$$
>[!question] Qual è la dimensione di questo spazio?

Fissiamo *basi* di $V$ e $U$, ad esempio:
- $e_{1}=(1,0,0),e_{2}=(0,1,0),e_{3}=(0,0,1)$ ***base*** di $V$
- $e_{1}'=(1,0),e_{2}'=(0,1)$ ***base*** di $U$

Dato $g\in \text{Hom}(V,U)$ *scriviamo* la sua ***matrice*** in tali *basi*
- Calcoliamo quindi
$$
\begin{pmatrix}
a & c & e \\
b & d & f
\end{pmatrix}
$$
- $g(e_{1})\in\mathbb{R}^2\implies \exists! a,b:g(e_{1})=ae_{1}'+be_{2}'$
- $g(e_{2})\in\mathbb{R}^2\implies \exists! c,d:g(e_{2})=ce_{1}'+de_{2}'$
- $g(e_{3})\in\mathbb{R}^2\implies \exists! e,f:g(e_{3})=ee_{1}'+fe_{2}'$

Consideriamo $\Phi:\text{Hom}(U,V)\to\mathcal{M}_{2,3}$

$\Phi$ è:
>[!abstract] Lineare

Perché la ***somma di matrici*** è uguale alla ***matrice della somma***
- Lo stesso vale per il ***prodotto per scalare***

>[!abstract] Iniettiva

Perché se matrice di $g$ è $$\begin{pmatrix}
0 & 0 & 0 \\
 0& 0 & 0 
\end{pmatrix}$$
Allora $g$ è l'applicazione nulla $(g=0)$

>[!abstract] Suriettiva

Ogni *matrice*
$$
\begin{pmatrix}
a & c & e \\
b & d & f
\end{pmatrix}
$$
Viene da una $g$ per il [[3 - Estensione Lineare#Teorema dell'Estensione Lineare|teorema dell'estensione lineare]]

>[!done] In altre parole
>L'applicazione $\Phi$, che associa ogni *applicazione lineare* alla sua matrice è un ***isomorfismo*** tra:
>$$\text{Hom}(V,U)$$ e $$\mathcal{M}_{2,3}(\mathbb{R})$$


>[!example] Osservazione
>Se avessi scelto ***basi diverse*** di $V,U$ avrei ottenuto un altro isomorfismo $\Phi$ tra 
>$$\text{Hom}(V,U)$$ e $$\mathcal{M}_{2,3}(\mathbb{R})$$

$$
\begin{array}
\ f_{11}: e_{1}\to e_{1}', e_{2}\to 0, e_{3}\to0 \underbrace{ \rightarrow }_{ \Phi } \begin{pmatrix}
1 & 0 & 0 \\
0 & 0 & 0
\end{pmatrix} = E_{11}, f(e_{1})=1e_{1}'+0e_{2}' \\
f_{21}: e_{1}\to e_{2}', e_{2}\to 0, e_{3}\to0 \underbrace{ \rightarrow }_{ \Phi } \begin{pmatrix}
0 & 0 & 0 \\
1 & 0 & 0
\end{pmatrix} = E_{21} \\
f_{12}: e_{1}\to 0, e_{2}\to e_{1}', e_{3}\to0 \underbrace{ \rightarrow }_{ \Phi } \begin{pmatrix}
0 & 1 & 0 \\
0 & 0 & 0
\end{pmatrix} = E_{12} \\
f_{22}: e_{1}\to 0, e_{2}\to e_{2}', e_{3}\to0 \underbrace{ \rightarrow }_{ \Phi } \begin{pmatrix}
0 & 0 & 0 \\
0 & 1 & 0
\end{pmatrix} = E_{22} \\
f_{13}: e_{1}\to 0, e_{2}\to 0, e_{3}\to e_{1}' \underbrace{ \rightarrow }_{ \Phi } \begin{pmatrix}
0 & 0 & 1 \\
0 & 0 & 0
\end{pmatrix} = E_{13} \\
f_{23}: e_{1}\to 0, e_{2}\to 0, e_{3}\to e_{2}' \underbrace{ \rightarrow }_{ \Phi } \begin{pmatrix}
0 & 0 & 0 \\
0 & 0 & 1
\end{pmatrix} = E_{23}
\end{array}
$$

>[!done] Quindi $f_{11},\dots,f_{23}$ è una base di $\text{Hom}(V,U)$

>*Analogamente, dato un campo $\mathbb{K}$ e due spazi vettoriali $V,U$ di dimensione $n,m$*

L'insieme $\text{Hom}(V,U)$ di tutte le applicazioni lineari $V\to U$ è uno spazio vettoriale su $\mathbb{K}$
- Con la dimensione: $\text{Dim } m\times n$

Fissando basi di $V,U$ posso associare a *un'applicazione lineare* $g:V\to U$ una matrice $m\times n$ e questa corrispondenza è un ***isomorfismo***
- Tra $\text{Hom}(V,U)$ e $\mathcal{M}_{m,n}(\mathbb{K})$

#### Esempio Cambio di Base
>*Siano $v_{1}=(2,1),v_{2}=(1,-1)$*

>[!question] Mostrare che $v_{1},v_{2}$ è una base di $\mathbb{R}^2$

>[!question] Mostrare che esiste un unico isomorfismo $f$ tale che
>$$f(v_{1})=v_{1}+v_{2},f(v_{2})=3v_{1}-2v_{2}$$

>[!question] Scrivere la matrice di $f$ nella base $v_{1},v_{2}$

>[!question] Scrivere la matrice di $f$ nella base $e_{1},e_{2}$

##### Soluzione
1. $v_{1},v_{2}$ è una base $\Leftrightarrow \forall v=(x,y)\in \mathbb{R}^2\exists! a_{1},a_{2}\in \mathbb{R}:v=a_{1}v_{1}+a_{2}v_{2}$ 

Cioè:
$$
(x,y)=(2a_{1}+a_{2},a_{1}-a_{2})
$$
$$
\begin{cases}
2a_{1}+a_{2} = x \\
a_{1}-a_{2}=y
\end{cases}\Leftrightarrow
\begin{cases}
a_{1}=\displaystyle{\frac{x-a_{2}}{2}} \\
-\frac{3}{2}a_{2}=y-\frac{1}{2}x
\end{cases}\Leftrightarrow
\begin{cases}
a_{1}=\frac{1}{3}x+\frac{1}{3}y \\
a_{2}=-\frac{2}{3}y+\frac{1}{3}x
\end{cases}
$$
>[!done] Ha una unica soluzione, si, $v_{1},v_{2}$ è una base

2. $v_{1}+v_{2}=(3,0),3v_{1}-2v_{2}=(4,5)$

È anche essa una base di $\mathbb{R}^2$
- Poiché $v_{1},v_{2}$ è una base, esiste un'unica $f$ *lineare* tale che:
$$
f(v_{1})=v_{1}+v_{2},f(v_{2})=3v_{1}-2v_{2}
$$
>[!done] Poiché $(3,0),(4,5)$ è una base, $f$ è un ***isomorfismo***

3. $$
\begin{pmatrix}
1 & 3 \\
1 & -2
\end{pmatrix}
$$
>[!done] È la *matrice* di $f$ se scelgo $v_{1},v_{2}$ come ***base del dominio e del codominio***

4. 
$f(e_{1})=\frac{1}{3}f(v_{1})+\frac{1}{3}f(v_{2})=\frac{1}{3}(3,0)+\frac{1}{3}(4,5)$
- $\left( \frac{7}{3}, \frac{5}{3} \right)=\frac{7}{3}e_{1}+\frac{5}{3}e_{2}$


$f(e_{2})=\frac{1}{3}f(v_{1})-\frac{2}{3}f(v_{2})$
- $\left( -\frac{5}{3},-\frac{10}{3} \right)=-\frac{5}{3}e_{1}-\frac{10}{3}e_{2}$

$$
\begin{pmatrix}
\displaystyle\frac{7}{3} & \displaystyle-\frac{5}{2} \\
\displaystyle\frac{5}{3}  & \displaystyle-\frac{10}{3}
\end{pmatrix}
$$
