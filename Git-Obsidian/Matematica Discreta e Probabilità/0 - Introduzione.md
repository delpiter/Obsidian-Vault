## Definizioni
---
>[!Def] Calcolo Combinatorio
>Il ***Calcolo Combinatorio*** ha il compito di *contare* quanti elementi contiene un insieme dato

#### Esempio
>[!question] 100 Lanci di Moneta: Quante sono le sequenze possibili con 55 testa e 45 croci?


>[!tip] Statistica Descrittiva
>La ***Statistica Descrittiva*** ha il compito di *presentare* i dati raccolti in una certa indagine in modo sintetico, comunicativo e rappresentativo

#### Esempio
>[!info] Campione
>100 Lanci di Moneta

> *Se ottengo 55 testa e 45 croce presento il dato con un grafico simile*
```mermaid
pie

    "Testa" : 55

    "Croce" : 45
```


>[!definizione] Probabilità
>La ***Probabilità*** studia le possibilità che possa *realizzarsi* un certo evento *casuale o aleatorio*
>- È una ***scienza esatta***

#### Esempio
>[!question] Qual è la probabilità che su 100 lanci di moneta otteniamo 55 testa e 45 croce?

>[!tip] Statistica Inferenziale
>La ***Statistica Inferenziale*** ha il compito di dedurre caratteristiche di una certa popolazione partendo dalla conoscenza di un certo campione scelto a caso

#### Esempio
> Su 100 lanci abbiamo 55 testa e 45 croce

>[!question] Con questo dato, qual è la probabilità che la moneta sia truccata?

## Insiemistica
---
### Cardinalità
>[!Definizione]
>Se $A$ è un insieme finito con $n$ elementi scriviamo: $|A|=n$ e diciamo che $A$ ha ***cardinalità*** $n$

Diciamo che 2 insiemi $A$ e $B$ hanno la stessa cardinalità se esiste una ***corrispondenza biunivoca*** tra essi
#### Esempio
>$A=\mathbb{N}=\{ 0,1,2,\dots \}$
>$B=\mathbb{N}_{>0}=\{ 1,2,3,\dots \}$

>[!tip] $A$ e $B$ hanno la stessa cardinalità

$$
f:\underset{ n\ \mapsto \ n+1 }{ A\to B }
$$

### Insiemi Numerabili
>[!Definizione] 
>Un insieme si dice ***numerabile*** se ha la cardinalità di $\{ 1,2,3,\dots \}=\mathbb{N}_{>0}$

>[!question] $\mathbb{Z}=\{ \dots-3,-2,-1,-,1,2,3,\dots \}$ è numerabile?

- Si:
$0\mapsto 1\quad 1\mapsto 2\quad -1\mapsto 3\quad 2\mapsto 4\quad-2\mapsto 5, \dots.$

>[!caution] Oservazione
>Se $A$ è ***numerabile***, riusciamo a scrivere tutti gli elementi di $A$ in una fila infinita

>$\mathbb{Q}_{>0}=\left\{ \frac{a}{b}:a,b\in\mathbb{N}_{>0}   \right\}$ è numerabile?

- SI
$1,\quad \frac{1}{2},\quad2, \quad \frac{1}{3}, \quad \frac{2}{3},\quad \frac{3}{2},\quad 3, \dots$

>[!question] Sia $B=\{$ successioni infinite di $0$ e $1\}$, $B$ è numerabile?

#### Dimostrazione
> Supponiamo per assurdo di riuscire a mettere tutti gli elementi di $B$ in fila

$$
\begin{array}
\ b_{1}\to \text{Primo Elemento della fila} \\
b_{2}\to \text{Secondo Elemento della fila} \\
b_{3}\to \text{Terzo Elemento della fila} \\
\vdots
\end{array}
$$
>[!tip] Mostriamo che esiste una sequenza binaria che non sta in fila

Costruisco questa sequenza $b$ `Bit` a `Bit` in questo modo:
- Il primo `Bit` di $b$ lo scelgo $\neq$ dal primo `Bit` di $b_{1}$
- Il secondo `Bit` di $b$ lo scelgo $\neq$ dal secondo `Bit` di $b_{2}$
- Il terzo `Bit` di $b$ lo scelgo $\neq$ dal terzo `Bit` di $b_{3}$
- $\vdots$

>[!fail] Contraddizione
>Ottengo una sequenza nuova

### Insiemi discreti e continui
>[!Definizione]
>Un inseme è ***discreto*** se è finito o numerabile
>Un insieme si dice ***continuo*** se ha la cardinalità di $\mathbb{R}$