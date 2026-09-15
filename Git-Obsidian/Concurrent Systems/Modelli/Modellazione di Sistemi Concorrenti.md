## Modelli
---

> [!Modelli]
> Un ***modello*** è una rappresentazione semplificata del mondo reale, e come tale, include solamente gli aspetti del sistema del mondo reale *rilevanti al problema in questione*.

> Esempio

Il modello di un aeroplano, usato nei "wind tunnel tests", modella solamente la forma esterna dell'aeroplano.
- Potenza, numero di posti a sedere e la capacità del carico **non influiscono nell'aerodinamica**.

I modelli sono usati nell'ingegneria poiché possono essere usati per *focalizzare un aspetto particolare* del sistema reale.

>[!help] Concetti chiave
>I modelli sono basati su ***teorie formali e framework*** che permettono di verificare meccanicamente che il sistema soddisfa le proprietà di correttezza, requisite da un programma nella sua implementazione.

Un modello è diverso dal test driven development, anche se il concetto è lo stesso.
### Ruolo principale della modellazione
> La creazione di un modello ha i seguenti scopi

- Descrizione del ***comportamento*** di un sistema concorrente in generale.
- Supporto nel ***design*** di un programma concorrente.
- *Analisi* del comportamento di un sistema concorrente e dell'esecuzione di un programma concorrente.

>[!info]
>Un modello rappresenta il comportamento di un programma concorrente ad un ***livello di astrazione*** che permette di concentrarsi sugli aspetti concorrenti.

#### Approcci di modellazione

> [!todo] Labelled Transition System e Process Algebra

Sono modelli di concorrenza che utilizzano il concetto di [[../../Sistemi Operativi/Teoria/8 - Concorrenza#Multiprogramming|interleaving]].
- Esempio: ***Finite State Processes*** come *process algebra*.


> [!abstract] Petri Nets

Approccio non basato sull'interleaving.