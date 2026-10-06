## Metriche per la misura di prestazioni
---
Una possibilità consiste nell'utilizzare direttamente la ***funzione obiettivo*** per quantificare le **prestazioni**.
In genere però si preferisce una misura legata direttamente alla semantica del problema.


> [!todo] Accuratezza
> In un *problema di Classificazione*, l’***accuratezza*** di classificazione $[0…100\%]$ è la percentuale di pattern correttamente classificati. L’errore di classificazione è il complemento. 

$$
\text{Accuratezza}=\displaystyle{\frac{\text{Pattern correttamente classificati}}{\text{Pattern Classificati}}}
$$
- L'errore si ricava tramite la formula $\text{Err}=100 - \text{Accuratezza}$


> [!warning] Cardinalità Sbilanciate
> in un problema di ***classificazione binaria***, se una delle due classi è *rara*, un classificatore "dummy" che non la predice mai potrebbe raggiungere un’accuratezza di classificazione vicina al $100\%$. Meglio usare Precision/Recall in questo caso

> Per la regressione

Si valuta in genere l’`RMSE` (***Root Mean Squared Error***) ovvero la radice della media dei quadrati degli scostamenti tra valore vero e valore predetto (ulteriori approfondimenti nel seguito).
$$
RMSE = \sqrt{ \frac{1}{N}\sum_{i=1\dots N}(pred_{i}-true_{i})^{2} }
$$

### Matrice di confusione
> [!abstract] Definizione
> La ***matrice di confusione*** confusion matrix è molto utile nei problemi di classificazione per capire come sono distribuiti gli errori.

> Esempio: Classificazione delle cifre (10 classi)
- Assumiamo che sulle righe ci siano le classi ***True*** (o *Real* o *Actual*) e sulle colonne le classi *Predicted*.
- Una cella $(r,c)$ riporta il numero di casi in cui il sistema ha predetto di classe $c$ un pattern di classe vera $r$.
- Idealmente la matrice dovrebbe essere [[../Algebra e Geometria/Applicazioni/9 - Matrici Diagonali|diagonale]].
	- Fuori dalla diagonale indicano casi di errore.

![[attachements/Pasted image 20260925092812.png]]

### Classificazione binaria
> [!info] 
> Dato un [[Tipi di Machine Learning#Classificazione|classificatore binario]] e $T=P+N$ pattern da classificare (positivi $P$ e negativi $N$) il risultato di ciascuno dei tentativi di classificazione può avere quattro casi.

- *True* **Positive**
- *True* **Negative**
- *False* **Positive**, Errore di tipo $I$ o $False$
- *False* **Negative**, Errore di tipo $II$ o $Miss$

![[attachements/Pasted image 20260925093656.png]]

Passando da errori a frequenze/probabilità (che corrisponde a normalizzare per righe la confusion matrix):
- $TPR=\frac{TP}{P}$ (true positive rate)
- $TNR=\frac{TN}{N}$
- $FPR=\frac{FP}{N}$
- $FNR=\frac{FN}{P}$

Con questa notazione l'accuratezza di classificazione può essere scritta come:
$$
Accuracy = \frac{TP+TN}{P+N}
$$

### DET e ROC
> L’output di un classificatore #addLink è spesso ***probabilistico*** (valore continuo in $[0\dots1]$).

> [!summary] Soglia
> In una ***problema di classificazione*** binaria i pattern possono essere predetti come **positivi** (o **negativi**) confrontando l’output (della classe positiva) con una soglia $t$.

Soglie restrittive (*elevate*) **riducono** i ***false positive*** a discapito dei ***false negative***
- viceversa soglie tolleranti (*basse*) riducono i false negative a discapito dei false positive.

![[attachements/Pasted image 20260925094833.png]]

Le due curve possono essere "*condensate*" in una curva `DET` (***Detection Error Tradeoff***) che nasconde la soglia.
- Esprime il rapporto dei falsi negativi in funzione dei falsi positivi.

Piuttosto usata è anche la rappresentazione `ROC` (***Receiver Operating Characteristic***) che in ordinata riporta True positive invece di False negative (ROC è ribaltata verticalmente rispetto a DET).

![[attachements/Pasted image 20260925095240.png]]

Un confronto può essere fatto "*mediando*" sui diversi punti di lavoro del sistema. L’area sotto la curva `ROC` (`AUC`) è uno scalare in $[0,1]$ che caratterizza la prestazione media (maggiore è, meglio è). 
- Può essere calcolata come integrale numerico attraverso il metodo dei trapezi.
#### Notazione
> [!hint] Tip
> Una notazione molto usata in information retrieval e in generale nelle applicazioni di detection o classificazione è ***Precision-Reccal***.

Precision/Recall sono definiti a partire da $TN$, $TP$, $FP$, $FN$

La precisione indica quanto è accurato il sistema
$$
Precision = \frac{TP}{TP+FP}
$$

Risponde alla domanda
> [!question] Che percentuale di elementi selezionati è pertinente?
> 

Recall indica quanto il sistema è selettivo
$$
Reccal=\frac{TP}{TP+FN}=TPR
$$

> [!question] Tra tutti gli elementi pertinenti, quanti sono stati selezionati?
> 


Nella classificazione *multi-classe*, **precision** e **recall** si possono calcolare per ciascuna classe (considerando la classe come Positive e gli esempi di tutte le altre come Negative), come nell'esempio sopra.

##### Average Precision

> [!abstract] 
> **AP** è una sorta di AUC sul grafico Reccal/Precision

$$
AP=\sum_{n}(R_{n}-R_{n-1})P_{n}
$$
