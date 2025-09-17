> Per rappresentare gli oggetti vengono usate primitive principalmente lineari come **punti**, **linee**, **segmenti** e **piani**.

Dobbiamo sapere come *trasformare gli oggetti*, *calcolare distanze*, *effettuare cambiamenti di sistemi di coordinate*, etc...

## I Sistemi di Riferimento di Coordinate
----
>[!definizione] Sistema Destroso
>Un sistema di riferimento si dice ***destroso*** se la rotazione attorno ad $y$ che porta $z$ a coincidere con $x$ è *antioraria*.

### Elementi dei Sistemi di Coordinate
#### Elementi Grafici
>[!note] Scalare
>Specifica una ***quantità***.

>[!help] Punto
>Entità il cui unico attributo è la ***sua posizione*** rispetto ad un *sistema di riferimento*.

>[!abstract] Vettore
>Entità i cui attributi sono *lunghezza e direzione*, **non ha una posizione nello spazio**.
>Il vettore rappresentano ***spostamenti nello spazio***.

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
- $v$ è il vettore che da $Q$ va a $P$
- Da cui deriva la *somma punto-vettore* #wtf
$$
P=Q+v
$$
#### Spazi
![[2 - Campi e Spazi Vettoriali#Spazio Vettoriale]]

![[2 - Campi e Spazi Vettoriali#Sottospazio Affine]]

![[2 - Campi e Spazi Vettoriali#Combinazioni Lineari]]

![[2 - Campi e Spazi Vettoriali#Base]]
