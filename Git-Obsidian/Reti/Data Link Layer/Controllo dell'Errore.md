> Si farà riferimento a *codici a blocco*.

Si applica la codifica a blocchi di $k$ `bit` di informazione.


>[!abstract] Calcolo
>Vengono calcolati $r$ `bit` di ***ridondanza*** come *funzione combinatoria* dei $k$ `bit` e trasmessi $n=k+r$ `bit`.

I messaggi possibili sono $2^k$ `bit`.
- Parole di codice possibili sono $2^n>2^k$

>[!done] Messaggi "Leciti"
>$2^k$ sono i messaggi che fra i $2^n$ corrispondono ai ***messaggi originali leciti***.

$2^n-2^k$ sono invece i messaggi che corrispondono a configurazioni non ammesse e permettono di *rilevare* e/o *correggere* gli errori.
- [[Correzione di Errori]]


##### Codici a rilevazione di Errore
>La ricezione di una parola di codice invalida indica la presenza di ***errori di trasmissione***.
- Impossibile dire quali `bit` siano errati

>[!tip] Sarà necessaria la ritrasmissione dei dati errati.
>Richiede un ***numero limitato*** di `bit` aggiuntivi.

###### Uso del Codice
![[ErrorCorrection.png]]

>Il messaggio viene "*passato*" in una funzione che genera la sequenza di `bit` di ***ridondanza***.
- Il destinatario *ricalcola* con la stessa funzione i `bit` ridondanti

>[!done] Se sono uguali non c'è stato errore

>[!fail] Se sono diversi è accaduto un errore

