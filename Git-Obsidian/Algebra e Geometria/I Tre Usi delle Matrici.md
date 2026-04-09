>*A tre diversi usi delle matrici corrispondono tre diverse nozioni di equivalenza*
## Sistemi Lineari
---
>[!info] Descrizione dell'Utilizzo
>$Ax=b$ Dove $A_{ij}$ è il ***coefficiente*** di $x_{j}$ nella $i$-esima equazione

>[!question] Cosa Rappresenta?

Due matrici $A,M$ rappresentano ***sistemi equivalenti*** (cioè hanno le *stesse soluzioni*)
$\iff$
Applicando ad esse l'[[Risoluzione di Sistemi#Metodo di Gauss|algoritmo di Gauss]] ottengo la stessa matrice

## Applicazioni Lineari
---
>[!info] Descrizione dell'Utilizzo
>$A_{ij}$ è la $i$-esima ***coordinata*** del vettore $f(v_{j})$ scritto nella base $u_{1},\dots,u_{n}$

>[!question] Cosa Rappresenta?

Due matrici $A,M$ rappresentano la stessa ***applicazione***
$\iff$
Sono [[Applicazioni/6 - Cambiamenti di Base#Matrici Simili|simili]], cioè $\exists B$ ***invertibile*** tale che $M=B^{-1}AB$

## Forme Bilineari
---
>[!info] Descrizione dell'Utilizzo
>$A_{ij}=\beta(v_{i},v_{j})$ indica il valore di $\beta$ su una ***coppia di elementi*** della base

>[!question] Cosa Rappresenta?

Due matrici $A,M$ rappresentano la stessa ***forma bilineare***
$\iff$
Sono [[Frome Bilineari e Prodotti Scalari/1 - Forme Bilineari#Matrici Congruenti|congruenti]], cioè $\exists B$ invertibile: $M=B^TAB$

