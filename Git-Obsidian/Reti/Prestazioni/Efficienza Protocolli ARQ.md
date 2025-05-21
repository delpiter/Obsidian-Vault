## Prestazioni Stop-and-Wait
---
>Il protocollo [[ARQ]] ***Stop and wait*** equivale ad un protocollo a finestra scorrevole con finestra unitaria.

>[!info]
>Siano:
>- $D$: Dimensione campo dati in `bit`.
>- $H$: Dimensione dell'header `PCI` in `bit`.
>- $F=D+H$: Lunghezza totale del frame.
>- $A$: Lunghezza dell'`ACK`.
>- $E, \ E'$: *Tempi di elaborazione* per il controllo del frame in partenza.
>- $R$: *Tempo di propagazione del segnale* da un campo all'altro del collegamento.
>- $I=E+R\qquad I'=E'+R'$
>- $C,\ C'$: Velocità dei canali di trasmissione.

![[StopAndWait.png|400]]

### Efficienza
>Chiamiamo $T_{0}$ il tempo intercorso fra l'***invio di due frame successivi***.

$$
T_{0}=\frac{F}{C}+I+\frac{A}{C'}+I'
$$
- Il tempo strettamente necessario per la trasmissione dei dati utente:
$$
T_{u}=\frac{D}{C}
$$

>[!tip] Efficienza
>$$\eta=\frac{T_{u}}{T_{0}}=\frac{D}{CT_{0}}=\frac{D}{\left( D+H+IC+I'C+\frac{AC}{C'} \right)}$$

Per semplicità poniamo $I=I'$ e $C=C'$, inoltre l'`ACK` è praticamente composto dalla sola `PCI` quindi $A\approx H$.

$$
\eta=\frac{D}{(D+2H+2IC)}=\frac{D}{(D+O)}
$$
>[!abstract] Overhead
>Rappresenta la quantità di ***dati aggiuntivi introdotti dal protocollo***.
>$$O=2H+2IC$$
>
>È una *grandezza* in `bit`.
>- L'efficienza **diminuisce** al **crescere** di $O$.
>	- $H$ Cresce: Molti `bit` per `PCI`.
>	- $C$ Cresce: **Linea Molto Veloce**.
>	- $I$ Cresce: **Grandi distanze**.

Tiene conto di:
- `bit` aggiuntivi di protocollo.
- Tempo non usato dalla trasmissione a causa del protocollo.

#### Caso con Errore
> Prima di trasmettere un frame correttamente, possono avvenire $k\geq 0$ **errori**.

Il tempo necessario a trasmettere il frame, dati $k$ errori, vale:
$$
T_{k}=kT_{e}+T_{0}
$$
*Dove*:
$$
T_{0}=\frac{D+O}{C}\qquad T_{e}=\frac{D}{C}+\frac{H}{C}+T_{out}
$$
>[!danger] Errori
>Se $P_{k}$ è la probabilità di avere $k$ errori, il tempo medio per trasmettere un frame vale:
>$$E[T_{k}]=\sum_{k=0}^{\infty}T_{k}p_{k}=\sum_{k=0}^{\infty}(kT_{e}+T_{0})P_{k}$$

![[TransmissionWithError.png|300]]

>[!check] Determinare $P_{k}$
>> Ipotesi
>
>Gli errori sui ***frame*** sono *indipendenti* e *identicamente distribuiti* (di uguale [[3 - Variabili Aleatorie#Schema Successo-Insuccesso a Prove Indipendenti Consecutive|probabilità]]).
>- $P_{F}=$ Probabilità di errore per *ciascun frame*. 
>$$P_{k}=P\{ k \text{ frame errati seguiti da uno corretto} \}=P_{F}^{k}(1-P_{F})$$

Il numero medio di errori consecutivi risulta $E[k]=\frac{P_{F}}{1-P_{F}}$ #wtf $E[k]=\frac{1-P_{F}}{P_{F}}$
- ([[6 - Valore Atteso#Valore Atteso di una Variabile Geometrica]])

Sia $P_{e}$ la probabilità di un errore per `bit`.
$$P_{F}=1-P_{\text{frame corretto}}=1-(1-P_{e})^{F}\approx FP_{e}$$

> ***Valore medio di*** $T_{k}$.
- In teoria possono essere errati i **frame** ma anche gli `ACK`.

Se vale la formula $P_{F}=FP_{e}$

