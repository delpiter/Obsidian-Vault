## Il Calcolatore
---
>[!info] Hardware
L'**hardware** è l’insieme dei dispositivi che compongono il calcolatore. Si compone di oggetti tangibili: circuiti integrati, memorie, stampanti, ecc.

>[!info] Software
Il **software** è l’insieme delle istruzioni e delle informazioni necessarie per risolvere i problemi a cui il sistema è preposto. Un insieme di istruzioni, codificate in termini comprensibili a un calcolatore, per risolvere un problema

- Il software **richiede** un apposito hardware per essere eseguito, **viceversa** l’hardware è pressoché inutile se non si dispone di un apposito software che ne sfrutti le potenzialità

- Programmare un calcolatore significa scrivere la sequenza di istruzioni ([[../Algoritmi e Strutture Dati/Problemi e Algoritmi#Algoritmo|Algoritmo]]) necessaria a risolvere un problema. 
>[!info] Firmware
Il **firmware** è un software integrato in un componente elettronico in grado di **avviare** il componente stesso e di farlo **interagire** con altri componenti.

## Traduzione di Programmi
---
### Compilazione
>[!tip] Definizione
>Il codice viene "inviato" ad un traduttore (*Compilatore/Assemblatore*) che avrà il compito di tradurre il programma in linguaggio macchina-`i` e produce un nuovo programma in un linguaggio macchina più basso
>>[!done] Il compilatore:
>>1. Traduce
>>2. Salva (generalmente un file in linguaggio oggetto: `.obj` o `.o`)
>>3. Codice eseguibile in un secondo momento
>
>>[!warning] Attenzione
>>Il traduttore è detto ***compilatore*** quando il linguaggio sorgente è un ***linguaggio di alto livello***
>>È detto ***assemblatore*** quando il linguaggio sorgente è ***linguaggio assembly***
>>>[!example] Differenza principale
>>>Nel primo caso il rapporto istruzione sorgente $\iff$ istruzione macchina è $1$ a molti
>>>Nel secondo caso è $1$ a $1$

### Interpretazione
>[!tip] Definizione
>Il traduttore (o *interprete*) legge il programma in linguaggio macchina-`i`, il programma verrà eseguito direttamente.
>Il compito dell'**interprete** sarà quello di compilare (o "tradurre") riga per riga durante l'esecuzione (**run time**)
>>[!done] I'interprete
>> 1. Traduce man mano che esegue


### Linker
>[!tip] Definizione
>Il linker ha il computo di collegare i moduli e risolvere i riferimenti inter-modulo durante la **compilazione**
>Serve per ottenere una unica sequenza di byte, un unico file eseguibile
>- Su windows genera un unico file `.exe`

### Loader

> [!tip] Definizione
> Carica il programma in memoria e trasforma i riferimenti tra le istruzioni  in indirizzi di memoria
> - "Genera" il programma in esecuzione

## Unnità di Misura e Prefissi
---
| Prefissi     | Unità | Prefissi Binari|
| ------------ | ----- |-----|
| Yotta        |     $10^{24}$  |Yotta `byte`$\to 2^{80}=1.2089258e+24$|
| Zetta        |     $10^{21}$  |Zetta `byte`$\to 2^{70}=1.1805916e+21$|
| Exa          |       $10^{18}$|Exa `byte`$\to 2^{60}=1.1529215e+18$|
| Peta         |       $10^{15}$|Peta `byte`$\to 2^{50}=1.258999e+15$|
| Tera         |       $10^{12}$|Tera `byte`$\to 2^{40}=1.0995116+12$|
| Giga         |       $10^{9}$|Giga `byte`$\to 2^{30}=1.073.741.824$|
| Mega         |       $10^{6}$|Mega `byte`$\to 2^{20}=1.048.576$|
| Kilo         |       $10^{3}$|Yottta `byte`$\to 2^{10}=1.024$|
| Milli        | $10^{-3}$      |`/`|
| Micro        |       $10^{-6}$|`/`|
| Nano| $10^{-9}$|`/`|
|Pico |       $10^{-12}$|`/`|
| Femto        |       $10^{-15}$|`/`|
| Atto         |       $10^{-18}$|`/`|
| Zepto        |       $10^{-21}$|`/`|
| Yocto        |       $10^{-24}$|`/`|


> [!warning] Attenzione
> I prefissi del sistema binario non corrispondono ai prefissi del sistema decimale
> - Secondo lo standard `IEEE 1541` ai prefissi binari andrebbe aggiunta una `i` per evitare confusione
>>[!example] Esempio
>>`1024 Bytes` andrebbero indicati come `1 KiB`

## Parity Bit
---
>[!info] Definizione
>Un **`BIT` di parità** o **check `BIT`** è un bit aggiunto ad una stringa di codice binario.
>Il `BIT` di parità sono generalmente applicati ai protocolli di comunicazione più "*piccoli*", tipicamente a protocolli con 8`BIT` 
>- Possono comunque essere applicati a messaggi interi
>>[!done] Funzionamento
>>Il `BIT` di parità assicura che il numero totale di `BIT` impostati a `1` sia pari o dispari
>>- Nel numero di `BIT` a `1` viene contato anche il `BIT` di parità
>>- Di conseguenza il `BIT` di parità viene impostato a `1` solo quando il numero di `BIT` impostati a `1` (escluso il `BIT` di parità) è dispari

La [[../Architettura degli Elaboratori/Architettura del Calcolatore/Correzione di Errori#Distanza di Hamming|distanza di Hamming]] di questa tecnica è $2$ quindi ***non permetterà di correggere nessun errore*** e permetterà di ***identificare errori*** di $1$ `BIT`

> Dati $k$ `bit` di informazione $b_{0},b_{1},b_{2},\dots,b_{k-1}$
- $b_{k}=b_{0}\oplus b_{1}\oplus\dots\oplus b_{k-1}$: parità ***pari***
- $b_{k}=\text{NOT}[b_{0}\oplus b_{1}\oplus\dots\oplus b_{k-1}]$: parità ***dispari***
## Code Point
---
>[!info] Definizione
>I ***code points*** sono comunemente utilizzati nella codifica di caratteri.
>Un ***code point*** è un valore numerico che viene mappato ad uno specifico carattere.
>Nella codifica di caratteri un *code point* rappresenta un ***grafema*** (segno elementare e non ulteriormente divisibile)
>- Tipicamente una lettera, una cifra o un simbolo di punteggiatura

>[!warning] Nota Bene!

I termini "*code point*" e "*carattere*" non sono sinonimi
- Alcuni "*caratteri*" sono ottenibili combinando più codepoints

## Macchine Turing Complete
---
>[!info] Turing Completeness
>"*Turing Complete*" è un termine utilizzato in informatica per descrivere un sistema o un linguaggio di programmazione che può eseguire qualsiasi calcolo che la macchina di Turing poteva fare

## Ordinamento dei `BYTE`
---
>Quando una word contiene più di un `BYTE` si pone il problema di come enumerare i `BYTE` al suo interno, come rappresentare i numeri binari che sono memorizzati su più `BYTE`

>[!info] Big Endian
>Il `BYTE` più significativo del numero è memorizzato nel `BYTE`della word con offset minore

>[!info] Little Endian
>Il `BYTE` meno significativo del numero è memorizzato nel `BYTE` della parola con offset minore
>Questa rappresentazione è utilizzata dai processori *Intel* e *Alpha **RISC***
>Nell'*indirizzo più basso* di memoria inserisco la parte *meno significativa* della word
>- Parte di numero più "*bassa*"$\to$ Indirizzo di memoria più "*basso*"
>- Parte di numero più "alta"$\to$ Indirizzo di memoria più "*alto*"


## Stack
---
>[!info] Definizione
>Lo [[../Programmazione/Introduzione Programmazione/Spazio di Indirizzamento Virtuale#Stack|stack]] è una parte della memoria utilizzata in genere per 
>- Valutazione di *espressioni aritmetiche*
>- Memorizzazione di *variabili locali*
>- Chiamata di *sottoprogrammi*


## Raster Graphics
---
>[!info] Definizione
>Una grafica "***Raster***" è una collezione di piccoli ***pixel*** uniformi, disposti in un ***array bidimensionale***
>Ogni `PIXEL` contiene uno o più `BIT` di informazione in base al ***livello di dettaglio*** dell'immagine

## Economy
---
![[attachements/Economy.png]]
*"Might have a negative effect"*
>*Structured Computer Organization, Andrew S. Tanenbaum, Todd Austin*

## BIOS
---
>[!info] Definizione
>***B***asic ***I***nput ***O***utput ***S***ystem
>Il `BIOS` è il ***programma*** che il microprocessore di un calcolatore utilizza per l'*inizializzazione del sistema* poco dopo la sua accensione

## Tri-State Buffer
---
>[!info] Definizione
>I ***buffer tri-state*** agiscono come *interruttori elettronici* capaci di ***collegare/scollegare elettricamente*** due parti di un circuito

![[attachements/Tri-State-Buffer.png]]
>$a)\to$ *buffer tri-state*
>$b)\to$ *effetto di un* $a)$ *quando il controllo ha uno stato alto*
>$c)\to$ *effetto di un* $a)$ *quando il controllo ha uno stato basso*

## Chipset
---
>[!info] Definizione
>***Chipset*** (dall'inglese "*Insieme di Chip*") è un chip unico contenente diversi chip per il ***controllo di periferiche***
>Permette alla `CPU` di interfacciarsi con la ***maggior parte delle periferiche***

## Benchmarck
---
>[!info] Definizione
>Un ***benchmark*** è un insieme di ***programmi di prova*** rappresentativi di una particolare classe di applicazioni

## Cluster
---
>[!info] Definizione
>Tecnica che abbina core più potenti a core meno potenti
>- Utilizzata nelle ultime `CPU` da parte di Intel (*Performance core* - *Efficiency Core*)

## Scalabilità
---
>[!info] Definizione
>Una architettura è detta ***scalabile*** se le sue prestazioni aumentano ***aumentando il numero di core***