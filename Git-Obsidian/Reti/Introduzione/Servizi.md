## Tassonomia dei Servizi
---
>[!attention] Servizi Interattivi
>Un ***servizio interattivo*** è una tipologia di servizio in cui esiste *interazione* fra **sorgente** e **destinazione**

Alcuni esempi di *servizi interattivi*:
- **Conversazione**
	- Scambio informativo in *tempo reale*
- **Messaggistica**
	- Scambio informativo in *tempo differito*
- **Consultazione**
	- Scambio informativo con *flusso controllato dall'utente*
	- Il flusso informativo è un una direzione unica (es. `w.w.w.`)

>[!abstract] Servizi Distributivi
>Nei ***servizi distributivi*** la *sorgente* **diffonde** informazioni in modo indipendente ad un *numero impreciso di destinazioni*

**Senza** controllo di presentazione:
- L'utente di destinazione *non controlla l'ordine* con cui riceve le informazioni.

**Con** controllo di presentazione:
- L'utente di destinazione *può controllare l'ordine* con cui ricevere le informazioni

>[!example] Servizio Monomediale
>**Trasporta informazioni** di *un solo tipo* oppure trasferisce più tipologie di informazione sotto forma di *un solo segnale*

Esempio
- Televisione: Le immagini e i suoni sono codificati in ***un unico segnale analogico***

>[!note] Servizio Multimediale
>Trasporta informazioni di *almeno due tipologie diverse*.

Vengono applicati ***diversi protocolli*** per il *trasporto* dell'informazione
- Di conseguenza ci sono diverse ***qualità di servizio***

## Flusso Informativo
---
### Secondo il Numero di Sorgente/Destinatari

>[!caution] Punto a Punto
>Il *trasferimento informativo* avviene da **un utente** ad **un altro utente**.

>[!summary] Multicast
>Il *trasferimento informativo* avviene da **un utente** a **tanti utenti**

>[!todo] Broadcast
>Il *trasferimento informativo* avviene da **un utente** a **tutti gli utenti**

### Secondo la Direzione del Flusso

>[!example] Monodirezionale
>Il *trasferimento informativo* avviene in **una sola direzione**

>[!info] Bidirezionale Simmetrico
>Il *trasferimento informativo* avviene in **entrambe le direzioni** con *uguale capacità* per ogni direzione

>[!tldr] Bidirezionale Asimmetrico
>Il *trasferimento informativo* avviene in **entrambe le direzioni** con *diversa capacità* per ogni direzione
>- es. **ADSL**

## Qualità di servizio
---
>[!warning] Problema di Trasparenza
>La rete può modificare l'informazione ***pertinente ad un dialogo***

>Dati questi dati:

![[attachements/Original Data.png]]
### Trasparenza Semantica
>[!info] Concetto
>Riguarda l'***integrità*** delle informazioni trasportate

Richiede di attuare **procedure di recupero** da *situazioni di errore* che possono insorgere nella rete.

![[attachements/SemanticTransparency.png]]
- Rallenta il trasferimento dell'informazione

>[!done] Uso
>Usato principalmente nelle applicazioni ***non real-time***
>- Necessità di *bassa probabilità di errore*
### Trasparenza Temporale
>[!abstract] Concetto
>Riguarda la ***variabilità dei ritardi*** di transito

Un minimo ritardo di transito è ***sempre presente***

![[attachements/TemporalTransparency.png]]
- Può provocare errori nel trasferimento del dato

>[!done] Uso
>Usato principalmente nelle applicazioni ***real-time***
>- Necessità di *basso ritardo e jitter*

##### Proprietà
>[!info] Affidability
>Probabilità di Errore o perdita delle informazioni.

>[!cite] Fairness
>Uniformità delle prestazioni.

>[!Jitter]
>Variazioni del ritardo nella consegna delle informazioni.

>[!missing] Delay
>Ritardo nella consegna delle informazioni.