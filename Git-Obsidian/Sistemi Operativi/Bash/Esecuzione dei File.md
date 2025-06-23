## Come Eseguire da Terminale a Linea di Comando
---
> I comandi *built-in* possono essere eseguiti semplicemente *invocandone il nome*

> I file eseguibili (***binari o script***) devono essere invocati specificando il percorso in 3 modalità:

>[!abstract] Percorso Assoluto
>Il *percorso* a partire dalla **root**
>- `/home/pinacoteca/file.exe`

>[!caution] Percorso Relativo
>Il *percorso* a partire dalla **directory corrente**

>[!example] Specificando solo il Nome
>A condizione che il file sia contenuto in una directory specificata nella variabile `PATH`

##### Esempio Esecuzione
```bash
wich echo # /usr/bin/echo

echo ciao
ciao

# Alternativa
/usr/bin/echo ciao
ciao
```

## Subshell
---
>[!info] Definizione
>Una *subshell* è una `shell` ("***shell*** figlia") creata da un'altra `shell` ("***shell*** padre")

Le **subshell** ereditano una *copia* di tutte le *variabili d'ambiente* e i *file aperti*
- **NON** eredita le variabili locali del padre

Per l'*esecuzione* dello script, in ogni caso [[#Comando `source`|(*)]] viene **creato un nuovo processo figlio** (una nuova `shell`)
 - Lo *script* viene ***quasi*** sempre [[#Comando `source`|(*)]] eseguito dal *processo figlio*
 - Quando il processo figlio inizia l'esecuzione, il *processo padre ferma la propria esecuzione*
	 - Si mette in **attesa** che il processo figlio finisca
 - Quando il processo figlio *termina*, il padre **riprende il controllo**
	 - I processi figli sono in grado di *restituire un valore intero* che indica se l'esecuzione dello script è andata a buon fine o meno
- Al termine dell'esecuzione l'ambiente "figlio" viene ***eliminato dalla memoria***

##### Variabile e Esecuzione
>Il comando:`var="string" command`

Crea la *variabile* all'interno della nuova `shell` che esegue lo **script** `command`
- La variabile creata [[Variabili#Le Variabili|d'ambiente]]
- Se la variabile `var` *esiste già* nella shell corrente, **non viene sovra scritta**, viene invece creata una nuova variabile, che non tocca quella del padre

### Esecuzione di uno Script
>[!question] Qual è l'*interprete* che deve essere usato per eseguire lo script?

>Quando una `shell` deve eseguire uno script, deve fare un controllo sulla ***prima riga*** di comando dello *script*

- Indica quale *interprete* di comandi utilizzare
	- Se voglio eseguire uno ***script*** in un *linguaggio diverso* è necessario specificare il *percorso* dell'interprete che si intende utilizzare

La prima riga dello script sarà di questo tipo:
> `#!/bin/bash`

- Se la riga non è presente, viene utilizzato lo *stesso interprete* in **esecuzione** sul momento

##### Attenzione!
```bash
#!/usr/bin/perl

echo stuff
ls -al ./
```

>[!quote] Ghini
>>[!fail] Errore:
>>_stronzo mi stai parlando in tedesco, che sono finlandese_


### Comando `source`
>Una shell può eseguire uno script attraverso il comando `source` o `.`

Scrivendo `source scriptname` o `. scriptname`
- Lo script viene *eseguito* dalla `shell` su cui è stato scritto il comando

>[!question] A cosa serve?

Serve principalmente a *modificare i valori delle variabili* della `shell` mediante uno **script**
- Ricorda
	- Lanciando normalmente uno **script**, modificare le variabili nello script **NON modifica** le variabili della `shell` ***chiamante***

Con il comando `source` **NON** viene considerata la prima riga:
- `#!/usr/bin/perl`, che indica l'*interprete* da usare per quello script
- Di conseguenza lo script darà errore, se lo script utilizza un linguaggio diverso dall'interprete in utilizzo
##### Permessi
>[!warning] Per eseguire uno script con il comando `source` non è necessario avere i permessi di esecuzione

Il comando `source`, infatti, non esegue direttamente l'eseguibile
- *Legge* e *esegue* una riga alla volta, le operazione all'interno dello script
	- ***Potenzialmente pericoloso***

### Passaggio di argomenti ad un eseguibile
> `chmod u+x /home/pinacoteca/example.exe`

La prima parola: `chmod` è il nome dell'***eseguibile*** o *argomento* di *indice* $0$

Ciascuno degli altri pezzi è un ***argomento o parametro***
- La sequenza di caratteri `u+x` è l'*argomento* di *indice* $1$
- La sequenza di caratteri `/home/pinacoteca/example.exe` è l'*argomento* di *indice* $2$

>[!done] Si dice che in questo caso il numero di argomenti passati è $2$

### Comando `exit`
>Il comando `exit #`

- Chiude la `shell` corrente
- Consente di *ritornare* un valore dalla chiusura dello *script*
	- Si inserisce tale valore al posto del `#`
