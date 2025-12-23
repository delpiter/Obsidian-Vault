>[!info]
>Il ***firewall*** si interpone fra [[Reti IP|rete]] interna (da *proteggere*) e rete esterna (fonte di *minacce*).
>>[!done] È una linea di difesa contro le intrusioni di rete

È un apparato che può essere *co-localizzato* con il [[Routing#Ruolo del Gateway|gateway]].

Il compito del ***firewall*** è quello di filtrare tutti i pacchetti in entrata e uscita *secondo delle regole prestabilite*.

Il firewall è un filtro ***software***/***hardware***, può essere:
- Un semplice programma installato sul proprio `PC`.
- Una macchina dedicata che filtra tutto il traffico da e per una [[LAN|rete locale]].
## Categorie
---
### Packet Filter Firewall
>[!tldr] Idea
>Il ***packet filter firewall*** lavora a livello network e [[Livello di Trasporto|transport]].
>Prende le decisioni in base al contenuto dei campi del [[Protocollo IP]].

Molto efficiente poiché deve solo valutare il contenuto di pochi `byte` *header*.
- `IP` sorgente e destinazione.
- Protocollo di livello superiore.

>[!warning] Non ha possibilità di controllare i dati all'interno del pacchetto
>Un ***virus*** contenuto in una mail *passa tranquillamente*.

Confronta questi parametri con delle liste di accesso (`ACL`) che specificano **regole di comportamento**.

>[!cite] Access Control List
>L'`ACL` sono un elenco di istruzioni da applicare alle interfacce di un [[Routing#Router|router]].

> ***Tipologie***
- `ACCEPT`: Il pacchetto viene *instradato* normalmente.
- `DENY`: Il pacchetto viene *bloccato* e *cancellato*.
- `REJECT`: Il pacchetto viene bloccato e **viene inviato un messaggio di errore** alla sorgente (simile a [[ICMP#Tipi di Errori|destination unreachable]]).

> **Standard** `ACL`
- Specificano limitazioni ai pacchetti *guardando esclusivamente l'indirizzo sorgente*.

> **Extended** `ACL`
- Pongono limitazioni in base a:
	- Protocollo usato.
	- [[Protocollo IP|IP]] sorgente e destinazione.
	- [[Livello di Trasporto#Numero di Porta|Porta]] di destinazione.

``` title:"ACL examples"
deny icmp any host 10.0.1.54
permit tcp host 10.0.0.37 host 10.1.1.230
deny 10.0.10.0 0.0.0.255 host 10.0.1.254 80
```

Le `ACL` vengono consultate *sequenzialmente*.
- La prima regola che risulta vera **conclude la lettura e viene applicata**.

```sh title:"Default Rules"
# At the end of the file
permit any any # Lets any packet through except some explicit packets.

deny any any   # Blocks any packet except some explicit packets.
```

![[PacketFilterFirewall.png]]

Il packet filter è un dispositivo "**stateless**", non tiene conto di **possibili correlazioni fra pacchetti successivi**.
- Lo rende facilmente vulnerabile tramite `IP` *spoofing* (modifica dell'indirizzo `IP`).
### Stateful Packet Inspection Firewall
>[!tldr] Idea
> Simile a un *packet filter* ma capace di controllare anche ***possibili correlazioni fra pacchetti successivi***.

![[StatefulPacketInspection.png]]
### Application Layer Firewall
>[!tldr] Idea
>L'***application layer firewall*** (*proxy*) intercetta le trasmissioni a [[Protocolli Applicativi|Livello Applicativo]].

Valuta il *contenuto applicativo dei pacchetti*.
- Riconosce e blocca dati appartenenti a **virus** o **worm noti**.

A questa categoria appartengono i ***proxy***.

![[ApplicationLayerFirewall.png]]

## Configurazione Firewall
---
>[!hint] Configurazione Reale
> In una rete complessa, una rete è divisa in più zone:
>- ***DMZ***
>- [[LAN]].

![[FirewallConfiguration.png]]

### Demilitarized Zone
>[!info]
>La ***demilitarized zone*** è una zona in cui il traffico [[LAN]] e [[Infrastrutture di Telecomunicazioni|WAN]] sono fortemente **limitati** e **controllati**.

Permettono l'accesso sia da *fuori* (`WAN`) che da *dentro* (`LAN`) per fornire servizi come [[HTTPS]].
- Con policy *altamente restrittive*.

#### Tipologie
>[!missing] Vicolo Cieco
> Un solo firewall con tre *porte tagged* per: `LAN`, `WAN` e `DMZ`.
 
>[!info] Zona Cuscinetto
>Alternativa più costosa, composto da ***due firewall separati***.

Un firewall separa la `WAN` dalla `DMZ`.
Un firewall separa la `DMZ` dalla `LAN`.