[[Definizioni_Architettura#Parity Bit|Esempio più facile]].

###### Internet Checksum
> Nei protocolli di internet vengono usati codici a blocchi semantici
- Estensione del `bit` ***di parità***

>[!info] \[RFC1071\]
>In outline, the Internet checksum algorithm is very simple:
>1. Adjacent octets to be checksummed are paired to form $16$-`bit` integers, and the *1's complement sum* of these $16$ `bit` integers is formed.
>2. To generate a ***checksum***, the *checksum* field itself is cleared, the $16$ `bit` 1's complement sum is *computed* over the octets concerned, and the 1's complement of this sum is placed in the **checksum field**.
>3. To ***check*** a checksum, the 1's complement sum is computed over the same set of octets, including the checksum field. If the result is all 1 bits (-0 in 1's complement arithmetic), the check succeeds.

**Complemento a 1**
- Una somma `bit` a `bit`, se l'ultimo `bit` provoca un riporto, si *somma al numero finale*.

>[!hint] Proprietà
>L'internet checksum è indipendente dalla rappresentazione [[Definizioni_Architettura#Ordinamento dei `BYTE`|Little-Big Endian]]
##### Codici a correzione di Errore
>Una parola di codice invalida indica la presenza di ***errori di trasmissione***.
- Permette di individuare la ***parola di codice*** *valida* corrispondente.

>[!tip] Garantisce la trasparenza semantica nei casi in cui l'errore è correggibile
>Richiede un ***numero elevato*** di `bit` aggiuntivi, ma permette la *correzione* dei dati in base ai soli dati ricevuti.

##### Scelta
>[!question] Quale codifica scegliere?

Si sceglie in base all'***affidabilità del canale***.
- Se il canale è *affidabile* (tasso di errore per `bit` del canale pari a $10^{-6}$) 
	- Conviene la Rilevazione
- Se il canale è *poco affidabile* (tasso di errore per `bit` del canale pari a $>10^{-4}$)
	- Conviene la Correzione

>[!hint] Nelle reti
>Di solito si usano codici a correzione di errore nello ***strato fisico***.
>Si usa la rilevazione nei *protocolli di linea di trasporto* (**data link layer**).

## Definizioni
---
>[!summary] Codici Lineari
>Dati due messaggi di $k$ `bit` $m_{1}$ e $m_{2}$, ricavate le parole di codice $c_{1}$ e $c_{2}$.
><u>Il codice si dice ***Lineare*** se </u>
>$m_{3}=m_{1}+m_{2}$ da origine a $c_{3}=c_{1}+c_{2}$

>[!help] Codificatori Semantici
>Nella sequenza di $n$ `bit` da trasmettere i $k$ `bit` di informazione, mantenuti distinti dagli $r$ bit di *ridondanza*, vengono trasmessi inalterati.

## Algebra Binaria
---
>L'algebra si costruisce sull'insieme delle cifre binarie $0$ e $1$: $\mathbb{A}=\{ 0,1 \}$

>[!example] Operazioni
>>[!help] OR Esclusivo $\oplus$  (somma e sottrazione)
>>- $0$ Elemento Neutro
>>- $1$ Opposto
>>
>>Vale la ***prorprietà commutativa***.
>
>>[!abstract] Moltiplicazione
>>- $1$ Elemento neutro
>>
>> Valgono le ***prorprietà commutativa*** e ***distributiva***.

Algebra analoga a quella ordinaria ma ***limitata alle cifre binarie***.
### Codici Polimoniali
>[!definizione]
>I ***codici polinomiali*** sono basati sull'uso di polinomi in un'algebra binaria
>- $k$ `bit` vengono posti in corrispondenza con un polinomio di grado $k-1$ nella variabile binaria $x$:
>$$P_{k-1}(x)=b_{0}+b_{1}x+b_{2}x^2+\dots+b_{k-1}x^{k-1}$$

Vengono calcolati i `bit` di *ridondanza* utilizzando operazioni sui polinomi

> **Polinomio generatore**
- Viene stabilito un polinomio di grado $r$ noto a ***trasmettitore*** e ***ricevitore***.
- $G_{r}(x)$ determina le proprietà di rivelazione del codice.

> **Polinomio trasmesso**

Per calcolare il polinomio $T_{n-1}(x)$ da trasmettere:
- Si moltiplica $P_{k-1}(x)$ per $x^r$ ($r$ `bit` a zero posti in coda)
- Si esegue la divisione polinomiale fra $P_{k-1}x^r$ e $G_{r}(x)$  ottenendo un quoziente e un resto
$$
P_{k-1}(x)x^r=G_{r}(x)Q_{k-1}(x)\oplus R_{r-1}(x)
$$
Poiché somma e sottrazione coincidono:
$$
T_{n-1}(x)=P_{k-1}(x)x^r\oplus R_{r-1}(x)=G_{r}(x)Q_{k-1}(x)
$$
>[!hint] Proprietà
>$T_{n-1}(x)$
>- Realizza una codifica di tipo ***sistematico***, i `bit` di *resto* (al più $r$ `bit`), vanno a sovrapporsi agli $r$ zeri in coda.
>- È un multiplo di $G_{r}(x)$

> **Polinomio Ricevuto**

Il ricevitore riceve una sequenza di $n$ `bit` che corrisponde al *polinomio ricevuto*.
$$
T'_{n-1}(x)
$$
- Se si verifica un ***errore di trasmissione***
$$
T'_{n-1}(x)\neq T_{n-1}(x)
$$
>[!hint] Esisterà un polinomio $E(x)$ tale che
>$$T'_{n-1}(x)= T_{n-1}(x)+E(x)$$
>- $E(x)$ ha coefficienti non null in corrispondenza dei `bit` in cui $T'_{n-1}(x)$ differisce da $T_{n-1}(x)$
>- Rappresenta in forma polinomiale gli eventuali *errori* (***Polinomio Errore***)

#### Rivelazione dell'Errore
>Il ricevitore esegue la *divisione*:

$$
\frac{T'_{n-1}(x)}{G_{r}(x)}=\displaystyle{\frac{T_{n-1}(x)+E(x)}{G_{r}(x)}}=\frac{T_{n-1}(x)}{G_{r}(x)}+\frac{E(x)}{G_{r}(x)}
$$
- Il primo di questi termini ha ***sempre resto*** $0$.

>[!caution] Funzione
>Se $E(x)\neq 0$ e $E(x)$ non è divisibile per $G_{r}(x)$, allora il resto della divisione precedente risulta diverso da $0$ e ***viene rilevato l'errore***.

Per rilevare gli errori si deve evitare:
- $Resto\left[ \displaystyle\frac{E(x)}{G_{r(x)}} \right]=0$

> $G_{r}(x)$ va scelto per minimizzare la probabilità di non rilevare un errore

>[!abstract] Capacità del codice e scelta di $G_{r}(x)$
>***Singolo errore***
>- $E(x)=x^i$
>	- È sufficiente che in $G_{r}(x)$ vi siano almeno due `bit` a $1$.
>
>***Numero dispari di errori***
>- Se $G_{r}(x)$ è multiplo di $(1+x)$ non divide **mai** un polinomio con *numero dispari di termini*.
>- Se si sceglie $G_{r}(x)=1+x$, il codice polinomiale fornisce $1$ singolo `bit` di ridondanza.
>
>***2 Errori***
>- $E(x)=x^i+x^j=x^j(x^h+1)$
>- Esistono diversi polinomi che non dividono **mai** $(x^h+1)$
>
>*ITU* propone il seguente polinomio:
>$$G_{16}(x)=x^{16}+x^{12}+x^5+1$$

#### Errori a Burst
>[!question] Problema
>Nelle reti di telecomunicazione è *frequente una distribuzione non uniforme* degli errori, con **concentrazione** degli stessi in ***certi intervalli***.

Chiamiamo ***burst*** una sequenza di `bit` lunga $k$ i cui bit intermedi sono ***inaffidabili***.
- Rappresentato da un polinomio di grado $k-1$

>[!summary] Casi
>- $k-1<r$: L'errore viene **sempre rilevato**.
>- $k-1=r$: Si ha resto nullo se $E(x)=G_{r}(x)$ (probabilità $\frac{1}{2^{r-1}}$)
>- $k-1>r$: Il resto ha **valore casuale** e l'errore sfugge se il resto è nullo ($r$ `bit` a $0$)

#### Cyclic Redundancy Check
>[!info] `CRC`
>Il `CRC` (***C***iclic ***R***edundancy ***C***heck) è un codice adatto a riscontrare errori di tipo "*burst*", ovvero errori che **compromettono più bit consecutivi**.

Anche chiamato ***codice polinomiale*** in quanto i `bit` di dati da controllare possono essere considerati come *coefficienti* di un polinomio che chiameremo $M(x)$.

>Per calcolare il `CRC`, oltre $M(x)$, abbiamo bisogno di un **polinomio detto generatore** che chiameremo $G(x)$ e che dovrà rispettare alcune regole:
- Deve essere ***noto*** sia al mittente che al destinatario.
- I `bit` di ordine più **alto** e più **basso** devono essere $1$.
- Il ***grado*** di $M(x)$ deve essere maggiore di quello di $G(x)$.


>[!done] Considerazioni

- Il `CRC` è progettato per rilevare sia ***errori singoli*** che ***burst*** di errori grazie alla divisione polinomiale.
- $G(x)$ ben scelto *massimizza* la capacità del `CRC` di rilevare errori comuni.
- Polinomi più **lunghi** migliorano l'*affidabilità* ma aumentano il calcolo richiesto.

>[!question] Perché il `CRC` viene usato in protocolli come Ethernet e non il checksum semplice?

Il ***checksum*** usa l’*addizione*, che non rileva errori di bit invertiti con la stessa somma.
- Il `CRC` invece usa *operazioni binarie* più **resistenti** agli errori.
