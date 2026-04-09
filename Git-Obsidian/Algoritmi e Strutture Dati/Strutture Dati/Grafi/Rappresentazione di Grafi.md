## Liste di Adiacenza
---
>[!info] Definizione
>La ***lista di adiacenza*** di un vertice $v$ è la lista che concatena *tutti i vertici adiacenti* a $v$
>Il [[I Grafi#Grafo Definizione|grafo]] può essere rappresentato dalle ***liste di adiacenza*** di *tutti i suoi vertici*

>[!tip] Spazio Necessario
>$$\Theta\left( n+\sum_{v} deg(v) \right)=\Theta(n+m)$$
>>[!done] In Breve
>>Sommatoria dei [[I Grafi#Grado di un Vertice|gradi]] di tutti i vertici $+$ il numero di vertici

#### Esempio
```
[1]: 6
[2]: 6
[3]: 2
[4]: 1, 3, 5
[5]: 2
[6]: 1
```

![[attachements/graph 1.png]]

## Matrice di Adiacenza
---
>[!info] Definizione
>Una ***matrice di adiacenza*** è una matrice $M$ di variabili ***booleane*** con una cella per ogni coppia di vertici
>$$M[i,j]= \text{ vero }\to \text{ esiste l'arco }(i,j)$$
>$$M[i,j]= \text{ falso }\to \text{ non esiste l'arco }(i,j)$$

>[!tip] Spazio Necessario
>$$\Theta(n^2)$$

>[!tldr] Osservazione
>Una ***Matrice di Adiacenza*** *non ordinata* è una matrice *completamente simmetrica* rispetto alla diagonale
#### Esempio

| $/$ | $1$ | $2$ | $3$ | $4$ | $5$ | $6$ |
| :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| $1$ | $0$ | $0$ | $0$ | $0$ | $0$ | $1$ |
| $2$ | $0$ | $0$ | $0$ | $0$ | $0$ | $1$ |
| $3$ | $0$ | $1$ | $0$ | $0$ | $0$ | $0$ |
| $4$ | $1$ | $0$ | $1$ | $0$ | $1$ | $0$ |
| $5$ | $0$ | $1$ | $0$ | $0$ | $0$ | $0$ |
| $6$ | $1$ | $0$ | $0$ | $0$ | $0$ | $0$ |

![[attachements/graph 1.png]]