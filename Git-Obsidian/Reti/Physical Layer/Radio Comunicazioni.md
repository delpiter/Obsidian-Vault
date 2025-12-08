>[!info]
> Le ***radio comunicazioni*** sono comunicazioni che avvengono senza il vincolo del *collegamento fisico*.

>[!danger] Problema
>Lo ***spettro radio*** è unico e va condiviso.

### Attenuazione
>[!cite] Definizione
>L'[[Strato Fisico#Attenuazione|attenuazione]] nei radiocollegamenti cresce con la distanza con ***legge polinomiale*** e con il ***quadrato della frequenza***.

> Le antenne diventano più efficienti quando la frequenza cresce.

>[!caution] Propagazione

Le onde elettromagnetiche si propagano il linea retta:
- Sotto i $3MHz$, con visibilità diretta o *onda di terra*.
	- ***Onda di terra***: Sono onde che si propagano *lungo la superficie terrestre* o *vicino ad essa*, sfruttando la conducibilità del suolo.
- Fra i $3$ e $30Mhz$, propagazione *ionosferica*.
- Sopra i $30MHz$, **solo** *visibilità diretta* (ponti radio).

## Servizi su Comunicazioni Radio
---
> Sono possibili trasmissioni [[Reti IP#Multicast|punto-multipunto]].

>[!fail] Forte limitazione delle risorse
- Lo spettro radio è **finito**.

>[!help] Cella Radio
>Con la *diffusione radiofonica*, si doveva raggiungere la maggior quantità di utenti possibili con un segnale.
>Si dovette pianificare la ***localizzazione*** delle **emittenti** (*celle*).

Ogni *cella radio* ha un'area di copertura.
- Il segnale è confinato in un'area limitata per **poter riutilizzare lo spettro**.

>[!abstract] Grandi Distanze
>La ***propagazione ionosferica*** è il fenomeno per cui le onde radio, in particolare le onde corte, vengono **riflesse dalla ionosfera**.

Al giorno d'oggi ci sono costellazioni di satelliti sofisticati che ***formano una rete***.

>[!hint] Osservazioni
- I ponti radio e i satelliti sono il modo più *economico* di distribuzione dei **servizi di telecomunicazione** in territori vasti.
- Il mezzo radio è ***vulnerabile ai disturbi***.
	- Numerosi collegamenti presentano una probabilità di fuori servizio.
	- Possibili sabotaggi.

### Sistemi Cellulari
> Sistema creato per una principale applicazione: la *telefonia mobile*.

Potenza trasmessa è piccola e i segnali interferiscono ***solo fra celle adiacenti***.

>[!done] Le frequenze possono essere riusate in celle non adiacenti
- Gruppi di celle (***cell cluster***).
- Con un centinaio di canali si possono servire *numerosi utenti*.
>[!fail] Sono necessari terminali molto sofisticati
- Selezione del canale e segnalazione