>[!info]
>Il ***modello Incrementale*** è un modello *iterativo* [[Produzione|di produzione del software]] che combina gli aspetti del modello a cascata applicati a sottosistemi del prodotto finale, producendo il **software** a *incrementi*.

Consiste nell'applicare più sequenze lineari, ***scalate nel tempo***, ognuna delle quali produce uno *stadio operativo del software*.

1. Il primo stadio consiste in un "**prodotto base**" (che soddisfa i requisiti fondamentali).
2. In seguito a una valutazione dell'utente si stende un piano per lo stadio successivo che prevede l'aggiunta di **nuove funzionalità**.

>[!help] Progetti
>È adatto a progetti in cui i requisiti iniziali sono ***ben definiti*** ma la dimensione del sistema scoraggia l'adozione di un processo [[Modello a Cascata|puramente lineare]].

![[incremental_model.png]]

> **Incrementale** vs **Iterativo**

>[!hint] Similarità
>Prevedono **più versioni successive** del sistema.
>Ad ogni istante dopo il primo rilascio esiste una versione in [[Il Ciclo di Vita del Software#Attività|esercizio]] e una in [[Il Ciclo di Vita del Software#Attività|sviluppo]].

>[!missing] Differenze
>***Incrementale***
>- Ogni versione aggiunge nuove funzionalità.
>
>***Iterativo***
>- Da subito sono presenti tutte le funzionalità, *raffinate successivamente*.
## Modello RAD
---
>[!abstract] Rapid Application Development
>Il modello ***RAD*** è un modello di *processo incrementale* che punta a un ciclo di sviluppo *molto breve*.

È un ibrido tra il modello incrementale e il [[Modello a Cascata]].
- Incrementale poiché sono presenti **più team concorrenti**.
- A cascata poiché **non è possibile tornare indietro**.

L'accelerazione dello sviluppo è raggiunto tramite strategie costruttive fondate sull'***uso di componenti***.

![[RAD_model.png]]

>[!fail] ***RAD*** fallisce se
>- Gli utenti non riescono a *tenere il passo*.
>- Le funzionalità non sono implementabili in meno di $3\text{ mesi/uomo}$
>- I punti critici del software è l'***interfacciamento tra componenti***.