> Il sistema visivo umano percepisce una parte molto limitata delle [[../Fisica/Elettromagnetismo/Elettromagnetismo|radiazioni elettromagnetiche]] con lunghezze d'onda compresa tra $400nm$ (*ultravioletti*) e $800nm$ (*infrarossi*).


![[attachements/visibleLightSpectrum.png]]

La sensazione che il sistema visivo umano produce quando l'*occhio* viene colpito dalla **luce** *riflessa*, *emessa* o *trasmessa* da un oggetto viene definite come ***colore***.
- L'*ampiezza* d'onda influisce sull'**intensità luminosa**.
- La *lunghezza* d'onda influenza la **tonalità del colore percepito**.

## Colore
---
> Gli oggetti posseggono delle particelle, chiamati ***pigmenti colorati***.

>[!abstract] Pigmenti
>I ***pigmenti*** sono le particelle responsabili dell'*assorbimento del selettivo della luce*.
>>[!done] In altre parole
>>La luce incidente sulla superficie dell'oggetto viene *in parte riflessa* e *in parte* **no**.

Gli oggetti appaiono di un certo colore perché assorbono tutti i colori della luce visibile, **tranne il colore che viene riflesso all'occhio**.

### Teoria Tricromatica

>[!check] Teoria di Young
>Il medico inglese **Thomas Young** ritenne *impossibile* che in ogni punto della retina potessero esistere **infiniti fotorecettori diversi** quanti i colori discriminati dall'occhio.
>
>Teorizzò l'esistenza di ***tre soli tipi di recettori*** associati ai ***tre colori primari additivi***: [[../Architettura degli Elaboratori/Rappresentazione dell'Informazione/Rappresentazione di Immagini#Codifica RGB|Rosso Verde e Blu]].

I ***tre tipi di fotorecettori***, ognuno sensibile ad un *colore primario*, rilevano tre diversi stimoli che il cervello unisce generando il *colore*.

#### Modelli di Colore
> Un ***modello di colore*** è un modello matematico astratto che descrive il modo in cui i colori possono essere rappresentati come *tuple di numeri*.

![[../Architettura degli Elaboratori/Rappresentazione dell'Informazione/Rappresentazione di Immagini#Codifica RGB]]

>[!hint] Osservazione

- $\text{Rosso}+\text{Verde}=\text{Giallo}$
- $\text{Rosso}+\text{Blu}=\text{Magenta}$
- $\text{Blu}+\text{Verde}=\text{Ciano}$

> Nella rappresentazione `3D` del modello `RGB` possiamo associare ad ogni **asse** un *colore primario*.

I grigi sono sulla diagonale del cubo.
- Un *grigio* è rappresentato da una terna con ***tutti i valori uguali***.
##### Modello CMY

>[!caution] Cyan Magenta Yellow
>Modello basato sulla ***sintesi sottrattiva dei colori***, che consiste nell'assorbire alcune lunghezze d'onda della luce bianca per creare i colori.

![[../Architettura degli Elaboratori/Architettura del Calcolatore/attachements/CYMK.png]]

>[!hint] Osservazione

- $\text{Ciano}+\text{Magenta}=\text{Rosso}$
- $\text{Ciano}+\text{Giallo}=\text{Verde}$
- $\text{Magenta}+\text{Giallo}=\text{Blu}$

### Spazio di Colori
>[!check] HSI
>Lo ***spazio di colori*** `HSI` (**H**ue, **S**aturation, **I**ntensity) è un modello che permette di descrivere un colore attraverso i concetti più familiari e vicini alla percezione visiva umana.

> **Hue**, Tonalità

- È il ***colore puro***, così come viene percepito dall'osservatore.

> **Saturation**, Saturazione

- È la ***quantità di luce bianca miscelata*** con una certa tinta.
	- Un colore *saturo* è vivido e brillante.
	- Un colore *desaturato* è più pallido e tendente al grigio.

> **Intensity**, Luminosità

- Determina la ***quantità di luce presente*** in un colore.
	- Un colore con alta luminosità è *luminoso*.
	- Un colore con bassa luminosità è *scuro*.

>[!definizione]
>Si definisce Cromaticità:
>$$\text{Hue}+\text{Saturation} = \text{Cromaticità}$$

![[attachements/HSI.png]]

Si immagini di mettere il [[../Architettura degli Elaboratori/Rappresentazione dell'Informazione/attachements/RGBspectrum.png|cubo RGB]] in equilibrio sul vertice $(0,0,0)$ con il vertice $(1,1,1)$ in alto, mantenendo verticale la linea dei grigi.
- La **tonalità** (`H`) viene misurata da una angolo intorno all'asse verticale con il *rosso* a $0^{\circ}$, il *verde*a $120^{\circ}$ e il *blu* a $240^{\circ}$.
- La **saturazione** (`S`) vale zero sull'asse del modello.
- La **luminosità** (`I`) è rappresentata dall'altezza del modello, con lo zero che rappresenta il *nero* e l'uno il *bianco*.

