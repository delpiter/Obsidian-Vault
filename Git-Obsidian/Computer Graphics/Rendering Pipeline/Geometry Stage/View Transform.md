>[!tldr] Idea
>La fase di ***view transform***, prende in *input* i vertici in `WCS` e da in output i vertici in `3D`-view o `VCS`.

Per costruire una trasformazione di vista è necessario:
- Posizionare la camera nel `WCS` e *orientarla opportunamente*.
	- Permette di generare la [[Sistemi di Riferimento#Cambio di Sistema di Riferimento|matrice del cambiamento di sistema di riferimento]].
	- Matrice usata per trasformare ***ogni vertice degli oggetti in scena*** dal `WCS` al `VCS`.


>[!info] Definire la Vistsa
>Abbiamo bisogno di sapere ***quattro informazioni*** sul *modello di fotocamera sintetica*.
>- Punto $C$: Posizione della telecamera in `WSC`.
>- Punto $A$: Il vettore $C-A$ specifica in quale direzione sta *puntando la telecamera*.
>- Field of View (`FOV`): ***Angolo di visibilità verticale*** nella scena, espresso in $\text{rad}$.
>- Depth of Field: **Distanza** tra l'oggetto *più vicino* e quello *più lontano* che appaiono perfettamente a fuoco.

![[SyntheticCamera.png]]

> Definiamo un [[Sistemi di Riferimento|sistema di riferimento]] `VCS` associato all'osservatore, di origine $C$.

$$
F(C,u,v,w)
$$
L'asse $w$ indica la direzione di vista unitaria verso cui punta la fotocamera.
- Per convenzione la camera guarda in direzione $-w$.
$$
w=\displaystyle{\frac{C-A}{\|C-A\|}}
$$
View Up Vector (`VUP`): Determina il modo in cui la fotocamera viene ***ruotata*** attorno alla direzione di vista.

L'asse $u$ unitario, punta alla destra dell'osservatore, è perpendicolare sia all'asse $w$ che a `VUP`.
$$
u=\displaystyle{\frac{VUP\times w}{\|VUP\times w\|}}
$$

Questo modo di rappresentazione prende il nome di **camera** "***look at***".

>[!done] Ottimizzazione

Nel caso di $VUP \parallel y$ il prodotto vettoriale può essere ottimizzato come segue:
$$
[0 \ 1\ 0]\times w =[w_{z}\ 0 \ -w_{x}]
$$
- L'asse $v$ è ortogonale sia all'asse $w$ che a $u$, quindi
$$
v=w\times u
$$
- Poiché $w$ e $u$ sono normalizzati, anche $v$ risulta normalizzato.
$$
\|v\|=\|u\|\|v\|\cos(90^{\circ})=1
$$

## Costruzione della Matrice di Trasformazione
---
> Dati i [[Sistemi di Riferimento#Frame|frame]] `WCS` e `VCS`, calcoliamo ora la ***matrice di trasformazione di vista*** $T_{v}$.

>[!failure] Cambiamento di Base
>Esprimiamo il sistema di riferimento `VCS` in termini del `WCS`: $(O,x,y,z)$.

$$
\begin{array}
\ u=u_{x}x+u_{y}y+u_{z}z+0\cdot O \\
v=v_{x}x+v_{y}y+v_{z}z+0\cdot O \\
w=w_{x}x+w_{y}y+w_{z}z+0\cdot O \\
C=C_{x}x+C_{y}y+C_{z}z+1\cdot O
\end{array}
$$
> In termini matriciali:

$$
M=\begin{bmatrix}
u_{x} & v_{x} & w_{x} & C_{x} \\
u_{y} & v_{y} & w_{y} & C_{y} \\
u_{z} & v_{z} & w_{z} & C_{z} \\
0 & 0 & 0 & 1
\end{bmatrix}
$$
La matrice $M$ mappa le coordinate di un punto nel `VCS` nelle coordinate di `WCS`.
- A noi serve la ***matrice inversa*** $M^{-1}$ che chiameremo $T_{v}$, che determina la rappresentazione di un punto $P_{v}$ in coordinate omogenee in `VCS` data la rappresentazione in `WCS`.