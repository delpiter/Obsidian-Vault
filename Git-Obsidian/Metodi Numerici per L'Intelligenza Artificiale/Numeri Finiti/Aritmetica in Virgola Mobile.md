## Operazioni Macchina
---
>[[Floating Point|!example]]
>$fl(x)\oplus fl(y)=fl(fl(x)+fl(y))$
>$fl(x)\ominus fl(y)=fl(fl(x)-fl(y))$
>$fl(x)\otimes fl(y)=fl(fl(x)\cdot fl(y))$
>$fl(x)\oslash fl(y)=fl(fl(x) / fl(y))$

## Propagazione degli Errori nella Somma
---
>[!summary] Somma
>Assumiamo $x,y\in \mathbb{R}$, ma $x,y\notin F$
>- $x$ e $y$ devono essere arrotondati in $F$:
>$x \to fl(x)=x(1+\mathcal{E}_{x})\in F$
>$y \to fl(y)=y(1+\mathcal{E}_{y})\in F$
>
>I due numeri di $F$ vengono quindi ***sommati***, ottenendo:
>$$fl((fl(x))\oplus(fl(y)))=[[1+\mathcal{E}_{x})+y(1+\mathcal{E}_{y})](1+\mathcal{E}_{s}|x(1+\mathcal{E}_{x})+y(1+\mathcal{E}_{y})]]$$
>
>Con:
>- $\mid\mathcal{E}_{x}\mid,\mid\mathcal{E}_{y}\mid,\mid\mathcal{E}_{s}\mid \leq u$

#### Errore Relativo
>Il risultato finale sarà $[[1+\mathcal{E}_{x})+y(1+\mathcal{E}_{y})](1+\mathcal{E}_{s}|x(1+\mathcal{E}_{x})+y(1+\mathcal{E}_{y})]]$ da confrontare con il vero risultato $x+y$.

$$
Err_{rel_{s}}=\displaystyle{\frac{\mid[[1+\mathcal{E}_{x})+y(1+\mathcal{E}_{y})](1+\mathcal{E}_{s}|x(1+\mathcal{E}_{x})+y(1+\mathcal{E}_{y})]]-(x+y)\mid}{\mid x+y\mid}}=
$$
$$
=\displaystyle{\frac{\mid \cancel{ x }+x\mathcal{E}_{s}+x\mathcal{E}_{x}\mathcal{E}_{s}\cancel{ +y }+y\mathcal{E}_{s}+y\mathcal{E}_{y}\mathcal{E}_{s}\cancel{ -(x+y) }\mid}{\mid x+y\mid}}
$$

- Assumendo che la [[Floating Point#Conclusioni|roundoff unit]] "$u$" sia molto più piccola di $1$, in modo da poter trascurare $u^2$ rispetto a $u$.

$$
Err_{rel_{s}}\approx \left| \displaystyle{\frac{x}{x+y}\mathcal{E}_{x}}+\displaystyle{\frac{y}{x+y}\mathcal{E}_{y}}  +\mathcal{E}_{s}\right|\leq \left|\displaystyle{\frac{x}{x+y}}\right|u+\left|\displaystyle{\frac{y}{x+y}}\right|u + u 
$$

>[!todo] $x$ e $y$ hanno lo stesso segno

Allora $\left|\displaystyle{\frac{x}{x+y}}\right|,\left|\displaystyle{\frac{y}{x+y}}\right|\leq 1$.
- E di conseguenza:

$$Err_{rel_{s}}\leq 3u$$

>[!caution] $x$ e $y$ hanno segno diverso

Le quantità $\left|\displaystyle{\frac{x}{x+y}}\right|$ e $\left|\displaystyle{\frac{y}{x+y}}\right|$ possono assumere ***qualunque grandezza***, quindi **non possiamo controllare l'errore a priori**.

## Propagazione degli Errori nella Moltiplicazione
---
>[!cite] Moltiplicazione
>Assumiamo $x,y\in \mathbb{R}$, ma $x,y\notin F$
>- $x$ e $y$ devono essere arrotondati in $F$:
>$x \to fl(x)=x(1+\mathcal{E}_{x})\in F$
>$y \to fl(y)=y(1+\mathcal{E}_{y})\in F$
>
>I due numeri di $F$ vengono quindi ***sommati***, ottenendo:
>$$fl((fl(x))\otimes(fl(y)))=[[1+\mathcal{E}_{x})\cdot y(1+\mathcal{E}_{y})](1+\mathcal{E}_{p}|x(1+\mathcal{E}_{x})\cdot y(1+\mathcal{E}_{y})]]$$
>
>Con:
>- $\mid\mathcal{E}_{x}\mid,\mid\mathcal{E}_{y}\mid,\mid\mathcal{E}_{p}\mid \leq u$

#### Errore Relativo
>Il risultato finale sarà $[[1+\mathcal{E}_{x})\cdot y(1+\mathcal{E}_{y})](1+\mathcal{E}_{p}|x(1+\mathcal{E}_{x})\cdot y(1+\mathcal{E}_{y})]]$ da confrontare con il vero risultato $x\cdot y$.

