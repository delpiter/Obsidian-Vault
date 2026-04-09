>*Per potere dire cosa deve fare una [[La CPU|CPU]] sono necessari dei dispositivi di Input/Output*
## I Monitor
---
### I Monitor LCD
>[!info] *L*iquid *C*rystal *D*siplay
>I monitor `LCD` sono il sostituto del `CRT` (***C***athode ***R***ay ***T***ube)
>Forniscono una ***qualità grafica superiore*** rispetto ai `CRT` e hanno un *ingombro e peso inferiore*

#### Funzionamento
>*I cristalli liquidi sono **molecole organiche vischiose** che scorrono in un liquido, ma come i cristalli sono anche dotate di una struttura spaziale*

>[!tip] Polarizzazione

Utilizzando un **campo elettrico** per modificare l'***orientamento delle molecole***
- Si fanno variare le *proprietà ottiche dei cristalli* e quindi l'***angolo di polarizzazione*** della luce che li attraversa

#### Composizione
>*Uno schermo `LCD` è composto da numerose celle nelle quali sono intrappolati i cristalli*

>[!abstract] Contatti Elettrici
>Ogni cella è provvista di ***contatti elettrici***:
>- In modo da poter applicare un *campo elettrico* al liquido che contiene

>[!abstract] Schermi Polarizzatori
>Le celle sono contenute all'interno di due ***schermi polarizzatori***
>- Lungo gli assi perpendicolari tra loro

>[!abstract] Luce
>Una ***luce*** posizionata dietro la lastra posteriore

![[attachements/LCDPanel.png]]

>[!done] RGB
>In uno schermo `LCD` a colori, ogni cella viene divisa in tre sezioni
>1. Una con un filtro ***Rosso***
>2. Una con un filtro ***Verde***
>3. Una con un filtro ***Blu***

#### Matrice Attiva / Passiva

>[!info] Matrice Passiva
>Usata nei primi modelli degli schermi `LCD`
>La ***struttura a matrice passiva*** prevede un gruppo di contatti per ***ogni riga e colonna*** dello schermo, invece che una cella per ogni `PIXEL`
>>[!fail] Svantaggi
>>Può essere controllato un solo `PIXEL` alla volta
>>- Gli altri `PIXEL` devono *ricordare il loro stato* fino a che il **circuito di controllo** non si dedichi nuovamente a loro
>>Come conseguenze ci sono:
>>- Problemi di ***Persistenza***
>>	- Scie lasciate da *oggetti* in *moviemento*
>>- ***Diafonia*** 
>>	- *Diffusione laterale della luce* in parti molto luminose su sfondi scuri


>[!info] Matrice Attiva
>A ogni `PIXEL` dello schermo è associato un `TFT` (***T***hin ***F***ilm ***T***ransistor) realizzato con un substrato di materiale *semiconduttore* trasparente depositato sulle superfici interne dei vetri contenenti i **cristalli**
>Questo dispositivo ***memorizza lo stato elettrico*** di ogni `PIXEL` dello schermo mentre altri `PIXEL` vengono aggiornati
### Altre Tecnologie
>[!help] ***O***rganic ***L***ight-***E***mitting ***D***iode

- Ogni `pixel` emette luce autonomamente, più sottili e flessibili degli `LCD`.

>[!check] Mini-LED
- Offre un **contrasto** più elevato e una migliore *gestione delle zone scure*.

>[!info] *A*ctive *M*atrix *O*rganic *LED*

`AMOLED` è la tecnologia più recente utilizzata.
- È costituita da led organici che *emettono la luce* invece di bloccarla

## Il Mouse
---
>*È la periferica di puntamento più diffusa, resa popolare dalle `GUI` point & click, introdotte da Apple*

>[!tip] Modello Meccanico
>Nei ***modelli meccanici***, una sfera fa girare due *rotelle* *forate* *ortogonalmente* tra loro
>La loro *velocità di rotazione* è misurata da ***sensori a infrarossi*** e trasmessa al calcolatore

![[attachements/BallMouse.png]]

>[!hint] Modello Ottico
>I primi ***mouse ottici*** utilizzavano un `LED` e un *trasduttore ottico-elettrico* per rilevare il ***movimento relativo*** alla superficie
>>[!fail] Limitazione
>>Questi mouse potevano essere usati unicamente su ***speciali superfici metalliche*** con rete di sottili linee blue e grigie
>
>Venne introdotto successivamente un ***chip per l'elaborazione dell'immagine*** per supportare un maggior numero di superfici

