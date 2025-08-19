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
>Un ***raster device*** è composto da una matrice rettangolare di `pixel`.

La ***risoluzione*** di un dispositivo raster misura la densità dei `pixel`:
- È il numero di pixel su unità di distanza o area (`ppi` - *inch*, `ppc` - *centimeter*)

La ***risoluzione display*** è il numero di `pixel` in ogni dimensione (es. $1929\times 1080$)

La ***dimensione fisica*** di un dispositivo raster è la larghezza $\times$ altezza del dispositivo.

$$
\text{dimensione fisica}=\displaystyle{\frac{\text{risoluzione display}}{\text{risoluzione}}}
$$

> Dispositivi con la *stessa dimensione fisica*, ma *risoluzione diverse* risulta in un dimensionamento differente del singolo pixel.