$$
Err_{rel_{p}}=\displaystyle{\frac{\mid xy(1+\mathcal{E}_{x})(1+\mathcal{E}_{y})(1+\mathcal{E}_{p})-xy\mid}{\mid xy\mid}}=
$$
- Semplificando per $xy$ si ottiene:
$$
Err_{rel_{p}}=\mid (1+\mathcal{E}_{x})(1+\mathcal{E}_{y})(1+\mathcal{E}_{p})-1\mid=
$$
Da cui si ottiene:
$$
\mid \mathcal{E}_{x}+\mathcal{E}_{y}+\mathcal{E}_{p}+\mathcal{E}_{x}\mathcal{E}_{y}+\mathcal{E}_{x}\mathcal{E}_{p}+\mathcal{E}_{y}\mathcal{E}_{p}+\mathcal{E}_{x}\mathcal{E}_{y}\mathcal{E}_{p}\mid
$$
Con:
- $\mid\mathcal{E}_{x}\mid,\mid\mathcal{E}_{y}\mid,\mid\mathcal{E}_{p}\mid \leq u$

- Assumendo che la [[Floating Point#Conclusioni|roundoff unit]] "$u$" sia molto più piccola di $1$, in modo da poter trascurare $u^2$ rispetto a $u$.

Trascurando i termini moltiplicati:
$$
Err_{rel_{p}}\approx \mid \mathcal{E}_{x}+\mathcal{E}_{y}+\mathcal{E}_{p}\mid \leq 3u
$$

>[!done] Conclusione
>Qualunque siano i numeri $x,y\in \mathbb{R}$, l'**errore relativo** sul prodotto è sempre ***minore o uguale*** a $3u$
>Di conseguenza il prodotto è sempre una operazione sicura (**stabile**).

## Somma Algebrica
---
>[!info]
>La ***somma algebrica macchina*** tra due numeri $x,y\in F(\beta,t,L,U)$ richiede:

>[!caution] 1\. *Confronto* degli **esponenti**
>Se gli esponenti sono **uguali**, si può procedere direttamente con la *somma delle mantisse*.
>Se sono **diversi**, è necessario *allinearli*.

>[!abstract] 2\. *Allineamento* degli **esponenti**
>Per *allineare* il gli **esponenti** bisogna determinare il numero con l'*esponente minore*.
>Successivamente si ***scala*** la mantissa del numero con l'esponente minore, spostando la virgola a sinistra di un numero di posizioni pari alla *differenza di esponenti*.

>[!tip] 3\. *Somma* delle **mantisse**

>4\. *Normalizzazione* del risultato
>Se la mantissa non è **normalizzata**, si sposta la virgola e si aggiusta l'esponente

>[!missing] 5\. *Arrotondamento*

### Esempio
> Consideriamo i numeri $x=0.78546\cdot 10^{2},\quad y=0.61332\cdot 10^{-1}$

>[!caution] Calcoliamo: $x\oplus y$

> **Confronto** e **Allineamento**

Scaliamo $y$ in maniera tale che abbia la stessa parte esponente di $x$.
$$
y=0.61332\cdot 10^{-1}=0.00061332\cdot 10^{2}
$$

> **Somma**

Sommiamo le mantisse:
$$
0.78546 \cdot 10^{2}+ 0.00061332\cdot 10^{2}=0.78607332\cdot 10^2
$$

>[!done] Il risultato è già normalizzato

> **Arrotondamento**

$$
fl(0.78607332\cdot 10^2)= 0.78607 \cdot 10^2
$$

## Prodotto Macchina
---
>[!info]
>Il ***prodotto*** tra due numeri $x,y\in F(\beta,t,L,U)$, richiede le seguenti fasi:

>[!caution] 1\. **Prodotto** delle *mantisse*

>[!missing] 2\. *Arrotondamento*
>Si [[Floating Point#Troncamento e Arrotondamento|arrotonda]] (o *tronca*) il numero ottenuto alle prime $t$ cifre.

>[!tip] **Somma** degli *esponenti*
>In fine si **sommano** gli esponenti, **normalizzando** se necessario

### Esempio
>Consideriamo i due numeri: $x = 0.11111\cdot10^3 ,\ y = 0.52521\cdot10^2\in F(10,5,L,U)$

>[!caution] Calcoliamo $x\otimes y$

>**Prodotto** delle Mantisse

$$
0.11111 \cdot 0.52521 = 0.0583568
$$

>**Arrotondamento** a $5$ cifre

$$
0.0583568 = 0.058356 \cdot 10^{-1}
$$

> **Somma** degli esponenti

$$
x\cdot y= 0.058356 \cdot 10^{-1} \cdot 10^3 \cdot 10^2=0.58356\cdot 10^4
$$

## Divisione Macchina
---
>[!info]
>La ***divisione macchina*** tra due numeri $x,y\in F(\beta, t,L,U)$ richiede le seguenti fasi:

>[!caution] 1\. **Scala** il *dividendo*
>Si **scala** il *dividendo* $x$ finché la sua mantissa non risulti ***minore*** di quella del *divisore* $y$.

>[!abstract] 2\. **Divisione** tra *Mantisse*
>Si esegue la **divisione** tra le mantisse.

>[!missing] 3\. *Arrotondamento*
>Si [[Floating Point#Troncamento e Arrotondamento|arrotonda]] (o *tronca*) il numero ottenuto alle prime $t$ cifre.

>[!tip] **Sottrazione** tra *esponenti*

### Esempio
>Consideriamo i due numeri: $x = 0.12100\cdot10^5 ,\ y = 0.11000\cdot10^2\in F(10,5,L,U)$

>[!caution] Calcoliamo $x \oslash y$

> **Scaliamo** il dividendo

$$
0.12100\cdot10^5 = 0.012100\cdot10^6
$$

>**Dividiamo** le mantisse

$$
\frac{0.012100}{0.11000}=0.11000
$$
>**Sottrazione** degli esponenti

$$
0.11000 \cdot 10^6 \cdot 10 ^{-2}= 0.11000\cdot10^4
$$
