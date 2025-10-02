![[Elementi e Categorie#^82988f]]

## Table
---
>[!info] `{html icon} <table>`
>Elemento usato per realizzare ***tabelle***.
>- Sono organizzate per righe, realizzate attraverso l'elemento `{html icon} <tr>` (*table row*).
>- Ciascuna *riga* è poi divisa in **celle**.

Le ***celle*** possono essere:
- Celle **normali**: `{html icon} <td>` (*table data*).
- Celle di **intestazione**: `{html icon} <th>` (*table header*).

Con l'elemento `{html icon} <caption>` è possibile aggiungere un ***titolo***.


```html title:"horizontal table"
<table>
	<tr>
		<th>Month</th>
		<td>January</td>
		<td>February</td>
	</tr>
	<tr>
		<th>Savings</th>
		<td>$100</td>
		<td>$80</td>
	</tr>
</table>
```

<table><tr><th>Month</th><td>January</td><td>February</td></tr><tr><th>Savings</th><td>$100</td><td>$80</td></tr></table>

```html title:"vertical table"
<table>
	<caption>Monthly Savings<caption/>
	<tr>
		<th>Month</th>
		<th>Savings</th>
	</tr>
	<tr>
		<td>January</td>
		<td>$100</td>
	</tr>
	<tr>
		<td>February</td>
		<td>$80</td>
	</tr>
</table>
```

<table><caption>Monthly savings</caption><tr><th>Month</th><th>Savings</th></tr><tr><td>January</td><td>$100</td></tr><tr><td>February</td><td>$50</td></tr></table>

Per migliorare la strutturazione semantica, e quindi l'accessibilità della tabella si possono usare anche elementi strutturali: `{html icon} <colgroup>`, `{html icon} <thead>`, `{html icon} <tfoot>`, `{html icon} <tbody>`.

#### Attributi delle Celle
>[!summary] Unione di Celle
> Una cella di tipo `{html icon} <td>` o `{html icon} <th>` può ***occupare più righe o più colonne*** utilizzando rispettivamente l'attributo `rowspan` e `colspan`.

>[!failure] Riferimento all'Header
>Una cella di tipo `{html icon} <td>` o `{html icon} <th>` può fare ***riferimento***, tramite l'attributo `headers`, ad altre celle per specificare che queste rappresentano una *intestazione* della cella corrente.
>- `headers` deve avere come valore degli `id` ***separati da spazio***.

```html
<table>
	<caption>Orario delle lezioni</caption>
	<thead>
		<tr>
			<th></th>
			<th id="lun">Lunedì</th>
			<th id="mar">Martedì</th>
			<th id="mer">Mercoledì</th>
		</tr>
	</thead>
	<tbody>
		<tr>
			<th id="9_10">9-10</th>
			<td rowspan="2" headers="lun 9_10 10_11">
			Tecnologie Web</td>
			<td headers="mar 9_10">Analisi</td>
			<td rowspan="2" headers="mer 9_10 10_11">
			Sistemi multimediali</td>
		</tr>
		<tr>
			<th id="10_11">10-11</th>
			<td rowspan="2" headers="mar 10_11 11_12 ">
			Sistemi multimediali</td>
		</tr>
		<tr>
			<th id="11_12">11-12</th>
			<td headers="lun 11_12">Algebra</td>
			<td headers="mer 11_12">Fisica</td>
		</tr>
	</tbody>
</table>
```

<table><caption>Orario delle lezioni</caption><thead><tr><th></th><th id="lun">Lunedì</th><th id="mar">Martedì</th><th id="mer">Mercoledì</th>	</tr></thead><tbody>	<tr><th id="9_10">9-10</th>	<td rowspan="2" headers="lun 9_10 10_11">Tecnologie Web</td><td headers="mar 9_10">Analisi</td><td rowspan="2" headers="mer 9_10 10_11">Sistemi multimediali</td></tr><tr><th id="10_11">10-11</th><td rowspan="2" headers="mar 10_11 11_12 ">Sistemi multimediali</td></tr><tr><th id="11_12">11-12</th><td headers="lun 11_12">Algebra</td><td headers="mer 11_12">Fisica</td></tr></tbody></table>

##### Scope
>[!caution] Attributo
>Nelle tabelle, l'attributo `scope` indica se una cella di intestazione appartiene a una **colonna**, a una **riga**, a un *gruppo di colonne* o a un *gruppo di righe*.

Nell'esempio [[#Attributi delle Celle|precedente]], si potrebbe aggiungere lo `scope` nel seguente modo:
```html
...
	<tr>
		<th></th>
		<th id="lun" scope="colgroup" colspan="2">Lunedì</th>
		<th id="mar" scope="colgroup" colspan="2">Martedì</th>
	</tr>
...
	<tr>
		<th></th>
		<th id="aula21_l" headers="lun" scope="col">Aula 2.1</th>
		<th id="lab22_l" headers="lun" scope="col">Laboratorio 2.2</th>
		<th id="aula21_m" headers="mar" scope="col">Aula 2.1</th>
		<th id="lab22_m" headers="mar" scope="col">Laboratorio 2.2</th>
	</tr>
...
	<tr>
		<th id="9_10" scope="row">9-10</th>
		<td rowspan="2" headers="lun9_10 10_11 aula21_l">Sistemi multimediali</td>
		...
	</tr>
...
```

Migliora solamente l'***accessibilità***.

## List
---
>[!info] Liste
>In `{html icon} HTML5` sono previsti tre tipi di liste:
>- `{html icon} <ul>`: Per le liste ***non ordinate*** (*unordered list*).
>- `{html icon} <ol>`: Per le liste ***ordinate*** (*ordered list*).
>- `{html icon} <dl>`: Per le liste di ***definizioni*** (*definition list*).

Nelle liste *ordinate* e *non ordinate* ogni elemento è definito dal **tag** `{html icon} <li>` (*list item*).

> Liste non ordinate:

- Elemento 1
- Elemento 2

> Liste ordinate:
1. Elemento 1
2. Elemento 2

Nelle liste ordinate possono essere specificati:
- `start`: ***valore iniziale*** della numerazione
- `type`: il ***tipo di numerazione*** usata
- `reversed`: la numerazione è ***inversa***.

Per le liste di definizioni non si usa `{html icon} <li>` ma due elementi che specificano termine `{html icon} <dt>` e definizione `{html icon} <dd>`.

```html
<ul>
	<li>Unodrered Element</li>
	<li>Unodrered Element</li>
	...
</ul>
<ol>
	<li>Element 1</li>
	<li>Element 2</li>
	...
</ol>
<dl>
	<dt>Element</dt>
	<dd>Definition 1</dd>
	<dd>Definition 2</dd>
	...
</dl>
```

> Le liste di definizione sono ***liste associative***
- Pensate per correlare un concetto con uno o più altri termini.
- A ogni termine possono corrispondere più definizioni.

