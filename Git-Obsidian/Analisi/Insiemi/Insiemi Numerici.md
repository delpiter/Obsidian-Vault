[[Concetti Base#Insieme |Insiemi]]

## Tipologie
- - -
### Numeri Naturali
- Tutti i numeri ottenuti aggiungendo di volta in volta una unità, partendo da 0

$$\mathbb{N} = \{0,1,2,...\}$$

Operazioni possibili:
- Somma
- Prodotto
Mancanza:
- Non è possibile fare sottrazioni, mancano gli **opposti**
### Numeri Interi
- Corrispondono all'insieme ottenuto unendo i numeri **naturali e i numeri negativi**

$$\mathbb{Z} = \{0,-1,1,-2,2,...\}$$
Mancanza:
- Mancano gli **inversi**
### Numeri Razionali
- Tutti i numeri che si ottengono dal rapporto di numeri interi

$$\mathbb{Q} = \{\displaystyle{\frac{m}{p}|m,\;p \in \mathbb{Z},\;p\neq0}\}$$
Mancanza:
- Non è possibile fare i [[Limiti|limiti]]
### Numeri Reali
- Numeri descritti mediante una rappresentazione decimale limitata o illimitata, periodica o non periodica
- Sono tutti i numeri razionali e irrazionali
- Ha una proprietà caratteristica
	- ***La Completezza***

$$\mathbb{R}$$
Mancanze:
- Alcune equazioni ancora non hanno soluzione ($x^2+1=0$)
### [[Numeri Complessi]]
$$
\mathbb{C} = \{ a+ib, a,b\in\mathbb{R} \}
$$
#### Teorema Fondamentale dell'Algebra
Ogni equazione polinomiale a coefficienti in $\mathbb{R}$ o $\mathbb{C}$ ha soluzioni in $\mathbb{C}$

### Classe e Classe di Resto
>[!info] Definizione Classe
>Dato $n\in\mathbb{N}, n\geq 2$, dato $a \in \mathbb{Z}$, definisco:
>$$\overline{a}=\{ b\in\mathbb{Z}:b\equiv a(n) \}$$
>E lo chiamo classe di $a$

>[!info] Definizione Classi di Resto
>Sia $\mathbb{Z}_{n}=\{ \overline{0},\overline{1},\dots,\overline{n-1} \}$,
>Chiamo $\mathbb{Z}_{n}$ *insieme delle classi di* [[Definizioni_Analisi#Numeri Congrui a Modulo $n$|resto modulo]] $n$

>[!done] Fatto

$\mathbb{Z}_{n}$ è un [[2 - Campi e Spazi Vettoriali#Campo|campo]] $\Leftrightarrow$ $n$ è primo
## Insiemi Separati
- - -
- Siano $A$ e $B \subseteq \mathbb{R}$, diciamo che $A$ e $B$ sono **separati** se
$$\forall \;a \in A, \forall \;b \in B$$
- Si ha $a \leq b$
## Assioma di completezza
- - -
- L'insieme $\mathbb{R}$ soddisfa l'assioma  di completezza ($\mathbb{R}$ è completo), cioè
$$\forall \; A,B \subseteq \mathbb{R} \; separati$$
$$\exists \;c \in \mathbb{R}: a\leq c \leq b$$
## Cardinalità
- - -
- La cardinalità rappresenta il numero di elementi all'interno di un insieme
- Nella teoria degli insiemi un insieme viene detto numerabile se:
	- I suoi elementi sono in numero finito
	- Possono essere messi in [[Git-Obsidian/Definizioni/Definizioni_Analisi#Corrispondenza biunivoca|corrispondenza biunivoca]] con i numeri naturali
#### Lista di insiemi numerabili
- $\mathbb{N}$
- $\mathbb{Z}$
- $\mathbb{Q}$
- $\mathbb{R}$ ***NON È NUMERABILE***
###### Osservazione
$\mathbb{Q}$ è denso in $\mathbb{R}$ cioè
$$\forall \; x,y \in \mathbb{R},\;x<y,\; \exists \;q \in \mathbb{Q}, \exists d \in \mathbb{R}\setminus\mathbb{Q}:x<q<y, x<d<y $$

## Massimo e Minimo di $A \subseteq B$
- - -
Sia $A$ incluso in $\mathbb{R}$ e $A \neq \varnothing$, diciamo che
- $M \in \mathbb{R}$ è massimo di $A$ se
	- $M \in A$
	- $M \geq a, \forall a \in A$
- $m \in \mathbb{R}$ è minimo di $A$ se
	- $m \in A$
	- $m \leq a, \forall a \in A$
##### Osservazione
Sia $A \subseteq \mathbb{R}$ se $A$ ammette un massimo o un minimo allora esso  unico
###### Dimostrazione
Siano $M_1$ e $M_2$ massimi di $A$
- Allora per definizione di massimo si ha $M_1\geq M_2$
- Ma anche $M_2\geq M_1$ 
- Perciò $M_1=M_2$
## Maggiorante e minorante
- - -
- Elementi più grandi o più piccoli dell'insieme di partenza
	- Non è sempre detto che ci siano
	- Possono essere più di uno a differenza del massimo e del minimo
### Maggiorante
> Sia $A\subseteq \mathbb{R}$ diciamo che $\mu \in \mathbb{R}$  **Maggiorante** $A$ se
> $$\mu \geq a\;\;\;\; \forall a\in A$$
### Minorante
> Sia $A\subseteq \mathbb{R}$ diciamo che $\lambda \in \mathbb{R}$  **Minorante** $A$ se
> $$\lambda \leq a\;\;\;\; \forall a\in A$$
## Insiemi Limitati
- - -
### Superiore
>Se un insieme $A$ ammette elementi maggioranti si dice che tale insieme è limitato superiormente
##### Teorema
- Sia $A \subseteq \mathbb{R}$ allora l'insieme dei maggioranti ammette sempre un minimio
	- Viene chiamato estremo superiore di $A$ ($supA$)

### Inferiore
>Se un insieme $A$ ammette elementi minoranti si dice che tale insieme è limitato inferiormente
##### Teorema
- Sia $A \subseteq \mathbb{R}$ allora l'insieme dei minoranti ammette sempre un massimo
	- Viene chiamato estremo inferiore di $A$ ($supA$)

### Insieme limitato
> Se un insieme ammette sia elementi minoranti che maggioranti



#### Teorema
>Sia $A \subseteq \mathbb{R}$ allora l'insieme dei maggioranti ammette sempre un minimo
>>Viene chiamato estremo superiore di $A$ o $supA$

Analogamente

>Sia $A \subseteq \mathbb{R}$ allora l'insieme dei minoranti ammette sempre un massimo
>>Viene chiamato estremo inferiore di $A$ o $infA$

- Per convenzione se $A$ non è limitato superiormente poniamo $supA =+\infty$
- Per convenzione se $A$ non è limitato superiormente poniamo $supA =-\infty$