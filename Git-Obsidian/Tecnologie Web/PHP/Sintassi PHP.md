## Variabili
---
>[!info] Variabili
>Tutte le ***variabili*** iniziano con il carattere `$`:
>- `{php} $variable`.

`{php icon} PHP` è un linguaggio ***debolmente tipizzato***.
- Possiamo associare alla stessa variabile *più tipi di dato*.

```php
$variable = 3;
$variable = true;
$variable = "Hello!";
/* Correct */
```

### Tipi di Dato
> I [[Tipi di Dati|tipi di dato]] del linguaggio `PHP` sono:

>[!bug] Boolean

>[!todo] Integer, Float

>[!tl;dr] String

È possibile definire una stringa in 4 modi:
- **Single Quote**: `{php} $string='string'`
	- Non vengono espanse e ammette pochi ***caratteri di escape***.
- **Double Quote**: `{php} $string="string"`
	- Vengono espanse e sono ammesse le *più comuni* sequenze di escape.
- **Heredoc**: `{php} $string=<<< ID string stuff;`
	- Si comporta come le double quote ma senza usarle.
- **Newdoc**: `{php} $string=<<< 'id' stuff id;`
	- Si comporta come le single quote ma senza usarle.

>[!summary] Array

Definiti tramite la funzione `{php icon} array()`
- `{php} $example = array(1,2,3);`
Esistono 3 tipi di array:
> ***Indexed***
- Array classici con indice numerico
```php
$strings=array("one", "two", "three");
/* Equivalent to */
$strings[0] = "one";
$strings[1] = "two";
$strings[2] = "three";
```

> ***Associative***
- Array che hanno *stringhe come indici*

```php
$strings=array("one"=>1, "two"=>2, "three"=>3);
/* Equivalent to */
$strings["one"] = 1;
$strings["two"] = 2;
$strings["three"] = 3;
```

> ***Multidimensional***
- Array che contengono *uno o più array*.
```php
$multidimarray = array(1, array(2,3,4,5), "test", array("hello",true));
```

>[!tip] Object

`PHP` consente di definire classi e istanziare oggetti.
> Supporta i principali meccanismi del [[Paradigma ad Oggetti]].

```php
class Person {
	private $name;
	private $surname;
	public $birthDate;
	
	public function __construct($name, $surname, $birthDate) {
		$this->name = $name;
		$this->surname = $surname;
		$this->birthDate = $birthDate;
	}
	
	public function toString(){
		echo "I am ".$this->name." ".$this->surname;
	}
}

$mario = new Person("Mario", "Super", "12/09/1985");
$mario->toString();
// I am Mario Super

echo $mario->name;
// fatal error
```

È presente il valore `NULL`.

>[!cite] Resource

Una risorsa non è un vero e proprio ***tipo***.
- È una variabile che contiene il ***riferimento ad una risorsa esterna***.
- Create e usate da funzioni speciali.
	- Es. [[Introduzione ai Files|file aperti]] o connessioni ad un [[Git-Obsidian/DataBase/Introduzione#Database|database]].

### Variabili Superglobali
>[!info]
>Le ***variabili superglobali*** sono variabili accessibili *ovunque*.

>[!example] Esempi
- `{php} $GLOBALS`: Memorizza tutte le variabili globali.
- `{php} $_SERVER`: Gestisce informazioni sul server.
- `{php} $_GET`: Usato per collezionare dati inviati con metodo `GET`.
- `{php} $_COOKIE`: Gestisce i cookies.
- ...

## Output
---
> In `PHP` ci sono due modi per ottenere un output

>[!abstract] `{php icon} print`
>Può stampare una sola riga e restituisce sempre `1`.

>[!check] `{php icon} echo`
>Può stampare una o più *stringhe* e **non** ha valore di ritorno.

Solitamente usato `echo` in quanto più veloce.

#### Vardump
>[!failure] `{php} var_dump()`
>`{php} var_dump()` è una funzione per stampare **tipo** e **contenuto** di un'espressione, *utile in fase di debug*.

```php
<?php
	$a = array(1, array("a", "b", "c"));
	var_dump($a);
?>
/* prints */
/*
array(2) {
	[0]=>
	int(1)
	[1]=>
	array(3) {
		[0]=>
		string(1) "a"
		[1]=>
		string(1) "b"
		[2]=>
		string(1) "c"
	}
}
 */
```

## Gestione dello Stato
---
>[!done] Stato
>`PHP` fornisce due strumenti per la gestione dello stato
>- [[HTTP#Cookie|Cookie]].
>- **Session**.

Un cookie consente di salvare un'informazione nel *browser dell'utente*.
- È possibile creare un cookie utilizzando la funzione `{php icon} setcookie()`, specificando nome (**obbligatorio**), valore, validità e percorso.

```php title:example
$cookie_name = "n_access";
if(!isset($_COOKIE[$cookie_name])) {
	echo "Cookie '" . $cookie_name . "' not Set! 
	setting now.";
$cookie_val = 1;
setcookie($cookie_name, $cookie_value, time() + 
(60 * 60 * 24 * 30), "/");
} else {
	echo "Cookie '" . $cookie_name . "' set!<br>";
	$n_visit = $_COOKIE[$cookie_name]+1;
	setcookie($cookie_name, $n_visit, time() + 
	(60 * 60 * 24 * 30), "/");
	echo "The site was visited: ".$n_visit." times";
}
```

>[!fail] Cancellazione
> Per ***cancellare un cookie*** è sufficiente impostare il tempo di validità "*passato*".
> `{php icon} setcookie($cookie_name, "", time() - 100, "/")`

### Sessioni
>[!abstract] Session
>Con una ***session*** è possibile salvare un'informazione *direttamente sul server*.
>Al browser viene assegnato un **identificatore di sessione** che viene registrato in un *cookie* (`PHPSESSID`).

Alle successive interazioni `PHP` controllerà automaticamente se un `id` è stato inviato con la richiesta.
- In caso positivo, rende accessibili le informazioni salvate aggiungendole alla variabile `{php icon} $_SESSION`

Tutto avviene in maniera trasparente dal lato client.
- Una sessione termina quando il browser viene chiuso.
>[!question] Come fa il server a sapere se il browser viene chiuso?

> **Non lo sa!**
- Il server ha un parametro di configurazione `session.gc_maxlifetime` che indica il **tempo di vita di una sessione**.
- Allo scadere del tempo, la sessione *viene considerata scaduta*.


>[!question] Come salvare variabili nella variabile di sessione?

- Usando direttamente la *variabile superglobale*.
- Usando la funzione `{php} session_register()`

```php
$_SESSION['name'] = "william";
/* or */
$name = "william";
session_register("name");
```

>[!fail] E per rimuoverle?

- La funzione `{php} unset()` per rimuovere **una singola variabile**. `{php} unset($_SESSION["name"]);`
- La funzione `{php} session_unset()` per rimuovere **tutte le variabili**.
- La funzione `{php} session_destroy()` per rimuovere **tutte le informazioni della sessione** (non solo le variabili).