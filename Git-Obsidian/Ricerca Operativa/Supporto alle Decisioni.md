>[!info]
>Il ***supporto alle decisioni*** consiste nel realizzare soluzioni software che aiutano manager, operatori finanziari, medici, etc. ad **individuare la miglior decisione** nell'ambito.

I metodi usati per il supporto alle decisioni spaziano da:
- [[../Definizioni/Definizioni_Algoritmi#Problema di Ottimizzazione|Ottimizzazione]]
- **Intelligenza artificiale**.

> Per sviluppare una soluzione per il supporto alle decisioni sono necessari:
- Modellare matematicamente il problema.
- Identificare la sua [[../Algoritmi e Strutture Dati/Confronto fra Algoritmi/Complessità di Algoritmi|complessità]].
- Progettare l'algoritmo più adatto, usando le tecniche di soluzione in relazione al modello e alla complessità.

## Problema, Modello e Algoritmo
---
![[../Algoritmi e Strutture Dati/Problemi e Algoritmi#Problemi]]

Una *istanza* rappresenta i dati noti del problema.
- Calcolare l'area di un triangolo è il **problema**.
- Il triangolo di altezza $20cm$ e base $30cm$ è l'**istanza**.

![[../Algoritmi e Strutture Dati/Problemi e Algoritmi#Algoritmo]]

### Modelli
>[!definizione] 
>I ***modelli*** sono una *rappresentazione*, spesso semplificata di concetti, fenomeni, relazioni, strutture, processi, sistemi, etc.
>Possono riguardare sia aspetti puramente teorici che del mondo reale.

Consentono di perseguire i seguenti obbiettivi:
- **Facilitare la comprensione**, identificando i componenti fondamentali e i meccanismi di funzionamento.
- **Spiegare**, **controllare** e **predire eventi**, anche sulla base delle osservazioni passate.
- Supportare i **processi decisionali**.

### Modello Matematico
>[!info]
>Un ***modello matematico*** consente di rappresentare la realtà di interesse con un *alto grado di astrazione*, attraverso:
>- Simboli, equazioni, etc.

I modelli matematici prevedono l'uso di ***parametri*** che rappresentano l'*input* e di ***variabili*** che rappresentano l'*output*.

Nel caso in cui i parametri possono essere definiti con esattezza a priori parleremo di ***modelli deterministici***.
- Altrimenti *modelli stocastici*.

Nella definizione e nell'uso dei modelli non bisogna dimenticarsi dell'***aspetto numerico***.
- L'[[../Metodi Numerici per L'Intelligenza Artificiale/Numeri Finiti/Errore di Rappresentazione|approssimazione]] dei parametri e gli errori nel calcolo possono inficiare la **validità dell'output** ([[../Metodi Numerici per L'Intelligenza Artificiale/Condizionamento e Stabilità/Condizionamento]] di una istanza).

## Tipologie di Problemi
---
> Distinguiamo le seguenti tipologie:

>[!caution] Problema di ***Decisione***
- Data un'*istanza* si vuole determinare se esiste o meno una certa soluzione.

>[!hint] Problemi di ***Ricerca***
- Data un'*istanza* si vuole determinare una possibile soluzione.

>[!example] Problemi di ***Enumerazione***
- Data un'*istanza* si vuole determinare tutte le possibili soluzioni.

>[[../Definizioni/Definizioni_Algoritmi#Problema di Ottimizzazione|Ottimizzazione]]
-  Data un'*istanza* si vuole determinare la *migliore soluzione possibile* rispetto a una misura fissata.
### Complessità Computazionale
>[!info]
>La teoria della [[../Algoritmi e Strutture Dati/Confronto fra Algoritmi/Complessità di Algoritmi|complessità computazionale]] è un ambito di ricerca della matematica spesso denotato come "*informatica teorica*".
>Ha l'obbiettivo di classificare i problemi secondo la loro **intrinseca complessità**.

*Banalizzando*:
- Ci consente di determinare se un problema è **facile** o **difficile**.

>[!fail] Problema difficile
>Un ***problema è difficile*** se in una sola istanza **non** sempre si trova una *soluzione ottima* ([[../Algoritmi e Strutture Dati/Complessità/Classi P e NP]]).

## Ricerca Operativa
---
>[!info]
>La ***ricerca operativa*** è la disciplina che si occupa dei *problemi di ottimizzazione*.

> Campi di applicazione:
- Business Analytics
- Data Science
- Machine Learning

### Ottimizzazione non Vincolata
>[!tldr] Idea
>Nell'***ottimizzazione non vincolata*** si cerca la soluzione migliore (*ottimale*) all'interno di uno spazio di ricerca **senza limiti imposti**.

Le variabili possono assumere ***qualsiasi valore reale***.

>[!hint] Obiettivo
>L'**obbiettivo** è trovare il valore di massimo o minimo di una ***funzione obiettivo*** (detta anche *funzione di* costo).

- **Spazio di ricerca:** L'intero dominio della funzione è il potenziale spazio di soluzione.

### Ottimizzazione Vincolata
>[!tldr] Idea
>L'***ottimizzazione vincolata*** è un problema matematico in cui si cerca di massimizzare o minimizzare una *funzione obiettivo*, ma le variabili **devono rispettare** delle condizioni specifiche, chiamate ***vincoli***.

 Le **variabili** devono soddisfare *contemporaneamente* un'equazione e/o una disuguaglianza.

Un *sistema di disequazioni* definisce l'insieme delle ***soluzioni ammissibili*** del problema.
- Anche chiamata ***regione ammissibile***.
- Tutti i punti della *regione ammissibile* soddisfano i vincoli del problema.