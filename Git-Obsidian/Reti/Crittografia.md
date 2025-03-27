> La crittografia mette in sicurezza il trasferimento di dati **attraverso una cifratura degli stessi**.

>[!quote] Legge di **Kerckhoffs**
>La sicurezza di un *criptosistema* **non deve dipendere dal tener celato il cripto-algoritmo**, la sicurezza dipenderà solo dal **tener celata la chiave**.

Un algoritmo di criptazione è buono se è pubblico e la chiave è ***difficile da reperire***.

>[!info] Crittografia
>L'idea di base è quella di trasformare un messaggio in modo tale che solo utenti autorizzati riescano a leggerlo.

![[Cryptography.png]]

- $P$: Testo in chiaro, *comprensibile a tutti*.
- $C$: Testo cifrato, comprensibile *solo al destinatario*.
- $E$: Funzione di cifratura, rende il messaggio *decifrabile solo dal destinatario*.
- $D$: Funzione di decifrazione, usata dal destinatario per *leggere il messaggio cifrato*.
## Tipologie
---
> Ci sono 2 tipi di crittografia principali.

>[!caution] Simmetrica

>[!abstract] Asimmetrica

Inoltre si presenta anche una terza opzione ***Ibrida***.
### Simmetrica
>[!tldr] Idea
>In un sistema con ***crittografia simmetrica*** mittente e destinatario **condividono la stessa chiave** per criptare e decriptare i messaggi.

La crittografia *simmetrica* richiede **poche risorse** per l'utilizzo
- [[Complessità di Algoritmi|Complessità computazionale]] ridotta.

>[!danger] La chiave deve essere nota sia a chi invia sia a chi riceve il messaggio
>Durante il trasferimento della chiave chiunque riesca ad ottenerla ***è in grado di decifrare il testo***.

![[SymmetricCryptography.png]]

Le funzioni di cifratura e decifrazione sono *una l'inversa dell'altra*
$$
\begin{array}
\ D(E(P,K),K)=P \\
E(D(C,K),K)=C
\end{array}
$$
#### Alcuni Algoritmi
>[!help] Data Encryption Standard
>Chiave a $56$ `bit`, ormai *insicuro*.

>[!Triple DES]
>Chiave a $168$ `bit`.

>[!cite] Advanced Encryption Standard
>Chiave a $128$, $192$ o $256$ `bit`
### Asimmetrica
>[!tldr] Idea
>In un sistema di comunicazione con ***crittografia asimmetrica***, si usano due chiavi $K_{1}$ e $K_{2}$, una utilizzata per *cifrare* e l'altra per *decifrare*.

![[AsymmetricCryptography.png]]

#### Algoritmi
> Generalmente gli algoritmi di crittografia asimmetrica sono basati su formule matematiche basate sui **numeri primi**.

Sono algoritmi **matematicamente** "***solidi***".

>[!fail] Complessità
>Algoritmi decisamente ***più complessi*** rispetto alle chiavi simmetriche

#### Funzionamento
> La crittografia asimmetrica consiste nell'avere 2 chiavi:

>[!info] Chiave pubblica
>Utilizzata per *criptare* i messaggi e **condivisa** fra i due terminali.

>[!hint] Chiave Privata
>Utilizzata per *decriptare* i messaggi, rimane ***solamente al mittente***.

> Le chiavi sono ***interscambiabili***:
- Si cripta con una e decripta con l'altra.

Per instaurare una ***comunicazione a due vie*** sono necessarie **4 chiavi** (*due coppie*) una *privata* e una *pubblica* per ogni terminale.

### Tipologia Ibrida
> Vengono uniti i due metodi.

>[!abstract] Due fasi
>>[!caution] Scambio di chiavi simmetriche
>>La prima fase consiste nello scambio di chiavi *simmetriche* utilizzando un ***algoritmo di cifratura asimmetrico***.
>
>>[!help] Scambio di informazioni
>>Una volta stabilite le chiavi *simmetriche* può partire una comunicazione **sicura** tramite un algoritmo di criptazione **simmetrica**
>>- ***Bassa*** complessità computazionale.

Utilizzato per ridurre l'*utilizzo eccessivo delle risorse*.

![[Hybrid.png]]

