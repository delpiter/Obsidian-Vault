>[!info] Circuito Bistabile
>Un ***circuito bistabile*** è un circuito in grado di mantenersi in *posizione di stabilità* in ***due differenti stati***
>Il ***cambio di stato*** è provocato da un particolare *segnale o impulso*
>- A seguito dell'impulso il circuito si ***mantiene nello stato raggiunto*** a meno che non vengano inviati ulteriori *segnali/impulsi*
## Latch
---
>*Tramite due semplici porte [[Logica Digitale#NOR|NOR]] è possibile realizzare un circuito bistabile denominato* ***latch SR***

![[attachements/LatchSR.png]]

>[!warning] Differenze da circuito Combinatorio
>A differenza dal ***circuito combinatorio***, il ***Latch SR***, o altri circuiti sequenziali in generale, l'*output* non è determinato univocamente dai valori in input
>- Come si può notare, stessi valori in *input*, diversi valori in *output*

- L'*input* $S$ (**set**) è utilizzato per impostare lo stato a $1$
- L'*input* $R$ (**reset**) è utilizzato per impostare lo stato a $0$
- $Q$ è l'*output* (**state**), mentre $\overline{Q}$ è il suo *complemento*

>[!abstract] Situazione di normalità
>Quando $S$ e $R$ sono $0$, il circuito conserva lo stato, infatti:
>- $Q$ vale $0$ (**stato stabile $0$**), la porta `NOR` superiore continua ad avere *output* $1$ e quella inferiore *output* $0$
>- $Q$ vale $1$ (**stato stabile $1$**), la porta `NOR` superiore continua ad avere *output* $0$ e quella inferiore *output* $1$

>[!done] In Definitiva
>Un ***latch SR*** ricorda, fino a che è alimentato elettricamente, qual è stato l'ultimo valore impostato e pertanto può essere utilizzato come elemento di base per la realizzazione di memorie [[../Architettura del Calcolatore/Organizzazione della Memoria#Memoria Principale|RAM]] 

Nei circuiti più complessi, il *latch* è rappresentato nel modo seguente
![[attachements/Latch-Circuit-Symbol.png]]
*Rispettivamente: Latch attivato con **clock alto** e latch attivato con* ***clock basso***
### Set
>[!info] `SET` *state*
>Se nel *Latch* **stato** $0$, $S$ diventa $1$, gli *input* della porta superiore sono $1$ e $0$ e quindi l'*output* $\overline{Q}=0$
>Non appena tale *output* si propaga sull'*input* della porta inferiore, questa viene ad avere entrambi gli *input* a $0$, e quindi $Q$ diventa $1$
>>[!done] Il *Latch* è passato allo stato $1$
>
>>[!fail] Latch *stato* $1$
>>Se invece il *Latch* era in stato $1$ e $S$ diventa $1$, non succede *nulla*, poiché l'*input* che viene dalla porta inferiore è impostato a $1$


### Reset
>[!info] `RESET` *state*
>Se nel *Latch* **stato** $1$, $R$ diventa $1$, gli *input* della porta inferiore sono $1$ e $0$ e quindi l'*output* $Q=0$
>Non appena tale *output* si propaga sull'*input* della porta inferiore, questa viene ad avere entrambi gli *input* a $0$, e quindi $\overline{Q}$ diventa $1$
>>[!done] Il *Latch* è passato allo stato $0$
>
>>[!fail] Latch *stato* $0$
>>Se invece il *Latch* era in stato $0$ e $R$ diventa $1$, non succede *nulla*, poiché l'*input* che viene dalla porta superiore è impostato a $1$

### Stati da Evitare

>[!question] Cosa succede quando $S=R=1$?

Questa situazione il cui output è *indeterminato*, ***dovrebbe essere evitata***
- La figura mostra un ***Latch di tipo D sincronizzato*** che risolve il problema di avere $S$ e $R$ contemporaneamente a $1$
- Il circuito ha un *input* (**trigger**) che permette di ***sincronizzare*** la scrittura con un evento

![[attachements/Sync-Latch.png]]
*Impostare $D$ a $1$ esegue un `SET`, mentre impostare $D$ a $0$ esegue un `RESET`*
## Flip-Flop
---
>[!info] ‎ 
>Un ***flip-flop*** è un circuito molto simile a un [[#Latch]], tanto che spesso i due termini vengono *scambiati*
>L'unica differenza è relativa all'istante in cui il segnale di clock ***determina il cambiamento di stato***
>>[!done] Nel *Flip-Flop*
>>Il cambiamento di stato è determinato dal ***fronte*** (*discesa/salita*) del **clock**
>
>>[!fail] Nel *Latch*
>>Il cambiamento di stato è determinato dal ***livello*** (*alto/basso*) del **clock**

Nei circuiti più complessi, il *flip-flop* è rappresentato nel modo seguente
![[attachements/Flip-Flop-Circuit-Symbol.png]]
*Rispettivamente: flip-flop attivato con **clock alto** e flip-flop attivato con* ***clock basso***

## Tipi di Memoria con Circuiti Sequenziali
---
>*Come mostrato in tabella esistono diversi tipi di memoria, di cui le più comuni sono: [[../Architettura del Calcolatore/Organizzazione della Memoria#Memoria Principale|RAM]] e `ROM`*

![[attachements/Sequential Memories.png]]