>[!info] Definizione
>Le *tabelle hash* sono una delle strutture dati ***più importanti***
>Caratterizzate dalla forma dei **dati**: 
>- *Coppia attributo / valore* (**key**, **value**)
>>[!example] Operazioni
>>- **Inserimento** di una *coppia* nella collezione
>>- **Cancellazione** di una *coppia* dalla collezione
>>- **Ricerca** di una *chiave*
>>- **Modifica** di un valore corrispondente a una *chiave*
## Direct Address Table
---
>[!info] Descrizione
>Una delle *hash table* più semplici
>Ogni chiave trova un posto nella tabella in funzione del suo valore
>$$\text{key value } = \text{ position in the vector}$$

![[attachements/image-removebg-preview 1.png]]
>[!done] Pro

Estremamente efficiente in termini di [[../../Confronto fra Algoritmi/Complessità di Algoritmi#Analisi di Complessità|complessità computazionale]].

```pseudo
	\begin{algorithm}
	\caption{DAT Search}
	\begin{algorithmic}
	\Procedure{Search}{$ V,k $}
\Return $ V[k] $
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```

```pseudo
	\begin{algorithm}
	\caption{DAT Insert}
	\begin{algorithmic}
	\Procedure{Insert}{$ V,x $}
\State $ V[key[x]] = x $
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```

```pseudo
	\begin{algorithm}
	\caption{DAT Delete}
	\begin{algorithmic}
	\Procedure{Delete}{$ V,x $}
\State $ V[key[x]] = NULL $
 \EndProcedure
	\end{algorithmic}
	\end{algorithm}
```

- Costi computazionali delle funzioni: $\Theta(1)$

>[!fail] Contro

Quando lo *spazio delle chiavi* è **enorme** e il numero di chiavi attive (*actual keys*) è molto **piccolo:**
- Avviene un grande ***spreco di memoria***

![[attachements/Pasted image 20240317162039.png]]

### Esempio
> Prendiamo come esempio l'**insieme delle persone** (*Italiane*)

>[!tip] ***Chiave***: Codice fiscale

- $MRGLCN68M03G273W$

>[!example] Spazio delle chiavi

- $9$ caratteri letterali $\to 21^9$
- $7$ cifre decimali $\to 10^7$

Numero di ***chiavi distinte***
- $21^9\cdot 10^7 =7.942.800.465.810.000.000$

 Numero di ***chiavi attive***
- Circa $60.000.000$
