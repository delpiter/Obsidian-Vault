>[!info]
>Il ***flusso*** di un [[Campi Elettrostatici#^32aa5b|campo]] attraverso una *superficie* è una grandezza scalare *proporzionale* al numero di linee di campo che attraversano tale superficie.

> Il ***Flusso*** è:
1. Proporzionale alla *densità delle linee*.
![[DensitaLinee.png]]
2. Dipende dall'*orientazione della superficie* rispetto al campo.
![[OrientamentoSuperficie.png]]
3. Proporzionale all'*area della superficie*.
![[GrandezzaArea.png]]

>[!definizione] Flusso in Termini Matematici
>$$\phi_{A}(\vec{E})=\vec{E}\cdot(A\hat{n})\equiv\vec{E}\cdot\vec{A}=EA\cos\theta$$
>- $\vec{A}\equiv A\hat{n}$ è un ***vettore normale*** alla superficie il cui modulo è pari all'area.
> 
>>[!attention] Nota bene
>>Questa definizione è valida se la *superficie è piana* e il ***campo è uniforme*** su tutta la superficie.

![[Flusso.jpg|500]]

> Casi:
- Campo *Perpendicolare* al piano: $\phi=E\Delta S$
- Campo *Parallelo* al piano: $\phi=0$
- Tutti gli altri campi: $\phi=E\Delta S\cos\theta$

## Flusso di un campo non Uniforme
---
>[!info]
>Se il [[Campi Elettrostatici#^32aa5b|campo]] **non** è *uniforme* e/o la superficie **non** è piana, il flusso è definito come un [[Calcolo Integrale|integrale]] sulla *superficie*.
>$$\phi_{A}(\vec{E})=\int _{A} \,\vec{E}\cdot \text{d}\vec{A}=\int _{A}\vec{E}\cdot\hat{n} \, \text{d}A  $$

![[FlussoCampoNonUniforme.png]]

> Se la superficie è ***chiusa***:
- Si prende convenzionalmente $\text{d}\vec{A}$ diretto *verso l'esterno*.
- Si utilizza per l'integrazione il simbolo $\displaystyle\oint$:  $\phi_{A}(\vec{E})=\displaystyle\oint_{A}\vec{E}\cdot\text{d}\vec{A}$

### Attraverso una Sfera
>[!hint] Osservazione
>Dato che $\vec{E}$ è **radiale**, $\text{d}\vec{A}=\hat{n}\text{d}A$ è **sempre** parallelo ad $\vec{E}$, visto che $A$ è una *sfera*.

![[FlussoSfera.png]]

$$
\vec{E}\cdot\hat{n} =E=\frac{Q}{4\pi\varepsilon_{0}r^2}
$$
$$
\phi_{A}(\vec{E})=\oint_{A}\vec{E}\cdot\hat{n}\text{d}A=E\oint_{A}\text{d}A=\frac{Q}{4\pi\varepsilon_{0}r^2}\cdot 4\pi r^2=\frac{Q}{\varepsilon_{0}}
$$

>[!warning] Nota Bene
>**Non c'è dipendenza** dal *raggio* della sfera.

## Teorema di Gauss
---
>[!check] Teorema
>Il ***flusso*** del [[Campi Elettrostatici|campo elettrico]] uscente da una *qualunque superficie chiusa* contenente una [[Elettromagnetismo#Cariche Elettriche|carica]] puntiforme $Q$ vale $\displaystyle\frac{Q}{\varepsilon_{0}}$, come ottenuto per la sfera centrata sulla carica.
>>[!cite] In termini formali
>>$$\phi_{A}(\vec{E})=\oint_{A}\vec{E}\cdot\text{d}\vec{A}=\frac{Q}{\varepsilon_{0}}$$

>Consideriamo una superficie sferica esterna ad $A$ e centrata sulla carica $Q$.

![[TeoremaGauss.png|400]]

Ad ogni *porzione della superficie* $A$ corrisponde una ***porzione della sfera*** attraversata dallo stesso flusso.
- Il flusso totale attraverso la superficie $A$ è quindi ***uguale al flusso attraverso la sfera***.

>[!check] Teorema
>Il flusso del campo elettrico uscente da una *qualunque superficie* **chiusa** contenente un *qualsiasi insieme di cariche* la cui somma algebrica è $Q_{tot}$, vale:
>$$\phi_{A}=\oint_{A}\vec{E}\text{d}\vec{A}=\frac{Q_{tot}}{\varepsilon_{0}}$$

>[!attention] Nota Bene
>Per qualsiasi superficie, ***coni di angolo solido*** intercettano un numero <u>*pari*</u> di volte la superficie se la carica è **esterna**, un numero <u>*dispari*</u> di volte se è **interna**.

### Applicazioni della legge di Gauss
> Per sistemi con certe caratteristiche di simmetria diventa semplice il calcolo del flusso $\phi(\vec{E})$.

>[!info] Densità di Carica
>> ***Volume***
>
>$$\rho=\displaystyle{\frac{\text{d}q}{\text{d}v}}$$
>> ***Superficie***
>
>$$\sigma=\displaystyle{\frac{\text{d}q}{\text{d}s}}$$
>> ***Lineare***
>
>$$\lambda=\displaystyle{\frac{\text{d}q}{\text{d}l}}$$
#### Lamina Piana Infinitamente Estesa
>Densità **superficiale** di carica $\sigma$ uniforme.

Lontano dai bordi $\vec{E}$ sarà $\perp$ alla superficie, verso l'esterno se $\sigma>0$
L'*intensità* la **stessa** sui due lati.
- Scelgo $S$ cilindrica con asse $\perp$ alla superficie.
![[LaminaPiana.png]]

- *Superficie laterale*: $\vec{E}\perp \hat{n}_{lati}\implies \phi_{elati}=0$
- *Basi*: $\vec{E}\parallel \hat{n}_{base}\implies\phi_{b}=ES+ES$, dove $S$ è l'area della base del cilindro

$$
\phi=\phi_{lati}+\phi_{base}=2ES
$$
>[!done] Carica
>La carica all'interno sarà $q=\sigma S$, quindi per la ***legge di Gauss***, $\phi=\frac{q}{\varepsilon_{0}}$ avrò:
>$$2ES=\frac{\sigma S}{\varepsilon_{0}}\implies E=\frac{|\sigma|}{2\varepsilon_{0}}$$


>[!hint] Osservazione
>Notare che coincide con il risultato del disco carico ***quando molto vicino***.

### Due Piani Infinitamente Estesi

- $\downarrow\vec{E}_{-}\quad \uparrow\vec{E}_{+}\implies\vec{E}=0$
- $\uparrow\vec{E}_{-}\quad \uparrow\vec{E}_{+}\implies\vec{E}=\displaystyle\frac{\sigma}{\varepsilon_{0}}\hat{j}$
- $\uparrow\vec{E}_{-}\quad \downarrow\vec{E}_{+}\implies\vec{E}=0$

![[Piani.png]]

>[!cite] Ricavare la [[Coulomb#Legge di Coulomb|Legge di Coulomb]]
>Data una carica puntiforme, scelgo: $\phi(\vec{E})=4\pi r^2E=\frac{q}{\varepsilon_{0}}$
>$S$ è una sfera centrata sulla carica. (raggio $r$) $\vec{E}\parallel \hat{n}$ in ***ogni punto***.

$$
E=\frac{1}{4\pi\varepsilon_{0}}\cdot \frac{q}{r^2}\implies F=q_{2}E=\frac{qq_{2}}{4\pi\varepsilon_{0}r^2}
$$

### Filo Molto Lungo
>Densità **lineare** di carica $\lambda$ uniforme.

![[FiloLungo.png]]

- $\lambda= \displaystyle{\frac{q}{l}}$
Lontano dalle estremità il campo sarà ***radiale***.
- $S\equiv$ Cilindro coassiale al filo

$$
E=\frac{1}{2\pi\varepsilon_{0}}\cdot \frac{\lambda}{r}\implies E=\frac{1}{2\pi l\varepsilon_{0}}\cdot \frac{q}{r}
$$

### Sfera Uniformemente Carica
>[!tldr]
>Sfera uniformemente carica (*positivamente*).
>> ***2 Casi***:
>
>- Carica in **tutto il volume**.
>- Carica **solo sulla superficie**.

![[CampoSfera.png|500]]

- $\rho=\displaystyle\frac{p}{v}=\frac{3q}{4\pi R^2}$
##### Sfera $S$ carica in tutto il volume
- Per simmetria il campo sarà ***radiale***.

>[!check] $r>R$

$$4\pi r^2E=\frac{q}{\varepsilon_{0}} \implies E=\frac{1}{4\pi\varepsilon_{0}} \cdot \frac{q}{r^2}$$
> Come una ***carica puntiforme al centro***.

>[!caution] $r<R$

$$
4\pi r^2E=\frac{1}{\varepsilon_{0}}\frac{4}{3}\pi r^3
\rho \implies E=\frac{1}{3\varepsilon_{0}}\rho r=\frac{1}{4\pi\varepsilon_{0}}\cdot \frac{qr}{R^3}
$$

![[GraficoSferaCarica.png]]


##### Sfera $S$ cava
>[!check] $r>R$

$$E=\frac{1}{4\pi\varepsilon_{0}}\cdot \frac{q}{r^2}$$
> Come una ***carica puntiforme***.

>[!caution] $r<R$

$$E=0$$
![[SferaCaricaSuperficie.png]]

- Perché $4\pi r^2E=\displaystyle\frac{q}{\varepsilon_{0}}=0$

> Il flusso $\phi(\vec{E})$ è sempre zero.