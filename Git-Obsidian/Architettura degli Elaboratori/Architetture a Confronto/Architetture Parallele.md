## Calcolatori Paralleli
---
>L'utilizzo in parallelo di più unità di calcolo è una soluzione progettuale che, sebbene già utilizzata da molti anni, offre ancora enormi possibilità di sviluppo

![[attachements/TypesOfParallelism.png]]
>*La figura distingue diversi tipi di parallelismo*

### Notazione
>*I fattori che caratterizzano, dal punto di vista hardware, un sistema parallelo sono i seguenti:*

>[!example] Natura e numero degli elementi di Calcolo
>Il parallelismo può essere stabilito tra semplici [[../Algebra di Bool e Logica Digitale/Arithmetic Logic Unit|ALU]] oppure tra potenti `CPU` complete

>[!abstract] Natura e numero degli elementi di Memoria
>Normalmente la memoria è suddivisa in ***moduli indipendenti*** al fine di permettervi l'accesso da più `CPU` contemporaneamente

>[!caution] Modalità di Interconnesione
>>[!question] Come sono collegate le varie unità di calcolo?
>
>Rappresenta il principale elemento di differenziazione.
>La connessione può essere:
>- ***Statica***: I legami tra le `CPU` sono determinati a priori e sono ***fissi***
>- ***Dinamica***: I legami tra le `CPU` sono definiti in base alla necessità da opportuni dispositivi in ***grado di instradare i messaggi***

Sebbene qualsiasi combinazione di queste caratteristiche sia possibile, si tendono a realizzare due tipi di sistemi:
-  Sistemi con un ***piccolo numero*** di `CPU` *indipendenti*, *grandi* e dotate di *interconnessioni a bassa velocità*
	- Sistemi "***loosely coupled***"
- Sistemi in cui il parallelismo è realizzato a ***livello di componenti più piccole*** che ***interagiscono fortemente*** tra loro
	- Sistemi "***strongly coupled***"

#### Granularità del Parallelismo
>[!info] Parallelismo *Course-Grained*
>L'elemento software che viene ***parallelizzato è grande***, per esempio un programma.
>I vari processi ***non hanno bisogno di comunicare*** fra di loro

>[!abstract] Parallelismo *Fine-Grained*
>L'elemento software che viene ***parallelizzato è piccolo***, come una singola operazione.
>I vari processi paralleli hanno ***bisogno di comunicare*** poiché stanno risolvendo lo stesso problema

### Parallelismo nel Chip
>*Distinguiamo diverse possibilità, già in parte discusse*

>[!info] Parallelismo a livello di *istruzioni*
>[[Pipelining]], [[Pipelining#Architetture Superscalari|Architetture Superscalari]], [[../Assembly/Istruzioni IA-32 Speciali#Istruzioni MMX|Istruzioni SIMD]]

>[!abstract] *Multi-Threading*
>La `CPU` ***esegue contemporaneamente due thread***.
>In casi limite il multi-threading su `CPU` può portare a peggioramento delle prestazioni

>[!example] *Multi-Core*
> Consente un vero ***multi-threading*** e permette in molti casi di aumentare notevolmente le prestazioni
> Esempio [[Alcune Architetture#Intel Core i7|Intel Core i7]]

>[!caution] Più *Core eterogenei* nel Chip
>Ingloba nello stesso chip due o più core ma con ***funzionalità specializzate***

### Coprocessori
>[!info] Definizione
>Un ***Coprocessore*** è un processore indipendente che esegue *compiti specializzati* sotto il ***controllo del processore principale***.

I piu diffusi di seguito:
#### Processori di rete
Specializzati per gestire ad altissima velocità lo ***smistamento di pacchetti che viaggiano in rete***
- Solitamente montati in schede a innesto da usare negli apparati di rete come ***router***, ma anche nei PC, come le ***schede di rete***

#### Crittoprocessori
Consentono di cifrare/decifrare molto velocemente flussi di dati con "***state-of-the-art algorithms***"
- ***Advanced Encryption Standard***, ***RSA***

#### Processori Grafici
Processori che vengono montate nelle [[../Architettura del Calcolatore/Schede Grafiche|GPU]] per consentire di ***processare grandi quantità di dati video*** e grafica 3D
- Una `GPU` può contenere fino ad alcune ***migliaia di core che operano in parallelo***

#### GPGPU Computing

>[!tldr] *G*eneral *P*urpose computing on *G*raphic *P*rocessing *U*nit

Grazie all'introduzione di linguaggi e modelli di programmazione come `CUDA` e `OpenCL`, che permettono di usare una `GPU` per applicazione di ***calcolo floating point***

### Multiprocessori
>[!info] Definizione
>I multiprocessori sono ***sistemi a memoria condivisa***, ossia sistemi in cui tutte le `CPU` condividono una ***memoria fisica comune***

![[attachements/Multiprocessor.png]]
- Qualsiasi processo può ***leggere o scrivere su tutta la memoria***
- Due o più processori comunicano ***leggendo o scrivendo in una opportuna cella di memoria***
- Presentano ***un'elevata capacità di interazioni*** tra i processori (*strongly coupled*)
- C'è una sola copia del sistema operativo in esecuzione

### Multicomputer
>[!info] Definizione
>I ***multicomputer*** hanno più `CPU` ognuna dotata di una ***propria memoria***
>Dato che ogni `CPU` può accedere solo alla propria memoria è necessario un meccanismo basato su messaggi che permetta lo ***scambio di informazioni***

![[attachements/Multicomputer.png]]
- I *multicomputer* sono normalmente sistemi ***loosley coupled***
- Richiedono un complesso sistema di routing dei messaggi lungo una ***rete di interconnessione***
- L'allocazione dei processori e dei dati è un fattore fondamentale per l'***ottimizzazione delle prestazioni***
- Su ogni `CPU` è in esecuzione una ***copia del sistema operativo***

>[!warning] Nota Bene
>Programmare un multicomputer è molto più complesso che programmare un multiprocessore
>Costruire un multiprocessore è più complesso e più costoso che costruire un multicomputer
>>[!done] In breve
>>È compito del programmatore quello di ***suddividere e scambiare operazioni***
>> Architettura molto più ***scalabile***, ***facile*** da realizzare, ma la ***programmazione è molto complessa***


#### Reti di Connessione
>*La topologia usata per realizzare la rete di connessione tra le diverse `CPU` caratterizza fortemente la capacità di comunicazione*

Sono possibile svariate soluzioni caratterizzabili in base alle caratteristiche seguenti:

>[!info] Grado o Fanout
>Rappresenta il ***numero di archi collegati ad un nodo***
>Determina la ***fault tollerance*** della rete, ossia la capacità di continuare a funzionare anche se il link fallisce nella sua *operazione di routing*

![[attachements/Fanout.png]]

>[!info] Diametro
>Rappresenta la ***distanza tra i due nodi più distanti del grafo***, espressa come *numero di archi da percorrere* per passare da un nodo all'altro
>Da informazioni sul tempo di comunicazione (***caso peggiore***)

![[attachements/Diameter.png]]

##### Topologie di Rete
![[attachements/Topology1.png]]
>*a) Topologia a stella, b) Topologia a interconnessione completa (maglia)*

![[attachements/Topology2.png]]
>*c) Topologia ad albero o stella estesa, d) Topologia ad anello*

