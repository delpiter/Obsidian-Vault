## Physical Layer
---
### Codifica Manchester
>[!tldr] Idea
>Il segnale di clock del trasmettitore e il segnale dei dati vengono combinati per ***garantire una transizione per ogni*** `bit`.

Due convenzioni opposte:
- Nella prima il `bit` $1$ è rappresentato con una ***transizione al semiperiodo*** tra il segnale *alto* e il segnale *basso* ($0$ da basso a alto).
- La seconda afferma l'**esatto opposto**.

>[!done] Pro
- Si elimina il problema delle *lunghe sequenze di* `bit` con **uguale valore**.

### Attenuazione
> Qualunque mezzo trasmissivo degrada il segnale [[Elettromagnetismo|elettromagnetico]] durante lo spostamento.

>[!cite] Definizione
>L'***attenuazione*** misura il degrado, misurando la perdita di potenza nel segnale.
>- Si misura in $dB/km$.

$$
A_{dB}=10\cdot \log_{10}\left( \frac{P_{T}}{P_{R}} \right) = \alpha\sqrt{ f_{MHz} }L
$$
L'*attenuazione* cresce esponenzialmente con:
- La **lunghezza** del collegamento.
- La radice della **frequenza** del segnale.

>[!todo] In breve
>È molto difficile portare **lontano** segnali ad *alta frequenza*.
## Cavi per la Trasmissione
---
>[!info] Notazione
>$x \text{ Base } y$
>Dove
>- $x$ indica che il segnale può viaggiare per $x\cdot 100m$.
>- $y$ indica la velocità in $Mbps$.
### Cavi Coassiali
> Un cavo coassiale è formato da:
- Un filo conduttore centrale (***core***).
- Racchiuso in una *guaina isolante*.
- A sua volta avvolta in un *foglio metallico* (***calza***).
- Ulteriormente rivestito da una **guaina isolante**.

![[Coax.png]]

- Più è grande $D$ più il cavo è ***costoso e performante***.

>[!fail] Cavo ormai vecchio e poco usato

>[!caution] Thick Coax
>$10 \text{ Base }5$
> Cavo coassiale a $50\ohm$.
- Serviva per connettere le [[Routing Globale|backbone]].

>[!summary] Thin Coax
>$10 \text{ Base }2$
> Cavo coassiale a $50\ohm$, diametro molto più piccolo (*circa la metà*).
- Usato per raggiungere le *prese al muro*.

### Doppini
> Il **doppino** è un cavo elettrico formato da **due fili conduttori** avvolti da una *guaina isolante* e attorcigliati per ridurre rumore esterno.

>[!abstract] Unshielded Twisted Pair
> $10 \text{ Base }T$
> Quattro coppie di fili ***attorcigliati***.

Connettore usato: `RJ45` (*Registered Jack*) o `RJ11`.
> Tipologie di cavo:
- ***Straight Through***: permette il collegamento tra la porta di uno *switch* e un `PC`
- ***Crossover***: permette il collegamento tra le porte di **due switch** o di **due** `PC`.

>[!bug] Shielded Twisted Pair e Foiled Twisted Pair
>> `STP` cavo in cui ogni coppia di fili è ***attorcigliata e schermata***.
>
>> `FTP` è un cavo `UTP` avvolto in un foglio metallico.

>[!failure] Evoluzioni Successive
>Fast Ethernet a $100$`Mbit/s` (`802.3u`).

> $100 \text{ Base } T4$

> $100 \text{ Base } TX$
 
> $100 \text{ Base } FX$: ***Fibra ottica multimodo***.

>[!done] Gigabit (`802.3z`)

> $1000 \text{ Base } SX$

> $1000 \text{ Base } LX$

> $1000 \text{ Base } CX$

> $1000 \text{ Base } T$

#### Livelli di Qualità
> Vengono definiti livelli di qualità detti ***categorie***.

>[!hint] Standardizzate da `Cat 1` a `Cat 7`.

### Fibra Ottica
>[!tldr] Idea
>Utilizzare la ***luce*** per trasportare l'informazione.

