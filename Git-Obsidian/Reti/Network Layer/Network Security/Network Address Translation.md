#reti_2
## NAT
---
>[!cite] Network Address Translation
>Il `NAT` è ([RFC 3022](https://www.rfc-editor.org/rfc/rfc3022.html)) una tecnica attuata dal router che *sostituisce* l'[[Protocollo IP|indirizzo IP]] sorgente o destinazione **con un altro indirizzo**.

Maschera la rete privata utilizzando il [[Routing#Ruolo del Gateway|gateway]].
- Permette ad una rete privata di accedere ad internet attraverso un solo `IP`.

Il router analizza e modifica gli *header dei pacchetti* in ingresso/uscita con lo scopo di ***cambiare gli indirizzi degli end-point***.
- Agisce su indirizzi `IP` e [[Livello di Trasporto#Numero di Porta|numeri di porta]].

>[!warning] Sicurezza
>Non fornisce il livello di sicurezza di un [[Firewall]] ma offre già buone garanzie.

Nasconde gli host interni e **non indirizza** il *traffico generico proveniente dall'esterno*.
- Include [[Firewall#Packet Filter Firewall|packet filter]] e [[Firewall#Stateful Packet Inspection Firewall|stateful packet inspection]] configurati dinamicamente.

### Conversione di Indirizzi
>[!info] Basic NAT
>Il `NAT` può fornire una ***semplice conversione*** di indirizzo `IP`.

- Il router **mantiene la stessa** porta della **sorgente** all'uscita, modificando solo l'`IP` *inserendo quello del gateway*.

>[!tip] Conversione di Indirizzo e Porta
>Il `NAT` può fornire anche conversione di indirizzo `IP` e porta [[TCP]] o [[UDP]].

- Il router può anche cambiare la **porta sorgente**.
- Consente al router di utilizzare un singolo `IP` per gestire $65536$ connessioni private ***contemporaneamente***.

>[!danger] Nota Bene
>Il `NAT` modifica l'intestazione `IP` e `TCP`/`UDP`, questo potrebbe causare problemi in alcuni casi specifici.
>- [[FTP#Connessione Passiva|FTP]].

### Direzione delle Connessioni
>[!caution] Connessione Tipica
>Tipicamente una connessione va dalla **rete privata** verso la **rete pubblica**.

Sarà il `NAT` a preoccuparsi a effettuare la conversione inversa quando arrivano le ***risposte***.

#### Port Forwarding
>[!definizione]
>Il `NAT` permette l'ingresso di ***pacchetti destinati a porte specifiche*** effettuando la traduzione opportuna.