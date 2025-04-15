## Data Manipulation Language
---
> TODO

### Operatori
#### SELECT
> Le operazioni di *interrogazione* vengono implementate dal costrutto `{sql icon} SELECT` 

Specifica quali **colonne** delle **righe selezionate** devono comparire nel **risultato finale**.
- Possibile **ridenominare** le colonne del risultato di una query con la **clausola** `{sql icon}AS`.  
- Possibile usare **espressioni aritmetiche** **semplici** sui valori degli attributi di una select

```sql
SELECT attribute1 AS attr, attribute2
FROM ...
```

> Se si vogliono selezionare tutti gli attributi si può usare: `*`.

##### TOP
> L'operatore *select* con la **clausola** `{sql icon} TOP(n)` serve a selezionare le prime $n$ tuple del **risultato della query**.

Spesso usato insieme all'[[#ORDER BY|operatore di ordinamento]].

```sql
SELECT TOP(5) attribute1
FROM ...
```

>[!hint] Causola "WITH TIES"
>La clausola ***WITH TIES*** si può usare solo in presenza di *ORDER BY*.
>Vengono **mantenuti i pareggi**.

```sql
SELECT TOP(5) WITH TIES attribute1
FROM ...
```

Se la 5a e 6a tupla sono in **pareggio** dopo l'ordinamento *vengono ritornate entrambe*.
#### FROM
>Specifica la ***lista di tabelle*** a cui si deve accedere.

È possibile cambiare nome con la **clausola** `{sql icon} AS`.
- La *keyword* `{sql icon} AS` si può omettere.

In caso di **più tabelle con attributi** con nome **uguali**.
- È necessario **specificare la tabella** per risolvere **l’ambiguità**  (`TableName.AttrName`).

```sql
SELECT attribute1 AS attr, attribute2
FROM table1 AS t1, table2
```

##### JOIN
> Utilizzato nella clausola **FROM**.

Utilizzato al posto di fare il **prodotto cartesiano** e poi *filtrare* le righe nella clausola **WHERE**.

```sql
SELECT attribute1 AS attr, attribute2
FROM table1 AS t1 JOIN table2 ON table1.attr=table2.attr
```

Sono possibili anche:  
- **LEFT JOIN**.
- **RIGHT JOIN**.
- **FULL JOIN**.
#### WHERE
> Usato per selezionare **quali righe** delle tabelle devono **comparire nel risultato finale**.

Le tuple vengono selezionate attraverso una **espressione booleana** o una *combinazione di espressioni*.

