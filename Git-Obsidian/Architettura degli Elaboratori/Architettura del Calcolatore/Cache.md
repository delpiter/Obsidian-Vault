>*La [[Organizzazione della Memoria#Memoria Principale|memoria principale]] costituita da `DRAM` è più lenta della [[La CPU|CPU]], e pertanto la necessitàdi leggere codice e operandi dalla memoria causa un rallentamento rispetto alle prestazioni teoriche della `CPU`*

>[!done] Soluzione
>Una soluzione potrebbeessere quello di utilizzare `SRAM` invece di `DRAM`, molto più ***veloci*** e ***costose***

## La Memoria Cache
---
>[!info] Cache
>La ***cache*** è una piccola memoria `SRAM` inserita fra la *memoria principale* e la `CPU`
>La `CPU` reperisce sempre i dati dalla ***cache***, come se questa potesse contenere tutta l'informazione memorizzabile in `RAM`
>>[!done] *Cache Hit*
>>Qualora la parola desiderata sia *effettivamente presente* in **cache** otteniamo un indiscutibile *vantaggio* in termini di ***tempo di accesso alla memoria***
>
>>[!fail] *Cache Miss*
>>D'altro canto, se la parola non è presente, è necessario trasferirla da `DRAM` a ***cache*** e poi *leggerla*
>>In questo caso il tempo totale è *sostanzialmente maggiore* rispetto alla lettura della `DRAM`

![[attachements/CachePosition.png]]
*L'utilizzo di cache è **vantaggioso** solo quando la percentuale di hit è sufficientemente alta*

### Caricamento del Dato
>*Il caricamento di un dato in un sistema dotato di cache è il seguente:*

>[!abstract] *Steps*
>1. Richiedi il dato alla ***cache***
>2. Se il dato ***è presente*** in cache, caricalo subito (***cache hit***)
>3. *Altrimenti*:
>	1. *Leggi* il dato dalla ***memoria***
>	2. *Carica* il nuovo dato in ***cache***, se la *cache* è "*piena*" ([[#Ricerca di un Valore in Cache|vedi mappatura]]), applica la politica di rimpiazzamento per caricare il nuovo dato al posto di uno di quelli esistenti

- I valori ***modificati in cache*** in genere non sono riscritti immediatamente in *memoria*
	- Potrebbero dovere essere nuovamente *aggiornati*
	- Vengono riscritti prima del rimpiazzamento (***write-deferred***)
	- ***write-back***, scrive subito il valore cambiato in *memoria*


>[!info] *Linee di Cache*
>La copia di dati tra memoria principale e cache *non avviene per parole singole* ma per blocchi denominati ***linee di cache***
>La dimensione di una ***linea di cache*** varia da $8$ a $512$ *parole*

## Principi della Cache
---
>[!tldr] Principio di Località Spaziale
>Il ***principio di Località Spaziale*** dice che vi è alta probabilità di accedere, entro un *breve intervallo di tempo*, a celle di memoria con ***indirizzo vicino***

>[!tldr] Principio di Località Temporale
>Il ***principio di Località Temporale*** dice che vi è alta probabilità di accedere nuovamente, entro un *breve intervallo di tempo*, ad una cella di memoria alla quale si è ***appena avuto accesso***

## Tecniche di Gestione
---
>[!abstract] Basate sul Principio di Località Spaziale
>Le ***politiche di allocazione*** tengono conto di ciò che leggendo normalmente più dati di quelli necessari (un'intera ***linea di cache***) con la speranza che questi *vengano in seguito richiesti*

>[!abstract] Basate sul Principio di Località Temporale
>Le ***politiche di rimpiazzamento*** sfruttano il principio di località temporale per decidere quale blocco di ***cache*** rimpiazzare
>Normalmente la politica utilizzata è `LRU` (***L***east ***R***ecently ***U***sed)
>- Viene rimpiazzato il blocco utilizzato ***meno recentemente***
>
>Se il dato è *stato modificato* in cache ***prima del rimpiazzamento*** deve essere aggiornato in memoria

## Livelli di Cache
---
*Nei calcolatori moderni vengono spesso utilizzate più cache*

>[!info] Livelli
>Diversi ***Livelli di Cache*** ($L_{1},L_{2},L_{3}$) sono impiegati a cascata per ottimizzare il ***trade-off costi/prestazioni***

La realizzazione di tutti i ***livelli di cache*** all'interno della `CPU` consente di realizzare `BUS` *interni molto veloci* riservati esclusivamente alla comunicazione `CPU`-*cache*

>[!example] Livello $1$

La cache di livello $I$ è la più veloce tra tutte, molto vicino alla `CPU`
- È divisa in due ***cache***
	- Una utilizzata per le ***istruzioni***
	- Una utilizzata per i ***dati***
>[!question] Perché questa divisione?

>*Esempio Banale*

Un ***ciclo*** che scorre un array *molto grande*
- Le *istruzioni* sono ***sempre le stesse***
- I *dati* cambiano ***ogni ciclo***

>[!example] Livello 2

La cache di livello $II$ è un po' più grande di quella di livello $I$
- Leggermente più lenta di quella di livello $I$
- Più capiente di quella di livello $I$

>[!example] Livello 3

La cache di livello $III$ è la *cache* più capiente, qualche decina di $Mb$
- Leggermente più lenta di quella di livello $II$
- Più capiente di quella di livello $II$

## Ricerca di un Valore in Cache
---
>[!question] Come fa una cache a capire "velocemente" se un certo dato/indirizzo è presente?

>[!info] Mappatura Diretta
>Nel tipo di ***cache*** più semplice, denominata ***mappatura diretta*** una linea, quando presente, può essere caricata in una sola posizione che dipende da un sottoinsieme dei `BIT` dell'indirizzo

>[!fail] Svantaggio

Questo modello non consente l'implementazione di ***politiche di rimpiazzamento efficaci***
- Ogni collisione determina l'***uscita obbligatoria*** del contenuto *precedente*

>[!info] $n$-way set-associative
>Ciascuna linea può essere ospitata in $n$ ***posizioni diverse*** e questo garantisce migliori prestazioni potendo applicare rimpiazzamento con politica `LRU`

*La cache nei processori Intel e AMD recenti sono associative a $n$-vie con valori di $n=8$ o superiori*

## Cache in una CPU Multicore
---
>*In una [[La CPU|CPU]] multicore, solitamente, i livelli $\text{L1}$ e $\text{L2}$ sono privati per ciascun core, mentre il livello $\text{L3}$ è condiviso*

>[!question] Come mantenere consistenza in memoria?

Supponiamo che il core #$3$ abbia caricato nella propria cache l'indirizzo $100$ e *modificato anche il valore*
- Il suddetto valore *non è subito aggiornato* per ***ottimizzare le prestazioni***
- Se il core #$5$ deve accedere allo stesso dato e lo preleva dalla memoria si rischia una ***situazione inconsistente***

>[!done] Soluzione: *Snooping*

Per gestire queste situazioni i core ascoltano sempre cosa avviene sul `BUS` della memoria
Se ci sono operazioni che ***interessano linee che sono nella loro cache***
- Subentrano e forniscono alle ***cache richedenti*** di altri *core* il valore corretto prima che la memoria risponda
