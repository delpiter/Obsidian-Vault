## Standard di Internet
---
### Enti di Gestione
>[!abstract] Internet Society
>Insieme di *enti di coordinamento* delle attività di **ricerca** e di **sviluppo**.

Dalla internet society dipende l'**I**nternet **A**dvisory **B**oard (***IAB***) che si compone di due gruppi:
- ***IETF***
- ***IRTF***

##### Internet Engineering Task Force
>L'*IETF* è stato creato con lo scopo di coordinare le ***attività di ingegnerizzazione ed implementazione***

##### Internet Research Task Force
>L'*IRTF* è stato creato con lo scopo di coordinare le ***attività di ricerca***

## RFC
---
>[!info] Definizione
>Un ***RFC*** (*Request for Comments*) è un documento pubblicato dalla [[#Internet Engineering Task Force]] che riporta *informazioni o specifiche* riguardanti **nuove ricerche** o innovazioni dell'ambito di **internet**

I vari protocolli sono frutto del lavoro di gruppi di ricerca
- Gli ***RFC*** sono documenti di *pubblico dominio* distribuiti liberamente a chiunque li richieda

> I documenti in **procinto di diventare standard** evolvono secondo i seguenti passi:
- **Proposed Standard**
- **Draft Standard**
- **Standard**

## IANA
---
>[!summary] IANA
>L'***Internet Assigned Number Authority*** ha la responsabilità nell'assegnazione degli indirizzi **IP**.
>Mantiene i *database* dei numeri che hanno *significati convenzionali* nei protocolli internet.


## Internet Service Provider
---
>[!definizione]
>Un `ISP` è un'organizzazione che fornisce servizi per l'utilizzo di internet.

Tipicamente un `ISP` si registra come [[../Network Layer/Routing/Routing Globale#Routing Gerarchico|Autonomous System]].

Un `ISP` locale fornisce un servizio a *gruppi di utenti co-localizzato*.
- Realizza un'infrastruttura con router e switch in un punto della zona detto ***Point of Presence*** (`PoP`).

Un `ISP` collega i propri utenti tramite:
- ADSL.
- [[../Physical Layer/Strato Fisico#Fibra Ottica|Fibra Ottica]]. 
- [[../Physical Layer/Radio Comunicazioni|Collegamento Radio]].

### Interconnessione tra ISP
> Teoricamente ogni `ISP` dovrebbe fare peering con ogni altro `ISP` con cui scambia traffico.

>[!fail] Grande numero di collegamenti dedicati

>[!done] Soluzione
>Alcuni `ISP` svolgono la funzione di `AS` di ***transito*** per interconnettere con una [[../Introduzione/Topologie di Rete|topologia]] a stella gli `ISP`.

Gli `ISP` specializzati nel fornire servizi di transito sono anche detti `NSP` (***N***etwork Service Provider).
- Gli `NSP` spesso coincidono con gli `ISP` di ***tier 1***.
- Per la connessione tra `ISP` e `NSP` esistono gli `IXP` (Internet Exchange Point).

### Classificazione

>[!info] Tier 1

Un `ISP` che all'interno di una ***internet region*** raggiunge tutte le reti senza accedere a servizi a pagamento di altri.
- Possono essere nazionali (servono una sola `IR`) o globali.

>[!abstract] Tier 2

Un `ISP` che raggiunge l'internet globale acquistando servizi di interconnessione da un `ISP` ***tier 1***.

>[!summary] Tier 3

Un `ISP` che serve un'area **abbastanza delimitata**.
- Per raggiungere l'internet globale acquista servizi di interconnessione da un `ISP` **tier 2**.

### Peering
>[!important] Relazione di Peering
> Una ***relazione di peering*** è una interconnessione fra due `AS` (appartenenti a `ISP` *diversi*) stabilita al fine di scambiarsi traffico.

Il peering avviene fra gli `ISP` dello stesso livello.

## IEEE
---
>[!quote] Institute of Electrical and Electronics Engineers
>"`IEEE` is an American charitable professional organization for ***electrical engineering***, ***electronics engineering***, and *related disciplines*"

>[!tldr] Institute of Electrical and Electronics Engineers Standards Association
>L'`IEEESA` è un settore del `IEEE` incaricato dello ***sviluppo di standard*** in un ampio range di discipline.

### Progetto IEEE 802
>[!info] Idea
>Progetto creato per *tentare di definire* degli standard [[../Data Link Layer/Networks/LAN]].

> [IEEE 802 - Wikipedia](https://en.wikipedia.org/wiki/IEEE_802)

![[attachements/IEEE802Project.png]]