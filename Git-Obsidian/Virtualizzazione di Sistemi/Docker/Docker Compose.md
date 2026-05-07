## File YAML
---
>[!definizione]
>`{yaml icon} YAML` (***Yet Another Markup Language***) è un formato di serializzazione di dati *leggibili ad esseri umani*.

È molto usato per *configurazioni* perché è semplice e ordinato.

>[!tldr] Idea di Base

`YAML` è fatto di chiavi e valori organizzati in una struttura gerarchica con indentazione.
- Indentazione è fatta ***necessariamente di spazi***.

### Struttura
> Alla base è un semplice oggetto composto da ***chiave e valore***.

Ogni chiave è seguita da `:` e poi dal valore.

>[!info] Valori
- Non servono apici se il ***valore è semplice***.
- I *valori* possono essere **stringhe**, **numeri**, **booleani** o **oggetti**.
- I *valori* possono anche essere **multipli**, nel qual caso si parla di liste, ogni elemento della lista sta in una riga diversa ed è preceduta dal carattere "`-`".
	- Gli elementi della lista *devono essere indentati* rispetto alla chiave.
- I *valori* possono essere oggetti, l'oggetto deve essere indentato.

```yaml title:Example
services:
 web:
  image: nginx:latest
  depends_on:
   - app
 app:
  build: ./app
  ports:
   - "80:80"
```

> Modo compatto per liste di oggetti

```yaml
people:
 - { name: Luca, age: 28 }
 - { name: Laura, age: 32 }
```

> Stringhe multi-linee
- Si può scrivere un valore distribuendolo su più righe per comodità di visualizzazione o per inserire delle andate a capo nel valore.
	- Nel primo caso è sufficiente specificare il simbolo `>`.
	- Nel secondo caso occorre specificare il simbolo `|`.

```yaml
descrizione: >
 Questa è una stringa
 multilinea YAML che viene
 trattata come una sola linea.
testo: |
 Questa è una stringa multilinea
 che mantiene i newline.
```

#### Alias e Riferimenti
>[!abstract] Info
>`YAML` permette di definire ***alias*** per evitare ripetizioni.
>La *definizione dell'alias* definisce un valore (semplice, lista o oggetto) a cui ci si può riferire in un punto del file per usare una copia del valore.

Nella definizione il nome dell'alias viene specificato con `&` mentre il punto in cui si vuole usare l'alias si indica con `*`.

```yaml
# key_name: &alias_name value

# Defining the 'location' anchor with value Milan
original_location: &location Milan
office: *location
residence: *location
```

>[!danger] L'alias **non** può essere usato al posto del nome della chiave

Se l'alias è un valore complesso, per usarlo devo usare la notazione `YAML` "***merge key***"
```yaml
base_person: &person # saving the entire object as an anchor
 name: Luca
 city: Milan

employee:
 <<: *person
 role: Developer

client:
 <<: *person
 customer_code: 1234
```

## Compose File
---
>[!tldr] Idea
>Un ***compose file*** è un file `YAML` utilizzato da [[Docker]] *compose* per definire e gestire applicazioni multi-[[Container]].

Il formato di un compose file richiede specificatamente che alcune chiavi abbiano come valore delle mappe (oggetti), ed altre delle liste.