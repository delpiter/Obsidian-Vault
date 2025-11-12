![[UML#^8c1477]]

## Diagramma di Deployment
---
>[!info]
>I ***diagrammi di deployment*** specificano l'*hardware* su cui verrà eseguito il software e il modo in cui il *software è dislocato* sull'hardware.

Può avere ***due forme***:

> *Descrittore*
- Contiene nodi, relazioni tra nodi e manufatti, modella i *tipi di architetture*.

> *Istanza*
- Contiene *istanze* di nodi, di relazioni tra nodi e di manufatti.
- Modella un **deployment dell'architettura su un particolare sito**.

### Componenti
>[!tip] Nodi
>Un ***nodo*** rappresenta un tipo di *risorsa computazionale* su cui i manufatti possono essere dislocati per l'esecuzione.

Due [[UML#Meccanismi di Estendibilità|stereotipi]] standard:
> `<<device>>`
- rappresenta un tipo di *periferica fisica* (es. un **PC**).

> `<<executionEnviroment>>`
- Rappresenta un tipo di *ambiente software di esecuzione* (es. un **Web Server**).

>[!important] Info
>Si possono *usare ulteriori stereotipi* e *icone* per aumentare la leggibilità del diagramma

I nodi possono essere annidati in nodi.
Una associazione tra nodi rappresenta un canale di comunicazione tra di essi.

>[!summary] Manufatti
>Un ***manufatto*** rappresenta un'entità concreta del mondo reale, per esempio:
>- File sorgenti, eseguibili, script, tabelle di un [[Git-Obsidian/DataBase/Introduzione#Database|database]], documenti, modelli [[UML]].

I manufatti vengono *dislocati sui nodi*.
![[DeploymentDiagram.svg]]