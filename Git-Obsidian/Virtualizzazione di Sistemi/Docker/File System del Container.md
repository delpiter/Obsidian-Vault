> Le immagini dei [[Container]] sono salvate nel ***registry*** del *daemon docker*, cioè nel file system dell'host.

>[!help] Docker Area
>La directory predefinita all'interno dell'host è detta ***docker area***, e di default è la directory `/var/lib/docker/`.

Quando viene creato, un container possiede un *file system iniziale* che è quello contenuto nella propria immagine.
- I container che eseguono a partire da una stessa immagine condividono in ***sola lettura*** il file system dell'immagine nella **docker area**.

Durante l'esecuzione il container può **modificare** il contenuto del proprio file system. Le modifiche verranno salvate in uno ***strato superiore*** rispetto all'immagine originale del container.

>[!info]
>I container che eseguono a *partire da una stessa immagine* condividono in ***sola lettura*** il file system dell'immagine nella docker area.

![[attachements/DifferentialLayer.png]]

>[!check] Copy-on-Write
> Questo ***layer differenziale*** viene salvato sul file system dell'host, nella **docker area**. Questo tipo di immagine si dice ***Copy-on-Write***.

Ciò è *efficiente* perché esisterà **solo una istanza dell'immagine originale** (***read only***), ogni container avrà poi una propria copia con le sole modifiche, risparmiando memoria sul disco.
- Ogni layer è identificato da un digest univoco, calcolato con una [[../../Algoritmi e Strutture Dati/Strutture Dati/Hash/Funzione di Hash|Funzione di Hash]] partendo dal contenuto del layer stesso.

Il daemon docker definisce una dimensione massima occupabile dal file system di ciascun container pari a $10Gb$ .
- Configurazione modificabile tramite il file di configurazione del daemon docker (`/etc/docker/daemon.json`).


In sistemi molto grandi, la docker area nel sistema host, è una ***partizione separata*** con un file system specializzato come: `btrfs`, `overlayfs`, etc...

>[!tip] File System Sovrapposto
> Nel caso la docker area non sia in una partizione dedicata, il daemon *adatta il file system esistente* alle proprie esigenze

>[!warning] Dangling Images
> Potrebbero esserci alcune immagini intermedie che sono state *create durante il build* per funzionare come cache per build successivi.
> Quando queste immagini non sono più referenziate da nessuna immagine o container (es. è stato cambiato il [[Dockerfile]]), tali immagini sono dette ***dangling***.

Si possono visualizzare tutte le ***immagini dangling*** attraverso il seguente comando:
```sh
docker images -f dangling=true
```

## Mounts
---
> Docker di default supporta i seguenti tipi di ***mount***, per memorizzare dei dati al di fuori del layer scrivibile dal container.

>[!danger] Attenzione
>I container sono effimeri, ciò significa che ***ogni cosa salvata dentro al file system*** del container **sarà persa** quando il container verrà terminato e rimosso.

>[!question] Motivazioni dell'aggiunta di mount al file system dei container

> 1. ***Persistenza dei dati***

Se il container deve salvare alcune modifiche, affinché *sopravvivano* alla propria rimozione, deve collocare queste modifiche in delle partizioni (***esterni al container***) montate nel file system.
- Le modifiche ai file **non** vengono salvate ***incrementalmente*** nel file system principale nel container.

> 2. ***Condivisione*** tra container dell'host

Gli storage esterni possono essere acceduti ***contemporaneamente da più container***.

> 3. ***Superamento del limite*** su spazio disco del container

Lo spazio occupato negli storage esterni non concorre a saturare il limite di spazio disco di $10Gb$ dei container.

> 4. ***Efficienza*** delle scritture su disco

