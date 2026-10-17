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
- Esempio: [[Finite State Processes]] come *process algebra*.


> [!abstract] [[Petri Nets]]

Approccio non basato sull'interleaving.

## Modellazione e Verifica di programmi concorrenti
---
> Dai modelli ai programmi e viceversa

> [!abstract] Cosa sono i modelli
> I ***modelli*** sono descrizioni rigorose della struttura e del comportamento dei programmi, a un *livello adeguato di astrazione*.

Spesso hanno una rappresentazione ***sotto forma di diagramma*** per il design di un programma.

### Approcci di modellazione per programmi concorrenti
- Modellazione basata sull'[[Sistemi Concorrenti#Interleaving|interleaving]].
- Programmazione multi-threading.
### Modellare l'esecuzione con FSP
> Quando si usa [[Modelli/Finite State Processes|FSP]], i **processi** sono astrazioni di modellazione sia per i thread sia per la memoria condivisa.

Si modella:
- l'esecuzione di un programma sequenziale come un **processo**;
- l'esecuzione di un programma concorrente come **composizione di processi**;
- la condivisione di variabili come **processi**.

## Modellare l'esecuzione con state diagram
> L'esecuzione di un programma può essere rappresentata formalmente da *stati* e *transizioni* tra stati.

> [!cite] Stato
> Uno ***stato*** è una tupla composta da:
> - un elemento per ogni **processo**, che è una *label* di quel processo (la prossima istruzione da eseguire);
> - un elemento per ogni **variabile** (globale o locale), che è un valore dello stesso tipo della variabile.

> [!cite] Transizione
> Esiste una transizione tra due stati $s_{1}$ e $s_{2}$ se l'esecuzione di uno statement nello stato $s_{1}$ porta allo stato $s_{2}$.

Un diagramma degli stati è un grafo che contiene tutti gli stati raggiungibili del programma.
- Gli **scenari** sono rappresentati dai percorsi diretti del diagramma a partire dallo stato iniziale.
- I **cicli** rappresentano la possibilità di una computazione infinita.

### Esempio

`integer n := 0`

```text title:"process P"
integer k1 := 1
p1: n := k1
```

```text title:"process Q"
integer k2 := 2
q1: n := k2
```

> [!cite] Istruzione atomica
> Ogni riga con una label (`p1`, `q1`) rappresenta un'***istruzione atomica***.

- Ogni processo ha una **memoria privata**: le variabili locali `k1` e `k2`.
- I processi condividono della **memoria**: le variabili globali, come `n`.

L'esecuzione ha due scenari:
- `p1, q1` → valore finale `n = 2`
- `q1, p1` → valore finale `n = 1`

Tupla che rappresenta lo stato:
$$
<p,q,n,k_{1},k_{2}>
$$

![[attachements/BasicConcurrencyScenario.png]]

> [!success] Risultato
> Lo stesso programma produce **risultati diversi** a seconda dell'ordine di interleaving delle istruzioni atomiche.

### Conteggio degli scenari
#### Due processi

```text title:"process P"
p1: print("p1")
p2: print("p2")
```

```text title:"process Q"
q1: print("q1")
q2: print("q2")
```

Scenari possibili: **6**

```text title:"process P"
p1: print("p1")
p2: print("p2")
p3: print("p3")
```

```text title:"process Q"
q1: print("q1")
q2: print("q2")
q3: print("q3")
```

Scenari possibili: **20**

> [!hint] Numero di scenari con due processi

| Numero di azioni per processo | Numero di scenari |
| ----------------------------- | ----------------- |
| $1$                           | $2$               |
| $2$                           | $6$               |
| $3$                           | $20$              |
| $4$                           | $70$              |
| $5$                           | $252$             |
| $6$                           | $924$             |
| $7$                           | $3432$            |
| $8$                           | $12870$           |
| $\dots$                       | $\dots$           |
### Tre processi
```text title:"process P"
p1: print("p1")
p2: print("p2")
```

```text title:"process Q"
q1: print("q1")
q2: print("q2")
```

```text title:"process R"
r1: print("r1")
r2: print("r2")
```

Scenari: **90**

> [!hint] Numero di scenari con tre processi

| Numero di azioni per processo | Numero di scenari |
| ----------------------------- | ----------------- |
| $1$                           | $6$               |
| $2$                           | $90$              |
| $3$                           | $1680$            |
| $4$                           | $34650$           |
| $\dots$                       | $\dots$           |

