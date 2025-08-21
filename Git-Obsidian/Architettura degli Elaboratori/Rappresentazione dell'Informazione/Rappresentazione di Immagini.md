> L'immagine di un video è rappresentata tramite una griglia o matrice di **pixel** 
> (***PI***cture ***EL***ement) di ognuno dei quali è memorizzata l'intensità luminosa e/o il colore


![[pixelGrid.png]]
##### Parametri importanti
- ***Dimensione*** (*Risoluzione*)
- ***Profondità***
- ***Formato di Rappresentazione*** (*Grayscale*, `RGB` , *Palette*)

## Codifica di Immagini
---
>[!tip] Tipi di Codifica
>Per *digitalizzare* immagini ci sono diverse modalità:
>1. Codifica *Grayscale*
>2. Codifica *RGB*
>3. Codifica con un numero *arbitrario* di colori
>4. Codifica tramite *Palette*

### Codifica Grayscale
>[!info] Immagini a scala di grigi
>Ogni pixel è codificato con un `BYTE`, rappresentabili $256$ livelli di grigio

 Livello $0\to$ Corrisponde al colore nero
 Livello $255\to$ Corrisponde al colore bianco

  >[!done] Occupazione di memoria
  
  Un'immagine di dimensioni $W\times H$ occupa $W\times H$ `BYTES`

### Codifica RGB
>[!info] Immagini *Red, Green, Blue*
>Ogni pixel dell'immagine è codificato con tre `BYTE` ciascuno dei quali specifica l'intensità di uno dei tre colori fondamentali

Il numero dei colori disponibili è $2^{24}=16.777.216$ 
-  Livello $0,0,0\to$ Corrisponde al colore nero
 - Livello $255,255,255\to$ Corrisponde al colore bianco

>[!tip] Grigio in codifica RGB
>Per codificare un qualsiasi tipo di grigio con la codifica RGB basta avere l'intensità di ogni colore uguale
>Grigio$\to x,x,x$

>[!done] Occupazione di memoria

Un'immagine di dimensioni $W\times H$ occupa $W\times H\times3$ `BYTE`.

![[RGBspectrum.png]]

### Codifica con un numero *arbitrario* di colori
>[!info] Sia $N$ il numero di `BIT` per pixel
>Il numero di colori disponibili è $2^N$
>Un immagine di dimensioni $W\times H$ occupa $(W\times H\times N)/8$ `BYTE`

### Codifica con Palette
> Per ridurre la quantità di memoria richiesta viene spesso utilizzata una **palette di colori**

>[!info] Definizione
>Una ***palette*** è una tabella che definisce $2^c$ colori, ognuno caratterizzato da una tripletta *RGB* con profondità di $p$ `BIT`, e associa a ciascun colore un **indice** (posizione nella *palette*)

In un immagine codificata con una *palette* il colore di ogni pixel è definito dall'indice del colore nella *palette* 
- Sono necessari $c$ `BIT` invece di $p$ `BIT` per ogni pixel
- In questo modo in un'immagine, pur potendo utilizzare un numero massimo $2^c$ di colori diversi, questi potranno essere scelti da un insieme molto più ampio ($2^p$)
