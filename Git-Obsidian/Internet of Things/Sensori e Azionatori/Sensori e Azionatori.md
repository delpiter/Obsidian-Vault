> Un [[../Sistemi Embedded|sistema embedded]] interagisce con l'ambiente esterno tramite sensori e azionatori.

## Sensori
---
>[!definizione]
>Un ***sensore*** è un trasduttore che permette la *misurazione di un fenomeno fisico* o la rilevazione e quantificazione di concentrati chimici.

### Principi di Utilizzo
>[!hint] Fisica
>Ci si basa sulle leggi fisiche che governano le ***relazioni*** tra quantità fisiche e un output di [[../../Fisica/Elettromagnetismo/Potenziale Elettrico|quantità elettrica]].

>[!example] Esempio: Thermistor
>***Sensore di Temperatura***

La [[../../Fisica/Elettromagnetismo/Circuiti/Resistenza Elettrica#Resistività|resistività]] cambia in base alla temperatura.
- Per ricevere il segnale una corrente in `input` è necessaria per misurare il ***voltaggio in uscita***.

### Quantità Fisiche
> Le quantità fisiche misurate dai sensori possono essere classificate in:

>[!caution] Continue

>[!summary] Discrete

Le informazioni associate a quantità fisiche sono chiamate ***segnali***.
> Tipologie di ***Sensori Digitali***:
- Sensore Logico: *Output booleano*.
- Sensore Codificato: Output una *sequenza* di `bit`.

>[!failure] Da quantità continua a discreta
> [[../../Architettura degli Elaboratori/Rappresentazione dell'Informazione/Rappresentazione dei Suoni#Campionamento|Campionamento]]
> [[../../Architettura degli Elaboratori/Rappresentazione dell'Informazione/Rappresentazione dei Suoni#Quantizzazione|Quantizzazione]]

#### Misurazioni
>[!hint] Misurazione di quantità fisiche
>La ***misurazione*** è un confronto tra due quantità fisiche omogenee.

Per le misurazioni si usa il [[../../Fisica/Misurazione#Sistema Internazionale|sistema internazionale]].
##### Errori
>[!fail] Systematic Errors
>Un ***errore è sistematico*** se, quando le condizioni sperimentali sono fisse, l'errore ha *sempre lo stesso impatto*.

>[!missing] Random Error
>Sono ***errori accidentali***, errori che cambiano ogni volta che si ripetono le misurazioni.

>[!bug] "Gross" Errors
>Errori fatti dall'**operatore** o un **fallimento di uno strumento**.
### Caratteristiche Statiche
>[!info]
>Le ***caratteristiche statiche di un trasduttore*** possono essere rappresentate da una funzione.
>$$y=f(x)$$

$f$ è definita in un range finito di input tra $x_{m}$ e $x_{M}$ e l'output è definito tra $y_{m}$ e $y_{M}$.

>[!important] Ideale
>Le ***caratteristiche statiche*** di un sensore dovrebbero idealmente avere un *pattern lineare*.
>$$y=kx$$

A causa di errori, la ***linearità è spesso sbagliata***.
- L'andamento lineare si può ottenere tramite il [[../../Metodi Numerici per L'Intelligenza Artificiale/Equazioni Lineari/Problema Minimi Quadrati|metodo dei minimi quadrati]].

#### Tipologie di Errori
>***Offset Error***
- L'offset error è il valore $d$ della funzione quando l'*input è zero*.
- Per avere caratteristiche lineari, l'offset va **rimosso** $y=f(X)-d$.

>***Threshold Error***
- È il **valore più basso** di input che può essere misurato.
- Per avere caratteristiche lineari, l'offset va **rimosso** $y=f(X)-d$.

> ***Gain Error***
- È la differenza tra le caratteristiche ideali $K$ e la retta che approssima le caratteristiche reali $K_{1}$.
$$
e_{G}\%=\displaystyle{\frac{|K_{1}-K|}{H}}\cdot100
$$

#### Accuratezza
>[!hint] Accuracy
>L'***accuratezza*** di un sensore è una misurazione di quanto il valore letto *differisce dal valore reale*.

$$
\in_{f}=100\cdot \displaystyle{\frac{ X_{m}-X_{v}}{X_{FS}}}
$$
- $X_{v}$ **misurazione** senza errori.
- $X_{m}$ **misurazione** reale.
- $X_{FS}$ **massimo** valore del range.
>[!example] Esempio

Un sensore di pressione misura valori nel range di $0-10 \text{bar}$ con una accuratezza di $\pm 1.0\%$ rispetto alla scala completa.
- L'errore massimo è $10\cdot1.0\%=10\cdot 0.01=0.1\text{bar}$.

#### Precisione
>[!hint] Precision
>La ***precisione*** misura quanto un sensore è influenzato dai **random errors**.

Una precisione alta migliora la ripetibilità di un evento.
>[!caution] Calibrazione
>La ***calibrazione*** di un sensore è la *modifica dei parametri* per allineare l'output con quello misurato dallo strumento di riferimento.

### Comportamento Dinamico
>[!todo] Sensore
>Un sensore ha un ***comportamento dinamico*** quando la risposta ad un input **non è istantanea**.

> **Rise Time**:
- Tempo trascorso per passare dal $10\%$ a $90\%$ del valore finale.

> **Response Time**
- Tempo trascorso per raggiungere una percentuale del valore finale.

## Azionatori
---
>[!definizione]
>Un ***azionatore*** è un dispositivo che produce un effetto nell'ambiente.

>[!info] Trasduttori
>I ***trasduttori*** sono dispositivi che convertono un tipo di [[../../Fisica/Lavoro e Energia/Energia]] in un altro tipo.

### Interfacciamento
> Due casi principali

>[[../Elementi del Microcontroller/General Purpose Input Output|!done]] è abbastanza

>[!missing] Il voltaggio non è abbastanza.
>Il dispositivo deve essere caricato da un ***circuito esterno***.

In questo caso il `GPIO` è usato per aprire/chiudere il circuito tramite [[../../Architettura degli Elaboratori/Storia dei Calcolatori#Generazione $II$|transistor]] e *relays* che funzionano come switch.

### Carichi
> Da un punto di vista elettronico il carico può essere classificato in due categorie.

>[!caution] Carichi Resistivi
- Un componente che applica una [[../../Fisica/Elettromagnetismo/Circuiti/Resistenza Elettrica]] al passaggio di [[../../Fisica/Elettromagnetismo/Circuiti/Corrente Elettrica|corrente]], risultando in una ***variazione del livello di voltaggio***.

>[!help] Carichi Induttivi
- Dispositivi che lavorano [[../../Fisica/Elettromagnetismo/Induzione|inducendo corrente]] in un filo.
	- Solitamente generano una corrente inversa.


## Problemi di Voltaggio
---
>[!info]
>***Sensori*** e ***Azionatori*** possono operare a $2$ diversi livelli di voltaggio.
>- $5V$ e $3.3V$.

Per usare sensori e azionatori che funzionano a $3.3V$ nei `MCU` dobbiamo adottare delle strategie specifiche per ***non danneggiare i componenti***.

> Vale anche per quando si connette Arduino e ESP attraverso il `BUS` ***seriale***.

>[!done] TX(**ESP**) => RX(*Arduino*)
- Non c'è problema, $3.3V$ sono abbastanza per essere interpretati come `HIGH`.


>[!fail] TX(**Arduino**) => RX(*ESP*)
- Problema!
- L'input di $5V$ ***potrebbe danneggiare la scheda***.

### Divisori di Voltaggio
>[!hint] Voltage Divider
>I ***Voltage Divider*** vengono usati per produrre un output `Vout` (es. $3.3V$) partendo da un voltaggio più alto (es. $5V$).

![[../attachements/VoltageDivider.svg]]

$$
\alpha=\frac{R_{2}}{R_{1}+R_{2}}\qquad V_{out}=\alpha V_{in}
$$
> Valori tipici *utilizzati*:
- $R_{1}:1KOhm$
- $R_{2}:2KOhm$

### Bi-Directional Logic Level Converter
>[!help] Info
>Il ***Bi-Directional Logic Level Converter*** è un modulo che *riduce il voltaggio di un segnale*.

Metodo raccomandato per cambiare segnali che richiedono una ***comunicazione ad alta velocità***.