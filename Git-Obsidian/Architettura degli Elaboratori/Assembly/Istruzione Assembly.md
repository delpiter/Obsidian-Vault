## L'Istruzione [[Il Livello ISA|assembly]]
---
> Consideriamo l'istruzione `MOV`, utilizzata per copiare un valore da una *sorgente* a una *destinazione*

```assembly
MOV DST,SRC
```

>[!info] Operandi
>`DST` e `SRC` vengono chiamati **operandi** dell'istruzione
>Esistono istruzioni *senza* operandi, istruzioni con *un solo* operando e istruzioni a *due o più* operandi
>Un operando può specificare ***elementi diversi***:
>- Un registro
>- Una costante
>- Un indirizzo di memoria *semplice*
>- Un indirizzo di memoria con *scostamento*

## Modi di Indirizzamento
---
>[!info]
>Gran parte delle istruzioni [[Il Livello ISA|ISA]] consentono di *caricare/salvare* i dati attraverso i registri e la memoria
>Le modalità di reperimento dei dati sono definite dai ***modi di indirizzamento***


### Indirizzamento Immediato
>[!done] ‎ 
>Il valore è *codificato direttamente nell'istruzione*
>La lunghezza del valore (1, 2, 4 `BYTE`) dipende dal tipo di *operazione e dai registri coinvolti*

```assembly
MOV AL,10 
MOV AH,10h 
MOV AH,10100101b 
MOV AX,0d3c5h      // 0 davanti al valore esadecimale per il compilatore* 
MOV EAX,104ed3c5h

MOV AX, 104ed3c5h // Errore -> Registro a 16 BIT valore a 32
```
* * Visual Studio non accetta valori che iniziano con le *lettere*

>[!tip] La costante $0$

Per caricare la costante $0$ (azzeramento del registro) invece di scrivere
```assembly
MOV EAX, 0
```
È preferibile
```assembly
XOR EAX, EAX
```
### Indirizzamento dei Registri
>[!done] ‎ 
>L'operando contiene l'indicazione di uno *specifico registro* della `CPU`

```assembly
MOV AL, AH
MOV CX, AX
MOV EAX, EBX

MOV AL, CX    //Errore dimensioni di registri diverse
```

### Indirizzamento in Memoria
>[!done] ‎ 
>L'operando specifica un *indirizzo di memoria* che viene indicato come segue:
>`Indirizo = Segmento : Offset`

#### Segmento
>Il *segmento* può essere specificato con uno dei registri di segmento (`CS`, `DS`, `ES`, `SS`, `FS`, `GS`)

- Se il *registro di segmento* non è indicato esplicitamente, viene implicitamente utilizzato `DS`

#### Offset
>Chiamato anche *Effective Address* è calcolato al momento dell'esecuzione dell'istruzione utilizzando uno o più componenti della formula seguente:

$$
\text{Offset}= \text{ Base } +(\text{Index}\times\text{Scale})+\text{ Displacement}
$$
Dove:
- ***Displacement***
	- È una *costante* e può essere omessa
- ***Base***
	- Se presente è un *registro*
- ***Index***
	- Se presente è un *registro*
- ***Scale***
	- È una *costante* (2, 4 o 8) moltiplicata per ***Index***
	- Può essere omessa ($\text{Scale = 1}$)

![[attachements/MemoryOffsetASM.png]]
#### Esempi
Nell'istruzione seguente, l'**offset** utilizza solo  la componente *displacement*
- Questo indirizzamento viene anche chiamato ***assoluto o diretto***

```assembly
MOV AL, DS:[104532a0h] // carica in AL il byte all'indirizzo DS:104532a0
```

Nell'istruzione seguente, l'**offset** utilizza solo la componente *base*
- Questo indirizzamento viene anche chiamato ***indiretto***
```assembly
MOV EAX, [ECX] //Carica in EAX la doubleword all'indirizzo contenuto nel
               //registro ECX, DS è implicito 
```

