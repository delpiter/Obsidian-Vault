## Principio di Sovrapposizione
---
>[!tldr] Idea 
>Se una carica $q$ risente di una forza a causa di molte [[Elettromagnetismo#Cariche Elettriche|cariche]] $(q_{1},q_{2},q_{3},\dots,q_{n})$, tale forza è la ***somma vettoriale*** delle singole forze $(\vec{F}_{1},\vec{F}_{2},\vec{F}_{3},\dots,\vec{F}_{n})$ determinate dalla [[Coulomb#Legge di Coulomb|legge di Coulomb]].
>$$\vec{F}=\sum\vec{F}_{i}$$
>>[!quote]
>>L'interazione tra due cariche è ***indipendente*** dalle altre cariche eventualmente presenti.

Unendo un oggetto di carica $q_{1}$ con un oggetto di carica $q_{2}$:
- Ottengo un oggetto di carica $q=q_{1}+q_{2}$ (*somma algebrica*)

>[!hint] Additività delle Cariche

## Campo Elettrostatico
---
>[!definizione] Campo
>Un ***campo*** è una *grandezza fisica* che può essere **definita in ogni punto dello spazio**.
>>[!example] Esempi
>>Temperatura dell'aria in una stanza $T(x,y,z)$
>>- Magari varia anche nel tempo: $T(x,y,z,t)$
>>
>>Esistono anche ***campi vettoriali*** come quello della [[../Gravitazione/Legge di Gravitazione|gravitazione]].

^32aa5b

---
Una particella **carica** $q_{0}$ ("*carica di prova*" o "*esploratrice*") sente l'effetto di **altre cariche** quando sta nel punto $P$.

>[!check] Campo Elettrico
>Definisco ***Campo Elettrico*** in $P$ la forza su di essa esercitata divisa per la sua carica.
>$$\vec{E}=\displaystyle{\frac{\vec{F}}{q_{0}}}$$

> $q_{0}$ sente la forza $\vec{F}=\sum\vec{F}_{i}$.
- Somma di tutte le cariche.

Ciascuna delle forze delle cariche è:
- $\vec{F_{i}}\propto q_{0}\qquad \left( \displaystyle{\frac{q_{0}q_{i}}{4\pi\varepsilon_{0}r^2_{i}}} \right)$

>[!hint] Il campo elettrico non dipende dalla carica $q_{0}$

$q_{0}$ deve essere piccola per non perturbare la *distribuzione spaziale delle altre cariche*.

>[!info]
>Il ***campo elettrostatico*** $\vec{E}$ prodotto da un gruppo di particelle cariche dipende da:
>1. Il *valore della carica* di ciascuna particella.
>2. Come sono disposte nello spazio: "*Distribuzione di carica*".
>3. In quale punto lo misuro.

Dato che $\vec{E}$ non dipende dalla carica usata per la misura è una ***proprietà dello spazio*** creata dalle cariche elettriche.

>[!abstract] Proprietà
>- $\vec{E}$ è un campo vettoriale.
>- Vale il [[#Principio di Sovrapposizione]].
>- $[E]=\frac{N}{C}$
>- $\vec{F}=q\vec{E}$ la forza cui è soggetta una particella di carica $q$ quando soggetta ad un campo $\vec{E}$
>	- Il segno di $q$ definisce il *verso della forza*.

#### Calcolo di $\vec{E}$ per cariche Puntiformi
> Una carica sente la forza: $\vec{F}=\displaystyle{\frac{1}{4\pi\varepsilon_{0}}}\cdot \displaystyle{\frac{qq_{0}}{r^2}\hat{r}}$

$$
\implies \vec{E} = \displaystyle{\frac{q}{4\pi\varepsilon_{0}r^2}\hat{r}} 
$$
- $\mid \vec{E}\mid\propto q$
- $\mid \vec{E}\mid\propto \frac{1}{r^2}$
- $\vec{E}$ ha verso "*esterno*" se $q>0$, "*interno*" se $q<0$.

>[!tl;dr] Se ho più cariche
>Vale la ***legge di sovrapposizione***.
>$$\vec{F}=\frac{1}{4\pi\varepsilon_{0}}\sum_{i} \displaystyle{\frac{q_{i}q_{0}}{r_{i}^2}}\implies \vec{E}=\frac{1}{4\pi\varepsilon_{0}}\sum_{i} \frac{q_{i}}{r_{i}^2}\hat{r}_{i}$$

## Linee di Forza
---
> Le linee di forza forniscono una idea intuitiva della ***forma e intensità del campo elettrico***.

>[!abstract] Proprietà
>1. $\vec{E}$ è *tangente* alla linea in ogni punto.
>2. Le linee indicano la *direzione* di $\vec{E}$.
>3. Le frecce indicano la *direzione del verso*.
>4. La densità delle linee è *proporzionale* a $\mid \vec{E}\mid$

![[attachements/linee-di-forza.png]]

## Moto delle Cariche in un Campo Uniforme
---
> Siamo in una regione di spazio dove è stato generato un *campo uniforme*.

$$
\vec{F} =q\vec{E} \implies m\vec{a}=q\vec{E}\implies \vec{a}=\frac{q\vec{E}}{m}
$$
>[!abstract] Carica inizialmente in Quiete
> Se $\vec{E}=\vec{E}\hat{i}$ e $\vec{r}(0)=(0,0,0)$
> $$a_{x}=\frac{qE}{m}\quad v_{x}=\frac{qE}{m}t\quad x(t)=\frac{1}{2} \frac{qe}{m}t^2 \quad v_{x}^2= \frac{2qe}{m}x$$

>[!caution] Carica con $\vec{v_{0}}\perp\vec{E}$: Moto Parabolico
>Metto $\vec{v_{0}}=v_{0}\hat{j}$ e $\vec{E}=E\hat{j}$

- $\displaystyle a_{y}=\frac{qE}{m}\quad a_{x}=a_{z}=0$
- $\displaystyle v_{y}= \frac{qE}{m}t\quad v_{x}=v_{0} \quad v_{z}=0$
- $\displaystyle y=\frac{1}{2}\left( \frac{qE}{m} \right)t^2\quad x=v_{0}t\quad z=0$

> ***Traiettoria***:

$$
y=\frac{1}{2} \frac{qE}{mv_{0}^2}x^2
$$
### Esperimento di Millikan
>[!info] Obbiettivo
>Cercare di misurare la *quantità di carica minima*.


>[!tldr] Idea
>Prendere oggetti ***molto piccoli*** e ***caricarli molto*** poco e metterli in un campo elettrico per misurare *quanta carica hanno*.

![[attachements/MillikanExperiment.png|400]]
- *Apparato dell'esperimento*

> ***Funzionamento***

- Le goccioline di olio si [[Elettromagnetismo#Cariche Elettriche|caricano]] per strofino *uscendo dal nebulizzatore*.
	- Le goccioline *cadono a velocità costante* ($mg=6\pi\eta rv_{g}$) a causa dell'attrito.
	- $F=6\pi\eta rv$
- Alcune goccioline entrano attraverso il piccolo buco nel ***campo elettrico*** opportuno.
	-  Satura la velocità $v_{e}: qE-mg=6\pi\eta rv_{e}$

Divido tra loro le due espressioni:
$$
\frac{v_{g}}{v_{e}}=\frac{mg}{qE-mg}\implies q=\frac{mg}{E}\left( \frac{v_{e}}{v_{g}}+1 \right)
$$
>[!hint] Osservazioni
>$q$ sono **multipli** di una *stessa unità*.