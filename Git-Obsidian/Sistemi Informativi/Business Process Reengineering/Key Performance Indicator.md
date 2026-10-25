## Key Performance Indicator
---
> Per verificare l'efficacia del processo è necessario misurare quantitativamente come questo soddisfa i requisiti del cliente.

Per ogni processo, a seconda del cliente cambiano i requisiti/obbiettivi
- Parto da una spiegazione qualitativa in linguaggio naturale di qual è il requisito per il cliente.
- Progressivamente vanno tradotti in formule

> Es.

***Requisito***: Impianto ben disegnato, completamente operativo e consegnato puntualmente.

> [!question] Cosa significa?

Devo ***rispettare i tempi***, devo avere una elevata qualità di analisi e stime accurate.

> [!question] Cosa vuol dire rispettare i tempi?

Definisco ***formule matematiche*** per definire la proprietà

> [!tldr] Idea
> ***Traduzione progressiva*** di un *aspetto qualitativo* che si traduce in una *formula calcolabile* e *misurabile* che misura l'**aspetto qualitativo**.

Un `KPI` è:
- ***Quantificabile***: Esprimibile tramite formula.
- ***Rilevabile***: I dati devono essere disponibili, altrimenti la formula non è calcolabile.
- Correlato con l'obbiettivo preposto.

Costruire un `KPI` significa costruire un *insieme di indicatori* e la creazione di ***formule calcolabili***.

> Proprietà:
- Significatività
- Controllabilità
- Semplicità: dove possibile meglio molti KPI semplici che pochi complessi, si applica anche adottando opportune tecniche di visualizzazione.
- Misurabilità
- Equilibrio

Possono essere di 2 tipi principalmente:
- I `KPI` **tecnici** misurano attività che influenzano le performance (bontà di ogni sotto-attività)
- I `KPI` **di risultato** misurano le performance a un momento dato


> [!todo] Mappa degli indicatori
> Un ***indicatore*** cattura un *singolo aspetto* del fenomeno che misura.

Per misurare efficacemente il fenomeno è necessario definire una mappa integrata di `KPI` che copra diversi punti di vista:

> Fenomeno da misurare
- Il processo o soggetto da valutare

> Obbiettivi
- Specifica quale scopo deve raggiungere il processo o soggetto.

> Misure
- Identificazione concreta ma ancora qualitativa degli aspetti da misurare

> Stakeholder
- Soggetti interessati ai KPI, soggetti diversi sono interessati ad aspetti diversi dello stesso fenomeno.

> Sorgente dati
- Determina l'effettiva calcolabilità dell'indicatore

> Formulazione
- Specifica la formula di calcolo dell'indicatore.

##### Esempio
> [!example] Overall Equipment Effectiveness
> ***OEE*** è il principale KPI per misurare la capacità di produzione di un'azienda manifatturera.
> $$\text{Availability}\times\text{Performance}\times\text{Quality}$$

È spesso usato nella ***lean manufacturing*** per raggiungere l'*eccellenza* operativa.

> Availability
- Percentuale di tempo lavorato rispetto al tempo disponibile.

> Performance
- Percentuale di pezzi effettivamente lavorati rispetto ai pezzi teoricamente lavorabili.

> Quality
- Rapporto percentuale dei pezzi conformi sul totale dei pezzi prodotti.


> [!hint] Esempio

- Produzione pianificata: $5300$ pezzi.
- Tempo di processazione teorico per pezzo: $87\sec$
- Turno lavorativo: $3\times 8\text{h}$ al giorno, $5$ giorni settimanali.
- Tempo lavorativo teorico: $100\%$

$$
(5300\times 87) / (8\times 3600) = 16.01 \text{ Turni}
$$

> **Ma**...
- Setup del macchinario: $90\min$
- Setup settimanale: $35\min$
- Durante i turni:
	- Check manuali dello stato del macchinario: $24\min$
	- Allarmi vari (sicurezza, fallimento, controlli, etc): $24\min$

Di conseguenza:
$$
(60\times 8-90-35-24-48) / (60\times 8)=63\%
$$
- $63\%$ di utilizzazione del macchinario al primo giorno.