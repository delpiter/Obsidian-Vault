>[!summary] Tipi di Organizzazione dei Dati
>>[!help] Primaria vs Secondaria
>>*Primaria*:
>>- Definisce un criterio di allocazione dei dati nei file.
>>*Secondaria*:
>>- Rappresenta un ulteriore metodo di accesso all’organizzazione primaria.
>
>>[!abstract] Statica vs Dinamica
>>*Dinamica*:
>>- Si adatta alla mole effettiva dei dati.
>>*Statica*:
>>- Prevede fasi di riorganizzazione globale a *fronte di variazioni*.
>
>>[!caution] Per [[Vincoli di Integrità#Chiavi|chiave primaria]] vs chiave secondaria.
>> Il valore della chiave identifica un **unico record** in un’organizzazione per chiave primaria, e più record nel secondo caso.

### Tipi di Operazioni
>Le operazioni, per quanto complesse, ***sono riconducibili***, in termini di I/O, ad alcune primitive di base:

>[!check] Ricerca Esatta

> ***Chiave Primaria***
- Restituisce al più un solo record.
> ***Chiave Secondaria***.
- Restituisce 0 o più record.
> ***Intervallo***
- Restituisce 0 o più record.
> ***Varie Combinazioni***
- 0 o più record.

>[!abstract] Inserimento di Record

>[!missing] Cancellazione di Record

>[!caution] Modifica di Record

## Organizzazioni Primarie e Secondarie
---
> Le ***organizzazioni primarie*** si dividono in quattro categorie:

- Strutture sequenziali non ordinate (*heap*).
- Strutture sequenziali ordinate (*sorted sequential file*).
- Ad accesso calcolato (*hash file*).
- Ad albero (*indexed organization*).

Le *organizzazioni secondarie* sono principalmente **strutture ad albero**.

### Organizzazioni Sequenziali
#### Heap
> L'ordine temporale della registrazione e l'organizzazione è detta **heap** o **pile**.

>[!abstract] Heap File
>L'inserimento di un nuovo record è effettuato ***appendendolo alla fine del file***.
>L'eliminazione comporta "*marcare*" come ***non valido*** il record interessato.

La struttura permette di gestire [[Dispositivi di Memorizzazione#Rappresentazione dei Valori|record a lunghezza fissa o variabile]].
- La modifica può richiedere la *cancellazione del vecchio record* e l'**inserimento in altra pagina** con spazio sufficiente.

>[!info] Utilità
>La struttura ***non è efficiente*** per memorizzare record a *lunghezza variabile*, se soggetta a frequenti aggiornamenti.
>È utile invece:
>- Con **piccoli volumi** di dati.
>- Operazioni che interessano **tutti o gran parte dei record**.
>- Aggiornamenti **poco frequenti**.

#### Sorted Sequential File
>Un [[Problema dell'Ordinamento|ordinamento]] in base a un **campo chiave** e l'organizzazione è detta ***sorted***
 ***sequential file*** o ***clustered file***.

>[!summary] SSF
>Può dare vantaggi nel caso in cui si debba cercare record secondo l'***ordine dei valori*** (caso tipico: *Chiave Primaria*).
>- Ricerche di un ***singolo record***.
>- Ricerche di ***intervallo***.

Non ottiene nessun vantaggio per ricerche su altri attributi ***non di ordinamento***.

> Mantenere l'ordinamento a fronte di modifiche può essere ***molto dispendioso***.

Per aumentare l'efficienza:
- Si prevedono molti spazi liberi, con ulteriori *blocchi* in un ***overflow file*** non ordinato.
- Periodicamente i due file (*master* e *overflow*) vengono fusi per produrre un unico file.
### Hash File
> Prevede l'uso di [[Funzione di Hash|funzioni hash]] per ***allocare i record nei blocchi***.

Ogni indirizzo generato dalla funzione $H$ individua una ***pagina logica***.
- Possono verificarsi delle [[Funzione di Hash#Collisioni|collisioni]].

>[!caution] Efficienza
>Pur in presenza di collisioni, le ***organizzazioni hash*** sono in genere efficienti per il ***reperimento di un singolo record***.
>Poco efficienti per altri tipi di ricerca (es. *intervallo*).

> Una funzione hash deve essere [[Git-Obsidian/Analisi/Funzioni/Introduzione Funzioni#Funzione Surriettiva|suriettiva]], quindi generare $n$ indirizzi tanti quanti sono i ***bucket dell'area primaria***.
##### Organizzazione Statica
>[!info] Il valore di $n$ è fissato alla creazione della struttura e mantenuto costante

##### Organizzazione Dinamica
>[!help] Il valore di $n$ è variabile, l'area primaria può contrarsi ed espandersi.

