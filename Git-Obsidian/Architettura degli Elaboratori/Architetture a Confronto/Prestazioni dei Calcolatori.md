## Tempo di Esecuzione
---
>[!abstract] Elementi
>Gli elementi che consentono di calcolare il ***tempo di esecuzione*** sono:
>>[!info] Periodo di Clock
>>$T_{clock}$
>>Dipende dalla ***tecnologia*** e dalla ***organizzazione*** del sistema
>
>>[!caution] Numero di clock per istruzione
>>$CPI_{i}$
>>Indica il numero di clock occorrenti affinché venga eseguita l'istruzione di tipo $i$
>>- Istruzione ***Semplice*** $\to CPI$ ***ridotto***
>>- Istruzione ***Complessa*** $\to CPI$ ***elevato***
>
>>[!info] Numero di istruzioni $i$
>>$N_{i}$
>>Indica il numero di istruzioni di tipo $i$
>
>>[!done] Formula
>>$$T_{esecuzione}=T_{clock}\cdot\left( \sum_{i=1}^n N_{i}\cdot CPI_{i} \right) $$

### IPS
>[!info] Instruction Per Second
>L'$IPS$ è una misura che serve per ***valutare le prestazioni*** di un sistema
>Indica quante istruzioni vengono ***eseguite al secondo***
>Al giorno d'oggi viene riportata come $MIPS$ (***M***illion ***IPS***)
>$$MIPS=\frac{\text{Frequenza del Clock}}{10^6\cdot CPI}$$

Questa misura è affetta da una ***forte approssimazione***
- Non tiene conto delle possibilità offerte dal ***set di istruzioni***
	- Più il set di istruzioni di una certa macchina è ***potente*** tanto più è possibile ***ridurre la lunghezza*** dei programmi eseguiti
- Non tiene conto delle ***percentuali delle diverse istruzioni*** all'interno di programmi reali
	- Una macchina più veloce in un programma può essere più lenta in altre
- Non tiene conto dell'ampiezza dei [[BUS dei Calcolatori|BUS]], della presenza di [[Cache]] o altre tecniche che ottimizzano i tempi di esecuzione

### Benchmark
>*Le stime vengono solitamente ottenute attraverso [[Definizioni_Architettura#Benchmarck|Benchmark]]*

>[!info] Benchmark Dhrystone
>Utilizzato per ottenere stime di $IPS$
>Contiene solamente operazione di aritmetica intera

>[!info] ***Flo***ating Point ***P***er ***S***econd
>`FLOPS`
>È una misura che è significativa se si intende utilizzare un programma dove la maggior parte delle operazioni sono di ***tipo floating point***
>Tipicamente riportata come `MFLOPS`, `GLOPS`

>[!info] LINPACK Benchmark
>Il ***LINPACK Benchmark*** misura il numero di `FLOPS` a $64$ `BIT` per risolvere sistemi di equazioni lineari densi $n \times n$

## Classificazione dei Calcolatori
---
>[!abstract] Computer usa e Getta

Cartoline d'auguri musicali , `RFID`, $\dots$
- **Costo**: *alcuni centesimi*
- **Potenza**: *alcuni `MIPS`*


>[!info] Sistemi Embedded

***SmartCard***, Orologi, Parti di automobili, Elettrodomestici, ***giocattoli***, $\dots$
- **Costo**: $1-50$€
- **Potenza**: $1000$ `MIPS`

>[!abstract] Smartphone e Tablet

***Applicazioni Mobili*** di ogni Genere:
- **Costo**: $100-1000$€
- **Potenza**: $1-2000$ `MIPS`

>[!info] Console da Gioco

*PlayStation, Xbox*,$\dots$
- **Costo**: $100-500$€
- **Potenza**: $250-10000$ `GFLOPS` ([[Schede Grafiche|GPU]])

>[!abstract] Personal Computer

***Desktop*** o Portatili
- **Costo**: $500-2000$€
- **Potenza**: $50-50000$ `GFLOPS` ([[La CPU|CPU]])

>[!info] Server Workstation

***Gestione archivi***, ***centralizzazione servizi***, multiutenza, deep learning, $\dots$:
- **Costo**: $5-100\text{K}$€
- **Potenza**: $1-5000$ `TFLOPS` ([[Schede Grafiche|GPU]] $+$ [[La CPU|CPU]])

>[!abstract] Cluster

***Raggruppamento di più server*** per scalare verso l'alto le prestazioni di singoli server:
- **Costo**: $10\text{K}-1\text{M}$€
- **Potenza**: $1-10000$ `TFLOPS`

>[!info] Supercalcolatore

Elevata potenza di calcolo per ***applicazioni scientifiche***:
- **Costo**: $50\text{M}-250\text{M}$€
- **Potenza**: $1$ `PFLOPS`-$1$ `EFLOPS`

### Valutare il Miglioramento delle Prestazioni
>*Poter valutare le prestazioni di un calcolatore permette di calcolare:*
- La bontà di un investimento
- L'adeguatezza del calcolatore al tipo di applicazione

$$
Prestazione\ P=\frac{1}{T_{esecuzione}}
$$
$$
Speed \ Up=\displaystyle{\frac{P_{A}-P_{B}}{P_{B}}}=\displaystyle{\frac{T_{B}-T_{A}}{T_{A}}}
$$
*Dove $A$ è il sistema "nuovo" e $B$ è il sistema "vecchio*

#### Legge di Amdhal
>[!check] Legge di Amdhal
>La ***Legge di Amdhal*** afferma che il miglioramento delle prestazioni che si ottiene in un sistema di elaborazione accelerando un ***qualsiasi sottoinsieme*** del calcolatore è ***proporzionale*** alla percentuale  di tempo per cui quel sottoinsieme è ***utilizzato***
>>[!done] Formula
>>$$T_{es.finale} =\displaystyle{\frac{p\cdot T_{es.iniziale}}{a}}+(1-p)\cdot T_{es.iniziale}$$
>>*$p$ è la percentuale di tempo utilizzata dal sottoinsieme migliorato*
>>*$a$ è il fattore di accelerazione*
>
>Si può vedere come una comune ***media pesata***

##### Esempio
>*Modificando l'unità che esegue le operazioni in virgola mobile (`FPU`) si riduce a $\frac{1}{10}$ il tempo necessario per eseguire le stesse*
>*Si supponga che del tempo di esecuzione solo il $40$% venga utilizzato per eseguire operazioni in virgola mobile*

$$
T_{es.finale} =\displaystyle{\frac{0.4\cdot T_{es.iniziale}}{10}}+(1-0.4)\cdot T_{es.iniziale}=0.64\cdot T_{es.iniziale}
$$
$$
Speed \ Up=\displaystyle{\frac{T_{es.iniziale}-0.64T_{es.iniziale}}{0.64T_{es.iniziale}}}=0.56 = 56\%
$$
