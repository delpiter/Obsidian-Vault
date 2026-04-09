## LCS
---
*Applicazioni biologiche spesso necessitano di un confronto di DNA fra due o più diversi organismi*
*Per esempio, siano $S_{1}$ e $S_{2}$ le sequenze di DNA di due organismi diversi*
- $S_{1}=ACCGGTCGAGTGCGCGGAAGCCGGCCGAA$
- $S_{2}=GTCGTTCGGAATGCCGTTGCTCTGTAAA$

*Una delle ragioni di confrontare queste due stringhe di DNA è quella di determinare quanto "**simili**" queste due sequenze sono, per misurare la relazione fra i due organismi*
*Uno dei tanti modi per determinare la similarità fra $S_{1}$ e $S_{2}$ è quello di trovare una terza sequenza $S_{3}$ che appare sia in $S_{2}$ che in $S_{1}$, gli elementi di $S_{3}$ devono apparire nello stesso ordine in $S_{2}$ e $S_{3}$ ma non necessariamente consecutivamente*
*Più $S_{3}$ è lunga, più i due organismi sono simili, nel nostro caso la sequenza $S_{3}$ più lunga è:*
- $S_{3}=GTCGTCGGAAGCCGGCCGAA$

>[!info] Definizioni
>Formalizziamo questo problema come "***Longest Common Subsequence Problem***"
>>[!tldr] Subsequence
>>Una ***sottosequenza*** di una sequenza data è la sequenza data con $0$ o più elementi "*lasciati fuori*"
>>Formalmente, data una sequenza $X=<x_{1},x_{2},\dots,x_{n}>$, un'altra sequenza $Z= <z_{1},z_{2},\dots,z_{n}>$ è una ***sotto-sequenza*** si $X$ se esiste una sequenza strettamente crescente  $<i_{1},i_{2},\dots,i_{k}>$ di indici di $X$ tali che:
>>$$\forall j=1,2,\dots,k$$
>>Si ha:
>>$$x_{i_{j}}=z_{j}$$
>>>[!example] Esempio
>>>$Z=<B,C,D,B>$ è una *sotto-sequenza* di $X= <A,B,C,B,D,A,B>$ con la sequenza di indici corrispondenti: $<2,3,5,7>$
>
>>[!summary] Common Subsequence
>>Date due sequenze $X$ e $Y$ diciamo che $Z$ è una ***sotto-sequenza comune*** di $X$ e $Y$ se $Z$ è una sotto-sequenza di $X$ e $Y$
>>>[!example] Esempio
>>>Siano $X= <A,B,C,B,D,A,B>$ e $Y=<B,D,C,A,B,A>$ due sequenze, la sequenza $<B,C,A>$ è una sotto-sequenza comune a $X$ e $Y$
>
>>[!tldr] Prefisso
>>Data una sequenza $X= <x_{1},x_{2},\dots,x_{m}>$
>>Definiamo l'$i$-*esimo prefisso* di $X$ per $i=0,1,\dots,m$ come:
>>$$X_{i}= <x_{1},x_{2},\dots,x_{i}>$$
>>>[!example] Esempio
>>>Sia $X= <A,B,C,B,D,A,B>$ allora:
>>>- $X_{4}= <A,B,C,B>$
>>>- $X_{0}$ è una ***sequenza vuota***
### Problema
>[!info] Definizione del Problema
>Il problema della ***massima sotto-sequenza comune*** è un [[../../Definizioni/Definizioni_Algoritmi#Problema di Ottimizzazione|problema di ottimizzazione]], risolvibile tramite [[Algoritmi di Programmazione Dinamica#Programmazione Dinamica|programmazione dinamica]].
>Consiste nel trovare la ***più lunga sotto-sequenza comune*** fra due sequenze di caratteri
>>[!abstract] Input
>>In input sono date *due sequenze*: $X= <x_{1},x_{2},\dots,x_{n}>$ e $Y= <y_{1},y_{2},\dots,y_{m}>$
>
>>[!caution] Output
>>Si chiede di trovare la più lunga sequenza $Z= <z_{1},z_{2},\dots,z_{k}>$ che è sotto-sequenza sia di $X$ che di $Y$

#### Sottostruttura Ottima
>[!Teorema]
>Siano $X= <x_{1},x_{2},\dots,x_{m}>$ e $Y= <y_{1},y_{2},\dots,y_{n}>$ due sequenze
>Sia $Z= <z_{1},z_{2},\dots,z_{k}>$ una qualsiasi `LCS` di $X$ e $Y$
>>[!abstract] $1.$
>>Se $x_{m}=y_{n}$ allora $z_{k}=x_{m}=y_{n}$ e $Z_{k-1}$ è una `LCS` di $X_{m-1}$ e $Y_{n-1}$
>>>[!done] A parole
>>>Se le sequenze *finiscono con la stessa lettera*, anche la sotto-sequenza finisce con la stessa e se tolgo l'ultima lettera da tutte le sequenze ho ancora un ***risultato ottimo***
>>>$X=<A,B,B,A>\quad Y= <B,A,B,A>\quad Z=<A,B,A>$
>
>>[!example] $2-3$
>>>[!abstract] $2.$
>>>Se $x_{m}\neq y_{n}$ e $z_{k}\neq x_{m}$ allora $Z_{k}$ è `LCS` di $X_{m-1}$ e $Y$ 
>>
>>>[!abstract] $3.$
>>>Se $x_{m}\neq y_{n}$ e $z_{k}\neq y_{n}$ allora $Z_{k}$ è `LCS` di $X$ e $Y_{n-1}$

##### Dimostrazione
>1. 

>[!abstract] Supponiamo che $x_{m}=y_{n}$

Se $z_{k}\neq x_{m}=y_{n}$
Potremmo aggiungere il simbolo $x_{m}=y_{n}$ in coda a $Z$ ottenendo una sotto-sequenza comune di lunghezza $k+1$.

>[!danger] Contraddizione $Z$ è gia una `LCS`

>2.

>[!abstract] Se $z_{k}\neq x_{m}$

Allora $Z$ è sotto-sequenza di $X_{m-1}$ e $Y$
Essendo $Z$ una `LCS` di $X$ e $Y$, essa è anche una `LCS` di $X_{m-1}$ e $Y$

>3.

>[!done] Dimostrazione simmetrica a 2.

#### Soluzione Ricorsiva
>*Siano $X= <x_{1},x_{2},\dots,x_{m}>$ e $Y= <y_{1},y_{2},\dots,y_{n}>$ le due sequenze di cui vogliamo calcolare una `LCS`*

Per $i=0,1,\dots,m$ e $j=0,1,\dots,n$ sia $c_{i,j}$ la lunghezza di una `LCS` dei due prefissi $X_{i}$ e $Y_{i}$

>[!abstract] Per le proprietà appena dimostrate, possiamo scrivere

$$
c_{i,j}=\begin{cases}
0 \qquad \qquad \qquad \qquad\text{se }  i=0 \text{ o } j=0 \\
c_{i-1,j-1}+1\qquad\quad \ \ \  \text{se } i,j>0 \text{ e } x_{i}= y_{j} \\
max(c_{i,j-1},c_{i-1},j) \ \ \ \text{se }i,j>0\text{ e }x_{i}\neq y_{j}
\end{cases}
$$
##### Esempio
![[attachements/LCS_Example.png]]

#### Pseudocodice
```pseudo
	\begin{algorithm}
	\caption{Longest Common Substring}
	\begin{algorithmic}
	\Procedure{LCS}{$ X,Y $}
	\State $ m=X.length $
	\State $ n=Y.length $
	\For{$ i=0 \to m $}
	  \State $ c[i,0] =0 $
 \EndFor
 \For{$ j=0 \to n $}
	  \State $ c[0,j] =0 $
 \EndFor
 \For{$ i=1 \to m $}
  \For{$ j=1 \to n $}
  \If{$ x_i == y_j  $}
  \State $ c[i,j] = c[i-1,j-1]+1 $
  \State $ b[i,j]="\nwarrow" $
  \Else 
 \If{$ c[i-1,j] \geq c[i,j-1]  $}
  \State $ c[i,j]=c[i-1,j] $
  \State $ b[i,j]="\uparrow" $
  \Else 
 \State $ c[i,j]=c[i,j-1] $
  \State $ b[i,j]="\leftarrow" $
 \EndIf
 \EndIf
 \EndFor
 \EndFor
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```

##### Ricostruzione della Sotto-Sequenza
```pseudo
	\begin{algorithm}
	\caption{LCS Solution}
	\begin{algorithmic}
\Procedure{Print-LCS}{$ b,X,i,j $}
\If{$ i=0 \text{ or }j=0 $}
  \Return
 \EndIf
 \If{$ b[i,j]="\nwarrow"  $}
  \State \Call{ Print-LCS }{$ b,X,i-1,j-1 $}
  \State \Call{ Print }{$ x_i $}
  \Else 
  \If{$ b[i,j]="\uparrow"  $}
  \State \Call{ Print-LCS }{$ b,X,i-1,j $}
  \Else 
 \State \Call{ Print-LCS }{$ b,X,i,j-1 $}
 \EndIf
 \EndIf
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```
