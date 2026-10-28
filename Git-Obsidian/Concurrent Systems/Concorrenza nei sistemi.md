## Tassonomia
---
> Esistono due tipologie di sistemi concorrenti che interagiscono con l'ambiente:


> [!failure] Reactive Systems
> Un ***reactive system*** è un sistema che esegue reagendo agli stimoli dall'ambiente.

Le interazioni sono *asincrone* e la non terminazione del programma potrebbe essere una feature voluta.

> [!abstract] Transformational Systems
> Un ***transformational system*** è un sistema puramente funzionale e sincrono.

Formalizzabile come una *macchina di Turing*.

### L'hyper-cubo della programmazione concorrente
> La tassonomia della *programmazione concorrente* può essere modellata attraverso uno spazio multidimensionale dove vengono allocati i vari approcci.

> [!caution] Control Flow Model
> Sincrono vs Asincrono

> [!help] Shared Memory e Message Passing
> - Asynchronous Message Passing: Actor Programming
> - Synchronous/Channel based message passing


> [!info] Distribuito e Non Distribuito
> 


> [!tl;dr] Control oriented e data oriented
> Reactive Programming (*Data oriented*)

> Esempio di reactive programming

$$
\begin{aligned}
x \leftarrow 1 \\
y\leftarrow x + 1 \\
x \leftarrow 2
\end{aligned}
$$
- In un sistema *control oriented* il valore di $y$ alla fine dell'esecuzione sarà $2$.
- Nel *reactive programming* $y$ avrà il valore $3$.

## Interazione tra processi
---
> Qualsiasi programma concorrente non banale si basa su più processi che devono ***interagire*** in qualche modo.

### Cooperazione
> [!abstract] Definizione  
> La cooperazione si riferisce alle interazioni che sono sia **previste** (_expected_) che **volute** (_wanted_).

Esistono due tipologie di cooperazione:
- Comunicazione
- Sincronizzazione

Sincronizzazione e comunicazione sono due tipologie diverse di meccanismi collegati a due modelli architetturali diversi per macchine concorrenti:
- Modello a ***memoria condivisa***
- Modello ***message passing***
#### Comunicazione
> Si occupa della necessità di realizzare un flusso di informazioni tra processi, tipicamente realizzato in termini di messaggi.

> [!tip] Differenze con OOP  
> In ***OOP*** la chiamata a un metodo non è solo comunicazione tra classi: viene trasferito anche il **controllo dell'esecuzione**.

#### Sincronizzazione
> Si occupa della ***definizione esplicita*** di una *relazione temporale* o di dipendenze tra processi e tra azioni di processi distinti.

### Competizione
> [!abstract] Definizione  
> La competizione si riferisce alle interazioni che sono **previste** e **necessarie**, ma **non volute**.

Tipicamente si occupa di *coordinare l'accesso* di più processi alle **risorse condivise**.

> [!example] Esempio  
> 

_Lock_ e _Unlock_ sono interazioni che dobbiamo *necessariamente implementare* ma che **non sono volute**, poiché ***serializzano l'esecuzione***, diminuendo lo speedup.

Due problemi principali:
> [[../Sistemi Operativi/Teoria/9 - Condivisione di Risorse#Mutua Esclusione|Mutua esclusione]]
- Regolare l'accesso alle risorse condivise da parte di processi distinti.

> [[../Sistemi Operativi/Teoria/10 - Sezioni Critiche|Sezioni critiche]]
- Regolare l'esecuzione concorrente di blocchi di azioni di processi distinti.

### Sincronizzazione vs Mutua esclusione
> Sono concetti **diversi**, anche se in **relazione** tra loro.

> [!caution] Sincronizzazione  
> Definisce una **relazione temporale** tra processi

Mantenere relazioni temporali, il che include:
- azioni che avvengono nello **stesso momento**
- azioni che avvengono con la **stessa velocità relativa**
- o semplicemente un'azione che **deve avvenire prima di un'altra**.

> [!important] Mutua esclusione  
> Definisce una **restrizione all'accesso** di informazioni condivise.

- È inutile se non c'è informazione condivisa.

### Interferenze e corse critiche
> [!abstract] Definizione  
> Si riferisce alle interazioni che **non sono né previste né volute**.

- Producono effetti negativi solo quando il rapporto tra le velocità dei processi assume valori specifici (**errori dipendenti dal tempo** o [[../Sistemi Operativi/Teoria/8 - Concorrenza#Race Condition|Race Condition]]).

### Situazioni critiche
#### Deadlock
>[!info] Definizione
>Una situazione di *Deadlock* (*stallo*) si verifica quando due o più processi *rimangono in attesa* di eventi che **non potranno mai verificarsi** a causa di condizioni cicliche nel ***possesso*** e nella ***richiesta*** di risorse.
>>[!question] Come sistemare un processo in stato di Deadlock?
>>Nei sistemi reali, se ne può uscire sono con metodi "**distruttivi**", ***terminando i processi***

![[attachements/Starvation&Deadlock.png]]

>Immagine $b$: Autisti in un incrocio
- **Nessuno da la precedenza** e finiscono tutti per bloccarsi

##### Condizioni per deadlock
>[!info] Mutua Esclusione
> Le *risorse* coinvolte devono essere ***seriali***

>[!example] Risorsa non Prerilasciabile
> Le risorse non possono essere ***prerilasciate***, devono essere lasciate *volontariamente*

>[!todo] Richieste bloccanti
> Le richieste di risorse devono essere ***bloccanti***

>[!definizione] Attesa Circolare
>Esiste una **sequenza di processi** $P_{0},P_{1},\dots,P_{n}$, tali per cui $P_{0}$ attende una risorsa *controllata* da $P_{1}$, $P_{1}$ attende una risorsa *controllata* da $P_{2}$, $\dots$, $P_{n}$ attende una risorsa *controllata* da $P_{0}$

La *presenza* di queste condizioni è ***necessaria e sufficiente***
- Devono valere tutte contemporaneamente affinché un *deadlock* si presenti nel sistema
#### Starvation
>[!info] Definizione
>Una situazione di *Starvation* (o *blocco individuale*) si verifica quando un processo *rimane in attesa* di un **evento che non accadrà mai**, e quindi non può portare a termine il proprio lavoro
>>[!note] Situazione di Uscita
>>A differenza del **deadlock**, non è una condizione definitiva, basta adottare un'opportuna politica di assegnamento
#### Livelock
> [!info] Definizione  
> Un ***livelock*** è simile a un *deadlock*, con l'unica differenza che gli stati dei processi coinvolti nel livelock **cambiano costantemente**, senza che alcuno proceda con l'esecuzione.
### Linguaggi e macchine concorrenti
> [!example] Linguaggio di programmazione concorrente  

Per **descrivere/specificare** un *programma concorrente* è necessario un **linguaggio di programmazione concorrente**.
- Deve permettere ai programmatori di scrivere programmi come insiemi di istruzioni da eseguire in modo concorrente.

> [!important] Macchina concorrente  

Per **eseguire un programma concorrente** serve una *macchina concorrente*: una macchina (che può essere anche astratta) progettata per gestire l'esecuzione di più processi sequenziali, sfruttando più processori (fisici o virtuali).

Una macchina concorrente fornisce il supporto per l'esecuzione di programmi concorrenti e forniscono il meccanismo di base per:
- la **multiprogrammazione**
	- Tramite *generazione* e *gestione* dei processi virtuali.
- Sincronizzazione e comunicazione
- Controllo degli accessi alle risorse.
