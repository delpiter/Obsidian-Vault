>[!question] [[9 - Condivisione di Risorse#Azioni Atomiche|atomico]] come possiamo garantire la non-interferenza??

>Dobbiamo specificare che certe parti dei programmi devono essere eseguite in *modo atomico*

>[!info] Definizione
>La *sequenza di istruzioni* con la quale un processo **accede** e **modifica** un insieme di variabili *condivise* prende il nome di ***sezione critica*** (***critical section***).

> Obbiettivi
- Vogliamo ***garantire*** che le sezioni critiche siano eseguite in modo *mutualmente esclusivo*
- Vogliamo ***evitare*** situazione di blocco ([[../../Concurrent Systems/Concorrenza nei sistemi#Deadlock|deadlock]] o [[../../Concurrent Systems/Concorrenza nei sistemi#Starvation|starvation]])
 
>[!note] Assunzione
>Un processo può terminare solamente ***fuori dalla sua sezione critica***
#### Notazione
>[!example] Sintassi
>Per indicare una ***sezione critica*** si utilizzano le seguenti parole chiave
>- `[enter cs] <operations> [exit cs]`

>[!question] Perchè abbiamo bisogno di costrutti specifici?

> Il *sistema operativo* non può capire da solo cosa è una sezione critica e cosa non lo è

![[../../Concurrent Systems/Critical Section/Sezione Critica#Requisiti]]

#### Approcci
>[!todo] Approcci Software
>La *responsabilità* cade sui **processi** che vogliono accedere ad un oggetto distribuito 

>[!abstract] Approcci Hardware
>Si utilizzano *istruzioni speciali* del linguaggio macchina, progettate apposta
>- Molto efficienti
>
>>[!warning] Problema
>>Non sono adatti come soluzioni general-purpose

>[!tl;dr] Approcci basati su Supporto nel Sistema Operativo o nel Linguaggio
>La *responsabilità* di garantire la mutua esclusione ricade sul ***sistema operativo*** o sul ***linguaggio***

>Esempi
- Semafori
- Monitor
- Message Passing

### Busy-Waiting
>[!definizione] Busy-Waiting
>Il ***busy-waiting*** è una *tecnica di sincronizzazione* dei processi dove il processo *aspetta* e *controlla continuamente* per la verifica della condizione che ***permette l'avanzamento*** della sua esecuzione