> Le immagini dei [[Container]] sono salvate nel ***registry*** del *daemon docker*, cioè nel file system dell'host.

>[!help] Docker Area
>La directory predefinita all'interno dell'host è detta ***docker area***, e di default è la directory `/var/lib/docker/`.

Le immagini sono composte a layer, se applico delle modifiche ad una immagine di base, salvare la nuova immagine consiste nel salvataggio di solo i nuovi file in un livello aggiuntivo, la nuova immagine sarà composta dalla immagine originale + il livello "finale".

Sistema Copy-on-Write (CoW). o file system differenziale.