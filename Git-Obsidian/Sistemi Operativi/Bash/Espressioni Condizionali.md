>[!definizione] Definizione
>Le ***espressioni condizionali*** sono particolari comandi che valutano alcune condizioni e *restituiscono* un [[Exit Status]] di valore `0` per indicare la ***verità*** dell'espressioni o di valore diverso da `0` per indicarne la ***falsità***
>>[!note] Sintassi
>>Ciascuna espressione si scrive mettendo le condizioni da valutare tra doppie parentesi quadre
>>- `[[...]]`

>[!warning] Le condizioni che possono essere inserite sono condizioni apposite, ***NON*** possono essere comandi

Le condizioni possono essere composte mediante *operatori logici*:
- `!` not
- `&&` and
- `||` or

E mediante delle parentesi tonde pere stabilire l'*ordine di valutazione*

>[!hint] Espressioni Valutate
>La `bash` effettua solo le seguenti interpretazioni:
>- [[Variabili#Variable Expansion|Variable Expansion]]
>- [[Valutazioni Aritmetiche|Arithmetic Expansion]] con `$(())`
>- [[Command Substitution]]
>- Process Substitution
>- [[Command Substitution#Quoting di Stringhe|Quote Removal]]
>
>Ma solamente negli operandi
>- Non si possono fare operazioni sugli ***operatori***

Usando l’operatore `[[...]]` 
- Le espressioni condizionali *possono essere collegate* con gli operatori logici usati anche in C, quali `!` `&&` `||` e raggruppati con parentesi tonde

>[!warning] Spaziature
>È importante inserire le spaziature giuste prima e dopo ogni operatore dell'espressione:
>- `[[`, `]]`
>- `-x`


#### Cosa non si può fare
>[!fail] Non si possono generare operatori

>[!danger] Non si possono eseguire assegnamenti a variabili

>[!fail] Non si possono usare valutazioni aritmetiche come condizioni isolate

>[!danger] Una espressione condizionale non può contenere espressioni condizionali
## Operatori di Condizione
---
>Ci sono numerose operazioni disponibili tramite gli ***operatori di condizione***

>[!summary] Confronti Aritmetici
>Specificando gli operatori opportuni:
>- `-eq -ne -le -lt -ge -gt`
>
>Questi operatori corrispondono a:
>- $=$, $\neq$, $\leq$, $<$, $\geq$ e $>$   

#### Operatori sulle Stringhe
>[!abstract] Condizioni su Stringhe
>Usando ***operatori di confronto*** *lessicografico* tra stringhe
>- `== = != < <= >= > `
>
>È possibile verificare se delle stringhe sono vuote
>- `-z -n`
- `-z [string]` returns ***True*** if *length of string* is $0$
- `-n [string]` returns ***True*** if *length of string* is not $0$
- `[string1] == [string2]` returns ***True*** if the strings are *equal*
- `[string1] != [string2]` returns ***True*** if the strings are *not equal*
- `[string1] < [string2]` returns ***True*** if `string1` *sorts* before `string2` *lexicographically*
- `[string1] > [string2]` returns ***True*** if `string1` *sorts* after `string2` *lexicographically*
#### Operatori sui File
>[!tl;dr] Condizioni sui file
>Usando gli operatori:
>- `-d -e -f -h -r -s -t -w -x -O -G -L`
>
>Confronto di date di ultima modifica di *files*
>- `-nt -ot`
>
>>[!note] Nota Bene
>>Ne esistono altre

- `-d [file]` returns ***True*** if file *exists* and is a *directory*
- `-e [file]` returns ***True*** if file *exists*
- `-f [file]` returns ***True*** if file *exists* and is a *regular file*
- `-h [file]` returns ***True*** if file *exists* and is a *symbolic link*
- `-r [file]` returns ***True*** if file *exists* and is *readable*
- `-s [file]` returns ***True*** if file *exists* and has a *size* greater than $0$
- `-t [fd]` returns ***True*** if file *descriptor* `fd` is *open* and refers to a terminal
- `-w [file]` returns ***True*** if file *exists* and is *writable*
- `-x [file]` returns ***True*** if file *exists* and is *executable*
- `-O [file]` returns ***True*** if file *exists* and is *owned* by the [[Utenti e Permessi#Utenti e Gruppi|effective user]] id
- `-G [file]` returns ***True*** if file *exists* and is *owned* by the *effective group* id
- `-L [file]` returns ***True*** if file *exists* and is a *symbolic link* (deprecated, see -h)
- `[file1] -nt [file2]` True if `file1` is *newer* (last modification date) than `file2`, or if `file1` *exists* and `file2` *does not*
- `[file1] -ot [file2]` True if `file1` is *older* than `file2`, or if `file2` *exists* and `file1` *does not*

