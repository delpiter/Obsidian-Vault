## Forza Agente su un Conduttore con Corrente
---
> Preso un filo percorso da [[Circuiti/Corrente Elettrica|corrente]], vediamo che tipo di forza agisce su questo filo.

>[!tldr] Idea
>Immaginiamo di avere un filo con sezione $A$, supponiamo di avere un [[Magnetismo|campo magnetico]] $\vec{B}$ che attraversa il filo.

> Ora considero una porzione di filo di lunghezza $l$.

>[!question] Che forza sente il filo, a causa della forza delle cariche interne al filo?
>

$$
N(q\vec{v}_{d}\times\vec{B})
$$

Dove $n$ è la densità delle particelle dei portatori di carica ($N$ è la quantità totale di carica)
- $N=nAl$


La ***forza totale agente sul filo sarà***:
$$
\vec{F}=N(q\vec{v}_{d}\times\vec{B})
$$
Dato che $N=nAl$
$$
\vec{F}=nAlq\vec{v_{d}}\times \vec{B} 
$$

> Ricordiamo che:

$I=nqv_{d}A$
- Questa formula ci dice quanta carica in [[Coulomb]] al secondo si muove nel filo.

Dato che:
$$
\vec{l}\parallel \vec{v}_{d}
$$
- Il vettore direzione e lunghezza del filo è parallelo alla velocità di deriva.
> Quindi

$$
l\vec{v}_{d}=\vec{l}v_{d}
$$


>[!done] Conclusione

$$
\vec{F}=I\vec{l}\times\vec{B}
$$

>***Proprietà***

- $\vec{F}\perp$ al piano formato da $\vec{l}$ e $\vec{B}$
- $|\vec{F}|$ è proporzionale a $I$, a $l$ e a $B$
- $|\vec{F}|$ è massima per $\vec{B}\perp$ al filo, nulla per $\vec{B}\parallel$ al filo

### Spira percorsa da Corrente
> Due forze $\vec{F_{1}}$ e $\vec{F_{2}}$ generano una coppia che tende a far **ruotare** la spira rispetto all'*asse di rotazione*.

Di fatto si ha momento:
$$
\tau =IwlB\sin\theta=ISB\sin\theta
$$
![[attachements/SpiraCorrente.png|400]]

Esprimendo la superficie $S$ della spira come vettore $\vec{S}$ perpendicolare alla stessa:
$$
\vec{\tau}=I\vec{S}\times\vec{B}
$$
Il risultato vale per ***spire di qualsiasi forma***.

>[!hint] Alla base dei principi di funzionamento del Motore Elettrico

### Campo Elettrico vs Campo Magnetico
>[!info] Flusso Totale
>Il flusso totale di $\vec{B}$ attraverso qualunque superficie chiusa è sempre nullo.

$$
\Phi_{A}(\vec{E})=\oint_{A}\vec{E}\cdot\text{d}\vec{A}=\frac{Q_{tot}}{\varepsilon_{0}}\neq 0
$$
$$
\Phi_{A}(\vec{B})=\oint_{A}\vec{B}\cdot \text{d}\vec{A}=0
$$

> Le equazioni appena scritte sono le ***equazioni di Maxwell***.

#### Teorema della Circuitazione
>[!cite] Legge della Circuitazione di Ampere
>$$\oint_{\Gamma} \vec{B}\, \text{d}\vec{r}=\mu_{0} \sum I_{conc} $$

> Consideriamo un pezzo di filo percorso da [[Circuiti/Corrente Elettrica]] $I$.

La ***circuitazione*** del *campo magnetico* su un percorso chiuso è pari alla **somma algebrica** delle correnti "*concatenate*" con $\Gamma$, cioè che attraversano qualsiasi superficie di cui $\Gamma$ si il bordo.


La costante $\displaystyle\mu_{0}=\frac{1}{\varepsilon_{0}c^{2}}=4\pi\times10^{-7} \frac{Tm}{A}$ è detta "***permeabilità***" magnetica del vuoto.

