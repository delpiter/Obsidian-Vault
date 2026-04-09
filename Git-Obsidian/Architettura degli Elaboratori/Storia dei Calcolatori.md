## Generazione $0$
---
>[!info] I calcolatori Meccanici

### Blaise Pascal - 1642
Il primo a costruire macchine calcolatrici fu lo scienziato ***Blaise Pascal*** nel 1642
- Realizzò un dispositivo a ingranaggi azionati per mezzo di una manovella
- Era in grado di effettuare *addizioni e sottrazioni*
- Implementava meccanicamente i **meccanismi di riporto**

### Von Leibniz - 1672
Successivamente, nel 1672, **Gottfried Von Leibniz**:
- Inventò una macchina in grado di fare anche moltiplicazioni e divisioni
- La novità: Era costituita da un **traspositore** che permetteva di memorizzare un numero per sommarlo ripetutamente

### Charles Babbage, Ada Lovelace - 1834
Nel 1834, Charles Babbage, progettò l'***analytical engine***
- Primo dispositivo in grado di calcolare funzioni diverse in base al tipo di programma caricato
- Per problemi di finanziamento la realizzazione non venne mai completata
	- È stato dimostrato che il dispositivo poteva realmente funzionare
- Per produrre il software necessario Babbage collaborò con **Ada Lovelace**
	- Prima programmatrice della storia
	- I programmi rimasero teorici e non vennero mai eseguiti

## Generazione $I$
---
>[!info] Valvole Termoioniche e Relè
>Sono i primi calcolatori elettrici e digitali
>*Valvole termoioniche, relè* e *transistor* si basano sullo stesso principio:
>- Permettono di memorizzare un'informazione *binaria*

### Colossus - 1943
Nato in Inghilterra per l'esigenza di decodificare i messaggi criptati tra Hitler e i capi di stato maggiore durante la $II$ Guerra Mondiale

Evoluzione della macchina "*The British Bombe*" a cui lavorò ***Alan Turing*** per decifrare i messaggi di Enigma
- "*Bombe*" era una macchina progettata per un compito specifico
- "*Colossus*" era un calcolatore **programmabile** basato su *valvole termoioniche*

### ENIAC - 1946
>[!done] **Electronic Numerical Integrator and Computer**

Costituito da $18000$ valvole e $3000$ relè
- Nasce negli Stati Uniti per calcolare le tabelle per il puntamento dell'artiglieria pesante
- Basato su aritmetica decimale, era programmabile tramite interruttori multi-posizione
- L'input/output era possibile attraverso schede perforate

Queste macchine sono tutte [[../Definizioni/Definizioni_Architettura#Macchine Turing Complete|Turing Complete]]

### IAS - 1952
Denominata macchina di **Von Neumann** rappresenta uno dei più importanti punti di riferimento dell'ingegneria informatica
- La sua *architettura* è tuttora alla base della maggior parte dei *calcolatori digitali*
- L'idea fondamentale è quella di memorizzare anche i *programmi*, riducendo i tempi di programmazione

### IBM 701 - 1953
È il primo computer prodotto da *IBM* 
- *IBM* diventò nei dieci anni seguenti, leader del mercato.


## Generazione $II$
---
>[!info] Transistor
>Il ***transistor*** fu inventato nel 1948 ai Bell Labs e fruttò ai suoi inventori il premio Nobel per la Fisica
>Un transistor è un semiconduttore usato per amplificare o alternare segnali elettrici
>- È uno dei componenti base per la costruzione di dispositivi elettronici

### PDP
#### PDP-1 1960
Prodotta dalla *DEC* rappresenta il primo ***minicalcolatore***
- Il progetto basa il suo punto di forza non tanto sulla potenza ma sul prezzo
	- Infatti il **PDP-1** era oltre 10 volte meno costoso della macchina più potente di quel momento
	- Era solo due volte più lento
- Era dotato di un *display grafico*, venne sviluppato il primo ***videogioco*** della storia: ***Spacewar***

#### PDP-8 1965
Molto più economico della versione precedente
- Presenta una grande innovazione: Il ***BUS***

>[!tip] `BUS`
>Il `BUS` è un insieme di fili usato per collegare i componenti di un calcolatore

### CDC 6600 - 1964
Realizzato dalla CDC (*Control Data Corporation*)
- Rappresenta la prima macchina parallela della storia
- Al suo interno coesistevano *diverse unità funzionali* preposte a compiti diversi
- **Dieci volte più potente** della macchina più veloce del tempo

### Elea 9003 - 1957/1959
In questo periodo, l'italiana *Olivetti*
- Sotto la guida di Adriano
- Sviluppò uno dei primi mainframe computer a transistor
- *Olivetti* era un'azienda molto innovativa e temuta dalle grandi aziende come *IBM*

### Programma-101 1965
Considerato il primo *desktop coputer programmabile*
- Ebbe molto successo e la NASA ne acquistò 45

## Generazione $III$
---
>[!info] Circuiti Integrati
> Un ***circuito integrato*** è un piccolo dispositivo elettronico costituito da numerosi componenti elettronici *interconnessi*, come transistor, resistor e capacitor.
> Permisero di inserire dozzine di transistor in una singola piastra di silicio
> - Favorirono la costruzione di calcolatori più piccoli, veloci e meno costosi

### IBM 360 - 1962
Rappresenta la prima famiglia di calcolatori
- Esistevano 4 modelli con prestazioni via via crescenti
- Importante innovazione è la ***Multiprogrammazione***

>[!tip] Multiprogrammazione
>Possibilità di avere più programmi in memoria, cosicché, mentre si aspettava il completamento dell'input/output, si poteva eseguire un altro programma

## Generazione $IV$
---
>[!info] Very Large Scale Integration
>Nel 1970 *Intel* progetta il primo microprocessore della storia, **Intel 4004**, progenitore della famiglia `x86`
>I progressi della tecnologia hanno permesso di integrare su un singolo chip un numero sempre crescente di transistor
>- Una `CPU` moderna ne contiene circa 10 miliardi
>- Riducendo enormemente il costo dei calcolatori
>	- Inizia l'era dei **personal computer**

- Uno dei passi più grandi nel campo dell'informatica è stato il passaggio dell'architettura da `32` a `64 BIT` 
### IBM 5150 - 1981 
Primo personal computer con `CPU` Intel 8088 e sistema operativo `MS-DOS`
- Raggiungerà una diffusione enorme
- Unica differenza è il bus a 8 `BIT` rispetto al bus a 16 `BIT`  dell'8086

### Altre Società
Sorsero numerose altre società tra cui:
>[!tip] Commodore

Il Commodore 64 è il modello di computer più venduto al mondo
- Ne furono venduti più di 10 milioni di esemplari in tutto il mondo solo nel 1986

>[!tip] Apple

L'unica società che è sopravvissuta, grazie al successo del Macintosh
- Primo computer con una `GUI` simile a quelle odierne

## Generazione $V$
---
>[!info] Obiquitous Computing
>Quella che possiamo oggi definire la generazione $V$ di computer è legata soprattutto alle **forti riduzioni di dimensioni** e **integrazioni in altri oggetti**

### Sistemi Embedded
Sono i cosiddetti "**computer invisibili**" in quanto integrati all'interno di altri apparati
- Elettrodomestici
- Giocattoli
- Orologi
- Carte di Credito