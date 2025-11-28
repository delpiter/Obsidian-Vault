> Nei primi *computer* (anni 60') la [[La CPU|CPU]] era responsabile anche dell'intera fase di [[Rendering Graphics Pipeline|rendering]].

Verso la fine degli anni 70' alle `CPU` vengono affiancati dispositivi *special purpose* chiamati ***Display Processor Unit***.
- Si occupavano del **refresh del monitor** ed erano collegati a `CPU` e *video*.

Con la diffusione dei ***PC***, il peso economico del mercato dei *videogiochi* spingeva affinché l'interactive rendering arrivasse sui **PC** a prezzi contenuti.

>[!hint] Graphics Processing Unit
>La [[Schede Grafiche|GPU]] è un chip grafico facilmente integrabile nei comuni ***PC***.

In questo modo le `GPU` sono progettate *specificatamente per la grafica*.
- Le `GPU` risultano molto più veloci nell'elaborazione di ***graphic task*** rispetto alle `CPU`.

## Evoluzione della Pipeline
---
### Fixed Function Pipeline
>[!definizione]
>Una ***Fixed Function Pipeline*** è una pipeline non programmabile, in cui il programmatore interagisce con la pipeline via interfaccia software standard ([[Il Sistema Grafico#Interazione tra Software e Hardware|OpenGL o DirecrX]]).

Una pipeline non programmabile implementa gli algoritmi di [[Rendering Graphics Pipeline|rendering]] ***direttamente nella scheda grafica***.

![[FixedFunctionPipeline.png]]

>[!done] Pro

-  Elevate ***prestazioni***

>[!fail] Contro

- ***Limitato controllo*** su come l'hardware crea l'immagine finale.
- **Non** permette ***flessibilità*** negli effetti di resa grafica.

>[!info] Offline-Rendering
>L'***off-line rendering***, a differenza del ***real-time rendering***, si avvaleva di general purpose `CPU` che costruivano *frame by frame* le animazioni impiegando ***giorni o settimane***.
>>[!check] Conclusione
>>L'***off-line rendering system*** pecca di *scarsa velocità* ma ottiene rendering di ***alta qualità e realismo***.

### Programmable Pipeline
> Era necessaria una `GPU` in cui le diverse fasi della *pipeline* fossero programmabili.

>[!tip] Shader Unit
>Le ***shader unit*** sono unità computazionali che possono essere ***riprogrammate***.

Si sono cominciate a inserire nelle `GPU` le *shader units*.

>[!definizione] Programmable Pipeline
>Una ***Pipeline Programmabile*** significa libertà di implementare vari tipi di algoritmi:
>- *Modelli di Luminosità*
>- Generazione di *coordinate texture*
>- *Trasformazioni non Lineari*

Si hanno due distinte unità programmabili:
- ***Vertex Processor*** per la manipolazione della [[Rendering Graphics Pipeline#Geometry Stage|geometria]].
- ***Fragment Processor*** per la manipolazione della [[Rendering Graphics Pipeline#Rasterization|rasterizzazione]].

![[ProgrammablePipeline.png]]

#### Vertex Shader
>[!definizione]
>Un ***vertex shader*** è un programma che prende in *input* una serie di informazioni su un **vertice** della scena e da in *output* un la posizione del vertice nel sistema di *coordinate di vista*.

La *shader unit* può modificare i dati in uscita variando i parametri necessari a specificare le operazioni di trasformazione e illuminazione del [[Rendering Graphics Pipeline#Geometry Stage|geometry stage]].

I ***vertex shader*** aprono la strada per una vasta gamma di effetti, che prima dovevano essere elaborati nel [[Rendering Graphics Pipeline#Application Stage|livello applicativo]].
- Come *deformazioni della geometria* (oggetti semi rigidi spostati dal vento o **fluidi**) o distorsioni come la *rifrazione della luce*.

#### Fragment Shader
>[!definizione]
> I ***fragment shader*** prendono come **input** gli **output** del *vertex shader* producono un *colore finale* e una trasparenza come output.

## Architettura GPU
> Per ogni fase di elaborazione della [[Rendering Graphics Pipeline|pipeline]] le `GPU` contengono diverse centinaia ***unità di elaborazione identiche***.

>[!info] Shader Processing Unit
>Le ***shader processing unit*** sono *unità di elaborazione identiche* che hanno una propria area di memoria temporanea e propri ***registri interni***.

A ciascuna unità è assegnato un *diverso elemento nel buffer* di origine:
- Quando un numero sufficiente di processing unit è pronto tutti i dati sono ***elaborati contemporaneamente***.

Questa architettura è molto efficiente perché l'*esecuzione di un numero elevato di elaborazioni uguali* è molto comune nella pipeline grafica.

![[GPUArchitecture.png]]

> Architettura di tipo [[Istruzioni IA-32 Speciali#Istruzioni MMX|SIMD]].
- Dato uno stream di dati in ingresso, essa applica la ***stessa operazione a tutti i dati***.

## Ultima Evoluzione
---
> Vengono introdotti *shaders unificati*.

>[!failure] Unified Shader
>Invece di usare processori separati specifici per gestire esclusivamente **vertex shaders**, **geometry shaders** e **pixel shaders**, si è introdotta un'architettura "***unified shader***".
>Una grande griglia di processori paralleli [[Numeri Floating-Point|floating-point]], sufficientemente generali da gestire ***i carichi di tutti gli shader***.

#### General Purpose GPU
>[!info] GPGPU
>`GPGPU` è un termine che indica tutte le tecnologie usate per ***accedere alla potenza di calcolo*** delle moderne *periferiche grafiche* e usarle per effettuare pesanti operazioni su *dati matematici e scientifici*.

>[!example] Esempi

- *Previsioni* meteo
- *Analisi* delle **immagini** medicali
- Astrofisica
- ***Reti neurali***
- Ricerche oceanografiche
- Fisica delle Particelle
- Chimica quantistica
- *Crittografia*
- etc...