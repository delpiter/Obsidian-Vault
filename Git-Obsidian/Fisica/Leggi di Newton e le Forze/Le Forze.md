## Diagramma del Corpo Libero
---
>Nell'applicare le [[Leggi di Newton]], uno strumento fondamentale è il ***diagramma del corpo libero***.

>[!tldr] Idea
>Si tratta di un disegno in cui sono ***riportate tutte le forze che agiscono su un corpo***.

Il diagramma consente di "*visualizzare*" le **interazioni dell'ambiente esterno** con il **corpo** e di determinare il modo in cui si calcolerà la somma delle forze esterne.

![[DiagrammaCorpoLibero.png|400]]

## Forza Peso
---
>[!info]
>Ogni corpo lasciato libero di cadere presenta una accelerazione $g$ ***diretta verso il basso***.
>In termini di [[Leggi di Newton#Seconda Legge di Newton|forza]], possiamo dire il corpo è soggetto ad una **forza** di modulo $mg$, *diretta verso il basso*.
>Chiameremo tale forza: ***Forza Normale***.

Prendendo come [[Trasformazioni di Galileo|sistema di riferimento]] l'asse $y$ verticale verso l'alto:
$$
\vec{P}=m\vec{g} \implies \vec{g}=-g\hat{j}
$$

## Forze di Tensione
---
>[!abstract] Fune Ideale
>Chiamiamo ***fune ideale*** una fune molto sottile di *massa* $m\approx 0$ *trascurabile*, *perfettamente flessibile* e *intensibile*.

![[ForzaTensione.png]]
 
>[!question] Posto un asse $x$ diretto verso destra, cosa possiamo dire sulla somma delle forze sulla fune?

$$
\sum F_{x}=F-T=m_{\text{fune}}a_{x}=0
$$
Possiamo dire ciò perché:
- $m_{\text{fune}}=0$

> Quindi $T=F$

>[!quote] In altre Parole
>La ***fune ideale*** non fa altro che *trasmettere la forza* per tutta la sua lunghezza, eventualmente cambiandone la direzione.

## Forza Normale
---
>[!example] Esempio
>Un libro appoggiato sul tavolo sta fermo, dunque la sua ***accelerazione*** è nulla.

In base alla [[Leggi di Newton#Seconda Legge di Newton|seconda legge di Newton]] la somma delle forze agenti su di esso sarà anch'essa nulla.

![[ForzaNormale.png|500]]
$$
\vec{a}=0\implies \sum \vec{F}=0
$$

> Fissiamo un asse $y$ verticale diretto verso l'alto.

Il peso $\vec{P}=-mg\hat{j}$ sarà dunque bilanciato da una forza che il ***tavolo esercita sul libro***.
- "*Normale*" ha significato di ***perpendicolare***.

>[!warning] Nota Bene
>$\vec{P}$ e $\vec{N}$ **NON** formano una coppia [[Leggi di Newton#Terza Legge di Newton|azione reazione]].
>- $\vec{P}$ è la forza gravitazionale che *esercita la terra sul libro*.
>	- Esiste una reazione: la forza gravitazionale che il libro esercita sulla terra
>- $\vec{N}$ è la forza che il tavolo *esercita sul libro*, reazione alla forza che esercita il libro.

### Piano Inclinato
>[!example] Esempio di Riferimento
>Un corpo di massa $m=18.0kg$ è poggiato su un piano, privo di #addLink attrito, *inclinato* di $\theta=27^\circ$ rispetto all'orizzontale.
>Il corpo è tenuto da una fune che sale parallela al piano.

Scelgo un asse $x$ lungo il *piano*, con verso nella salita, e un asse $y$ perpendicolare, diretto verso l'alto.

![[PianoInclinato.png]]

La forza può essere scomposta nelle sue ***componenti cartesiane***.
$$
\vec{P}=-P_{||}\hat{i}-P_{\perp}\hat{j}=-(mg\sin(\alpha))\hat{i}-(mg\cos(\alpha))\hat{j}
$$
La tensione della fune è *parallela* al piano, quindi all'asse $x$
- La forza normale è *perpendicolare* al piano quindi parallela all'asse $y$.
$$
\vec{T}=T\hat{i},\quad \vec{N}=N\hat{j}
$$

>L'accelerazione del corpo è ***nulla***: le componenti cartesiane dell'accelerazione sono ***nulle***.

Di conseguenza sappiamo che la somma delle forze è nulla:
$$
\begin{cases}
0=ma_{x}=\sum F_{x}=T-mg\sin\alpha \\
0=ma_{y}=\sum F_{y}=N-mg\cos\alpha
\end{cases}\implies \begin{cases}
T=mg\sin\alpha \\
N=mg\cos\alpha
\end{cases}
$$

>In forma *vettoriale*

$$
\vec{T}=(mg\sin\alpha)\hat{i}\quad \vec{N}=(mg\cos\alpha)\hat{j}
$$
>[!question] Se taglio la corda?

La tensione della fune viene a mancare.
- Avrò una componente lungo $x$ dell'*accelerazione* diversa da zero.

Lungo l'asse $y$ la *forza normale* continuerà a **bilanciare** il peso del corpo.
$$
\begin{cases}
ma_{x}=\sum F_{x}=-mg\sin\alpha \\
0=ma_{y}=\sum F_{y}=N-mg\cos\alpha
\end{cases}\implies
\begin{cases}
a_{x}=-g\sin\alpha \\
N=mg\cos\alpha
\end{cases}
$$

>[!example] Ulteriore Esempio
>Per i due corpi connessi da una fune come nella figura seguente si calcoli l'**accelerazione** e la **tensione** della fune.

![[PianoInlcinato2.png]]

> Scegliamo ***sistemi di riferimento diversi*** per ciascun blocco.

La fune è una ***fune ideale***:
- $|\vec{T}_{M}|=|\vec{T}_{m}|$
- $|\vec{a}_{M}|=|\vec{a}_{m}|$

Ad ogni spostamento del blocco $M$ *lungo il piano*, corrisponde uno spostamento della stessa entità di $m$ in *verticale*

>Tali relazioni diventano:

$$
\begin{cases}
T_{Mx}=T_{my}\equiv T \\
a_{Mx}=-a_{my}\equiv a
\end{cases}
$$
Dove:
- $T$ è il ***modulo della tensione*** della fune.
- $a$ è il ***modulo dell'accelerazione*** del blocco $M$.

Il sistema ha solo un grado di libertà:
Il moto può essere ***definito da una sola accelerazione*** determinata dalle *forze parallele* al piano agenti su $M$ e da quelle *verticali agenti* su $m$.

$$
\begin{cases}
\vec{N}=Mg\cos\alpha\hat{j} \\
\vec{a}_{M}=\displaystyle{\frac{m-M\sin\alpha}{m+M}}g\hat{i} \\
\vec{T}=\displaystyle{\frac{Mmg}{M+m}}(1+\sin\alpha)\hat{i}
\end{cases}\implies \text{SdR 1}
$$
Con l'aggiunta di:
$$
\vec{a}_{m}=-\displaystyle{\frac{m-M\sin\alpha}{M+m}}g\hat{j} \implies\text{SdR 2}
$$

## Forze di Attrito
---
>[!info]
>Un corpo che striscia su un piano, ad un certo punto si *ferma*.
>Ne concludiamo che ha ***subito una forza***.
>>[!cite] Attrito
>>Chiamiamo tale forza ***forza di attrito***.

> Applico una forza crescente nel tempo per misurare la forza di attrito

Finché il ***corpo è fermo***, la forza di attrito sarà *uguale in modulo* e *opposta in verso* alla forza esterna applicata.

>[!tip] Attrito Statico
>Chiamiamo ***forza di attrito statico***, la forza presente quando il corpo è in *quiete*.
>>[!help] Valore Massimo
>>L'***attrito statico*** è dunque caratterizzato dall'avere un valore massimo.
>>Tale valore ***non dipende dall'area di contatto*** ed è ***proporzionale alla forza normale***.
>
>$$F_{s}\leq \mu_{s}N$$
>$\mu_{s}$ è detto *coefficiente di attrito statico*
>- È il rapporto tra la *massima intensità* della forza di attrito statico possibile e la forza normale.

All'improvviso, superato un certo valore della forza applicata, ***il corpo si mette in moto*** e quindi la forza di attrito ora è minore di quella esterna e non dipende più da essa.

>[!abstract] Attrito Dinamico
>Chiamiamo ***forza di attrito dinamico***, la forza presente quando il corpo è in *moto*.
>>[!quote] Coefficiente
>>Anche l'attrito dinamico segue le stesse due leggi citate sopra.
>>Si introduce un analogo ***coefficiente di attrito dinamico***
>
>$$F_{k}=\mu_{k}N$$

![[Attrito.png]]

> Nella maggioranza dei casi si ha $\mu_{s}> \mu_{k}$

### Esempio
>[!example] Problema
>Ponendo un oggetto su un *piano inclinato* e aumentando progressivamente l'**angolo** che questo forma con l'orizzontale.
>Troviamo un angolo $\theta_{0}$ a partire dal quale il ***corpo scivola***.

> Risolvendo il problema è possibile determinare il ***coefficiente di attrito statico*** $\mu_{s}$

![[AttritoStatico.png]]

Un attimo prima che il corpo scivoli abbiamo: $\sum F=0$
- Detto $x$ un asse parallelo al piano, avremo: $\sum F_{x}=-mg\sin\theta+F_{s}=0$

> Per l'angolo $\theta_{0}$ ho raggiunto la ***massima forza di attrito possibile*** $F_{s}^{\text{max}}$.

$$
\begin{array}
\ -mg\sin\theta_{0}+F_{s}^{\text{max}}=0 \\
-mg\sin\theta_{0}+\mu_{s}N=0 \\
-mg\sin\theta_{0}+\mu_{s}mg\cos\theta_{0}=0
\end{array}\implies\mu_{s}=\tan\theta_{0}
$$

>[!abstract] Analogamente
>Si potrebbe determinare $\mu_{k}$
>Detto $\theta_{k}$ l'angolo che annulla l'accelerazione, avremo:
>$$\mu_{k}=\tan\theta_{k}$$

## Forza Elastica
---
>[!info]
>Una *molla* esercita una forza di richiamo: può **tirare** se la **allunghiamo** o può **spingere** se la comprimiamo.
>Ha quindi la tendenza a riportarsi ad una sua ***lunghezza naturale***.
>>[!quote] La forza esercitata dalla molla è proporzionale all'allungamento/compressione

> Caratterizziamo la molla con una lunghezza a riposo $l_{0}$ e con una costante elastica $k$

$$
F=-k(l-l_{0})
$$
- $k$ determina la proporzionalità tra la *forza espressa* e l'*allungamento*.

>[!help] $k$ è ***negativo***:

- Se *aumentiamo* $l$ oltre la lunghezza di riposo la molla "*tira*" (allungamento **positivo**, forza **negativa**).
- Se *diminuiamo* $l$ oltre la lunghezza di riposo la molla "*spinge*" (allungamento **negativo**, forza **positiva**).

### Moto Armonico
> Scelgo un sistema di riferimento con asse $x$ tale che $x=0$ nella ***posizione di riposo***.

L'espressione della forza diventa:
$$
F=-kx
$$
>[!abstract] Riformuliamo secondo la $II^a$ Legge di Newton.

$$
ma(t)=-kx(t) \implies m \displaystyle{\frac{\text{d}^2x}{\text{d}t^2}}=-kx
$$
$$
\displaystyle{\frac{\text{d}^2x}{\text{d}t^2}}=-\frac{k}{m}x
$$
Abbiamo una ***equazione differenziale*** che è soddisfatta da una $f(t)$ tale che la sua derivata seconda è uguale a sé stessa, a meno di un *fattore moltiplicativo negativo*.

>[!done] Seno e Coseno

$$
\begin{array}
x(t)=A\cos(\omega t+\phi) \\
\displaystyle{\frac{\text{d}x}{\text{d}t}}(t)=-\omega A\sin(\omega t+\phi) \\
\displaystyle{\frac{\text{d}^2x}{\text{d}t^2}}(t)=-\omega^2 A\cos(\omega t+\phi)=-\omega^2 x(t)
\end{array}
$$
Vediamo che la $x(t)$ scelta soddisfa l'equazione differenziale quando $\omega^2=\displaystyle{\frac{k}{m}}$.

>[!info]
>Un sistema che soddisfa l'equazione differenziale della forza elastica, e ha soluzioni armoniche è detto ***oscillatore armonico***.

![[MotoArmonico.png]]

Vediamo che il periodo della funzione è:
$$
T=\frac{2\pi}{\omega}=2\pi\sqrt{ \frac{m}{k} }\quad \nu=\frac{1}{2\pi}\sqrt{ \frac{k}{m} }
$$
Dove  $\omega$ è detta ***pulsazione***, $T$ è detto ***periodo***, $\nu$ è detta ***frequenza***.

## Il Pendolo Semplice
---
>Scriviamo la somma delle forze lungo l'asse $x$ scelto come in figura.

$$
\sum F_{x}=-mg\sin\theta=ma\implies a=-g\sin\theta
$$
![[Pendolo.png]]

Dato che la massa $m$ si muove su un arco di circonferenza di raggio $l$, la sua *accelerazione tangenziale* sarà pari al **raggio** per l'**accelerazione angolare**.
$$
a=l\alpha=l\displaystyle{\frac{\text{d}^2\theta}{\text{d}t^2}}
$$
- Quindi abbiamo l'equazione differenziale:
$$
\displaystyle{\frac{\text{d}^2\theta}{\text{d}t^2}}=-\frac{g}{l}\sin\theta
$$
>[!abstract] Osservazione
>Nell'ipotesi di ***piccole oscillazioni***, ovvero che la massima escursione angolare $\theta$ sia piccola, possiamo approssimare $\sin\theta\simeq\theta$, ottenendo:
>$$\displaystyle{\frac{\text{d}^2\theta}{\text{d}t^2}}=-\frac{g}{l}\theta=-\omega^2\theta$$

Si tratta di un'equazione differenziale di un ***oscillatore armonico*** con **pulsazione** e **periodo**.

$$
\omega=\sqrt{ \frac{g}{l} }\qquad T=\frac{2\pi}{\omega}=2\pi\sqrt{  \frac{l}{g}}
$$

> Concetto usato per ricavare misure precise dell' #addLink accelerazione gravitazionale.