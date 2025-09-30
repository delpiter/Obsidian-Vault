## Oggetti
---
>[!definizione]
>Gli ***oggetti*** sono elementi di base del paradigma e corrispondono a *entità* del dominio applicativo.
>Un ***oggetto*** è un *individuo* sostanziale che possiede un **identità**, e un insieme di proprietà, che ne rappresentano lo **stato** e il **comportamento**.

> ***Identità*** (***O***bject ***ID***entifier)
- Viene assegnata alla creazione, non può essere modificata ed è indipendente dallo stato dell'oggetto.

> ***Stato***
- Definito come l'*insieme dei valori assunti* a un certo istante da un insieme di attributi.

> ***Comportamento***
- Definito da un *insieme di operazioni*.

>[!warning] Attenzione
>Non c'è bisogno di aggiungere attributi "*ID*" aggiuntivi all'oggetto, poiché nel ***paradigma ad oggetti*** è già presente.

### Operazioni e Interfaccia
>[!info]
>Ogni operazione dichiarata da un oggetto specifica il ***nome dell'operazione***, gli oggetti che prende come ***parametri*** e il ***valore restituito***.
>- L'insieme di questi tre elementi è detto *signature*.

L'insieme di tutte le *signature* di un oggetto sono dette ***interfaccia*** dell'oggetto.
- Specifica l'insieme completo di tutte le richieste che possono essere inviate all'oggetto.

### Tipo di Dati Astratto
>[!example] Tipo Astratto
>Il ***tipo di dati astratto*** è una rappresentazione di un insieme di oggetti "*simili*", caratterizzato da una struttura per i dati e da un'**interfaccia** che definisce quali sono le operazioni associate agli oggetti, ovvero l'insieme dei servizi implementati.

Un *tipo* è *sottotipo* di un *supertipo* se la sua interfaccia contiene quella del *supertipo*.
- Un *sottotipo* eredita l'interfaccia del *supertipo*.
- L'interfaccia **non vincola l'implementazione** del servizio offerto.
- Oggetti con la stessa interfaccia possono avere ***implementazioni diverse***.

### Classe
>[!help] Class
>La ***classe*** fornisce una **realizzazione** di un tipo di dati astratto, specifica un'*implementazione* per i metodi a esso associati.
>>[!done] Un oggetto è sempre istanza di ***esattamente una classe***.

Tutti gli oggetti di una classe hanno gli stessi attributi e metodi.
Esistono due tipi di metodi:
- Quelli che ***restituiscono astrazioni*** significative sullo stato dell'oggetto.
- Quelli che ne ***alterano lo stato***.

### Incapsulamento
>[!tldr] Idea
>L'***incapsulamento*** protegge l'oggetto *nascondendo* lo **stato dei dati** e l'**implementazione** delle sue operazioni.

Un oggetto incapsula i dati (*attributi*) e le procedure (*operazioni*) che li possono modificare.

> Il ***principio di incapsulamento*** sancisce che gli attributi di un oggetto possono essere *letti* e *manipolati* **solo** attraverso l'interfaccia che l'oggetto stesso mette a disposizione.

- I dettagli di implementazione sono *privati*, manipolabli solo dai metodi della classe.
- L'accesso dall'esterno agli attributi avviene attraverso una ***ristretta interfaccia pubblica***.
- Un oggetto esegue una operazione quando riceve una richiesta (*messaggio*) da un oggetto "*client*".

>[!done] Pro

- Per l'utilizzo di una classe è sufficiente conoscere l'***interfaccia pubblica***.
- La *modifica dell'implementazione* di una classe **non** si ripercuote sull'applicazione, a patto che non venga alterata l'interfaccia.
- Fortemente ridotta la possibilità di commettere ***errori*** nella gestione dello stato degli oggetti.
- Il ***debugging*** delle applicazioni è velocizzato, l'incapsulamento rende più semplice identificare la *sorgente di un errore*.

### Operazioni
> Un ***metodo*** cattura l'implementazione di una operazione.

L'***operazione*** è la *signature* della funzione.

>[!tip] Classificazione
>> ***Costruttori***
> - Usati per *costruire* oggetti a partire da parametri di ingresso, restituendo l'***OID***.
>
>> ***Distruttori***
> - Per *cancellare* gli oggetti e eventuali altri oggetti collegati.
>
>> ***Accessori***
>- Per *restituire informazioni* sul contenuto degli oggetti (*proprietà derivate*).
>
>> ***Trasformatori***
>- Per *modificare lo stato* degli oggetti e di eventuali altri oggetti collegati.

