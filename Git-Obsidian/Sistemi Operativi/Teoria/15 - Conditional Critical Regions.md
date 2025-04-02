## Regioni Critiche Condizionali
---
>[!definizione] Definizione
>Le ***regioni critiche condizionali*** sono costrutti che specificano *operazioni* su dati *condivisi* da eseguire in [[9 - Condivisione di Risorse#Mutua Esclusione|mutua esclusione]] 
>Possono determinare la *sospensione* e la *riattivazione* dei ***processi***

##### Sintassi
***Dichiarazione***
>`{c icon} resource name (var declarations)`

>[!info] `name`
>`name` è un'***identificatore*** per la risorsa *condivisa*

>[!abstract] `var declarations`
>È un insieme di ***variabili condivise***
>Dichiara che le variabili *racchiuse tra le parentesi* sono condivise e devono essere accedute in **mutua esclusione**

***Uso***
>`{c icon} region name when condition do statement`
>`{c icon} region name do statement`

>[!question] `condition`
>È una condizione *booleana*

>[!cite] `statement`
>È uno ***statement*** potenzialmente *composto* da eseguire
>È l'istruzione per acquisire la **mutua esclusione** su `name`

##### Esecuzione
>[!info] Concetto
>L'esecuzione consiste in:
>1. Acquisire la **mutua esclusione**
>2. Valutare la *condizione*
>3. Se è *falsa*, lasciare la **mutua esclusione** e attendere fino a quanto non è *vera*
>4. Se è *vera* eseguire lo `statement`

#### Implementazione tramite semafori

```cpp title:"resource name (var declaration)"
/* Mutual exclusion semaphore, one for each critical region */
Semaphore mutex_name = new Semaphore(1); 

/* Processes for which the condition is false must be suspended */ 
Semaphore suspended_name = new Semaphore(0);

/* Number of suspended processes */
int nsuspended_name = 0;

/* Additional declarations */
var declarations
```

```cpp title:"region name when condition do statement"
mutex_name.P();
while (!condition) {
/* condition is false */ 
	nsuspended_name++;
	mutex_name.V();
	suspended_name.P(); 
	/* when process is reactived, it must re-gain access to the mutual exclusion */ 
	mutex_name.P();
} 
	/* condition is true */ 
	statement; 
	/* after statement, one or more conditions may be true */ 
while (nsuspended_name-- > 0) 
suspended_name.V();
```

>[!warning] Soluzione molto inefficiente
>I *processi* possono essere ***riattivati ripetutamente*** prima di trovare la condizione *vera*

>[!done] Vantaggi
>Più ***facile*** da realizzare qualora le condizioni siano *complesse* e coinvolgono ***variabili locali***

