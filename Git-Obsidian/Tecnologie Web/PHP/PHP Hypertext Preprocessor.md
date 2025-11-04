## PHP
---
>[!info]
>`{php icon} PHP` è un ***linguaggio di scripting***, [[Definizioni_Architettura#Interpretazione|interpretato]], originariamente concepito per la programmazione di pagine web dinamiche *lato server*.

L'interprete `PHP` è un software *open source*, sotto la `PHP License`.
### Architettura e Sintassi
>[!todo] Interprete
>L'interprete `PHP` preprocessa tutti i file con estensione `.php` che sono file contenenti `{html icon} HTML` all'interno dei quali è presente del codice `PHP`.

Il codice `PHP` è contenuto all'interno dei delimitatori specifici:
```php
<!DOCTYPE html>
<html lang="en">
	<body>
		<?php echo "Hello, World!"; ?>
	</body>

</html>
```

Solo il codice contenuto tra i delimitatori `{php icon} <?php ?>` viene realmente *preprocessato*.

La *sintassi* di `PHP` è `C`-like con differenze legate allo scopo specifico del `PHP`.

#### Uso di più File PHP
>[!question] Come posso risolvere la ripetizione di codice `{php icon} PHP`?

È possibile realizzare un ***file separato*** con estensione `.php` che contiene il codice più articolato e di uso più *frequente* (es. gestione del [[Git-Obsidian/DataBase/Introduzione#Database|Database]]).
- Sarà poi necessario includere il codice nel file `PHP` principale usando `require` e `include`.

>[!example] Esempio

```php title:"dbtw-mysql.php"
<?php
	$host = "localhost";
	$user = "silvia";
	$pass = "techweb";
	$database = "TW";
	// connessione DBMS
	$myconn = mysql_connect($host, $user, $pass) or 
	die('Errore...');
	//connessione DB database
	mysql_select_db($database, $myconn) or 
	die('Errore...');
?>
```
All'interno di tutte le pagine che operano sul database, possiamo includere il file usando ***uno dei due costrutti a dispoizione***.
- `{php icon} <?php include "dbtw-mysql.php";?>`
- `{php icon} <?php require "dbtw-mysql.php";?>`

I due costrutti sono ***equivalenti*** eccetto per come trattano gli errori:
- `{php} include` produce un *Warning*, mentre `{php} require` restituisce un ***Fatal Error***.

Le primitive possono essere usate anche per includere:
- Librerie `{php icon} PHP` (con attenzione allo [[Visibilità e Tempo di Vita|scope]] delle variabili).
- File `{html icon} HTML`.

>[!warning] Attenzione
>**Non** è possibile includere un file `.php` in un file `.html`, non verrebbe interpretato.
