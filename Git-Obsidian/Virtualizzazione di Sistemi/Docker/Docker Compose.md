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

> Un file compose è suddiviso in diverse sezioni tra cui:
- `version`: Specifica la *versione del formato* del file compose.
- `services`
- `volumes`: Definisce i [[File System del Container#Mounts|volumi]] per la persistenza dei dati.
- `networks`: Definisce le [[Network nei Container|reti]] per la comunicazione tra i servizi.
- `secrets`: Stabilisce come *fornire informazioni riservate* ai container.

### Sintassi
>[!abstract] Services
>Definisce i ***servizi*** che compongono l'applicazione

```yaml
services:
 web:
  image: nginx:latest
  ports:
   - "80:80"
  volumes:
   - ./nginx.conf:/etc/nginx/nginx.conf
  depends_on:
   - app
  networks:
   - my_network
 app:
  build: ./app
  ports:
   - "5000:5000"
  environment:
   MYSQL_HOST: db
  networks:
   - my_network
```

L'oggetto è composto da più oggetti identificati da un nome (`web` e `app`)
- I campi dei servizi sono molto simili alle opzioni del [[Docker Cheatsheet|comando docker run]].

Tra le proprietà del servizio ci sono:
- `image`: Specifica il ***nome*** dell'immagine da scaricare dalla [[Docker#Nome di una Immagine Docker|repository]]
- `build`: Indica che l'immagine non deve essere scaricata ma deve essere creata con un [[Dockerfile]], come valore si indica il percorso del `{dockerfile icon} Dockerfile`, se si specifica sia `image` che `build`, il parametro `image` definisce solo il nome dell'immagine.
- `ports`: Indica una lista di porte. ("*La porta* $x$ *del container è mappata alla porta* $y$ *dell'host*")
- `depends_on`: Specifica che il servizio per funzionare necessita di altri servizi.
- `enviroment`: Dichiara ***variabili d'ambiente*** che verranno create all'interno del container.
- `volumes`: Monta dei volumi sul container, la sintassi è uguale a quella del comando `{sh icon} docker run`

Altri comandi:
- `healthcheck` definisce una serie di operazioni per verificare il *corretto funzionamento del container*.
- `restart` indica cosa deve essere fatto nel caso il container non venga eseguito con successo.


>[!cite] Volumes

```yaml
volumes:
 db_data:
networks:
 my_network:
```

### Comandi docker Compose
>[!tldr] Info
>***Docker compose*** ha diversi comandi utili per la creazione, avvio e rimozione dei container definiti all'interno del *file compose*.

> Esempi

```sh
docker compose build
```

Costruisce le immagini definite nel compose file.
- Vengono costruite solo le immagini definite dal parametro `build`.

```sh
docker compose up
```

Avvia i servizi definiti nel compose file.
- Si aggancia alla shell corrente, con il flag `-d` viene lanciata il background (*daemonize*).

```sh
docker compose down
```

Arresta e rimuove i servizi del compose file.
- Con il flag `--rmi all` **rimuove** anche tutte le *immagini create*.
- Con il flag `-v` rimuove anche i volumi.

