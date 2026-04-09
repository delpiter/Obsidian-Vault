## PHP e MYSQL
---
>[!question] Perché MSQL?

- È ***open source***.
- **Cross Platform**.
- Usa lo standard [[../../DataBase/Interrogazioni/SQL|SQL]].

>[!caution] PHP Hypertext Preprocessor
>`{PHP icon} PHP` 5 e successivi possono lavorare con `{sql icon} mySQL` usando:
>- `MySqliAPI`
>- `PDO`: `PHP` Data to Object.

`PDO` si può usare con ***12 diversi database***, mentre `MySqliAPI` si può usare solo con `mySQL` ma ha **prestazione leggermente migliori**.

### MySqli
>[!info] `API`
>`MySqli` mette a disposizione `API` sia [[../../Ingegneria del Software/Paradigma ad Oggetti|object-oriented]] che **procedurali**.

```php
$servername = "localhost";
$username = "username";
$password = "password";
$sql = "CREATE DATABASE dbname;";
//object-oriented
$conn = new mysqli($servername, $username, $password);
$conn->query($sql) === TRUE
//procedural
$conn = mysqli_connect($servername, $username, $password);
mysqli_query($conn, $sql)
```

>[!failure] Apertura e Chiusura di una Connesione

```php
<?php
$servername = "localhost";
$username = "username";
$password = "password";
$dbname = "dbname";
// Start the connection
$conn = new mysqli($servername, $username, $password, $dbname);
//Close the connection
$conn->close();
?> 
```

#### Esecuzione di Query
>[!todo] Queries in PHP
>È possibile eseguire una *query* di `SQL` di qualsiasi tipo **usando il metodo** `{php icon} query()`.

Il risultato sarà diverso in base al tipo di query eseguito.
- La query [[../../DataBase/Interrogazioni/DDL|DDL]] restituendo semplicemente `true` o `false`.
- Le query [[../../DataBase/Interrogazioni/DML|DML]] restituiranno i dati.

##### Prepared Statement
>[!definizione]
>I ***prepared statement*** permettono di creare query con *placeholder*, che vengono valorizzati successivamente.

```php
$stmt = $conn->prepare("INSERT INTO Guests (firstname, lastname, email) VALUES (?, ?, ?)");
$stmt->bind_param("sss", $firstname, $lastname, $email);
$stmt->execute();
```

>[!help] Sicurezza
>Per motivi di sicurezza, è preferibile usare i ***prepared statement*** al posto del metodo `{php icon} query()`.

Quando si esegue il binding (`{php} bind_param("x", $variable)`) è necessario specificare il ***tipo di parametro***.
- `i`: Interi.
- `d`: Double.
- `s`: String.
- `b`: BLOB.
