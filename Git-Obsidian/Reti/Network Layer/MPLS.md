## Label Switching
---
>[!definizione]
>Il ***label switching*** consiste nella scomposizione della [[Routing/Routing|funzione di instradamento]] in due componenti: *controllo* e *trasferimento*.

> ***Controllo***
- La componente di controllo si basa su *protocolli di rete convenzionali* e meccanismi di associazione delle etichette.

> ***Trasferimento***
- La componente di trasferimento si basa su *hardware veloce* e *identificazione* basata su etichette dei flussi informativi.

>[!done] Vantaggi
- Mantenimento dei protocolli di routing [[Protocollo IP|IP]] standard ([[Routing/Open Shortest Path First|OSPF]], [[Routing/Routing Globale#Border Gateway Protocol|BGP]]).
- Trasferimento veloce dei pacchetti.

### Modalità di Trasferimento
> Si adotta un modo di trasferimento con [[../Introduzione/Comunicazione#Commutazione|commutazione]] orientata alla connessione.

>[!tldr] Idea
>La **commutazione** si basa sul riconoscimento di un'***etichetta*** (*label*) associata al [[Protocollo IP#Datagram|datagram]].

La label è trasportata dal pacchetto usando parte dell'***header di livello 2***.

>[!info] Differenze con Routing Normale
- Cambia l'algoritmo di forwarding cambia da ***longest prefix match*** a ***exact match***.
- L'algoritmo di routing può essere lo stesso delle reti standard, ***può essere diverso***.
- Apparati che non implementano l'instradamento `IP` possono commutare datagram con la tecnica [[#Multi Protocol Label Switching|MPLS]].

### Ingegneria del Traffico
>[!info]
>Usando indicazioni esplicite è possibile far ripartire i flussi di traffico su *diversi percorsi*.

È possibile avere ***percorsi alternativi già pronti*** da usare in caso di guasto.
- Si parla di *ingegneria del traffico nella rete di trasporto*.

## Multi Protocol Label Switching
---
> Protocollo definito dall'[[../Standards/Enti Importanti#Internet Engineering Task Force|IETF]] per implementare il label switching.

La label viene usata sia per il ***trasferimento*** sia per la ***gestione delle risorse***.

>[!cite] [RFC3031](https://www.rfc-editor.org/rfc/rfc3031.html) [RFC3032](https://www.rfc-editor.org/rfc/rfc3032.html)
>L'`MPLS` è stato concepito per poter trasferire *flussi di unità informative* in una rete a [[../Introduzione/Comunicazione#Commutazione|commutazione di pacchetto]] ***garantendo parametri di qualità di servizio analoghi a quelli di reti a commutazione di circuito***.

Ciò si realizza rendendo possibile l’***individuazione di percorsi attraverso la rete IP*** (percorsi `MPLS` o *Label-Switched Path* `LSP`).
- Nei percorsi vengono trasferiti tutti i *datagram* di un **dato flusso** ingresso-uscita.
- L’inoltro lungo il percorso è reso possibile dalla definizione di ***etichette*** (*label*)
	- Usate per identificare lo specifico **circuito virtuale** su un collegamento fisico tra [[Routing/Routing#Router|router]].

>[!tldr] Idea del Funzionamento

Un percorso `MPLS` è caratterizzato da una serie di router `LSR` (*label switching routers*, router **capaci di label switching**), dei quali: 
- Il *primo* lungo il percorso ***aggiunge l’etichetta*** `MPLS` al datagram IP 
- L’*ultimo* la ***rimuove***.

Ciascun router mantiene una ***tabella di instradamento*** detta *Label Forwarding Information Base* (`LFIB`), composta da:
- Elenco delle *label attive*.
- ***Interfaccia*** sulla quale va inviato un datagram con una certa label.
- ***Nuova label*** da associare al datagram.

L'`LSP` è definito dal percorso attraverso uno o più `LSR` seguito dai pacchetti appartenenti ad una `FEC`.

- ***Label Edge Router*** (`LER`): Router che attribuiscono ai pacchetti entranti nel dominio `MPLS` la **label** (la *tolgono agli uscenti*).
	- Determina la `FEC` e il *next hop*
	- Se il **next hop** è un `LSR` viene determinata la **label da aggiungere**.
	- Invia il pacchetto.
- ***Dominio*** `MPLS`: Gruppo di `LSR` connessi.
- ***Binding***: Associazione tra `FEC` e *label*.
- ***Next Hop***: Nodo a valle del nodo corrente.
### Label
>[!definizione]
>La ***label*** è un'entità breve e di lunghezza fissa.
>>[!warning] **Non** codifica gli indirizzi di rete.

#### Formato del Pacchetto
>[!concept] Posizionamento delle Label
>È *trasportata assieme al pacchetto*, inserita tra l'intestazione del **protocollo di linea** e l'intestazione del **protocollo di rete**.

![[attachements/MPLS.png]]

>[!abstract] Parametri

> ***Label***
- Etichetta vera e propria.

> ***Exp***
- Riservato per *uso sperimentale*.

> ***S***
- Usato per ***label stacking*** in reti `MPLS` gerarchiche.
	- `S=1` se non ci sono ulteriori etichette.
	- `S=0` altrimenti.

> ***TTL***
- Simile al [[Protocollo IP#Datagram|pacchetto IP]].
	- Si vuole sapere il numero di `LSR` attraversati.
	- Il `TTL` viene inserito nella label `MPLS` con lo stesso valore dell'header `IP` all'ingresso del primo `LSR`.
	- Viene *decrementato* ad ogni ***hop*** di un `LSR`.
	- Viene infine copiato nell'intestazione `IP` all'uscita di un domain.
##### Label Stacking
>[!hint] È possibile innestare domini `MPLS`
>Si realizzano **diversi livelli di instradamento**.

> ***Push Label***
- Quando si entra in un dominio viene aggiunta un'etichetta del dominio.

> ***Pop Label***
- Uscendo dal dominio si toglie.

#### Gestione delle Label
>[!abstract] Inizio
>L'`LSR` associa una label ad ogni `LSP` (*label binding*), il router riconosce e associa la label i pacchetti che appartengono alla medesima `FEC`.

1. Si concorda la label con il `LSR` a monte.
2. Si calcola il prossimo `LSR` di un `LSP`.
3. Si concorda una label con il `LSR` a valle.

>[!caution] Label Swapping
>Quando un `LSR` riceve un ***datagram***:
- Estrae la *label di ingresso*.
- Cerca nella tabella `LFIB` il *record relativo alla label*.
- ***Sostituisce*** la label di ingresso con la label di uscita.
- Invia il pacchetto sull'interfaccia specificata verso il *next hop*.

>[!failure] Label Merging
>Se l'allocazione della label ***non dipende dall'interfaccia***, può accadere che due o più flussi di traffico siano ***aggregati in un unico flusso***.
### Flusso di Pacchetti
>[!definizione]
>Un ***flow*** (*flusso*) è una sequenza di datagram inviati da una particolare sorgente a una particolare destinazione e accomunati da:
>- Medesima ***route***.
>- Uniformi richieste di ***qualità di servizio***.
>- Insieme delle ***politiche di gestione*** richieste nei router.

#### Forwarding Equivalence Classes
>[!info]
>Una `FEC` è un ***gruppo di pacchetti*** che condividono *caratteristiche identiche* (`IP` di destinazione, porte, [[../Data Link Layer/Networks/VPN]]) e che quindi vengono **instradati nello stesso modo**, assegnati alla stessa etichetta `MPLS` e inviati lungo lo **stesso percorso** attraverso la rete.

Durante l'instradamento, tradizionalmente si valuta ad ogni "**hop**" il contenuto della `FEC`.

> Con `MPLS`
- Si associa a una `FEC` una ***label*** all'ingresso del dominio.
- I `LSR` instradano i pacchetti *identificati dalla stessa label*.