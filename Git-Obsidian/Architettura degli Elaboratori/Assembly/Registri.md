## Registri [[IA-32]]
---
![[attachements/IA32Registry.png]]

## Registi di Base
---
![[attachements/CommonRegistry.png]]

>[!info] $8$ registri di utilizzo **più o meno generale**
- Fra questi i primi *4 registri* possono essere utilizzati in 3 *modalità*
	1. A $8$ `BIT` $\to$ `AL,AH,BL,BH,...`
	2. A $16$ `BIT` $\to$ `AX,BX,CX,DX,...`
	3. A $32$ `BIT` $\to$ `EAX,EBX,ECX,...`

>[!info] ***Instruction Pointer*** `EIP`:
- Contiene l'indirizzo della prossima istruzione da eseguire
- Viene *incrementato automaticamente* durante il **Fetch** delle istruzioni e *modificato dalle istruzioni di salto*

### Flags di Stato
>[!info] ***EFLAGS***, `BIT` di stato
- Questo registro contiene diversi `BIT` utili sia alla `CPU` sia al programmatore
- I `BIT` principali determinano i cosiddetti **condition code**
	- Vengono scritti a ogni ciclo dell'`ALU` e riflettono il risultato dell'operazione e riflettono il risultato dell'operazione più recente

>[!abstract] Flag più comuni
*Tra parentesi il nome visualizzato nel debug di Visual Studio*
- `CF` (`CY`): ***Carry Flag***
	- Attivo quando il risultato ha determinato un riporto uscente
- `PF` (`PE`): ***Parity Flag***
	- Attivo quando il `BYTE` meno significativo del risultato ha il numero di `0` o `1` *pari*
- `AF` (`AC`): ***Auxiliary Flag***
	- Attivo quando il risultato ha determinato *riporto intermedio* sul `BIT` 3
- `ZF` (`ZR`) ***Zero Flag***
	- Attivo quando il risultato è *zero*
- `SF` (`PL`) ***Sign Flag***
	- Attivo quando il risultato è negativo
- `OF` (`OV`) ***Overflow Flag***
	- Attivo quando il risultato ha causato *overflow* con operazioni in aritmetica intera con segno
- `DF` (`UP`) ***Direction Flag***
	- Indica la direzione nelle istruzioni di *manipolazione stringhe*

Altri `BIT` sono dedicati alla [[IA-32#Modalità Operative|modalità operativa]] e a particolati **modalità di funzionamento**
- Come esecuzione *step by step* o *interrupt*

## Organizzazione della Memoria
---
>[!tip] Costruzione di Indirizzi nelle diverse Modalità Operative

Il processore `8086` originale (`16 BIT`) poteva gestire fino a `1MB RAM`
- 16 `BIT` potevano gestire fino a `65.536` indirizzi di memoria
- $1MB\geq 65536$

>[!question] Come poteva indirizzare tutte le celle di memoria?


### Real
Venivano combinati due registri a `16 BIT` (`CS`, `DS`, `...`) per ottenere un singolo ***indirizzo a `20 BIT`***
- Non è supportata la *paginazione*
### Virtual $8086$
L'*indirizzo* a `20 BIT` viene determinato come nella ***modalità real***
- Il *sistema operativo* è in grado di trasformarlo in un *indirizzo* a `32 BIT` 
- È supportata la paginazione

### Protected
Un registro di segmento a `16 BIT` è combinato con un indirizzo a `32 BIT`
- Supporta il modello di ***memoria segmentato*** o **flat** con *paginazione*

![[attachements/MemoryAddressing.png]]
### $\text{x}64$ Compatibility Mode
L'indirizzo a `32 BIT` viene determinato come nella modalità *protected*
- Convertito poi a `64 BIT` considerando i 32 `BIT` alti pari a zero
- Gli indirizzi virtuali a `64 BIT` sono convertiti in indirizzi fisici mediante paginazione

### $64$ `BIT` Mode
I principali registri di segmento (`CS`,`DS`,`ES`,`SS`) sono sostanzialmente ignorati
- Il modello di memoria è **flat** 
- Gli indirizzi virtuali a `64 BIT` sono convertiti in indirizzi fisici mediante paginazione

![[attachements/MemoryAddressingx64.png]]