![[attachements/Topology3.png]]
>*e) Topologia a griglia, f) Topologia a toroide 2D*

![[attachements/Topology4.png]]
>*g) Topologia a cubo, h) Topologia a Ipercubo*

![[attachements/Toroide3D.png]]
>*Topologia toroide 3D*

Una delle topologie di rete ***più utilizzata nei supercomputer*** con decine di migliaia di nodi
- È un buon compromesso tra ***diametro e numero di interconnessioni***
![[attachements/FatTree.png]]
>*Topologia "Fat Tree"*

I rami più vicini alla radice sono più "*grassi*", offrono una maggiore ***larghezza di banda***
- Più il ***rischio di traffico*** è alto, più è aumentata la larghezza di banda

### Parallelismo e Prestazioni
>[!question] Di quanto accelera l'esecuzione del programma se uso $n$ `CPU`?

Ottenere l'accelerazione ottima è ***praticamente impossibile***:
- Esistono parti dei programmi ***intrinsecamente sequenziali***
- La comunicazione tra i processi ***comporta dei ritardi***
- Gli algoritmi paralleli sono spesso ***sub-ottimi*** rispetto ai sequenziali

>[!tldr] Lo speed-up di un programma può essere calcolato come:
>$$Speedup=\frac{n}{1+(n-1)\cdot f}$$
>$$T_{es.paral}=f\cdot T_{es.seq}+\displaystyle{\frac{(1-f)\cdot T_{es.seq}}{n}}$$
>Dove: 
>- $f$ è la percentuale del programma che ***non sono riuscito a parallelizzare*** (*% sequenziale*)
>- $T$ è il tempo di esecuzione su un ***sistema monoprocessore***
>- $n$ è il numero delle `CPU`

![[attachements/Speed-up.png]]

Per raggiungere prestazioni elevate non è sufficiente aumentare il numero delle `CPU`
- È necessario utilizzare ***architetture [[../../Definizioni/Definizioni_Architettura#Scalabilità|scalabili]]***

>[!fail] Il parallelismo perfetto non può essere raggiunto a causa dell'aumento del *diametro della rete*
>L'ipercubo rappresenta la soluzione ottimale poiché il diametro ***aumenta logaritmicamente*** rispetto al numero dei nodi

### Classificazione di sistemi Paralleli
>*Non esiste una classificazione universalmente riconosciuta*

La tassonomia più utilizzata è quella proposta da ***Flynn*** che si basa su due concetti principali

>[!abstract] Sequenza di istruzioni
>Insieme di istruzioni associate a un ***program-counter***

>[!tip] Sequenza di Dati
>Insieme di ***operandi***

![[attachements/Classificazione di sistemi Paralleli.png]]

![[attachements/Flynn Taxonomy.png]]