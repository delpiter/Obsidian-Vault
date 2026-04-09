>*Alcune applicazione necessitano il raggruppamento di $n$ elementi distinti in una collezione di insiemi disgiunti, degli insiemi senza elementi in comune*

## Disjoint Set
---
>[!info] Definizione
>Una ***disjoint set data structure*** mantiene una collezione $\mathcal{S}=\{ s_{1},s_{2},\dots,s_{k} \}$ di *insiemi disgiunti dinamici*
>>[!tip] Identificazione
>>Per identificare ciascun insieme si sceglie un ***rappresentante***
>>- Uno dei membri dell'insieme
>
>>[!example] Operazioni
>>$\text{Make-Set}(x)$
>>- Dove $x$ non fa già parte di un altro insieme, crea un ***nuovo insieme*** dove l'*unico membro*, e quindi ***rappresentante*** è $x$
>>
>>$\text{Union}(x,y)$
>>- Unisce due *insiemi disgiunti dinamici* che contengono $x$ e $y$, diciamo $S_{x}$ e $S_{y}$ in un ***nuovo insieme*** che è l'***unione*** di questi due insiemi
>>- Il ***rappresentante*** del nuovo insieme potrebbe essere ***qualsiasi elemento*** dei due insiemi
>>	- Molte implementazioni di questa operazione scelgono il *rappresentante* di uno dei due insiemi come ***nuovo rappresentante***
>>
>>$\text{Find-Set}(x)$
>>- Ritorna un puntatore al ***rappresentante dell'insieme*** che contiene $x$

### Strutture Dati per Insiemi Disgiunti
>[!info] Disjoint-Set Forests
>Una delle implementazioni per gli *insiemi disgiunti* è rappresentata da [[Grafi/Alberi/Gli Alberi|alberi]] ***radicati***
>Dove ***ogni nodo*** contiene un ***elemento***, e ***ogni albero*** rappresenta un ***insieme***
>- In una ***Disjoint-Set Forests*** ogni elemento ha solo un *puntatore al padre*
>- La *radice* di ciascun albero contiene il ***rappresentante dell'insieme*** ed è il ***padre di se stessa***

![[attachements/Pasted image 20240330100435.png]]
*Una foresta di insiemi disgiunti*

#### Up-Tree Make-Set
>*Inizializza un nuovo Up-Tree contenente solo il nodo $x\implies \Theta(1)$*

![[attachements/Screenshot 2024-03-30 10asd5.png]]
#### Up-Tree Find-Set
>*Percorre la catena dei puntatori fino a trovare il rappresentante di $x\implies O(h)$*

![[attachements/findset2024-03-30 100721.png]]
```pseudo
	\begin{algorithm}
	\caption{Find Set}
	\begin{algorithmic}
\Procedure{Find-Set}{$ x $}
\If{$ x\neq p[x]  $}
	  \State $ p[x] =$\Call{Find-Set}{$p[x]$}
 \EndIf
\Return $ p[x] $
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```

#### Up-Tree Union
>*La radice dell'albero la cui altezza è minore la si fa puntare alla radice dell'albero con altezza maggiore*

>[!tip] Rango
>Il rango è il ***cammino più lungo*** da una foglia al nodo

- La radice di ***rango inferiore*** avrà come padre la radice di ***rango superiore***

![[attachements/Pasted image 20240330101911.png]]
```pseudo
	\begin{algorithm}
	\caption{Link}
	\begin{algorithmic}
	\Procedure{Link}{$ x,y $}
\If{$ rank[x] > rank[y]  $}
  \State $ p[y]=x $
  \Else 
 \State $ p[x]=y $
 \If{$ rank[x]==rank[y]  $}
  \State $ rank[y]++ $
 \EndIf
 \EndIf
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```

```pseudo
	\begin{algorithm}
	\caption{Union}
	\begin{algorithmic}
\Procedure{Union}{$ x,y $}
	\State \Call{ Link }{\Call{ Find-Set }{$ x $},\Call{ Find-Set }{$ y $}}
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```
#### Compressione di Cammini
>*Serve nel corso della $\text{Find-Set}$, fa puntare direttamente alla radice ogni nodo del cammino d'accesso al nodo dato*
>*Migliora la complessità asintotica se si eseguono più $\text{Find-Set}$ che $\text{Union}$*

![[attachements/Pasted image 20240330102722.png]]


#### Complessità Up-Tree
>[!Lemma]
>Per tutte le radici $x$ di alberi $\text{size}[x]\geq 2^{\text{rank[x]}}$
>>[!done] In breve
>>Un albero con radice in $x$ ha un numero di nodi minimo di $2^{\text{ rango di x}}$

##### Dimostrazione
>*Dimostrazione per [[../../Analisi/Tipologie di Dimostrazioni#Principio di induzione|induzione]], se è vero per un rango più piccolo è vero per un rango più grande*

>[!abstract] Passo 0

Passo base, banale:
- $\text{rank}[x]=0$

>[!abstract] Passo Induttivo

- Sia $T$ un albero di rango $r$, radice $x$
>[!question] Cerchiamo il minimo $\text{size[x]}$ possibile

$T$ è derivato da una unione di $T_{1}$ e $T_{2}$
- $x$ era radice di $T_{1}$
> Per ***ipotesi induttiva***:
- $size[T_{1}]\geq 2^{\text{rank}[T_{1}]}$ e $size[T_{2}]\geq 2^{\text{rank}[T_{2}]}$

>*Per ottenere un albero di rango $r+1$ devo unire due alberi di rango uguale*

Il rango di $T_{1}=r-1$

>$T$ *viene dall'unione di 2 alberi di rango $\text{rank[T]-1}$*

- Se rango di $T_{1}$ fosse $r$, $\text{size[T]}>\text{size}[T_{1}]\geq2^{\text{rank[T1]}}$ per ***ipotesi induttiva***

Il rango di $T_{2}=$ rango di $T_{1}$, quindi rango di $T_{2}=r-1$

Quindi:
$$
\text{size[T]}\geq 2^{rank[T_{1}]}+2^{rank[T_{2}]}=2^{r-1}+2^{r-1}=2\cdot2^{r-1} = 2^r
$$
