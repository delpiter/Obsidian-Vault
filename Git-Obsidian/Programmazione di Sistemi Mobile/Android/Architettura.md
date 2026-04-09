![[attachements/Android.png]]

## Linux Kernel
---
>[!done] Vantaggi

- **Portabilità**.
- **Sicurezza**.
	- Ambiente multi-processo sicuro.
	- Modello di *permessi user-based*.
	- I processi sono isolati.
	- Inter-process communication.
	- Ogni applicazione ha il proprio user ID.
- **Power Management**.
- **Android Run Time** basato sul kernel per thread e gestione della memoria.

## Hardware Abstraction Layer
---
>[!info] 
>Il ***livello di astrazione hardware*** fornisce *interfacce standard* che espongono le capacità hardware del dispositivo al framework `API` Java di *livello superiore*.

È costruito da più ***moduli di libreria***, ognuno dei quali implementa un'interfaccia per un tipo specifico di componente hardware:
- **Videocamera** o **Bluetooth**.

Quando un framework effettua una chiamata per accedere all'hardware:
- Il sistema *carica il modulo della libreria per quel componente hardware*.
>[!done] Vantaggi
>Il `HAL` nasconde il vero device e consente di implementare funzionalità senza influire o modificare il sistema di livello superiore.

## Android Runtime
---
> Per i dispositivi con [[Introduzione ad Android|android]] 5.0 o superiore.

>[!tldr] Idea
>Ogni applicazione viene eseguita nel proprio processo e con la propria istanza di ***android runtime***.

`ART` è scritto per eseguire più macchine virtuali su dispositivi a memoria insufficiente eseguendo file `DEX`.
- `DEX` è un formato *bytecode* progettato appositamente e ottimizzato per un **minimo ingombro di memoria**.

>[!abstract] Caratteristiche di `ART`
- Compilazione *anticipata* e *just-in-time*.
- ***Garbage collection*** ottimizzata.
- Conversione dei file `DEX` in codice macchina più compatto (9.0+).
- Migliore supporto per il ***debug***.

## Native C/C++ Libraries
---
> Molti componenti come [[#Android Runtime|ART]] e [[#Hardware Abstraction Layer|HAL]] sono costruiti da codice nativo che richiede librerie native scritte in `{c icon} C` e `{cpp icon} C++`

>[!summary] `API`
>La piattaforma ***android*** fornisce `API` del framework `{java icon} java` per esporre le funzionalità di alcune di queste librerie native delle app.

Se si vuole sviluppare un'app che richiede codice `C/C++` si può usare ***Android NDK*** per accedere a queste librerie della piattaforma nativa.

## Java API Framework
---
> L'intero set di funzionalità del `SO` *android* è disponibile tramite `API` scritte in `{java icon} java`.

>[!example] Idea
>Queste `API` costituiscono i mattoni necessari per creare app ***android*** semplificando il riutilizzo di componenti e servizi di sistema modulari e core.

Alcuni *componenti*:
- ***Resource manager***: Fornisce accesso a risorse non di codice, come testo localizzato.
- ***Notification manager***: Consente a tutte le app di visualizzare avvisi personalizzati.
- ...

## System Apps
---
> Android viene fornito con una serie di ***app principali*** per e-mail, messaggi `SMS`, calendari, browser, etc...

>[!tldr] Idea
- Le app incluse con la piattaforma ***non hanno uno stato speciale*** tra le app che l'utente.
	- Un'app di terze parti *può diventare* il browser web predefinito.
- Le app di sistema funzionano sia come ***app per gli utenti*** sia per ***fornire funzionalità*** a cui gli sviluppatori possono accedere dalla propria app.

>[!definizione] App
>Un'app è un'***applicazione software*** che permette di accedere ai più svariati servizi, contenuti, giochi, etc...