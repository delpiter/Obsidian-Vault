> Le immagini dei [[Container]] sono salvate nel ***registry*** del *daemon docker*, cioè nel file system dell'host.

>[!help] Docker Area
>La directory predefinita all'interno dell'host è detta ***docker area***, e di default è la directory `/var/lib/docker/`.

Quando viene creato, un container possiede un *file system iniziale* che è quello contenuto nella propria immagine.
- I container che eseguono a partire da una stessa immagine condividono in ***sola lettura*** il file system dell'immagine nella **docker area**.

Durante l'esecuzione il container può **modificare** il contenuto del proprio file system. Le modifiche verranno salvate in uno ***strato superiore*** rispetto all'immagine originale del container.

>[!check] Copy-on-Write
> Questo ***layer differenziale*** viene salvato sul file system dell'host, nella **docker area**. Questo tipo di immagine si dice ***Copy-on-Write***.

Ciò è *efficiente* perché esisterà **solo una istanza dell'immagine originale** (***read only***), ogni container avrà poi una propria copia con le sole modifiche, risparmiando memoria sul disco.

Il daemon docker definisce una dimensione massima occupabile dal file system di ciascun container pari a $10Gb$ .
- Configurazione modificabile tramite il file di configurazione del daemon docker (`/etc/docker/daemon.json`).

## Mounts
---
> Docker di default supporta i seguenti tipi di ***mount***, per memorizzare dei dati al di fuori del layer scrivibile dal container.

>[!question] Motivazioni dell'aggiunta di mount al file system dei container

> 1. ***Persistenza dei dati***

Se il container deve salvare alcune modifiche, affinché *sopravvivano* alla propria rimozione, deve collocare queste modifiche in delle partizioni (***esterni al container***) montate nel file system.
- Le modifiche ai file **non** vengono salvate ***incrementalmente*** nel file system principale nel container.

> 2. ***Condivisione*** tra container dell'host

Gli storage esterni possono essere acceduti ***contemporaneamente da più container***.

> 3. ***Superamento del limite*** su spazio disco del container

Lo spazio occupato negli storage esterni non concorre a saturare il limite di spazio disco di $10Gb$ dei container.

> 4. ***Efficienza*** delle scritture su disco

In caso di container che devono modificare spesso i propri files ([[Git-Obsidian/DataBase/Introduzione#Database|Database]]) è meglio usare files in storage esterni che hanno un file system che ***non usa il modello copy-on-write***.

> 5. ***Eliminazione*** delle scritture su disco

Se il container sa che le modifiche apportate al file system dovranno essere 
**eliminate** dopo la terminazione, è meglio risparmiare scritture su disco montando un volume esterno di tipo `TMPFS` che *non scrive su disco*.

> 6. ***Condividere*** dati tra container di *macchine diverse*

Può essere necessario configurare più repliche di uno stesso servizio, che devono perciò ***accedere agli stessi file***.
- Un modo è quello di sfruttare i volumi appoggiandosi ad uno **storage remoto**.
### TMPFS Mounts
>[!definizione]
>I `TMPFS` ***mounts*** sono file system creati in memoria [[RAM]].

Si può dare un nome al mount o si può mantenere anonimo.
>[!warning] Questi mount vengono svuotati quando il container termina e distrutti alla rimozione.

Sono utilizzati per file di appoggio, consentono un accesso veloce ad astrazioni di files (es. [[Cache]]).
### Bind Mounts
>[!definizione]
> I ***bind mounts*** sono directory in *percorsi qualunque del file system* dell'host che vengono fatti vedere al container come partizioni, **formattate con un file system**.

Sono identificati dal percorso assoluto nel file system dell'host.
- La partizione vista dal container ha lo ***stesso formato del file system*** dell'host.
### Volume Mounts
>[!definizione]
> I ***volume mounts*** sono *spazi di disco creati da docker* e salvati in una directory predefinita della ***docker area*** dell'host.

Si può assegnare al volume un nome (*named volume*) per poter fare usare il volume a più container.
- Si può mantenere un volume anonimo (*anonymous volume*).
>[!warning] Non possono esistere due volumi con lo stesso nome

