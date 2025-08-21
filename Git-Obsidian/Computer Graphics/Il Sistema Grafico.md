>[!info] Sistema Grafico
>Il ***sistema grafico*** è l'insieme di *dispositivi hardware*, e *programmi software* che concorrono alla creazione, manipolazione e visualizzazione di [[Git-Obsidian/Computer Graphics/Introduzione|immagini digitali]].

I ***dispositivi hardware***:
- Rappresentano la *potenzialità del sistema grafico*, forniscono la potenza di calcolo e le interfacce necessarie per produrre immagini.

Il ***software***:
- Utilizza le risorse dell'hardware per eseguire operazioni come *creazione* e *modifica* di **immagini grafiche**.


### Interazione tra Software e Hardware
>[!caution] Application Model

È la parte del software che contiene i *dati e le informazioni* necessarie per creare le immagini o [[Git-Obsidian/Computer Graphics/Introduzione#Animazione|animazioni]].
- Potrebbe essere un modello `3D`, un'immagine, un video, etc...

>[!abstract] Application Program

È il **programma** che utilizza i dati presenti nel [[Git-Obsidian/DataBase/Introduzione#Database|database]] per creare le istruzioni che verranno inviate alla [[Schede Grafiche|scheda grafica]].

>[!tl;dr] Graphics Library

***Libreria di funzioni*** che fornisce un'*interfaccia standard* per comunicare con l'hardware grafico.
Le librerie più comuni sono:
- [OpenGL](https://www.opengl.org/)
- [DirectX](https://directx12.com/)

>[!cite] Graphics ***API***

**OpenGL** e **DirectX** forniscono un insieme di funzioni che permettono alle applicazioni di interagire direttamente con l'hardware grafico.
- Inviano istruzioni per la *creazione* e *manipolazione* di immagini e animazioni.

>[!failure] Driver della Scheda Video

Software che permettono al [[3 - Livelli del Sistema Operativo#Introduzione|sistema operativo]] di comunicare con la scheda.
- Interpretano l'output delle ***API*** e lo convertono in una forma che è riconoscibile per la scheda.

>[!example] Graphics System

È la scheda grafica, componente specializzato nell'elaborazione delle immagini.

>[!caution] Monitor e Tastiera

[[Le Periferiche|Dispositivi di input/output]] che permettono all'utente di *interagire con il sistema*.

### Raster Devices
>[!definizione]
>Un ***raster device*** è composto da una matrice rettangolare di [[Rappresentazione di Immagini|pixel]].

La ***risoluzione*** di un dispositivo raster misura la densità dei `pixel`:
- È il numero di pixel su unità di distanza o area (`ppi` - *inch*, `ppc` - *centimeter*)

La ***risoluzione display*** è il numero di `pixel` in ogni dimensione (es. $1929\times 1080$)

La ***dimensione fisica*** di un dispositivo raster è la larghezza $\times$ altezza del dispositivo.

$$
\text{dimensione fisica}=\displaystyle{\frac{\text{risoluzione display}}{\text{risoluzione}}}
$$

> Dispositivi con la *stessa dimensione fisica*, ma *risoluzione diverse* risulta in un dimensionamento differente del singolo pixel.

#### Immagini Raster e Vettoriali

>[!caution] Grafica Vettoriale
>Nella ***grafica ad oggetti*** (o *vettoriale*), un'immagine consiste di oggetti grafici (punti, linee, rettangoli, curve, etc...) ognuno dei quali è *definito da un'equazione matematica*.
>- Generalmente occupa meno spazio di un'*immagine raster*.

Per riprodurre l'immagine di un *oggetto vettoriale* su un *dispositivo raster*, questo va trasformato in `pixel`.
- Questa operazione si dice #addLink rasterizzazione (o ***scan conversion***).

Ogni oggetto del disegno viene memorizzato in un [[Git-Obsidian/DataBase/Introduzione#Database|database]] interno di oggetti grafici.

> Gli oggetti si possono **ingrandire**, **rimpicciolire**, **ruotare**, **ridimensionare**, **colorare**, senza nessuna *perdita di qualità*.

La qualità di una ***illustrazione ad oggetti*** è *device independent*.
- L'output uscirà alla **migliore risoluzione del dispositivo**.


>[!tip] Grafica Raster
> Nella ***grafica raster*** l'immagine è una griglia rettangolare di `pixel` *colorati*.

Usata nell'**elaborazione** di immagini *fotografiche*.
- I programmi di fotoritocco lavorano con *immagini raster*, il ritocco sono possibili ***punto per punto***.
>[!fail] Svantaggi

L'immagine si può ingrandire solo ***ingrandendo la dimensione del*** `pixel`.
- Si possono creare effetti sgradevoli (***pixelizzazione***).
- Operazioni come spostamento o rotazione di aree dell'immagine possono portare a perdite di qualità

![[Raster-Vector.png]]

#### Raster Scan Display System
> I sistemi grafici a ***display raster*** consistono in *tre* componenti.

>[!hint] [[Schede Grafiche|Scheda Grafica]]

>[!caution] [[Schede Grafiche#^985740|GPU]]

- Un ***microprocessore specializzato*** nel calcolo ad alta velocità di *operazioni grafiche*, come il rendering #addLink di immagini `3D`.

>[!failure] Frame Buffer

- Una memoria ad alta velocità usata per ***immagazzinare temporaneamente i dati grafici*** che devono essere visualizzati sullo schermo.
- Ogni `pixel` ha una corrispondente posizione nel *Frame Buffer*.

> *Per la visualizzazione*:
- Un [[Le Periferiche#I Monitor LCD|Monitor]] (*display raster*) connesso alla scheda grafica.
- Un ***device driver*** che funge da ponte tra il sistema operativo e la scheda grafica.

##### Generazione dell'Immagine
> Di seguito i passaggi per la generazione di una immagine raster.

1. Il **software** invia i dati alla *scheda grafica*.
2. *Elaborazione*
	- La `GPU` elabora i dati e li memorizza nel ***frame buffer*** 
3. *Visualizzazione*
	- Il contenuto del *frame buffer* viene continuamente trasferito al monitor.
4. *Aggiornamento*
	- Ogni volta che un'immagine viene modificata, il processo viene ripetuto.

Questo processo viene ripetuto circa sessanta volte al secondo (film, video).
- Per videogiochi si cerca di ripeterlo più volte possibile ($90-120$).

>[!hint] Refresh Rate
>Il *numero di frame* che vengono calcolati sullo schermo al secondo è detto ***refresh rate***, misurato in $Hz$.

>[!failure] Frame Rate
>Il ***frame rate*** (`FPS`) misura quante *immagini differenti* al secondo sono **visualizzate**.

#### Frame Buffer
>[!definizione]
>Il ***Frame Buffer*** è una *porzione della memoria* presente nella scheda video, dove vengono memorizzate le immagini prima di essere visualizzate sul display.

> Il frame buffer è una ***collezione di diversi buffer***.

>[!info] Color Frame Buffer

Il *principale* tra i buffer
- Contiene le ***componenti del colore*** per ogni `pixel`.
- Ogni cella del buffer è divisa in 3 *zone*, per i tre [[Rappresentazione di Immagini#Codifica RGB|colori in sintesi additiva]].

Il *color buffer* ha $N$ `bit` (o *piani*) per `pixel`.
- Tipicamente si fa uso di $24$ piani di `bit` per le tre componenti colore e un quarto `byte` per il ***canale alfa***.
	- Se un `pixel` ha il canale alpha a $0$, il pixel dovrà essere considerato **trasparente**.
	- Un `pixel` con il canale alpha a $1$ dovrà essere considerato **opaco**.


>[!abstract] Z-Buffer

>[!help] Double Buffer

Composto da ***front $+$ back buffer***.
- Utilizzato per velocizzare le animazioni.

Se l'immagine finale mostrata a video è contenuta nel ***front buffer***, nel ***back buffer*** è contenuta la *scena che sta per essere mostrata*.
- I due buffer vengono poi scambiati dal processore grafico.