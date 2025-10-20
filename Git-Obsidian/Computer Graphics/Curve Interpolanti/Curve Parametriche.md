## Geometria delle Curve
---
>[!definizione]
>Una ***curva parametrizzata*** in $\mathbb{R}^{3}$ è un'[[1 - Applicazioni Lineari|applicazione]]
>$$C(t): I=[a,b]\subseteq \mathbb{R} \to \mathbb{R}^{3}$$
>- Con
>
>$$t \mapsto (x(t),y(t),z(t))$$
>
>Dove $x(t),y(t),z(t)$ sono funzioni continue del parametro $t\in [a,b]\subseteq \mathbb{R}$, dette ***componenti parametriche*** della curva.

Al variare di $t$, le coordinate $x(t),y(t),z(t)$ individuano un punto che si **sposta sulla curva**.

### Esempi

> Circonferenza di centro l'*origine* e di raggio $r$ in $\mathbb{R}^{2}$.

$$
C(t)=\begin{cases}
x(t) =r \cos(t) \\
y(t) = r \sin(t)
\end{cases}
$$
Con $t \in[0,2\pi]$

Un qualsiasi punto della circonferenza si trova nelle coordinate $P=(x(t),y(t))$.

> Equazione parametrica del segmento che congiunge due punti $P_{1}$ e $P_{0}$.

- $P(t)=P_{0}+t(P_{1}-P_{0})$
$$
P(t)=\begin{cases}
x=x_{0}+t(x_{1}-x_{0}) \\
y=y_{0}+t(y_{1}-y_{0})
\end{cases}
$$
Con $t\in[0,1]$

### Velocità
> L'intervallo $I=[a,b]$ definisce un insieme di punti in cui si sceglie di *visualizzare la curva*.

>[!info] Supporto
> L'immagine in $\mathbb{R}^{2}$ tramite $C$ dell'intervallo $I$ ($C(I)$), prende il nome di **supporto**, **sostegno** o **traiettoria** della curva.

>[!definizione] Curva Regolare
>Una curva si dice ***regolare*** se è [[Differenziabilità|differenziabile]] per ogni valore di $t\in I$ e se la norma del vettore derivata **non è nulla** in alcun punto di $I$.

Nel "*modello fisico*" del [[Moto Rettilineo|moto del punto]], ad ogni istante $t_{0}$, le coordinate $(x(t_{0}),y(t_{0}))$ individuano un punto che si sposta sulla curva con ***velocità*** data dalla tangente alla curva parametrica in $t_{0}$.
$$
v(t_{0})=\displaystyle{\frac{\text{d}C(t)}{\text{dt}}} = C'(t_{0})=\begin{bmatrix}
\displaystyle{\frac{\text{d}x(t_{0})}{\text{dt}}} \\
\displaystyle{\frac{\text{d}y(t_{0})}{\text{dt}}}
\end{bmatrix}=\begin{bmatrix}
x'(t_{0}) \\
y'(t_{0})
\end{bmatrix}
$$

Il ***modulo del vettore velocità*** rappresenta la *velocità istantanea*.
$$
\|C'(t_{0})\|_{2} =\sqrt{ x'(t_{0})^{2}+y'(t_{0})^{2} }
$$
- La direzione del vettore è data dal vettore tangente $C'(t_{0})$ e punta verso delle $t$ **crescenti**.

### Lunghezza di una Curva
> Sia $C(t):[a,b]\to \mathbb{R}^{2}$ una ***curva regolare***.

Consideriamo una suddivisione dell'intervallo $[a,b]$, mediante un insieme di punti $t_{1}=a<t_{2}<\dots<t_{n-1}<t_{n}=b$.
- Consideriamo la *poligonale* $P_{n}$ che collega i vertici $C(t_{i}), \ i=1,\dots,n$ sulla curva.
>[!abstract] Lunghezza
>La ***lunghezza della poligonale*** è data dalla somma delle lunghezze dei suoi lati.
>$$L(P_{n})=\sum_{i=1}^{n-1}\|C(t_{i+1}-C(t_{i}))\|$$

