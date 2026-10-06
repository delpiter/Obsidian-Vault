## Deep Learning e Generative AI
> A partire dal 2018 sono addestrati Large Language Models (modelli generativi basati su reti neurali profonde di tipo Transformer) su enormi quantità di testo

Sebbene questi modelli siano stati "prevalentemente" addestrati a eseguire compiti semplici (predire la prossima parola in una frase): 
- Emergono capacità reasoning e comprensione oltre alle aspettative (sparks of AGI). 
- L’addestramento su codice sembra essere determinante a tal fine


Le tecniche di deep learning raggiungono e superano lo stato dell’arte in molteplici applicazioni. Talvolta superano anche le prestazioni umane.
Alcuni esempi di applicazione possono essere:
> Perception (visual, auditory)
- Object Detection and Localization
- Face Recognition, Pedestrian Detection
- Autonomous Car and Drones 

> Language
- Large Language Models (Chat and Agents).
- Translation, Summarization, Question Answering
-  Generazione Immagini da Testo.
- Programming Assistant (e.g. Github Copilot, Claude Code).

> Medicine, Biochemistery, Human Computer Interfaces
- Medical Image Analysis
- Protein Folding, Biomolecule combination
- Brain Implants (es. Neuralink)


Con l'avvento del deep learning i big dell'ICT investono molto nel settore reclutando talenti e acquistando startup.

### Nearest Neighbor
Data una metrica $dist(\cdot)$ nello spazio multidimensionale (es distanza euclidea), il classificatore nearest neighbor classifica un pattern $x$ con la stessa classe dell'elemento $x'$ ad esso più vicino nel training set.

$$
dist(x,x')=\min_{x_{i} \in TS} \{ dist(x,x_{i}) \}
$$
Invece di derivare dai dati le distribuzioni condizionali delle classi per poi usare la regola di Bayes, questo classificatore cerca in modo pragmatico di massimizzare direttamente la probabilità a posteriori
Infatti se $x'$ è molto vicino a $x$ è lecito supporre che:
$$
P(w_{i}|x) \approx P(w_{i}|x')
$$

> [!hint] Voronoi
> La regola nearest neighbor produce un partizionamento dello spazio, noto come ***tassellazioe di Voronoi***.

Ogni elemento determina un tassello all'interno del quale i pattern saranno assegnati alla stessa classi di $x_{i}$.
- La regola di classificazione è piuttosto radicale, basta un elemento del training set non affidabile affinché tutti i pattern nelle vicinanze siano etichettati non correttamente.

Un metodo più robusto può essere visto come una estensione del NN


> [!help] K-nn
> La regola k-nearest neighbor determina i $k$ elementi più vicini al pattern $x$ da classificare (con $k$ iperparametro).

Ogni pattern tra i $k$ più vicini "*vota*" per la classe cui esso stesso appartiene.
- Il pattern $x$ viene assegnato alla classe che ha ottenuto il ***maggior numero di voti***.

Con training set infiniti la classificazione $k$-$nn$ si dimostra migliore di NN e all'aumentare di $k$ l'errore converge all'errore Bayesiano.
- Nella pratica aumentare $k$ significa estendere l'ipersfera di ricerca andando a sondare la probabilità a posteriori ***lontano dal punto di interesse***.

#### Complessità computazionale
L’utilizzo di un classificatore NN o k-NN nel caso di training set di elevate dimensioni può diventare problematico:ù
- Necessario memorizzare tutti i pattern del Training Set
- Per ogni classificazione è necessario calcolare la distanza del pattern da classificare da tutti i pattern del training set e ordinare (parzialmente le distanze) per ottenere le più piccole.

#todo Prototipi di classi e metriche

#### Normalizzazione
Per evitare problemi legati a diversi spazi di variazioni delle feature si consiglia di normalizzare i pattern.

Le normalizzazione più comuni sono:

Min-max scaling
- Per ogni feature i-esima si calcolano il massimo max_i e il minimo min_i e si applica una trasformazione lineare che mappa min a 0 e max a 1.

$$
x'=\frac{x-\min_{i}}{\max_{i}-\min_{i}}
$$
Pochi punti "outlier" possono causare diversi problemi sulla classificazione.

Standardization
- Per ogni feature i-esima si calcola la media $mean_{i}$ e la devizione ztandard $stddev_{i}$ e si trasformano i valori come

$$
x'=\frac{x-mean}{stddev_{i}}
$$
Dopo la trasformazioni hanno media $0$ e deviazione standard $1$.


> [!warning] Attenzione
> parametri della normalizzazione (es. minimi, massimi) si calcolano ***sul solo training set*** e la trasformazione si applica a tutti i dati. Nel caso di k-fold cross-validation la normalizzazione dovrebbe essere ripetuta k volte (uso di pipeline in scikit-learn).


#### Whitening Transform
Costa molto e non produce chiari vantaggi

#### Metric Learning

> [!hint] Obbiettivo
> L'obbiettivo è determinare una trasformazione degli input che: "avvicini" pattern della stessa classe e "allontani" pattern di classi diverse.

La distanza euclidea nello spazio originale è:
$$
dist(a,b) = \sqrt{ (a-b)^{t}(a-b) } = \mid\mid a-b \mid\mid_{2}
$$
#addLink norma 2

Un tipico approccio di metric learning lineare determina una matrice $G$ che trasforma gli input e continua ad applicare la distanza euclidea agli input trasformati.
$$
dist(a,b)=||Ga-Gb||_{2}
$$
Una possibile soluzione nell'ambito della riduzione di dimensionalità con il Linear Discriminant Analysis.

$$
dist(a,b)=||G\phi(a)-G\phi(b)||_{2}
$$
dove $\phi$ è una funzione non lineare.

