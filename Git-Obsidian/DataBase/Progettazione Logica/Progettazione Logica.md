![[attachements/ProgettazioneLogica.png|400]]

>[!hint] Obbiettivo
>L'obbiettivo della fase di *progettazione logica* è pervenire a uno schema logico che rappresenti ***in modo fedele*** i *concetti* e i *requisiti* analizzati e che sia, allo stesso tempo, "***efficiente***".

L'efficienza è legata alle ***prestazioni***, ma poiché non sono valutabili precisamente, si ricorre all'impiego di ***indicatori semplificati***.

>[!question] Che cosa si intende quando si dice che uno *schema relazionale* ($DB_{rel}$) rappresenta "***fedelmente***" uno *schema concettuale* ($DB_{conc}$)

- Significa che i due schemi sono **equivalenti** dal punto di vista della loro ***capacità informativa***.

Questa attività di progettazione può essere vista, come la definizione di un mapping $M$ che spiega come trasformare ogni stato legale $db_{conc}$ di $DB_{conc}$ in un *corrispondente* stato $db_{rel}$ di $DB_{rel}$

>[!done] La progettazione preserva l'informazione se $M$ è totale e iniettiva.

## Progettazione che Garantisce l'Equivalenza
---
>[!definizione] Definizione
>Diciamo che la progettazione garantisce l'equivalenza se:
>- ***Preserva l'informazione***.
>- Per ogni stato legale $db_{rel}$ di $DB_{rel}$ esiste uno stato legale $db_{conc}$ di $DB_{conc}$ tale che $M(db_{conc})=db_{rel}$

La definizione intuitivamente asserisce che esiste una [[../../Analisi/Funzioni/Introduzione Funzioni#Funzione Biunivoca|biiezione]] tra gli insiemi di stati legali.

![[attachements/FunzioniBiunivoche.png]]

#### Fasi della Progettazione Logica
>La *progettazione logica* può essere articolata in ***due fasi*** principali

>[[Ristrutturazione|!tip]]

>[[Traduzione|!cite]]