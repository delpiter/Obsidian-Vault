>[!info] Intro
> Ogni calcolatore dispone di un set di caratteri da utilizzare
- All'interno del calcolatore i caratteri sono codificati sotto forma di numeri

Per associare a ciascun numero un carattere specifico è necessario introdurre una mappatura
- Questa mappatura dei caratteri in numeri è detta ***codice di caratteri***
- Per potere comunicare è essenziale che tutti i calcolatori utilizzino la stessa mappatura
## ASCII
---
>[!info] American Standard Code for Information Interchange
> L'***ASCII*** è una delle mappature standard per la comunicazione elettronica

Ogni carattere `ASCII` utilizza 7 `BIT`
- Sono quindi possibili $128$ configurazioni

>[!tip] CheckSum

Dato che  i dati vengono trasmessi in `BYTE` l'ottavo `BIT` viene utilizzato per verificare la correttezza del dato inviato
- Questo ottavo `BIT` viene chiamato **check `BIT`** o [[../../Definizioni/Definizioni_Architettura#Parity Bit|parity]] `BIT`
- Il formato `ASCII` non viene ormai più utilizzato come protocollo di trasmissione
	- Ne consegue il fatto che l'ottavo `BIT` viene normalmente utilizzato per codificare caratteri *non-standard*
### Caratteri di Controllo
>[!info] 
>I caratteri da $0$ a $1F_{16}$ ($31_{10}$) sono **caratteri di controllo** e non vengono stampati

Molti dei caratteri di controllo servivano alla trasmissione dei dati, ma con l'evoluzione dei *protocolli di comunicazione* non vengono più utilizzati

### Caratteri Latini
>[!info]
>Il resto dei caratteri rappresentabili è un insieme di lettere maiuscole, minuscole caratteri speciali e cifre numeriche

## Unicode
---
>[!info] Definizione
>L'***unicode*** è il sistema per la codifica dei caratteri di *quasi* tutte le lingue vive (e alcune lingue morte), includendo anche simboli matematici, alfabeto Braille, ideogrammi, etc...

Inizialemente pensato come codifica a `16 BIT`, quindi con $65.536$ simboli
- Molto presto `16 BIT` diventarono insufficienti per rappresentare tutti i caratteri
- Fu prevista la possibilità di avere caratteri codificati con un numero di `BIT` maggiore di 16
- Nella versione $v10.0$ sono presenti più di $136.000$ [[../../Definizioni/Definizioni_Architettura#Code Point|code points]] con codifica fino a `21 BIT`

### Codifiche Possibili
>[!tip] `UTF-8`
>L'`UTF-8` necessita di $8,16,24$ o $32$ `BIT` (da uno a quattro `BYTES`) per codificare un carettere unicode

- Utilizzato per la compatibilità, dato che i primi $128$ codepoints corrispondono al codice `ASCII`
- Tipicamente adottato nei file `.txt .html .xml`

>[!tip] `UTF-16`
>L'`UTF-16` necessita di $16$ o $32$ `BIT` per codificare un carettere unicode

- Utilizzato dai moderni sistemi operativi e linguaggi di programmazione per codifica di stringhe
 
>[!tip] `UTF-32`
>Tutti i code points sono codificati con `4 BYTES`