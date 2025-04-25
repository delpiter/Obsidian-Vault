## Anomalie
---
>[!help] Ridondanza Logica
>Una ***ridondanza logica*** è una *duplicazione* di dati che, oltre a comportare *spreco di memoria*, può generare **anomalie** nelle operazioni sui dati.

>Esempio

Tabella studente con annesse le informazioni dell'università:
- **STUDENTI**(<u>Matricola</u>, Nome, Cognome, Università, Indirizzo_Università).

#### Anomalia di aggiornamento
>[!caution] Concetto
>Necessità di ***estendere l'aggiornamento*** di un dato a tutte le tuple in cui esso compare.

>Esempio
- Se l'indirizzo dell'università cambia, è necessario modificare il valore in diverse tuple *studente*.

#### Anomalia di inserimento
>[!abstract] Concetto
>L'inserimento di ***dati nuovi*** deve essere accompagnato dall'inserimento di dati *non necessari*.
>>[!quote] In altre Parole
>>L’inserimento di informazioni relative a uno solo dei concetti di pertinenza di una relazione è **impossibile** *se* non esiste un intero insieme di concetti in grado di costituire una ***tupla completa***.

>Esempio
- Per aggiungere una ***nuova università***, bisogna aggiungere anche uno *studente*.
#### Anomalia di cancellazione
>[!fail] Concetto
>***Perdita di informazione*** a seguito di una cancellazione di un dato diverso.
>>[!quote] In altre Parole
>>L’**eliminazione di una tupla**, può comportare l’***eliminazione di dati*** che conservano comunque la loro validità.

> Esempio
- Se tutti gli studenti di una università interrompono la partecipazione all'università, bisogna ***eliminare l'università***.

## Forme Normali
---
>[!info] 
>La ***normalizzazione*** è una *attività* che permette di trasformare schemi non normalizzati in schemi che soddisfano una **forma normale**.

- Utilizzata come tecnica di verifica dei risultati della progettazione di una base di dati.
- **Non** è una metodologia di progettazione.

>[!hint] Proprietà di uno schema relazionale
>Garantiscono:
>- **Qualità** del database.
>- **Assenza di determinati difetti**.

![[NormalForms.png]]
### Decomposizione Senza Perdita
>La decomposizione *non deve alterare* il **contenuto informativo** del database.

