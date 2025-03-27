> Versione "*sicura*" dell'[[HTTP]]

>[!tip] Strategie di sicurezza
>Per la comunicazione in rete si applica in generale il *principio di sicurezza minimo*, che consiste nel:
>- Proteggersi dagli ***attacchi passivi***.
>- Accorgersi degli ***attacchi attivi***.

La [[Crittografia#Asimmetrica|chiave pubblica]] diventa *certificato*.

## Autenticazione e Confidenzialità
---
> Autenticazione e confidenzialità hanno ***significato ben diverso***.

>[!note] Autenticazione
> L'***autenticazione*** consiste nell'avere la **garanzia** che l'utente con cui si collega per la comunicazione *è realmente chi dice di essere*.

>[!info] Confidenzialità
>La ***confidenzialità*** consiste nella **criptazione**, nel tenere il contenuto della comunicazione *nascosto*.

## Certificati
---
>[!tldr] Idea
> Il server ***deve avere*** un documento che lo autentica.

Il **certificato** va *verificato*:
- La verifica dei certificati è delegata ad **autorità** che **certificano** la *proprietà della chiave pubblica*.

L'ente verifica una serie di dati sul server e poi crea il certificato.

>[!abstract] Certification Authority
>Si ricorre a **terze parti**, dette ***Certification Authority***, che garantiscono *lʼintegrità* e *lʼautenticità* dellʼelenco delle chiavi pubbliche.

La ***certification authority*** deve essere al di sopra di ogni *sospetto*, compatibilmente con il livello di sicurezza desiderato.
- La **CA** genera un certificato contenente la *chiave pubblica* dell'utente e lo firma con la ***propria chiave privata***.

>[!danger] Certificato self-signed
>Quando il server si crea il certificato da solo, quel certificato si dice ***self-signed***.
>Il browser riconosce questo tipo di certificato e ti *avverte*.

### Generazione di un Certificato
> Il certificato viene generato con i seguenti passaggi.

1. L'utente genera la ***coppia di chiavi***.
2. Utilizzando la chiave pubblica della *Certification Authority* **crea un messaggio cifrato** contenente la propria *chiave pubblica*.
3. Invia il messaggio alla *Certification Authority* che è l'unica in grado di leggerlo.
4. La *CA* genera il certificato contenente la chiave pubblica dell'utente e lo ***firma*** (*firma digitale*) con la *propria chiave privata*.
5. Qualunque altro utente può **verificare** che il certificato sia stato firmato dall'*Authority*

#### Struttura
> Il certificato si compone di diverse parti

*Numero di Serie*
- **Identifica** in modo univoco il certificato.

*Certification Authority*
- La **CA** che ha *prodotto* il certificato.

*Validità*
- La **validità temporale** del certificato.

*Firma*
- Un **hash** di **tutti** i **campi** precedenti del certificato.

#### Firma Digitale
>[!tldr] Idea
>La ***firma digitale*** consiste nel passare il messaggio in una [[Funzione di Hash]], cifrare il risultato ottenuto con la propria chiave privata e infine "*appendere*" al messaggio originale la **cifratura del messaggio hash**.

Così facendo, *chiunque* abbia la **chiave pubblica** dell'ente che firma il messaggio è in grado di **verificare** l'**autenticità** dello stesso.

![[DigitalSignature.png]]