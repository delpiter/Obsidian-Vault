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