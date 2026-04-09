>*La memoria è organizzata in **Chip**, ciascuno dei quali è caratterizzato da:*

## Caratteristiche del Chip
---
>[!info] Lunghezza di Parola
>La ***lunghezza di parola*** specifica la dimensione in `BIT` di ogni unità di informazione indirizzabile (***leggibile*** o ***scrivibile***) singolarmente
>Le tipiche lunghezze sono:
>- $1$, $4$, $8$, $16$ `BIT`

>[!info] Numero di Parole
>Il ***numero di parole*** indica quante parole sono contenute all'interno del *Chip*

>[!done] La ***capacità*** in `BIT` di un *Chip* si ottiene: $\text{ numero di parole}\times\text{lunghezza di parola}$

Un *chip di memoria*, indipendentemente dall'organizzazione interna, è dotato di una serie di piedini $I/O$ necessarie per il collegamento alla [[../Architettura del Calcolatore/La CPU|CPU]] e al `BUS`

>[!abstract] Lunghezza Parola $N$

Se la lunghezza della parola è $N$, saranno presenti $N$ ***pin*** attraverso i quali i dati vengono *letti e scritti*

>[!abstract] Indirizzi

Per selezionare quale parola leggere o scrivere, sono necessari $log_{2}(N)$ ***pin***, che specificano l'*indirizzo*

### Alcuni Chip di Memoria
>*La seguente figura mostra una possibile organizzazione di un chip di `RAM` da $4Mbit$*

![[attachements/Memory-Chip.png]]
- *Lunghezza di Parola* $\to 8$ `BIT` 
- *Numero di Parole* $\to 512\ K$

>[!abstract] Numero di `BIT` necessari per l'indirizzamento

$$
log_{2}(512\times 1024) = 19 \ \text{bit}
$$
### Unione di Chip
>[!question] Come realizzare una memoria $512K \times 32$ utilizzando Chip $512K\times 8$?

È sufficiente utilizzare ***4 chip identici***
- Ciascuna parola di memoria è *suddivisa* in $4$ parti e ogni parte è *memorizzata* in un ***diverso chip allo stesso indirizzo***

- Le $19$ linee di indirizzi sono ***comuni a tutti i chip***
- I $3$ input `CS`, `WE`, `OE` sono ***comuni a tutti i chip***
- Relativamente al `BUS` dei dati, le $4$ parole ($8$ `BIT` ciascuna) dei singoli chip vengono affiancate a sostituire la parola a $32$ `BIT` desiderata

![[attachements/32Bit-MemoryChip.png]]


>[!question] Come realizzare una memoria $512K \times 8$ utilizzando Chip $512K\times 8$?

Anche in questo caso possiamo utilizzare $4$ *chip identici*, ma questa volta i $4$ chip ***contengono parole complete***
- Dobbiamo fare in modo che a seconda dell'indirizzo richiesto, si ***attivi il chip che contiene la parola corrispondente***


- I `BUS` *dati* possono essere collegati insieme
	- Uno solo dei chip è attivo per volta è attivo, non ci sono conflitti
- Gli input `WE` e `OE` sono *condivisi* anche essi con ***tutti i chip***

Per potere indirizzare $2M$ *parole* occorre estendere il `BUS` indirizzi da $19$ a $21$ *linee*
- Le linee da $A_{0},\dots,A_{18}$ sono ancora collegati in parallelo a tutti chip per determinare quale parola *selezionare* da ***ciascun chip***
- I due `BIT` più significativi degli *indirizzi* $A_{19},A_{20}$ sono invece utilizzati per ***selezionare*** attraverso un decoder ***quale chip attivare*** (collegamento a `CS`)

![[attachements/8Bit-MemoryChip.png]]

## DIMM-DDR
---
>*L'organizzazione delle [[../Architettura del Calcolatore/Organizzazione della Memoria#Assemblaggio|DIMM]] moderne con chip di memoria [[../Architettura del Calcolatore/RAM#DDR|DDR]] prevede un `BUS` dati a $64$ `BIT`.*

Su ciascuna `DIMM` sono generalmente montati $8$ chip che operano in parallelo
- Ciascun *chip* fornisce $8$ `BIT`
- Un *nono chip* può essere utilizzato per il ***controllo dell'errore*** ([[../Architettura del Calcolatore/Organizzazione della Memoria#Assemblaggio|ECC-DIMM]])

Ogni chip, è collegato con il controller della memoria, che si trova tipicamente all'interno della `CPU`

![[attachements/DramMemoryStick.png]]
