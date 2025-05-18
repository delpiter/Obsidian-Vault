## B-Tree
---
> Famiglia di ***indici multilivello*** che soddisfa i tre requisiti.

Esistono molte varianti tra cui:
- $B$-Tree.
- $B^{*}$-Tree.
- $B^{+}$-Tree.

>[!definizione] $B$-Tree
>Un $B$-Tree è un [[Gli Alberi|albero]] direzionato a più vie *perfettamente bilanciato*, organizzato a nodi che corrispondono a **blocchi di dati** (pagine) di uno storage device.

Siano $g,h>0$ due numeri naturali, rispettivamente **ordine** e **altezza** del $B$-Tree
- L'ordine corrisponde al ***numero minimo di chiavi*** in un nodo **non** radice.

Un $B$-Tree $\tau$ della classe $\tau(g,h)$ ha le seguenti *proprietà*:
1. *Ogni percorso* dalla **radice** a una foglia ha sempre la *stessa lunghezza* $h$, chiamata ***altezza***.
2. Ogni nodo, a eccezione della **radice** e delle **foglie**, ha almeno $g+1$ figli.
3. La radice e ogni **nodo intermedio** hanno al più $2g+1$ nodi figli.

### Organizzazione
> Un $B$-Tree è organizzato a *nodi*.

1. Ogni nodo intermedio o foglia memorizza tra $g$ e $2g$ *chiavi*, la radice può contenere da $1$ a $2g$ chiavi -> Può avere da $0$ a $2g+10$ figli.
2. Un nodo intermedio con $l$ *chiavi* ($g\leq l\leq2g$) ha $l+1$ puntatori ad **altrettanti nodi figli**.
3. In ogni nodo le chiavi sono memorizzate in ***ordine decrescente***.

![[BTree.png]]

>Sia $k_{i}$ un generico valore di chiave:

Per $i=1,\dots,l-1$
- $p_{i}$ è *puntatore* al **record** con valore di chiave $k_{i}$.
- $q_{i-1}$ è *puntatore* al **nodo figlio** che contiene valori chiave valori di chiave $k<k_{i}$
- $q_{i}$ è *puntatore* al **nodo figlio** che contiene valori di chiave $k_{i}<k<k_{i+1}$

Per $i=l$
- $q_{l}$ è il *puntatore* al **nodo figlio** che contiene valori $k>k_{l}$.

### Insieme dei Valori
> Sia $K(q_{i})$ l'insieme dei **valori di chiave** del sottoalbero la cui radice è il nodo $p$ di indirizzo $q_{i}$.

Si ha:
- $\forall y\in K(q_{0}): (y<k_{1})$
- $\forall y\in K(q_{i}): (k_{i}<y<k_{i+1})\quad i=1,2,\dots,l-1$
- $\forall y\in K(q_{l}):(k_{l}<y)$

```pseudo
	\begin{algorithm}
	\caption{Ricerca in un B-Tree}
	\begin{algorithmic}
	\State $ q=root $
	\State $ s=null $
	\State $ found = False $
	\While{$q\neq null \text{ AND } !found$}
	\State $ s=q $
	\If{$ y<k_1  $}
	\State $ q=q_0 $
	\Elif{$\ \exists i(y=k_i)$}
	\State $ found=True $
	\Elif{$\ \exist i (k_i<y<k_i+1)$}
	\State $ q=q_i $
	\Else
	\State $ q=q_l $
	\EndIf
    \EndWhile
	\end{algorithmic}
	\end{algorithm}
```
> Al termine della ricerca:
- Se $found=True$ allora $q$ punta al nodo dove risiede il valore cercato $y$.
- Altrimenti $q=null$ e $s$ punta al nodo dove andrebbe inserito $y$.

### Evoluzione di un B-Tree
>[!tldr] Idea
>Le modifiche *partono sempre dalle foglie* e l’albero cresce o si accorcia "***verso l'alto***".

>[!abstract] Inserimento

> Non si "*appendono*" nuovi nodi alle foglie.
- Se il nodo foglia in cui verrebbe inserito il nuovo valore è "**piena**":
	- Si divide la foglia in ***due foglie allo stesso livello*** propagando un valore di chiave (*separatore*, solitamente il valore in "**mezzo**"), verso l'alto.

Questo modo di procedere possibile poiché i **nodi ai livelli superiori** ***non*** sono necessariamente *pieni*.
- Possono "*assorbire*" le informazioni che si propagano a partire dalle foglie.
- La propagazione degli effetti **sino alla radice** può provocare l’aumento dell’altezza dell’albero.

>[!missing] Rimozione

Se la chiave $y$ da cancellare si trova in una foglia $L$ si *rimuove*.
- Altrimenti, $y$ è rimpiazzato dal valore di chiave più piccolo del suo *sottoalbero di destra*.

