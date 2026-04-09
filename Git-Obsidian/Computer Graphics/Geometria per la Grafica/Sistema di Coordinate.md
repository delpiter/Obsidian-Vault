> Per rappresentare gli oggetti vengono usate primitive principalmente lineari come **punti**, **linee**, **segmenti** e **piani**.

Dobbiamo sapere come *trasformare gli oggetti*, *calcolare distanze*, *effettuare cambiamenti di sistemi di coordinate*, etc...

## I Sistemi di Riferimento di Coordinate
----
>[!definizione] Sistema Destrorso
>Un sistema di riferimento si dice ***destrorso*** se la rotazione attorno ad $y$ che porta $z$ a coincidere con $x$ è *antioraria*.

### Elementi dei Sistemi di Coordinate
#### Elementi Grafici
>[!note] Scalare
>Specifica una ***quantità***.

>[!help] Punto
>Entità il cui unico attributo è la ***sua posizione*** rispetto ad un *sistema di riferimento*.

>[!abstract] Vettore
>Entità i cui attributi sono *lunghezza e direzione*, **non ha una posizione nello spazio**.
>Il vettore rappresentano ***spostamenti nello spazio***.

- I vettori sono sempre definiti come *vettore colonna*.

In due dimensioni il vettore perpendicolare ad un vettore generico si trova nel seguente modo:
$$
a=(a_{x},a_{y})\implies a^{\perp}=\pm (-a_{y},a_{x})
$$
>[!tip] Vettore Normale
>Vettore **perpendicolare** ad una *superficie*, *piano*, o *curva* in un punto specifico.

^d4f7f8

>Un **vettore** in un piano è definito dalla *differenza tra due punti nel piano*. 

$$
v=P-Q
$$
- $v$ è il vettore che da $Q$ va a $P$.
- Da cui deriva la *somma punto-vettore*.
$$
P=Q+v
$$
#### Simplesso
> Un simplesso è una generalizzazione geometrica dei concetti più familiari come segmenti e triangoli, *estesa a dimensioni arbitrarie*.

>[!help] Dimesione $0$
>In $0$ dimensioni, un simplesso è un ***singolo punto***.

>[!abstract] Dimensione $1$
>In $1$ dimensione, un simplesso è un ***segmento***, definito da due vertici distinti.

>[!summary] Dimensione $2$
>In $2$ dimensioni, un simplesso è un ***triangolo***, formato da tre punti **non allienati** (*vertici*).

>[!tip] Dimensione $3$
>In $3$ dimensioni, un simplesso è un ***tetraedro***, definito da quattro punti **non complanari**.

> In Generale
- Un simplesso di dimensione $k$ è il più piccolo insieme convesso che contiene $k+1$ punti indipendenti, detti ***vertici del simplesso***.
#### Spazi
![[../../Algebra e Geometria/Basi dell'algebra/2 - Campi e Spazi Vettoriali#Spazio Vettoriale]]

![[../../Algebra e Geometria/Basi dell'algebra/2 - Campi e Spazi Vettoriali#Sottospazio Affine]]

![[../../Algebra e Geometria/Basi dell'algebra/2 - Campi e Spazi Vettoriali#Combinazioni Lineari]]

![[../../Algebra e Geometria/Basi dell'algebra/2 - Campi e Spazi Vettoriali#Base]]
