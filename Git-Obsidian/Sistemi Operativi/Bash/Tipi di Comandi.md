## Comandi Eseguibili
---
>[!info] Tipologie di comandi Eseguibili
>Usando l'interfaccia utente a linea di comando, possono essere eseguiti:
>>[!summary] Comandi Built-In
>>Implementati e inclusi nella `shell` stessa
>
>>[!example] File binari e Eseguibili
>>***File*** che contengono *codice macchina* e si trovano nel ***file system***
>
>>[!tip] Script
>>***File*** di testo che contengono una *sequenza* di nomi di ***comandi*** binari e altri ***script***

Per essere ***eseguito*** un file binario o uno script deve avere i [[Utenti e Permessi#Permessi dei File|permessi]] di esecuzione
- È possibile modificare i permessi di un file o script tramite il ***comando*** `chmod`

## Tipologie di Comando
---
>[!info] Comandi
>I ***Comandi propriamente detti*** sono ordini la cui *implementazione* è ***contenuta*** nel file eseguibile della ***shell*** stessa
>- Anche detti "*built-in commands*"
> 
>>[!warning] Non si trovano come file separati nel file system
>
>Sono ordini che diamo all'interprete di comandi e che l'interprete ***esegue***, senza cercare sul disco un eseguibile corrispondente al nome che noi abbiamo dato come ordine
>>[!done] Servizi
>>Sono nomi di servizi che sono ***implementati dall'interprete stesso***
>
>Es: comando `cd` non esiste l'eseguibile del comando, il comando è implementato direttamente all'interno dell'interprete

>[!tldr] Eseguibili
> *Ordini* la cui implementazione è ***contenuta fuori dalla shell***
> Memorizzata in altri file nel *file system*
> >[!cautiom] Ricerca
>> Sono dei file con il nome che digitiamo da tastiera che troviamo su disco
>> - L'*interprete* quando vede che il comando ***non è implementato internamente***, va a cercare l'eseguibile su disco

#### Differenza fondamentale
Un comando è ***sempre presente***, sa sempre come *eseguire* il comando

Un ***eseguibile*** nel file sistem ***non è detto*** che l'interprete sappia come ***rintracciare*** l'eseguibile
- Bisogna mettere l'interprete nelle condizione di ***saper rintracciare*** l'eseguibile

## Liste di Comandi
---
>[!definizione] Definizione
>Una ***lista di Comandi*** è un elenco di comandi da lanciare in esecuzione in *successione*
>Sintatticamente, ciascun elemento dell'elenco deve essere **separato** dal successivo da un `;`

>Ciascun elemento dell'elenco può essere:
- *Comando Semplice*
- Espressione valutata *Aritmeticamente*
- Sequenza di Comandi *connessi da Pipe* (`|`)
- Sequenza di comandi *condizionali*
- *Raggruppamento* di comandi
- Espressione *condizionale*

### Comandi Composti
>[!info] Controllo di Flusso
>`for [condition]; do [command]; done`
>`while [condition]; do [command]; done`
>`if [condition]; then [command]; elif [command]; else[command]; fi`

### Sequenza di Comandi Condizionali
>Sequenze di comandi **non** condizionali
- Sono comandi separati dal `;`, i comandi sono eseguiti in *successione*

>[!definizione] Definizione
>Sono sequenze di comandi che vengono eseguite *secondo delle condizioni*
>>[!abstract] Caratteri
>>`||` Viene utilizzato per eseguire due comandi in sequenza
>>- Il secondo viene eseguito solo se il primo termina con un [[Exit Status|exit code]] diverso da $0$ (***fail***)
>>
>>`&&` Viene utilizzato per eseguire due comandi in sequenza
>>- Il secondo viene eseguito solo se il primo termina con un [[Exit Status|exit code]] uguale a $0$ (***success***)

>[!info] Raggrupamento Tramite `()`
>Se si ***racchiude*** una *sequenza di comandi* tra parentesi tonde
>- In esecuzione viene creata una `subshell` per eseguire quella sequenza di comandi

In un certo senso "***raggruppo***" anche quello che viene mandato nello `stdout`
