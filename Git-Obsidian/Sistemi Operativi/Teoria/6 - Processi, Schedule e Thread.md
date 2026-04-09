## Processi
---
>[!info] Definizione
>Un ***processo*** è una attività controllata da un programma che si svolge su un processore
>>[!note] Descrizione del Processo
>>Ad ogni istante un ***processo*** può essere interamente descritto dalle seguenti componenti
>>- La sua immagine nella *memoria*
>>- La sua immagine nel *processore*
>>- Il suo *stato di avanzamento*

>[!warning] Processo $\neq$ Programma

>Un programma è una entità statica
- È un *insieme di istruzioni*

>Un processo è una entità dinamica
- Rappresenta il modo in cui il programma viene *eseguito nel tempo*


>[!question] Qual è la manifestazione fisica di un processo?

- Il segmento di ***codice*** da eseguire
- I ***dati*** su cui operare
- Uno ***stack*** di lavoro per la gestione di chiamate di funzione, etc...
- Un ***insieme di attributi*** contente tutte le info necessarie per la gestione del processo stesso

>[!done] Questo insieme di attributi prende il nome di Process Control Block


![[attachements/ProcessInMemory.png|150]]
![[attachements/MemoryExample.png]]


- Ogni processo ha un ***descrittore associato***
- L'insieme dei descrittori è ***contenuto in una tabella***

>[!abstract] Divisione delle informazione nel descrittore
>1. Informazioni di ***identificazione di processo***
>2. Informazioni di ***stato del processo***
>3. Informazioni di ***controllo del processo***
#### Descrittori di processo
##### Informazione di identificazione di un processo
>[!info] Process ID
> Il ***process id*** è un identificatore di processo o `PID`

Può *essere*:

>[!abstract] Identificatore di processo
- Semplicemente un indice in una ***tabella di processi***
- Un ***numero progressivo***
- Molte tabelle usano il `PID` per ***identificare un elemento*** della tabella dei processi

>[!abstract] Identificatore di altri processi logicamente collegati al processo

- Identificatore del processo padre

>[!abstract] Identificatore dell'utente che ha richiesto l'esecuzione

##### Informazioni di stato del processo
> ***Registri generali*** del processore

> ***Registri speciali***, (program counter e registri di stato)

##### Informazioni di controllo del processo
>[!info] Informazioni di scheduling
>Indica lo stato del processo
>- ***In esecuzione - Pronto - In attesa***

***Gestione della memoria***
- Valori dei registri di base

***Informazioni di accounting***
- Tempo di esecuzione e trascorso dall'attivazione

***Informazioni relative alle risorse***

***Informazioni per interprocess communication***
- *Semafori*

