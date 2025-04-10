>[!info]
>In [[SQL]] è possibile esprimere condizioni che si basano sul risultato di altre [[DML|interrogazioni]]:
>- **Subquery**.
>- **Query Innestate**.
>- **Query Nidificate**.

```sql
SELECT attr
FROM tableName
WHERE attr IN (SELECT attr2
			   FROM table2
			   WHERE condition)
```

> Una **subquery** può fare uso a sua volta di altre **subquery**.
- Il risultato si può ottenere risolvendo a partire dal ***blocco più interno***.

>[!help] Subquery Scalari
>Gli operatori di confronto $=,>,<,\dots$ si possono usare **solo** se la *subquery* restituisce non più di una tupla.
>Tali query si dicono ***scalari***.
### Operatori con Query Annidate
![[DML#IN]]

![[DML#EXIST]]

![[DML#ANY]]

![[DML#ALL]]

## Tipi di Query Annidate
---
### Query Annidate Semplici
>[!info] Semplice
>In una *query annidata semplice* **non** c'è ***passaggio di binding***.
>Sono composte da una query *esterna* e una *interna*.
>- La query interna ha **sempre lo stesso risultato**.

La Query interna è la **prima ad essere calcolata**.
- Viene calcolata ***una sola volta***.
Successivamente viene valutata la *query esterna*.

```sql title:Example
SELECT CodEmpl
FROM Employees
WHERE HQ IN (SELECT HQ
			 FROM HeadQuarters
			 WHERE City='Milan')
```
#### Query Annidate Complesse
>[!abstract] Complesse
>In una *query annidata complessa* c'è ***passaggio di binding***.
>- La query interna viene *chiamata* per ***ogni riga*** della *query esterna*.

```sql title:Example
SELECT HQ
FROM Employees AS E
WHERE EXISTS (SELECT *
			  FROM Employees
			  WHERE Role='Programmer' AND HQ=E.HQ)
```
  
- Confronta **ciascuna riga della tabella esterna** con il *risultato* della query interna.