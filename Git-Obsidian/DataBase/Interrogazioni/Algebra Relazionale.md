
>[!definizione] Definizione
> L'***algebra relazionale*** è un linguaggio procedurale di tipo algebrico i cui *operandi sono relazioni*.
>È un linguaggio formale per [[Linguaggi di Manipolazione|interrogare]] un [[Modello Relazionale]].


>[!tip] Curiosità
>L'insieme delle operazioni dell'*algebra relazionale* **non** è ***turing-complete***

## Operatori
---
>[!cite] Operatori
>L’***algebra relazionale*** è costituita da un insieme di **operatori di base** che si applicano a una o più relazioni e che *producono una relazione*.

La ***semantica*** di ogni operatore si definisce specificando:
- Come lo *schema del risultato* **dipende** dallo *schema degli operandi*.
- Come lo *stato della relazione risultato* **dipende** dagli stati delle *relazioni in ingresso*.

Gli operatori si possono ***comporre***, dando luogo a espressioni algebriche di *complessità arbitraria*.

>[!help] Completezza
>Si *dimostra* che l’insieme $\{ \sigma, \pi, \rho, \cup, -, \bowtie \}$ degli operatori di base dell’algebra relazionale è ***completo***, ovvero ogni altra operazione può essere espressa come ***composizione di operazioni*** di questo insieme.
### Unari

#### Selezione
>[!tl;dr] Definizione
>L'operatore di ***selezione*** $\sigma$, permette di *selezionare* un sottoinsieme delle tuple di una relazione, attraverso un'**espressione booleana** $F$

>**Sintassi:**

$$
\sigma_{F}(r)=\{ t|t\in r \text{ AND }F(t)=\text{True} \}
$$

$F$ si compone di ***predicati*** connessi da `AND` ($\wedge$), `OR` ($\vee$) e `NOT` ($\neg$).
Ogni predicato è del tipo $A\ \theta \ c$ oppure $A\ \theta\  B$ dove:
- $A\in X$ e $B\in X$ sono ***attributi***.
- $c\in \text{dom}(A)$ è una ***costante***.
- $\theta$ è un ***operatore di confronto***: $\theta\in\{ =,\neq, <,>,\leq, \geq\}$

>[!caution] Valutazione della formula $F$
>Per gli ***operatori booleani*** $\vee, \wedge, \neg$ valgono le regole dell'[[Algebra di Bool]].

##### Esempio
> **ESAMI**(<u>Matricola</u>,<u>CodCorso</u>, Voto, Lode)

>[!question] Selezionare le tuple di esami con voto $30$ ma senza lode.

$$
\sigma_{(\text{Voto}=30)\text{ AND (Lode}=\text{'no'})}(\text{ESAMI})
$$
#### Proiezione
>[!tl;dr] Definizione
>L'operatore di ***proiezione*** $\pi$, è ortogonale alla *selezione*, in quanto permette di selezionare un sottoinsieme $Y$ degli *attributi di una relazione*.

>**Sintassi:**

$$
\pi_{Y}(r)=\{ t[y]|t\in r \}
$$

##### Cardinalità del Risultato
>[!help] Idea
>In generale la cardinalità di $\pi_{Y}(r)$ è minore o uguale della cardinalità di $r$
>>[!missing] La proiezione "elimina i duplicati".
>
>L'uguaglianza è garantita se e solo se $Y$ è una [[Vincoli di Integrità#Superchiave|superchiave]] di $R(X)$

Si noti che il risultato ammette la possibilità che "*per caso*" la cardinalità non vari anche se $Y$ **non** è superchiave.
##### Esempio
>**CORSI**(<u>CodCorso</u>, Titolo, CodDocente, Anno)

>[!question] Selezionare il codice del corso e codice docente di tutti i corsi.

$$
\pi_{\text{CodCorso,CodDocente}}(\text{CORSI})
$$
#### Ridenominazione
>[!tl;dr] Idea
>Operatore **non fondamentale**.
>L'operatore di ***ridenominazione*** $\rho$ modifica lo schema di una relazione *cambiando* i *nomi* di uno o più attributi.

>**Sintassi:**

$$
R(XZ),\rho_{\ Y\leftarrow X }(R)
$$
- Cambia lo schema in $YZ$, *lasciando invariati* i valori delle tuple.
### Binari

#### Join Naturale
>[!tl;dr] Idea
>L'operatore di ***join naturale*** $\bowtie$, combina le tuple di due relazioni sulla base dell'*uguaglianza* dei valori negli **attributi comuni** alle due relazioni (quelli *presenti* in $X_{1}\cap X_{2}$)

