Nel contesto della **programmazione parallela**, la *scaling efficiency* misura **quanto bene un programma sfrutta l’aumento delle risorse di calcolo** (tipicamente il numero di core o processori).
Si studia con due approcci diversi:

* **Weak scaling**
* **Strong scaling**

La differenza fondamentale riguarda **come cambia il problema quando aumentano i processori**.

---

# 1. Strong scaling efficiency

## Definizione

Nel **strong scaling** si mantiene **la dimensione del problema costante** mentre si aumenta il numero di processori.

Esempio:

* un problema con **1 miliardo di elementi**
* lo si esegue con **1, 2, 4, 8, 16 processori**

L’obiettivo è verificare **quanto il tempo di esecuzione diminuisce**.

### Speedup

Si definisce lo **speedup**:

[
S(p) = \frac{T(1)}{T(p)}
]

dove:

* (T(1)) = tempo con 1 processore
* (T(p)) = tempo con (p) processori

### Efficienza

La **strong scaling efficiency** è:

[
E(p) = \frac{S(p)}{p} = \frac{T(1)}{p \cdot T(p)}
]

Interpretazione:

* **E = 1 (100%)** → scaling perfetto
* **E < 1** → inefficienze

---

## Come dovrebbe essere il grafico ideale

In un grafico tipico:

* **asse x** → numero di processori
* **asse y** → efficienza

Caso ideale:

* linea **orizzontale a 1**

---

## Cosa significa se il grafico scende

Se la **strong scaling efficiency scende**, significa che **aggiungere processori produce benefici sempre minori**.

Le cause principali sono:

### 1. Parte seriale del programma (Legge di Amdahl)

Se una frazione del codice **non può essere parallelizzata**, quella parte limita lo speedup.

[
S_{max} = \frac{1}{f_s + \frac{f_p}{p}}
]

dove (f_s) è la parte seriale.

Con molti processori:

* i core rimangono **inattivi**
* l'efficienza cala

---

### 2. Overhead di comunicazione

I processori devono:

* scambiarsi dati
* sincronizzarsi
* coordinarsi

Con più nodi:

* **più messaggi**
* **più latenza**

Questo tempo **non contribuisce al lavoro utile**, quindi l’efficienza scende.

---

### 3. Sincronizzazioni

Esempi:

* barriere
* lock
* riduzioni

Alcuni processori devono **aspettare gli altri**.

Questo produce:

* **idle time**
* perdita di efficienza.

---

### 4. Granularità del lavoro

Quando il lavoro totale è fisso, aumentando i processori:

* ogni core riceve **meno lavoro**

Se il lavoro diventa troppo piccolo:

* l’overhead supera il tempo di calcolo.

---

### Interpretazione del grafico

Se la curva scende velocemente:

* il problema **non scala bene in strong scaling**
* c’è molta **serialità o overhead**

Se scende lentamente:

* lo scaling è **abbastanza buono**.

---

# 2. Weak scaling efficiency

## Definizione

Nel **weak scaling** si mantiene **costante il lavoro per processore**.

Quando si raddoppiano i processori, si **raddoppia anche la dimensione del problema**.

Esempio:

| Processori | Dimensione problema |
| ---------- | ------------------- |
| 1          | N                   |
| 2          | 2N                  |
| 4          | 4N                  |
| 8          | 8N                  |

Ogni processore lavora sempre su **N dati**.

---

### Efficienza

La **weak scaling efficiency** si definisce:

[
E_w(p) = \frac{T(1)}{T(p)}
]

dove:

* (T(1)) → tempo per problema di dimensione N con 1 processore
* (T(p)) → tempo per problema di dimensione pN con p processori

---

## Comportamento ideale

Idealmente:

* il tempo **rimane costante**

Quindi:

* **efficienza = 1**

---

## Cosa significa se il grafico scende

Se la **weak scaling efficiency diminuisce**, significa che **il tempo cresce anche se il lavoro per core è costante**.

Questo indica che il sistema **non scala bene con problemi più grandi**.

Le cause principali sono diverse da quelle dello strong scaling.

---

### 1. Comunicazione che cresce con i processori

Molti algoritmi hanno comunicazioni che crescono con (p).

Esempi:

* scambi tra vicini
* operazioni globali
* broadcast
* reduce

Quando aumentano i nodi:

* aumenta la **quantità di dati scambiati**
* aumenta il **tempo di comunicazione**

---

### 2. Comunicazioni globali

Operazioni come:

* barrier
* allreduce

possono costare:

[
O(\log p) \quad \text{o} \quad O(p)
]

Quindi aumentando (p):

* il costo cresce
* il tempo totale aumenta.

---

### 3. Contention di rete o memoria

Con molti processori:

* più traffico di rete
* più accessi alla memoria distribuita

Questo crea:

* **congestione**
* latenza maggiore.

---

### 4. Squilibrio di carico

Anche se teoricamente ogni core ha lo stesso lavoro, nella pratica può verificarsi:

* **load imbalance**

Alcuni core finiscono prima e aspettano.

---

### Interpretazione del grafico

Se la **weak scaling efficiency scende**:

* il sistema diventa **sempre più dominato dalla comunicazione**
* l’architettura o l’algoritmo **non scala bene per grandi sistemi**

---

# 3. Differenza chiave nell’interpretazione della discesa del grafico

### Strong scaling: grafico che scende

Significa:

➡ il problema è **troppo piccolo per molti processori**

oppure

➡ c’è **una forte parte seriale**

---

### Weak scaling: grafico che scende

Significa:

➡ **il costo della comunicazione cresce con il numero di processori**

oppure

➡ l’algoritmo **non è progettato per scalare su grandi sistemi**

---

# 4. Riassunto concettuale

| Tipo               | Problema              | Cosa misura           | Se il grafico scende     |
| ------------------ | --------------------- | --------------------- | ------------------------ |
| **Strong scaling** | dimensione fissa      | riduzione del tempo   | overhead + parte seriale |
| **Weak scaling**   | lavoro per core fisso | crescita del problema | comunicazione crescente  |

---

✅ **Idea intuitiva finale**

* **Strong scaling** → “quanto velocemente posso risolvere *lo stesso problema* con più processori?”
* **Weak scaling** → “posso risolvere *problemi sempre più grandi* mantenendo lo stesso tempo?”

Se vuoi, posso anche mostrarti **come appaiono tipicamente i grafici di strong e weak scaling negli esperimenti HPC** e **come interpretarli in un report o paper**.