>[!abstract] Modello Laser
>I ***mouse laser*** sono essenzialmente mouse ottici che utilizzano un ***laser*** al posto di un `LED` per l'illuminazione del piano d'appoggio
>Si ha una *maggiore risoluzione* nell'acquisizione dell'immagine

## Le Stampanti
---
>*La stampante è uno dei principali dispositivi di output*

>[!info] Tipi di Stampante
>>[!tip] Stampante a Matrice
>>Basate su una testina mobile contenente da $2$ a $24$ ***aghi*** azionati ***elettromagneticamente***.
>>La qualità di stampa varia a seconda del *numero di aghi* e dalla possibilità di poter *sovrapporre la loro immagine*
>
>>[!tldr] Stampante Laser
>
>>[!abstract] Stampante a Getto d'inchiostro

Il livello di definizione di una stampa si misura in `DPI` (***D***ots ***P***er ***I***nch)
- Indica il numero di punti distinti disegnabili in un segmento di lunghezza di $1$ pollice
- $1$ pollice $= 2.54cm$

### Stampanti a Getto di Inchiostro
>*In questo tipo di stampante la testina mobile contiene 4 cartucce di colori*

>[!info] ‎ 
>Le immagini per luce riflessa assorbono certe lunghezze d'onda e ne riflettono altre
>Queste vengono create dalla superimposizione dei $3$ ***colori primari sottrattivi***
>Quasi tutti i sistemi di stampa sfruttano questo principio utilizzando la *combinazione*
>- ***C***yan ***Y***ellow ***M***agenta bla***K***
>Il *nero* viene aggiunto poiché è difficile ottenere degli *inchiostri puri* da assorbire tutta la luce e produrre il colore nero

![[attachements/CYMK.png]]
#### Modelli
>[!abstract] Piezoelettrici
>Nei modelli ***Piezoelettrici*** un cristallo che opera come "*tappo*" si deforma quando gli si applica una *tensione* e fa fuoriuscire una gocciolina

>[!abstract] Bubble Jet
>Nei modelli ***termici o Bubble Jet*** all'interno di ogni *ugello* una goccia di inchiostro viene riscaldata ***fino all'ebollizione***
>L'ebollizione comporta lo "***scoppio***" della goccia e la sua fuoriuscita dall'*ugello*
>**Raffreddandosi** l'ugello crea una *depressione* che *risucchia* un'altra goccia di inchiostro

La qualità di stampa varia dai $300$ `DPI` fino a oltre i $4000$ `DPI`
### Stampanti Laser
>*Le stampanti laser usano una tecnologia simile a quelle delle fotocopiatrici*

![[attachements/LaserPrinter.png]]

>[!done] ‎Funzionamento
>1. Il tamburo viene ***caricato elettricamente*** e ricoperto di materiale *fotosensibile*
>2. Tramite uno ***specchio ottagonale*** viene fatta passare una luce laser sul **tamburo**
>	- I punti colpiti dal raggio *perdono la carica elettrica*
>3. Ruotando, il **rullo** raggiunge il **toner**, i punti elettricamente carichi attirano il materiale
>	- Il toner è un contenitore di ***polvere elettrostaticamente sensibile***
>4. Una serie di ***rulli riscaldati*** fissa il materiale colorante sulla carta
>5. Il rullo viene **scaricato** e **pulito** dai *residui*

Le stampanti laser possono creare punti neri o punti bianchi
- Per raffigurare immagini a livello di grigio è necessario rappresentare le diverse intensità di grigio

>[!abstract] Soluzione

La soluzione più diffusa si chiama ***halftoning***
- Si ***suddivide*** l'immagine in celle di $6\times6$ `PIXEL`
- In base al ***livello di grigio medio*** della cella verranno *lasciati bianchi* un numero diverso di `PIXEL`

#### Stampanti Laser a Colori
>[!info] Single Pass
>$4$ toner $+$ $4$ tamburi

>[!info] Multi Pass
>$4$ toner $+$ $1$ tamburo sul quale il ***foglio passa $4$ volte*** a seguito di caricamento con i diversi toner
>>Più lento e più impreciso

