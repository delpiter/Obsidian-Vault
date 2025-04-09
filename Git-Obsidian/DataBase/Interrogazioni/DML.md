## DML
Le operazioni di interrogazione vengono implementate dal costrutto **SELECT**
### **SELECT**
* Specifica quali **colonne** delle **righe selezionate** devono comparire nel **risultato finale**  
* Possibile **ridenominare** le colonne del risultato di una query con il **costrutto AS**  
* Possibile usare **espressioni aritmetiche** **semplici** sui valori degli attributi di una select
### **FROM**
* Specifica la **lista di tabelle** a cui si deve accedere  
* È possibile cambiare nome con la **clausola AS**  
* In caso di **più tabelle con attributi** con nome **uguali**  
  * Necessario **specificare la tabella** per risolvere **l’ambiguità**  
    * TableName.AttrName
* #### JOIN
  * Utilizzato nella clausola **FROM**  
  * Al posto di fare il **prodotto cartesiano** e poi selezionare le righe nella clausola **WHERE**  
    * **FROM** table1 **JOIN** table2 **ON** table1.attr \= table2.attr  
  * Anche possibili  
    * **LEFT JOIN**  
    * **RIGHT JOIN**  
    * **FULL JOIN**
### **WHERE**
* **Quali righe** delle tabelle devono **comparire nel risultato finale** attraverso una **espressione booleana** o una combinazione di espressioni  
* In caso di valori **Null** la riga viene **esclusa dal risultato**
* #### Confronti fra String
  * Operatore **LIKE** e wildcards  
    * **‘\_’** Carattere arbitrario  
    * **‘%’** Sequenza di caratteri arbitrari  
    * ES. WHERE nome LIKE ‘M\_R%O’  
      * Sting che inizia con M, ha R come terza lettera e finisce con O
* #### Operatore **BETWEEN**
  * Consente di verificare l’appartenenza di un valore ad un certo range di valori  
  * WHERE attrName BETWEEN(10,20) \=\> valori tra 10 e 20 inclusi
* #### Operatori  **IS NULL** & **IS NOT NULL**
  * Controlla se il valore di un attributo è nullo o no
* #### Operatori **IN** & **NOT IN**
  * Controlla se il valore di un attributo è contenuto in una lista di valori
* #### Operatore **EXIST** & **NOT EXIST**
  * Condizione di **esistenza**  
  * **Ritorna un valore booleano** in base a **quante righe** vengono riportate nella query interna  
    * 0 righe \=\> false  
    * \> 0 righe \=\> true
* #### Operatore **ANY**
  * La riga soddisfa la condizione se è vero il confronto fra il valore di un attributo e **almeno uno** dei valori **ritornati dalla query annidata**
* #### Operatore **ALL**
  * Come Any ma **tutti i valori della query** annidata devono soddisfare la condizione
### **ORDER BY**
* Dopo la clausola **WHERE**  
* **Ordina le righe del risultato** di una interrogazione in base al valore di un attributo specificato  
  * ORDER BY attrName \[**asc/desc**\], attrName2 \[asc/desc\]
### **OPERATORI AGGREGATI**
* Si applicano a **gruppi di tuple** e restituiscono sempre una sola riga  
* Solitamente inseriti nella select e **valutati dopo** la clausola **WHERE**  
* Tipi:  
  * **COUNT**(\*)  
    * Count delle righe  
  * **SUM**(Attribute)  
    * Somma dei valori di una colonna  
  * **MAX**(Attribute)  
    * Valore massimo di una colonna  
  * **MIN**(Attribute)  
    * Valore minimo di una colonna  
  * **AVG**(Attribute)  
    * Valore medio di una colonna
### **GROUP BY**
* Consente di **dividere in gruppi**, ognuno caratterizzato da un valore comune dell’attributo uguale  
* Produce **una sola linea nel risultato finale PER ogni gruppo**  
* SELECT attrList1 FROM table WHERE condition GROUP  BY attrList2  
* **\!\!** attrList1 **DEVE ESSERE** un sottoinsieme di attrList2 **\!\!**
### **HAVING**
* Funge da **filtro** sui vari **gruppi**  
* Usata dopo la clausola **GROUP BY**
## Ordine delle operazioni
* FROM  
* WHERE  
  * Valutazione operatori aggregati  
* GROUP BY  
* HAVING  
* ORDER BY  
* SELECT
## Operatori insiemistici
Gli **attributi** della SELECT **devono avere** **tipi** di dato **compatibili** e possibilmente gli stessi nomi
### **UNION**
* Unione di tutte le righe senza ripetizioni
### **INTERSECT**
* Selezionate solamente le righe comuni
### **EXCEPT**
* Selezionate tutte le righe della tabella A che non sono nella tabella B
## Manipolazione dell’istanza
* **INSERT INTO** tableName \[attrList\] values \[valueList\]  
* **DELETE FROM** tableName \[WHERE Condition\]  
* **UPDATE** tableName  
  * SET attribute \= value/select/NULL/default  
  * \[WHERE condizione\]
# **Query Annidate**
## Semplici
* Non c’è passaggio di binding  
* Composte da **una query esterna e una interna**  
* La Query interna è la **prima ad essere calcolata**  
* La Query interna viene **calcolata solo una volta**
## Complesse
* C’è un **passaggio di binding**  
* La query interna viene chiamata **per ogni riga della query esterna**  
  * SELECT attr  
    FROM table AS t1  
    WHERE attr \>/\</= specialOperator(SELECT attr2  
                 FROM table2  
                  **WHERE t1.attr \=/\>/\</\!=table2.attr**)  
* Confronta **ciascuna riga della tabella esterna con il risultato della quey interna**
# **Viste**
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