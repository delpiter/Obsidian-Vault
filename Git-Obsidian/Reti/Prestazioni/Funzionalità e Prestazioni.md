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
>- - $k(t)$: Numero di *richieste* accettate in **attesa di essere soddisfatte**.

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
	- Se $\overline{\vartheta}=0.5\sec$ il servitore al più **smaltirà** $\mu=2$ pacchetti$/\sec$.

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
A=\lambda\overline{\vartheta}
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

>[!tldr] In un sistema ideale

Il sistema ha una ***capacità massima finita*** $\lambda_{s}^{\max}$di smaltire richieste.
- Se le richieste offerte sono eccessive una parte *non può essere soddisfatta*.
![[IdealSystem.png|500]]

>[!caution] In un sistema reale

La riduzione di capacità si interpreta come ***perdita di efficienza***.
- Efficienza del protocollo:
$$
\eta=\displaystyle{\frac{\lambda_{s}^{e}}{\lambda_{s}^{\max}}}\leq 1
$$
![[RealSystem.png|500]]

##### Capacità Massima e Efficienza
>[!question] Quali sono le prestazioni ideali per un protocollo [[ISO-OSI#Stack ISO-OSI|Data Link]]?

Il protocollo invia `bit` dello strato $3$ sul canale.
- La sua ***capacità massima teorica*** è la velocità del canale $C$.

Il tempo medio di servizio minimo possibile sarebbe:
$$
\overline{\vartheta}=\frac{L}{C}=\frac{1}{\mu}
$$
> Se il protocollo richiede maggiore tempo per la completa trasmissione del frame:

$$
\overline{\vartheta}_{e}=\frac{L}{C_{e}}> \frac{1}{\mu}
$$
$C_{e}$ (capacità effettiva) *dipende dal protocollo*.

##### Unità di Misura
>Il [[#Traffico]] è una grandezza adimensionale.

>[!info] $A_{0}=\lambda\overline{\vartheta}$
>**Richieste** di servizio per *unità di tempo* $\times$ **durata** del servizio.

Formalmente si misura con una unità fittizia detta ***Erlang***.
##### Valutazione dell'Efficienza
> Si fa riferimento alla `PDU`.

Confronto tra:
- ***Quantità di tempo*** strettamente usato per inviare i soli dati utente.
- ***Quantità di tempo*** usato complessivamente per completare l'invio della `PDU`.

$$
\eta=\displaystyle{\frac{T_{u}}{T_{0}}}=\displaystyle{\frac{\overline{\vartheta}}{\overline{\vartheta}_{e}}}
$$

#### Coda a Singolo Servitore
> Ogni collegamento in uscita viene schematizzato come ***sistema a coda con singolo servitore***.

>[!Ipotesi]
1. Le perdite di pacchetti in prima approssimazione sono ***trascurabili***.
	- $\lambda_{p}=0, \lambda_{s}=\lambda$
2. I pacchetti arrivano casualmente con [[3 - Variabili Aleatorie#Variabili di Poisson|Distribuzione di Poisson]]. ($k$ arrivi al tempo $t$)
3. La dimensione dei pacchetti è ***casuale*** con [[11 - Variabili Esponenziali|distribuzione esponenziale]] uguale per tutti i pacchetti.

##### Utilizzazione
>[!tldr] Situazione ideale
>Idealmente si vorrebbe il ***servitore sempre attivo***, un servitore in pausa è uno *spreco di risorse*.

Definiamo $\rho$ come la percentuale di utilizzazione del servizio data da:
$$
\rho=\frac{B(T)}{T}
$$
- $B(T)$: Tempo in cui il servizio è usato.
- $T$: Tempo totale.

![[Utilization.png]]

$\rho$ può anche essere visto come: $\displaystyle{\frac{\lambda}{\mu}}$
- Rapporto tra il ritmo di arrivo delle richieste quello di servizio.

>[!summary] Tempo medio di Attesa in coda
>$$T_{A}=\overline{\vartheta} \frac{\rho}{1-\rho}$$
>>[!done] Se il tempo di servizio ($\rho$) diminuisce, lo fa anche il tempo di attesa in coda

>[!danger] Attenzione
> Con valori di $\rho$ vicini a $1$ (**occupazione alta**), il tempo di attesa in coda aumenta esponenzialmente.

Se il servizio è deterministico, viene migliorato leggermente:
$$T_{A}=\overline{\vartheta} \frac{\rho}{2(1-\rho)}$$
In un sistema a servitore singolo l'utilizzazione è la ***percentuale di tempo per cui il servitore è impegnato***.
- In un sistema ergodico questa è anche la probabilità di trovare il *servitore occupato in un istante qualunque*.

>[!definizione] Ergodicità
>L'***ergodicità*** è il principio fondamentale per cui il comportamento di un sistema nel tempo *è rappresentativo del suo comportamento collettivo*.
>Se un sistema è ergodico, osservarlo a lungo è come osservare tanti sistemi uguali tutti insieme.

#### Problema nella Progettazione dei Protocolli
>[!Padding]
>Pacchetti di ***lunghezza predeterminata*** e tutti uguali *migliorano le prestazioni* in caso di accodamento.

I dati utente arrivano in quantità casuale quindi è necessario il ***padding***.

>[!info]
>Il padding è una sequenza di `bit` senza significato, solo di **riempimento**.

