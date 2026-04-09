>Prima soluzione *poco efficiente* al [[Problema dell'Ordinamento]]
## Pseudo Codice
---
```pseudo
	\begin{algorithm}
	\caption{Insertion Sort}
	\begin{algorithmic}
	\Procedure{InsetionSort}{$A[]$}
	\For{$ j=2 \to size(A)$}
  \State $ key=A[j] $
  \State $ i=j-1 $
  \While{$i>0 \text{ and } A[i]>key$}
  \State $ A[i+1]=A[i] $
  \State $ i=i-1 $
  \EndWhile
  \State $ A[i+1]=key $
 \EndFor
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```
![[youtube.com)](https://www.youtube.com/watch?v=8oJS1BMKE64|Insertion Sort (youtube.com)]]
## Concetto
---
>Ad ogni passo ho una sottosequenza ordinata in cui inserisco un nuovo elemento dell'input

![[attachements/Pasted image 20240421180619.png]]
Si considera il primo elemento dell'insieme da solo come *ordinato*
- Prendo il primo elemento della sottosequenza non ordinata e lo inserisco nel sottoinsieme già ordinato

## Costo Computazionale
---
$$
T(n)=c_{1}n+c_{2}(n-1)+c_{3}(n-1)+c_{4}\sum_{i=1}^nt_{j}+(c_{5}+c_{6})\sum_{i=1}^n(t_{j}-1)+c_{7}(n-1)
$$
- $t_{j}\to$ Numero di esecuzione istruzione while, **dipende dai dati in *input***

>[!done] Caso Ottimo
>L'array è già ordinato
>$t_{j}=1 \implies T(n)=an+b\to \Theta(n)$ 
>

>[!danger] Caso Pessimo
>L'array è ordinato in maniera decrescente
>$t_{j}=j \implies T(n)=an^2+bn+c\to \Theta(n^2)$

