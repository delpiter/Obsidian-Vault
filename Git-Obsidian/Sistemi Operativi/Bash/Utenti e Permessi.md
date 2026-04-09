## Utenti e Gruppi
---
>Nei sistemi *Unix* esistono le astrazioni di utente (***user***) e gruppo di utenti (***group***)

>[!utente]
>Caratterizzato da una stringa `username` che contiene il ***nome utente*** ("*studente*", "*vic*", "*syslog*")
>>Un utente può corrispondere ad una ***persona umana*** oppure essere solo la rappresentazione di una entità usata per indicare chi è chi esegue un servizio di sistema

>[!summary] Gruppo
>Caratterizzato da una stringa `groupname` che contiene il nome del gruppo
>("*staff*", "*admin*")

Ciascun ***utente*** appartiene ad ***uno o più gruppi***

Ciascun ***file*** e ***directory*** del [[../Teoria/1 - Concetti Preliminali#File System|file system]] appartiene ad un ***utente***, detto *proprietario* del file ("***owner***")
- Normalmente è l'utente che ha creato il ***file/directory***

Ciascun ***file*** e ***directory*** è associata ad un ***gruppo***

>[!attention] Accesso
>Un utente può *tentare di accedere* ad un ***file***, chiedendo di ***leggere*** o ***modificare*** il contenuto, oppure di ***eseguire*** un file eseguibile, anche se non è l'***owner***

Viene indicato col termine ***effective user***:
- L'***utente*** che cerca di accedere ad un file
- Permette di ***distinguere*** tra chi sta ***usando*** il file e chi ne è il ***proprietario***.
	- Il proprietario di un file stabilisce chi può ***accedere*** a quel suo file, configurando i permessi di accesso a quel file.

## Permessi
---
>Comandi per i cambi dei permessi

- `chown`: cambio dell'***owner*** del ***file/directory***
- `chmod`: cambio dei ***permessi*** del ***file/directory***
### Permessi dei File
> I ***permessi di un file*** sono divisi in ***3 gruppi***

>[!info] Permessi
>>[!caution] Permessi dell'*Utente*
>>Permessi assegnati all'***owner*** del file 
>
>>[!abstract] Permessi del *Gruppo*
>> Permessi assegnati ai ***gruppi***
>
>
>>[!example] Altri permessi
>>Permessi assegnati a ***tutti gli altri***

Per vedere i permessi dei ***file*** in una ***directory*** si usa il comando `ls -l`: 
- "Fammi vedere tutti i file della directory corrente e i relativi permessi"

```bash
~/Unibo/OOP/oop-lab02$ ls -l
total 32
drwxr-xr-x 4 pinacoteca pinacoteca 4096 Oct  1 13:26 20-compilation-basics
drwxr-xr-x 4 pinacoteca pinacoteca 4096 Oct  1 13:28 21-compilation-with-packages
drwxr-xr-x 4 pinacoteca pinacoteca 4096 Oct  1 13:30 22-compilation-classpath
drwxr-xr-x 4 pinacoteca pinacoteca 4096 Oct  1 13:33 23-reference-value
drwxr-xr-x 4 pinacoteca pinacoteca 4096 Oct  1 13:36 24-program-arguments
drwxr-xr-x 4 pinacoteca pinacoteca 4096 Oct  1 17:26 25-constructors
drwxr-xr-x 4 pinacoteca pinacoteca 4096 Sep 30 12:49 26-array
drwxr-xr-x 3 pinacoteca pinacoteca 4096 Sep 30 12:19 27-debug
```

Nella prima colonna escono una serie di ***10 caratteri***:
- Il ***primo*** indica
	- `d` se è una ***directory***
	- `-` se è un ***file***
- Gli altri ***9***, divisi in gruppi da 3, rispettivamente: ***owner***, ***gruppi*** e ***altri***
	- `rwx` con possibili `-` al posto di qualsiasi dei 3 caratteri
		- `r` permesso di lettura (***read***)
		- `w` permesso di scrittura (***write***)
		- `x` permesso di esecuzione (***execute***)
	- Se è presente un `-`, significa che non c'è il permesso corrispondente

>[!quote] Caso Speciale: `s`
>La `s` inserita nella parte di permessi ***utente***, che *sostituisce* la `x` di ***esecuzione***, indica che quando il file viene eseguito da chi ha i permessi, l'esecuzioni avviene con i ***permessi del proprietario*** dell'eseguibile
>>[!done] Serve per effettuare operazioni con i permessi dell'amministratore di sistema

Può capitare anche una `S` *maiuscola*, in quel caso significa che il proprietario del file ha ***commesso qualche errore*** nella configurazione del *permesso*

#### Esempio
>Sia `-rwxr-xr-x` il permesso dato

>[!question] Che cosa possiamo dire?

Il primo `-` ci indica che l'elemento del ***file system*** su cui è stato chiamato il comando è un ***file***

L'***owner*** può:
- Leggere: `r`
- Scrivere: `w`
- Eseguire `x`

I ***gruppi*** possono:
- Leggere: `r`
- ~~Scrivere~~: `-`
- Eseguire `x`

***Tutti gli altri*** possono:
- Leggere: `r`
- ~~Scrivere~~: `-`
- Eseguire `x`

>[!warning] I permessi dei file non sono contenuti nel file ma sono contenuti all'interno della directory

### Permessi delle Directory
>Diversi concettualmente dai ***permessi dei file***

Stesso format per *Utente*, *Gruppi* e *Altri*:
- `drwxr-xr-x`

>[!info] Permesso di Lettura alla Directory

Il ***permesso di lettura alla directory***, permette di fare il *listing* dei file della directory
- Consente l'utilizzo dell'esecuzione del comando `ls`

#### Comando `ls -ld`
La flag `-d` indica che il comando deve ritornare ***informazioni sulla directory*** specificata
- Invece di ritornare informazioni sul contenuto della directory


>[!attention] Permesso di Scrittura di una Directory

Il ***permesso di scrittura di una directory***, permette di modificare il contenuto della directory:
- *Creazione*
- *Eliminazione*
- *Rinomina* dei file

>[!abstract] Permesso di Esecuzione della Directory

Il ***permesso di esecuzione di una directory***, significa avere la possibilità di cambiare la directory corrente, spostandosi sulla directory specificata.
- Se ho il permesso di *esecuzione*, posso eseguire il ***comando*** `cd` ed entrare dentro la directory