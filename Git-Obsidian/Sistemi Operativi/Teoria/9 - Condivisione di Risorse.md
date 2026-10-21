## Mutua Esclusione
---
>[!info] Definizione
>L'accesso ad una risorsa si dice ***mutualmente esclusivo*** se ad ogni istante, **al massimo** un processo può *accedere alla risorsa*
>>[!done] Regola
>>La *regola* della ***mutua esclusione*** impone che le operazioni con le quali i processi accedono alle variabili comuni **non si sovrappongano nel tempo**

- Due processi che vogliono accedere ad una stampante

>[!warning] Problemi: Starvation e Deadlock

![[../../Concurrent Systems/Concorrenza nei sistemi#Deadlock]]

![[../../Concurrent Systems/Concorrenza nei sistemi#Starvation]]

## Garantire l'esecuzione Corretta
---
#### Azioni Atomiche
>[!info] Definizione
>Le *azioni atomiche* vengono compiute in modo indivisibile
>Soddisfano la condizione: "**o tutto o niente**"

Le singole azioni del linguaggio macchina sono *atomiche*

>[!tldr] Caso: Interrupt
>Nel caso degli [[../../Architettura degli Elaboratori/Architettura del Calcolatore/Interfacciamento di Periferiche#Interrupt|interrupt]], il meccanismo di interruzione garantisce che un interrupt venga eseguito **prima** o **dopo** un'istruzione

>Assumiamo che in ogni istante vi possa essere al *massimo* un accesso alla memoria alla volta

Questo significa che operazioni tipo:
- Aggiornamento di una Variabile
- Valutazione di espressioni
- etc

>[!fail] Non sono istruzioni atomiche

Operazioni tipo:
- Assegnamento di un valore costante ad una variabile

>[!done] Sono istruzioni atomiche

>[!note] Notazione
>Si usa la notazione `<S>` per indicare che lo statement `S` deve essere eseguito in modo atomico