> I protocolli sono progettati per garantire:

>[!summary] Funzionalità
>La *trasmissione* dei dati deve poter avvenire ***risolvendo i problemi*** che si riscontrano nell'accesso e nell'uso del [[Git-Obsidian/Reti/Introduzione/Introduzione#Canale|canale]].
>>[!example] Esempi
>>- [[Controllo dell'Errore]] ed eventuale *recupero*.
>>- [[ARQ|Controllo di Flusso e Sequenza]].


>[!caution] Prestazioni
>La *trasmissione* deve **avvenire con successo** utilizzando la ***capacità*** messa a disposizione dallo strato fisico.

## Prestazioni
---
> Un sistema deve *smaltire* il **lavoro** che gli viene offerto dall'esterno.

>[!hint] Arrivi e Partenze
>- $a(t)$: Numero di *richieste di servizio* **giunte** al tempo $t$.
>- $s(t)$: Numero di *richieste* **accettate** al tempo $t$.
>- $p(t)$: Numero di *partenze* dal sistema al tempo $t$.

![[Performance.png|500]]

> Richieste offerte e smaltite:

- **Frequenza media** delle *richieste offerte*:
$$
\lambda=\lim\limits_{t\to \infty} \frac{a(t)}{t}
$$
- **Frequenza media** delle *richieste smaltite*:
$$
\lambda_{s}=\lim\limits_{t\to \infty} \frac{p(t)}{t}
$$
Se il sistema in oggetto non produce lavoro ma lo riceve solamente:
- $\lambda_{s}\leq\lambda$

> Richieste Perdute

- $\lambda_{s}=\lambda$ implica $s(t)=a(t)$
	- Tutte le richieste vengono *accettate* e prima o poi *soddisfatte*.

- $\lambda_{s}<\lambda$ implica $r(t)=a(t)-s(t)$
	- Dove $r(t)$ rappresenta le richieste non accettate (***rifiutate***) o ***perdute*** dal sistema.

**Posso definire**:
$$
\lambda_{p}=\lim\limits_{t\to \infty} \frac{r(t)}{t}
$$
- Da cui consegue $\lambda=\lambda_{s}+\lambda_{p}$.

### Utente e Servizio
>In una ***rete a pacchetto*** considerare il semplice "`bit` *rate*" del canale **non** è del tutto corretto.

L'unità di servizio è il ***pacchetto***.

>[!info]
>Il riferimento è il ***tempo di servizio dell'intero pacchetto*** che *solo se completato* produce un risultato "*utile*" per l'utente.


$\vartheta$ è il tempo richiesto dal servizio di un generico cliente.
> Lunghezza del Pacchetto
- $L$ Lunghezza del pacchetto in `bit`.
-  $C$ capacità del canale in `bit`$/\sec$.
$$\overline{\vartheta}=\frac{L}{C}$$

> Frequenza di servizio

 L'inverso del tempo medio di servizio:
 $$
\mu=\frac{1}{\overline{\vartheta}}
$$
Il ruolo di $\mu$:
- Può essere interpretato come la ***capacità massima del servitore***.
	-Se $\overline{\vartheta}=0.5\sec$ il servitore al più **smaltirà** $\mu=2$ pacchetti$/\sec$.

Per il singolo servitore $\lambda_{s}^{\max}=\mu$

#### Sistemi a Coda
> Per le reti hanno particolare importanza i ***sistemi a coda***.

>[!tldr] Funzionamento
>L'utente permane nel sistema per un tempo che tiene conto dell'***attesa in coda*** e del ***tempo di esecuzione del servizio***.
>- $\overline{\delta}=\overline{\vartheta}+\overline{T}_{A}$ è il tempo medio totale speso dal singolo utente nel sistema, composto da:
>	- $\overline{\vartheta}$ tempo *effettivo di servizio*.
>	- $T_{A}$ tempo *sospeso in coda*.

#### Traffico
>[!definizione]
>Si definisce ***traffico*** il numero medio di utenti presenti nel sistema.

Si dimostra che il prodotto tra la frequenza di arrivo e il tempo medio di permanenza nel sistema, risulta uguale al *traffico*.
$$
A=\lambda\overline{\delta}
$$

Possiamo definire:

> $A_{0}=\lambda\overline{\vartheta}$
- *Traffico Offerto* (Occupazione media di un sistema ideale).

> $A_{s}=\lambda_{s}\overline{\vartheta}$
- *Traffico Smaltito* (Occupazione media dei servitori del sistema).
- Se $\lambda_{s}$ utenti mediamente *entrano* per unità di tempo allora $\lambda_{s}$ devono *uscire*.
Da una valutazione della ***capacità del servizio*** del sistema considerato.

>[!info] Throughput
>$A_{s}$ è spesso indicato con il nome di ***Throughput***.

> $A_{p}=\lambda_{p}\overline{\vartheta}$
- *Traffico perduto* (Occupazione media di un sistema che serve gli ***utenti rifiutati***).

