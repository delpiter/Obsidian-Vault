![[Elementi e Categorie#^392e61]]

## Form
---
>[!info] `{html icon} <form>`
>Una ***form*** è una parte della pagina web che *contiene controlli di input*, come **campi di testo**, **bottoni** e **checkbox**.

In `{html icon} HTML5` la *form* può avere anche campi per l'***output***.

>La *form*:
- Può essere processata a lato ***client*** (`{js icon} javascript`).
- Può essere processata a lato ***server***.
- Entrambe le cose.

### Attributi 
> Gli attributi di `{html icon} <form>` sono:

>[!failure] `action`
>Specifica l'[[URL]] dell'applicazione ***server-side*** che riceverà i dati.

>[!caution] `method`
>Specifica il metodo [[HTTP]] che deve essere usato per i dati.
>- `GET` o `POST`.

```html
<form action="http://www.google.com/search" method="get">
</form>
```

#### Attributi Comuni
> Tra i tanti elementi dei form, molti attributi sono ***comuni a tutti***.

`name`
- Specifica il *nome del controllo*, usato nella sottomissione del form.

`required`
- È un attributo *booleano* dei controlli che indica che è ***obbligatorio*** inserire un valore per quel campo.

`autofocus`
- Mette il ***focus*** su questo campo.

`autocomplete`
- Attributo *booleano* di input che consente di attivare l'***autocompletamento***.

### Elementi del Form
#### Label
>[!info] `{html icon} <label>`
>Ogni *controllo* deve avere una ***label*** che descriva il controllo all'utente.

La presenza delle *label* è fondamentale per l'accessibilità, se non si vuole che sia visibile, va resa invisibile ma senza rimuoverla.

> La ***label*** può essere associata al controllo:

- Annidando il controllo nella label
- Mettendo un `id` nel controllo e relazionandolo alla ***label*** nell'attributo `for`.

```html
<form>
	<p>
		<label>Customer name: 
			<input....../>
		</label>
	</p>
	<p>
		<label for="CN">Customer name: </label>
		<input .... id="CN" />
	</p>
</form>
```

#### Fieldset
>[!info] `{html icon} <fieldset>`
>Elemento che raggruppa più controlli che ***hanno semantica comune***.

```html
<form>
	<fieldset> 
		<legend>dati personali:</legend>  
		<label>Nome: 
			<input type="text" name="nome"/>
		</label><br/>
		<label>Email:
			<input type="email" name="mail"/>
		</label><br/>
		<label>Data di nascita: 
			<input type="date" name="date"/>
		</label >
	</fieldset><br/>
	<input type="submit" value="Invia"/>
 </form>
```

#### Input
>[!info] `{html icon} <input>`
>Elemento che consente di inserire nella pagina molti ***tipi diversi di controllo***.
>- Il *tipo* è specificato mediante l'attributo `type`, che può assumere i valori:
>	- `hidden`, `text`, `search`, `tel`, `url`, `email`, `password`, `date`, `time`, `number`, `range`, `color`, `checkbox`, `radio`, `file`, `submit`, `image`, `reset` e `button`.

[HTML input type Attribute](https://www.w3schools.com/tags/att_input_type.asp)

> `reset`, `submit` e `button`.

Sono bottoni che servono per, rispettivamente:
- **Ripristinare** i valori di default.
- **Sottomettere** il form.
- Bottone associabile ad uno **script** `{js icon} javasctipt`.

In tutti e tre gli elementi, attraverso l'attributo `value` viene modificato il *testo sul bottone*.

> `image`

- Ha la stessa funzione di un bottone (`submit` di default), con un immagine per resa grafica.

> `hidden`

- Input per creare una ***associazione variabile-valore*** invisibile all'utente.
- Non viene visualizzato.

> `password`

- Input per creare una ***associazione variabile-valore*** invisibile all'utente.
- Quando si riempe il controllo, la visualizzazione della *password* viene oscurata.

> `radio`

- Input che realizzano un ***radio button***.
- Le diverse opzioni possibili sono definite inserendo ***più radio*** con lo **stesso** `name`.

> `checkbox`

- Input che realizzano una ***checkbox***.
- Le diverse opzioni sono definite inserendo più *checkbox* con `name` **diversi**.

> `text`

- Input usati come controlli per l'***input di testo generico***.

> `search`

- Consente di inserire testi che diventano ***chiavi di ricerca***.

> `color`

- Consente di ***scegliere un colore***, attraverso un *color picker*.

> Data e Ora

- `time`: ***Orario***.
- `week`: ***Settimana dell'anno***.
- `date`: ***Data***.
- `datetime`: ***Data e Orario***.
- `datetime-local`: Data e Orario ***Locali***.

> `tel`, `url`, `email`

- Consente di inserire dati personali, di tipo specifico.
	- Presenta un controllo basilare (tipo *regex*) dei dati inseriti
		- es. `email`: deve avere `@` e `.com/it/edu/...`

> `number` e `range`

Tipi di controllo per i numeri:
- `number`: consente di ***inserire un numero***.
- `range`: consente di ***scegliere un range***.
- Per entrambi si possono definire:
	- `min` e `max` che specificano il valore *minimo* e *massimo* ammissibile.

> `file`

- Consente di ***selezionare un file***.
- Possono essere caricati più *files*.

```html title:"big ass example"
<form>
	<fieldset> <legend>Fieldset:</legend>  
		<label>text: 
			<input type="text" name="name"/>
		</label><br/>
		<label>email:
			<input type="email" name="email"/>
		</label><br/>
		<label>tel:
			<input type="tel" name="usrtel"/>
		</label><br/>
		<label>url: 
			<input type="url" name="homepage"/>
		</label><br/>
		<label>password:
			<input type="password" name="pwd" maxlength="8" />
		</label><br/>
	</fieldset><br/>
	
	
	<fieldset><legend>Radio Buttons</legend>
		<label> 
			<input type="radio" name="gender" value="r1"/>radio 1
		</label> <br/>
		<label>
			<input type="radio" name="gender" value="r2"/>radio 2
		</label> <br/>
		<label>
			<input type="radio" name="gender" value="r3"/> radio 3
		</label> <br/>
	</fieldset><br/>
	
	<fieldset><legend>Checkboxes</legend>
		<label>
			<input type="checkbox" name="c1" value="Value1"/>checkbox 1
		</label><br/>
		<label>
			<input type="checkbox" name="c2" value="Value2"/>checkbox 2
		</label><br/>
		<label>
			<input type="checkbox" name="c3" value="Value3"/>checkbox 3
		</label><br/>
	</fieldset><br/>
	
	<label>color: 
		<input type="color" name="colors"/>
	<label><br/>
	
	<fieldset><legend>Time</legend>
		<label> time:
			<input type="time" name="usr_time"/>
		</label><br/>
		<label> week:
			<input type="week" name="week_year"/>
		</label><br/>
		<label> date: 
			<input type="date" name="day"/>
		</label> <br/>
		<label> date and time: 
			<input type="datetime" name="dt"/> 
		</label> <br/>
		<label>local date and time: 
			<input type="datetime-local" name="ldt"/>
		</label> <br/>
	</fieldset><br/>
	
	<label>range (0-10) 
		<input type="range" name="points" min="0" max="10"/>
	</label><br/>
	<label>number (1-5): 
		<input type="number" name="quantity" min="1" max="5"/>
	</label><br/>
	
	<input type="button" value="Button" onclick="…"/> 
	<input type="reset" value="Reset"/>
	<input type="submit" value="Submit"/>
</form>
```



<form><fieldset><legend>Fieldset:</legend></br><label>text:<input type="text" name="name" /></label><br /><label>email:<input type="email" name="email" /></label><br /><label>tel:<input type="tel" name="usrtel" /></label><br /><label>url:<input type="url" name="homepage" /></label><br /><label>password:<input type="password" name="pwd" maxlength="8" /></label><br /></fieldset><fieldset><legend>Radio Buttons</legend></br><label><input type="radio" name="gender" value="r1" />radio 1</label> <br /><label><input type="radio" name="gender" value="r2" />radio 2</label> <br /><label><input type="radio" name="gender" value="r3" /> radio 3</label> <br /></fieldset><br /><fieldset><legend>Checkboxes</legend></br><label><input type="checkbox" name="c1" value="Value1" />checkbox 1</label><br /><label><input type="checkbox" name="c2" value="Value2" />checkbox 2</label><br /><label><input type="checkbox" name="c3" value="Value3" />checkbox 3</label><br /></fieldset><br /><label>color:<input type="color" name="colors" /><label><br /><fieldset><legend>Time</legend></br><label> time:<input type="time" name="usr_time" /></label><br /><label> week:<input type="week" name="week_year" /></label><br /><label> date:<input type="date" name="day" /></label> <br /><label> date and time:<input type="datetime" name="dt" /></label> <br /><label>local date and time:<input type="datetime-local" name="ldt" /></label> <br /></fieldset><br /><label>range (0-10)<input type="range" name="points" min="0" max="10" /></label><br /><label>number (1-5):<input type="number" name="quantity" min="1" max="5" /></label><br /><input type="button" value="Button" onclick="" /><input type="reset" value="Reset" /><input type="submit" value="Submit" /></form>

#### Textarea
>[!info] `{html icon} <textarea>`
>Elemento che definisce un controllo di input per ***testi multilinea***.

Gli attributi `cols` e `rows` specificano la dimensione dell'*area*.

```html
<form>
	<label>
		testo libero 
		<br/>
		<textarearows="4" cols="50">
			il testo inserito tra inizio e fine 
			elemento è il valore di default della textarea
		</textarea>
	</label>
</form>
```

#### Select e Option
>[!info] `{html icon} <select>`
>Elemento usato per realizzare ***menù a tendina***.
>Le diverse opzioni sono introdotte attraverso l'elemento `{html icon} <option>`.

```html
<form> 
	<label> scegli un insegnamento<br/>
		<select name="insegnamento">
			<option value="SO">Sistemi Operativi</option>
			<option value="TW">Tecnologie Web</option>
			<option value="SM">Sistemi Multimediali</option>
		</select>
	</label>
</form>
```

> Attributi `{html icon} <select>`

`multiple`
- Attributo booleano per effettuare selezioni multiple
`size`
- Definisce le opzioni da mostrare all'utente.

> Attributi `{html icon} <option>`

`selected`
- Attributo booleano, se è `true` indica che quella `{html icon} <option>` è il valore di default.
- Se si vuole un `default` nullo, si aggiunge una **option** vuota.

`value`
- Indica il valore quando diverso dal testo della **option** (es. un *abbreviazione*).

##### Option Group
> Elemento usato per raggruppare le `{html icon} <option>` in una **select**

```html
<form> 
	<label> scegli un insegnamento<br/>
		<select name="insegnamento">
			<optgroup label="2014/15"> 
				<option value="SO">Sistemi Operativi</option>
				<option value="SM">Sistemi Multimediali</option>
			</optgroup>
			<optgroup label="2015/16">
				<option value="TW">Tecnologie Web</option>
				<option value="SM">Sistemi Multimediali</option>
			</optgroup>
		</select>
	</label>
</form>
```

#### Datalist
>[!info] `{html icon} <datalist>`
> Insieme all'elemento **option** può essere usato anche per predisporre dei suggerimenti per i valori di un campo testuale.

```html
<form>
	<label> scegli un insegnamento
		<input list="corsi" name="insegnamento"/>
	</label>
	<datalist id="corsi">
		<option value="SO">Sistemi Operativi</option>
		<option value="TW">Tecnologie Web</option>
		<option value="SM">Sistemi Multimediali</option>
	</datalist><br/>
</form>
```

#### Output
>[!info] `{html icon} <output>`
>Elemento che rappresenta il ***risultato di un calcolo o azione*** dell'utente.

```html
<form oninput="x.value=parseInt(a.value)">
	<label for="a">slider: <br/>
		0<input type="range" id="a" value="50"/>100
	</label> <br/>
	il valore dello slider è: <output name="x" for="a"></output>
</form>
```
