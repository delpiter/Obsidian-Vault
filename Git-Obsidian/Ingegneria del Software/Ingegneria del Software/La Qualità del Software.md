## Classificazione
---
> La qualità su cui si basa la valutazione di un `sw` possono essere classificate in:

>[!failure] Interne `I`
>Riguardano le **caratteristiche** legate allo sviluppo, **non** *sono visibili agli utenti*.

>[!abstract] Esterne `E`
>Riguardano le **funzionalità** fornite dal prodotto, *sono visibili agli utenti*.

>[!info] Relative al Prodotto `P`
>Riguardano le caratteristiche stesse del software, *sono sempre valutabili*.

>[!caution] Relative al Processo `PC`
>Riguardano i **metodi utilizzati** durante lo sviluppo.

## Le Qualità
---
>***Correttezza*** `E` `P`
- Un **sw** è *corretto* se rispetta le [[Il Ciclo di Vita del Software|specifiche del progetto]].

> ***Affidabilità*** `E` `P`
- Un **sw** è *affidabile* se l'utente può dipendere da esso.

> ***Robustezza*** `E` `P` `PC`
- Un **sw** è *robusto* se si comporta in modo ragionevole anche in circostanze non previste dalle specifiche.

> ***Efficienza*** `E` `P`
- Un **sw** è *efficiente* se usa intelligentemente le risorse di calcolo.

> ***Facilità d'uso*** `E` `P`
- Un **sw** è *facile da usare* se l'interfaccia che presenta all'utente gli permette di esprimersi in modo naturale.

> ***Verificabilità*** `I` `P` `PC`
- Un **sw** è *verificabile* se le sue caratteristiche sono facilmente valutabili.
- Qualità necessaria per ottenere una certificazione #addLink.

> ***Riusabilità*** `I` `P`
- Un **sw** è *riusabile* se può essere usato, in tutto o in parte per costruire nuovi sistemi.

> ***Portabilità*** `E` `P`
- Un **sw** è *portabile* se può funzionare su più piattaforme.

> ***Manutenibilità*** `I` `P`
- Un **sw** è *facile da mantenere* se:
	- È strutturato in modo da facilitare la ricerca degli errori.
	- La struttura permette di aggiungere nuove funzionalità o di adattarlo ai cambiamenti del dominio applicativo.

> ***Interoperabilità*** `E` `P`
- Fa riferimento all'abilità di un sistema di *coesistere con altri sistemi*.

> ***Produttività*** `PC`
- Misura l'*efficienza del processo di produzione* del software in termini di velocità di consegna.

> ***Tempestività*** `PC`
- Misura la *capacità del processo di produzione* di **valutare** e **rispettare** i tempi di consegna del prodotto.
	- Solitamente essere *produttivi* -> Essere *tempestivi*.

> ***Trasparenza*** `PC`
- Un processo di produzione di un **sw** si dice *trasparente* se permette di capire il suo stato attuale e tutti i suoi passi.
	- Importante per ottenere una **certificazione del processo du produzione**.