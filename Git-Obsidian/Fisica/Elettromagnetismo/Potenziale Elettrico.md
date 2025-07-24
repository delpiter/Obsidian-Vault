## Energia Potenziale Elettrica
---
> Idea molto simile alla [[Energia Potenziale Gravitazionale]].

>[!definizione]
>L'***energia potenziale elettrica*** è l'energia immagazzinata da una carica $q$ posta in un [[Campi Elettrostatici|campo]] $\vec{E}$.

>[!info] Lavoro della forza Elettrica
>Possiamo affermare che se la carica generatrice è ferma, risulta che il [[Lavoro di una Forza|lavoro]] della [[Coulomb|forza elettrica]] ***non dipende dal percorso***.

Consideriamo due [[Elettromagnetismo#Cariche Elettriche|cariche elettriche]] $Q$ e $q$, di cui:
- $Q$ ferma e non necessariamente puntiforme.
- $q_{0}$ puntiforme e *soggetta a spostamento* tra due punti $A$ e $B$.

Consideriamo il lavoro
$$
\mathscr{L}=\int _{A}^B \vec{F}\cdot \text{d}\vec{l}=q_{0}\int _{A}^B \vec{E}\cdot\, \text{d}\vec{l}
$$

-  $q_{0}$ è costante quindi può "*uscire*" dall'integrale.

Il campo è ***radiale***, quindi la traiettoria è fatta di tratti infinitamente piccoli:
- O radiali
- O perpendicolari (Da ignorare perché $\cos\left( \frac{\pi}{2} \right)=0$)

$$
\mathscr{L}=q_{0}\int _{r_{a}}^{r_{b}} \displaystyle{\frac{q}{4 \pi\varepsilon_{0}r^2}\hat{r}}\cdot \, (\hat{r}\text{d}r)=\frac{q_{0}q}{4\pi\varepsilon_{0}}\int _{r_{a}}^{r_{b}} \, \frac{\text{d}r}{r^{2}}  
$$

>[!done] Contano solo i tratti radiali

$$
\mathscr{L}=\frac{q_{0}q}{4\pi\varepsilon_{0}}\left[ \frac{1}{r_{a}}-\frac{1}{r_{b}} \right] 
$$
Quindi il lavoro vale:
$$
\mathscr{L}=\int _{a}^b \vec{F\cdot} \, \text{d}\vec{l}= \frac{q_{0}q}{4\pi\varepsilon_{0}}\left( \frac{1}{r_{a}}-\frac{1}{r_{b}} \right)
$$

>[!abstract] Per qualsiasi Traiettoria
>La [[Coulomb#Legge di Coulomb|forza elettrica]] è una [[Lavoro di una Forza#Forze Conservative e Non Conservative|forza conservativa]].

>[!caution] Differenza di Energia Potenziale
>$$U_{b}-U_{a}=-\int _{a}^b\vec{F}\cdot \, \text{d}\vec{l}=\frac{q_{0}q}{4\pi\varepsilon_{0}}\left( \frac{1}{r_{b}}-\frac{1}{r_{a}} \right) $$

> Come per l'[[Energia Potenziale Gravitazionale]], scelgo

$$
U(r\to \infty)=0\implies U(r)=\frac{q_{0}q}{4\pi\varepsilon_{0}r}
$$
Ovvero:
$$
U(r)=-\int _{\infty}^r \vec{F}\cdot\, \text{d}\vec{l} 
$$
Se ho più cariche, per il [[Campi Elettrostatici#Principio di Sovrapposizione|principio di sovrapposizione]]:
$$
\vec{F}=q_{0}\sum_{i}\vec{E}_{i}
$$
- ***Quindi***
$$
U=\frac{q_{0}}{4\pi\varepsilon_{0}}\sum_{i} \frac{q_{i}}{r_{i}}
$$
### Potenziale Elettrico
>[!quote]
>"Ho una [[Elettromagnetismo#Cariche Elettriche|carica elettrica]] $q$ e questa genera un ***potenziale elettrostatico*** in tutto l'universo".
>Il ***potenziale elettrico*** è un valore associato alla *posizione* di una carica $q_{0}$ in un campo $\vec{E}$.

$$
V=\frac{U}{q_{0}}
$$
Quindi
$$
V=\frac{1}{4\pi\varepsilon_{0}}\sum_{i} \frac{q_{i}}{r_{i}}
$$
> Per una ***singola carica puntiforme***:

$$
V=\frac{q}{4\pi\varepsilon_{0}r}
$$
> Per una ***distribuzione di cariche***:

$$
V=\frac{1}{4\pi\varepsilon_{0}}\int  \, \frac{\text{d}q}{r} 
$$

>[!abstract] Unità di Misura
>$[V]=\text{volt}=\frac{N}{C}m$
>$[E]=\frac{V}{m}$

#### Differenza di Potenziale
>[!caution] DDP
>Tra due punti $a$ e $b$ c'è una ***differenza di potenziale***:
>$$V_{b}-V_{a}=\frac{U_{b}-U_{a}}{q_{0}}\qquad V_{b}-V_{a}=-\int _{a}^b \vec{E}\cdot\, \text{d}\vec{l} $$

> In **generale**:

$$
E_{x}=\displaystyle-\frac{\partial V }{ \partial x }\qquad E_{y}=\displaystyle-\frac{ \partial V }{ \partial y }\qquad
E_{z}=\displaystyle-\frac{ \partial V }{ \partial z } 
$$
*Quindi*
$$
\vec{E}=-\vec{\nabla}V
$$
>[!cite] A parole
>Il ***campo elettrico*** è $-$ il gradiente di $V$

##### Superfici Equipotenziali
> Le ***superfici equipotenziali*** (sulle quali si trova lo stesso valore di $V$), sono perpendicolari a $\vec{E}$ in ogni punto.

![[SuperficiEquipotenziali.png|250]]

- Del tutto analogo all'uso di [[Funzioni di due Variabili Reali#Curva di Livello|ISOIPSE]].
## Elettrostatica e Conduttori
---
> In un conduttore le [[Elettromagnetismo#Cariche Elettriche|cariche]] sono mobili.

>[!info] Elettrostatica
>Se le cariche sono in una situazione di ***equilibrio elettrostatico***, il [[Campi Elettrostatici|campo elettrico]] $\vec{E}$ <u>dentro</u> il *conduttore* sarà nullo.
>$$\vec{E}=0$$
>- Altrimenti le cariche si muoverebbero.
>

Ora applicando la [[Flusso di un Campo Vettoriale#Teorema di Gauss|legge di Gauss]], per qualsiasi superficie interna, risulterà sempre $\rho=0$.
- La carica elettrica può trovarsi ***solo sulla superficie esterna***.

Vicino alla superficie il campo $\vec{E}$ deve essere $\perp$ alla superficie
- Se non fosse, avrei uno *spostamento di cariche*.
- $E_{t}=0$ ***sulla superficie***.

> Considero la [[Flusso di un Campo Vettoriale#Lamina Piana Infinitamente Estesa|superficie gaussiana]], un cilindro con le basi localmente parallele alla superficie

$$E_{\perp}=\frac{\sigma}{\varepsilon_{0}}
$$

>[!info] Sfera
>L'interno di un conduttore è tutto allo stesso potenziale.
>Ad esempio per la sfera uniformemente carica di raggio $R$:
>- **Costante** all'*interno*
>- $\frac{1}{r}$ all'*esterno*

![[CaricaConduttore.png|500]]

>[!hint] Osservazione
>Si vede che $\vec{E}=0$ e $V=\text{cost}$ vale anche nelle cavità.
>- Se non fosse cosi, avrei
>$$\int _{a}^b\vec{E}\cdot \, \text{d}\vec{l}\neq0\implies V_{b}-V_{a}\neq 0 $$
>
>>[!cite] Schermatura
>>Un conduttore che racchiude una regione di spazio fornisce una ***schermatura elettrostatica***.

### Calcolo del Potenziale
#### Piano Uniformemente Carico
> Campo $\vec{E}$:

$$
\vec{E}=\pm \frac{\sigma}{2\varepsilon_{0}}\hat{k}
$$
- $+$ o $-$ a seconda del semispazio in cui mi trovo

>[!question] Troviamo il *D.D.P* tra un punto $P$ e un punto $p_{0}$ posto sul piano

$$
-\text{d}V=\vec{E}\cdot\text{d}\vec{r}=E_{z}\text{d}z=\pm \frac{\sigma}{2\varepsilon_{0}}
$$
$$
V(z)-V(0)=\int _{z}^0 \left(\pm \frac{\sigma}{2\varepsilon_{0}}\right)\, \text{d}z=\pm \frac{\sigma}{2\varepsilon_{0}}z=-\frac{\sigma}{2\varepsilon_{0}} \mid z\mid
$$
- $|z|$ è la distanza di $P$ dal piano

Presi due punti qualsiasi $A$ e $B$ avrò:
$$
V_{A}-V_{B}=\frac{\sigma}{2\varepsilon_{0}}(|z_{B}|-|z_{A}|)=\frac{\sigma}{2\varepsilon_{0}}(d_{B}-d_{A})
$$

#### Doppio Piano
> Sappiamo che $\vec{E}$ va dal piano caricato positivamente ($\oplus$) a quello negativo ($\ominus$).

$$
E=\frac{\sigma}{\varepsilon_{0}}
$$
>[!info]
>Detta $d$ la ***distanza*** tra i piani:
>$$V_{\oplus}-V_{\ominus}=\frac{|\sigma|}{\varepsilon_{0}}d$$

Calcolando il potenziale all'interno, e ricordando che all'esterno $\vec{E}=0\implies V=\text{ cost}$
- Indicando con $C$ una costante arbitraria.

$$
\begin{cases}
V(z)=- \displaystyle\frac{|\sigma|}{\varepsilon_{0}}z+c \quad 0\leq z\leq d\\
V(z)=C\equiv V_{\oplus} \quad z<0 \\
V(z)=- \displaystyle\frac{|\sigma|}{\varepsilon_{0}}z+c\quad z>d
\end{cases}
$$
![[DoppioPiano.png]]

#### Calcolo del Potenziale per Cariche a Simmetria Sferica
> Usiamo le espressioni per $\vec{E}$ già trovate e calcoliamo l'espressione per $V(r)$ con $V(r\to \infty)=0$:

>[!help] Guscio sferico di Raggio $R$

$$
\begin{cases}
V = \dfrac{1}{4 \pi \varepsilon_0} \dfrac{Q}{r} & \text{for } r > R \\
V = \dfrac{1}{4 \pi \varepsilon_0} \dfrac{Q}{R} & \text{for } r \leq R
\end{cases}
$$

>[!caution] Sfera Uniformemente Carica
$$
\begin{array}{ll}
V = \dfrac{1}{4 \pi \varepsilon_0} \dfrac{Q}{r} & \text{for } r > R \\
V = \dfrac{1}{4 \pi \varepsilon_0} \dfrac{Q}{2R} \left( 3 - \dfrac{r^2}{R^2} \right) & \text{for } r \leq R
\end{array}
$$

> In entrambi i casi:
- Il potenziale all'esterno della sfera è uguale a quello del ***campo*** [[Coulomb#Legge di Coulomb|Columbiano]] di una carica puntiforme *posta al centro della simmetria*.

Per $r<R$ dipende dalla distribuzione.
- Nel caso del guscio vuoto, $V=\text{cost} \iff\vec{E}=0$

### Energia Potenziale e Moto di Particelle Cariche
> Dato che $U\equiv qV$ 

$$
U_{B}-U_{A}=q(V_{B}-V_{A})=-\mathscr{L}_{AB}
$$
>[!tip] Posso usare la conservazione energia meccanica

$$
\frac{1}{2}mv^2+qV=\text{cost}
$$
>[!cite] Elettrovolt
>Un elettrone che parte da fermo in una differenza di potenziale di $1V$.
>$$\frac{1}{2}mv^2=e\Delta V=1.6\times 10^{-19}J$$
>- Tale valore di energia è detto ***elettrovolt***.