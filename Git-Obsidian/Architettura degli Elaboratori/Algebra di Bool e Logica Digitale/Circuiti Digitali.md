>*L'output di un circuito digitale può essere descritto, oltre come [[Algebra di Bool#Da Tabella di Verità a Espressione Booleana|tabella di verità]], anche come [[Algebra di Bool#Funzione Booleana|funzione booleana]] dei suoi input*

$$
M=\overline{A}BC+A\overline{B}C+ABC
$$
![[attachements/Truth Table.png]]
*Tabella di verità $\nearrow$*

![[attachements/Truth-Table-Circuit.png]]
*Circuito associato alla tabella di verità e funzione booleana*

>[!done] Da funzione booleana a circuito digitale

1. Scrivere la ***tabella di verità*** per la funzione
2. Disporre di invertitori (`NOT`) per generare il ***complemento di ogni input***
3. Introdurre una ***porta*** `AND` per ogni termine con `1` nella colonna dell'***output***
4. ***Collegare le porte*** `AND` agli input appropriati
5. Inviare l'output di tutte le porte `AND` in ***una porta*** `OR`

>[!abstract] Dal punto di vista Hardware
>Dal punto di vista costruttivo, è preferibile realizzare un circuito utilizzando ***un solo tipo di porta logica***
>- Preferibilmente `NOR` o `NAND`

## Circuiti Integrati
---
>[!info] Descrizione
>Le porte logiche non vengono prodotte o vendute individualmente, ma in unità chiamate ***Integrated Circuit*** o più generalmente ***chip***
>>[!tldr] Definizione
>>Un circuito integrato è un pezzo rettangolare di ***silicio*** con dimensioni che variano da pochi $mm^2$ ad alcuni $cm^2$ su cui vengono realizzate le ***porte logiche***
>
>I chip sono classificabili in base al numero di porte
>- `SSI`: ***S***mall ***S***cale ***I***ntegrated $\to$ da $1$ a $10$ porte
>- `MSI`: ***M***edium ***S***cale ***I***ntegrated $\to$ da $10$ a $100$ porte
>- `LSI`: ***L***arge ***S***cale ***I***ntegrated $\to$ da $100$ a $10.000$ porte
>- `VLSI`: **V**ery ***L***arge ***S***cale ***I***ntegrated $\to$ da $10.000$ a $100.000$ porte
>- `ULSI`: ***U***ltra ***L***arge ***S***cale ***I***ntegrated $\to$ da $>100.000$ porte

### Package
>[!info] Contenitore
>I circuiti integrati vengono poi montati in contenitori plastici o ceramici detti ***package***. 
>Per utilizzare il circuito il *package* espone dei ***contatti*** su cui far passare la *corrente*

#### Tipi di Package
>[!abstract] *D*ual *I*nline *P*ackage
>`DIP`
>Utilizzato dai circuiti più semplici
>- I contatti di uscita sono realizzati in ***due file parallele***

![[attachements/Dual Inline Package.png]]

>[!tldr] *P*in *G*rid *A*rray
>`PGA`
>Utilizzato per circuiti più complessi
>- I contatti di uscita sono posizionati ***sotto forma di matrice*** nella parte *inferiore* del circuito

![[attachements/Pin Grid Array.png]]

>[!abstract] *L*and *G*rid *A*rray
>`LGA`
>Il tipo di package ***più utilizzato*** nelle moderne [[../Architettura del Calcolatore/La CPU|CPU]]
>Si tratta di un ***package*** che non fa fuoriuscire *alcun pin* dal chip, ma presenta dei ***contatti piatti*** nella parte inferiore del circuito
>- I *pin* si troveranno nella scheda su cui attaccare il ***chip***

![[attachements/Land Grid Array.png]]

>[!tldr] *B*all *G*rid *A*rray
>`BGA`
>Simile al `PGA` con al posto dei *pin* delle "*sfere*" saldate in un pattern a matrice


## Fabbricazione di Circuiti Integrati
---
>*Pochissime fabbriche nel mondo sono in grado di realizzare `ULSI` con transistor di pochi $nm$:*
- *`TSMC`: Taiwan Semiconductor Manifacture Company*
- *`Intel` e `Samsung`* 

>[!abstract] Il processo di fabbricazione prevede i seguenti passi

### Creazione dei Wafer
 ‎ 
Si fondono ***sabbie silicee*** per formare dei ***wafer***
- Su questi ***wafer*** verranno poi realizzati numerosi chip
- Su ogni ***wafer*** verranno depositati *sottili strati di materiali* diversi necessari per la produzione come:
	- ***Semiconduttori***
	- *Ossidi*
	- *Isolanti*
	-  *Metalli*