I **metodi** possono essere:
- *Pubblici*
- *Privati*
- *Protetti*

### Ereditarietà
>[!definizione]
>Il meccanismo di ***ereditarietà*** permette di basare la *definizione* e *implementazione* di una classe su quelle di altre classi.

È possibile definire relazioni di **specializzazione**/**generalizzazione** tra classi.
- La classe generalizzata viene detta *superclasse*.
- La specializzante *sottoclasse*.

Date due classi $A$ e $B$ di cui $B$ è sottoclasse di $A$, esiste la relazione $B$ "***IS A***" $A$.

Ciascuna sottoclasse eredita la struttura e i comportamenti (*attributi*, *metodi* e *interfaccia*).
- È in grado di ***specializzare le caratteristiche*** ereditate e ***aggiungere caratteristiche specifiche*** non presenti.

#### Forme di Ereditarietà
> Ci sono diversi tipi derivati di *ereditarietà*

>[!summary] Ereditarietà Multipla
>Si parla di ***ereditarietà multipla*** quando una sottoclasse può essere *derivata contemporaneamente da più classi*.

>[!abstract] Gerarchie di Classi
>Una classe derivata può essere ulteriormente specializzata.
>Si vengono a formare delle ***gerarchie di classi***, strutturate come *alberi* (ereditarietà *singola*) o *reticoli* (ereditarietà *multipla*)

### Polimorfismo
>[!quote] Capacità di assumere forme molteplici
>Nel paradigma a oggetti il termine si usa per alludere alla possibilità di ***creare metodi con lo stesso nome ma implementazioni differenti***.

Tramite il meccanismo di *overload*, è possibile definire all'interno di una classe più metodi con lo stesso nome ma *signature* (insieme dei parametri) differenti.

>[!caution] Istanziamento Dinamico

Il polimorfismo, abbinato all'istanziamento dinamico, permette a ciascun oggetto di ***rispondere a uno stesso messaggio*** in modo appropriato a *seconda della classe da cui deriva*.

### Delegazione
> Utilizzata per gestire le ***associazioni*** tra classi.

>[!info]
>Si parla di ***delegazione*** quando un oggetto $A$ contiene al suo interno un riferimento a un altro oggetto $B$, cosicché $A$ (*oggetto complesso*), può delegare alcune funzioni alla classe a cui appartiene $B$.

## Sviluppo di Sistemi a Oggetti
---
> L'obbiettivo principale dell'approccio ***Object-Oriented*** è migliorare la **produttività**, aumentando l'**estendibilità** e **riusabilità** del software, controllando *complessità e costi di manutenzione*.

>[!caution] Dll'approccio funzionale...

La *decomposizione funzionale* è un'analisi di tipo ***top-down*** impiegata nel ***paradigma procedurale***.
- Basata sui concetti di procedura e flusso di dati.
- Risponde alla domanda: *cosa fa il sistema, qual è la sua funzione?*
- Ad alto livello il sistema viene caratterizzato tramite un'***unica funzionalità***.

I blocchi di base sono i *task* che durante l'implementazione danno luogo a procedure.
- I *task* sono legati alla **specifica soluzione proposta**.
>[!fail] Problemi

- Mancanza di *estendibilità*.
- *Nessun modello unificante* per le diverse fasi.
- Mancanza di *iterazione* nella progettazione.
- Poca attenzione alla *riusabilità*.
- *Progettazione dei dati* trascurata.

>[!abstract] All'approccio a oggetti

L'***analisi*** va dall'inizio del progetto fino all'analisi delle *specifiche utente* e allo [[Definizione Strategica e Pianificazione#Studio di Fattibilità|studio di fattibilità]].

Si definiscono progettazione logica e fisica del sistema (***design***).

***Implementazione***:
- Scrittura del codice.
- Test di verifica.
- Validazione.
- Manutenzione.

>[!done] Soluzioni
- I confini tra le fasi non sono più distinti, il centro di interesse è l'***oggetto e le sue interrelazioni***.
- Processo di sviluppo ***iterativo***.

>La **decomposizione** è orientata alla **modellazione**:
- I blocchi di base sono entità che interagiscono, modellate come classi di oggetti.
- I risultati dell'analisi sono ***parte integrante del design***.

I sistemi sviluppati a oggetti risultano ***più stabili nel tempo*** di quelli progettati per decomposizione funzionale.

Alta produttività
- Fasi diverse dell'analisi e del ciclo di vita possono essere svolte ***contemporaneamente***.

