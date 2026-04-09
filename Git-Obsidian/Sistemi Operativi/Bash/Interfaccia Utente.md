## Tipi di Interfacce
---
>[!info] Interfacce
> Il sistema operativo può avere 2 tipi diversi di interfaccia
> 
>>[!tldr] Command Line Interface
>>Interfaccia composta da una interfaccia funzionante a ***comandi*** (una serie di *caratteri*)
>>>[!done] Pro
>>> Comunicazione più veloce fra macchine in remoto
>>> - Vengono trasferiti solo pochi `byte`, sotto forma di ***messaggi testuali***, al posto di un intero aggiornamento dell'*interfaccia grafica*
>>>
>>> Automatizzazione delle operazioni
>>> - Possibilità di scrivere ***script*** che eseguono una serie di comandi 
>
>>[!summary] Graphical User Interface
>>Interfaccia che sfrutta ***finestre*** sparate e un ***mouse*** per controllare la posizione dell'utente
>>- Nei sistemi più moderni, la `GUI` implementa un terminale a caratteri

![[attachements/GUI.png|400]]
>*Esempio di finestra (window) in una interfaccia grafica*

![[attachements/CLI.png]]
>*Esempio di interfaccia a caratteri*


## Command Line Interface
---
>[!info] CLI
>L'interfaccia a caratteri è una interfaccia che è in grado di recepire dei ***comandi*** costituiti da ***sequenze di caratteri***
>>[!tldr] Inteprete
>>L'***interprete*** di *comando* (*shell*) è un programma che è in grado di leggere i caratteri da tastiera
>>- Per le `CLI` più semplici il *comando* viene ***letto*** solo quando viene premuto il tasto *invio*, da qui la sequenza di caratteri viene passato all'*interprete* che ***legge*** e ***esegue*** le operazioni richieste
>>
>>Nelle interfacce più moderne, l'*interprete* legge anche ***durante la scrittura***, *interpretando i singoli caratteri* facendo delle operazioni che ci ***facilitano l'utilizzo*** del terminale:
>>- Completamento dei comandi e dei nomi dei file

Quando si preme "***invio***" la sequneza viene ricevuta e la shell analizza il contenuto e decide cosa fare:
- Nella riga di comando ci possono essere degli ***ordini sbagliati***
	- La shell non fa nulla, spesso stampa a video, l'errore

#### Shell nei diversi Sistemi Operativi
>[!info] Unix-Linux-Mac: ***Bash***

>[!hint] Windows: ***DOS***

#### Standard POSIX
>[!info] Definizione
>*Standard* che cerca di ***uniformare alcune funzionalità*** che i sistemi operativi mettono a disposizione degli utenti e linguaggi di programmazione

### Avvio della shell bash
>L'interprete bash si comporta in modo diverso in base a quali argomenti gli vengono passati all'avvio
Separati in 3 gruppi

>[!caution] Shell non interattiva
>Una `shell` **non** interattiva è una `shell` "*figlia*" che esegue script, si crea inserendo il *flag* `-c`
>All'esecuzione del comando `./executable.sh`, la `bash` esegue in realtà:
>- `/bin/bash -c ./executable.sh`
>>[!missing] Non è possibile personalizzare questa `shell`


>[!abstract] Shell Interattiva di login
> Una `shell` *interattiva di login* è la `shell` che viene eseguita quando un sistema operativo **non ha una interfaccia grafica**, si crea inserendo il *flag* `-l` o `--login`
> 
> Cerca di *eseguire* i seguenti file:
>- `/etc/profile`
>	- Viene eseguito dalla `bash` tramite il comando `source` [[Esecuzione dei File#Comando `source`|(*]])
>		- Il comando imposta le ***variabili di default*** della `shell`
>- *Uno solo* (il primo trovato) tra: `.bash_profile`,`.bash_login`, `-profile`
>- Il *file* `.bashrc` nella home directory dell'utente
>
>>[!done] Il file `.bashrc` permette di ***personalizzare*** la `shell` 
>
>- Chiede uno *username* e successivamente una *password*
>- Una volta **verificato l'utente** si apre una *shell interattiva*


>[!tldr] Shell interattiva non di login
> Una `shell` che viene eseguita all'*apertura* di una finestra di un terminale
>>[!done] Il file `.bashrc` permette di ***personalizzare*** la `shell`

>Quando termina esegue il file `.bash_logout`