![Understanding B-Trees: The Data Structure Behind Modern Databases](https://www.youtube.com/watch?v=K1a2Bk8NrYQ)

#### Proprietà B-Tree
>[!tip] Numero minimo di Nodi
>Il numero di nodi di un albero $\tau(g,h)$ è:
>$$IP_{\min}=1+2+2(g+1)+2(g+1)^{2}+\dots+2(g+1)^{h-2}=1+2\sum_{i=0}^{h-2}(g+1)^{i}$$

>[!tip] Numero massimo di Nodi
>$$IP_{\max}=\sum_{i=0}^{h-1}(2g+1)^{i}=\displaystyle{\frac{(2g+1)^{h}-1}{(2g+1)-1}}$$

>[!abstract] Altezza
>Se il $B$-Tree ha $n$ chiavi si ha:
>$$\lceil \log_{2g+1}(n+1)\rceil\leq h\leq\left\lfloor 1+\log_{g+1}\left( \displaystyle{\frac{n+1}{2}} \right) \right\rfloor$$

### Pro e Contro
>[!done] Pro
- Molto **efficiente** per *modifica* e *ricerca* dei singoli record.
- Esiste un **limite inferiore** all'utilizzo della memoria ($50\%$).

>[!fail] Contro
- Utilizzazione di **memoria** **media** è solo $69\%$.
- Non particolarmente adatto per ***elaborazioni di tipo sequenziale***, nell'ordine dei valori di chiavi e nel reperimento di chiave in un intervallo dato.
- La **ricerca del successore** di un valore di chiave può comportare la scansione di molti nodi.

### B*-Tree
>[!info] $B^{*}$-Tree
>Il $B^{*}$-Tree è una variante del $B$-Tree in cui l'utilizzazione dei nodi è almeno pari a $\frac{2}{3}$ invece di $\frac{1}{2}$.

### B+-Tree
>[!info] $B^{+}$-Tree
>In un $B$-Tree, i valori di chiave svolgono una *duplice funzione*:
>- **Separatori**.
>- **Valori di Chiave**.
>
>Nei $B^{+}$-Tree i sono mantenuti separati

Le foglie contengono **tutti i valori di chiave**
- La radice e i nodi interni, organizzati come un $B$-Tree costituiscono una "*mappa*" per consentire una rapida localizzazione delle chiavi e memorizzano i "*separatori*" di cammino.

>[!caution] Separatori
>In un $B^{+}$-Tree la sola funzione dei separatori è ***determinare il giusto cammino quando si ricerca una chiave***.
>È possibile che un **separatore** *non sia un valore di chiave presente* nel file dati.

Nel caso di chiavi alfanumeriche la scelta dei separatori è **particolarmente importante**.
- Facendo uso di separatori di lunghezza ridotta, si *risparmia spazio* e d eventualmente si *riduce l'altezza dell'albero*.

##### Ordine
>In un $B^{+}$-tree l’ordine è un concetto ancora significativo solo se si fa uso di ***separatori di lunghezza fissa***.

>[!info] Ipotesi
>*Ipotizziamo* che:
>1. La dimensione di un nodo sia fissa a $D$ `byte`.
>2. Ogni puntatore $q$ a nodi dell'albero richieda $len(q)$ `byte`.
>3. Si supponga che i separatori siano gli ***stessi valori di chiave*** di lunghezza $len(k)$.

Con queste ipotesi, si deriva, **trascurando l'header della pagina**, che l'ordine di un $B^{+}$-*Tree* è:
$$
g=\left\lfloor  \displaystyle{\frac{D-len(q)}{2(len(k)+len(q))}}\right\rfloor
$$
##### Numero di Foglie
> Il numero di foglie dipende dal *numero dei record* $nr$ presenti nel file, dalla dimensione $D$ e dall'utilizzazione delle foglie stesse.

- Si può dimostrare che l'utilizzazione media delle foglie $u$ è pari a circa $\ln(2)\approx 0.69$

>[!abstract] Numero di Foglie
>Trascurando il *puntatore alla foglia successiva* e considerando chiavi di lunghezza $len(k)$ e puntatori ai dati di lunghezza $len(p)$ il numero di foglie si può approssimare come:
>$$n=\left\lceil \displaystyle{\frac{nr\cdot(len(k)+len(p))}{D\cdot u}}\right\rceil $$

>[!caution] Altezza minima
>Si ottiene quando *tutti i nodi dei livelli intermedi* (radice compresa) sono ***pieni***.
>- Si ottiene $(2g+1)^{h-1}\geq n$
>
>Da cui si ricava
>$$h\geq 1+\lceil \log_{2g+1}n \rceil$$

>[!missing] Altezza Massima
>Caso peggiore, la radice contiene solo $2$ puntatori e ogni nodo dei livelli intermedi ne contiene $g+1$:
>$$2\cdot(g+1)^{h-2}\leq n$$
>- Quindi
>
>$$h\leq 2+\left\lfloor \log_{g+1}\left( \frac{n}{2} \right)\right\rfloor$$

#### Ricerca di Valori
> Il ***costo della ricerca*** di un singolo valore di chiave, misurato in numero di nodi visitati, è sempre pari all'altezza $h$.

Il caso medio id costo di ricerca nell'indice è superiore a quello che si ha con un $B^{+}$-Tree.
- Dovuto dal fatto che i valori di chiavi sono ***solo nelle foglie***.

#### Secondary $B^{+}$-Tree
>[!info] 
>In un $B^{+}$-tree per **chiavi secondarie**, per ogni valore di chiave "*si gestisce*" nelle foglie una ***lista di puntatori*** (`RID`) ai *record con quel valore* (Anche nota come *inverted index*).

