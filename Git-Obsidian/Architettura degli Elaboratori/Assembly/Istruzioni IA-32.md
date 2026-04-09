>Di seguito le istruzioni usate nello standard [[IA-32]]
## Copia e Spostamento di Valori
---
![[attachements/AssemblyEditOperators.png]]
### MOV
>[!info] Descrizione
>`MOV DST, SRC`
>Copia un valore dall'operando `SRC` all'operando `DST`
>- `SRC` e `DST` devono avere la stessa dimensione
>- Per `SRC` è possibile utilizzare un indirizzamento *immediato*, *registro* o *memoria*
>- Per `DST` è possibile utilizzare un indirizzamento di *registro* o *memoria*
>	- Non può essere *immediato* poiché non ha senso impostare come destinazione una *costante*
>
>>[!warning] Indirizzamento
>>Non è possibile utilizzare un indirizzamento in memoria per entrambi gli operandi nella stessa istruzione
>>- Non è possibile scrivere una istruzione che copia valori da memoria a memoria

### PUSH e POP
>[!info] Descrizione
>`PUSH` e `POP` *mettono e tolgono* [[I Tipi di Dati|word]] dalla **cima** dello [[../../Definizioni/Definizioni_Architettura#Stack|stack]]
>>[!warning] Attenzione
>>Lo **stack** cresce verso il basso, ovvero verso indirizzi più piccoli, pertanto una `PUSH` causa causa, oltre alla copia, anche il decremento di `ESP` e una `POP` l'incremento di `ESP` (***E***xtended ***S***tack ***P***ointer)
>
>
>Si possono inserire solo **word** (`2 BYTE`) o **doubleword** (`4 BYTE`)

#### Esempio
```assembly
...            // ESP = 0x0023F7D8
PUSH EAX       // ESP = 0x0023F7D4
PUSH BX        // ESP = 0x0023F7D2
PUSH WORD PTR  // ESP = 0x0023F7D0
POP AX         // ESP = 0x0023F7D2, AX = 0x0010

ADD ESP 6      // Stack "Reset" ESP = 0x0023F7D8
```


### Exchange
>[!info] Descrizione
>`XCHG DS1, DS2`
>Scambia il contenuto di `DS1` e `DS2` in un'**unica** *operazione*

#### Esempio
```assembly
MOV AX, 5
MOV BX, 4
XCHG AX, BX //AX = 4 e BX = 5
```

### Load Effective Address
>[!info] Descrizione
>`LEA DST, SRC`
>Carica in `DST` (*registro* solitamente a `32 BIT`) l'[[Istruzione Assembly#Offset|offset]] di `SRC`
>`LEA` è l'acronimo di *Load Effective Address*
>

- Questo strano costrutto è utilizzato talvolta per **ottimizzare al massimo** il *codice*
	- Si sfruttano le peculiarità del modo di *indirizzamento* con *offset* per ***eseguire operazioni aritmetiche***
#### Esempi
```assembly
LEA EAX, [10456de4h]  // EAX = 10456de4
LEA EAX, pippo        // EAX = offset dell'indirizzo di pippo
```

```assembly
LEA EAX, pippo //Carica in EAX l'indirizzo di pippo
MOV [EAX], 10  // pippo = 10
```

### Conditional MOV
>[!info] Descrizione
>`CMOVcc DST, SRC`
>Istruzione simile alla `MOV` ma la copia viene eseguita solo se a condizione `cc` è vera
>La condizione viene determinata a partire dal valore dei `BIT` del [[Registri#Registi di Base|registri]] `EFLAG`
>Può essere considerato come una assegnazione con condizione

#### Esempio
```assembly
CMP AX,BX    // Confronta AX e BX, se sono uguali -> ZF = 1
CMOVZ CX, DX // Se ZF = 1 CX = DX
```

Questa istruzione risulta molto utile per evitare di usare ***salti condizionali***
- I salti condizionali generalmente *deteriorano le prestazioni* in quanto rendono inefficace il ***pre-fetching***


## Aritmetica Intera
---
![[attachements/AssemblyArithmeticOperators.png]]


### Complemento a 2
>[!info] Descrizione
>`NEG DST`
>Questa istruzione esegue il complemento a due del registro `DST`

#### Esempio
```assembly
MOV EAX, 15
NEG EAX     // EAX = -15
```
### Somma
>[!info] Descrizione
>`ADD DST, SRC`
>Questa istruzione esegue la somma fra `DST` e `SRC`
>Il risultato è **inserito in `DST`** il cui valore iniziale viene, quindi, *sovrascritto*

In base al risultato ottenuto da questa istruzione andranno opportunamente ***aggiornati i flag***:
- `OF`, `SF`, `ZF`, `AF`, `CF`, `PF`

#### Esempio
```assembly
MOV EAX, 5
ADD EAX, pippo // EAX = EAX + pippo
```

### Sottrazione
>[!info] Descrizione
>`SUB DST, SRC`
>Esegue la ***sottrazione*** `DST-SRC` e memorizza il risultato in `DST` il cui valore iniziale viene quindi *sovrascritto*

#### Esempio
```assembly
MOV EAX, 15
SUB EAX, 20 // EAX = -5 (in complemento a 2)
```

### Moltiplicazione
#### Moltiplicazione Senza Segno
>[!info] Descrizione
>`MUL SRC`
>Esegue una moltiplicazione ***senza segno***
>Il risultato dell'operazione viene messo in un registro *sufficientemente* *grande* per contenere il ***valore più grande ottenibile***
>>[!warning] Nota
>>Non è possibile usare un operando immediato per `SRC`

![[attachements/MUL.png]]
Nel caso in cui il valore più grande ottenibile si rappresenta con un numero più alto di `BIT` del registro, il risultato viene memorizzato in due registri differenti

##### Esempio
```assembly
MOV EAX, 80000000h
MOV EBX, 2h
MUL EBX             // EDX:EAX = EAX * EBX = 100000000h
					// EDX = 1h
					// EAX = 0h
```

#### Moltiplicazione con Segno
>[!question] Perchè la somma non ha bisogno di una istruzione apposita per le operazioni con e senza segno?

La somma in [[../Rappresentazione dell'Informazione/Il Calcolatore e i Numeri Binari#Complemento a due|complemento a due]] si fa nello stesso identico modo di una somma fra due numeri binari
- Di conseguenza la somma necessita di un unico circuito per essere eseguita

D'altra parte il prodotto deve tenere conto del segno separatamente

>[!info] Descrizione
>Esegue una *moltiplicazione intera* con **segno**, con operandi in ***complemento a 2***
>A differenza di `MUL` il cui formato prevede solo un operando, `IMUL` prevede *3 formati*
>>[!example] Formato 1
>>`IMUL SRC`
>>Il funzionamento è analogo a `MUL` per quanto riguarda i registri utilizzati
>
>>[!example] Formato 2
>>`IMUL DST, SRC`
>>In questo caso `SRC` può essere anche un *valore [[Istruzione Assembly#Indirizzamento Immediato|immediato]]*
>>Equivalente alla scrittura:
>>- `DST = DST * SRC`
>
>>[!example] Formato 3
>>`IMUL DST, SRC1, SRC2`
>>In questo caso `SRC2` è * **obbligatoriamente** un valore immediato*
>>Equivalente alla scrittura:
>>- `DST = SRC1 * SRC2`

>[!warning] Attenzione

Nei formati 2 e 3 possono non essere sufficienti $n$ `BIT` per memorizzare il risultato della moltiplicazione di due operandi a $n$ bit
- Sarà necessario controllare il valore del [[Registri#Flags di Stato|flag]] `OF`

##### Esempio
```assembly
MOV EAX, 10000000h
IMUL EBX, EAX, 16   // Risultato = 100000000h, EBX = 0, OF = 1!
```

### Divisione Intera
#### Divisione Senza Segno
>[!info] Descrizione
>`DIV SRC`
>Analogamente alla `MUL` la `DIV` si *comporta in modo diverso* in base alla **dimensione** dell'operando `SRC` (***divisore***)
>In particolare il *divisore*, il *quoziente* e il *resto* sono **prelevati/scritti** differentemente in base alla dimensione in `BIT` di `SRC`

![[attachements/DIV.png]]
>[!warning] Attenzione

L'operazione può causare *overflow* (es. $\frac{256}{1} =256 \implies$ overflow)
- Necessario gestirlo per prevenire il blocco del programma
#### Divisione con Segno
>[!info] Descrizione
>Per definire l'operatore `IDIV` è necessario dare una definizione al ***resto***
>>[!done] Resto
>>Il *resto* è quel numero che ***sommato*** al prodotto fra *quoziente* e *dividendo* ti da il numero originale
>
>`IDIV SRC`
>Equivalente al `DIV` ma gli operandi sono con segno

>[!warning] Problema

Quando il valore da dividere occupa solamente uno dei due registri il segno del valore deve essere "*propagato*"

>[!done] Soluzione

È stata creata una istruzione apposita per *estendere il valore* di un registro in un altro registro, ***mantenendo il segno***
- Istruzione ***specifica*** per la divisione con il *segno*
- Istruzione ***senza operandi***

`CDQ`
- Convert Doubleword to Quadword
- Converte, estendendo il segno la `DWORD EAX` nella `QWORD EDX:EAX`

`CDW`
- Converte un registro a `16 BIT` in un registro `16 BIT:16 BIT`

##### Esempio
```assembly
MOV EAX, 100
CDQ

MOV EBX, -3
IDIV EBX     // EAX = 100/-3 = -33 (quoziente), EDX = 1 (resto)
```

### Incremento
>[!info] Descrizione
>`INC DST`
>Incrementa di $1$ il valore specificato da `DST` senza alterare il [[Registri#Flags di Stato|flag]] `CF`
>Utilizzato in genere nei *cicli*

Lo stesso risultato si otterrebbe  con `ADD DST, 1`
- `INC DST` è più efficiente poiché non richiede di caricare *[[Istruzione Assembly#Indirizzamento Immediato|operandi immediati]]*

>[!note] Nota

Se `DST` ha raggiunto il valore massimo (ex. `EAX = ffffffffh`) l'istruzione incremento causa un *overflow* e quindi la destinazione assume valore `0`
- Ciò però non causa il *set* del [[Registri#Flags di Stato|flag]] `OF`
- Siccome neanche il flag `CF` viene alterato l'unico ***flag*** utile per verificare *traboccamento* è `ZF`

#### Esempio
```assembly
INC EAX    // EAX = EAX + 1
INC pippo  // pippo = pippo + 1
```
### Decremento
>[!info] Descrizione
>`DEC DST`
>Decrementa di $1$ il valore specificato da `DST` senza alterare il [[Registri#Flags di Stato|flag]] `CF`
>Utilizzato in genere nei *cilci*

Lo stesso risultato si otterrebbe  con `SUB DST, 1`
- `DEC DST` è più efficiente poiché non richiede di caricare *[[Istruzione Assembly#Indirizzamento Immediato|operandi immediati]]*

Per verificare *underflow* (***traboccamento sotto lo zero***) può essere usato il flag di segno `SF`
#### Esempio
```assembly
DEC EAX    // EAX = EAX - 1
DEC pippo  // pippo = pippo - 1
```

## Operazioni sui BIT
---
![[attachements/AssemblyBitwiseOperations.png]]
### AND, OR, XOR
>[!info] Descrizione
>`AND/OR/XOR DST, SRC`
>Sono le istruzioni per ***AND***, ***OR*** e ***XOR*** logici `BIT` a `BIT`
>Il risultato viene *sovrascritto* su `DST`

***AND*** e ***OR*** sono ampiamente usati per le operazioni di [[../Rappresentazione dell'Informazione/Mascherature dei Bit|mascheratura e impostazioni]] di `BIT`
***XOR*** molto utilizzato per *crittografia*
#### Esempi
```assembly
AND EAX, 00001111h       // EAX = EAX AND 00001111h
AND pippo, EBX           // pippo = pippo AND EBX
OR EAX, Vettore[EBX*2+4] // EAX = EAX OR dword all'indirizzo vettore+EBX*2+4
XOR EAX, EAX             // EAX XOR EAX -> azzera il registro
XOR EBX, 0a0b0c0dh       // EBX = EBX XOR 0a0b0c0dh
```

### SHL, SHR
>[!info] Descrizione
>`SHL/SHR DST, #`
>*Shift logico* `BIT` a `BIT` a sinistra (**L**eft) e a destra (**R**ight) in `DST` di un numero **specificato** di `BIT`
>- `#` Può essere un valore [[Istruzione Assembly#Indirizzamento Immediato|immediato]] a `8 BIT` compreso tra $0$ e $31$ oppure il registro `CL`

Entrambe le istruzioni pongono il `BIT` *entrante* a $0$, rispettivamente
- `SHR` pone il `MSB` a $0$
- `SHL` pone il `LSB` a $0$

#### Esempio
```assembly
MOV AL, 01001011b
SHR AL, 1          // AL = 00100101b
```

### SAL, SAR
>[!info] Descrizione
>`SAL/SAR DST, #`
>*Shift* ***aritmetico*** `BIT` a `BIT` a sinistra (**L**eft) e a destra (**R**ight) in `DST` di un numero di `BIT` specificato dal secondo operando (`#`)
>***Aritmetico*** significa equivalente ad una *moltiplicazione* per $2$ (`SAL`) o *divisione* per $2$ (`SAR`)
>- `#` Può essere un valore [[Istruzione Assembly#Indirizzamento Immediato|immediato]] a `8 BIT` compreso tra $0$ e $31$ oppure il registro `CL`
>
>>[!tip] Shift a Sinistra
>>Per ogni shift (`SAL`) atomico (1 posizione) il `BIT` *meno significativo* assume valore $0$
>>Mentre il `BIT` *più significativo* (che **fuoriesce**) finisce nel [[Registri#Flags di Stato|flag]] `CF`
>>`SAL` opera in modo identico al `SHL`, hanno lo stesso **OP-CODE**
>
>>[!tip] Shift a Destra
>>Per ogni shift (`SAR`) per ogni shift atomico il `BIT` *meno significativo* fuoriesce, finisce in `CF`
>>Mentre il `BIT` *più significativo* **estende il segno** (*stesso valore* del precedente `MSB`)

#### Esempi
```assembly
MOV EAX, 20
SAL EAX, 2      // EAX = 80

MOV EAX, -9
SAR EAX, 1      // EAX = -5
```

### ROL, ROR
>[!info] Destinazione
>`ROL/ROR DST, #`
>*Rotazione logica* `BIT` a `BIT` a sinistra (**L**eft) e a destra (**R**ight) di un numero specificato dal *secondo operando*
>- `#` Può essere un valore [[Istruzione Assembly#Indirizzamento Immediato|immediato]] a `8 BIT` compreso tra $0$ e $31$ oppure il registro `CL`
>Il `BIT` che **fuoriesce** rientra dall'*altra parte del valore*

#### Esempio
```assembly
MOV AL, 01010101b
ROR AL, 1          // AL = 10101010b
```

## Istruzioni di Salto
---
![[attachements/AssemblyJumpOperators.png]]
### Codici Mnemonici e Significato dei Condition Codes
![[attachements/ConditionCodes.png]]

### Test
>[!info] Descrizione
>`TEST SRC1, SRC2`
>L'*istruzione* `TEST` esegue l'`AND` logico fra `SRC1` e `SRC2`
>A *differenza* dell'operatore logico `AND` il **risultato** non viene scritto da *nessuna parte* ma viene utilizzato per l'*impostazione* dei [[Registri#Flags di Stato|flag]] `SF`, `ZF` e `PF` nel registro `EFLAG`

>[!question] A cosa Serve?

Le istruzioni di salto condizionato operano sulla base del valore dei flag
- Tramite questa istruzione è possibile decidere di saltare quando alcuni `BIT` di un certo registro sono impostati a $0$ o a $1$

#### Esempi

```assembly
TEST AL, 00000011b
JNZ Addr           //Salta ad Addr se uno dei BIT 0 o 1 in AL è impostato ad 1
```

### Compare
>[!info] Descrizione
>`CMP SRC1, SRC2`
>Esegue la sottrazione `SRC1-SRC2`
>Il risultato ***non viene salvato*** da nessuna parte ma viene utilizzato per l'*impostazione* dei flag `CF`, `SF`, `ZF`,`PF`,`OF`,`AF` nel *registro* `EFLAGS`

#### Esercizi
```assembly
CMP AL, 20
JE Addr    // Salta ad Addr se AL = 20
```

### Uncoditional Jump
>[!info] Descrizione
>`JMP Addr`
>Esegue un salto *incondizionato* a `Addr`
>Il salto viene eseguito caricando in `EIP` l'indirizzo `Addr`

Il programma *assemblatore* permette di utilizzare ***etichette* *simboliche***
- Esse verranno poi sostituite con **indirizzi relativi** all'*istruzione corrente*, a tempo di *compilazione del programma*
- È anche possibile specificare **indirizzi assoluti** utilizzando in ***modo indiretto*** *registri o memoria*
#### Esempio
```assembly
JMP Fine // salto all'indirizzo Fine
...
Fine: MOV AX, 20
```

```assembly
JMP [EDX] // Salta all'indirizzo di memoria 
		  // indicato dalla DWORD all'indirizzo specificato da EAX
		  // Dentro i 4 byte c'è scritto che indirizzo si deve impostare EIP
```

### Conditional Jump
>[!info] Descrizione
>`Jcc Addr`
>"Salta" all'indirizzo `Addr` ***se e solo se*** la *condition code* `cc` determinata dall'istruzione **solitamente precedente**, è vera

#### Esempio
```assembly
CMP EAX, ECX
JE Addr      // Salta ad Addr se EAX = ECX
```

```assembly
CMP EAX, ECX
JB Addr      // Salta ad Addr se EAX < ECX (unsigned)
```

```assembly
CMP EAX, ECX
JA Addr      // Salta ad Addr se EAX > ECX (unsigned)
```

```assembly
CMP EAX, ECX
JNE Addr     // Salta ad Addr se EAX != ECX
```

### Conditional Jump for LOOP
>[!info] Descrizione
>`JCXZ Addr` e `JECXZ Addr`
>Versioni particolari di `Jcc`
>`JCXZ` salta ad `Addr` se `CX` $=0$
>`JECXZ` salta ad `Addr` se `ECX` $=0$
>Queste istruzioni sono *specifiche* per il controllo per l'istruzione `LOOP`

### Loop e Conditional Loop
>[!info] Descrizione
>`LOOP Addr`
>Si tratta di un'istruzione compatta e ottimizzata per l'***esecuzione di cicli***
>Per la variabile di **contatore** viene *obbligatoriamente utilizzato* il registro `ECX`
>Simile al `do{}while();` nei linguaggi ad alto livello
>Non altera i [[Registri#Flags di Stato|flag]]

>[!info] Descrizione
>`LOOPcc Addr`
>Variante dell'istruzione `LOOP`
>Oltre che a controllare quando `ECX` diventa $0$ controlla anche 1 di 4 ***condition code***:
>- `E`, `Z`, `NE`, `NZ`
> Sarebbe come mettere in `AND` le ***due condizioni***

>[!warning] Attenzione

È fondamentale avere la *sicurezza* che `ECX` sia ***diverso*** da $0$
Dato che il *controllo condizionale* è fatto **dopo il decremento** di `ECX`
- $0-1\implies 2^{32}$
- E ciò vuol dire che prima che `ECX` torni a $0$ verranno eseguiti $2^{32}$ *cicli*
#### Esempio
>*Somma in `EAX` gli elementi di un vettore di `DWORD` di lunghezza $10$*
>*Offset da $0$ a $9$ con ogni elemento 4 `BYTE`*

```assembly
MOV ECX, 10    // Valore iniziale di ECX
XOR EAX, EAX
Ciclo: ADD EAX, Vettore[ECX*4-4]  // Si scorre l'array da 9 a 0
	   LOOP Ciclo
```

- Un risultato uguale ma ***meno efficiente*** può essere ottenuto con:

```assembly
MOV ECX, 10    // Valore iniziale di ECX
XOR EAX, EAX
Ciclo: ADD EAX, Vettore[ECX*4-4]
	   DEC ECX
	   JNZ Ciclo
```

L'istruzione `LOOP` costringe a ***contare all'indietro*** e ad utilizzare `ECX`

#### Esempio
```assembly
MOV ECX, 10    // Valore iniziale di ECX
XOR EAX, EAX
Ciclo: ADD EAX, Vettore[ECX*4-4]
	   CMP EAX, 100
	   LOOP Ciclo
```
In questo caso il ciclo si conclude con due condizioni
1. Quando `EAX` $=0$
2. Quando in un qualsiasi momento la *somma dei valori* è $=100$ 

>[!tip] Se non sono sicuro dell'*indirizzo iniziale*

```assembly
MOV ECX, pippo   // Non sono sicuro del valore iniziale
JECXZ Fine
XOR EAX, EAX
Ciclo: ADD EAX, Vettore[ECX*4-4]
       CMP EAX, 100
       LOOPNE Ciclo
Fine:
```

### Call e Return
>[!info] Descrizione
>`CALL Addr`
>Questa istruzione fa partire l'***esecuzione di un sottoprogramma*** a partire dall'indirizzo `Addr`
>Consiste nell'insieme di operazioni:
>- `PUSH EIP` $\to$ Push del ***program counter***, per avere l'istruzione da *eseguire* alla fine del *sottoprogramma*
>- `JUMP Addr` $\to$ Salto all'indirizzo del *sottoprogramma*
>Sullo [[../../Algoritmi e Strutture Dati/Strutture Dati/Stack]] viene caricata una `DWORD` equivalente a `EIP`

Il sottoprogramma termina con un'istruzione `RET`
>[!info] Descrizione
>`RET`
>Il controllo ritorna al programma *chiamante* che continua l'esecuzione all'istruzione ***successiva rispetto alla chiamata***
>Consiste nell'*operazione*:
>- `POP EIP` $\to$ Riprendo l'indirizzo **precedentemente salvato** e lo inserisco nell'*instruction* *pointer*

![[attachements/CallRetAssembly.png]]

>[!done] Vantaggi

1. Se la funzione deve essere chiamata *più volte*, non è *necessario* ***replicare il codice***
2. È possibile creare delle *funzioni* [[../../Programmazione/Funzioni/Recursive Functions|ricorsive]]
3. Utilizzo di *parametri*, sia per ***valore*** che per ***riferimento*** (*indirizzo*)
4. I ***sottoprogrammi*** possono essere raccolti in **librerie** e utilizzati in *applicazioni diverse*

>[!Danger] Nota Bene
>Non è possibile manipolare `EIP` direttamente con istruzioni del tipo
>`MOV EIP, EAX`
#### Esempio
>*Esempio di chiamata a procedura*

```assembly
JMP Main

// Sottoprogramma che trasforma in big endian la WORD in AX
Swap: MOV BL, AH   //ROR AX, 8
	  SHL AX, 8
	  MOV AL, BL
	  RET

// Programma Principale
Main: XOR ECX, ECX
	  XOR DX, DX

Ciclo: MOV AX, Vettore[ECX*2]
       CALL Swap
       ADD DX, AX
       INC ECX
       CMP ECX, 10  // Controllo condizione di uscita
       JNE Ciclo   
```


#### Disassembly di una Chiamata standard del C
>Di seguito i passaggi che l'assembler in C fa in esecuzione

1. I *parametri* sono messi sullo **stack** dal ***chiamante*** nell'ordine `RIGHT-to-LEFT`
2. La funzione *chiamata* sa dove ***andare a reperire i parametri***
3. Il valore di ***ritorno*** è sempre `EAX`
4. La funzione ***chiamante*** ripristina lo ***stato originale dello stack*** (pulizia)
	- Poiché in C è possibile avere funzioni con [[../../Programmazione/Funzioni/Funzioni in C#Funzioni variadiche|parametri variabili]]
	- La funzione non sa quanti parametri andare a "pulire"

![[attachements/FunctionCallExample.png]]

>[!question] Perché i parametri nella funzione sono presi con `+8` e `+12`??

Nello standard C sono state prese delle decisioni riguardo alla ***chiamata e esecuzione*** di funzioni:
- Il registro `EBP` è utilizzato come ***registro di appoggio*** per "*tenere il segno*" dello stack all'inizio della chiamata
	- Verrà fatto il `PUSH` del valore di `EBP` per **non perderne il contenuto**

Di conseguenza possiamo **ricostruire** lo *stato dello stack* al momento del salvataggio dei parametri:
- `PUSH EIP` implicitamente eseguito dall'istruzione `CALL` (`32 BIT`, `4 BYTE`)
- `PUSH EBP` per non perdere il ***contenuto del registro*** (`32 BIT`, `4 BYTE`)

Quindi il primo parametro sarà esattamente `8 BYTE` "*indietro*" nello stack

## Manipolazione di Stringhe
---
>Per quanto possa ingannare il titolo, non si lavora veramente con stringhe ma con ***buffer di byte***

![[attachements/AssemblyStringOperators.png]]
>[!info] Stringhe
>Le **stringhe** sono sequenze contigue di caratteri (`BYTE`), molto utilizzate.
>Risulta spesso necessario eseguire operazioni su stringhe, come:
>- Copia
>- Confronto
>- Concatenazione
>- Inversione
>- Ricerca di un carattere
>- Etc$\dots$

- Sono disponibili ***istruzioni ottimizzate*** per la manipolazione di stringhe
	- Tuttavia queste operazioni operano indipendentemente dalla rappresentazione [[../Rappresentazione dell'Informazione/Rappresentazione dei Caratteri#ASCII|ASCII]] dei caratteri e trattano gli elementi come `BYTE`
	- Sarebbe opportuno parlare di ***Manipolazione di blocchi contigui di memoria***

>[!abstract] Registri Dedicati
> Le operazioni su *stringhe* utilizzano obbligatoriamente due ***registri dedicati***
> `ESI` (***E***xtended ***S***ource ***I***ndex) e `EDI` (***E***xtended ***D***estination ***I***ndex)
> Vengono utilizzati come indirizzo dell'**elemento corrente** nella stringa *sorgente* o *destinazione*

>[!info] Prefisso `REP`
>Il prefisso `REP` o `REPcc` *anteposto* ad una delle istruzioni sopraelencate consente di eseguire un ***ciclo sulla stringa***

### Requisiti
- La lunghezza della stringa ***deve essere specificata*** dal registro `ECX`
	- Il registro viene ***automaticamente decrementato*** durante il ciclo
- Il registro `ESI` o `EDI` o *entrambi* vengono ***automaticamente incrementati o decrementati***
	- A seconda del [[Registri#Flags di Stato|flag]] `DF` in `EFLAGS`
- Il ciclo continua fino a che `ECX>0` e nel caso di `REPcc`, fino a che la condizione `cc` è vera
	- `REPcc` viene usato solo con `CMPS` e `SCAS` alle quali è concesso impostare i flag

>[!abstract] Flag `DF`

Il *direction flag* serve per dire al calcolatore se la sequenza di `BYTE` va "*percorsa*" ***indietro o in avanti*** 
- Per impostare il *direction flag* sono state introdotte due **istruzioni**

>[!info] Set Direction Flag
>`STD` imposta il flag `DF` a `1`
>Lo **scorrimento** della *stringa* avverrà all'***indietro***

>[!info] Clear Direction Flag
>`CLD` imposta il flag `DF` a `0`
>Lo **scorrimento** della *stringa* avverrà in ***avanti***

### Store String
>[!info] Descrizione
>`STOS`
>Scrive il contenuto di `AL` nell'indirizzo `[EDI]` 
#### Esempio
>*Azzera il blocco di memoria di 256 `BYTE` a partire dall'indirizzo `IndBlocco`*
```assembly
CLD                // Scorrimento in avanti
MOV ECX, 256       // Numero di elementi
LEA EDI, IndBlocco // Indirizzo di partenza in EDI
XOR AL, AL         // Valore da scrivere con STOS
REP STOS           // Scrive AL su [EDI], Decrementa ECX, incrementa EDI
```

### Move String
>[!info] Descrizione
>`MOVS`
>Copia il valore contenuto in `[ESI]` in `[EDI]`

#### Esempio
>*Copia il blocco di memoria di 256 `BYTE` a partire dall'indirizzo `IndBlocco` su il blocco il cui indirizzo di partenza è `IndBlocco2`*

```assembly
CLD                 // Scorrimento in avanti
MOV ECX, 256        // Numero di elementi
LEA ESI, IndBlocco  // Indirizzo di partenza stringa 1
LEA ESI, IndBlocco2 // Indirizzo di partenza stringa 2
REP MOVS            // Scrive [ESI] su [EDI] 
                    // Decrementa ECX incrementa i due registri
	                // Ripete fino a che ECX>0 e il flag ZF è 1
```

### String Compare
>[!info] Descrizione
>`CMPS`
>Confronta il valore contenuto nell'indirizzo `[ESI]` con il valore contenuto in `[EDI]`
#### Esempio
>*Confrontare 2 blocchi di memoria lunghi 256 `BYTE`, `IndBlocco` e `IndBlocco2` sono gli indirizzi di partenza*
```assembly
CLD                 // Scorrimento in avanti
MOV ECX, 256        // Numero di elementi
LEA ESI, IndBlocco  // Indirizzo di partenza stringa 1
LEA EDI, IndBlocco2 // Indirizzo di partenza stringa 2
REPE CMPS           // Confronta [ESI] con [EDI] e setta il flag di 
                    // conseguenza, decrementa ECX incrementa i due registri
	                // Ripete fino a che ECX>0 e il flag ZF è 1
```