Aggiungendo un punto alla suddivisione dell'intervallo, si determina la poligonale $P_{n+1}$ di lunghezza $L(P_{n+1})\geq L(P_{n})$ ([[Proprietà degli Integrali#Disugualianza Triangolare|Disugualianza Triangolare]]).
- $L(P_{n+1})$ si avvicina alla ***lunghezza della traiettoria della curva***.

>[!help] Lunghezza della Curva
>Al tendere all'***infinito*** del numero dei punti delle suddivisioni di $[a.b]$, le lunghezze delle poligonali associate formano una [[Successioni#Successione Monotona|successione monotona]] **crescente** che converge all'integrale:
>$$L(C)=\lim\limits_{n\to \infty} L(P_{n})=\lim\limits_{n\to \infty}\sum_{i=1}^{n-1}\|C(t_{i+1}-C(t_{i}))\|=\int_{a}^{b} \,\|C'(t)\| \text{d}t $$

Siano $x'(t)$ e $y'(t)$ continue in $[a,b]$, allora la lunghezza di $C$ tra $C(a)$ e $C(b)$ è definita dalla seguente formula.
$$
L=\int _{a}^{b} \, \|C'(t)\| \text{d}t=\int _{a}^{b} \, \sqrt{ x'(t)^{2}+y'(t)^{2} } \text{d}t 
$$

### Curvatura
>[!definizione]
>La ***curvatura*** di una curva piana, è un elemento definito punto per punto dalla curva, che misura la *rapidità* con la quale la curva si **discosta dalla tangente**.

È la misura matematica di quanto una curva ***devii dall'essere retta*** nell'intorno di un punto.
- In generale *cambia da punto a punto*.

> Sia $C$ una curva regolare di classe $C^{k}$ con $k\geq2$.

Definiamo il ***versore della tangente***:
$$
T(t)=\frac{C'(t)}{\|C'(t)\|}
$$

>[!info] Funzione Curvatura
>La ***curvatura*** è la *funzione*:
>$$k(t): I\to \mathbb{R}^{+}$$
>di classe $C^{k-2}$.
>$$k(t)=\frac{\|T'(t)\|}{\|C'(t)\|}$$

>[!example] Esempio

> Sia $C(t)$ una circonferenza di raggio $R$

$$
C(t)=\begin{bmatrix}
R\cos(t) \\
R\sin(t)
\end{bmatrix}, \quad C'(t)\begin{bmatrix}
-R\sin(t) \\
R\cos(t)
\end{bmatrix}, \quad \|C'(t)\|_{2}=\sqrt{ R^{2}(\sin^{2}(t)+\cos^{2}(t)) }=R
$$

