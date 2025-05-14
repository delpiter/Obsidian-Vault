> Layer che sta al di sopra del [[Descrizione dei Livelli#Network Layer|network layer]] è lo strato che si occupa di creare un dialogo ***end-to-end***.

>[!hint] Obbiettivo
>L'**obbiettivo** del *livello transport* è quello di garantire il dialogo affidabile fra le applicazioni finali.

>[!help] Protocolli
>Il livello di trasporto ha due protocolli:
>- [[TCP]]: *Connection Oriented*.
>- [[UDP]]: *Connectionless*.

Il ***network layer*** consente di applicare una strategia di [[Multiplexing]] nella comunicazione.
- Permette a più processi applicativi di usare le *funzioni di comunicazione in contemporanea*.

Questo layer ha il compito di controllare il *comportamento del canale di comunicazione* ***end-to-end***.
### Numero di Porta
>[!info] Indirizzo
>Il ***numero di porta*** è l'*indirizzo* del livello transport.
>Formato da $16$ `bit` (valori da $0$ a $65535$)
>- **Locale** ad ogni singolo calcolatore.
>- Condiviso fra tutti i ***protocolli di trasporto***.

>[!question] A cosa serve?

Il numero di porta serve a **distinguere** quale *applicazione* all'interno della macchina ha fatto ***richiesta dell'informazione***.

#### Well Known Port
>[!help] Porte Well-Known
>Le ***porte*** da $0$ a $1023$ ($[0,2^{10}-1]$) sono le ***well-known ports***.
>Sono le *porte* usate dai *processi di sistema* per ricevere ***servizi vastamente usati***.

[List of TCP and UDP port numbers](https://en.wikipedia.org/wiki/List_of_TCP_and_UDP_port_number)