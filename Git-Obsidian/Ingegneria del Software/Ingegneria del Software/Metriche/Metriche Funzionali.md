> Metriche che si basano sulle *caratteristiche funzionali del programma*.

## Function Points
---
>[!info]
>Il metodo dei ***function points*** è la metrica più vecchia riguardante la *dimensione di un software*.
>>[!hint] Importante
>> Il metodo restituisce un ***parametro adimensionale*** (senza unità di misurazione).

Misura la dimensione di un **sw** in termine delle *funzionalità offerte all'utente*.
- Si basa sul disegno logico del software espresso in una forma qualsiasi.

>[!done] Pro
>È indipendente dall'ambiente tecnologico in cui si sviluppa il progetto
>Metodo "***blackbox***", non è necessario conoscere l'implementazione interna.
>- Può essere usato a partire *dalla prima fase dello sviluppo*.

> Può essere utilizzato come:
- Strumento per ***determinare la complessità*** di un pacchetto applicativo.
- Strumento che aiuti gli utenti a determinare il beneficio per le loro organizzazioni.
	- Attraverso la *quantificazione delle sole funzioni necessarie*.
- Strumento per misurare la **qualità** e la **produttività** di un prodotto.
- Strumento per la **stima dei costi** e **risorse** per sviluppo e manutenzione.
- ***Fattore di normalizzazione*** per effettuare confronti.

### Conteggio dei Function Points
>[!caution] Conteggio
>Il metodo consiste nell'identificare $5$ tipi di funzionalità.
>
>>[!hint] Funzioni di tipo Dati
>>- **Internal Logic File** (`ILF`).
>>- **External Interface File** (`EIF`).
>
>>[!abstract] Funzioni di tipo Transazione
>>- Input Esterno.
>>- Output Esterno.
>>- Interrogazioni Esterne.

Una volta identificate le funzioni, a ciascuna di esse si assegna un ***peso*** sulla base della quantità di dati e sulla *complessità* delle *relazioni tra loro*.

>[!missing] Numero Non pesato
>La somma dei pesi delle funzioni costituisce il ***numero di function points non pesato***.

Questo numero è poi moltiplicato per un fattore di aggiustamento ottenuto considerando un insieme di $14$ ***caratteristiche generali del sistema***.

#### Tipi di Conteggio
>[!todo] Per progetti di Sviluppo
- Il calcolo dei `FP` di un software da realizzare *ex novo* più un eventuale conversione dei dati dalla vecchia applicazione.

>[!caution] Per progetti di Manutenzione Evolutiva
- Misura le modifiche a un software esistente, comprendendo funzioni aggiuntive, modificate, cancellate e di conversione.
	- Si contano i `FP` in *positivo* sia la rimozione di una funzionalità precedente sia l'aggiunta della successiva.

>[!abstract] Per una Applicazione Esistente
- Consiste nel calcolo dei `FP` detti "***installati***" e il loro aggiornamento.
	- Differisce dal calcolo per i progetti di sviluppo: **Non** prevede *funzioni di conversione*.
	- Differisce dalla manutenzione evolutiva: I punti delle funzioni cancellate vengono **sottratti**.


>[!quote] Quindi
>I `FP` possono essere usati per misurare una applicazione durante **tutto il suo tempo di vita**.

>[!example] Esempio calcolo dei `FP`

- $1000\text{ fp}$ iniziali.
- $20\text{ fp}$ per la conversione.
- $5\text{ fp}$ per rimozioni.
- $7\text{ fp}$ per l'installazione.

> $1020\text{ fp}$ di *sviluppo*.
- Iniziali + Conversione.

>$12 \text{ fp}$ di *Manutanzione*.
- Rimozione + Installazione.

>[!hint] `FP` totali:
>$$1000+7-5$$
>Rappresentano l'***applicazione esistente***.

Quelli per la conversione erano di funzioni che nel software finale ***non sono presenti***.
- Non vengono contati nel conteggio totale.

#### Funzioni di tipo Dati
> `ILF` e `EIF` sono gruppi di dati o informazioni di controllo logicamente collegati e riconoscibili dall'utente.

>[!failure] Internal Logic File
>I dati sono mantenuti all'***interno dei confini*** dell'applicazione.

Il compito primario di un `ILF` è contenere dati mantenuti attraverso uno o più processi elementari dell'applicazione.
- Ha un costo `FP` maggiore rispetto all'`EIF`.
>[!example] Esempi
- Dati sulle entità gestite.
- Dati di log.
- etc...

>[!help] External Interface File
>I dati sono ***referenziati dall'applicazione*** ma sono mantenuti all'interno dei confini di un'altra applicazione.

Un `EIF` in una applicazione **DEVE** essere un `ILF` in un'altra.
- Dati referenziati da un'altra applicazione.
>[!example] Esempi
- Entità gestite da altre applicazioni.
- Dati sulla sicurezza mantenuti all'esterno dell'applicazione.
- etc...

#### Funzioni di tipo Transazione
>[!important] External Input `EI`
>È un *processo elementare* dell'applicazione che ***elabora*** dati o informazioni di controllo provenienti dall'***esterno del confine*** dell'applicazione.

Il compito principale di un `EI` è di mantenere uno o più `ILF`.

>[!abstract] External Output `EO`
> È un *processo elementare* dell'applicazione che ***manda*** dati o informazioni di controllo all'***esterno del confine*** dell'applicazione.

Il compito di un `EO` è di presentare informazioni all'utente attraverso una logica di processo *diversa* dal o in *aggiunta* al **recupero dati o informazioni di controllo**.
- La logica deve contenere almeno una *formula matematica o calcolo* (***deve creare derivati***).

>[!question] External Inquiry `EQ`
>È un *processo elementare* dell'applicazione che ***manda*** dati o informazioni di controllo all'***esterno del confine*** dell'applicazione.

Il compito principale di una `EQ` è di presentare informazioni all'utente attraverso il recupero di dati o informazioni di controllo da un `ILF` o `EIF`.
- **Non contiene** formule matematiche o calcoli.

### Fattore di Aggiustamento
>[!tldr] Idea
>Il numero totale dei `FP` viene moltiplicato per un fattore di aggiustamento per ***tenere conto delle funzionalità generali*** del sistema *non sufficientemente rappresentate*.

Il valore del fattore di aggiustamento varia tra $[0.65, 1.35] \quad (\pm 35\%)$ e viene calcolato sulla base del grado di influenza di ciascuna delle $14$ ***caratteristiche generali del sistema***.

Il grado di influenza di una caratteristica è compreso tra:
- $0$ *nessuna influenza*.
- $5$ *forte influenza*.

$$
f=0.65+(\text{TDI}\cdot 0.01)
$$
- Con `TDI` (totale degree of influence) la *somma dei gradi di influenza* per ciascuna caratteristica.