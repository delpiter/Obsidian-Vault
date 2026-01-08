>[!definizione] Definizione
>Il ***multiplexing*** è il meccanismo per cui più *canali trasmissivi in ingresso* condividono lo stesso [[Git-Obsidian/Reti/Introduzione/Introduzione#Canale|canale]] per trasferire più flussi di informazione in **un solo segnale** (detto _multiplato_).

Più canali sono trasportati dallo stesso ***mezzo di trasmissione***.

Si può realizzare utilizzando:
- ***Tempo*** (***T***ime ***D***ivision ***M***ultiplexing)
- ***Frequenza*** (***F***requency ***D***ivision ***M***ultiplexing)
- ***Codice*** (***C***ode ***D***ivision ***M***ultiplexing)
- ***Spazio*** (***S***pace ***D***ivision ***M***ultiplexing)

>[!hint] Efficienza
>Dal punto di vista ***teorico*** queste modalità sono *equivalenti*

### Time Division Multiplexing
>[!info] Definizione
>Il ***TDM*** è una ***tecnica di multiplexing*** di un canale di comunicazione secondo la quale ogni dispositivo *ottiene a turno* l'uso esclusivo del canale

#### TDM Slotted/Unslotted

>[!note] TDM Unslotted
>Nel *Time Division Multiplexing* di tipo ***Unslotted***, l'asse dei tempi *non* è suddiviso a priori.
>Si possono adottare unità informative di *lunghezza variabile*.
>- È necessario un ***sistema esplicito di delimitazione*** delle unità informative

![[TDMUnslotted.png]]

>[!example] TDM Slotted
>Nel *Time Division Multiplexing* di tipo ***Slotted***, l'asse dei tempi è *suddiviso* in intervalli di durata prefissata (**slot**)
>- Le *unità informative* hanno tutte la **stessa lunghezza** commisurata al singolo ***slot***

![[TDMSlotted.png]]

##### Framed/Unframed
>[!caution] Framed
>I singoli *slot* vengono strutturati in un ***frame***.
>La **sincronizzazione** non è necessaria a livello di ogni singolo slot, ma viene fatta ad ogni *frame*

>[!todo] Unframed
>I singoli *slot* si susseguono ***senza una struttura predefinita***.
>- Occorre un sistema di sincronizzazione di *slot*

### Wavelength Division Multiplexing
>[!info] Concetto
>Il ***wavelength division multiplexing*** è una modalità di multiplazione di diversi flussi su diversi ambiti di *lunghezze d'onda*.

I flussi di dati diversi vengono trasmessi su [[Luce e Colori|colori]] ***diversi*** nella stessa [[Strato Fisico#Fibra Ottica|fibra]].
- Richiede **trasmettitori** e **ricevitori** **selettivi** ma permette un largo aumento della capacità della rete *senza installare nuove fibre*.

> `ROADM` (Reconfigurable Optical Add Drop Multiplexer)
- Apparato in grado di ***selezionare il colore della luce*** in modo comandato.

> `MEM` 
- Sposto la luce con piccoli specchi disposti a matrice (`MEMs` switch matrix).
## Assegnazione della Banda
---
### Assegnazione Statica
>[!definizione] Concetto
>Nella ***assegnazione statica*** la quantità di banda che viene riservata per una comunicazione è *fissa* durante l'intera durata della comunicazione.
>- La banda dedicata è espressa in **bit per secondo** (`bit/sec`).

Questo approccio è tipico quando le **risorse sono limitate** e devono essere ***gestite in modo rigoroso***

### Assegnazione Dinamica
>[!abstract] Concetto
>L'***assegnazione dinamica*** della banda è un approccio che contrasta con l'assegnazione statica e introduce *maggiore flessibilità* nella gestione delle risorse.
>- In un sistema con **assegnazione dinamica della banda**, la banda disponibile viene condivisa tra i flussi in *base alla necessità*.
>
>>[!done] Cambiamento
>>La **banda** che un flusso può utilizzare ***non è fissa***, ma può *variare* durante la comunicazione

Un flusso che ha bisogno di più banda può richiedere una **porzione maggiore di banda**
- Se un flusso non utilizza tutta la banda di cui *dispone*, altri flussi possono utilizzare quella porzione ***inattiva***.

>L'assegnazione ***dinamica della banda*** può essere effettuata sia nel caso *slotted* che *unslotted*