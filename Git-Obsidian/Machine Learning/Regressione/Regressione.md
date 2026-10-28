## Regressione
---
> [!info] 
> Nella ***regressione*** dato un pattern $x_{i}$ con etichetta $y_{i}$, i valori $y_{i}$ sono numerici e continui in $\mathbb{R}$ e l'obbiettivo del training è l'apprendimento di una funzione $f(x)\mapsto y$.

La funzione $f$ è controllata da un ***insieme di parametri***.
- Se la dipendenza dai parametri è ***lineare*** (es. assenza di elevazioni a potenza dei parametri nella definizione di $f$ ), la regressione si definisce *lineare*.

Nella regressione $x$ è detta ***variabile indipendente*** e $y$ ***variabile dipendente***.
- Si assume che la variabile indipendente *sia esatta* mentre la variabile dipendente sia *affetta da errore* (es. **imprecisione di misura**)

Se la variabile indipendente è uno *scalare* $x$ (i.e., una sola variabile indipendente), parliamo di [[Simple Linear Regression]] (retta di regressione).

Se la variabile indipendente è un *vettore* $x$ (i.e., più variabili indipendenti), parliamo di [[Multiple Linear Regression]] (esempio: iperpiano di regressione).

### Come Scegliere il regressore corretto
> Per problemi di regressione di ***piccole-medie dimensioni***:
- Il modello **lineare** risolto tramite `LS` con fattorizzazione `SVD` è l'approccio più semplice che costituisce una baseline.
- Un modello **non lineare** rispetto alla variabile indipendente può essere una buona seconda scelta.
- Quando sono necessari modelli più potenti `SVR`, *random forest* e *gradient boosting* sono valide alternative.
- Se la dipendenza è nota ma non lineare rispetto ai parametri, l'*ottimizzazione numerica con Gauss-Newton* è la migliore scelta.

> Per problemi di regressione di ***grandi dimensioni***:
- L'approccio iterativo ***gradient descent*** usato in *combinazione* con ***reti neurali*** è spesso preferibile.