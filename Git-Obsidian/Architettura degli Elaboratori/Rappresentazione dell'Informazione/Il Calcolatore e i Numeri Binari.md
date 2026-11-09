## I sistemi Digitali
---
>[!info] Segnale analogico
>Un segnale è ***Analogico*** quando i valori utili che lo rappresentano sono continui (*infiniti*) in un intervallo e non numerabili

>[!info] Segnale digitale
>Un segnale è ***digitale*** quando i valori utili che lo rappresentano sono discreti e finiti
>I calcolatori moderni utilizzano due stati logici (binari)

## L'aritmetica dei Calcolatori
---
Diversa da quella comunemente usata dalle persone

>[!tip] La Precisione

La precisione è con cui i numeri possono essere espressi è finita e predeterminata
 - I numeri devono essere memorizzati entro un limitato spazio di memoria
>[!tip] La Rappresentazione

La rappresentazione è normalmente ottenuta utilizzando il sistema binario
- Molto più adatto a essere maneggiato da un caloclatore

### Numeri a Precisione Finita
Fissate le caratteristiche del numero è determinato anche l'insieme di valori rappresentabili
- Le operazioni con i numeri a precisione finita causano errori ogniqualvolta il loro risultato **non appartiene all'insieme dei valori rappresentabili**
#### Errori possibili
>[!error] Underflow

Si verifica quando il risultato dell'operazione è minore del più piccolo valore rappresentabile

>[!error] Overflow

Si verifica quando il risultato dell'operazione è maggiore del più grande valore rappresentabile

>[!error] Non appartenenza all'insieme

Si verifica quando il risultato dell'operazione, pur non essendo troppo grande o troppo piccolo, non appartiene all'insieme dei valori rappresentabili
##### Esempi
>Numeri a precisione finita con 3 cifre senza virgola e senza segno

- $600+600 = 1200 \to$ overflow
- $300-600 = -300\to$ underflow
- $\displaystyle{\frac{007}{002}}=3,5\to$Non appartenenza all'insieme

#### Proprietà algebriche non rispettate
Le proprietà delle **operazioni** comunemente conosciute non sono **sempre vere**
>[!warning] Proprietà associativa

$a+(b-c)=(a+b)-c$
##### Esempio
$$
\begin{array}{}
400+(300-500) = (400+300)-500 \\
400+(\underbrace{ -200 }_{ \text{Underflow} }) = 700-500
\end{array}
$$

>[!warning] Proprietà distributiva

$a\times(b-c) = a\times b -a\times c$
##### Esempio
$$
\begin{array}{}
50\times (50-40)=50\times 50 -50\times 40 \\
50\times 10 = \underbrace{ 2500 }_{ \text{Overflow} }-\underbrace{ 2000 }_{ \text{Overflow} }
\end{array}
$$
## Sistema Posizionale
---
I sistemi di numerazione posizionali associano alle cifre un diverso valore in **base alla posizione che occupano** nella stringa che compone il numero
- Un sistema di numerazione posizionale è definito dalla ***base utilizzata per la rappresentazione***
### Sistemi posizionali utilizzati
>[!tip] Sistema Decimale

$b=10 \implies 0,1,2,3,4,5,6,7,8,9$

>[!tip] Sistema Binario

$b=2 \implies 0,1$
Ogni cifra, detta *bit* (**B**inary dig**IT**), può essere rappresentata direttamente tramite un livello elettrico di tensione

>[!tip] Sistema Ottale

$b=8\implies 0,1,2,3,4,5,6,7$

>[!tip] Sistema Esadecimale

$b=16\implies 0,1,2,3,4,5,6,7,8,9,A,B,C,D,E,F$
Utilizzato nel linguaggio dell'assebly poichè molto compatto e semplice da scandire.
- Inoltre si presta bene alla traduzione in valori binari
	- Ogni cifra esadecimale corrisponde a 4 cifre binarie

### Conversione tra Basi
#### Da Base $n$ a Base $10$ 
$$
\begin{array}{}
\displaystyle\sum_{i=k}^{n_{d}-1} n_{i}\cdot b^i 
 \\n_{d} = \text{number of digits} \\
k = \text{index of first digit} \\
b = \text{ base}
\end{array}
$$
##### Binario-Decimale
`11111010001`
$1\cdot 2^{10}+1\cdot 2^{9}+1\cdot 2^{8}+1\cdot 2^{7}+1\cdot 2^{6}+0\cdot 2^{5}+1\cdot 2^{4}+0\cdot 2^{3}+0\cdot 2^{2}+0\cdot 2^{1}+1\cdot 2^{0}$
$1024+512+256+128+64+0+16+0+0+0+1$

##### Ottale-Decimale
`3721`
$3\cdot 8^3+7\cdot 8^2 +2\cdot 8^1+1\cdot 8^0$
$1536+448+16+1$

##### Esadecimale-Decimale
`7D1`
$7\cdot 16^2+13\cdot 16^1+1\cdot16^0$
$1792+208+1$

#### Binario $\Leftrightarrow$ Ottale/Decimale
Dato che una cifra del sistema ottale è rappresentabile esattamente con tre cifre del sistema binario
- La conversione può essere ottenuta raggruppando le cifre binarie a 3 a 3 ***a partire dalla virgola***
- Discorso simile per la base esadecimale, basta raggruppare le cifre a 4 a 4 ***a partire dalla virgola***
È possibile anche il procedimento inverso

