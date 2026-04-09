## Programmazione Dinamica
---
>[!info] Definizione
>La ***programmazione dinamica*** è una tecnica di risoluzione di problemi simile a quella [[../Divide et Impera]]:
>- Risolve problemi *combinando soluzioni* di *sotto problemi*
>
>>[!question] Quando usarla?
>
>La ***programmazione dinamica*** entra in gioco quando il *divide et impera* calcola molto più di quanto sia necessario per la risoluzione del problema.
>- Quando il *divide et impera* ricalcola la ***stessa soluzione di un sotto problema*** numerose volte
>
>La ***programmazione dinamica*** tiene traccia delle soluzioni dei sotto problemi per non dovere calcolare la stessa soluzione più volte
>>[!abstract] Applicazione
>>Si applica tipicamente a [[../../Definizioni/Definizioni_Algoritmi#Problema di Ottimizzazione|problemi di ottimizzazione]]

>[!warning] Attenzione

Il termine "***programmazione***", in questo caso, non significa "***scrivere codice***"
- Si riferisce ad un metodo di risoluzione chiamato [[../../Definizioni/Definizioni_Algoritmi#Tabular Method|tabular method]]

### Passi Fondamentali
>*Nella **programmazione dinamica** ci sono 4 passi fondamentali da rispettare*

>[!abstract] 1

***Verifica della caratterizzazione della struttura*** di una *soluzione ottima*

>[!abstract] 2

***Definizione ricorsiva del valore*** di una soluzione ottima tramite *equazioni ricorsive*

>[!abstract] 3

***Calcolo del valore*** di una soluzione ottima con strategia "***bottom-up***"

>[!abstract] 4

***Costruzione di una soluzione ottima*** a partire dalle informazioni già calcolate
- Spesso ripaga *mantenere informazioni aggiuntive* durante lo ***step 3*** affinché sia più facile ricostruire una soluzione
---
>I ***primi tre passi*** formano la *base* di una soluzione di *programmazione dinamica* di un problema

>Il ***quarto passo*** serve per costruire la soluzione effettiva del problema
>Se serve solo il *valore della soluzione ottimale* è possibile ***omettere*** questo step

### Requisiti
>*Per applicare con successo la programmazione dinamica, è necessario che il problema abbia:*

![[../../Definizioni/Definizioni_Algoritmi#Sottostruttura Ottimale]]

>[!info] Sotto problemi Comuni
>Un [[../../Definizioni/Definizioni_Algoritmi#Problema di Ottimizzazione|problema di ottimizzazione]] ha sotto ***problemi comuni*** quando un algoritmo ricorsivo richiede di risolvere ***più di una volta lo stesso problema***


### Numeri di Fibonacci
>*I numeri di Fibonacci è un esempio di problema che può essere ottimizzato con la programmazione dinamica*

#### Algoritmo 1
```pseudo
	\begin{algorithm}
	\caption{Numeri di Fibonacci}
	\begin{algorithmic}
\Procedure{Fibonacci}{$ n $}
\If{$ n<= 2$}
\Return $ 1 $
\Else 
\Return \Call{ Fibonacci }{$ n-1 $}+\Call{ Fibonacci }{$ n-2 $}
 \EndIf
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```

>[!caution] Complessità

$$
T(n)=2+T(n-1)+T(n-2)=O(2^n)
$$
Quindi con $n$ anche molto piccoli il numero di passi è esorbitante
- $n=45\to \ \approx$ ***un miliardo*** di passi

#### Algoritmo 2
```pseudo
	\begin{algorithm}
	\caption{Numeri di Fibonacci}
	\begin{algorithmic}
\Procedure{Fibonacci}{$ n $}
\State $ f= \text{new array}[n+1] $
\State $ f[1]=f[2]=1 $
\For{$ i=3 \to n $}
  \State $ f[i]=f[i-1]+f[i-2] $
 \EndFor
 \Return $ f[n] $
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```

>[!caution] Complessità

$$
T(n)=O(n)
$$
- $n=45 \to 45$ passi 
