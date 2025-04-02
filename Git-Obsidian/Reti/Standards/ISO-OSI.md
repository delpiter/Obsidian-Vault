>[!info] International Organization for Standardization
>L'**ISO** è la più importante organizzazione mondiale per la ***definizione di norme tecniche***

La *ISO* ha dato il via a lavori per giungere ad una serie di standard unificati per la realizzazione di ***reti di calcolatori aperte***

> Per prima cosa ha proposto un modello di riferimento

### Stack ISO-OSI
>[!hint] OSI
>L'***Open System Interconnection*** reference model è uno standard architetturale per **reti di calcolatori interoperabili** 
>Stabilisce una *struttura a strati* composta da uno [[Stack]] di ***protocolli di comunicazione*** di reti suddiviso in *7 livelli*.

![[StackIso-Osi.png]]

>[!done] Vantaggi

- Scompone il problema in *sotto problemi* più semplici da trattare.
- Rende i vari livelli *indipendenti*.
- Definendo solamente *servizi e interfacce*, **livelli diversi** possono essere sviluppati da **enti diversi**

### Flusso informativo
I dati prodotti "***scendono***" lungo lo *stack*.
- Ad ogni passaggio, viene aggiunta *informazione*.
- All'ultimo strato il dato **diventa una sequenza** di `Bit`

>Il processo deve funzionare anche al contrario
- Bisogna essere in grado di ricostruire il dato passando da ogni livello dello stack

### Trasferimento dei Dati
>[!tldr] Protocol Data Unit
>La **PDU** rappresenta l'unità di dati trasferita tra due entità dello stesso livello ($n$) in una *rete*.

Ogni strato del modello *OSI* utilizza una propria **PDU** per comunicare con il livello corrispondente del ***nodo remoto***.

>[!abstract] Service Data Unit
>La **SDU** è l'unità di dati che viene *consegnata da un livello superiore* ($n+1$) a un *livello inferiore* ($n$) per la trasmissione.

Il livello superiore *affida i suoi dati al livello sottostante*, che a sua volta li incapsula in una **PDU**

>[!hint] Service Access Point
>Il **SAP** è un indirizzo o *punto di accesso* che identifica il flusso di dati tra due livelli adiacenti

Funziona come un **punto di ingresso** in cui un livello riceve *servizi* dal **livello inferiore**
- Un'entità di strato $n$ può servire più **SAP** contemporaneamente.
- Un utilizzatore di strato $n$ può servirsi di più **SAP** contemporaneamente
- Non è permesso connettere più user allo stesso **SAP**

>[!caution] Protocol Control Information
>Il **PCI** contiene informazioni di *controllo* **necessarie per il dialogo** a livello $n$, come *intestazioni* e *metadati*.

### Encapsulation
>[!definizione] Definizione 
>L'***incapsulamento*** è il processo in cui i dati passati da un livello superiore vengono combinati con le informazioni di controllo del livello attuale per formare una **PDU**

Una **PDU** è costituita dall'informazione di ***controllo del protocollo*** e dai dati ricevuti dallo ***strato superiore***.
$$
n\text{-}PDU = n\text{-}PCI +n\text{-}SDU
$$
## TCP-IP
---
>"***Modello di Internet***"

Stesso concetto dello stack ***ISO-OSI***

>[!differenza]
>Alcuni layer nello stack **ISO-OSI** sono raggruppati in un unico layer nello stack **TCP-IP**


![[TCP-IP.png|300]]