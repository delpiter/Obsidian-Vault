## Clustering

> [!tl;dr] Definizione
> Con il termine [[Tipi di Machine Learning#Clustering|clustering]] si denota una famiglia di metodi [[Tipi di Machine Learning#Apprendimento|non supervisionati]] in grado di individuare ***raggruppamenti intrinseci di pattern*** nello spazio multidimensionale.

Opzionalmente si definisce in corrispondenza di tali raggruppamenti le classi (***incognite***).

Il clustering ha applicazioni in numerose discipline come:
- Pattern recognition
- Machine Learning
- Computer vision
- Data mining
- etc

![[attachements/Clustering.png]]

Il problema è molto complesso ([[../Algoritmi e Strutture Dati/Complessità/Classi P e NP|NP-Hard]])
- Determinare la soluzione ottima con ricerca esaustiva è possibile solo nei casi semplici con pochi pattern.

### Numero di Soluzioni
> [!todo] Calcolo
> Dati $n$ pattern, assumendo di conoscere $s$ il numero di gruppi, il numero di soluzioni è dell'ordine di $\displaystyle{\frac{s^{n}}{s!}}$.

Anche per esempi molto piccoli come $n=100$ e $s=5$ il numero totale di soluzioni è $\approx 10^{67}$

Se $s$ non è noto, il numero di soluzioni è dato dal [[../Matematica Discreta e Probabilità/Combinatoria/3 - Partizioni#Triangolo di Bell|numero di bell]] ottenibile sommando i casi precedenti per tutti i valori di $s$ da $1$ a $n$.
### Criteri di Clustering
> Criteri e algoritmi di clustering sono due cose ben distinte

> [!abstract] Criteri vs algoritmi
> **Criteri di clustering**: descrivono _cosa_ si vuole ottenere, specificando il grado di ottimalità di ogni soluzione ammissibile.
> **Algoritmi di clustering**: dato un criterio, forniscono una procedura algoritmica per determinare soluzioni che lo ottimizzano.

La maggior parte dei criteri di clustering si fonda su due osservazioni:
1. **Similarità**: i pattern all'interno dello stesso cluster devono essere tra loro più simili rispetto a pattern appartenenti a cluster diversi.
2. **Densità**: i cluster sono costituiti da nuvole di punti a densità relativamente elevata, separate da zone a densità più bassa.

> 
- [[#Minimizzazione distanze dai centroidi]]
- [[#Minimizzazione distanze intra-classe]]
#### Minimizzazione distanze dai centroidi
>[!tldr] Idea
>Minimizza la ***somma dei quadrati delle distanze*** dei pattern $x$ dai centroidi delle classi
>$$cJ_{e}=\sum_{i=1,\dots,s}\sum_{x\in C_{i}} \| x-\overline{x}_{i} \|^{2}, \qquad \overline{x}_{i}=\frac{1}{n_{i}}\sum_{x\in C_{i}} x$$

- La *sommatoria esterna* fa una **media**
- La *sommatoria interna* calcola la **distanza euclidea relativa** ad un centroide

> Dove
- $C_{i}$ è l'$i$-esimo cluster
- $n_{i}$ il numero di pattern che contiene e $\overline{x}_{i}$ il suo centroide.

È un buon criterio per cluster a simmetria radiale, ma ***penalizza forme allungate*** o *cluster innestati*.
#### Minimizzazione distanze intra-classe
> [!tldr] Idea
> Minimizza le distanze tra il **pattern** e il **cluster** a cui appartiene.
> $$J_{e}=\sum_{i=1,\dots,s}n_{i}\cdot \overline{s}_{i},\qquad \overline{s}_{i}=\frac{1}{n_{i}}\sum_{x\in C_{i}}f_{s}(x,C_{i})$$

Dove $f_{s}(x,C_{i})$ è una misura di distanza tra $x$ e il cluster a cui appartiene.

Se scegliamo $f_{s}$ come $\frac{1}{n_{i}}\sum_{x'\in C_{i}}\| x-x'\|^{2}$, il criterio è *simile a quello della minimizzazione delle distanze dai centroidi*.

Se invece scegliamo: $f_{s}(x,C_{i})=\displaystyle\min_{x'\in C_{i}, x'\neq x} \| x-x'\|^{2}$
- Questo non penalizza cluster allungati, infatti è sufficiente che un pattern di $C_{i}$ sia vicino a $x$.

### Algoritmi di Clustering

> [!summary] Clustering gerarchico
> Tramite operazioni tipicamente _bottom-up_ che aggregano i pattern in base a una misura di distanza, i dati vengono organizzati in una struttura ad albero (***Dendrogramma***).

> [!help] Clustering basato su centroidi
> Tramite ***tecniche euristiche iterative*** si individuano i cluster minimizzando la distanza dei pattern dai centroidi dei cluster a cui appartengono.

Algoritmi principali:
- [[K-means]]
- [[Fuzzy k-means]]
- [[Expectation Maximization]] (***gaussian mixture***)


> [!hint] Clustering basato sulla densità
> I cluster individuati sono ***regioni connesse in aree ad elevata densità***.

L'approccio più noto è ***DBSCAN***.
#### Hard vs soft clustering


> [!caution] Clustering hard (esclusivo)
> Ogni pattern è assegnato in ***modo esclusivo a un solo cluster***.


> [!tip] Clustering soft (fuzzy)
> I pattern appartengono ai diversi cluster con un ***certo grado di appartenenza***, compreso tra $0$ e $1$.

È più efficace nel gestire:
- pattern vicini al bordo di due o più cluster
- Pattern ***Outlier***


> [!hint] Osservazione  
> Un *clustering soft* può diventare *esclusivo* scegliendo, per ogni pattern, il cluster verso cui il ***grado di appartenenza è massimo***.

Quindi, prendendo il massimo nel vettore dei gradi di appartenenza, da un clustering soft si ottiene sempre un clustering hard.

#### Clustering Gerarchico
> Simile al modo di eseguire classificazione in tassonomia biologica:

Gli insetti sono ***gerarchicamente classificati***, specializzandone le specie a partire da famiglie molto ampie fino a famiglie più ridotte.

Gli algoritmi sono generalmente *bottom-up* (***agglomerativi***)

> [!tldr] Idea
> Si parte cercando di ***aggregare singoli elementi***
> - Ad ogni passo si aggregano *pattern a pattern*, *pattern a cluster* o *cluster a cluster* gli elementi tra loro più simili (per esempio **per distanza minore**) rispetto a una soglia che dipende dal livello.

Le principali differenze implementative dipendono dalla definizione usata per calcolare le distanze tra cluster:
- ***Single Link***: Distanza *minima* tra due pattern dei cluster
- ***Average Link***: Distanza *media* tra i pattern dei due cluster
- ***Complete Link***: Distanza *massima* tra due pattern dei cluster

![[attachements/HierarchyClustering.png]]