### Formula generale

> [!cite] Numero di scenari
> Il numero di scenari prodotti da $n$ processi, ciascuno con $m_{i}$ azioni, è il seguente

$$
n_{s}=\displaystyle{\frac{\left( \displaystyle\sum_{i=1}^{n} m_{i} \right)! }{\displaystyle\prod_{i=1}^{n}(m_{i}!)}}
$$

> [!warning] Esplosione degli stati
> Il numero di scenari cresce in modo **fattoriale** con il numero di processi e di azioni. Per questo la verifica esaustiva di programmi concorrenti è difficile senza strumenti automatici.

### L'importanza dell'atomicità

#### Esempio: incremento atomico

`integer n := 0`

| `p`              | `q`              |
| :--------------- | :--------------- |
| `p1: n := n + 1` | `q1: n := n + 1` |

> [!success] Risultato
> L'incremento è un'unica istruzione atomica, quindi in ogni scenario il valore finale è sempre `n = 2`.

#### Esempio: incremento non atomico

`integer n := 0`

```text title:"process P"
integer tmp
p1: tmp := n
p2: tmp := tmp + 1
p3: n := tmp
```

```text title:"process Q"
integer tmp
q1: tmp := n
q2: tmp := tmp + 1
q3: n := tmp
```

> [!warning] Race condition
> Nel caso non atomico esistono scenari in cui il valore finale di $n$ è $1$.
> Esempio: `p1, q1, p2, p3, q2, q3`. Entrambi i processi leggono `n = 0`, quindi il secondo scrive `1` sopra il risultato del primo.

![[attachements/GraphScenarios.png]]

#### Atomicità degli oggetti
> La nozione di "***atomico***" può riferirsi non solo alle **azioni**, ma anche alle strutture dati.

> [!cite] Oggetto atomico
> Un ***oggetto*** è ***atomico*** se può trovarsi in un numero finito di stati pari al numero di valori che può assumere.

- Tipicamente i tipi di dato dei linguaggi concorrenti sono atomici.
- Non sempre: per esempio il `{java icon} double` di Java.
- I dati astratti composti da più oggetti semplici sono tipicamente **non atomici**.

##### Stato interno ed esterno
Per un ***data object*** si possono identificare due tipi base di stato:
- **stato interno**: significativo per chi definisce l'oggetto;
- **stato esterno**: significativo per chi usa l'oggetto.

La corrispondenza tra stato interno ed esterno è **parziale**:
- esistono stati interni che non hanno corrispondenza con lo stato esterno;
- gli stati interni che hanno uno stato esterno corrispondente si dicono ***consistenti***.

> [!abstract] In sintesi
> Un oggetto non atomico può attraversare stati interni **non consistenti**, e un altro processo che lo osserva in quel momento vede un valore privo di significato.
### Processi ciclici

> [!caution] Cyclic processes
> Siano $p$ e $q$ due processi che iterano su una condizione.

`integer n := 1`

```text title:P_cyclic
p1: while (n < 1)
p2:     n := n + 1
```

```text title:Q_cyclic
q1: while (n >= 0)
q2:     n := n - 1
```

> [!question] Com'è il diagramma degli stati?
- Genera uno scenario in cui il loop di $p$ esegue *esattamente* **una volta**.
- Genera uno scenario in cui il loop di $p$ esegue *esattamente* **tre volte**.
- Genera uno scenario in cui entrambi i loop vengono eseguiti ***all'infinito***.

![[Modelli/attachements/InfiniteLoop.png]]

> [!success]- Soluzioni
> **Una volta:** `q1, q2, p1, p2, p1`
> `q` porta `n` a `0`, `p` entra nel loop e porta `n` a `1`, poi il test `n < 1` è falso e `p` esce.
>
> **Tre volte:** `(q1, q2, p1, p2)` ripetuto 3 volte, poi `p1`
> Ogni ripetizione fa passare `n` da `1` a `0` e di nuovo a `1`. Al quarto test di `p` si ha `n = 1` e il loop termina.
>
> **Infinito per entrambi:** `(q1, q2, p1, p2)` ripetuto all'infinito
> `n` alterna tra `1` e `0`: `p` vede sempre `n < 1` quando tocca a lui, `q` vede sempre `n >= 0`.
>
> Nota: se `q` esegue due volte di seguito `q1, q2` si arriva a `n = -1` e `q` esce dal loop.

