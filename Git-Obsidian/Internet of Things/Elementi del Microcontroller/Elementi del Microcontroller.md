>[!example] Elementi
> Il [[../Sistemi Embedded#Processore|microcontroller]] è composto di diversi componenti.
> - [[../../Architettura degli Elaboratori/Architettura del Calcolatore/La CPU|CPU]]
> - [[Memorie]]
> - [[General Purpose Input Output|Input Output]]
> - [[Timers]]
> - [[Bus di Comunicazione]]
> - [[Power Circuit]]

![[attachements/MicrocontrollerElements.png]]

> [!hint] Differenze tra microcontrollore e microprocessore
>

I ***microcontroller*** sono piccoli sistemi contenuti interamente in un unico chip completamente assestante.
- Un *microcontrollore* ha un piccolo *microprocessore* al suo interno.
Utilizzano una architettura speciale chiamata ***Harvard Architecture***.
- Una memoria per il codice, una per i dati.
- I ***registri*** sono mappati all'interno della memoria dei dati.

![[attachements/HarvardArchitecture.png]]

Un ***microprocessore*** è un dispositivo molto più potente di un microcontrollore con capacità computazionali molto elevate.
- A differenza del microcontroller **necessita di periferiche** come memoria, controller e interfacce di comunicazione.
Usato in sistemi con architettura di [[../../Architettura degli Elaboratori/Architettura del Calcolatore/Organizzazione del Calcolatore|Von Neumann]].

## Basic Control Architecture
---
>[!failure] Super-Loop
>Il ***super loop*** è la più semplice architettura di controllo adottata per la programmazione di [[../Sistemi Embedded#Processore|microcontroller]].

Non richiede alcun *supporto hardware*.

>[!tldr] Idea

- Inizializzazione.
- **Loop infinito**.

```c
#include "X.h"

void main(void) {
	X_Init();
	while(1)
	{
		X();
	}
}
```

>[!done] Pro
- Semplicità.
- Affidabile e sicuro.
- Efficiente.

>[!fail] Contro
- Timing poco accurato.
- Poco flessibile.

> Semplici regole per le routine
- Più sono pesanti, più il sistema sarà lento e meno reattivo.
- Dovrebbero fare scorrere il `super loop` velocemente.