##### Binario-Ottale
$$
\underbrace{ 001 }_{ 1 }\underbrace{ 100 }_{ 4 }\underbrace{ 101 }_{ 5 }\underbrace{ 001 }_{ 1 }\underbrace{ 000 }_{ 0 }.\underbrace{ 101 }_{ 5 }\underbrace{ 101 }_{ 5 }\underbrace{ 100 }_{ 4 }
$$
##### Binario-Esadecimale
$$
\underbrace{ 0111 }_{ 7 }\underbrace{ 1011 }_{ B }\underbrace{ 1010 }_{ A }\underbrace{ 0011 }_{ 3 }.\underbrace{ 1011 }_{ B }\underbrace{ 1100 }_{ C }\underbrace{ 0100 }_{ 4 }
$$

#### Decimale $\Leftrightarrow$ Binario
Si procede con i seguenti calcoli:
1. Sottrarre al numero da decomporre la più grande potenza di $2$ minore del numero
2. Il processo viene reiterato al resto della sottrazione
3. Il risultato binario si ottiene ponendo a uno le cifre delle potenze che sono state utilizzate
$$
\begin{array}{}
1492.25 = 2^{10}+468.25 \\
468.25 = 2^8+212.25 \\
212.25 = 2^7+84.25 \\
84.25 = 2^6+20.25 \\
20.25 = 2^4 +4.25 \\
4.25 = 2^2 +0.25 \\
0.25 = 2^{-2}
\end{array}
\implies 10111010100.01
$$
Questo procedimento è generalizzabile per passare da base decimale a qualsiasi base
1. Sottrarre al numero da decomporre la più grande potenza di $n$ minore del numero
2. Controllare quante volte la potenza di $n$ può stare nel numero da convertire
3. Il processo viene reiterato al resto della sottrazione
4. Il risultato binario si ottiene ponendo a uno le cifre delle potenze che sono state utilizzate
##### Decimale-Base 3
$$
\begin{array}{}
1492_{10} = 2 \cdot 3^6 34\\
34 = 0\cdot 3^5 +34 \\
34 = 0\cdot 3^4 +34 \\
34 = 1 \cdot 3^3 +7\\
7 = 0\cdot 3^2 +7\\
7 = 2\cdot 3^1 +1 \\
1 = 1\cdot 3^0
\end{array}
\implies 2001021_{3}
$$
## Calcolatore e i numeri Binari
---
La più importante unità di misura dell'informazione manipolata è il `BYTE` composto da 8 `BIT`
- Nel `BYTE` il `BIT` più a destra è quello meno significativo
- Il `BIT` più a sinistra è quello più significativo
Sequenze più lunghe di `BYTE` sono denominate `WORD`
- La loro lunghezza dipende dalle caratteristiche del sistema, ma è sempre multiplo del `BYTE`: 
	- `16/32/64/128 BIT`

>[!info] Intervalli Rappresentabili con $n$ `BIT`

| n   | Numero di Combinazioni       | Intervallo                     |
| --- | ---------------------------- | ------------------------------ |
| 1   | $2$                          | `0-1`                          |
| 8   | $256$                        | `0-255`                        |
| 16  | $65.536$                     | `0-65535`                      |
| 32  | $4.294.697.296$              | `0-4.294.697.295`              |
| 64  | $18.446.744.073.709.551.616$ | `0-18.446.744.073.709.551.615` |
### Numeri Negativi
Nella storia sono state utilizzate diverse modalità di rappresentazione dei numeri negativi
- La codifica ideale prevede:
	- Una sola rappresentazione per lo $0$
	- Lo stesso insieme di valori positivi e negativi rappresentabili
- Entrambi le proprietà sono ***impossibili da ottenere insieme***
#### Modalità di Rappresentazione
##### Grandezza e segno

Con questa rappresentazione il `BIT` più significativo viene **utilizzato per il segno**
- Con `0` si indicano i valori positivi
- Con `1` si rappresentano i valori negativi

>[!bug] Problema: doppia rappresentazione dello $0$

##### Complemento a due

Con questa rappresentazione il bit più significativo viene **comunque usato per il segno**

Codifica a *due passaggi*:
1. Negare tutti i bit
	1. `0101`$\to$ `1010`
2. Si aggiunge uno al risultato
	1. `1010 + 0001 = 1011`

In caso di riporto nella ottava cifra, *non è necessario aggiungere la nona cifra*, basta ignorare l'ultimo riporto.

###### Pro
- I numeri positivi sono rappresentati esattamente come prima
- Mentre per conoscere i numeri negativi bisogna ripetere i passaggi usati nella conversione
	1. `1011`$\to$`0100`
	2. `0100 + 0001 = 0101`
- Unica rappresentazione dello `0`
- La sottrazione è eseguibile ***semplicemente*** sommando il primo numero con il secondo numero in complemento a $2$

###### Operazioni in colonna con complemento a due

Il riporto generato dai bit più a sinistra, esso viene ignorato
- Se gli addendi sono di segno opposto non si può verificare un *overflow*
- L'*overflow* si verifica se gli ultimi due riporti nel fare la somma sono **diversi fra di loro**
-  Gli ultimi due riporti sono i " segnalatori di overflow"
##### Eccesso $2^{m-1}$

Consente di rappresentare i numeri come *somma di se stessi con* $2^{m-1}$ dove $m$ è il numero di `BIT` utilizzati per rappresentare il valore
- Si noti che il sistema è identico al complemento a due con il bit di segno invertito
- Per rappresentare il numero in eccesso $2^{m-1}$ basta sommare al numero il numero massimo rappresentabile con $m-1$ bit 
	- `0100` $\to$ 4 `BIT`
	- `0100 + 0111 = 1011`
- Visualizzandolo nella retta dei numeri naturali sarebbe come *"spostare" il minimo e il massimo numero rappresentabile* a sinistra del valore massimo rappresentabile con $n-1$`BIT` ($2^{m-1}$)

Anche in questa codifica è possibile fare la sottrazione come addizione di un numero con l'altro numero codificato in eccesso $2^{m-1}$