>[!missing] Valori nulli
>Il trattamento dei [[Informazione Incompleta#Null|valori nulli]] si basa su quanto già visto in [[Algebra Relazionale]].
>- Logica a tre valori: **Vero**, **Falso** e **Sconosciuto**.

```sql
SELECT attribute1 AS attr, attribute2
FROM table1 AS t1 JOIN table2 ON table1.attr=table2.attr
WHERE condition1 AND condition2
```

In assenza della clausola `{sql icon} JOIN` è possibile sostituirla con un ***predicato di join***.
- Il predicato stabilisce il ***criterio*** con cui le tuple *devono essere combinate*.
##### Confronti fra String
>[!options] Operatore **LIKE**
>Permette di esprimere *pattern su stringhe* mediante ***wildcard***.

L'operatore `{sql icon} LIKE` ammette le seguenti wildcards:
- `_`: *Carattere arbitrario*.
- `%`: *Sequenza di caratteri arbitrari*.

```sql
SELECT attribute1 AS attr, attribute2
FROM table1 AS t1 JOIN table2 ON table1.attr=table2.attr
WHERE attr LIKE 'M_R%0'
```

> Seleziona le stringhe che iniziano con la *M*, ha *R* come terza lettera e finisce con *O*.

##### BETWEEN
>Consente di verificare l’*appartenenza di un valore* ad un certo **range di valori**.

```sql
SELECT attribute1 AS attr, attribute2
FROM table1 AS t1 JOIN table2 ON table1.attr=table2.attr
WHERE attr BETWEEN(n1,n2)
```

> I valori `n1` e `n2` sono *inclusi nel range*.

##### IS NULL
> Controlla se il valore di un attributo è *nullo*.

```sql
SELECT attribute1 AS attr, attribute2
FROM table1 AS t1 JOIN table2 ON table1.attr=table2.attr
WHERE attr IS NULL
```

È possibile invertire la condizione: `{sql icon} IS NOT NULL`.
#### ORDER BY
> Usato per ***ordinare il risultato*** di una query secondo i valori di uno più attributi.

Inserito dopo la clausola `{sql icon} WHERE`.
- Bisogna specificare se l'ordinamento è per valori ***ascendenti*** (`{sql icon} ASC` *default*) oppure ***discendenti*** (`{sql icon} DESC`).

```sql
SELECT attribute1 AS attr, attribute2
FROM table1 AS t1 JOIN table2 ON table1.attr=table2.attr
WHERE condition
ORDER BY attr1 ASC, attr2 DESC
```

#### EXIST
> Condizione di **esistenza**.
 
 Ritorna un *valore booleano* in base a **quante righe** vengono riportate nella ***query interna***.
 - $0$ Righe: `False`.
 - $>0$ Righe: `True`

```sql
SELECT attribute1 AS attr, attribute2
FROM table1 AS t1 JOIN table2 ON table1.attr=table2.attr
WHERE EXISTS (SELECT * ...)
```

È possibile invertire la condizione: `{sql icon} NOT EXISTS`.
- È vero se la [[Query Annidate|subquery]] ***non*** restituisce alcuna tupla.

>[!hint] Non molto utile se la subquery ritorna sempre lo stesso risultato
>Quando la tupla **non dipende** dalla specifica tupla del *blocco esterno*.

#### IN
>Controlla se il valore di un attributo è **contenuto** in una *lista di valori*.

```sql
SELECT attribute1 AS attr, attribute2
FROM table1 AS t1 JOIN table2 ON table1.attr=table2.attr
WHERE attr IN list
```

È possibile invertire la condizione: `{sql icon} NOT IN`.

>[!cite] Query Annidate
>Al posto di una lista di attributi "*statica*" è possibile inserire una [[Query Annidate|query annidata]].
#### ANY
>La riga soddisfa la condizione se è **vero** il confronto fra il valore di un attributo e ***almeno uno*** dei valori in una *lista*.

```sql
SELECT attribute1 AS attr
FROM table1 AS t1 JOIN table2 ON table1.attr=table2.attr
WHERE attr ANY list
```

Come `{sql icon} IN` la lista di elementi può essere sostituita con ***query annidate***.
#### ALL
>La riga soddisfa la condizione se è **vero** il confronto fra il valore di un attributo e ***tutti*** i in una *lista*.

```sql
SELECT attribute1 AS attr
FROM table1 AS t1 JOIN table2 ON table1.attr=table2.attr
WHERE attr ALL list
```

Come `{sql icon} IN` la lista di elementi può essere sostituita con [[Query Annidate|query annidate]].
#### Operatori Insiemistici
> Combinano i risultati di due istruzioni `{sql icon} SELECT`.

Gli **attributi** della `{sql icon} SELECT` **devono avere** **tipi** di dato **compatibili** e gli *stessi nomi*.

L'ordine degli ***elementi è importante***.

>[!help] Il risultato è sempre privo di duplicati
>Per mantenerli occorre aggiungere l'opzione `{sql icon} ALL`.

**UNION**
- Unione di *tutte le righe* senza ripetizioni.
**INTERSECT**
- Selezionate solamente le *righe comuni.*
**EXCEPT**
- Selezionate *tutte le righe* della tabella $A$ che **non sono** nella tabella $B$.
#### Operatori Aggregati
>Operatori che si applicano a **gruppi di tuple** e restituiscono sempre ***una sola riga***.

Inseriti nella select e **valutati dopo** la clausola `{sql icon} WHERE`.
 
 >[!summary] Tipologie

`{sql icon} COUNT(*)`
- Restituisce il *numero delle righe*.

`{sql icon} SUM(attr)`
- Restituisce la *somma dei valori* della colonna.

`{sql icon} MAX(attr)`
- Restituisce il *valore massimo* della colonna.

`{sql icon} MIN(attr)`
- Restituisce il *valore minimo* della colonna.

`{sql icon} AVG(attr)`
- Restituisce la *media dei valori* della colonna.
- A volte necessario fare il casting dell'argomento
	- `{sql icon} SELECT AVG(CAST(attr AS decimal(n,m)))`.

```sql title:Esempio
SELECT COUNT(*) AS n, SUM(attr) AS sum, AVG(attr) AS avg
FROM tableName
```

>[!warning] Attenzione
>Se si usano funzioni aggregate, la **SELECT** non può includere altri elementi che non siano a loro volta ***funzioni aggregate***.

####  GROUP BY
> Consente di **dividere in gruppi**, ognuno caratterizzato da un *valore comune* dell’attributo uguale.

>[!todo] Produce **una sola linea** nel risultato finale **PER ogni gruppo**
>

```sql
SELECT attributeList1, COUNT(*) AS Nattr
FROM table1
WHERE condition
GROUP BY attributeList2
```

>[!Warning] Attenzione
>L'insieme di attributi nella `{sql icon} SELECT` ***deve essere*** un sottoinsieme dell'insieme di attributi nel `{sql icon} GROUP BY`.
>$$\text{attributeList}_{1}\subseteq \text{attributeList}_{2}$$

##### Ragionamento
>[!info] Come si ragiona con il GROUP BY

Le tuple che soddisfano la clausola `{sql icon} WHERE`
- Sono raggruppate per *valori uguali* della/e colonna/e presenti nella **clausola** `{sql icon} GROUP BY`.

Infine a *ciascun gruppo* viene applicata una eventuale ***operazione aggregata***.

>[!example] Esempio
>Per ogni ruolo, visualizzare lo stipendio medio nelle sedi di Milano.

```sql
SELECT I.Ruolo, AVG(I.Stipendio) AS AvgStip
FROM Impiegati AS I JOIN Sedi AS S ON (I.Sede=S.Sede)
WHERE S.Citta='Milano'
GROUP BY I.Ruolo
```

##### Condizioni sui Gruppi
>È possibile *selezionare alcuni gruppi* sulla base di loro proprietà "***complessive***".

La clausola `{sql icon} HAVING` funge da ***filtro*** sui vari **gruppi**.  
* Usata dopo la clausola `{sql icon} GROUP BY`.

Si possono avere *due tipi di predicati*:
- Predicati con ***funzioni aggregate***.
- Predicati che si riferiscono alle ***colonne di raggruppamento***.
	- Questi si possono inserire anche nella clausola `{sql icon} WHERE`

```sql
SELECT I.Ruolo, AVG(I.Stipendio) AS AvgStip
FROM Impiegati AS I JOIN Sedi AS S ON (I.Sede=S.Sede)
WHERE S.Citta='Milano'
GROUP BY I.Ruolo
HAVING AVG(I.Stipendio)>1000
```


### Ordine delle Operazioni
>[!info]
>L'ordine degli operatori in [[SQL]] è *importante* per garantire che i dati vengano **elaborati correttamente**. Di seguito è riportato l'***ordine logico*** in cui **SQL** esegue le clausole all'interno di una query

1. **FROM**
2. **WHERE**
	- *Valutazione degli aggregati*.
3. **GROUP BY**
4. **HAVING**
5. **SELECT**
6. **ORDER BY**

## Viste
---
>[!cite] Tabelle Virtuali
>Mediante l’istruzione `{sql icon} CREATE VIEW` si definisce una ***vista***, ovvero una "***tabella virtuale***".
>Rappresentano tabelle ottenute da ***dati contenuti in altre tabelle***.
>Le tuple della vista sono il risultato di una query che viene *valutata* dinamicamente *ogni volta* che si fa **riferimento** alla vista.


Ogni ***vista*** ha associato un *nome* e una *lista di attributi*, dati dal risultato di una select.

```sql
CREATE VIEW viewName(attr1,attr2,...)
AS
	SELECT attr1,attr2,...
	FROM table1 t1 JOIN table2 t2 ON t1.attr=t2.attr
	WHERE condition
```

>[!tldr] I dati **non** sono fisicamente memorizzati a parte.
>I dati *dipendono* semplicemente da ***altre tabelle***.  
 
 >Servono a:
- Implementare *meccanismi di indipendenza* tra livello **logico** e il livello **esterno**.  
- **Semplificare interrogazioni** complesse.
- Garantire **Retro-compatibilità** con precedenti versioni di schema in caso di *restrutturazione*.

### Aggiornabilità
> Una vista è una funzione che calcola un risultato $y$ a partire da una istanza $r$ ($V(r)=y$)

>[!attention] Aggiornamento di una vista
>L'***aggiornamento di una vista*** che trasforma $y$ in $y'$, può essere eseguito se e solo se è univocamente definita la nuova istanza $r'$ tale che $V(r')=y'$.

Ciò corrisponde a dire che la vista è "***invertibile***", $V^{-1}(y')=r'$
- I [[Git-Obsidian/DataBase/Introduzione#DBMS|DBMS]] pongono dei limiti sulle tipologie di viste che possono essere aggiornate.

>[!summary] Restrizioni Comuni
>- `{sql icon} GROUP BY`
>- [[#Operatori Aggregati|Funzioni Aggregate]]
>- `{sql icon} DISTINCT`
>- `{sql icon} JOIN`

### Check Option
>[!info]
>La clausola `{sql icon} WITH CHECK OPTIONS` garantisce che **ogni tupla** inserita nella vista sia anche restituita dalla vista stessa.

> Tipi di *check option*:
- `CASCADED`
- `LOCAL`
## Manipolazione dell’Istanza
---
> Istruzioni che permettono di aggiornare il ***data base***.

>[!abstract] `{sql icon} INSERT`
> L'operatore *INSERT* permette di **inserire** nuove tuple in una ***tabella specificata***.

```sql
INSERT INTO tableName(attr1,attr2,attr3,...) VALUES(val1,val2,val3,...)
```

È possibile inserire multiple tuple che rappresentano il ***risultato di una query***.

```sql
INSERT INTO tableName(attr1,...)
SELECT attr1,...
FROM tableName2
WHERE condition
```

>[!fail] `{sql icon} DELETE`
>**Cancella** le tuple dalla ***tabella specificata***.


>[!caution] `{sql icon} UPDATE`
>**Modifica** le tuple della ***tabella specificata***.

```sql
UPDATE tableName
SET attribute1=value1,...
```

Le istruzioni **DELETE** e **UPDATE** possono fare uso di una condizione per specificare le *tuple da cancellare*/*modificare*.

```sql
DELETE FROM tableName
WHERE condition
```
