> Di seguito una serie di comandi da conoscere

>[!info] `pwd`
>Mostra directory di lavoro corrente

>[!abstract] `cd [directory_path]`
>Cambia la directory di lavoro corrente
>

>[!note] `mkdir [directory_path]`
>Crea una nuova directory nel percorso specificato

>[!fail] `rmdir [directory_path]`
>Elimina la directory specificata, se è vuota

>[!abstract] `ls -alh [path]` 
>Stampa informazioni su tutti i files contenuti nel percorso

>[!fail] `rm [file_path]`
>Elimina il file specificato

>[!tl;dr] `echo [character_sequence]`
>Visualizza in output la sequenza di caratteri specificata
>

>[!tl;dr] `cat [file_path]`
>Visualizza in output il contenuto del file specificato

>[!tl;dr] `tail -n [num] [file_path]` e `head -n [num] [file_path]`
>>[!info] `tail` Visualizza in output le ultime `num` righe del file
>
>>[!abstract] `head` Visualizza in output le prime `num` righe del file

>[!tl;dr] `tee [file_path]`
>Visualizza in output il contenuto dello `stdin` ma lo salva anche nel file specificato
>- "***Duplicazione dell'output***"

>[!hint] `grep string [file_name]`
>Cerca tra le righe di file quelle che contengono alcune parole
>- Stampa in `stdout` *solo* le righe che contengono la stringa `string`

>[!caution] `sed [transform] [file_name]`
>Il comando `sed` agisce sulle righe dei file specificati e opera una trasformazione
>- La *trasformazione* ha una sintassi specifica 

>[!warning] `cut [option] [file_name]`
>Stampa parti selezionate dal file
>>[!summary] `[option]` principali
>>- `cut -b n-`
>>	- Stampa il file togliendo da ogni riga i primi `n` caratteri
>>- `cut -b -n`
>>	- Stampa il file togliendo da ogni riga gli ultimi `n` caratteri
>>- `cut -b m-n` 
>>	- Stampa il file togliendo da ogni riga i primi `m` caratteri e gli ultimi `n`
>
>Ci possono essere più `option` *concatenate* da una `,`

> Gli ultimi ***7 comandi*** sono spesso *accorpati assieme*.

>[!todo] `env`
>Visualizza le variabili ed il loro valore


>[!question] `which [executable_file_name]`
>Visualizza il percorso in cui si trova (solo se nella variabile `PATH`) l’eseguibile

>[!summary] `exec`
>Utilizzato per l'***apertura***/***chiusura*** dei file [[Lettura da Standard Input#Apertura di un File|*]]

>[!abstract] `mv [file_path]`
>Sposta il file specificato in una nuova posizione

>[!tl;dr] `ps aux`
>Stampa informazioni sui processi in esecuzione
>


>[!tl;dr] `du [directory_path]`
>Visualizza l’occupazione del disco


>[!fail] `kill-9 [PID]`
>Elimina processo avente identificativo `PID`


>[!fail] `killall [process_name]` 
>Elimina tutti i processi con il nome `process_name`


>[!caution] `bg`
>Ripristina un job fermato e messo in sottofondo


>[!abstract] `fg`
>Porta il job più recente in primo piano

>Negli ultimi due comandi è possibile
- Identificare con un ***process identifier*** mettendo solo il numero del processo
- Identificare con un ***Job identifier*** mettendo il numero preceduto dal `%`


>[!tl;dr] `df`
>Mostra spazio libero dei filesystem montati


>[!note] `touch [file_path]` 
>Crea il file specificato se non esiste, oppure ne aggiorna data


>[!tl;dr] `more [file_path]`
>Mostra il file specificato un poco alla volta mostra


>[!cite] `man [command_name]`
>È il manuale, fornisce informazioni sul comando specificato

^617056


>[!caution] `find [path] [options] [expression]`
>Serve per cercare dei *files* in una cartella specificata da `[path]`
>>[!note] Parametri Comuni
>>`-iname [string]`
>>- Cerca ***tutti*** i file e directory con quel ***nome*** specifico (si possono usare [[Wildcards]])
>>
>>`-maxdepth [n]` / `-mindepth [n]`
>>- Cerca ***tutti*** i file e directory con una *profondità di ricerca* di al massimo/minimo `n`
>>
>>`-type [f/d]`
>>- Cerca ***solo file*** `f` o ***solo directory*** `d`
>>
>>`-exec`
>>- *Esegue* per ***ciascuno dei file*** che trova i comandi che seguono
>>	- Esempio: `find /usr/ -type f -exec head -n 1 '{}' \;`
>>	- Cerca tutti i file dentro la cartella `usr` e ne mostra la prima riga
>>	- `'{}'` contiene il ***nome del file*** trovato

>[!quote] `read [variable_name]`
>Legge input da standard input e lo inserisce nella variabile specificata


>[!abstract] `wc`
>Conta il numero di parole o di caratteri di un file


>[!done] `true`
>Restituisce exit status 0 (vero)


>[!error] `false`
>Restituisce exit status 1 (non vero)