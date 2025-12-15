## Logical Link Control
---
>[!tldr] Idea
>Lo strato `LLC` è indipendente dal mezzo fisico, dalla topologia e dal [[LAN#Accesso al Canale di Collegamento|protocollo di accesso]].

Lo strato `LLC` gestisce:
- Controllo del [[Controllo del Canale|canale]] e d'[[Controllo dell'Errore|errore]].
- [[Multiplexing]].

## Medium Access Control
---
>[!hint] Indirizzo `MAC`
>Gli indirizzi `MAC` sono composti da $48$ `bit` cablati nella scheda di rete.
>Sono ***univoci a livello mondiale***.

I primi $3$ `byte` individuano il costruttore e gli altri $3$ *numerano progressivamente le schede*.

> È possibile specificare:
- Un singolo destinatario (`00-60-b0-78-e8-fd`).
- Un *indirizzo di gruppo*.
- [[Reti IP#Broadcast|Broadcast]] (`ff-ff-ff-ff-ff-ff`).

In condizioni normali una [[LAN]] è anche un singolo dominio di broadcast.

### Efficienza con MAC ideale
> Un frame tiene impegnata la `LAN` per $T_{0}$

Il canale non può essere usato al $100\%$.

>[!abstract] Efficienza del `MAC`
>$$\eta=\frac{T}{T_{0}}=\frac{L/C}{L/C+d/v}=\frac{1}{1+a}$$

L'[[Funzionalità e Prestazioni|efficienza]] pone un limite superiore al massimo traffico.

> $A_{0}$: Occupazione media di un sistema ideale.

- $A_{0}<\eta$
	- Tutti i frame in arrivo vengono trasmessi
	- $A_{s}=A_{0}$.
- $A_{0}\geq \eta$
	- Il `MAC` non permette la trasmissione di tutti i frame.
	- Parte dei frame vengono accodati: $A_{s}=\eta<A_{0}$

