## Language Model
---
> [!info] Modello Generativo
> Un ***modello generativo*** è una *rappresentazione finita* (attraverso i parametri del modello) di una ***distribuzione di probabilità***, su uno spazio dati possibilmente infinito e, quando presenti nel modello, sulle relative *etichette di classificazione*.

Il sequence modelling considera un *dataspace* dove un dato è una ***sequenza ordinata di simboli***.
- Se questa sequenza non ha una lunghezza massima, il data space modellato è infinito.

> [!cite] Language Model
> Un ***language model*** è un modello generativo in cui lo spazio dei dati  è $\Sigma^{*}$.

Per esempio una sequenza senza limiti di [[Grammatiche a Struttura di Frasi#Tokenization|token]] in $\Sigma$.

> ***Esempio***

Una [[Grammatiche Probabilistiche#Grammatiche Probabilistiche Libere dal Contesto|PCFG]] $G$ consistente rappresenta una distribuzione di probabilità $P_{G}(T)$ su degli alberi sintattici, che include
- $\Sigma^{*}$ stringhe (*data space*)
- Le categorie sintattiche usate per generarle.

I parametri del modello sono le probabilità delle categorie che normalmente sono apprese durante la ***fase di training***.

### Equivalenze tra Modelli Generativi
> [!info] 
> Due ***modelli generativi*** $M_{1}$ e $M_{2}$ con lo stesso dataspace $D$ sono equivalenti *se rappresentano la stessa distribuzione di probabilità* su $D$.

In particolare due Language Model $M_{1}$ e $M_{2}$ con lo stesso alfabeto $\Sigma$ sono equivalenti *se rappresentano la stessa distribuzione di probabilità* su $\Sigma^{*}$
- In generale, per ciascun [[#Mixture of Bag Of Words Model]] c'è un equivalente [[Hidden Markov Model#Mixture of BoW come Terminating HMM|THMM]] *consistente*.
- Non vale il contrario.
### Mixture of Bag Of Words Model
---
> Esempio più semplice di *Language model*.

 Un ***mixture BoW model*** ha delle categorie per classificare le frasi ($\Sigma^{*}$), la generazione delle frasi si basa sui seguenti parametri del modello:
- La distribuzione di probabilità sulle categorie, usata principalmente per generare l'intera frase di una categoria.

> [!tldr] Idea
> Per ciascuna categoria ogni parola (*token*) è inserita nella *sacca* (bag), più la parola è comune (più probabile) più la inserisco nella sacca.

Una sacca di una categoria scelta viene usata per generare ***tutte le frasi possibili di quella categoria***.
- Per generare una frase, pesco una parola a caso dalla sacca e una volta segnata, la re-inserisco nella sacca per il prossimo pescaggio.

> [!done] Fine del processo
> Continuo a pescare finché non pesco un ***token speciale*** `<EOS>` end of string/sentence.
> Questo token deve avere una probabilità **diversa da zero**.

> [!quote] Non un buon modello generativo ma un buon classificatore

> [!hint] n-Gram
> Tecnicamente, un `BoW` è un ***n-gram model*** con $n=1$.
> Un ***n-gram model*** è un modello dove la probabilità di ciascuna parola *dipende* dalle $n-1$ precedenti.

### Generazione di una Stringa
> [!quote] Generazione condizionata
> La ***probabilità di generazione*** di una stringa $w=t_{1:n}\in\Sigma^{*}$, una sequenza di token $t_{1},t_{2},\dots,t_{n+1}$ con $t_{n+1}=<eos>$ ***data una categoria*** è:
> $$P(Categ, w)=P(Categ)P(w\mid Categ)=P(Categ)\prod_{i=1}^{N(w)}P(t_{i}\mid Categ)$$

Dove $N(w)=| w| +1=N+1$ è il numero di token necessari per generare $w$.

> La probabilità di generazione totale non è altro che la somma delle probabilità di generazione condizionate su ogni categoria.

$$
P(w)= \sum_{Categ}P(Categ,w)
$$


> [!done] Questo rappresenta la [[Grammatiche Probabilistiche#Probabilistic Formal Language|Probabilistic Formal Language]].
>

###### Esempio
> Categorie: $\{ \text{Business}, \text{Weather} \}$ con distribuzione $P(B)=0.6$ e $P(W)=0.4$

Per ogni categoria:

| Token $t$     | $P(t\mid\text{Business})$ | $P(t\mid\text{Weather})$ |
| ------------- | ------------------------- | ------------------------ |
| `<EOS>`       | $0.08$                    | $0.08$                   |
| $[cloudy]$    | $0.01$                    | $0.16$                   |
| $[continued]$ | $0.04$                    | $0.04$                   |
| $[heavy]$     | $0.05$                    | $0.06$                   |
| $[pound]$     | $0.15$                    | $0.01$                   |
| $[rain]$      | $0.01$                    | $0.21$                   |
| $[stocks]$    | $0.15$                    | $0.01$                   |
| $[to]$        | $0.04$                    | $0.04$                   |
| $\dots$       | $\dots$                   | $\dots$                  |
La probabilità di generare la frase:
- $w=\text{"Heavy rain continued to pound"}$

Può essere generata sia con la categoria *business* sia che con la categoria *weather*.
- $P(\text{Business}) \cdot P(w \mid \text{Business})$, dove:

$$
\begin{align*} P(w \mid \text{Business}) =& P(\text{[heavy]} \mid \text{Business}) \cdot P(\text{[rain]} \mid \text{Business}) \cdot P(\text{[continued]} \mid \text{Business}) \\ & \cdot P(\text{[to]} \mid \text{Business}) \cdot P(\text{[pound]} \mid \text{Business}) \cdot P(\text{<EOS>} \mid \text{Business})\end{align*}
$$
Quindi:
$0.05 \cdot 0.01 \cdot 0.04 \cdot 0.04 \cdot 0.15 \cdot 0.08 = 0.0000000096\implies 0.6\cdot 0.0000000096 = 0.00000000576 = P(\text{Business}) \cdot P(w \mid \text{Business})$

- $P(\text{Weather}) \cdot P(w \mid \text{Weather})$, dove:

$$
\begin{align*} P(w \mid \text{Weather}) =& P(\text{[heavy]} \mid \text{Weather}) \cdot P(\text{[rain]} \mid \text{Weather}) \cdot P(\text{[continued]} \mid \text{Weather}) \\ & \cdot P(\text{[to]} \mid \text{Weather}) \cdot P(\text{[pound]} \mid \text{Weather}) \cdot P(\text{<EOS>} \mid \text{Weather})\end{align*}
$$
Quindi:
$0.06 \cdot 0.21 \cdot 0.04 \cdot 0.04 \cdot 0.01 \cdot 0.08 = 0.000000016128\implies 0.4\cdot 0.000000016128 = 0.0000000064512 = P(\text{Weather}) \cdot P(w \mid \text{Weather})$


> [!done] Conclusione
> La ***probabilità di generare la frase*** $w$ è uguale alla *somma delle probabilità* calcolate e la categoria che genera la frase con più probabilità è $\text{Weather}$