La luce si propaga in linea retta all'interno di un *mezzo trasparente omogeneo* (**densità costante**) e *isotropo* (comportamento della luce **uguale in tutte le direzioni**).

>[!done] Elevato aumento delle prestazioni con aumento minimo dei costi

>[!fail] Problema
- La fibra ottica è più difficile da giuntare.

> ***Giuntare la fibra ottica*** significa unire due fibre per estendere una linea o riparare un danno, usando principalmente la tecnica a fusione.

Si possono avere giunti ***stabili*** e ***contemporanei***.

>[!question] Dove usare la fibra ottica?
- La fibra ottica viene tipicamente usata per i ***collegamenti a lunga distanza***.

#### Mantenimento del Segnale
> Il segnale viene mantenuto tramite l'***amplificatore ottico***.

>[!hint] Info
>L'amplificatore mantiene il segnale a livello ottico.
>In un segnale [[Multiplexing#Wavelength Division Multiplexing|WDM]] *tutti i canali vengono amplificati*.

È comunque necessario combattere gli effetti di ***dispersione e non linearità***.
>[!EDFA] EDFA
>Un `EDFA` (*Erbium-Doped Fiber Amplifier*) è un ***amplificatore ottico*** utilizzato nelle reti in fibra per aumentare la potenza del segnale senza convertirlo in elettrico.

È un tratto di fibra ottica **drogata con ioni di erbio** ($Er^{3+}$).  
- Quando la fibra viene “pompata” con un laser, gli ioni si eccitano e **amplificano direttamente il segnale ottico** che passa attraverso di essa.
#### Struttura di una Fibra Ottica
>[!info]
>La *trasmissione della luce* attraverso la fibra è basata sul fenomeno della ***riflessione totale interna***.
>>[!definizione] Riflessione
>>Il fenomeno della riflessione si presenta quando il *raggio di luce* incide **obliquamente** sull'interfaccia di separazione tra due mezzi.

![[FibreOptic.png]]

Per la fibra ottica i due mezzi diversi sono ***due tipi di pasta vetrosa***:
- Uno interno (*core*) con un indice di rifrazione $n_{1}$.
- Uno esterno (*cladding*) con un indice di rifrazione più basso rispetto al core $n_{2}< n_{1}$

>[!question] Quale Vetro?
> L'intensità del raggio diminuisce *mentre attraversa il vetro*.

- Vetro comune ($3cm$).
- Vetro di alta qualità ($3m$).
- Fibra ottica di media qualità ($15km$).

##### Funzionamento
![[FibreOpticReflection.png]]

Affinché il raggio luminoso rimanga entro il core (***riflessione totale***), è necessario che venga introdotto con un certo angolo
- L'insieme di questi angoli forma una **superficie tridimensionale** detta *acceptance cone*.

>[!done] In Range
- Un raggio introdotto nella fibra all'***interno del cono*** andrà ad incidere l'interfaccia tra *core* e *cladding* con un angolo maggiore dell'angolo limite ($\theta_{L}$) verrà totalmente riflesso.

>[!fail] Out of Range
- Un raggio introdotto al di fuori del cono inciderà l'interfaccia con un angolo inferiore all'angolo limite e verrà rifratto e si ***disperderà nel cladding***.


> Per la ***trasmissione***:

>[!abstract] On Off Keying
>Una sorgente di luce (*LED* o *Laser*) genera impulsi luminosi che si ***propagano per grandi distanze*** e a grandissima velocità.

Un ricevitore (*fotodiodo*) riceve gli impulsi.

#### La fibra ottica nella Rete di Accesso
> Classificate in base alla ***localizzazione dell'interfaccia***

>[!todo] Fibre to the Exchange
>L'***interfaccia elettro/ottica*** (`EOI`) è in una centrale di distribuzione.

>[!caution] Fibre to the Building
> L'`EOI` è alla base di un **palazzo**.

>[!info] Fibre to the Home
>L'`EOI` è direttamente nelle **case degli utilizzatori**.