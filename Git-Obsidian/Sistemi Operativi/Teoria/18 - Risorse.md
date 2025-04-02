>Un *sistema di elaborazione* è composto da un insieme di ***risorse*** da assegnare ai processi

I **processi** competono nell'accesso alle ***risorse***
- Effettuando delle *richieste* per ottenere l'assegnazione di quanto 
necessario per poter evolvere

>[!example] Alcuni esempi di Risorse
>- Memoria
>- Processore
>- Dischi
>- Interfacce di rete

## Risorsa
 >[!definizione] Definizione
 >Ogni *componente* riusabile o meno, sia *hardware* sia *software* necessario al processo o al sistema si chiama ***risorsa***

#### Definizioni
>Le risorse possono essere suddivise in ***classi***
-  Risorse appartenenti alla *stessa classe* sono ***equivalenti***

>[!info] Istanza
>Le risorse di una classe vengono dette istanze della classe

>[!note] Molteplicità
>Il numero di risorse in una classe viene detto molteplicità del tipo di risorsa

![[ResourceClassification.png]]
>[!example] Esempio
> La `RAM` è la ***classe*** delle risorse e le singole celle sono le ***istanze*** della risorsa
> - La capacità totale di memoria è la ***molteplicità*** della risorsa

## Classificazioni
>In merito all’*interazione* tra **risorse** e **processi** possiamo effettuare una classificazione in base:
- Al ***tipo*** di richieste
- Alla modalità di ***assegnazione***
### Classificazione delle Richieste
>Quando un processo ***necessita di una risorsa*** generalmente **non** può richiedere una *particolare risorsa* ma solo una “*generica*” ***istanza*** di quella specifica classe.
#### Secondo il Numero

>[!info] Singola
>La ***richiesta singola*** è il caso normale.
>Si riferisce a una ***singola risorsa*** di una *classe* definita

>[!caution] Multipla
>Si riferisce a **una o più classi**, e per ogni classe, a **una o più risorse**
>La richiesta ***deve essere soddisfatta*** integralmente per poter eseguire il processo

#### Secondo il Tipo
>[!hint] Bloccante
>Il processo *richiedente* si *sospende* se non ottiene immediatamente l'assegnazione.
>La richiesta **rimane pendente** e viene riconsiderata dalla *funzione di gestione* ad ogni rilascio

>[!note] Non Bloccante
>La mancata *assegnazione* viene notificata al processo richiedente,
>***senza provocare la sospensione***

### Classificazione dell'Assegnazione
>[!summary] Statica
> Avviene al **momento della creazione del processo** e rimane valida *fino al termine*
> 
- Descrittore del processo

>[!abstract] Dinamica
> I processi ***richiedono*** le risorse durante la loro esecuzione e le usano una volta ottenute.
> Le rilasciano quando non più necessarie
- Periferiche di I/O

### Tipi di Risorse
#### Secondo la Mutua Esclusività
>[!info] Seriali
>È il caso di risorse che **non** possono essere assegnate a più processi *contemporaneamente*
>Anche dette: "*con accesso mutualmente esclusivo*"
>- Accetta solo richieste in "***serie***", uno alla volta

###### Esempi
- Processore 
- Stampanti

>[!caution] Non Seriali
> Sono le risorse che ***ammettono l'accesso contemporaneo*** di più  processi

###### Esempi
- File di sola lettura

#### Secondo la Modalità di Utilizzo
>[!note] Prerilasciabili
>Una *risorsa* si dice ***prerilasciabile*** o ***preemptive*** se la *funzione di gestione* può **sottrarla** ad un processo prima che questo l'abbia effettivamente rilasciata

Meccanismo:
- Il processo che subisce il ***prerilascio*** deve sospendersi
- La risorsa ***prerilasciata*** sarà successivamente *restituita* al processo

Una risorsa è ***prerilasciabile*** se:
- Il suo *stato* **non** si modifica durante l'utilizzo
- Il suo *stato* può essere facilmente ***salvato e ripristinato***

###### Esempio
- Processore

>[!tldr] Non Prerilasciabili
> La *funzione di gestione* **non** può sottrarre al processo le risorse che gli sono assegnate.
> Sono **non prerilasciabili** le risorse il cui stato ***non può essere salvato*** e ***ripristinato***

###### Esempi
- Stampanti
- Classi di Sezioni Critiche

