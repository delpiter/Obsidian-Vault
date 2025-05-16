>[!definizione]
>Un ***indice*** può essere definito come struttura progettata per *ottimizzare le ricerche di record* che soddisfano un certo predicato di selezione.

Concettualmente è come una mappa che memorizza entrate come:
- `[Valore chiave di Ricerca, Riferimento ai record]`

>Due "*famiglie*" di indici principali:
- ***Order Index***: I valori di chiave sono mantenuti *ordinati*.
- Hash Index: I valori di chiave sono memorizzati in bucket i cui indirizzi sono generati da [[Funzione di Hash|funzioni Hash]].

## Hash Index
---
>[!info]
>Le entry: `[Valore chiave di Ricerca, Riferimento ai record]`, sono organizzate in una ***struttura hash***.

Organizzazione secondaria molto efficiente per ***ricerche su singolo valore***.
## Order Index
---
>[!tldr] Idea
>Consiste nell'associare al file dati una "*tabella*" in cui l’entrata $i$-*esima* memorizza una coppia del tipo $(k_{i},p_{i})$ dove: 
>- $k_{i}$ : È un ***valore di chiave*** dell’attributo su cui l’indice è costruito.
>- $p_{i}$ : È un *riferimento* al record con valore di chiave $k_{i}$.

> Accesso con *indice mono-livello*:

Ricerca del record con chiave $k_{i}$:
1. **Accesso** all'indice.
2. **Ricerca** della coppia $(k_{i},p_{i})$.
3. **Conversione** di $p_{i}$ in indirizzo assoluto.
4. **Accesso** al blocco dati.

Poiché l'indice contiene un insieme di valori chiave, le coppie $(k_{i},p_{i})$ possono essere mantenute ordinate in base ai valori $k_{i}$.
- Al fine di potere applicare la [[Recursive Functions#Un Algoritmo Ricorsivo Ricerca Binaria|ricerca binaria]].
- Permette risparmi più **grandi** tanto più è **grande** la ***differenza di dimensione*** in `byte` tra *chiave* e *record intero*.

#### Tipi di Indice Ordinato
---
<table border="1" cellpadding="8" cellspacing="0"> <thead> <tr> <th>Caratteristica</th> <th>Denominazione</th> <th>Significato</th> </tr> </thead> <tbody> <tr> <td rowspan=2 ><em>Unicità dei valori di chiave</em></td> <td>Primary (unique) index</td> <td>Indice su un attributo (o combinazione di attributi) che assume valori unici (non ripetuti)</td> </tr> <tr> <td>Secondary index</td> <td>Indice su un attributo (o combinazione di attributi) che può assumere valori ripetuti</td> </tr> <tr> <td rowspan=2><em>Ordinamento del file dati</em></td> <td>Clustered index</td> <td>Indice su un attributo (o combinazione di attributi) secondo cui il file dati è ordinato</td> </tr> <tr> <td>Unclustered index</td> <td>Indice su un attributo (o combinazione di attributi) secondo cui il file dati non è ordinato</td> </tr> <tr> <td rowspan=2><em>Numero di coppie nell’indice</em></td> <td>Dense index</td> <td>Indice in cui il numero di coppie <span class="math display">(k_i,p_i)</span> è pari al numero di record dati</td> </tr> <tr> <td>Sparse index</td> <td>Indice in cui il numero di coppie <span class="math display">(k_i,p_i)</span> è minore del numero di record dati</td> </tr> <tr> <td rowspan=2><em>Numero di livelli dell’indice</em></td> <td>Single-level index</td> <td>Indice organizzato in modo “flat”</td> </tr> <tr> <td>Multi-level index</td> <td>Indice organizzato in più livelli (albero)</td> </tr> </tbody></table>

> *Quasi* tutte le **combinazioni** di tipi di indice sono possibili.

>[!fail] Incompatibilità
>L'unica incompatibilità è data dalla combinazione ***sparse*** e ***unclustered***.

### Indici Multilivello
>Per ragioni di efficienza un indice in memoria secondaria è ***organizzato in più livelli***.

La soluzione più comune per un indice si basa su [[Gli Alberi Binari|alberi binari]] bilanciati.



>[!example] Indice multilivello a blocchi
>Un indice multilivello per memoria secondaria ***deve soddisfare i seguenti requisiti***:
>1. *Bilanciamento*: Deve essere bilanciato considerando i blocchi e non i singoli nodi.
>2. *Occupazione minima*: Si deve poter stabilire un limite inferiore all'utilizzazione di blocchi.
>3. *Efficienza di Aggiornamento*: I due requisiti espressi devono essere soddisfatti garantendo che le operazioni abbiano un ***costo limitato***.

![[UnbalancedTree.png|400]]
- *Albero sbilanciato rispetto ai blocchi ma bilanciato rispetto ai nodi*.

#### B-Tree
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

##### Organizzazione
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

##### Insieme dei Valori
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

##### Evoluzione di un B-Tree
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

##### Proprietà B-Tree
>[!tip] Numero minimo di Nodi
>Il numero di nodi di un albero $\tau(g,h)$ è:
>$$IP_{\min}=1+2+2(g+1)+2(g+1)^{2}+\dots+2(g+1)^{h-2}=1+2\sum_{i=0}^{h-2}(g+1)^{i}$$

>[!tip] Numero massimo di Nodi
>$$IP_{\max}=\sum_{i=0}^{h-1}(2g+1)^{i}=\displaystyle{\frac{(2g+1)^{h}-1}{(2g+1)-1}}$$

>[!abstract] Altezza
>Se il $B$-Tree ha $n$ chiavi si ha:
>$$\lceil \log_{2g+1}(n+1)\rceil\leq h\leq\left\lfloor 1+\log_{g+1}\left( \displaystyle{\frac{n+1}{2}} \right) \right\rfloor$$

##### Pro e Contro
>[!done] Pro
- Molto **efficiente** per *modifica* e *ricerca* dei singoli record.
- Esiste un **limite inferiore** all'utilizzo della memoria ($50\%$).

>[!fail] Contro
- Utilizzazione di **memoria** **media** è solo $69\%$.
- Non particolarmente adatto per ***elaborazioni di tipo sequenziale***, nell'ordine dei valori di chiavi e nel reperimento di chiave in un intervallo dato.
- La **ricerca del successore** di un valore di chiave può comportare la scansione di molti nodi.

#### B*-Tree
>[!info] $B^{*}$-Tree
>Il $B^{*}$-Tree è una variante del $B$-Tree in cui l'utilizzazione dei nodi è almeno pari a $\frac{2}{3}$ invece di $\frac{1}{2}$.

#### B+-Tree
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

