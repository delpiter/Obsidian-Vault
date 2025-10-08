>[!info]
>Stadio della [[Rendering Graphics Pipeline]] che può essere vista come una pipeline di [[Sistemi di Riferimento#Trasformazioni Geometriche|trasformazioni geometriche]] o *trasformazioni di sistemi di coordinate*.

Definita una ***camera virtuale*** e una ***scena tridimensionale***, la pipeline di rendering costruisce una *serie di trasformazioni* che **proiettano** la scena tridimensionale in un'immagine in una finestra contenuta nello schermo bidimensionale.

> Un *modello geometrico* è trasformato mediante trasformazioni:
- Di **modellazione**.
- Di **vista**.
- Di **proiezione** e **viewport**.

## Step del Geometric Stage
---
>[!failure] World Coordinate System

Inizialmente il modello geometrico viene creato nello ***Spazio Locale del Modello***.
- Viene posizionato e orientato in scena nel `WCS` (*World Coordinate System*) tramite ***trasformazioni di modellazioni sui vertici*** del modello.

>[!hint] View Coordinate System

Non tutti i modelli sono "*visti*" dalla camera
- Tutti i modelli sono trasformati tramite una ***trasformazione di vista*** nel **camera frame** (`VCS`-*View Coordinate System*).

>[!tip] Volume Canonico

Solo una porzione del ***volume di vista*** contiene la scena visibile.
- Il sistema elabora la trasformazione di proiezioni per trasformare il volume di vista in un **cubo** (*volume canonico*) di lato $2$ e diagonale di estremi: $(-1,-1,-1), \ (1,1,1)$.

> Questa operazione serve per semplificare le operazioni di clipping #addLink .
- Solo le primitive **interne al volume** sono passate all'ultima trasformazione.

>[!caution] Proiezione Ortogonale

Viene poi effettuata una *proiezione ortogonale* su una ***faccia del cubo***.
- La proiezione conserva le coordinate $x$ e $y$, e memorizza la coordinata $z$ nel `z`-buffer.

>[!tldr] Screen Mapping

Converte le coordinate $x,y$ di ogni vertice, in coordinate espresse in `pixel`.
- *Device Coordinate System* (`NDC`-*Normalized Device Coordinate*).

 Queste coordinate forniranno l'input per lo **stadio successivo della pipeline**.

#### Riassunto
1. Composizione degli oggetti nel ***world coordinate system***.
2. Trasformazione di coordinate dal `WCS` al `VCS` (*punto di vista dell'osservatore*).
3. Trasformazione del volume di vista nel **volume canonico**.
4. **Clipping** dei modelli che risultano all'*esterno* del cubo canonico.
5. Proiezione ortogonale `3D` su un piano immagine `2D`.
6. ***Trasformazione di viewport***, trasforma l'immagine nella window in coordinate `pixel` *viewport*.

![[GeometryStage.png]]

### Trasformazioni di Modellazione
> Ogni oggetto è definito in un suo sistema di coordinate, `OCS` (*Object Coordinate System*).

Le [[Sistemi di Riferimento#Trasformazioni Geometriche|trasformazioni di modellazione]] permettono di muovere, orientare e trasformare i modelli all'interno di un sistema di riferimento comune `WCS`.

>[!example] Trasformazioni
>Le trasformazioni necessarie sono queste:
>- [[View Transform]]
>- [[Projection Transform]]
