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
### Proprietà di uno schema relazionale
Garantiscono:
- **Qualità** del database.
- **Assenza di determinati difetti**.
### Dipendenze Funzionali
>[!def] Definizione
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
## Prima forma normale (1NF) - "Forma Atomica"
- Ogni attributo deve avere un **dominio atomico**.
- Ogni attributo deve contenere solo **un valore**.

## Seconda forma normale (2NF)
Uno schema è in **2NF** se:
1. È in **1NF**.
2. Ogni attributo **non chiave** dipende **completamente** da ogni chiave.

## Terza forma normale (3NF)
Uno schema è in **3NF** se:
1. È in **2NF**.
2. Non esistono **dipendenze transitive**.
   - **Un attributo non chiave** non deve dipendere da **un altro attributo non chiave**, che a sua volta dipende dalla chiave dello schema.
- È sempre possibile ottenere schemi in **3NF** preservando tutte le dipendenze.

## Forma normale di Boyce e Codd (BCNF)
Uno schema è in **BCNF** se:
- Per ogni dipendenza funzionale non banale **Y → Z**, **Y** è una **superchiave** dello schema.
- **Non è sempre possibile** portare uno schema in **BCNF**.

---

# DECOMPOSIZIONE SENZA PERDITA

- La decomposizione non deve alterare il **contenuto informativo** del database.
- **Decomposizione lossless**: Uno schema si decompone senza perdita se, eseguendo il **join naturale** delle tabelle “decomposte”, si ottiene esattamente la tabella originale.
- Una decomposizione **con perdita** può:
  - **Perdere** delle tuple.
  - **Generare** delle tuple errate.