***Ogni tupla*** che compare nel risultato del *join naturale* di $r_{1}$ e $r_{2}$, ([[Modello Entity-Relationship#Estensione di un'entità|estensioni]] rispettivamente di $R_{1}(X_{1})$ e $R_{2}(X_{2})$) è ottenuta come combinazione di una tupla di $r_{1}$ con una tupla di $r_{2}$.

>**Sintassi:**

$$
r_{1}\bowtie r_{2}=\{ t|t[X_{1}]\in r_{1} \text{ AND }t[X_{2}]\in r_{2}\}
$$
##### Esempio
>**ESAMI**(<u>Matricola</u>,<u>CodCorso</u>, Voto, Lode)
>**CORSI**(<u>CodCorso</u>, Titolo, CodDocente, Anno)

$$
ESAMI\bowtie CORSI
$$
>[!abstract] Esami


| <u>Matricola</u> | <u>CodCorso</u> | Voto | Lode |
| ---------------- | --------------- | ---- | ---- |
| 29323            | 483             | 28   | no   |
| 29323            | 913             | 26   | no   |
| 35467            | 913             | 30   | si   |
>[!abstract] Corsi

| <u>CodCorso</u> | Titolo              | CodDocente | Anno |
| --------------- | ------------------- | ---------- | ---- |
| 483             | Analisi             | 0201       | 1    |
| 913             | Sistemi Informativi | 0123       | 2    |

>[!caution] Esami$\bowtie$ Corsi


| Matricola | CodCorso | Voto | Lode | Titolo              | CodDocente | Anno |
| --------- | -------- | ---- | ---- | ------------------- | ---------- | ---- |
| 29323     | 483      | 28   | no   | Analisi             | 0201       | 1    |
| 29323     | 913      | 26   | no   | Sistemi Informativi | 0123       | 2    |
| 35467     | 913      | 30   | si   | Sistemi Informativi | 0123       | 2    |

##### Proprietà e Osservazioni
>[!abstract] Proprietà
>Il join naturale è ***commutativo*** e ***associativo***:
>- $r_{1}\bowtie r_{2}=r_{2}\bowtie r_{1}$
>- $r_{1}\bowtie r_{2} \bowtie r_{3}=(r_{1}\bowtie r_{2})\bowtie r_{3}$

>[!warning] Tuple Dangling
>È possibile che una tupla delle due relazioni *non faccia match* con nessuna tupla dell'altra relazione.
>In tal caso la tupla è denominata ***dangling***.

Nel caso limite è quindi possibile che il risultato del join sia ***vuoto***.

> Ne consegue che la cardinalità del *join* $|r_{1}\bowtie r_{2}|$ è:

$$
0\leq |r_{1}\bowtie r_{2}|\leq|r_{1}|\cdot |r_{2}|
$$
>[!hint] Osservazione
>Se $X_{1}\cap X_{2}$ è una [[Vincoli di Integrità#Chiave|chiave]] di $R_{1}(X_{1})$, e *foreign key* in $R_{2}(X_{2})$ allora $|r_{1}\bowtie r_{2}|=|r_{2}|$
>>[!missing] Vera in assenza di valori nulli

>[!hint] Osservazione
>Se due relazioni hanno lo ***stesso schema***, $X_{1}=X_{2}$ allora il join naturale equivale all'intersezione ($\cup$) delle due relazioni.

>[!warning] Prodotto Cartesiano
>Se non vi sono attributi in comune $X_{1}\cap X_{2} = \varnothing$, allora, il join naturale equivale al ***prodotto cartesiano***.

##### Self Join
>La ridenominazione permette di eseguire in modo significativo il join di una relazione con se stessa.

>[!example] Esempio

**Genitori**(Genitore, Figlio)
>[!question] Per trovare nonni e Nipoti

$$
\rho_{\text{ Nonno,Genitore }\leftarrow\text{ Genitore,Figlio} }\text{(GENITORI)}\bowtie\text{GENITORI}
$$

#### Differenza
> Poiché le relazioni sono insiemi, sono ben definite le operazioni di *unione* e *differenza*.

>[!tl;dr] Idea
>Operazione che permette di **escludere** dalle tuple di una relazione le tuple *uguali* di un’altra relazione.

>**Sintassi:**

$$
r_{1}- r_{2} = \{ t | t\in r_{1} \text{ AND } t\notin r_{2} \}
$$

>[!warning] Attenzione
>Applicato a relazioni con lo ***stesso insieme di attributi***.
#### Unione
>[!tl;dr] Idea
>Operazione che restituisce tutte le tuple presenti nelle relazioni A e B **senza ripetizioni**.

>**Sintassi:**

$$
r_{1}\cup r_{2}=\{ t| t\in r_{1} \text{ OR } t\in r_{2}\}
$$
>[!warning] Attenzione
>Applicato a relazioni con lo ***stesso insieme di attributi***.

##### Intersezione
>[!hint] Nota Bene
>L'intersezione si può scrivere come:
>$$r_{1} \cap r_{2} = r_{1}-(r_{1}-r_{2})$$

## Operatori derivati

### Theta Join (θ-join)
**Sintassi:**
```
r1 ⋈_F r2 = σ_F(r1 × r2)
```
- Combinazione fra join e selezione.

### Outer Join
Mantiene le tuple **dangling** aggiungendo i valori mancanti sotto forma di **NULL**.
- Una tupla di una delle relazioni operande che non fa “match” con alcuna tupla dell’altra relazione.

#### Tipi di Outer Join
- **Left Outer Join**
- **Right Outer Join**
- **Full Outer Join**

## Espressioni e viste

- Assegnare ad una soluzione un nome per facilitarne l’uso nelle query.