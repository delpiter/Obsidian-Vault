# Dati e Pattern
---
> I ***dati*** sono un ingrediente fondamentale del machine learning, dove il comportamento dei modelli non è pre-programmato ma appreso dai dati stessi.


> [!hint] Data-point
> Generalmente un campione (*multidimensionale*) nel dominio di interesse è definito ***data-point***.

> [!info] Pattern
> Un ***pattern*** può essere definito come l'*opposto del caos* e come un entità vagamente definita a cui può essere dato un nome.

Il termine pattern è spesso usato come sinonimo di *data-point*
- Pattern recognition.

> Esempi
- un volto
- un carattere scritto a mano
- una impronta digitale
- un segnale sonoro
- del testo, etc...

Il *Pattern recognition* è la disciplina che studia il **riconoscimento dei pattern**.

### Tipi di pattern
#### Numerici
> [!abstract] Pattern Numerici
> I ***pattern numerici*** sono valori associati a caratteristiche misurabili o conteggi.

Tipicamente *continui*, ma anche *discreti*, in ogni caso soggetti ad ordinamento.
- Sono rappresentabili come **vettori numerici** nello spazio multidimensionale
- L'*estrazione* di caratteristiche da segnali produce vettori numerici detti anche **feature vectors**

> Es.
- Persona: $[\text{altezza}, \text{lunghezza del piede} , \text{peso}, \text{circonferenza fianchi}]$

#### Categorici
> [!example] Pattern Categorici
> I ***pattern categorici*** sono valori associati a *caratteristiche qualitative* e alla presenza/assenza di una carattaristica (**yes/no value**).

>  Esempi 
- Persona: $[\text{sesso}, \text{maggiorenne}, \text{colore occhi}, \text{gruppo sanguigno}]$.
- *Talvolta* soggetti ad **ordinamento**
	- ***Temperatura***: alta media bassa,
	- ***Gruppo sanguigno***: *non* ordinabile.

#### Sequenze
> [!caution] Pattern sequenziali
> I ***pattern sequenziali*** sono pattern con *relazioni spaziali* o *temporali*.

Spesso a **lunghezza variabile**:
- La *posizione* nella sequenza e le *relazioni con predecessori e successori* sono importanti.
- Critico a trattare sequenze come pattern numerici.

L'allineamento spaziale/temporale e la "memoria" vengono usati per tener *conto del passato*.
- Usato in approcci moderni come **deep learning e transformers**.

> Es.
- Uno ***stream audio*** che corrisponde alla pronuncia di una parola
- una *frase* in linguaggio naturale
- l'*andamento* di un titolo in borsa.

#### Altri dati Strutturati
>[!hint] Altri dati
> Gli input/output sono organizzati in ***strutture complesse*** come [[../Algoritmi e Strutture Dati/Strutture Dati/Grafi/Alberi/Gli Alberi|Alberi]] e [[../Algoritmi e Strutture Dati/Strutture Dati/Grafi/I Grafi|Grafi]].

Applicazioni in bioinformatica, natural language processing, speech recognition, *etc*...

#### Dati Tabulari
> [!todo] Dati Tabulari
> I ***Dati tabulari*** sono dati tipicamente *estratti da un database*.

I dati sono eterogenei:
- Nelle *colonne* ci sono gli **attributi** (***features***) e nelle *righe* i **record** (***datapoint***).
- Le colonne possono avere formato *numerico* o *categorico* (spesso entrambi)
- Le colonne sono *eterogenee* (eta di una persona, il salario, città di residenza)
- I dati possono essere **incompleti** e ***fortemente sbilanciati***.

Le tecniche di deep learning ***non sono ancora molto competitive*** su dati tabulari.
- Multi classificatori basati su alberi rimangono spesso più performanti.

## Encoding
---
> [!Example] Esempio
> Dato il campo materiale con i seguenti $5$ valori possibili:
> - acciaio, cemento, ghisa, polietilene, PVC
>> [!question] Come codificarlo in formato numerico?
>>


Le soluzioni possibili e valide sono principalmente due:
- One-hot encoding
- Ordinal Encoding

### One-hot Encoding

> [!tldr] Idea
> Il ***one-hot encoding*** consiste nella conversione di un valore categorico creando una *colonna binaria* separata per ogni categoria del dataset, dove $1$ indica che la *presenza della categoria*. 

> Esempio
- Si rimuove il campo e al suo posto si aggiungono tanti campi quanti sono i valori distinti.
- Ciascun campo è **associato a un materiale diverso** e può assumere solo valore `0/1` dove 1 indica che il pattern è di quel materiale.

>[!cite] In pratica
>Nella pratica si sostituisce una colonna singola (*stringa*) in $n$ colonne binarie.


> [!danger] Attenzione

Se i valori sono tanti (es $500+$), si possono analizzare i dati e vedere quelli *più frequenti*, e rimuovere quelli meno usati, sostituendoli con una **colonna** "*altro*".

### Ordinal Encoding
> [!tldr] Idea
> Nell'***Ordinal encoding*** si trasforma il campo originale in campo numerico associando alle varie categorie dei valori ordinali.

> Esempio
- Acciaio = 1, Cemento = 2, Ghisa = 3, Polietilene = 4, PVC = 5.