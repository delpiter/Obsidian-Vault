## Unità Floating Point
---
>[!info] FPU
>La ***Floating Point Unit***, incorporata all'interno del chip della `CPU`, utilizza una serie di *registri aggiuntivi* rispetto a quelli fino ad ora introdotti


![[attachements/FloatingPointUnit.png]]

Gli 8 registri `R0,...,R7`, benchè accessibili senza nessuna restrizione sull'ordine
- ***Vengono trattati*** come uno [[../../Algoritmi e Strutture Dati/Strutture Dati/Stack]]
- Operazioni di ***caricamento e prelevamento*** aggiungono o rimuovono valori rispetto alla *cima dello stack*
	- La cima è memorizzata in un registro, `Status Register`
 
`ST(0)` si riferisce al registro $0$ a partire dalla cima dello stack, non necessariamente `R0`
- `ST(1),...,ST(7)` sono i successivi registri sullo stack

### Istruzioni
>[!info] Istruzioni disponibili
>L'unità floating point fornisce **molte istruzioni** che possono essere raggruppate sulla base delle loro funzioni:
>- **Trasferimento** di valori
>	- *Caricare*, *Salvare*, *Spostare* valori nei registri
>- **Aritmetiche** di base:
>	- *Somma*, *Sottrazione*, *Moltiplicazione*, *Divisione*,$\dots$
>- **Confronto**:
>	- Non è possibile confrontare con la tradizionale [[Istruzioni IA-32#Compare|CMP]] valori *floating point*
>- **Funzioni Trascendenti**:
>	- *Seno*, *Coseno*, *Logaritmo*, *Esponenziale*
>- **Caricamento di Costanti note**:
>	- Carica costanti come $0,1,\pi,e,\dots$ nei registri ***senza dover caricare il valore dalla memoria***
>- **Controllo dell'**`FPU`:
>	- *Inizializzazione*, *sincronizzazione*, $\dots$

>[!warning] Nota Bene

I dati in virgola mobile quando vengono caricati nei registri
- Indipendentemente dal fatto che siano in *singola precisione* ($32$ `BIT`), *doppia precisione* ($64$ `BIT`) o *doppia precisione estesa* ($80$ `BIT`)
- Vengono convertiti in *doppia precisione estesa* e memorizzati nei **registri** a $80$ `BIT`

#### Esempio
>*Calcolo della semplice espressione* $(a+b)\times(c-d)$

```assembly
FINIT           // Inizializza l'FPU
FLD   a         // Carica a in ST(0) che punta a R0
FADD  b         // R0 = R0 + b
FLD   c         // Carica a in ST(0) che punta a R1
FADD  d         // R1 = R1 - d
FMUL            // R0 = R0 * R1
```


## Istruzioni MMX
---
>[!info] Introduzione
>`MMX` Nasce a partire dal ***Pentium Pro*** e viene incorporato su tutti i processori successivi
>Si tratta di un meccanismo che consente di utilizzare il processore come macchina `SIMD`
>- ***S***ingle ***I***nstruction ***M***ultiple ***D***ata
>
>Permette di eseguire in ***parallelo*** la **stessa operazione** su ***più dati***

>[!warning] Nota Bene

`MMX` Opera solo su ***aritmetica intera***
- Utilizza $8$ registri a $64$ `BIT` che ***condivide*** con la `FPU`
	- Ed è per questo che non si possono utilizzare contemporaneamente istruzioni ***floating point*** e `MMX`

### Nuovi tipi di Dato
Le istruzioni `MMX` introducono 3 nuovi tipi di dati
![[attachements/MMXdataType.png]]

Tutti e tre memorizzati in registri da $64$ `BIT`
- ***Packed Byte Integer***
	- Il registro viene spezzato in 8 `BYTE`
- ***Packed Word Integer***
	- Il registro viene spezzato in 4 `WORD`
- ***Packed Doubleword Integer***
	- Il registro viene spezzato in 2 `DWORD`

### Gestione Overflow
>*Supponiamo di volere sommare in parallelo 4 `WORD` signed con un'unica istruzione*

>[!question] Come gestire il problema dell'overflow?

Le operazioni `MMX` introducono tre *modalità esplicite* che la maggior parte delle istruzioni supporta:

>[!abstract] Wraparound
>In caso di *overflow* si perdono i `BIT` più *significativi* e il registro conserva i `BIT` meno significativi

>*La somma di $2$ ad un byte senza segno con valore $255$ da come risultato $1$*

>[!abstract] Signed Saturation
>In caso di *overflow* verso l'**alto** il valore viene **rimpiazzato** con l'***intero positivo maggiore*** esprimibile con la lunghezza della parola considerata
>Analogo con l'*overflow* verso il **basso**

>*Sommare $10$ a $+120$ prodice il valore $127$, mentre sottrarre $50$ a $-120$ produce $-128$*

>[!abstract] Unsigned Saturation
>In caso di *overflow* verso l'**alto** il valore viene **rimpiazzato** con l'***intero positivo maggiore*** esprimibile con la lunghezza della parola considerata
>In caso di *overflow* verso il **basso** il valore viene sostituito con $0$

>*Sommare $40$ a $+220$ produce il risultato $255$, mentre sottrarre $50$ a $40$ produce $0$*


### Prodotto Scalare
>[!info] Descrizione
>Operazione particolare, frequentemente usata in applicazioni di calcolo numerico, matematico, grafica, analisi del suono e di immagini.
>È prevista una istruzione speciale `PMADDWD`
>Questa istruzione esegue il **prodotto scalare**
>Il *prodotto scalare* di due vettori $v_{1},v_{2}$ di lunghezza $4$ è definito come:
>$$\text{DotProd}=v_{1}[1]\times v_{2}[1]+v_{1}[2]\times v_{2}[2]+v_{1}[3]\times v_{2}[3]+v_{1}[4]\times v_{2}[4]$$

L'istruzione `MPADDWD` esegue
1. Moltiplicazione `WORD` a `WORD` delle due ***Packed Word*** in input
2. Memorizza i risultati intermedi in un registro a $128$ `BIT` per evitare *overflow*
3. Somma a due a due le coppie contigue per ottenere come risultato un ***Packet Dword***

L'ultima somma ***non viene eseguita***, spetta al *programmatore* farla **manualmente**

```c
// dichiarazione in C
unsigned int short V1[]={2,4,8,16}
unsigned int short V2[]={2,4,8,16}
```

```assembly
MOVQ    MM0, V1   // Carica packet signed word V1 in MM0
MOVQ    MM1, V2   // Carica packet signed word V2 in MM1

PMADDWD MM0,MM1   // Moltiplica e accumula
MOVD    EAX, MM0  // Carica in EAX la dword bassa
PSRLQ   MM0, 32   // Sposta la Dword alta in (0,...,31)

MOVD    EBX, MM0  // Carica in EBX la dword bassa

ADD     EAX, EBX  // EAX = EAX + EBX -> Risultato

EMMS              // Pulizia finale registri MMX
```

## Evoluzioni SIMD
---
>A partire dal **Pentium** $III$ è stato introdotto `SSE`

- Aggiunge $8$ ***nuovi registri a $128$*** `BIT` chiamati `XMM` non condivisi con i ***floating point***

### Nuove Funzionalità
>[!info] SSE
>- Sui nuovi registri è possibile eseguire operazioni **SIMD** su ***floating point in singola precisione***
>- `SSE` estende le funzionalità `MMX` con nuove operazioni come ***media, max e min***
>- `SSE` include nuove operazioni per il controllo e ottimizzazione di **prefetching e caching** 

>[!info] SSE2
>- Possibile eseguire operazioni **SIMD** su ***floating point a doppia precisione***
>- Estende nuovamente `MMX` rendendo possibile operare su ***packet interi*** a $128$ `BIT`
>- Aggiunge **nuove operazioni** `SIMD`
>- Maggiore controllo della ***cache*** e dell'ordine di esecuzione delle istruzioni

Negli anni successivi sono stati introdotti `SSE3`, `SSE4` e `AVX` 
(***A***dvanced ***V***ector ***E***xtentions)
- Aggiungono ***numerose nuove istruzioni*** rispetto alle versioni precedenti
- Principalmente *istruzioni floating point* per ***accelerazione video e grafica***
- Introdotti registri a $256$ `BIT` (`YMMn`) e successivamente a $512$ `BIT` (`ZMMn`)

### SIMD per ARM
>[!abstract] ARM Neon
>`NEON` è l'estensione `SIMD` per le architetture `ARM`. 
## Intrinsics
---
>[!info] Definizione
>Gli ***intrinsics*** sono funzioni che rendono disponibili alcune istruzioni **SIMD** che *non sono supportate* dai ***compilatori*** o *non accessibili* tramite ***assembly in line***.

Sono funzioni in standard `{c icon} C` mappate ***automaticamente in istruzioni assemblu***.