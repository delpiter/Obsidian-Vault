## Isometria
---
>[!info] Definizione
>Sia $V$ uno [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Spazio Vettoriale|spazio vettoriale]] su $\mathbb{K}=\mathbb{R}$ con un [[../Frome Bilineari e Prodotti Scalari/4 - Prodotto Scalare#I Prodotti Scalari|prodotto scalare]]
>Una ***Isometria*** è una [[../Applicazioni/1 - Applicazioni Lineari#Applicazione Lineare|applicazione lineare]]: $f:V\to V$
>$$\forall v,u \in V\quad (f(v),f(u))=(v,u)$$

### Osservazione Significato
>[!tldr] Isometria
>***Isometria*** $=$ "***Stessa misura***"
>In effetti
>>[!info] Proposizione
>>$f$ è una isometria $\iff \forall v\in V\quad \mid\mid f(v)\mid\mid=\mid\mid v\mid\mid$

#### Dimostrazione
>$\implies$

Se $f$ è una isometria (*conserva il prodotto scalare*)

$$
\mid\mid f(v)\mid\mid=\sqrt{ (f(v),f(v)) }=\sqrt{ (v,v) }=\mid\mid v\mid\mid
$$
> $\impliedby$

Se $f$ *conserva la norma* di ogni vettore:
- Dati $v,u\in V$ calcoliamo:

$$
\begin{array}
\ \mid\mid v+u\mid\mid^2-\mid\mid v-u\mid\mid^2=(v+u,v+u)-(v-u,v-u)= \\
=(v,v)+(u,u)+2(v,u)-[(v,v)+(u,u)-2(v,u)]=4(v,u) \\
\implies(v,u)=\frac{1}{4}(\mid\mid v+u\mid\mid^2-\mid\mid v-u\mid\mid^2)
\end{array}
$$

Quindi se ***conserva la norma***
$$
(v,u)= \frac{1}{4}(\mid\mid v+u\mid\mid^2-\mid\mid v-u\mid\mid^2)=\frac{1}{4}(\mid\mid f(v)+f(u))\mid\mid^2-\mid\mid f(v)-f(u))\mid\mid^2)=(f(v),f(u))
$$

##### Esempio
>*Sia $V=\mathbb{R}^2$ con il [[../Frome Bilineari e Prodotti Scalari/4 - Prodotto Scalare#Prodotto Scalare Standard|prodotto scalare standard]]*

Dato $v=(x,y),\quad f:V\to V \quad f(x,y)=\left( \frac{\sqrt{ 3 }}{2}x+\frac{1}{2}y, -\frac{1}{2}x\frac{\sqrt{ 3 }}{2}y \right)$

- $\mid\mid v\mid\mid = \sqrt{ x^2+y^2 }$
- $\mid\mid f(v)\mid\mid=\sqrt{ \left( \frac{\sqrt{ 3 }}{2}x+\frac{1}{2}y \right)^2+\left( -\frac{1}{2}x\frac{\sqrt{ 3 }}{2}y \right) ^2}=\sqrt{ \frac{3}{4}x^2+\frac{1}{4}y^2\cancel{ +\frac{\sqrt{ 3 }}{2}xy }+\frac{1}{4}x^2+\frac{3}{4}y^2\cancel{ -\frac{\sqrt{ 3 }}{2}xy } }=\sqrt{ x^2+y^2 }$


>[!done] $f$ è una *isometria*
##### Controesempio
>*Sia $g:\mathbb{R}^2\to\mathbb{R}^2\quad g(x,y)=(2x,3y)$*

- $\mid\mid e_{1} \mid\mid=1$
- $\mid\mid g(e_{1}) \mid\mid=2$


>[!fail] $g$ non è una isometria

### Osservazione Distanza Euclidea
>[!tldr] Osservazione
>Poiché abbiamo definito la [[../Frome Bilineari e Prodotti Scalari/4 - Prodotto Scalare#Distanza Euclidea|distanza euclidea]] come $d(P,Q)=\mid\mid\overrightarrow{PQ}\mid\mid$
>La precedente proprietà ci dice che una isometria ***conserva le distanze***
>>[!info] Proposizione
>> Se $f$ è una ***isometria***
>><u>Allora</u>
>>$f$ ***conserva gli angoli***

#### Dimostrazione
In effetti [[../Frome Bilineari e Prodotti Scalari/4 - Prodotto Scalare#Angolo Convesso|l'angolo convesso]] tra $u$ e $v$ è definito come:

$$arcos\left( \displaystyle{\frac{(v,u)}{\mid\mid v \mid\mid\cdot\mid\mid u\mid\mid}} \right)=arcos \left( \displaystyle{\frac{(f(v),f(u))}{\mid\mid f(v)\mid\mid\cdot\mid\mid f(u)\mid\mid}} \right)  $$

che è proprio l'angolo convesso tra $f(v)$ e $f(u)$

>[!summary] Osservazione
>Non vale il viceversa
>Non tutte le applicazioni che *conservano gli angoli* sono ***isometrie***

##### Esempio
>*Dato il prodotto scalare standard su $V=\mathbb{R}^2$*

L'applicazione $f:V\to V\quad f(v)=2v$
- Conserva gli angoli:
$$
\left( \displaystyle{\frac{(f(v),f(u))}{\mid\mid f(v)\mid\mid\cdot\mid\mid f(u)\mid\mid}} \right)=\frac{\cancel{ 4 }}{\cancel{ 4 }} \displaystyle{\frac{(v,u)}{\mid\mid v\mid\mid\cdot\mid\mid u\mid\mid }}
$$

Ma evidentemente ***non conserva le lunghezze***
$$
\mid\mid f(v)\mid\mid = 2 \mid\mid v\mid\mid \neq \mid\mid v \mid\mid
$$

### Isomorfismi e Isometrie
>[[../Applicazioni/4 - Isomorfismo#Isomorfismo|isomorfismi]] e ***isometrie***?

>[!Teorema]
>Ogni ***isometria*** è un ***isomorfismo***

#### Dimostrazione
>*Sia $V$ uno spazio vettoriale con un prodotto scalare e sia $f:V\to V$ una isometria rispetto a quel prodotto scalare*

>[!abstract] Mostriamo che $f$ è iniettiva

Poiché un prodotto scalare è [[../Frome Bilineari e Prodotti Scalari/3 - Forme Quadratiche#Tipi di Forme Quadratiche|definito positivo]]:
$$
\mid\mid v \mid\mid = 0 \iff v = \underline{0}
$$

Ora se $v\in \mathrm{ker}(f)$
- $f(v)=0$ quindi $\mid\mid f(v)\mid\mid = \mid\mid\underline{0}\mid\mid=0$

Ma poiché $f$ è una ***isometria***:
$$
\mid\mid v\mid\mid = \mid\mid f(v) \mid\mid
$$
- Cioè $v=\underline{0}\implies\mathrm{ker}(f)=\{ \underline{0} \}\implies f$ è ***iniettiva***

Per il [[../Applicazioni/2 - Teorema del Rango#Teorema|Teorema del Rango]]:
$$
\text{dim}(\mathrm{Im}(f))=\text{dim}(V)-0
$$
Quindi $f$ è anche ***suriettiva***

>[!done] $f$ è un ***isomorfismo***

>[!summary] Concetto a parole
>Come fa una applicazione che ***conserva le lunghezze*** a mandare un vettore non nullo in un vettore nullo?

#### Osservazione
>[!tldr] Non Vale il viceversa
>$f(v)=2v$ è un ***isomorfismo***
>Ma non è una ***isometria*** rispetto ad ***alcun prodotto scalare***

### Matrice Ortogonale
>[!info] Definizione
>Una matrice $A$ è detta ***ortogonale*** se:
>$$A\cdot A^T=I_{n}$$

#### Esempio
$$
A=\begin{pmatrix}
\frac{\sqrt{ 3 }}{2} & \frac{1}{2} \\
-\frac{1}{2} & \frac{\sqrt{ 3 }}{2}
\end{pmatrix}
$$
$$
A\cdot A^T=\begin{pmatrix}
\frac{\sqrt{ 3 }}{2} & \frac{1}{2} \\
-\frac{1}{2} & \frac{\sqrt{ 3 }}{2}
\end{pmatrix}
\cdot\begin{pmatrix}
\frac{\sqrt{ 3 }}{2} & -\frac{1}{2} \\
\frac{1}{2} & \frac{\sqrt{ 3 }}{2}
\end{pmatrix}
=\begin{pmatrix}
\frac{3}{4}+\frac{1}{4} &  \frac{\sqrt{ 3 }}{4}-\frac{\sqrt{ 3 }}{4} \\
\frac{\sqrt{ 3 }}{4}-\frac{\sqrt{ 3 }}{4} & \frac{1}{4}+\frac{3}{4}
\end{pmatrix}=I_{2}
$$
>[!done] $A$ è *ortogonale*

#### Osservazione Matrice Ortogonale
>[!tldr] Osservazione
>$A$ è ***ortogonale*** $\iff$ le sue colonne rispetto al [[../Frome Bilineari e Prodotti Scalari/4 - Prodotto Scalare#Prodotto Scalare Standard|prodotto scalare standard]] formano una [[../Frome Bilineari e Prodotti Scalari/4 - Prodotto Scalare#Base Ortonormale|base ortonormale]]
