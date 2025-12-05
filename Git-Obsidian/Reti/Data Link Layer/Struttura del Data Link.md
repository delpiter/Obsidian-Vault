## Logical Link Control
---
>[!tldr] Idea
>Lo strato `LLC` è indipendente dal mezzo fisico, dalla topologia e dal [[LAN#Accesso al Canale di Collegamento|protocollo di accesso]].
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
>[!caution] Dominio di Broadcast
>Insieme di stazioni **raggiungibili** con l'invio di un frame con *indirizzo di broadcast*.

In condizioni normali una [[LAN]] è anche un singolo dominio di broadcast.