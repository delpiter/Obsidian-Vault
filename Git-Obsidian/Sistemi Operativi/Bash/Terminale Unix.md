## Uso del Terminale Unix
---
>[!info] Posizione logica dell'Utente
>All'interno del terminale l'utente è situato logicamente all'interno di una directory
>- Solitamente dopo il login, l'utente si trova nella cartella del proprio profilo: `/home/username`

### Comandi per Muoversi Logicamente
`pwd`
- Comando utilizzato per sapere in *quale directory si trova logicamente l'utente*
- Visualizza sullo schermo il *percorso completo* da `/` fino alla directory in cui si trova in quel momento

`cd`
- Comando utilizzato per spostarsi logicamente in una diversa directory, specificata.
- `cd /home/documents`
- `./` -> indica la directory corrente nel percorso relativo
- `../` -> indica la directory padre nel percorso relativo

#### Esempio
![[attachements/Unix-Like_fileSystem.png|450]]
> Supponendo che siamo nella directory: `mthomas`, per andare nella cartella `bin`:

```bash
cd ../../usr/bin

pwd

/usr/bin
```

`df`
- Comando che da delle informazioni su quali sono le partizioni utilizzate dal sistema linux
```bash
~ df
Filesystem      1K-blocks      Used Available Use% Mounted on
none              3983968         0   3983968   0% /usr/lib/modules/5.15.153.1-microsoft-standard-WSL2
none              3983968         4   3983964   1% /mnt/wsl
drivers         999143420 115606904 883536516  12% /usr/lib/wsl/drivers
/dev/sdc       1055762868   3062676 998996720   1% /
none              3983968        84   3983884   1% /mnt/wslg
none              3983968         0   3983968   0% /usr/lib/wsl/lib
rootfs            3980552      2208   3978344   1% /init
none              3983968       792   3983176   1% /run
none              3983968         0   3983968   0% /run/lock
none              3983968         0   3983968   0% /run/shm
tmpfs                4096         0      4096   0% /sys/fs/cgroup
```

### FSH
>Filesystem Hierarchy Standard

>[!tldr] Convenzione usata per il layout dei sistemi Unix-Like
> Definisce una ***struttura delle directory*** *standard* per sistemi operativi unix-like

*Obbiettivo*
- Sapere dove siano posizionati files/directory e quale sia il loro utilizzo
- Vengono specificate un numero minimo di directory

Directory richieste sotto `/`:

```bash
bin   # Essential command binaries
boot  # Static files of the boot loader
dev   # Device files
etc   # Host-specific system configuration
lib   # Essential shared libraries and kernel modules
media # Mount point for removeable media
mnt   # Mount point for mounting a filesystem temporarily
opt   # Add-on application software packages
sbin  # Essential system binaries
srv   # Data for services provided by this system
tmp   # Temporary files
usr   # Secondary hierarchy
```

### Caratteri Speciali
>[!attention] Esistono una serie di caratteri che la bash interpreta e in presenza di questi caratteri la bash fa delle operazioni speciali

```bash
> >> <     # redirezione I/O
|          # pipe
* ? […]    # wildcards
`command`  # command substitution (back tick)
;          # esecuzione sequenziale
|| &&      # esecuzione condizionale
(…)        # raggruppamento comandi
&          # esecuzione in background
" " ’ ’    # quoting
#          # commento (tranne un caso speciale)
$          # espansione di variabile
\          # carattere di escape *
<<         # “here document”
```

### Espansioni
>[!info] Espansioni di comando
>La bash fa una ***sequenza di operazioni*** secondo un preciso ordine
> Cerca di interpretare il contenuto del comando scritto facendo delle "***espansioni***"
>>[!caution] Procedimento
>> La `bash` prende il comando originale
>> - Applica la prima espansione che cambia il contenuto del comando iniziale, modificandolo
>> - Poi cerca di applicare la seconda espansione al comando modificato

>[!done] In Breve
>La `bash` applica una ***successione di trasformazioni*** della riga di comando e alla fine esegue il comando modificato

> Sequenza di espansioni in ordine
```bash
history expansion 
brace expansion 
tilde expansion 
parameter and variable expansion
arithmetic expansion 
command substitution (effettuata da sinistra verso destra) 
word splitting 
pathname expansion 
quote removal
```

 Le operazioni vengono fatte in questo ordine
 - ***Non*** è detto che ***tutte le espansioni*** vengano eseguite