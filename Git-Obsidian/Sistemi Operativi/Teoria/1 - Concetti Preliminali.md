## File System
---
>[!info] Definizione
>Il ***file system*** è l'*organizzazione del disco rigido* che permette di contenere i file e le loro informazioni
>>[!caution] Partizioni
>>Lo spazio nel disco rigido è *diviso* in una o più parti dette ***partizioni***

Le partizioni contengono:
- Dei *contenitori di dati* detti ***files***
- Dei *contenitori di files* detti ***directories***

### Windows:
> Le partizioni sono viste come ***logicamente separate*** e a ciascuna è indicata da una lettera (`C:`, `D:`, `E:`)
 
Non c'è il concetto di ***priorità fra partizioni***, non ce n'è una più importante dell'altra sono partizioni "***simili***"

>[!tldr] Percorso
>Se un file si chiama `file.txt` ed è contenuto in una *directory* che si chiama `documenti` che è contenuta in una cartella che si chiama `home` contenuta nella ***partizione*** `C:`
>- `file.txt` è ***univocamente individuabile*** dal percorso, mediante il quale partendo dalla partizione `C:` si arriva al *file*
>	- `C:\home\documenti\file.txt` è il ***percorso assoluto*** del file

>[!quote] Partizioni Remote
> Il sistema operativo è in grado di ***montare una partizione in locale***, facendo vedere come se fosse una porzione di disco della macchina, qualcosa che in realtà è ***montata in remoto***

### Unix-Like
> Esiste il concetto di ***priorità fra partizioni***

Esiste una ***partizione principale***: `/`
- Le altre partizioni devono essere ***logicamente collocate*** dentro alla *partizione principale*, in un qualche punto dell'albero della partizione principale
- L'origine del *file system* è chiamata ***radice*** o ***root***

>[!summary] Percorso
> Se un file si chiama `file.txt` ed è contenuto in una cartella che si chiama `documenti` che è contenuta in una cartella che si chiama `home` contenuta nella partizione `/`
> - `file.txt` è ***univocamente individuabile*** dal percorso, mediante il quale partendo dalla partizione `/` si arriva al file
> 	- `/home/documenti/file.txt` è il ***percorso assoluto*** del file



![[../Bash/attachements/Unix-Like_fileSystem.png|350]]
>*Esempio di strutturazione in directories e files delle partizioni di un file system Linux*


>[!warning] Come capire se un nome in un percorso indica una directory o una partizione?

>*Boh?*

#### File Nascosti
>[!hint] Definizione
>I ***file nascosti*** sono file il cui nome incomincia con `.`

Se un file è considerato *nascosto*
- ***Non viene visualizzato*** se lanciato il comando `ls` senza specificare il flag `-a`

#### Directory Non Salvate nel Disco Rigido
>[!info] `/proc`
>La cartella `/proc` contiene delle ***informazioni sul sistema operativo*** e sui ***processi attivi*** al momento
>>[!warning] Questa cartella è una rappresentazione della struttura interna del kernel
>>Di conseguenza ***non è salvata*** da alcuna parte (o *salvata* in "`RAM`")

