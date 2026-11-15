## Data Cleaning
---
> Una volta riconciliati degli schemi è necessaria una pulizia dei dati.

> [!cite] Definizione
> Con il termine ***pulizia dei dati*** si intende (*data cleaning*) l'insieme delle operazione atte a garantire la consistenza e la correttezza dei dati presenti nel livello riconciliato.

### Cause di Errori
> Le principali cause di inconsistenza nei dati sono le seguenti

> [!fail] Errori di battitura
> Gli ***errori di battitura*** sono sempre possibili se al momento dell'inserimento non sono previste *procedure di controllo* dei valori inseriti (es controllo correttezza del `CF`).


> [!summary] Differenza del formato dei dati dello stesso campo
> Si verifica ogni volta che l'informazione memorizzata in un campo ***non sia rigidamente strutturata*** / ***non standardizzata***.

In pratica quando lo *stesso valore* viene rappresentato in *maniere diverse*:
- Es Informazione: 
	- ***Italia*** - modi di memorizzazione: `I`, `IT`, `Italia`
	- ***Coca Cola***: `Coca cola`, `The coca-cola Company`, `Coca-cola Co.`, etc...


> [!quote] Inconsistenza tra valori e descrizione dei campi
> Si verifica a causa dell'evoluzione del modo di operare in azienda o dal variare delle abitudini di vita che rendono ***indispensabile una informazione*** di cui *non era prevista la memorizzazione*.

> [!caution] Inconsistenza tra valori di campi correlati
> Si verifica quando i valori presenti in due o più campi sono ***singolarmente corretti*** ma ***inconsistenti***

Errore che coinvolge ***più di un campo*** del Database
- Es `citta:'Bologna', regione:'Lazio'`


> [!missing] Informazioni Mancanti

Come per esempio il `SI` di un pronto soccorso:
- Se il paziente è incosciente, non è possibile inserire i dati.

> [!example] Informazioni duplicate

### Tecniche di Risoluzione
#### Tecniche basate sui Dizionari
> [!info] Info
> Con questo termine si indicano le tecniche di verifica della correttezza dei valori di un campo basate su ***tabelle di look-up e dizionari*** per la ricerca di *abbreviazioni* e *sinonimi*.

Queste tecniche sono applicabili solo quando il dominio del campo è ***conosciuto e limitato***.
- Semplicemente si crea una *tabella di trans-codifiche*.

Possono essere applicate anche a più campi contemporaneamente per verificare inconsistenze tra due campi correlati.

#### Tecniche basate sulla Similarità
> [!abstract] Info
> Usate quando si devono ***combinare in una unica destinazione*** dati provenienti da *sorgenti diverse* senza una chiave comune.

>[!question] Esempio: Quando due date possono essere simili?

Quando tutta la data (rappresentata numericamente) **varia una sola cifra** da quella reale, che potrebbe essere causato da un errore di input.
- 15 *ottobre* - 15 *novembre* oppure gennaio $1981$ e gennaio $1991$.
	- Sono entrambe date simili.

Quando due istanze di uno stesso schema devono essere fuse assieme, si parla di ***purge-merge problem***.
- Due istanze non sono disgiunte

##### Similarità tra record
> [!tldr] Funzione di Similarità
> Le tecniche basate su ***funzioni di similarità***, comparano le sottostringhe di $A_{i}\in A$ e $B_{i}\in B$, calcolando la similarità in base alla seguente formula ricorsiva:
> $$\text{aff}(A,B)=\frac{1}{|A|}\sum_{i=1}^{|A|}\max_{j=1}^{|B|}\text{aff}(A_{i},B_{j})$$

Dove la comparazione tra i sotto-campi elementari è basata sul *confronto tra stringhe* e sulla verifica della ***presenza di abbreviazioni*** che vengono ricercate in base a pattern ben definiti.

Similarità tra record
3 casi di similarità (output della *funzione di similarità*) dati due record $P_{1}$ e $P_{2}$
- Campi ***uguali*** o ***quasi uguali***, restituisce `true`;
- Campi ***differenti*** restituisce `false`;
- Campi ***simili***, richiedo una verifica da un controllore umano;

> [!help] Gruppi di Regole
> Vengono valutate le caratteristiche come la edit-distance (o [[../../Architettura degli Elaboratori/Architettura del Calcolatore/Correzione di Errori#Distanza di Hamming|distanza di Hamming]]) tra le due stringhe o la differenza di valore tra due campi numerici.

> Esempio: Lotta digitale all'evasione fiscale
- L'obbiettivo era trovare dei pattern di evasione legati all'utilizzo delle case come:
	- Falsi separati: due sposi separati che hanno la residenza in due case diverse, ma i consumi non sono coerenti ($0$ in una casa e consumo di circa due persone nell'altra).

> [!abstract] Similarità al tempo degli `LLM`
> ***Similarità vettoriale***: Un `DBMS` *vettoriale* consente la ricerca di somiglianza semantica su dati complessi.

I `vectorDB` sono alla base di sistemi `RAG` (***Retreival Augmented Generation***)

Ogni record viene convertito in un vettore chiamato embedding
- Es Un documento di grandi dimensioni viene spezzato in chunk per migliorare le prestazioni e evitare che il modello si "perda"
- Gli embedding sono in grado di cogliere la somiglianza semantica
- La similarità semantica è particolarmente utile sulle descrizioni, su ID, codici date e quantità sono meglio confronti esatti.

![[attachements/VectorDataSimilarity.png]]

A lezione esempio di technogym che non funziona una sega xD.