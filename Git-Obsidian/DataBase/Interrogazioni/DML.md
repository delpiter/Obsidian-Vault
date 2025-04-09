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

##### IN
>Controlla se il valore di un attributo è **contenuto** in una *lista di valori*.

```sql
SELECT attribute1 AS attr, attribute2
FROM table1 AS t1 JOIN table2 ON table1.attr=table2.attr
WHERE attr IN list
```

È possibile invertire la condizione: `{sql icon} NOT IN`.

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

##### EXIST
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

* #### Operatore **ANY**
  * La riga soddisfa la condizione se è vero il confronto fra il valore di un attributo e **almeno uno** dei valori **ritornati dalla query annidata**
* #### Operatore **ALL**
  * Come Any ma **tutti i valori della query** annidata devono soddisfare la condizione


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

### Query Annidate

#### Semplici
* Non c’è passaggio di binding  
* Composte da **una query esterna e una interna**  
* La Query interna è la **prima ad essere calcolata**  
* La Query interna viene **calcolata solo una volta**
#### Complesse
* C’è un **passaggio di binding**  
* La query interna viene chiamata **per ogni riga della query esterna**  
  * SELECT attr  
    FROM table AS t1  
    WHERE attr \>/\</= specialOperator(SELECT attr2  
                 FROM table2  
                  **WHERE t1.attr \=/\>/\</\!=table2.attr**)  
* Confronta **ciascuna riga della tabella esterna con il risultato della quey interna**
#### Viste
Rappresentano “**tabelle virtuali**” ottenute da **dati contenuti in altre tabelle** del database  
Ogni vista ha associato un **nome** e una **lista di attributi**, dati dal risultato di una select.
* create view NomeView \[ListaAttributi\]
as SELECTSQL  
\[with \[local | cascade\] check option\]
* **I dati non sono fisicamente memorizzati a parte**  
  * **Dipendono** da altre tabelle  
  * **Non hanno istanze proprie**  
* Servono a:  
  * Implementare meccanismi di indipendenza tra livello logico e il livello esterno  
  * **Semplificare interrogazioni** complesse  
  * Garantire Retro-compatibilità con precedenti versioni di schema in caso di restrutturazione

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