Calcoliamo il versore della normale.
$$
T(t)=\frac{C'(t)}{\|C'(t)\|}=\displaystyle{\frac{\begin{bmatrix}
-R\sin(t) \\
R\cos(t)
\end{bmatrix}}{\|C'(t)\|_{2}}}=\begin{bmatrix}
-\sin(t) \\
\cos(t)
\end{bmatrix}
$$
E la ***curvatura***:
$$
k(t)=\frac{\|T'(t)\|}{\|C'(t)\|}= \displaystyle{\frac{\left \|  \begin{bmatrix}
 -\cos(t) \\
-\sin(t)
\end{bmatrix}\right\|}{R}}=\displaystyle{\frac{\sqrt{ \cos^{2}(t)+\sin^{2}(t) }}{R}} = \frac{1}{R}
$$

>[!done] Conclusione
>Cerchi di *grande raggio* hanno ***piccola curvatura*** mentre cerchi di *piccolo raggio* hanno una ***curvatura grande***.

### Continuità
Se tra due segmenti di curva si uniscono ad un estremo, si dice che tra i due segmenti c'è un ***raccordo*** $C^{0}$ che assicura l'*assenza di salti*.

> Se si uniscono in un punto $P_{0}$ e detti  $v_{1}$ e $v_{2}$ i vettori velocità in $P_{0}$, si definisce:

>[!caution] Continuità Parametrica $C^{1}$
>Le *direzioni* e i *moduli* dei **vettori tangenti** $v_{1}$ e $v_{2}$ dei due segmenti curvi nel punto $P_{0}$ sono ***uguali***.

> $C^{n}$
- Le ***derivate*** fino a quella di *ordine* $n$ dei due segmenti nel punto $P_{0}$ sono uguali.

>[!cite] Continuità Geometrica $G^{1}$
>Le *direzioni* dei vettori tangenti $v_{1}$ e $v_{2}$ nel punto di contatto sono ***uguali***.
>- I **moduli** possono essere diversi.
## Curve Equivalenti
---
>Una stessa curva può essere tracciata a ***velocità differenti***.

>[!example] Esempio

> Equazione parametrica della circonferenza.

$$
C(t)=(x(t),y(t))=(\cos(t), \sin(t)), t \in [0,2\pi]
$$
- La curva inizia in $(1,0)$ e il punto si muove percorrendo ***una volta*** la circonferenza.
- La stessa circonferenza si ottiene anche con le **funzioni coordinate**:
$$
C_{1}(t)=(x_{1}(t),y_{1}(t))=(\cos(2t), \sin(2t)), t \in [0,2\pi]
$$
- La curva inizia in $(1,0)$ e il punto si muove lungo la curva percorrendo ***due volte*** la circonferenza.

>[!hint] Conclusione
>Una stessa curva può avere ***parametrizzazioni differenti***.
>>[!done] In altre Parole
>>Due curve parametrizzate possono avere lo ***stesso sostegno*** (tracciare la stessa figura), ma **percorrerla in modi differenti**.

### Relazione di Equivalenza
> Introduciamo una ***Relazione di Equivalenza*** in modo che due curve equivalenti descrivano lo *stesso oggetto geometrico*.

>[!summary] Relazione di Equivalenza
>Una ***relazione di equivalenza*** delle curve parametriche è una relazione che raggruppa tutte le curve che tracciano lo *stesso oggetto geometrico*.
>- Tutte le parametrizzazioni che hanno la stessa [[Git-Obsidian/Analisi/Funzioni/Introduzione Funzioni#Dominio e Codominio e Immagine|immagine]].

Due curve sono nella stessa ***classe di equivalenza*** se descrivono lo stesso oggetto.
- Questa relazione **raggruppa le curve** che descrivono lo *stesso insieme di punti*, ***indipendentemente*** dal modo in cui vengono percorse o dal parametro usato.

#### Proprietà
>[!hint] Due curve equivalenti hanno la stessa lunghezza.
>

> Dimostrazione

Siano $C_{1}(t):[a,b]\to\mathbb{R}^{2}$ e $C_{2}(t):[c,d]\to\mathbb{R}^{2}$ due ***curve parametrizzate equivalenti***.
- Sia $g: [c,d]\to [a,b]$ il *cambiamento di parametro*.
Calcoliamo la lunghezza di $C_{2}(t)$.
$$
L(C_{2})=\int _{c}^{d} \,\|C'_{2}(t)\| \text{d}t 
$$
Facciamo ora il cambiamento di variabili $x=g(t)$.
$$
L(C_{2})=\int _{c}^{d} \,\|C'_{2}(t)\| \text{d}t=\int _{c}^{d} \,\|C'_{1}(g(t))\| |g'(t)| \text{d}t=\int _{a}^{b}\|C_{1}'(x)\| \, \text{d}x 
$$
### Diffeomorfismo
>[!definizione]
>Una funzione $g:[a,b]\to[c,d]$ è un ***diffeomorfismo*** tra gli intervalli $[a,b]$ e $[c,d]$
><u>se</u>
>$g$  è una funzione [[Git-Obsidian/Analisi/Funzioni/Introduzione Funzioni#Funzione Biunivoca|biunivoca]], [[Differenziabilità|differenziabile]] con [[Derivate|derivata]] ***prima mai nulla***.

$g$ ammette un'unica funzione inversa $g^{-1}$ che risulta anch'essa un ***diffeomorfismo***.

#### Riparametrizzazione
>Siano $I=[a,b]$ e $J=[c,d]$ due intervalli.

>[!definizione]
>Data una curva $C_{1}(t):[a,b]\to\mathbb{R}^{2}$ e dato un ***diffeomorfismo*** $g:[c,d]\to[a,b]$, la curva:
>$$C_{2}(t)=C_{1}(g(t)):[a,b]\to\mathbb{R}^{2}$$ è detta ***riparametrizzazione*** di $C_{1}$ e $g(t)$ è un *cambiamento di parametro*.

Due curve $C_{1}(t):[a,b]\to\mathbb{R}^{2}$ e $C_{2}(t):[c,d]\to\mathbb{R}^{2}$ sono equivalenti se esiste un *diffeomorfismo* $g:[c,d] \to [a,b]$  tale che $C_{2}(t)=C_{1}(g(t))$.

>[!hint] Osservazione
>Due curve equivalenti hanno lo ***stesso supporto*** ma è ***differente la velocità*** con cui vengono percorse.
>$$v'=C_{2}'(t)=C_{1}'(g(t))g'(t)$$

###### Esempio
> Consideriamo la ***parametrizzazione della circonferenza***.

$$
C_{1}(t)=(x(t),y(t))=(\cos(t), \sin(t)), t \in [0,\pi]
$$
Sia $g(t):\left[ 0, \frac{\pi}{2} \right]\to[0,\pi]$ definita come $g(t)=2t$
- $g$ è invertibile e con derivata $g'(t)=2>0$
>[!done] $g$ è un **diffeomorfismo**

Consideriamo la riparametrizzazione di $C_{1}(t)$ usando il diffeomorfismo $g$.
$$
C_{2}(t)=C_{1}(g(t)): [0,\pi]\to \mathbb{R}^{2}
$$
$$
C_{2}(t)=(\cos(2t), \sin(2t)), t \in \left[ 0, \frac{\pi}{2} \right]
$$

### Lunghezza d'Arco
> Sia $C(t):[a,b]\to\mathbb{R}^{2}$ una **curva regolare**.

>[!caution] Lunghezza d'Arco
>La ***lunghezza d'arco*** di $C$ misurata a partire da $a$ è la funzione data da:
>$$s(t)=\int _{a}^{t} \,\|C'(\tau)\| \text{d}\tau $$

$s$ *mappa* i valori di $t$ della curva nella ***lunghezza della curva*** fra due punti.
- Per il [[Calcolo Integrale#Teorema Fondamentale del Calcolo Integrale $II$|Teorema Fondamentale del Calcolo Integrale]]:
$$
s'(t)=\|C'(t)\| >0
$$
- $s(t):[a,b]\to [0,L_{C}]$
- Se $t=b$ allora $s(t)=L_{C}$

>[!hint] Obbiettivo
>Vogliamo *riparametrizzare* la curva parametrica $C(t)$ in una nuova parametrizzazione che abbia ***velocità costante*** e ***unitaria***.

#### Parametrizzazione alla Lunghezza d'Arco
> Una curva ammette una ***riparametrizzazione*** con velocità scalare costante unitaria.

>[!definizione]
>La ***parametrizzazione a lunghezza d'arco*** descrive una *curva* utilizzando la sua *lunghezza percorsa* invece di un parametro arbitrario.
>Questo significa che il parametro $s$ rappresenta la **distanza percorsa lungo la curva** a partire da un punto iniziale.

Data la funzione $s(t):[a,b]\to[0,L_{C}]$ che mappa valori del parametro  in distanze.
- Consideriamo la ***funzione inversa*** $s^{-1}(s)=t$ che mappa *distanze* $s$ sulla curva in valori del parametro:

$$s^{-1}(s):[0,L_{C}]\to[a,b]$$

Per ogni valore $s$ si trova il parametro $t$ che corrisponde ad aver percorso quella distanza.

>[!tldr] Idea
>Nella ***parametrizzazione alla lunghezza d'arco***, si vuole che il parametro $t$ indichi direttamente questa distanza $s$.

Consideriamo la curva $C_{2}$ che si ottiene ***riparametrizzando*** la curva $C(t)$ e considerando $s^{-1}(s)$ come ***funzione di cambiamento del parametro***.
$$
C_{2}(s)=C(s^{-1}(s)):[a,b]\to\mathbb{R}^{2} \quad s\in[0,L_{C}]
$$
- $C_{2}\equiv C$

> Verifichiamo che con questa scelta la curva sarà percorsa con ***velocità unitaria costante***:

Usando la [[Derivate di Funzioni Elementari#Derivate di Funzioni Composte|regola della catena]]:
$$
C_{2}'(s)=C'(s^{-1}(s))\cdot\displaystyle{\frac{\text{d}}{\text{d}s}}s^{-1}(s)
$$
E per la [[Derivate di Funzioni Elementari#Derivata della Funzione Inversa|regola sulle derivate di funzioni inverse]]:
$$
\displaystyle{\frac{\text{d}}{\text{d}s}}s^{-1}(s)=\displaystyle{\frac{1}{s'(s^{-1}(s))}}=\frac{1}{\|C'(s^{-1}(s))\|}
$$
Quindi:
$$
C_{2}'(s)=\frac{C'(s^{-1}(s))}{\|C'(s^{-1}(s))\|}
$$
- Che ha **sempre** norma $1$ (*velocità unitaria*).

$$
s(t)=\int _{a}^{t} \,\|C_{2}'(\tau) \|\text{d}\tau=t-a 
$$
- Se $a=0$, al valore $s$ del *parametro* corrisponde una ***lunghezza*** $s$ sulla curva.

##### Metodo Pratico per Calcolare i Valori di Parametrizzazione Naturale
> Seleziono dei punti $P_{1},P_{2},\dots, P_{n}$

Ora voglio trovare una *approssimazione* delle ***due leggi che li collegano***.
$$
P_{i}=C(t_{i})=\begin{cases}
x_{i}=x(t_i) \\
y_{i}=y(t_i)
\end{cases}
$$
>[!abstract] Metodo della Lunghezza d'Arco Accumulata


$$
\begin{array}
\ t_{0}=0 \\
t_{i}=t_{i-1} +\|P_{i}-P_{i-1}\| = t_{i-1}+\sqrt{ (x_{i}-x_{i-1})^{2} + (y_{i}-y_{i-1})^{2}}
\end{array}
$$
- $t_{i}$ rappresenta la ***lunghezza cumulata*** dal punto iniziale fino al punto $i$.

Successivamente si ***normalizzano*** i valori dividendo per $t_{n}$ (**lunghezza totale**), così che il parametro vada in modo naturale da $0$ a $1$.


#### Applicazione alla Computer Graphics
In molte applicazioni, come il controllo del movimento di una [[View Transform|telecamera]] o di un oggetto animato, è importante che la velocità lungo la curva $C(t)$ sia *costante*.
- Se la ***parametrizzazione originale*** non garantisce una velocità costante è necessario ***riparametrizzare*** la curva rispetto all'arco.

>[!important] Importante
>Questo concetto è fondamentale per ottenere un ***movimento fluido*** e ***regolare*** nelle *animazioni* o nelle *simulazioni fisiche*.