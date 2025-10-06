>[!help] Pattern
>Le computazioni di tipo ***stencil*** coinvolgono una griglia i cui valori sono aggiornati secondo un *pattern fisso* chiamato ***stencil***.

Problema di tipo [[Embarrassingly Parallel]].

Le computazioni ***stencil*** utilizzano, solitamente, *due domini*.
- Uno per i **valori correnti**.
- Uno per i **prossimi valori**.
> I due domini verranno ***invertiti*** alla fine di una computazione

## Tipi di Stencils
---
>[!hint] `2D` Stencils

![[2DStencils.png]]

- Solitamente gli *stencil* sono forme **regolari**, ma nulla vieta di avere forme **irregolari**.

>[!tip] `3D` Stencils

![[3DStencils.png]]

## Ghost Cells
---
>[!question] Come gestisco le celle situate ai bordi?

Uno *stancil* applicato ai bordi di un **dominio**, ha alcune celle che escono dal dominio stesso.

>[!done] Soluzione

***Estendo il dominio*** di un numero di celle pari a quanto è grande lo *stancil*.
- Es. Von Neumann neighborhood -> Estensione di $1$ **cella**.
Si estende il dominio cosicché le celle ai bordi ***non*** richiedono un **trattamento speciale**.

>[!missing] Ghost Area
>L'insieme di queste nuove "*ghost cells*" viene chiamata ***ghost area***.

### Valori nella Ghost Area
>[!static] Valori Statici
>Per alcune applicazioni, le *celle fuori dal dominio* hanno un ***valore fisso***, in base all'applicazione.

>[!failure] Valori Ciclici
>In alcuni casi, possiamo assumere un "***confine ciclico***".

> Possibilità
- ***Copiare*** i valori nella *ghost cell*.
- ***Condizioni cicliche***.

#### Condizioni Cicliche
> Si applicano delle condizioni cicliche alla sezione di codice che calcola i "*vicini*".

```c
int i, j;
for(i=0; i<n; i++)
{
	for(j=0; j<n; j++)
	{
		B[i][j]=f(A[i][j],
				  A[i][(j-1+n)%n],
				  A[i][(j+1)%n],
				  A[(i-1+n)%n][j],
				  A[(i+1)%n][j]);
	}
}
```

La soluzione appena descritta funziona, ma ha un ***problema di efficienza***.
- Alcuni processori non hanno l'operazione di `%` nell'hardware, quindi potrebbe essere sostituita con *diverse istruzioni*.
	- L'esecuzione di a funzione ha un costo di $6$ *addizioni* e $4$ *divisioni intere*, che potrebbero essere trasformate in **numerose istruzioni**.

>[!fail] La soluzione risulta essere molto inefficiente.

#### Periodic Boundary Conditions
> Modalità di riempimento delle ***ghost cells*** tramite *copiatura* degli elementi.

***Prima Modalità***:
- Più semplice da implementare ma ***meno efficiente***, richiede `8` **operazioni**.
	- Vengono copiati i quattro lati nella ***ghost area opposta***.
	- Successivamente bisogna impostare i *quattro angoli*.

![[PeriodicBoundaryCondition.png]]


>***Seconda Modalità***
- Leggermente più *complicata* da implementare, ma richiede solamente `4` **operazioni**.
	- Partendo da qualsiasi lato del dominio, si copia l'intera riga nel lato opposto, considerando anche la ***ghost area*** (*anche se vuota*).
	- Ripetere il procedimento per tutti e quattro i lati.

![[PeriodicBoundaryConditionAlternative.png]]

## Parallelizzare gli Stencil
---
> Calcolare il "*dominio successivo*" ha una struttura [[Embarrassingly Parallel]].

```pseudo
	\begin{algorithm}
	\caption{Parallelizing Stencil Computations}
	\begin{algorithmic}
	\State $ \text{Initialize current domain} $
	\While{$!\text{terminated}$}
	\State $ \text{Initialize ghost cells} $
	\State $ \text{Compute next domain in parallel}$
	\State $ \text{Exchange current and next domains}$
    \EndWhile
	\end{algorithmic}
	\end{algorithm}
```

>[!check] Architettura a Memoria Distribuita
>Le ***ghost cells*** sono essenziali per implementare efficientemente gli algoritmi *stencil* su un sistema a [[Git-Obsidian/Architettura degli Elaboratori/Architetture a Confronto/Architetture Parallele#Multicomputer|memoria distribuita]].

Dopo la partizione dei blocchi è necessaria una fase di *scambio di informazione* in modo tale che ciascuno abbia la ***propria ghost area completa***.