### Fotolitografia
>[!info] Descrizione
>Il processo di ***fotolitografia*** è un processo che può essere ripetuto *centinaia di volte* per chip più **complessi**

1. Il ***Wafer*** viene ricoperto con un *layer* ***fotosensibile***
2. Il *layer* ***fotosensibile*** viene esposto ad una ***luce ultravioletta*** che passa attraverso ad una *maschera* ad altissima definizione
3. Le zone illuminate ***diventano solubili*** e il *layer fotosensibile* può essere *facilmente asportato* lasciando scoperte le aree sottostanti
4. Attraverso un lavaggio chimico (***etching***) si possono rimuovere *layer sottostanti*

### Separazione dei Chip

Dato che *centinaia di chip* sono fabbricati nello stesso ***wafer***
- L'ultimo passaggio della fabbricazione è quello di separare i chip dello stesso ***wafer***

## Printed Circuit Board
---
>[!info] `PCB`
>Un `PCB` o ***P***rinted ***C***ircuit ***B***oard, è una scheda utilizzata per il *supporto meccanico* e per il *collegamento di componenti elettronici*
>È costituita da un ***substrato isolante*** come vetroresina e da uno o più ***strati conduttivi*** in rame che consentono di collegare i *componenti* tramite piste
>>[!tldr] Montaggio Tradizionale
>>Il *montaggio tradizionale* prevede ***piccole piazzole*** con *fori passanti* nelle quali sono ***saldati*** i ***piedini*** dei componenti
>
>>[!tip] Montaggio `SMT`
>>Il ***S***urface ***M***ounting ***T***echnology prevede il ***montaggio superficiale*** *senza fori* dei componenti e consente di ridurre il package degli stessi e ***automatizzare il montaggio***

## Tipologie di Circuiti Digitali
---
>*Esistono 2 tipologie di circuiti digitali*

>[!info] Circuito Combinatorio
>In un [[Circuiti Combinatori|Circuito Combinatoro]] il *valore istantaneo delle uscite* è determinato ***univocamente*** da valori degli ingressi del circuito
>>[!done] In Breve
>>L'***output*** è determinato solamente dall'***input***

![[attachements/Combinational Circuit.png]]

>[!info] Circuito Sequenziale
>In un [[Circuiti Sequenziali|Circuito Sequenziale]] il valore istantaneo delle uscite dipende, oltre che dai valori di ingresso anche dalla ***storia passata dal circuito***
>- Richiedono Temporizzazioni (***Clock***)
>- Possono essere ***sincroni*** o ***asincroni***
>- Analisi circuitale più complessa.

![[attachements/Sequential Circuit.png]]
## Porte Logiche Programmabili
---
>[!info] *P*rogrammable *L*ogic *A*rray
>`PLA`
>Il `PLA` è un chip costituito da un numero di porte ***collegate internamente*** a seconda delle necessità del progettista
>Un `PLA` è quindi in grado di calcolare funzioni booleane arbitrarie

>[!abstract] Possibilità

In un circuito con:
- $n$ ***Input***
- $m$ ***Output***
- $k$ ***Unità Interne***

>[!caution] Complemento

Di ciascuno degli $n$ input viene internamente generato il complemento (***negativo***)
- $2\times n$ linee di input intero

>[!caution] AND

Il chip contiene un array di $k$ porte `AND` a $2\times n$ input
- Ciascuna porta `AND` è *inizialmente* collegata a ***tutte*** le $2\times n$ ***linee di input***

>[!caution] OR

Il chip contiene $m$ porte `OR` a $k$ input
- Ciascuna porta `OR` è *inizialmente* collegata a ***tutte*** le $k$ uscite delle porte `AND`

### Versioni
>[!info] Fusibili
>I primi modelli di `PLA` funzionavano tramite ***fusibili***
>Il *programmatore* doveva far "*esplodere*" i **fusibili** per ottenere il circuito interessato
>>[!question] Non è meglio produrlo già programmato?
>>Per le piccole aziende che non si potevano permettere un **chip specifico**, questa era la soluzione ***meno costosa***

#### Esempio
>*$n=12, m=6,k=50$*
![[attachements/Programmable Logic Array.png]]

>[!info] `FPGA`
>***F***ield ***P***rogrammable ***G***ate ***A***rray
>Evoluzione del `PLA` con fusibile, in questo caso lo sviluppatore definisce i collegamenti via ***software***