## Scheduler
>[!abstract] Scheduler
>Lo ***scheduler*** è la componente più importante del [[3 - Livelli del Sistema Operativo#Kernel|kernel]]
>*Gestisce* quale processo deve essere in ***esecuzione*** ad ogni istante
>Interviene quando viene richiesta o termina un'operazione di `I/O`

>[!done] Precisione delle parole

##### Schedule
>Lo ***schedule*** è la sequenza temporale di assegnazioni delle risorse da gestire ai richiedenti

##### Scheduling
>Lo ***scheduling*** è l'azione di calcolare uno *schedule*

##### Scheduler
>Lo ***scheduler*** è la componente software che calcola lo *schedule*

#### Mode Switching e Context Switching
>Ogni volta che avviene un ***interrupt*** il processore è soggetto ad un [[4 - Livelli di Sicurezza#Cambio di Livello di privilegio|mode switching]]

Se lo *scheduler* decide di eseguire un altro processo il sistema è soggetto ad un ***context switching***
- Lo stato del ***processo attuale*** viene salvato nel `PCB` corrispondente
- Lo stato del ***processo selezionato*** per l'esecuzione viene caricato dal `PCB` nel processore

![[attachements/ContextSwitch.png]]

#### Stati dei Processi

>[!caution] Running
>Il Processo è in ***esecuzione***

>[!abstract] Waiting
>Il processo è in ***attesa*** di qualche ***evento esterno***

>[!done] Ready
>Il processo può ***essere eseguito***, ma attualmente il processore è ***impegnato in altre attività***

![[attachements/Process_States.png]]

##### Caratteristiche dei Processi
>Durante l'esecuzione di un processo, la `CPU` alterna periodi di

>[!info] `CPU` Burst
> I processi Caratterizzati da `CPU` *burst* lunghi si dicono `CPU` *bound*

>[!attention] `I/O` Burst
> I processi Caratterizzati da `I/O` *burst* lunghi si dicono `I/O` *bound*
##### Code dei Processi
>Tutte le volte che un processo entra nel sistema, viene inserito in una delle code gestite dallo [[#Scheduler]]

![[attachements/Code dei Processi.png]]![[attachements/CodeProcessi2.png]]

#### Gerarchia dei processi
>[!struttura]
>I [[#Processi]] sono organizzati in una *struttura gerarchica*
>- Quando un processo crea un nuovo processo: il creante viene detto *padre* e il creato viene detto *figlio*
>
>>[!done] Si viene a creare una struttura ad albero di processi

![[attachements/ProcessTreeStructure.png]]
### Thread
>[!info] Introduzione
>Tutti i [[3 - Livelli del Sistema Operativo#Introduzione|sistemi operativi]] odierni supportano l'esistenza di processi ***multithread***
>- In un **processo multithread** esistono molte *linee di controllo* ognuna delle quali è in grado di eseguire un insieme diverso di istruzioni

>[!Definizione]
>Un ***thread*** è l'unità di base di utilizzazione della `CPU`
>>[!example] Ogni *thread* possiede:
>>- La copia dello **stato del processore**
>>- Un proprio **program counter**
>>- Uno **stack**

> I thread appartenenti allo stesso processo condividono:
- Codice, dati e risorse `I/O`
![[attachements/Threads.png]]

>[!done] Thread: Pro
>I *thread* sono meno costosi in termini di:
>- **Creazione** di un novo thread in un processo
>- **Context Switching** fra thread

>Utilizzare i *thread* al posto dei *processi* rende l'implementazione più efficiente

#### Implementazione Thread
>Esistono due diverse implementazioni di *thread*: **User Thread** e **Kernel Thread**

>[!example] User Thread
>Gli *User Thread* vengono supportati ***sopra il kernel*** e sono implementati da una libreria a livello utente
>>[!info] Libreria
>>La *libreria* fornisce supporto per la **creazione**, **scheduling** e **gestione** dei thread senza l'intervento del kernel

>[!tldr] Kernel Thread
>I *Kernel Thread* vengono supportati direttamente dal ***sistema operativo***
>>[!info] Implementazione
>>**Creazione**, **scheduling** e **gestione** sono implementati a *livello kernel*

#### Modelli Multithreading
>Da queste [[#Implementazione Thread|due implementazioni]] sono stati creati tre modelli di multithreading

>[!abstract] Many-to-One
>Un certo numero di **user thread** vengono mappati su un unico **kernel thread**
>- Modello utilizzato da *sistemi operativi* che non supportano kernel thread multipli (nessuno)

![[attachements/Many-to-One.png]]

>[!note] One-to-One
>Ogni **user thread** viene mappato su un **kernel thread**
>- Soluzione *poco scalabile*

![[attachements/One-to-One.png]]

>[!cite] Many-to-Many
>Più **thread kernel** a cui associare più thread **livello user**

![[attachements/Many-to-Many.png]]
##### I Processi in Linux
>Di seguito alcune funzioni utilizzate per la gestione di un *programma multiprocessing*

>[!abstract] `fork()`
>La funzione `fork()` crea un processo *figlio* da un processo *padre*
>- Se la funzione ritorna un `PID` negativo, significa che la creazione ha dato errore
>- Se ritorna un `PID` $=0$, significa che la creazione è andata a buon fine ed è in **esecuzione il processo figlio**
>- Se ritorna un `PID` $>0$ , significa che la creazione è andata a buon fine ed è in **esecuzione il processo padre**

>[!note] `wait()`
>La funzione `wait()` lanciata dal *processo padre*, mette in attesa il processo fino alla fine dell'esecuzione del *processo figlio*

```c
int value = 5;

int main()
{
	pid_t pid;
	pid = fork(); // Returns 0 to the child process and the PID of the child to the parent process
	if(pid == 0)
	{/*if child process*/
		value += 15;
		printf("Child: value = %d\n",value);// value = 20
		return 0;
	}
	else if (pid > 0)
	{/*if parent process*/
		wait(NULL);
		printf("Parent : value = %d\n", value); // Value = 5
		return 0;
	}
}
```

###### Passaggio di valori tra processi: pipe

>La funzione `pipe()` crea una *pipe unidirezionale* di comunicazione che può essere utilizzata per il ***passaggio di dati fra processi***

La funzione chiede come argomento un **array** di *2 posizioni*
- `array[0]` -> estremità di **lettura** della pipe
- `array[1]` -> estremità di **scrittura** della pipe