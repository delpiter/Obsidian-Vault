## Computer Graphics
---
>[!definizione]
>Per ***computer graphics*** si intende la disciplina informatica che consiste nella creazione e manipolazione di *immagini sintetiche*.

È un insieme di tecniche di produzione di scene rappresentanti *oggetti* del ***mondo reale*** o ***astratti***, a partire da una loro **rappresentazione matematica**.

## Pilastri della Computer Graphics
---
>[!check] Modellazione #addLink

***Geometrica***:
- Creazione di *rappresentazioni matematiche* di oggetti `3D` (poligoni, curve. etc...).

***Procedurale***:
- Generazione di *forme complesse* attraverso algoritmi e regole (frattali, sistemi particellari).

***Physics-Based***:
- *Simulazione* di materiali e comportamenti fisici (Tessuti, liquidi, etc...).

>[!tldr] Illuminazione e Texturing #addLink

***Fonti Luminose***:
- Simulazione di diverse *tipologie di luce*.

***Materiali***:
- Definizione delle proprietà dei *materiali* (Riflessione, rifrazione, diffusione).

***Ombreggiatura***:
- Calcolo dell'interazione tra *luce e superfici*.

***Texture***:
- Applicazione di *immagini alle superfici* per simulare dettagli e materiali.

>[!failure] Rendering #addLink

***Rasterizzazione***:
- *Trasformazione* di una scena `3D` in un'immagine `2D`, *pixel* per *pixel*.

***Ray Tracing***: #addLink
- Simulazione del *percorso della luce* attraverso una scena per ottenere immagini fotorealistiche.

***Path Tracing***:
- Estensione del *Ray-Tracing*, per una simulazione più accurata della luce.

## Alcuni Concetti
---
### Rigging
>[!info]
>Il **rigging** consiste nell'aggiungere ad un modello una sorta di "*scheletro virtuale*", composto da ossa e giunture.

Le ossa sono **collegate alla mesh del modello** attraverso dei pesi che definiscono quanto ogni parte della mesh sarà influenzata dal movimento di un osso.

![[Rigging.png]]

### Scena e Camera
>[!info]
>È come un ***palcoscenico teatrale digitale***, dove vengono posizionati e organizzati tutti gli elementi che compongono l'*immagine finale*.

Le telecamere forniscono la visione del mondo `3D` *virtuale*.
- Inquadrano ogni immagine per indicare dove guardare.
>[!hint] Posizionamento
>Il ***posizionamento della telecamera*** determina ciò che l'osservatore *vede* nella scena.

### Animazione
>[!info]
> L'***animazione*** è una serie di immagini, ognuna leggermente diversa dalla precedente.

Se mostrate *abbastanza velocemente*, smettiamo di vedere le singole immagini e vediamo invece un'***illusione di movimento***.

#### Modalità di Animazione
L'animazione avviene *muovendo le ossa* dello [[#Rigging|scheletro virtuale]].

> ***Keyframing***

- Definizione dei ***punti chiave*** di un'animazione e [[Interpolazione Polinomiale|interpolazione]] tra di essi.

> ***Fisica***

- Simulazione di *movimenti realistici* sotto l'azione di [[Leggi di Newton#Seconda Legge di Newton|forze]].
