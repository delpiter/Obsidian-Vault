>[!example] Elementi
> Il [[Sistemi Embedded#Processore|microcontroller]] è composto di diversi componenti.
> - [[La CPU|CPU]]
> - [[Memorie]]
> - [[General Purpose Input Output|Input Output]]
> - [[Timers]]
> - [[Bus di Comunicazione]]
> - [[Power Circuit]]

![[MicrocontrollerElements.png]]


## Basic Control Architecture
---
>[!failure] Super-Loop
>Il ***super loop*** è la più semplice architettura di controllo adottata per la programmazione di [[Sistemi Embedded#Processore|microcontroller]].

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