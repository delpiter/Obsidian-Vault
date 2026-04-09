> Le velocità di trasmettitore e ricevitore **possono essere molto diverse**.

Si utilizza un meccanismo a ***finestra scorrevole*** analogo al [[../Data Link Layer/ARQ#Finestra di Trasmissione|caso dello strato 2]].
- Il ricevitore deve comunicare al trasmettitore le ***dimensioni della sua memoria di ricezione*** ([[TCP#Formato del Messaggio|advertised window]], `AW`).

## Finestra di Trasmissione e Ricezione
---
> Siano $W_{T}$ e $W_{R}$, rispettivamente le *finestre* di **trasmissione** e di **ricezione**.

- $W_{T}$ è l'insieme di segmenti inviabili dal trasmettitore *senza ricevere conferme*.
- $W_{R}$ è l'insieme di segmenti **fuori sequenza** memorizzabili dal ricevitore.

$M$ è lo ***spazio di numerazione*** (In [[TCP]] $2^{32}$)

>[!check] Se $W_{T}=W_{R}$
>Allora deve valere:
>$$W_{T}+W_{R}\leq M$$

$W$ può essere misurata:
- In `byte` ($w$).
- In *numero* di [[TCP|segmenti]] ($W$).

>[!info] Dimensionamento 
>$W$ (o $w$) viene messa a punto dinamicamente sulla base di informazioni provenienti dal ricevente (*advertised window*, `AW`) e correlate allo stato di congestione della rete (*congestion window*, `CW`).

`AW` e `CW` sono in funzione del tempo.
- In un generico istante di tempo la connessione imposta $W=\min[AW,CW]$

>[!hint] Obbiettivo
>L'obbiettivo è quello di ***garantire il controllo di flusso***.

Un errato dimensionamento di $W$ può congestionare:
- Il *ricevitore*.
	- `AW` per prevenire.
- I *nodi intermedi* della rete.
	- `CW` per prevenire.

### Il Ruolo di `AW`
> Con `AW` il *ricevitore* indica al trasmettitore la ***dimensione del suo buffer***.
- Così che da essere certi che possa ricevere l'*intera finestra di dati*.
 
>[!question] Attuazione del Controllo

> Il **ricevitore lento** blocca un **trasmettitore** più veloce:
- Il *buffer di ricezione* si riempie (`AW`$=0$).
- $W=0$ e il trasmettitore blocca la trasmissione.

> Il processo ricevente **legge dal buffer**:
- Imposta `AW`$>0$, e inizia ad inviare gli `ACK`.
	- Si libera il *buffer di trasmissione*
	- Viene ricevuto `AW`$>0$.
- Il processo trasmittente ***rincomincia a trasmettere***.

>[[../../Sistemi Operativi/Teoria/9 - Condivisione di Risorse#Deadlock|Deadlock]]
>Caso
>> *Trasmittente*:
>- Invia messaggi
>- Riceve un messaggio con `AW`$=0$
>- ***Sospende*** l'invio dei dati.
>
>> *Ricevente*
>- Il buffer di ricezione si riempie
>- Invia un messaggio con `AW`$=0$
>- Non ha altri messaggi da inviare.

A questo punto il ***protocollo è in deadlock***.

>[!done] Soluzione
>Quando il trasmettitore riceve un pacchetto contenente `AW`$=0$, fa partire il "***persistent timer***".
>- `PT`$=1,5\sec$ per un normale collegamento.
>
>Quando `PT` scade si invia un segmento di $1$ `byte`.
>- Il ricevitore ***deve rispondere***.
>	- Invia un `ACK` con `AW`$>0$ e la trasmissione riprende.

> ***Inefficienze***:
- Trasmissione "*lenta*"
	- L'applicazione trasmette un **carattere per volta**.
- Ricezione "*lenta*"
	- L'applicazione comunica una **dimensione di finestra molto piccola**.

#### Ricevitore Lento
##### Silly Window Syndrome
> Il fenomeno consiste nel generare segmenti `TCP` con un numero *piccolissimo* di `byte`, tipicamente uno.
- Ha luogo quando l’applicazione che sta utilizzando la connessione *legge i dati ricevuti* un `byte` alla **volta** e il buffer è pieno.

>[[../Network Layer/Protocollo IP|!warning]].

> *Soluzione*:
- Si autorizza l’invio di dati sulla connessione quando almeno la ***metà*** del suo *buffer di ricezione* è vuota.
- È disponibile lo spazio per memorizzare dei dati di un segmento di dimensione `MSS` (**M**ax **S**egment **S**ize).

#### Trasmettitore Lento
##### Algoritmo di Nagle
> L'applicazione trasmittente risulta essere molto lenta:
- Passa a `TCP` un carattere per volta (es. *Telnet*)

Vengono trasmessi dei "***tinygram***":
- Segmenti di un solo `byte`, ciascun `byte` richiede almeno $40$ `byte ` di *header* e $40$ di `ACK`
- Risulta essere **molto inefficiente**.

>[!check] Algoritmo di Nagle
>Il trasmettitore trasmette un nuovo segmento solo se è ***vera una delle condizioni***.
>1. Il *segmento* è di dimensioni pari a `MSS`.
>2. Il *segmento* è di dimensioni almeno pari alla metà del valore `AW`.
>3. Non ci sono `ACK` *pendenti* ed è possibile trasmettere tutto ciò che è in attesa.

L'algoritmo tende a **ritardare** i dati nel buffer di trasmissione.
- ***Non accettabile*** in alcune applicazioni.

> È possibile disabilitare l'algoritmo.


### Ruolo di `CW`, Controllo della Congestione
>Può accadere che la *rete* **non** sia in grado di trasferire tutti i dati consentiti dall'*apertura della finestra dichiarata* dalle stazioni riceventi.

>[!tldr] Idea
>Se si verifica una congestione in rete si ***rallenta la trasmissione***.
>- Quando si verifica una perdita si *riduce* $W$
>- Quando gli `ACK` arrivano correttamente $W$ viene *aumentata*.

#### `CW` Ideale
> Possibile solo se `AW` non pone un *vincolo più stringente*.

Avendo a disposizione una banda $B$ (`byte`$/sec$)
- Il massimo throughput si ottiene quando il protocollo a finestra non limita la velocità di scambio dei dati.
- $w_{id}=RTT\cdot B$
- $W_{id}=w_{id}/MSS$

>[!done] Si usa al $100\%$ la capacità disponibile.

- Se $w<w_{id}$: si spreca banda.
- Se $w>w_{id}$: è necessario accodare nei router intermedi, cresce il ritardo.

Il ***massimo throughput*** (`byte`$/sec$)vale circa:
$$
S=\frac{w}{RTT}
$$
#### Caso Reale
> Al momento dell'instaurazione della connessione la ***banda disponibile è incognita*** e *può cambiare* durante la connessione.

>[!question] A quale valore si deve impostare `CW`?

> Ipotesi di partenza:
- Trasmettitore e ricevitore sono correttamente configurati.
- `AW`$>$`CW` quindi `W`$=$`CW`.

Il ***controllo di congestione*** sulla connessione `TCP` si basa sulla definizione di due regioni di operazioni, denominate *slow start* e *congestion avoidance*.

>[!abstract] Slow Start

Nella prima "regione" che caratterizza la fase iniziale del trasferimento di dati, si procede a un ***aumento di tipo moltiplicativo*** della *congestion window*.

>[!missing] Congestion Avoidance

Al superamento di una data soglia per il parametro `CW`, denominata *slow start threshold*, si entra nella *seconda regione* in cui l'ulteriore aumento è di ***tipo additivo***.
- Di solito si sceglie un valore iniziale molto grande per la *slow start threshold* (es. `ssthr`$=65535$ `byte`).

##### Retransmission Time Out
>[!info]
> `RTO` *scade* quando un segmento non viene riscontrato oppure il relativo `ACK` ***non giunge in tempo utile***.
>>[!cite] Congestione
>>Tale evento viene interpretato come indicatore di ***rete congestionata***.
>

Il protocollo `TCP` prevede che un segmento ritenuto perso per la scadenza del *time-out* venga ritrasmesso e la `CW` venga *ridotta* all'***apertura minima***.
- Inoltre si impone `ssthr`$=\max(W /2,2\cdot MSS)$

![[attachements/CongestionAvoidance.png]]

>[!hint] Commenti
>Il protocollo [[TCP]] cerca di ***adattarsi dinamicamente*** alle variazioni di capacità della rete.
>- Cerca di occupare tutta la **banda disponibile** (*greedy*)

>Siano $T_{ss}$ e $T_{ca}$ rispettivamente la durata della fase di **slow start** e **congestion avoidance**.

Se la rete è abbastanza stabile:
$$
T_{ss}\ll T_{ca}
$$

> Velocità di trasmissione:
- Definiti: $MSS, RTT$ e $W(t)$ (numero di pacchetti in rete in un momento), possiamo definire la ***velocità di trasmissione come***:
$$
V_{tr}=\displaystyle{\frac{W(i)\times MSS \text{ bit}}{RTT\sec}}
$$
###### AIMD Congestion Control
> Questo tipo di andamento viene indicato con la sigla `AIMD`.

>[!check] **A**dditive **I**ncrease **M**ultiplicative **D**ecrease

> Additive Increase
- Aumento la velocità in *modo additivo*.
- $r(t_{i+1})=r(t_{i})+c\qquad c\ll r_{\max}$

> Multiplicative Decrease
- Decremento la velocità in *modo moltiplicativo*.
- $r(t_{i+1})=a\times r(t_{i})\qquad a<1$

Anche se i periodi di aumento lineare *non sono costanti* (dipendono dal *carico istantaneo* delle risorse di rete), possiamo dire che un andamento `AIMD` può essere graficamente rappresentato come "***a dente di sega***".

Nel lungo termine permette di avere un'***equa distribuzione della banda disponibile***.

>[!warning] Delayed `ACK`
>Se il protocollo utilizza i [[TCP#Acknowledgment|delayed ACK]]:
>- In un $RTT$ trasmetto $W$ messaggi e ricevo un `ACK` ogni due.
>
>Ogni $RTT$ incremento la finestra di:
>$$\#ACK\cdot\frac{1}{W}=\frac{1}{2}W\cdot \frac{1}{W}=\frac{1}{2}$$

