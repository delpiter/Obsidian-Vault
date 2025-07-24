>[!info]
> C'è una differenza nell'effetto *prodotto da una* [[Leggi di Newton#Legge|forza]] dello **stesso modulo** applicato ad un oggetto nelle seguenti situazioni.

![[Lavoro.png]]

La differenza sta nell'***angolo*** che la forza forma con lo spostamento del corpo.

## Lavoro di una Forza Costante
---
>[!definizione]
>Definiamo allora la quantità ***lavoro per una forza costante*** nel modo seguente:
>$$\mathscr{L}=\vec{F}\cdot\Delta\vec{r}=|\vec{F}|\cdot|\Delta\vec{r}|\cos\theta$$
>[[4 - Prodotto Scalare|Prodotto Scalare]].

![[Lavoro2.png]]

>[!hint] Alcuni Commenti

- Lo *spostamento* è quello del ***punto di applicazione della forza***.
- Se non c'è spostamento il lavoro è ***nullo***.
- Se la forza è *perpendicolare* allo spostamento, il lavoro è ***nullo***.

Il lavoro ha un *segno*:
- Se la proiezione della forza lungo lo spostamento ha *verso opposto* allo spostamento il *lavoro è negativo* (angolo $\theta$ ***convesso***).

>[!help] Unità di Misura
>L'unità di misura è il ***joule***
>$$J=[\mathscr{L}]=Nm=kgm^2s^{-2}$$

Il *lavoro* è un trasferimento di energia
- Verso il sistema se $\mathscr{L}>0$
- Dal sistema se $\mathscr{L}<0$

Il risultato del lavoro è un ***cambiamento della quantità di energia*** immagazzinata dal sistema.

## Lavoro di una Forza Variabile
---
> La definizione di lavoro di una forza costante si estende al caso di una ***forza variabile***.

Considerando la **somma** dei valori infinitesimi corrispondenti a *spostamenti infinitesimi* lungo la traiettoria:
 $$\mathscr{L}=\int ^{\vec{r}_{f}}_{\vec{r}_{i}} \vec{F}\, d\vec{r} $$
## Forze Conservative e Non Conservative
---
> Consideriamo un corpo che possa passare da una quota $h$ ad una quota $0$ in due modi:

![[ForzeConservative.png]]

- Piano inclinato in *assenza di attrito*.

>[!tip] Caso moto verticale
>Avremo:
>- Uno **spostamento** di modulo $\Delta r=h$.
>- Una **forza** peso $mg$.
>- Spostamento e forza sono *paralleli* e *concordi*.

$$
\mathscr{L}_{\text{vert}}=mgh\cos(0)=mgh
$$

>[!abstract] Caso [[Le Forze#Piano Inclinato|piano inclinato]]
>Avremo:
>- Uno spostamento di modulo $\displaystyle\Delta r=\frac{h}{\sin\theta}$
>- L'angolo formato dalla forza peso e il vettore spostamento: $\displaystyle{\frac{\pi}{2}}-\theta$

$$
\mathscr{L}_{\text{obliq}}=mg \frac{h}{\sin\theta}\cos\left( \frac{\pi}{2}-\theta \right)=mgh \frac{\sin\theta}{\sin\theta}=mgh
$$

>[!done] Il lavoro fatto dalla forza peso è lo stesso per i due percorsi
>Contano solo l'***altezza iniziale*** e ***quella finale***.

>[!definizione] Forze Conservative
>Chiamiamo le forze il cui **lavoro** *non dipende* dal percorso ma solo dalle posizioni iniziale e finale ***forze conservative***.
>>[!cite] Definizione
>>Il lavoro compiuto da una ***forza conservativa*** agente su un punto materiale che si muove tra due punti qualsiasi *non dipende dal percorso*.
>><u>Oppure</u>
>>Il lavoro compiuto da una ***forza conservativa*** agente su un punto materiale che descrive un *percorso chiuso* è **nullo**.

Le due definizioni sono *equivalenti*:
> Dimostrazione

$$
\oint_{\gamma} \vec{F} \cdot \text{d}\vec{r} =
\int_{A}^{B} \vec{F} \cdot \text{d}\vec{r}_{\gamma_1} +
\int_{B}^{A} \vec{F} \cdot \text{d}\vec{r}_{\gamma_2} =
\int_{A}^{B} \vec{F} \cdot \text{d}\vec{r}_{\gamma_1} -
\int_{A}^{B} \vec{F} \cdot \text{d}\vec{r}_{\gamma_2}
$$
Quindi:
$$
\oint_{\gamma}\vec{F}\cdot\text{d}\vec{r}=0\iff \int^{B}_{A} \vec{F} \cdot \text{d}\vec{r}_{\gamma_1} =
\int^{B}_{A} \vec{F} \cdot \text{d}\vec{r}_{\gamma_2}
$$

---

> Consideriamo la forza di [[Le Forze#Forze di Attrito|attrito dinamico]].

>[!note] Problema
>Un *punto materiale* poggiato sul piano che si sposta dalla posizione $A$ alla posizione $B$.

![[ForzeNonConservative.png]]

La *forza di attrito* è sempre opposta alla direzione del moto e ha ***modulo costante***.
- Il lavoro fatto da essa sulle due traiettorie $S_{1}$ e $S_{2}$ sarà diverso.

$$
|\mathscr{L}_{S_{1}}|< |\mathscr{L}_{S_{2}}|,\quad \mathscr{L}_{S_{1}}<0,\quad\mathscr{L}_{S_{2}}<0
$$
>[!definizione] Forze non Conservative
>Chiamiamo le forze il cui **lavoro** *dipende* anche dal percorso, ***forze non conservative***.