>[!hint] Decomposizione Lossless
>Uno schema $R(X)$ si decompone senza perdita negli schemi $R_{1}(X_{1})$ e $R_{2}(X_{2})$ se, per ogni stato legale $r$ su $R(X)$, il  [[Algebra Relazionale#Join Naturale|join naturale]] delle [[Algebra Relazionale#Proiezione|proiezioni]] di $r$ su $X_{1}$ e $X_{2}$ è uguale a $r$ stessa:
>$$\pi_{X_{1}}(r)\bowtie\pi_{X_{2}}(r)=r$$
>>[!quote] A Parole
>>Uno *schema* si decompone ***senza perdita*** se, eseguendo il **join naturale** delle tabelle “decomposte”, si ottiene esattamente la tabella originale.

>[!missing] Decomposizione Lossy
> Una decomposizione **con perdita**, a seguito del **join naturale**, può:
>  - **Perdere** delle tuple (*tuple spurie*).
>  - **Generare** delle tuple errate.


### Dipendenze Funzionali
>[!definizione] Definizione
>Si considerino uno [[Modello Relazionale|schema di relazione]] $R(T)$ e un'estensione $r$; Due sottoinsiemi *non vuoti* di $T$ denominati $X$ e $Y$ rispettivamente.
>Si dice che in $r$ vale la dipendenza funzionale $X\to Y$ ($X$ <u>determina funzionalmente</u> $y$) se:
>$$\forall t_{1},t_{2}\in r:t_{1}[X]=t_{2}[X]\implies t_{1}[Y]=t_{2}[Y]$$
>>[!quote] A Parole
>>Per ogni coppia di tuple $t_{1}$ e $t_{2}$ di $r$ con gli stessi valori su $X$,  $t_{1}$ e $t_{2}$ hanno gli stessi valori anche su $Y$

Una dipendenza funzionale sempre soddisfatta è detta **banale**.
- Se $Y\subseteq X$ allora sicuramente $X\to Y$

Dire che $X\to Y$ significa asserire che i valori della componente $Y$ ***dipendono*** (sono determinati) dai valori della componente $X$.

>Se $K$ è una [[Vincoli di Integrità#Chiavi|chiave]] in uno schema $R(T)$:
- Allora ogni altro attributo di $R(T)$ dipende funzionalmente da $K$

#### Dipendenze Funzionali e Superchiavi
> Il concetto di [[Vincoli di Integrità#Superchiave|superchiave]] si esprime facendo uso di *dipendenze funzionali*.

$$
K\subseteq T \text{ è superchiave di }R(T) \iff K \to T
$$

>[!Dimostrazione]

> Se $K\to T$ allora per ogni *istanza legale* di $r$ si ha che:

$$
\forall t_{1},t_{2}\in r:t_{1}[K]=t_{2}[K] \implies t_{1}[T]=t_{2}[T]
$$
- Ciò equivale a dire che non possono esistere due tuple distinte con lo stesso valore di $K$.

> Se $K$ è *superchiave* di $R(T)$, dalla definizione di [[Vincoli di Integrità#Superchiave|superchiave]]:

$$
t_{1}[K]=t_{2}[K] \implies t_{1}=t_{2}
$$
<u>Allora</u>
$$
t_{1}[T]=t_{2}[T]
$$
### Prima Forma Normale (1NF)
>[!tldr] Forma Atomica
>Uno schema $R(T)$ è in ***1NF*** <u>se e solo se</u> il *dominio* di ciascun attributo comprende solo valori valore ***atomici*** (semplici, indivisibili) e il **valore** di ciascun attributo in una tupla è un *singolo del dominio* di quell’attributo.
### Seconda Forma Normale (2NF)
>[!tldr] Second Normal Form
>Uno schema $R(T)$  con vincoli $F$ è in ***2NF*** <u>se e solo se</u> ogni attributo **non primo** dipende *completamente* da **ogni chiave** candidata dello schema.

> Esempio: **PRODUTTORI**(Produttore, Modello, <u>NomeModello</u>, Stato)

Dipendenze Funzionali:
- **NomeModello** $\to$ **Produttore**
- **NomeModello** $\to$ **Modello**
- **Produttore**, **Modello** $\to$ **NomeModello**
- **Produttore** $\to$ **Stato** (*dipendenza parziale*)

>[!fail] La relazione non è in ***2NF***

La trasformazione in **2FN** prevede due relazioni:
- **PRODUTTORI**(<u>Produttore</u>, Stato)
- **MODELLI**(<u>NomeModello</u>, <u>Modello</u>, NomeModello)
### Terza Forma Normale (3NF)
> Per definire la **3NF** è necessario introdurre il concetto di *dipendenza transitiva*.

>[!info] Dipendenza Transitiva
>Dato uno schema $R(t), X\subseteq T, A \in T$, $A$ ***dipende transitivamente*** da $X$ se esiste $Y \subset T$ tale che:
>1. $X\to Y$
>2. $\neg(Y \to X)$ ($Y$ non determina $X$)
>3. $Y \to A$
>4. $A\notin Y$

>[!tldr] Third Normal Form
>Uno schema $R(T)$  con vincoli $F$ è in ***3NF*** <u>se e solo se</u> **non** c'è ***dipendenza transitiva*** di un *attributo non primo* da una chiave.

> Esempio di normalizzazione in **3NF**:

**IMPIEGATI**(<u>Impiegato</u>, Stipendio, <u>Settore</u>, Budget, Ruolo)

Dipendenze:
- *Impiegato* $\to$ Stipendio (*dipendenza parziale*)
- *Settore* $\to$ Budget (*dipendenza parziale*)
- *Impiegato*, *Settore* $\to$ Ruolo

La tabella viene scomposta nelle seguenti tabelle:
- **IMPIEGATI**(<u>Impiegato</u>, Stipendio)
- **SETTORI**(<u>Settore</u>, Budget)
- **RUOLI**(<u>Impiegato</u>, <u>Settore</u>, Ruolo)


#### Algoritmo di Decomposizione in **3NF**
>[!hint] Idea
>L'algoritmo consiste nel creare una relazione per ogni gruppo di ***dipendenza funzionale*** che hanno lo **stesso lato sinistro** (*determinante*) e inserire nello schema corrispondente gli attributi coinvolti in *almeno una* dipendenza funzionale del gruppo.

> Esempio: se le **FD** individuate sullo schema **R**(<u>AB</u>CDEF) sono:
- **AB** $\to$ CD
- **AB** $\to$ E
- **C** $\to$ F
- **F** $\to$ G

Si generano gli schemi:
- **R1**(<u>AB</u>CDE)
- **R2**(<u>C</u>F)
- **R3**(<u>F</u>G)

### Forma normale di Boyce e Codd (BCNF)
>[!tldr] Boyce-Codd Normal Form
>Uno schema $R(T)$ con vincoli $F$ è in **BCNF** se, per ogni *dipendenza funzionale* non banale $X\to Y$ definita su di esso, $X$ è una [[Vincoli di Integrità#Superchiave|superchiave]] di $R(T)$

>[!warning] Attenzione
> **Non è sempre possibile** portare uno schema in **BCNF** e allo stesso tempo *preservare tutte le dipendenze funzionali*.

