> [[Docker]] può costruire immagini automaticamente leggendo le istruzioni da un `{dockerfile icon} Dockerfile`.

>[!definizione] 
> Un ***Dockerfile*** è un documento di testo che contiene tutti i comandi che un utente può invocare dalla riga di comando per ***assemblare un'immagine***.

L'esecuzione è divisa in più fasi:
- Fase di build-time, dove viene costruita l'immagine.
- Fase di run-time dove viene eseguito il container, a partire da quello assemblato.

Si può ispezionare il contenuto di una immagine docker tramite il comando:
```sh
docker image inspect image_name
```

Se voglio selezionare solo un campo del file in formato `{json icon} JSON`, posso usare il flag `--format`:
```sh
docker image inspect image_name --format='{{.Id}}'
```

#### Layers
>[!info] Campo Layers
>Il campo ***layers*** del file `{json icon} JSON` in una *docker image configuration object* è una lista di chiavi crittografiche (es. `sha256:...`) che identifica univocamente i [[Docker#Docker Objects|layer read-only]] che formano l'immagine.

---

## Panoramica
>[!hint] Istruzioni
>Il ***Dockerfile*** supporta le seguenti istruzioni:

| Istruzione                 | Descrizione                                                                  |
| -------------------------- | ---------------------------------------------------------------------------- |
| `ADD`                      | Aggiunge file e directory locali o remote.                                   |
| `ARG`                      | Usa variabili al momento della build.                                        |
| `CMD`                      | Specifica i comandi predefiniti.                                             |
| `COPY`                     | Copia file e directory.                                                      |
| `ENTRYPOINT`               | Specifica l'eseguibile predefinito.                                          |
| `ENV`                      | Imposta variabili d'ambiente.                                                |
| `EXPOSE`                   | Dichiara su quali porte è in ascolto l'applicazione.                         |
| `FROM`                     | Crea un nuovo stage di build da un'immagine base.                            |
| `HEALTHCHECK`              | Controlla la salute di un container all'avvio o periodicamente.              |
| `LABEL`                    | Aggiunge metadati a un'immagine.                                             |
| `MAINTAINER` *(deprecato)* | Specifica l'autore di un'immagine.                                           |
| `ONBUILD` *                | Specifica istruzioni da eseguire quando l'immagine viene usata in una build. |
| `RUN`                      | Esegue comandi di build.                                                     |
| `SHELL` *                  | Imposta la shell predefinita dell'immagine.                                  |
| `STOPSIGNAL` *             | Specifica il segnale di sistema per terminare il container.                  |
| `USER`                     | Imposta l'ID utente e gruppo.                                                |
| `VOLUME`                   | Crea mount point per volumi.                                                 |
| `WORKDIR`                  | Cambia la directory di lavoro.                                               |

\* Poco usati.

---

## Formato

```dockerfile
INSTRUCTION arguments
```

Le istruzioni non fanno distinzione tra maiuscole e minuscole, ma per convenzione si scrivono in **MAIUSCOLO** per distinguerle dagli argomenti.

Docker esegue le istruzioni nell'ordine in cui compaiono.
- Un Dockerfile ***deve iniziare con un'istruzione `FROM`*** (che può essere preceduta da direttive parser, commenti e `ARG` globali).
- L'istruzione `FROM` specifica l'**immagine base** da cui si costruisce.

Le righe che iniziano con `#` sono trattate come commenti, a meno che non siano direttive parser valide.
- Un `#` in qualsiasi altra posizione nella riga viene trattato come argomento.

```dockerfile
# Commento
RUN echo 'stiamo eseguendo alcune # cose interessanti'
```

>[!warning] Nota
> Gli ***spazi iniziali*** prima di commenti e istruzioni vengono *ignorati* per compatibilità. Gli spazi bianchi all'interno degli argomenti invece vengono preservati.

---

## Direttive parser
>[!abstract] Info
>Le ***direttive parser*** sono opzionali e influenzano *come vengono interpretate* le righe successive. Si scrivono come commenti speciali nella forma `# directive=value` e devono essere in cima al ***Dockerfile***.

Le direttive parser supportate sono:
- `syntax`
- `escape`
- `check` (dalla versione Dockerfile v1.8.0).

### syntax
---
```dockerfile
# syntax=docker/dockerfile:1
```

Dichiara la ***versione della sintassi Dockerfile*** da usare per la build.
- La maggior parte degli utenti vorrà usare `docker/dockerfile:1` per ottenere automaticamente l'ultima versione stabile.

### escape

```dockerfile
# escape=\
```
oppure
```dockerfile
# escape=`
```

Imposta il ***carattere di escape*** per il Dockerfile.
- Il valore predefinito è `\`.

### check

```dockerfile
# check=skip=<controlli|all>
# check=error=<boolean>
```

Configura come vengono valutati i controlli di build.
- Per default tutti i controlli vengono eseguiti e i fallimenti sono trattati come avvertimenti.

```dockerfile
# check=skip=JSONArgsRecommended,StageNameCasing   # Salta controlli specifici
# check=skip=all                                    # Salta tutti i controlli
# check=error=true                                  # Fallisce la build in caso di avvertimenti
# check=skip=JSONArgsRecommended;error=true         # Combinazione di opzioni
```

---

## Sostituzione di variabili d'ambiente
> Le variabili d'ambiente (dichiarate con `ENV`) possono essere usate in certe istruzioni nella forma `$variable_name` o `${variable_name}`.

La sintassi `{sh icon} ${variable_name}` supporta anche alcune modifiche stile [[CheatSheet#Manipolare il contenuto della variabile|bash]]:
- `${variable:-word}` — usa `word` se la variabile non è impostata
- `${variable:+word}` — usa `word` se la variabile è impostata, altrimenti stringa vuota

Pattern supportati in versioni pre-release della sintassi:
- `${variable#pattern}`
- `${variable##pattern}`
- `${variable%pattern}`
- `${variable%%pattern}`
- `${variable/pattern/replacement}`
- `${variable//pattern/replacement}`

Le istruzioni che supportano la sostituzione di variabili sono: `ADD`, `COPY`, `ENV`, `EXPOSE`, `FROM`, `LABEL`, `STOPSIGNAL`, `USER`, `VOLUME`, `WORKDIR`, `ONBUILD`.

---

## File .dockerignore

>[!info]
>Usa il file `.dockerignore` per escludere file e directory dal contesto di build.

---

## Forma shell e forma exec

>[!help] Forme
>Le istruzioni `RUN`, `CMD` ed `ENTRYPOINT` hanno due forme:
> - **Forma exec:** `ISTRUZIONE ["eseguibile","param1","param2"]` — non invoca una shell; usa array JSON con virgolette doppie.
> - **Forma shell:** `ISTRUZIONE comando param1 param2` — usa automaticamente una shell di comando.

### Forma exec

La forma `exec` è preferita per `ENTRYPOINT`.
- **Non esegue elaborazione shell** né sostituzioni di variabili (usa `sh -c` se le vuoi).

### Forma shell

> Usa automaticamente la shell di comando e supporta continuazioni di riga e heredoc:

```dockerfile
RUN source $HOME/.bashrc && \
echo $HOME

RUN <<EOF
  source $HOME/.bashrc
  echo $HOME
EOF
```

---
## Comandi
### FROM

```dockerfile
FROM [--platform=<platform_name>] <image> [AS <name>]
FROM [--platform=<platform_name>] <image>[:<tag>] [AS <name>]
FROM [--platform=<platform_name>] <image>[@<digest>] [AS <name>]
```

>[!hint] `{docker icon} FROM`
>Inizializza un nuovo stage di build e ***imposta l'immagine base***.

Con `AS <nome>` è possibile dare un nome allo stage per riferirlo in istruzioni successive.

Il flag `--platform` permette di specificare la piattaforma dell'immagine (es. `linux/amd64`, `linux/arm64`).

>[!warning] Ogni `FROM` azzera lo stato delle istruzioni precedenti.
#### Interazione tra ARG e FROM

```dockerfile
ARG  CODE_VERSION=latest
FROM base:${CODE_VERSION}
CMD  /code/run-app
```

Un `ARG` dichiarato prima del primo `FROM` è fuori dagli stage e non è disponibile dopo. Per usarne il valore dentro uno stage, ridichiarare `ARG` senza valore:

```dockerfile
ARG VERSION=latest
FROM busybox:$VERSION
ARG VERSION
RUN echo $VERSION > image_version
```

### RUN

```dockerfile
# Forma shell:
RUN [OPZIONI] <comando> ...
# Forma exec:
RUN [OPZIONI] [ "<comando>", ... ]
```

>[!hint] `{docker icon} RUN`
>***Esegue comandi*** creando un nuovo layer sull'immagine corrente.

Le opzioni disponibili sono:
- `--device`
- `--mount`
- `--network`
- `--security`
#### RUN --mount

> Crea [[File System del Container#Mounts|mount del filesystem]] accessibili durante la build:

| Tipo                 | Descrizione                                                     |
| -------------------- | --------------------------------------------------------------- |
| `bind` (predefinito) | Bind-mount di directory in sola lettura                         |
| `cache`              | Directory temporanea di cache per compilatori e package manager |
| `tmpfs`              | Mount di un filesystem temporaneo in RAM                        |
| `secret`             | Accesso a file segreti senza includerli nell'immagine           |
| `ssh`                | Accesso a chiavi SSH tramite agenti SSH                         |

> Esempio
- Cache pacchetti `{sh icon} apt`:

```dockerfile
RUN --mount=type=cache,target=/var/cache/apt,sharing=locked \
  --mount=type=cache,target=/var/lib/apt,sharing=locked \
  apt update && apt-get --no-install-recommends install -y gcc
```

> Esempio
- Segreti:
```dockerfile
RUN --mount=type=secret,id=aws,target=/root/.aws/credentials \
  aws s3 cp s3://... ...
```

#### RUN --network

> Controlla l'[[Network nei Container|ambiente di rete]] dove i comandi verranno eseguiti:

- `default`: rete predefinita della build.
- `none`: nessun accesso di rete.
- `host`: ambiente di rete dell'host

#### RUN --security
```dockerfile
RUN --security=<sandbox|insecure>
```


- `--security=sandbox`: Predefinito
- `--security=insecure`: Esecuzione senza sandbox, equivalente a `docker run --privileged`

#### RUN --device
```dockerfile
RUN --device=name,[required]
```
### CMD

```dockerfile
CMD ["eseguibile","param1","param2"]   # forma exec
CMD ["param1","param2"]                # parametri predefiniti per ENTRYPOINT
CMD comando param1 param2              # forma shell
```

>[!hint] `{docker icon} CMD`
> Imposta il ***comando predefinito da eseguire*** quando si *avvia* il container.

Solo l'ultimo `CMD` ha effetto. I suoi argomenti possono essere sovrascritti da `docker run`. Non esegue nulla al momento della build.

### LABEL

```dockerfile
LABEL <key>=<value> [<key>=<value>...]
```

>[!hint] `{docker icon} LABEL`
> Aggiunge ***metadati*** all'immagine sotto forma di coppie chiave-valore.

```dockerfile
LABEL "com.example.vendor"="ACME Incorporated"
LABEL version="1.0"
LABEL description="Multiline \
      Description."
```

### MAINTAINER (deprecato)

```dockerfile
MAINTAINER <nome>
```

Imposta il campo *Author* dell'immagine. È preferibile usare `LABEL`:
```dockerfile
LABEL org.opencontainers.image.authors="nome@esempio.com"
```

### EXPOSE

```dockerfile
EXPOSE <port> [<port>/<protocol>...]
```

>[!hint] `{docker icon} EXPOSE`
> ***Documenta*** su quali porte il container è in ascolto (TCP per default).
 
**Non pubblica effettivamente la porta**, serve come documentazione.
- Per pubblicare le porte usa `-p` o `-P` con `docker run`.

```dockerfile
EXPOSE 80/tcp
EXPOSE 80/udp
```

### ENV

```dockerfile
ENV <key>=<value> [<key>=<value>...]
```

>[!hint] `{docker icon} ENV`
> Imposta [[Variabili|variabili d'ambiente]] che persistono nell'immagine risultante e sono disponibili per le istruzioni successive e a runtime.

```dockerfile
ENV MY_NAME="Mario Rossi"
ENV MY_DOG=Rex\ Il\ Cane
```

Se una variabile d'ambiente serve *solo durante la build*, usa `ARG` (non persiste nell'immagine finale) o imposta la variabile inline nel `RUN`.

### ADD

```dockerfile
ADD [OPT] <src> ... <dest>
ADD [OPT] ["<src>", ... "<dest>"]
```

>[!hint] `{docker icon} ADD`
> ***Copia*** file/directory da `<src>` e li *aggiunge al filesystem* dell'immagine in `<dest>`. Le sorgenti possono essere:

- **File/directory locali**: copiati dal contesto di build
- **Archivi tar locali**: decompressi e estratti automaticamente
- **URL remoti**: scaricati
- **Repository Git**: clonati

**Opzioni disponibili:** `--keep-git-dir`, `--checksum`, `--chown`, `--chmod`, `--link`, `--exclude`, `--unpack`.

### COPY
```dockerfile
COPY [OPT] <src> ... <dest>
COPY [OPT] ["<src>", ... "<dest>"]
```

>[!hint] `{docker icon} COPY`
>***Copia*** file/directory dalla *sorgente alla destinazione*.

Simile ad `ADD`, ma più semplice (non gestisce URL o archivi tar).

**Opzioni disponibili:** `--from`, `--chown`, `--chmod`, `--link`, `--parents`, `--exclude`

### ENTRYPOINT

```dockerfile
ENTRYPOINT ["executable", "param1", "param2"]   # exec form
ENTRYPOINT command param1 param2                # shell form
```

>[!hint] `{docker icon} ENTRYPOINT`
> Configura il container *come un eseguibile*.

Gli argomenti di `docker run` vengono aggiunti dopo `ENTRYPOINT` (forma exec) e **sovrascrivono** `CMD`.
- Solo l'ultimo `ENTRYPOINT` ha effetto.

#### Interazione CMD e ENTRYPOINT
> Sia `ENTRYPOINT` che `CMD` concorrono a *definire il comando principale* che viene eseguito appena il container è in esecuzione.

<table>
    <tr>
      <th></th>
      <th>Nessun ENTRYPOINT</th>
      <th><code>ENTRYPOINT exec_entry</code></th>
      <th><code>ENTRYPOINT ["exec_entry"]</code></th>
    </tr>
    <tr>
      <th>Nessun CMD</th>
      <td>errore</td>
      <td><code>/bin/sh -c exec_entry</code></td>
      <td><code>exec_entry</code></td>
    </tr>
    <tr>
      <th><code>CMD ["exec_cmd"]</code></th>
      <td><code>exec_cmd</code></td>
      <td><code>/bin/sh -c exec_entry</code></td>
      <td><code>exec_entry exec_cmd</code></td>
    </tr>
    <tr>
      <th><code>CMD exec_cmd p1_cmd</code></th>
      <td><code>/bin/sh -c exec_cmd p1_cmd</code></td>
      <td><code>/bin/sh -c exec_entry p1_entry</code></td>
      <td><code>exec_entry p1_entry /bin/sh -c exec_cmd p1_cmd</code></td>
    </tr>
</table>
### VOLUME

```dockerfile
VOLUME ["/directory"]
```

>[!hint] `{docker icon} VOLUME`
>Crea un ***mount point*** con il nome specificato, marcato come *volume montato esternamente*.

I dati presenti nel percorso dell'immagine base vengono copiati nel volume alla **creazione del container**.

### USER

```dockerfile
USER <user>[:<group>]
```

>[!hint] `{docker icon} USER`
>Imposta l'***utente*** (e opzionalmente il gruppo) predefinito per le istruzioni `RUN`, `ENTRYPOINT` e `CMD` successive.

### WORKDIR

```dockerfile
WORKDIR /path/to/directory
```

>[!hint] `{docker icon} WORKDIR`
Imposta la ***directory di lavoro*** per le istruzioni `RUN`, `CMD`, `ENTRYPOINT`, `COPY` e `ADD` successive.

Se non esiste, viene creata. Può essere usata più volte.
- Percorsi relativi si riferiscono al `WORKDIR` precedente.

```dockerfile
WORKDIR /a
WORKDIR b
WORKDIR c
RUN pwd   # Output: /a/b/c
```

### ARG

```dockerfile
ARG <nome>[=<valore_predefinito>]
```

>[!hint] `{docker icon} ARG`
>Definisce una ***variabile*** passabile al momento della build con `--build-arg <name>=<value>`.

A differenza di `ENV`, **non persiste** nell'immagine finale.

>[!warning] Attenzione
>Non usare `ARG` per passare segreti, i valori sono visibili in `docker history`.

### ONBUILD

```dockerfile
ONBUILD <instruction>
```

>[!hint] `{docker icon} ONBUILD`
>Aggiunge un'***istruzione trigger all'immagine***, che verrà eseguita quando l'immagine è usata come base per un'altra build.

Utile per creare immagini base *riutilizzabili*.

**Limitazioni:**
- Non è possibile concatenare `ONBUILD`
- Non può attivare `FROM` o `MAINTAINER`

### STOPSIGNAL

```dockerfile
STOPSIGNAL signal
```

>[!hint] `{docker icon} STOPSIGNAL`
> Imposta il ***segnale di sistema*** inviato al container per **terminarlo** (es. `SIGTERM`, `SIGKILL` o numero intero).

Il valore predefinito è `SIGTERM`.

### HEALTHCHECK

```dockerfile
HEALTHCHECK [OPZIONI] CMD comando
HEALTHCHECK NONE
```

>[!hint] `{docker icon} HEALTHCHECK`
>Definisce come Docker ***verifica che il container funzioni correttamente***.

Opzioni:

- `--interval=DURATA` (predefinito: `30s`)
- `--timeout=DURATA` (predefinito: `30s`)
- `--start-period=DURATA` (predefinito: `0s`)
- `--start-interval=DURATA` (predefinito: `5s`)
- `--retries=N` (predefinito: `3`)

Codici di uscita del comando: `0` = sano, `1` = non sano, `2` = riservato.

```dockerfile
HEALTHCHECK --interval=5m --timeout=3s \
  CMD curl -f http://localhost/ || exit 1
```

>[!todo] In altre parole
>Come una sorta di [[ICMP#Comando PING|PING]] di livello applicativo.

---

Traduzione con integrazioni della documentazione ufficiale Docker: https://docs.docker.com/reference/dockerfile/.