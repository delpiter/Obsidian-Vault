## Problemi Astratti
---
>[!info] Definizioni
>>[!abstract] Problema
>>Un problema è un'***entità astratta***
>
>>[!done] Istanza
>>Una ***istanza del problema*** è un suo *caso particolare* in cui vengono specificati tutti i suoi elementi costitutivi
>
>>[!caution] Programma
>> Un ***programma*** risolve un problema se può generare una soluzione in ***corrispondenza di una qualunque istanza***

### Risolvibilità
>*Per poter risolvere un problema con un programma è necessario codificare l'istanza da risolvere con una stringa binaria comprensibile dal programma*

>[!abstract] Codifica
>La ***codifica*** è la corrispondenza fra l'insieme delle istanze del problema e un insieme di stringhe binarie
>$$e:I\to\{ 0,1 \}*$$

Un algoritmo risolve un problema in tempo $O(T(n))$ se
- Quando gli viene fornita la codifica binaria di una istanza $i$ di lunghezza $n=|i|$, produce una soluzione al più in un tempo $O(T(n))$

### Problemi Decisionali
>[!info] Definizione
>I ***problemi decisionali*** sono una classe di problemi dove per ogni possibile ingresso un algoritmo deve scegliere una di due possibili risposte: "*si*" o "*no*"
>Si tratta quindi della classe delle funzioni computabili del tipo:
>$$f:N\to\{ 0,1 \}$$

#### Esempi
>[!tip] Problema del sottografo Completo

Dati un [[../Strutture Dati/Grafi/I Grafi|grafo]] $G$ e un intero $n$, stabilire se il grafo $G$ contiene un sottografo completo con $n$ vertici

>[!tip] Problema del cammino hamiltoniano

Dato un [[../Strutture Dati/Grafi/I Grafi|grafo]] $G$ stabilire se esiste un cammino che tocchi tutti i vertici di $G$ una e una sola volta

>[!tip] Problema del cammino euleriano

Dato un grafo $G$ stabilire se esiste un cammino che percorra tutti gli archi di $G$ una e una sola volta

>[!tip]  Problema *SAT*

^969e0e

Data una [[../../Definizioni/Definizioni_Algoritmi#Conjunctive Normal Form|CNF]] $F$ stabilire se $F$ è ***soddisfacibile*** (***SAT***-*isfiability*):
- Cioè, se esiste un assegnamento di valori $0$ e $1$ alle variabili in $F$ tale per cui il valore di $F$ per quell'assegnamento è $1$

>[!tip] Problema $k$-SAT

Data una [[../../Definizioni/Definizioni_Algoritmi#K-CNF|k-CNF]] $F$ stabilire se $F$ è ***soddisfacibile***

#### Problemi di Ottimizzazione
>*Spesso il problema non richiede di rispondere si o no ma di trovare il massimo o il minimo di una funzione*

Questi sono [[../../Definizioni/Definizioni_Algoritmi#Problema di Ottimizzazione|Problemi di Ottimizzazione]]
- Sono comunque ***riconducibili a problemi decisionali***

>[!caution] Riduzione
>Mi riconduco ad un problema decisionale applicato ad una ricerca binaria
>Aggiungendo un fattore logaritmico
>*Problema di ottimizzazione* $= log\cdot$ *Problema Decisionale*

## Riducibilità Polinomiale
---
>[!info] Definizione
>Un *problema decisionale* $g:N\to\{ 0,1 \}$ è ***riducibile polinomialmente*** a $f:N\to\{ 0,1 \}$ se esiste una funzione $h$, calcolabile in tempo polinomiale, tale che $\forall x:$
>$$g(x)=f(h(x))$$
>>[!done] Notazione
>>$g\leq_{p} f$

![[attachements/Reduction.png]]

### Riduzione: Metodologia
>*Riducendo a $Q$ un qualunque problema $P'$ noto essere in $NPC$, implicitamente si riducono a $Q$ tutti i problemi in $NP$*

>[!abstract] Per dimostrare che un problema $Q$ è in $NPC$ si può:

1. Mostrare che $Q\in NP$
2. Selezionare un problema $P'\in NPC$
3. Progettare un algoritmo polinomiale che calcola una funzione $h$ che fa corrispondere ad ogni istanza di $P'$ una istanza di $Q$
4. Dimostrare che $h$ è tale per cui $x\in P'\iff h(x)\in Q,\quad\forall x$