>[!hint] Osservazioni

La *circuitazione* è molto simile al calcolo del [[../Lavoro e Energia/Lavoro di una Forza#Lavoro di una Forza Variabile|lavoro]].
- L'integrale lungo un percorso di un vettore.

Facendolo su un percorso chiuso, la ***Legge di Ampere*** afferma che *potrebbe non venire zero*.
- Il campo magnetico ***non è un campo*** [[../Lavoro e Energia/Lavoro di una Forza#Forze Conservative e Non Conservative|conservativo]].
##### Legge di Ampere-Maxwell
>[!question] È possibile che sia la variazione di $\vec{E}$ che generi un campo magnetico?

Consideriamo un [[Circuiti/Conduttori#Condensatore|condensatore]] a facce piane e parallele, e due superfici:
- $S_{1}$ tra i due piani.
- $S_{2}$ che taglia uno dei conduttori.

![[attachements/CircuitazioneAmpere.png]]


$S_{1}$ e $S_{2}$ hanno lo stesso "*circuito*" come **bordo**.
- Secondo la legge di ***Ampere*** con $S_{2}$ ho $\vec{B}=0$, mentre con $S_{1}$ avrei $\vec{B}\neq 0$.

In entrambi i casi la ***circuitazione*** è fatta sullo *stesso percorso*.

>[!danger] C'è una inconsistenza.

*Maxwell* la risolve.
Sia $E=\displaystyle{\frac{\sigma}{\varepsilon_{0}}}=\frac{Q}{\varepsilon_{0}A}$ il campo elettrico fra le armature.
- Il flusso del campo elettrico sarà:

$$
\phi(\vec{E})=EA=\frac{Q}{\varepsilon_{0}}
$$
>[!attention] Se stiamo caricando un condensatore
>Se nel filo passa un [[Coulomb]] al secondo (Corrente $[A]$), la carica nel condensatore aumenta di un ***Coulomb*** al secondo.

Quindi $Q=EA\varepsilon_{0}=\phi(\vec{E})\varepsilon_{0}$

Definiamo una **corrente** "*virtuale*".

$$
I_{s}=\varepsilon_{0}\displaystyle{\frac{\text{d}\phi(\vec{E})}{\text{d}t}}
$$

- Detta "***corrente di spostamento***".
Arriviamo dunque a una modifica della **legge di Ampere**.

$$
\oint \vec{B}\cdot \text{d}\vec{r}=\mu_{0}\left(I_{\text{conc}}+\varepsilon_{0}\displaystyle{\frac{\text{d}\phi(\vec{E})}{\text{d}t}}\right)
$$

##### Applicazione del Teorema di Ampere
>[!info]
>Un filo di Lunghezza $\infty$ e diametro $\approx 0$:
>- Il campo deve avere una *simmetria cilindrica*, **non può essere radiale**.
>
>>[!quote] In altre Parole
>> So che $\vec{B}$ deve avere linee ***chiuse***.
>
>Le linee sono *circonferenze centrate sul filo*.

Ora applico il ***teorema di ampere*** per circuitazione su circonferenza di raggio $r$.
$$
2\pi rB=\mu_{0}I \implies B=\frac{\mu_{0}I}{2\pi r}
$$
- $2\pi r$ è l'***integrale*** sul cerchio degli *spostamenti lungo il cerchio* (La circonferenza). 

> Detta anche ***legge di Biot e Savart*** per filo rettilineo.

###### Filo di Lunghezza $\infty$ e diametro $2a$
> Consideriamo una circonferenza $\Gamma$ di raggio $R$ perpendicolare al filo.

>[!question] Voglio trovare il valore del ***campo magnetico*** in funzione della distanza dall'asse del filo.

>[!abstract] Se $R>a$

$$
B2\pi R=\mu_{0}I\implies B=\frac{\mu_{0}I}{2\pi R}
$$

>[!missing] Se $R<a$

$$
I_{conc}=\frac{I}{\pi a^{2}}\pi R^{2}=I \frac{R^{2}}{a^{2}}
$$

In altre parole $I \frac{R^{2}}{a^{2}}$ non è altro che la corrente che passa all'*interno della circonferenza*.
- <u>Assunzione</u> $\implies$ La densità di corrente deve essere ***costante***.

$$
B=\frac{\mu_{0}I}{2\pi R} \frac{R^{2}}{a^{2}} \implies B=\frac{\mu_{0}IR}{2\pi a^{2}}
$$

###### Solenoide
> Se la lunghezza $L$ del solenoide, è $\gg R$ (raggio del solenoide), allora abbiamo un ***solenoide ideale***.

Prendiamo un *solenoide ideale* e prendiamone una sezione.
- Scegliamo come curva per l'applicazione della ***legge di Ampere*** un percorso rettangolare. 

![[attachements/SolenoideAmpere.png|400]]

Lungo il tratto $SR$ il campo magnetico è $B=0$ (*solenoide infinita ideale*).

Lungo i tratti $SP$ e $QR$:
- Il *prodotto scalare* è $0$ poiché $\vec{B}\perp \text{d}\vec{r}$

Lungo il tratto $PQ$ ho $BL$.

$$
\oint \vec{B} \text{d}\vec{r}=BL=\mu_{0}I_{conc}
$$
$I_{conc}=NI$
- Dove $N$ è il numero di volte che la s**pira ha fatto un giro completo**.

$$
\oint \vec{B} \text{d}\vec{r}=BL=\mu_{0}NI \implies B=\mu_{0} \frac{N}{L}I=\mu_{0}nI
$$
###### Toroide
> Consideriamo un toroide costruito attraverso l'avvolgimento di un conduttore.

![[attachements/ToroideAmpere.png|400]]

Scelgo come curva per l'applicazione del ***teorema di Ampere*** un cerchio di raggio $R$ che segue il *campo Magnetico*.
$$
\oint \vec{B} \, \text{d}\vec{r}=B2\pi R=\mu_{0}NI\implies B=\frac{\mu_{0}Ni}{2\pi R}
$$

>[!hint] Similitudine
>La formula del campo magnetico è ***uguale*** alla formula per un filo sottile di lunghezza infinita.

Basta far scorrere una corrente $N$ volte quella del filo.
- A volte **non è possibile** far scorrere $1000A$ di corrente in un filo, quindi si sceglie di far scorrere $1A$ in un toroide con $1000$ *avvolgimenti*.
###### Forza tra due Conduttori rettilinei e paralleli
$$
B_{2}=\mu_{0}
\frac{I_{2}}{2\pi R}
$$
> Quindi:
- $F_{1}=I_{1}lB_{2}\implies F=\frac{\mu_{0}I_{1}I_{2}}{2\pi R} l$

Si attirano o si respingono in ***base alla direzione della corrente***.

## Equazioni di Maxwell
---
### Campo Elettrico
>[[Flusso di un Campo Vettoriale#Teorema di Gauss|Teorema di Gauss]]

$$
\phi(\vec{E})= \frac{\sum Q^{\text{int}}}{\varepsilon_{0}}
$$

>[[Induzione#Legge dell'Induzione|Legge di Faraday Lenz]]

$$
\oint  \vec{E}\cdot\, \text{d}l=-\displaystyle{\frac{\text{d}\phi(\vec{B})}{\text{d}t}} 
$$

### Campo Magnetico
>[!info] Teorema di Gauss

$$
\phi(\vec{B})= 0
$$
>[[#Legge di Ampere-Maxwell|!help]]

$$
\oint \vec{B}\cdot \text{d}\vec{l}=\mu_{0}\left(I_{\text{conc}}+\varepsilon_{0}\displaystyle{\frac{\text{d}\phi(\vec{E})}{\text{d}t}}\right)
$$