In caso di container che devono modificare spesso i propri files ([[../../DataBase/Introduzione#Database|Database]]) è meglio usare files in storage esterni che hanno un file system che ***non usa il modello copy-on-write***.

> 5. ***Eliminazione*** delle scritture su disco

Se il container sa che le modifiche apportate al file system dovranno essere 
**eliminate** dopo la terminazione, è meglio risparmiare scritture su disco montando un volume esterno di tipo `TMPFS` che *non scrive su disco*.

> 6. ***Condividere*** dati tra container di *macchine diverse*

Può essere necessario configurare più repliche di uno stesso servizio, che devono perciò ***accedere agli stessi file***.
- Un modo è quello di sfruttare i volumi appoggiandosi ad uno **storage remoto**.
### Bind Mounts
>[!definizione]
> I ***bind mounts*** sono directory in *percorsi qualunque del file system* dell'host (o di un host remoto) che vengono fatti vedere al container come partizioni, **formattate con un file system**.

Sono identificati dal percorso assoluto nel file system dell'host.
- La partizione vista dal container ha lo ***stesso formato del file system*** dell'host.

Nel comando `{docker icon} docker run` l'opzione `-v` specifica il percorso della directory dell'host che deve essere condivisa e il percorso del del container in cui il volume sarà montato.
```docker
docker run -v /home/user/htdocs:/usr/local/apache2/htdocs
```

>[!important] Nota Bene
>Quando un container termina o viene fermato (con `docker stop`) i suoi bind mounts ***non vengono eliminati***.
>

Se faccio ripartire il container, quel container si ritrova montati gli **stessi bind mounts** che aveva in precedenza.
- Se qualcuno sposta la directory esterna o ha cambiato i permessi a cui il container si collegava, il container potrebbe *non avere più il bind*. 
### Volume Mounts
>[!definizione]
> I ***volume mounts*** sono *spazi di disco creati da docker* e salvati in una directory predefinita della ***docker area*** dell'host.

#### Categorie
>[!hint] Named volumes
>I ***named volumes*** vengono creati assegnando un nome esplicito, sono facili da individuare, riusare tra più container e gestire tramite `CLI`.

```docker
docker run -d -v myVolume:/app/data myImage
```

>[!warning] Non possono esistere due volumi con lo stesso nome

>[!missing] Unnamed Volumes
>I ***volumi anonimi*** vengono creati senza che l'utente assegni loro un nome.

```docker
docker run --rm -d -v /app/data myimage
```

Docker assegna un [[../../Algoritmi e Strutture Dati/Strutture Dati/Hash/Funzione di Hash|hash]] casuale come nome.

Sono difficili da gestire manualmente, non se ne conosce il nome.
- Difficili da condividere o riutilizzare tra più container.
- Tendono ad accumularsi come **zombie** se non si usa il flag `--rm` nel comando `docker run`.

#### Driver per i Mounted Volumes
>[!info]
>Ogni volume viene creato e gestito per tramite di un ***driver*** che serve come interfaccia tra il daemon con lo storage che contiene il volume.

Esistono due principali categorie di ***driver***:
- Local
- Volume Plugins

Supponiamo che nell'host ci sia un disco `/dev/sdb` con una partizione `/dev/sdb1` formattata con un file system di tipo `btrfs`.

```sh title:syntax
docker volume create --driver local \ #back slash just for new line
	--opt type=btrfs \
	--opt device=/dev/sdb1 \
	volumeName
```
I parametri preceduti da `--opt` sono passati al driver del volume.

Sarà poi necessario ***montare il volume*** nel file system del container.
```docker
docker run --rm -it -v volumeName:/root/my_storage ubuntu
```

##### Driver Local
>[!help] Info
>Il ***driver local*** è il driver predefinito di docker, usa le funzionalità del kernel linux e dei suoi moduli.

Usa internamente il comando `{sh} mount` di linux per montare e accedere alle partizioni e ai file system di tipo standard.
- Tutto ciò che può fare il `{sh} mount`  nell'host lo può fare il driver dei volumi local.

Il *driver local* normalmente non consente di limitare la dimensione di un volume.
- I file system sottostanti **non** supportano la ***gestione delle quote***.
- Si può montare una partizione con un tipo di file system che le supporta e creare un volume di dimensione specificata.

> Per usare uno storage esterno:
- Occorre sempre montare la partizione esterna sull'host.
- Questo mount può essere fatto manualmente dall'utente sull'host o in automatico dal daemon docker stesso.
##### Volume Plugins
>[!help] Info
>I ***volume plugins*** sono driver esterni, che non fanno parte di Linux, che devono essere installati.
>>[!hint] Per far funzionare questi driver occorre abilitare alcuni moduli aggiuntivi del ***kernel Linux***

Mirano principalmente a due scopi:
1. **Accedere** a file system di tipologia non nativamente gestita dal Kernel Linux.
2. Consentire di **interagire** con i volumi secondo modalità aggiuntive che il driver local non implementa.

> Esempio
- Se voglio usare volumi che si appoggiano su storage raggiungibili con `SSHFS` devo installare un driver dei volumi per `SSHFS`, poiché il comando `mount` **non** gestisce direttamente storage remoti con `SSHFS`.
- Se voglio montare un disco `EBS` o `EFS` (Entrambi forniti da *amazon* `AWS`), il driver ***local*** non basta, serve un driver che parli con le `API` di amazon.
- Se voglio usare uno "***storage a blocchi esterni***" come `Longhorn`, devo usare dei driver specifici.

>[!question] Quando vengono utilizzati?

Si usano solitamente quando occorre che docker ***crei dinamicamente il volume sul file system distribuito remoto*** senza che l'utente debba montare la partizione prima.

> Questi driver aggiuntivi funzionano così:

Quando deve essere creato un container con un volume in un `FS` distribuiti remotoç
1. Il daemon docker sfrutta il driver e fa automaticamente il mount del file system distribuito in un [[Container#Namespaces|namespace]] di mount separato.
2. Il daemon crea il volume sopra la partizione montata e lo rende disponibile al container.
3. Quando il container termina, il daemon ***smonta automaticamente*** la partizione.

### TMPFS Mounts
>[!definizione]
>I `TMPFS` ***mounts*** sono file system creati in memoria [[../../Architettura degli Elaboratori/Architettura del Calcolatore/RAM|RAM]].

Si può dare un nome al mount o si può mantenere anonimo.
>[!warning] Questi mount vengono svuotati quando il container termina e distrutti alla rimozione.

Sono utilizzati per file di appoggio, consentono un accesso veloce ad astrazioni di files (es. [[../../Architettura degli Elaboratori/Architettura del Calcolatore/Cache|Cache]]).

```docker title:syntax
docker volume create --driver local /
  --opt type=tmpfs /
  --opt device=tmpfs /
  --opt o=size=100m,uid=1000 /
  volumeName
```

In questo caso l'opzione che specifica la dimensione della partizione può essere usata.
Con l'opzione `uid=1000` indico che il mount è di proprietà dell'utente con `uid=1000`.
- Se nel container non esiste uno *user id* `1000` allora durante la creazione del container avviene un **errore nel mount**.

## File System Distribuiti
---
>[!definizione]
>Un ***file system distribuito*** è un file system tale che:
>- Dati e metadati sono *memorizzati su più server* a scopo di efficienza e robustezza.
>- Viene montato e usato mediante *protocolli* su client.
>- Realizza qualche forma di atomicità delle operazioni sui file.
>- Acceduto da client mediante ***protocolli standard***.

>[!example] Esempi

> `SSHFS`:
- **Non** un vero file system distribuito, è un protocollo di accesso a file system remoto su un unico server. **NON** fornisce alcun meccanismo di atomicità.

> `NFS`:
- **Non** un vero file system distribuito.
- Protocollo di accesso remoto a un file system che risiede su un unico server.
- Fornisce un ***meccanismo di*** [[../../Sistemi Operativi/Teoria/13 - Semafori|lock]] sui file, avviato quando un file viene aperto da un client.
- Molto ***efficiente***.

> `GlusterFS`:
- File system distribuito vero e proprio.
- I files sono ***copiati su più server***, i server si sincronizzano tra loro.
	- Se un server *fallisce*, i file sono disponibili sugli altri.
- Gestisce ***lock*** sui file in maniera **trasparente**.
- **Non** molto *efficiente* e *scalabile*.

> `MooseFS`:
- File system distribuito con una ***gestione centralizzata in un master*** che mantiene metadati.
- Altri server replicati **mantengono i files** veri e propri.
- Il server master *può essere replicato*.

> `Ceph`
- File system distribuito.
- Ci sono molti server che dividono e replicano i dati.
- Usa meccanismi per garantire ***atomicità***.
- Ha ***prestazioni eccellenti*** per velocità di accesso e per scalabilità e robustezza.
	- **Molto complesso** da configurare bene.
- Adatto per grandi *datacenter*.

