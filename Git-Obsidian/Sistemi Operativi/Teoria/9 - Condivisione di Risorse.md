## Mutua Esclusione
---
>[!info] Definizione
>L'accesso ad una risorsa si dice ***mutualmente esclusivo*** se ad ogni istante, **al massimo** un processo può *accedere alla risorsa*
>>[!done] Regola
>>La *regola* della ***mutua esclusione*** impone che le operazioni con le quali i processi accedono alle variabili comuni **non si sovrappongano nel tempo**

- Due processi che vogliono accedere ad una stampante

>[!warning] Problemi: Starvation e Deadlock
### Deadlock

>[!info] Definizione
>Una situazione di *Deadlock* (*stallo*) si verifica quando due o più processi *rimangono in attesa* di eventi che **non potranno mai verificarsi** a causa di condizioni cicliche nel ***possesso*** e nella ***richiesta*** di risorse.
>>[!question] Come sistemare un processo in stato di Deadlock?
>>Nei sistemi reali, se ne può uscire sono con metodi "**distruttivi**", ***terminando i processi***

![[attachements/Starvation&Deadlock.png]]
>Immagine $b$: Autisti in un incrocio
>- Nessuno da la precedenza e finiscono tutti per bloccarsi
### Starvation
>[!info] Definizione
>Una situazione di *Starvation* (o *blocco individuale*) si verifica quando un processo *rimane in attesa* di un **evento che non accadrà mai**, e quindi non può portare a termine il proprio lavoro
>>[!note] Situazione di Uscita
>>A differenza del **deadlock**, non è una condizione definitiva, basta adottare un'opportuna politica di assegnamento

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