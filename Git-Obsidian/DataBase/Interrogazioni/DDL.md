## Data Definition Language
---
>[!tldr] Idea
>Il **DDL** di [[SQL]] permette di **definire** schemi di relazioni (o *tabelle*), **modificarli** ed **eliminarli**.
>Permette anche di specificare [[Vincoli di Integrità|vincoli]] sia a livello di *tupla* che a livello di *tabella*.

Permette di definire nuovi **domini** oltre a quelli predefiniti
- Domini di cui potrà fare uso il [[DML]].

### CREATE
>[!help] Costrutto
>Mediante l'istruzione `CREATE` si ***definisce*** lo schema di una tabella e se ne crea un'*istanza vuota*.

Per *ogni attributo* va specificato:
- Il **dominio**.
- Un eventuale **valore di default**.
- Eventuali **vincoli**.

```sql
CREATE tableName (
	attribute1 char(4) PRIMARY KEY,
	attribute2 varchar(10) NOT NULL UNIQUE,
	attrivute3 int CHECK(<condition>) 
);
```

>[!info] Primary Key
>Per assegnare la [[Vincoli di Integrità#Chiavi|chiave primaria]] si indica di *fianco al dominio* dell'attributo voluto il parametro `PRIMARY KEY`.
>Se la *tabella* contiene una chiave composta da diversi attributi, si indicano tutti in una volta alla fine della *query*:
>- `PRIMARY KEY(attribute1, attribute2,...)`

### DROP
>[!help] Costrutto
>Mediante l'istruzione `DROP` è possibile ***eliminare*** lo schema di una tabella.
>>[!missing] Verrà eliminata la corrispondente istanza

Dopo la *keyword* `DROP` possono esserci diversi parametri:
- `schema`
- `domain`
- `table`
- `view`

```sql
DROP TABLE tableName;
```

### ALTER
>[!help] Costrutto
>Mediante l'istruzione `ALTER` è possibile ***modificare*** lo schema di una tabella.
>In particolare:
>- *Aggiungendo*/*rimuovendo* **attributi**.
>- *Aggiungendo*/*rimuovendo* **vincoli**.

```sql
ALTER TABLE tableName(
	ADD COLUMN attributeName char(1) CHECK (condition),
	DROP COLUMN attrivuteName,
	ADD CONSTRAINT constName CHECK (condition),
	DROP CONSTRAINT constName,
	DROP UNIQUE(attribute1, attribute2,...)
);
```

### Domini
>Utilizzabili 2 tipi di domini
#### Domini Elementari
>[!info]
>Domini di base, già presenti all'***interno del linguaggio***.
##### Caratteri
`{sql icon} char`
 - Solo *un carattere*.
 
`{sql icon} char(x)`
  - Stringa con un *numero* $x$ di *caratteri fisso*.
  
`{sql icon} varchar(x)`  
  - Stringa con al *massimo* un numero $x$ di caratteri.
##### Tipi Numerici Esatti
> Rappresentano ***numeri esatti*** *interi* o *decimali di lunghezza prefissata*.

`{sql icon} numeric(precision,scale)`
- Rappresentazione di *numeri esatti*.
	- *Precision*: Numero totale di cifre.
	- *Scale*: Numero di cifre dopo la virgola

`{sql icon} decimal(precision, scale)`
- Equivalente a *numeric*.

`{sql icon} integer`
- Rappresentazione di *numeri interi*.
- `{sql icon} smallint` e `{sql icon} bigint` sono alternative con range *minore*/*maggiore*.

`{sql icon} auto_increment`
- Serve per generare un *valore numerico cresente*.

`{sql icon} identity(a,b)`
- Aumenta, partendo da $a$, di $b$ valori.
##### Tipi Numerici Approssimati
> Serve per rappresentare valori numerici approssimati come [[Numeri Floating-Point|floating point]].

Valori possibili:
- `{sql icon} float(precision)`
- `{sql icon} double`
- `{sql icon} double precision`

##### Istanti Temporali
> Usati per gestire *date*, *orari* e *timestamp*.

`{sql icon} date`
- Per rappresentare **date** nel formato `yyyy-mm-dd`

`{sql icon} time(precision)`
- Per memorizzare l'**orario** nel formato `hh:mm:ss`
- Il parametro *precision*, aumenta la precisione dei **secondi**.

`{sql icon} timestamp(precision)`
- Usato per rappresentare sia **data** che **ora**.
	- Formato principale: `yyyy-mm-dd hh:mm:ss`.
##### Blob e cBlob
> Usato per rappresentare oggetti di grandi dimensioni.

`{sql icon} blob`
- Oggetti di **grandi dimensioni** sottoforma di `bit`.  
- **Non** è possibile interrogare in base al *blob*.

`{sql icon} cblob`
- Come il **blob** ma con stringhe al posto di `bit`.

#### Dominio “Custom”
> Utilizzabili in *definizioni di relazioni* anche con **vincoli** e **valori di default**.

```sql
CREATE DOMAIN domainName as int
DEFAULT NULL
CHECK(condition)
```
### Vincoli
> I vincoli sono definibili per ***ciascun dominio***.

#### Intra-Relazionali
```sql
attribute domain CHECK(condition)
```

Mediante la clausola `check` è possibile esprimere ***vincoli di tupla arbitrari***.

```sql
attribute domain NOT NULL
```

Sufficiente per **vietare** la presenza di valori [[Informazione Incompleta#Null|nulli]].

```sql
attribute domain UNIQUE
```

Esprime la definizione di [[Vincoli di Integrità#Chiavi|chiave non primaria]].

```sql
attribute domain PRIMARY KEY
```

Esprime il [[Vincoli di Integrità#Chiavi|vincolo di chiave primaria]].

#### Inter-Relazionali
>Vincoli espressi tra *diverse tabelle*.

>[!help] Vincolo References
>Consente di definire [[Vincoli di Integrità#Vincolo di Integrità Referenziale|vincoli di integrità referenziale]] tra i valori in cui è definito (*Tabella interna*) e i valori di un **attributo** di una *seconda tabella*.  

```sql
FOREIGN KEY attribute REFERENCES table
```

>[!abstract] Politiche di Reazione
> In caso di violazione di vincolo di integrità referenziale.
> 4 ***azioni possibili***:
> - **Cascade**
> 	- *Elimina*/*Aggiorna* le righe della tabella interna.
> - **Set Null**
> 	- Imposta i valori a **null**.
> - **Set Default**
> 	- Imposta i valori di **default**.
> - **No action**
> 	- **Non consente** l'azione.

Ciascuna delle azioni possibili si possono impostare:
- `{sql icon} ON DELETE`
- `{sql icon} ON UPDATE`
