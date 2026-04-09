![[Finite State Machines#^4073b9]]
## Dagli Interrupt agli Eventi
---
>[!tldr] Idea
>Il meccanismo degli [[../../Architettura degli Elaboratori/Architettura del Calcolatore/Interfacciamento di Periferiche#Interrupt|Interrupt]] può essere usato per progettare architetture ad alto livello ***event-based***.

Un ***interrupt*** può essere considerato un "*evento a basso livello*".
- Un meccanismo che interrompe il *flow* del **super loop** per eseguire un *handler*.

>[!warning] Attenzione
>A livello hardware gli interrupt sono implementati come un ***sistema di polling***.

> Esempi di Architetture event-based:
- [Observer](https://refactoring.guru/design-patterns/observer).
- [[Finite State Machines#FSM Sincrone e Asincrone|FSM Asincrone]].

### Observer Pattern
>[!quote] Design Pattern
> "***Observer*** is a **behavioral design pattern** that lets you define a subscription mechanism to notify multiple objects about any events that happen to the object they’re observing".

> Elementi

***Source***
- Il "*generatore*" di eventi.
- Espone un'interfaccia per i "*listener*" per registrarsi per essere notificati quando accade un evento.

***Event***
- L'evento generato (es. Un *bottone Premuto*).

***Observer***
- L'"*ascoltatore*" di una sorgente.
- Espone un'interfaccia per essere *notificato degli eventi*.

>[!caution] Funzionamento

1. Si registra un *listener* alla *source*.
2. La *source* avrà il compito di notificare tutti i *listener* in ascolto, quando un evento accade.

>[!warning] Attenzione
>Nei [[../Sistemi Embedded]] il codice del *listener* viene eseguito dall'***interrupt handler***.
>>[!danger] Il *listener* **non deve contenere** computazioni a lungo termine

### FSM Asincrone
>[!tldr] Idea
>Le `FSM` asincrone sono basate su due concetti base, il ***super-loop ininterrompibile*** (*event loop*) e una [[../../Algoritmi e Strutture Dati/Strutture Dati/Queue]] di eventi.

Non c'è il concetto di [[Architetture Task-Based#Architetture Task-Based|periodo]].

```c
/* event loop */
while(1)
{
	event e = waitEvent(); // Blocking Instruction
	h = e.selectHandler();
	exec(h);
}

/* Interrupt Handler */
void handlerExample()
{
	eventQueue.push(event);
}
```

Dietro all'***event-loop*** c'è una pool id [[../../Sistemi Operativi/Teoria/6 - Processi, Schedule e Thread|thread]] che esegue gli handler.
- Un eventuale valore di ritorno dell'**handler** è gestito tramite l'invio di un *ulteriore evento*.

> C'è un disaccoppiamento tra la *generazione dell'evento* e la *reazione del sistema*.
- Non c'è più la limitazione dovuta all'esecuzione del ***listener*** nell'*interrupt handler*.
- Non ci sono *variabili condivise*, la condivisione di informazioni deve essere fatta tramite la generazione di **altri eventi**.

>[!important] Importante
>È un ***concetto molto importante*** che non può essere gestito tramite delle librerie.
>- Alcuni linguaggi aggiungono le *keyword* `async` e `await` per la gestione nativa.
