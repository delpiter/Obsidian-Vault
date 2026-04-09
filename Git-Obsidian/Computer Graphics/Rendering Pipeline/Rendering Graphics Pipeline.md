> La [[../../Architettura degli Elaboratori/Architettura del Calcolatore/Schede Grafiche|GPU]] ha una architettura a pipeline, poiché progettata per soddisfare la ***rendering*** pipeline.

>[!definizione]
>La ***Rendering Graphics Pipeline*** è una [[../../Architettura degli Elaboratori/Architetture a Confronto/Pipelining|pipeline]] che prende in input un insieme di *primitive geometriche* `3D` e le trasforma in una *immagine raster* visualizzabile su un [[../Il Sistema Grafico#Raster Devices|dispositivo raster]].

I vari stadi possono essere accorpati in tre:
- ***Application***
- ***Geometry***
- ***Rasterizer***

![[attachements/GraphicsRenderingPipeline.png]]

### Application Stage
> L'application stage gira sulla [[../../Architettura degli Elaboratori/Architettura del Calcolatore/La CPU|CPU]].

>[!help] Concetto
>L'***Application Stage*** costruisce una geometria in base ad input forniti dall'utente e produce in output *poligoni*, o *mesh di poligoni*.

La maggior parte dei sistemi grafici in tempo reale presuppone che tutto sia fatto di ***triangoli***.
- Lo sviluppatore utilizza una [[../Il Sistema Grafico#Interazione tra Software e Hardware|libreria grafica]] per fornire ogni **triangolo** alla pipeline un *vertice alla volta*.

### Geometry Stage
> Il ***geometry stage*** si compone di *diversi stage*.

>[!caution] Model & View Transformations
>Si trasformano tutti gli oggetti in un ***sistema di coordinate comune***.

>[!tldr] Vertex Shading & Illumination
>Una volta che ogni triangolo è in un sistema globale di coordinate, si può calcolare il suo [[../Luce e Colori|colore]] in base alle *luci nella scena*.

>[!abstract] Projection
>Consiste nella *proiezione* del volume di vista che contiene la scena in un ***volume canonico***.

>[!hint] Clipping (Visibility Culling)
>Nella fase di ***clipping*** vengono eliminate tutte le superfici esterne al *volume di vista canonico*.

>[!check] Screen Mapping
>Trasforma in *coordinate dello spazio dello schermo*.
>- Le primitive sono ora in `2D` e si può passare alla ***rasterizzazione***.

### Rasterization
>[!failure] Scan Conversion 
>Il processo di ***Scan Conversion*** consiste nel determinare i `pixel` dello schermo interni ad ogni **triangolo** *visibile sullo schermo*.

Questa fase genera "*frammenti*"
- Un ***frammento*** è un insieme di `pixel` che corrisponde al **triangolo** appena trasformato.

>[!tip] Fragment Processing
>I ***frammenti*** hanno una posizione e altri attributi come colore e coordinate di texture che vengono determinati [[../../Metodi Numerici per L'Intelligenza Artificiale/Interpolazione/Interpolazione Polinomiale|interpolando]] i valori sui *vertici*.
