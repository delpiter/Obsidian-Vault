## Data Flow Diagram
---
> I `DFD` traggono origine dalla teoria dei [[../Algoritmi e Strutture Dati/Strutture Dati/Grafi/I Grafi|Grafi]].

Un sistema è visto come una **rete di processi funzionali** interconnessi da depositi di dati (*repository*).

> [!info] Title
> I ***data flow diagram*** enfatizzano le operazioni effettuate sulle informazioni e le dipendenze funzionali che vengono a crearsi fra i vari processi in base ai *flussi di informazione*.

### Entità
> [!hint] Entità rappresentate
> In un `DFD` vengono rappresentate le seguenti entità
> - Processi
> - Flussi
> - Agenti esterni
> - Depositi dati

![[attachements/DataFlowDiagram.svg|325]]

- I ***processi*** trasformano i dati.
- I ***flussi*** muovono i dati.
- Gli ***agenti esterni*** producono e consumano dati.
- I ***depositi di dati*** memorizzano informazioni in modo passivo.

> [!cite] Definizione Formale
> Un `DFD` è una ***quadrupla*** $<P,D,A,F>$ dove:

- $P=\{ p_{1},p_{2},\dots,p_{n} \}$ è un insieme finito, non vuoto di processi
- $D=\{ d_{1},d_{2},\dots,d_{n} \}$, è un insieme finito di depositi
- $A=\{ a_{1},a_{2},\dots,a_{n} \}$ è un insieme finito di agenti
- $F=\{ f\in (P\times(P\cup D\cup A))\cup((P\cup D\cup A)\times P) \}$ è un insieme finito di flussi.

Un flusso deve coinvolgere almeno un Processo

La rappresentazione avviene tramite un grafo orientato in cui ogni nodo appartiene a uno dei tre insiemi $P$, $D$ o $A$ e ogni arco orientato rappresenta un flusso di dati.
### Tips and Tricks
> [!consigli] 

- Non rappresentare le eccezioni e il trattamento degli errori.
- Un `DFD` non è un diagramma di flusso, dove le frecce indicano un ordinamento.

> [!hint] Regole

- Scegliere nomi significativi per ciascuna entità
- Numerare i processi
- Disegnare i `DFD` seguendo criteri estetici
- Evitare `DFD` eccessivamente complessi
- Accertarsi della coerenza interna di un `DFD` e che sia coerente con quelli ad esso associati.

> [!important] Vincoli
> 

- Evitare processi a consumo infinito
- Sospettare di processi a generazione spontanea
- Depositi a sola lettura o sola scrittura sono **rari**
- Non devono esistere flussi tra:
	- Due agenti
	- Due depositi
	- Un'entità esterna e un deposito

> [!warning] Avvertenze
> 

L'assenza di nomi per le entità può esse indice di trascuratezza

> ***Convenzione***
- Un flusso da o verso un deposito può essere non etichettato se i dati trasferiti *corrispondono a un oggetto intero*.

> [!caution] Strategie per la costruzione
> 

> ***Top down***
- Decomposizione di un processo in una serie di sottoprocessi indipendenti.

> ***Bottom Up***
- A partire da una collezione di concetti elementari si costruiscono via via le connessioni tra essi.

> ***Mixed***
- Raffinamento di un `DFD` di massima in stadi successivi con tecniche sia top down che bottom up.

> ***Outside in***
- Parte dalle interfacce con il sistema e propaga in avanti gli ingressi evidenziando i processi coinvolti nei flussi dati o in alternativa propaga all-indietro le uscite.