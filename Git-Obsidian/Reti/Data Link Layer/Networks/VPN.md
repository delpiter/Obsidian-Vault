## Rischi della Comunicazione Remota
---
> Rispetto al normale flusso delle informazioni, possono avvenire:

>[!missing] Blocking
>L'informazione ***non raggiunge il destinatario***.

![[attachements/Blocking.png]]

>[!bug] Sniffing
>Un ente *terzo* **ascolta la comunicazione**.

![[attachements/Sniffing.png]]

>[!caution] Counterfeiting
>Un ente *terzo* fa da "***ponte***" tra sorgente e destinatario.

![[attachements/Counterfeiting.png]]

>[!abstract] Spoofing
>Un ente *terzo* si **finge il mittente**.

![[attachements/Spoofing.png]]

## Virtual Private Network
---
>[!definizione]
> Una `VPN` è una rete privata creata all'interno di una ***infrastruttura di rete pubblica***.
>>[!hint] Sarebbe come collegarsi con un cavo fisico alla rete interna

Una `VPN` è una [[Virtualizzazione di Rete|rete di overlay]] attraverso **reti pubbliche**.

### Obbiettivi
> Gli obbiettivi di una rete privata sono:

>[!todo] Riservatezza
>Le informazioni **non sono leggibili** da tutti.

>[!done] Autorizzazione
>Definisco il *sottoinsieme* di coloro che sono ***in grado di leggere*** i dati.

>[!check] Autenticazione
>Verifico **chi sta leggendo i dati**.

>[!help] Paternità
>Garantisco l'***origine dei dati***.

### Tipologie di VPN
#### Remote Access VPN
>[!tldr] Idea
>Su una network viene configurato un server `VPN`.
>Tutti i clienti si collegano al server da un ***punto qualunque di internet***.

Il collegamento è ***instaurato*** dall'utente.
- Anche detto *roadwarrior*.

Si configura come una rete di comunicazioni sicure sul server `VPN`.
>[!warning] Problema
>Ogni host *richiede un tunnel privato*.

#### Site to Site VPN
>[!tldr] Idea
>Si ha una sede centrale con un ***server centralizzato***, diverse *filiali remote* vengono connesse tramite `VPN`.

L'utente interno alle filiali remote ***non è a conoscenza del collegamento***.
- Avviene in *automatico*.

Viene ***mascherato*** l'indirizzamento interno reale.
### Protocolli VPN
#### IPSec
>[!info] Documenti IPSec
>- [RFC 2401](https://www.rfc-editor.org/rfc/rfc2401.html)
>- [RFC 2402](https://www.rfc-editor.org/rfc/rfc2402.html)
>- [RFC 2406](https://www.rfc-editor.org/rfc/rfc2406.html)
>- [RFC 2408](https://www.rfc-editor.org/rfc/rfc2408.html)

>[!todo] `IP` Security
>Una ***Security Association*** è un accordo negoziato tra due dispositivi di rete che definisce i *parametri di sicurezza* specifici per un ***flusso di dati unidirezionale sicuro***.

> Una `SA` è definita da:
- Security Parameter Index (`SPI`).
- `IP` Destination Address.
- Security Protocol Identifier.

> Due modalità possibili di `SA`
- Transport Mode
- Tunnel Mode

#### Tunnel vs Transport

>[!tldr] Idea
> Nel ***transport*** si *aggiungono gli header* dei protocolli utilizzati.

![[attachements/Transport.png]]

>[!tldr] Idea
>Nel ***tunnelling*** il pacchetto intero viene "*incapsulato*".

![[attachements/Tunnel.png]]
- Anche l'**IP** interno è criptato.
#### Formato
> Lo standard `IP`Sec è un insieme di $3$ **protocolli**.

>[!caution] Internet Key Exchange
>Il protocollo `IKE` è il protocollo utilizzato per lo ***scambio delle chiavi***.
>- Vengono decise gli algoritmi e le chiavi [[../../Crittografia|crittografiche]].

> Scambio a $2$ Fasi
1. ***Negoziazione Preliminare***
	- Uno dei due nodi (*initiator*) tenta di contattare l'altro.
	- I due nodi si autenticano e creano un canale sicuro criptato.
		- Si usano **certificati** o "*pre-shared key*"
2. ***Negoziazione della Connessione***
	- All'interno del canale sicuro creato, i due nodi si accordano su *parametri di sicurezza* che verranno usate per la comunicazione.
	- Si generano e si rinnovano le **chiavi crittografiche**.

>[!todo] Authentication Header
>Garantisce ***autenticazione e integrità*** dei dati e l'identità del mittente.
>>[!warning] Non è criptato

>[!tip] Encapsulating Security Payload
>Garantisce ***confidenzialità***, ***integrità*** e **autenticazione**.
>>[!done] Criptato

I protocolli `AH` e `ESP` sono *protocolli succedanei* (uno esclude l'altro).
>[!question] Quando usare `AH`?
- Quando al livello superiore il protocollo è **già criptato**.