Nell'esempio seguente l'indirizzo di memoria è determinato a partire da un ***valore assoluto***
- Come l'*indirizzo* *iniziale di un vettore*
- A cui viene sommato il contenuto di un registro che è usato come *indice*

```assembly
MOV EAX, [1000h][ECX] //Copia in EAX la double word dall'indirizzo di memoria
					  //DS:1000h + <contenuto ECX>
```

Se l'indirizzo `DS:1000h` corrisponde al nome *simbolico* `Vettore`
- L'assemblatore consente di scrivere la seguente **istruzione** più **leggibile**

```assembly
MOV EAX, Vettore[ECX] //Copia in EAX la double word dall'indirizzo di memoria
					  //DS:Vettore + <contenuto ECX>
```

- In questo modo, è possibile accedere a tutti gli elementi di un vettore di `BYTE`

```assembly
XOR ECX, ECX
cycle: MOV AL, Vettore[ECX]
	  ...
	  INC ECX
	  JMP cycle	
```

La combinazione di ***Index*** e ***Scale*** consente di accedere efficientemente a vettori con elementi di `2/4/8 BYTE`
- Nell'esempio seguente si accede ad un vettore di **doubleword**

```assembly
XOR ECX, ECX
cycle: MOV EAX, Vettore[ECX*4]
	  ...
	  INC ECX
	  JMP cycle	
```

La combinazione di $\text{Displacement}+\text{Base}+\text{Index}\times\text{Scale}$ può anche essere utilizzato per accedere agli elementi di una ***matrice***
- Supponiamo che una matrice di $50\times100$ `doubleword` ($50$ righe e $100$ colonne) sia dichiarata come variabile `matrix`
- Si voglia accedere all'elemento che si trova alla ***riga*** il cui indice è in `EDX` e alla colonna in `ECX`
- La ***base*** `EBX` contiene il numero di `BYTE` da "*saltare*" per posizionarsi all'inizio della riga desiderata:
	- Dimensione di una riga: $100 \text{ elementi} \times4 \text{ byte}=400\text{byte}$

```assembly
MOV EDX, ... //EDX contiene l'indice della riga 0
MOV ECX, ... //ECX contiene l'indice della colonna 0

IMUL EBX, EDX, 400 //EBX = EDX * 400 -> byte da "saltare"

LEA ESI, matrix[EBX]
MOV EAX, [ESI][ECX*4] //Copia in EAX il valore dell'elemento  
                            //alla riga EDX e colonna ECX
```

```assembly
MOV EAX, DS:[10345467h]
MOV EAX, [ECX]
MOV EAX, [ECX+2]
```



Grazie al programma assemblatore, possiamo utilizzare *nomi simbolici per* ***variabili*** e ***indirizzi***
- Se l'indirizzo `10345467h` precedente fosse l'indirizzo della variabile `pippo`
	- Potremmo caricare il valore di `pippo` in `EAX` scrivendo:

```assembly
MOV EAX, pippo
```

## Modificatori di Tipo
---
>[!question] Nel caso in cui l'operando `SRC` indichi un indirizzo di memoria, come specificare la dimensione di bit dell'operando?


> Il programma assemblatore accetta davanti agli indirizzi i seguenti ***modificatori di tipo***

- `BYTE PTR`
- `WORD PTR`
- `DWORD PTR`

Che indicano rispettivamente che l'indirizzo fornito specifica un operando
- `BYTE` (8 `BIT`)
- `WORD` (16 `BIT`)
- `DOUBLEWORD` (32 `BIT`)

### Esempio
>Considerando `short pippo = 0x0102;` la dichiarazione in linguaggio `C`

```assembly
MOV EAX, 2h
MUL BYTE PTR pippo  //AX = 4h (pippo è memoria little endian)
```

```assembly
MOV EAX, 2h
MUL WORD PTR pippo // DX:AX = (0;204h)
```