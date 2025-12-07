## 802.1q
---
>[!tldr] Idea
> Un solo [[LAN#Switch|switch]] (*managed* o *configurabile*), più [[LAN]] separate.

Ogni `VLAN` rappresenta un diverso [[Reti IP#Broadcast|dominio di broadcast]].

Lo standard `802.1q` è un protocollo che permette l'utilizzo delle stesse `VLAN` su ***diversi switch interconnessi tra loro***.

### Funzionamento
> Uno switch ha *due tipologie di porte*:

>[!abstract] Access Mode
>Una porta associata ad una sola `VLAN`, usata per connettere *un host*.
>Anche detta porta ***untagged***.

>[!caution] Trunk Mode
>Una porta associata a `VLAN` *multiple*, usata per connettere *due switch* o uno *switch* e un [[Routing#Router|router]].
>Anche detta porta ***tagged***.

>[!tldr] Idea

Lo switch gestisce l'**aggiunta** e la **rimozione** del tag all'interno del [[Rete Ethernet|frame ethernet]].
> In generale:
- Ad un frame in *entrata* in una porta **untagged** verrà aggiunto il *tag*.
	- In uscita verrà **tolto**.

>[!important] Il frame avrà il tag della `VLAN` solo: dentro lo switch o in un collegamento "**trunk**".

![[VLANExample.svg]]

#### Router on a Stick
>[!caution] Routing Inter-`VLAN`
>Se due *host* appartenenti a `VLAN` differenti devono comunicare, si rende la porta collegata al router una porta "**trunk**".

Il **router** che riceve un pacchetto con il tag, sarà in grado di *ritrasmetterlo alla rete interna* con il tag corretto.

#### Formato del Frame
![[VLANFrame.png]]

>Al ***frame ethernet*** vengono aggiunti $4$`byte` per identificare la `VLAN`.

>[!abstract] Parametri

> ***Tag Protocol Identifier***
- Identifica il protocollo utilizzato.

> ***Priority***

> ***Canonical Format Indicator*** ($1$ `bit`)
- Indica il formato del [[Struttura del Data Link#Medium Access Control|MAC]] **address**.

> ***Unique*** `LAN` ***Identifier***
- $12$ `bit` che identificano il numero della `VLAN`.
### Classificazione
#### VLAN Statiche
>[!cite] Port-Based
>Nelle `VLAN` ***statiche*** ogni porta dello switch è associata ad una `VLAN`.

Un **host** appartiene alla `VLAN` corrispondente alla porta a *cui è connesso*.
- Lo switch conosce la `VLAN` di appartenenza di un *host* in base alla ***configurazione della porta*** a cui è connesso.
#### VLAN Dinamiche
>[!quote] Address-Based
>L'appartenenza alla `VLAN` è stabilita in base all'***indirizzo dell'host***.

Possono essere basate su:
- [[Struttura del Data Link#Medium Access Control|MAC]]-based.
- [[Protocollo IP|IP]]-based.

Un host appartiene ad una `VLAN` indipendentemente dalla porta a cui è connesso.