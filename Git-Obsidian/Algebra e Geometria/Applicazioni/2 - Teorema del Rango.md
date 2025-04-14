## Teorema
---
>[!check] Enunciato
>Sia $f:V\to U$ un'***applicazione lineare***
><u>Allora</u>
>$$\text{dim}(\mathrm{ker}f)+\text{dim}(\mathrm{Im}f)=\text{dim}(V)$$

### Dimostrazione
>Sia $v_{1},\dots,v_{d}$ una base di $\mathrm{ker}f$

Completiamola con una base di $V$
- Ciò è possibile poiché $\mathrm{ker}f$ è un [[1 - Applicazioni Lineari#Nucleo|sottospazio vettoriale]]

>$v_{1},\dots,v_{d},v_{d+1},\dots,v_{n}$

- Sappiamo già, per definizione di [[1 - Applicazioni Lineari#Nucleo|nucleo]] che:
$$
f(v_{1})=\underline{0},\dots,f(v_{d})=\underline{0}
$$

Ora basta mostrare che i vettori $f(v_{d+1}),\dots,f(v_{n})$ ($u_{d+1},\dots,u_{n}$) sono una [[2 - Campi e Spazi Vettoriali#Base|base]] di $\mathrm{Im}f$
- Poiché $v_{1},\dots,v_{n}$ sono una base di $V$ per il [[3 - Teoremi su Spazi Vettoriali#Teorema delle Coordinate|teorema delle Coordinate]]

$$
\exists!a_{1},\dots,a_{n}\in\mathbb{K}:V =a_{1}v_{1}+\dots+a_{n}v_{n}
$$
Poiché $f$ è [[1 - Applicazioni Lineari#Applicazione Lineare|lineare]] $f(v)=f(a_{1},v_{1}+\dots,a_{n}v_{n})=a_{1}f(v_{1})+\dots+a_{d}f(v_{d})+a_{d+1}f(v_{d+1})+\dots+a_{n}f(v_{n})$

$$
\cancel{ a_{1}f(v_{1}) }+\cancel{ \dots }+\cancel{ a_{d}f(v_{d}) }+a_{d+1}f(v_{d+1})+\dots+a_{n}f(v_{n})
$$

Dunque
$$
\forall u\in\mathrm{Im}f, \exists! a_{d+1},\dots,a_{n}\in\mathbb{K}:u=f(v)=a_{d+1}f(v_{d+1})+\dots+a_{n}f(v_{n})
$$
Di conseguenza, per il [[3 - Teoremi su Spazi Vettoriali#Teorema delle Coordinate|teorema delle Coordinate]]
- $f(v_{d+1}),\dots,f(v_{n})$ è una ***base dell'immagine***

>[!done] Quindi $\text{dim}(\mathrm{ker}f)=d,\quad\text{dim}(V)=n,\quad\text{dim}(\mathrm{Im}f)=n-d$

### Esempio
#### Riprendendo [[1 - Applicazioni Lineari#Es 1 - Nucleo|l'esempio 1]] 
>$f:\mathbb{R}^2\to\mathbb{R}^2, f(x,y)\mapsto (x+y,2x+2y)$

Abbiamo visto che $\mathrm{ker}f=\{ (t,-t),t\in\mathbb{R} \}$
- Quindi, applicando il teorema appena enunciato

$$
\text{dim}(\mathrm{ker}f) = 1, \text{dim}(\mathrm{Im}f)=1, \text{dim} (V)=1+1 = \text{dim}(\mathbb{R}^2) = 2
$$

>[!abstract] Ripercorriamo la dimostrazione

Prendiamo una base di $\mathrm{ker}f, v_{1}=(1,-1)$
- Completiamo a una base di $\mathbb{R}^2\implies v_{1}=(1,-1),v_{2}=(1,0)$

Calcoliamo $f(v_{1}) =(0,0)=\underline{0},f(v_{2})=(1,2)$
- $f(v_{2})$ è una base di $\mathrm{Im}f$ perché ogni $(s,2s)\in\mathrm{Im}f$ si scrive come $s\cdot(1,2)$

#### Riprendendo [[1 - Applicazioni Lineari#Es 2 - Nucleo|l'esempio 2]]
>Abbiamo mostrato che $\mathrm{ker}f=\{ \underline{0} \}$

Quindi $\text{dim}\mathrm{Im}f=\text{dim}\mathbb{R}^2-\text{dim}\mathrm{ker}f =2-0=2$
Quindi $\mathrm{Im}f=\mathbb{R}^2\implies f$ è suriettiva

>[!tldr] Il teorema ci dimezza l'esercizio

## Conseguenze del Teorema del Rango
---
>[!info] 1
>Se $f:V\to U$ è [[Git-Obsidian/Analisi/Funzioni/Introduzione Funzioni#Funzione Iniettiva|iniettiva]], allora
>$$\text{dim}(U)\geq \text{dim}(V)$$
><u>Infatti</u>
>$$\text{dim}(U) \underbrace{ \geq }_{ \mathrm{Im}f\subseteq U } \text{dim}(\mathrm{Im}f)= \text{dim}(V)-\underbrace{ \text{dim}(\mathrm{ker}f) }_{ 0 }$$

>[!info] 2
>Se $f:V\to U$ è [[Git-Obsidian/Analisi/Funzioni/Introduzione Funzioni#Funzione Surriettiva|suriettiva]], allora
>$$\text{dim}(U)\leq \text{dim}(V)$$
><u>Infatti</u>
>$$\text{dim}(U) = \text{dim}(\mathrm{Im}f) = \text{dim}(V)-\text{dim}(\mathrm{ker}f)\leq\text{dim} (V)$$

>[!info] 2
>Se $f:V\to U$ è [[Git-Obsidian/Analisi/Funzioni/Introduzione Funzioni#Funzione Biunivoca|biunivoca]], allora
>$$\text{dim}(U) = \text{dim}(V)$$
><u>Infatti</u>
>In fatti per i due punti precedenti valgono $\geq$ e $\leq$

>[!info] 4
>Se $\text{dim}(V)=\text{dim}(U)$ allora
>$$f:V\to U$$
>È iniettiva $\iff$ è suriettiva ($\iff$ è biunivoca)
><u>Infatti</u>
>$f$ è iniettiva $\iff\text{dim}\mathrm{ker}f=0$
>Per il ***teorema del Rango*** $\text{dim}(V)=\text{dim}(\mathrm{Im}f) \iff f$ è suriettiva 

