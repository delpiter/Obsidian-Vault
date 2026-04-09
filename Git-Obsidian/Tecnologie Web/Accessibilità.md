## Definizioni
---
>[!cite] Definizioni
>Ai fini della presente legge, si intende per:
>>[!quote] Accessibilità
>> La *capacità* dei sistemi informatici, nelle forme e nei limiti consentiti dalle conoscenze tecnologiche, di **erogare servizi** e fornire informazioni ***fruibili***, *senza discriminazioni*, anche da parte di coloro che a causa di disabilità necessitano di tecnologie assistive o configurazioni particolari. 
>
>>[!caution] Tecnologie Assistive
>>Gli **strumenti** e le **soluzioni tecniche**, hardware e software, che permettono alla persona disabile, superando o riducendo le condizioni di svantaggio, di ***accedere alle informazioni*** e ai servizi erogati dai sistemi informatici.

> Due tipologie di utenti traggono beneficio da una tecnologia accessibile:
- Utenti con ***disabilità***.
- Utenti che usano *diverse tecnologie*.
>[!hint] Curbcut Effect
>Si dice che un prodotto ha il ***Curbcut Effect*** quando i benefici del prodotto accessibile si può estendere ad altre tipologie di utenti.

### Soluzioni Tecnologiche
> Si opera in due direzioni

>[!failure] Input
>Prevedono una ***modalità diversa di interazione***.

>[!abstract] Output
>Effettuano una conversione dell'
## Disabilità
---
>[!info]
>Nel contesto del web development, consideriamo la disabilità come ***activity limitation*** come definite dall'`WHO` che può esserci nell'interazione con `PC` e altre tecnologie.

>[!summary] Classificazione
>Consideriamo tra le menomazioni classificati dall'`WHO` quelli legati a ***funzioni***:

> ***Visive***
- Daltonismo, Ipovisione, Cecità

> ***Uditive***

> ***Motorie***

## WAI
---
>[!info] Web Accessibility Initiative
>La `WAI` è un gruppo di lavoro che opera sull'accessibilità del ***Web***, che ha identificato alcune linee guida, e individuato diversi **livelli di accessibilità**.

### WCAG
>[!hint] Web Content Accessibility Guidelines
>***WCAG*** è un insieme di regole da utilizzare per rendere accessibile un sito web.

>[!summary] Struttura

La struttura delle `WCAG2.0` è basata su:

> $4$ Principi
- **Percepibile**, **Utilizzabile**, **Comprensibile** e **Robusto**.

> Linee guida

Dai $4$ principi discendono $12$ linee guida che forniscono indicazioni per rendere il contenuto più accessibile.
- Le linee guida **non sono verificabili**, ma definiscono gli obbiettivi generali per applicare le tecniche.

> Criteri di Successo

*Per ogni linea guida*, vengono forniti dei ***criteri di successo verificabili***.
- I criteri hanno 3 livelli: $A$ (*minimo*), $AA$ e $AAA$ (*massimo*).

Versioni successive (`WCAG 2.1`) introducono nuove guidelines e success criteria.

>[!todo] Livello di Conformità
>I siti possono raggiungere ***diversi livelli di conformità***.

Un sito per essere conforme, ogni livello ($A$, $AA$, $AAA$) deve.
- *Soddisfare* tutti i criteri di successo del **livello**, o fornire una versione alternativa conforme.
- *Soddisfare* tutti i criteri di successo del **livello precedente**.

>[!caution] Tecniche
>Per ciascun criterio presente, sono documentate una ***serie di tecniche***.
>
>>[!important] Sufficienti
>>Per **soddisfare** il criterio di successo
>
>>[!done] Consigliate
>>Vanno oltre ciò che viene richiesto dal singolo criterio, consentono di rispettare le linee guida ad un livello più elevato.

Una stessa tecnica può far riferimento a più **criteri di successo**.

Una tecnica può essere:
- Generale ($G$).
- Legata ad una tecnologia: `{html icon} HTML` ($H$), `{css icon} CSS` ($C$), etc...

>[!danger] Le tecniche cambiano e/o aumentano di giorno in giorno

#### Esempi
>[!info] Principio: Percepibile
>>[!caution] Linea Guida: Distinguibile
>>Rendere più semplice agli utenti la visione e ascolto dei contenuti, ***separando i contenuti in primo piano dallo sfondo***.
>>>[!done] Criterio di Successo: Contrasto (Livello $AA$)
>>>La rappresentazione visiva del testo e di immagini contenenti testo ha un rapporto di contrasto di almeno $4.5:1$ ad eccezione di alcuni casi (Testo grande, testo non essenziale o logotipi).

Linea guida per il [[Disabilità#Daltonismo|Daltonismo]].

> $G183$
- Tecnica generale ($G$) legata alla definizione di ***relative luminance***
	- La luminosità in un qualsiasi punto normalizzata a $0$ per il **nero più scuro** e $1$ per il *bianco più chiaro*.
- Suggerisce di usare un rapporto di contrasto $3:1$ per il testo e usare indizi visuali in aggiunta per [[HTML/Elementi di HTML/Link]] e controlli, dove è usato solo il colore per identificarlo.

>[!info] Principio: Percepibile
>>[!caution] Linea Guida: Alternative testuali
>> Fornire ***alternative testuali*** per qualsiasi contenuto non di testo .
>>>[!done] Criterio di Successo: Contenuti non testuali (Livello $A$)
>>>Tutti i contenuti non testuali presentati all'utente hanno un'alternativa testuale equivalente che serve allo stesso scopo ad eccezione di alcune situazioni.

Il testo è l'unico media multi sensoriale.
- L'alternativa testuale deve fornire lo stesso messaggio intrinseco del contenuto non testuale.
- Le immagini possono avere l'alternativa testuale tramite l'attributo `alt` ([[HTML/Elementi di HTML/Embedded#Figure|Immagini]]).
- Per gli altri media non testuali, bisogna introdurre una alternativa ***sincrona rispetto a un flusso multimediale***.

>[!info] Principio: Percepibile
>>[!caution] Linea Guida: Adattabile
>> Creare contenuti che possano essere ***rappresentati in modalità differenti*** senza perdere informazioni o struttura.
>>>[!done] Criterio di Successo: Informazioni e correlazioni (Livello $A$)
>>>Le informazioni e le correlazioni trasmesse dalla presentazioni possono essere determinate programmaticamente o disponibili tramite testo.

La struttura è usata dallo screen reader per supportare la navigazione, ma è utile anche come `SEO`.