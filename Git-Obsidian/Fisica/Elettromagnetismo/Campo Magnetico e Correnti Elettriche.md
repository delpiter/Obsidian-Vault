## Forza Agente su un Conduttore con Corrente
---
> Preso un filo percorso da [[Corrente Elettrica|corrente]], vediamo che tipo di forza agisce su questo filo.

>[!tldr] Idea
>Immaginiamo di avere un filo con sezione $A$, supponiamo di avere un [[Magnetismo|campo magnetico]] $\vec{B}$ che attraversa il filo.

> Ora considero una porzione di filo di lunghezza $l$.

>[!question] Che forza sente il filo, a causa della forza delle cariche interne al filo?
>

$$
N(q\vec{v}_{d}\times\vec{B})
$$

Dove $N$ è la densità delle particelle dei portatori di carica
- $N=nAl$

La ***forza agente sul filo sarà***:
$$
\vec{F}=N(q\vec{v}_{d}\times\vec{B})
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
![[SpiraCorrente.png|400]]

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

> Consideriamo un pezzo di filo percorso da [[Corrente Elettrica]] $I$.

La ***circuitazione*** del *campo magnetico* su un percorso chiuso è pari alla **somma algebrica** delle correnti "*concatenate*" con $\Gamma$, cioè che attraversano qualsiasi superficie di cui $\Gamma$ si il bordo.

![[CircuitazioneAmpere.png]]

La costante $\displaystyle\mu_{0}=\frac{1}{\varepsilon_{0}C^{2}}=4\pi\times10^{-7} \frac{Tm}{A}$ è detta "***permeabilità***" magnetica del vuoto.

##### Applicazione del Teorema di Ampere
>[!info]
>Un filo di Lunghezza $\infty$ e diametro $\approx 0$:
>- Il campo deve avere una *simmetria cilindrica*, **non può essere radiale**.
>
>>[!quote] In altre Parole
>> So che v$\vec{B}$ deve avere linee ***chiuse***.
>
>Le linee sono *circonferenze centrate sul filo*.

Ora applico il ***teorema di ampere*** per circuitazione su circonferenza di raggio $r$.
$$
2\pi rB=\mu_{0}I \implies B=\frac{\mu_{0}I}{2\pi r}
$$
> Detta anche ***legge di Biot e Savart*** per filo rettilineo.

###### Filo di Lunghezza $\infty$ e diametro $2a$
> Sia consideriamo una circonferenza $\Gamma$ di raggio $R$ perpendicolare al filo.

>[!question] Voglio trovare il valore del ***campo magnetico*** in funzione della distanza dall'asse del filo.

>[!abstract] Se $R>a$

$$
B_{2}\pi R=\mu_{0}I\implies B=\frac{\mu_{0}I}{2\pi R}
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

![[SolenoideAmpere.png|400]]

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

![[ToroideAmpere.png|400]]

Scelgo come curva per l'applicazione del ***teorema di Ampere*** un cerchio di raggio $R$ che segue il *campo Magnetico*.
$$
\oint \vec{B} \, \text{d}\vec{r}=B2\pi R=\mu_{0}NI\implies B=\frac{\mu_{0}Ni}{2\pi R}
$$

###### Forza tra due Conduttori rettilinei e paralleli
$$
B_{2}=\mu_{0}
\frac{I_{2}}{2\pi R}
$$
> Quindi:
- $F_{1}=I_{1}lB_{2}\implies F=\frac{\mu_{0}I_{1}I_{2}}{2\pi R} l$

Si attirano o si respingono in ***base alla direzione della corrente***.