## Deadlock
>Le risorse bloccate in [[9 - Condivisione di Risorse#Deadlock|Deadlock]] ***non*** possono essere utilizzate da altri processi
#### Condizioni per deadlock
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
## Grafo di Holt
>[!info] 
>Il ***Grafo di Holt*** è un *sistema di rappresentazione* mediante un [[I Grafi|grafo]] che permette di rappresentare tutte le situazioni in cui si possono venire a trovare i *processi* e le *richieste di risorse*
>>[!done] Grafo diretto e bipartito
>>Gli Archi hanno una ***direzione***.
>>I nodi sono ***suddivisi*** in due sottoinsiemi e non esistono archi che collegano nodi dello stesso sottoinsieme

##### Sottoinsiemi
>[!hint] Risorse
>Di forma *rettangolare*
>Le ***istanze*** sono come punti all'interno delle *classi di risorsa*

>[!example] Processi
>Di forma *rotonda*

>[!done] Significato Arco
>Gli archi *risorsa* $\to$ *processo*
>- Indicano che la **risorsa** è **assegnata** al processo
>
>Gli archi *processo*$\to$ *risorsa*
>- Indicano che il **processo** ha **richiesto** la risorsa

![[Pasted image 20250109114134.png]]
>[!note] Nota
> **Non si rappresentano** grafi di holt con archi relativi a richieste che possono essere soddisfatte

## Metodi di gestione dei Deadlock

###### Condizioni di Base per Deadlock
>[!warning] Se le risorse sono ad accesso ***mutualmente esclusivo***, ***seriali*** e ***non prerilasciabili***

^8b5cc1

### Deadlock Detection and Recovery
>[!info] Deadlock Detection and Recovery
>Permette al sistema di **entrare in stati di deadlock**
>Si utilizza un *algoritmo* per ***rilevare*** questo stato ed eventualmente eseguire un'azione di ***recovery***

#### Detection
##### Caso 1 una risorsa per Classe

>[!teor] Teorema
>![[#^8b5cc1]]
><u>Allora</u>
>Lo stato è di deadlock **se e solo se** il *grafo di Holt* contiene un [[I Grafi#^e45e8d|ciclo]]
###### Dimostrazione
>Si utilizza una *variante* del grafo di Holt: ***grafo Wait-For***

- Si ottiene un grafo wait-for *eliminando* i nodi di tipo **risorsa** e collassando gli archi in maniera appropriata
- Il grafo di Holt contiene un *ciclo* ***se e solo se*** il grafo Wait-for contiene un *ciclo*
- Se il grafo wait-for contiene un ciclo, abbiamo ***attesa circolare***

![[CicloDeadlock.png]]
- *Un collasso appropriato sarebbe un ciclo fra il processo $t_{1}$ e $t_{2}$*
##### Caso 2 più risorse per Classe
La presenza di un *ciclo* nel caso di Holt ***non è sufficiente*** per avere deadlock
![[Deadlock2.png]]
- *Immagine a) Deadlock, Immagine b) No Deadlock*
##### Riducibilità di un grafo di Holt
>[!definizione] Definizione
>Un grafo di Holt si dice ***riducibile*** se esiste almeno un nodo processo con soli archi entranti
>
>>[!done] Riduzione
>>La riduzione consiste nell'***eliminare*** tutti gli archi di tale nodo e *riassegnare* le risorse agli altri processi
>>>[!question] Con quale logica?
>>>Eventualmente un **nodo** che utilizza una **risorsa** prima o poi la ***rilascerà***.

- Dalle immagini di prima (*grafo b)*), possiamo applicare le seguenti *riduzioni*:
![[HoltReduction.png]]
>[!teorema]
>![[#^8b5cc1]]
><u>Allora</u>
> Lo stato ***non*** è di *deadlock* ***se e solo se*** il grafo di Holt è *completamente riducibile*
> - ***Esiste*** una sequenza di passi di riduzione che elimina tutti gli archi del grafo
###### Esempio
>Consideriamo il seguente Grafo di Holt:

- $R_{1}\to$ Classe di Risorsa con 3 Istanze
- $R_{2}\to$ Classe di Risorsa con 2 Istanze
- $R_{3}\to$ Classe di Risorsa con 2 Istanze
- $R_{1,1}$ è assegnata al processo $t_{1}$
- $R_{1,2}$ è assegnata al processo $t_{2}$
- $R_{1,3}$ è assegnata al processo $t_{4}$
- $R_{2,1}$ è assegnata al processo $t_{4}$
- $R_{2,2}$ è assegnata al processo $t_{4}$
- $R_{3,1}$ è assegnata al processo $t_{3}$
- $R_{3,2}$ è assegnata al processo $t_{4}$
- Il processo $t_{3}$ richiede una risorsa $R_{1}$
- Il processo $t_{2}$ richiede una risorsa $R_{2}$
- Il processo $t_{4}$ richiede una risorsa $R_{3}$

>[!question] Questa, è una situazione di deadlock?

- Risposta: ***No***
>[!done] Si possono eseguire le seguenti riduzioni

![[EsDeadlock.png]]
![[EsDeadlock2.png]]

##### Knot
>[!definizione] Definizione
>Dato un nodo $n$, l'insieme dei nodi raggiungibili da $n$ viene detto *insieme di raggiungibilità* di $n$ e si scrive $R(n)$
>Un ***knot*** del grafo $G$ è il massimo sottoinsieme *non banale* di nodi $M$ tale che:
>$$\forall n \in M, R(n) =M$$
>>[!done] In altre Parole
>>Partendo da un *qualunque nodo* di $M$ si **possono** raggiungere tutti i nodi di $M$ e nessun nodo all'*infuori* di esso.

>[!Teorema]
>Dato un ***grafo di Holt*** con una sola richiesta sospesa per processo
>![[#^8b5cc1]]
><u>Allora</u>
>Il grafo rappresenta uno *stato di deadlock* ***se e solo se*** esiste un *knot*

### Recovery
>Il sistema deve essere continuamente monitorato per riconoscere le situazioni di ***stallo***, utilizzando i *grafi di Holt* e quando si individua un problema si ***interviene per eliminarlo***

La risoluzione delle situazioni indesiderate può avvenire in modo:
- *Manuale*
- *Automatica*
 
>[!info] Soluzione Manuale 
>È richiesto all'operatore di *intervenire* per risolvere la situazione a favore di uno dei processi in **modo da sbloccare il sistema**

>[!Abstract] Soluzione Automatica
>Il [[3 - Livelli del Sistema Operativo#^9f2787|sistema operativo]] è in grado di risolvere *automaticamente* lo ***stallo*** applicando *meccanismi opportuni*

#### Soluzioni
>Le soluzioni per entrambe le modalità sono:

>[!Example] Terminazione dei Processi
>È il modo ***più semplice e più drastico*** per risolvere la situazione di *Deadlock*
>- Si **forza** la *terminazione* di un processo alla volta, osservando se man mano viene risolto il *deadlock*

>[!hint] Prerilascio di una risorsa
>Viene forzato il ***prerilascio*** di una *risorsa* da parte di uno dei processi in *Deadlock* in modo che questa possa essere acquisita da un altro processo.
>>[!warning] Attenzione
>>Questa operazione ***non*** può essere effettuata per *tutti i tipi di risorse*

>[!tldr] Checkpoint / Rollback
>Viene fatto periodicamente il *salvataggio* su disco dello ***stato dei processi*** in determinati istanti ben definiti (***checkpoint***)
>In caso di *Deadlock*, si ripristina (***rollback***) uno o più processi ad uno *stato precedente*

##### Considerazioni
>[!info] Terminare processi può essere costoso
>**Uccidere** un processo che è in esecuzione da *parecchio tempo* significa perdere completamente tutto il lavoro da esso effettuato

>[!caution] Risorse in uno stato inconsistente
>Se un processo viene terminato nel mezzo di una [[10 - Sezioni Critiche|sezione critica]] si rischia di lasciare le risorse in uno ***stato inconsistente***

>[!abstract] Preemption
>Fare ***preemption*** *non* è sempre possibile in automatico e può richiedere **interventi manuali**

### Deadlock Prevention / Avoidance
>[!hint] Deadlock Prevention / Avoidance
>Si impedisce al sistema di entrare in uno stato di deadlock

#### Prevention
>[!info] Definizione
>Per evitare il *deadlock* si elimina una delle ***quattro condizioni*** del *deadlock*
>- Il deadlock viene *eliminato* ***strutturalmente***

##### Rimozione Mutua Esclusione
>[!done] Significato
>Permette la condivisione "*apparente*" delle risorse
>>[!example] Esempio
>>***Spool*** di stampa:
>>- Tutti i processi pensano che la stampa sia avvenuta, mentre in realtà le stampe sono state inserite in una coda

###### Spooling
>[!danger] Non sempre applicabile

##### Rimozione della Richiesta Bloccante
>[!abstract] Allocazione Totale
>È possibile richiedere che un **processo** richieda ***tutte le risorse*** all'inizio della computazione
>>[!warning] Problemi
>>Non sempre l'*insieme di richieste* è **noto** dall'inizio
>>Si riduce il ***parallelismo***

>[!warning] Problema
>Anche se un processo ha necessità di risorsa per poco tempo
>deve allocarla per tutta la propria esistenza
##### Rimozione della Assenza di Prerilascio
>[!tip] Attenzione
>Come detto prima:
>- Non sempre è possibile
>- Può richiedere interventi manuali

##### Rimozione della Attesa Circolare
>[!summary] Allocazione Gerarchica
>Alle *classi di risorse* vengono associati ***valori di priorità***
>Ad ogni istante un processo può allocare *solamente* **risorse** di ***priorità maggiore*** a quelle che già possiede
>- Se deve allocare una risorsa di ***priorità inferiore***, deve prima *rilasciare* tutte le risorse con ***priorità superiore o uguale***

>[!warning] Problemi
>L'indisponibilità di una risorsa ad alta priorità ritarda processi che già detengono risorse ad alta prirorità
#### Avoidance
>[!info] Definizione
>*Prima di assegnare* una risorsa ad un processo, si controlla se l'operazione può portare al ***pericolo di deadlock***
>- Nel caso, l'operazione ***viene ritardata***

[[18.1 - Algoritmo del Banchiere]]
### Ostrich Algorithm
>[!abstract] Algoritmo dello "Struzzo"
>***Ignorare il Problema***, cioè:
>- Ipotizzare che i *deadlock* non si possano ***mai verificare***
>
>Spesso è ***troppo costoso*** mettere in atto le precauzione e si preferisce ignorare il problema

