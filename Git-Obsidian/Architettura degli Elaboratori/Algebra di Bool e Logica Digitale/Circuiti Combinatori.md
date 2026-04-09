>*Con le porte `NAND` è possibile realizzare qualsivoglia circuito*
>*Sarebbe logico creare [[Circuiti Digitali#Circuiti Integrati|circuiti integrati]] con una grande quantità di porte `NAND` indipendenti*
>[[../../Definizioni/Definizioni_Architettura#Economy|Problema]]

Allo scopo di ***aumentare il rapporto porte/piedini***
- I chip vengono realizzati *implementando internamente* circuiti più complessi collegando in uscita solo i ***piedini "rilevanti"***

## Multiplexer
---
>[!info] Descrizione
>Un ***multiplexer*** è un circuito con $2^n$ ***input di dati*** e $n$ ***input di controllo***
>- Gli *input di controllo* selezionano **quale** fra i $2^n$ *input dati* deve essere ***portato in uscita***

![[attachements/Multiplexer.png]]
#### Esempio
![[attachements/Multiplexer Circuit.png]]
*Multiplexer con $8$ input*

## Demultiplexer
---
>[!info] Descrizione
>Si tratta del circuito inverso del ***multiplexer***
>In questo caso $1$ ***input dati*** viene "*smistato*" su una delle $2^n$ ***linee di output***
>- Sempre in base alla selezione degli ***input di controllo***

![[attachements/Demultiplexer.png]]


> Un circuito costituito da un ***multiplexer*** $+$ una ***linea dati*** $+$ un ***demultiplexer***
> può essere usato per mettere in ***comunicazione più utenti*** su una stessa linea dati

## Decoder
---
>[!info] Descrizione
>Un ***decoder*** è un circuito che riceve in ***input*** $n$ segnali che vengono trattati come un numero binario di $n$ cifre
>Il *decoder* ha $2^n$ ***linee di output*** di cui ***una sola*** viene impostata a $1$
>- Sarà la linea **selezionata** dal *numero binario in input*

![[attachements/Decoder Circuit.png]]

>[!done] Ovviamente esiste anche il circuito inverso, chiamato *encoder*

## Comparatore
---
>[!info] Descrizione
>Un ***comparatore*** confronta due parole di input e produce un output che indica l'***uguaglianza/inuguaglianza*** degli input
>Il circuito può essere realizzato con porte `XOR`

![[Logica Digitale#XOR]]

#### Esempio
>*Un comparatore di due parole $A$ e $B$ di `4 BIT` ciascuna*

Ogni porta `XOR` confronta una coppia di `BIT`
- Se almeno una delle coppie è diversa uno degli input della porta `NOR` vale $1$
	- L'output del comparatore vale $0$

![[attachements/Comparator.png]]

## Circuiti Aritmetici
---
>[!info] Definizione
>I ***circuiti aritmetici*** sono circuiti specializzati nel calcolo di ***semplici operazioni aritmetiche*** dei loro input

### Shifter
>[!tldr] Descrizione
>Uno ***shifter*** è un circuito con $n$ **input** ($D_{0},\dots,D_{n-1}$) e $n$ **output** ($S_{0},\dots,S_{n-1}$)
>I `BIT` in *output* sono esattamente la copia di quelli in input traslati tutti di una posizione a destra o a sinistra
>- La direzione è impostata da un `BIT` di controllo $C$

![[attachements/Shifter Circuit.png]]

>*Shifter a `8-BIT`*

### Adder
>[!info] Definizione
>La ***somma*** tra numeri binari è un'***operazione fondamentale*** per qualsiasi calcolatore
>Per la realizzazione di un ***sommatore*** a $n$ `BIT`, vengono utilizzati $n$ "*mattoncini*" elementari denominati ***full-adder*** a $1$ `BIT`
>- Realizzati a loro volta realizzati a partire da ***half-adder*** a $1$ `BIT`

#### Half-Adder
![[attachements/Half Adder.png]]

- La **somma** (*sum*) vale $1$ solo se i 2 `BIT` di input sono diversi (`XOR`, $\oplus$)
- Il **riporto** (*carry*) vale $1$ solo se entrambi gli input sono $1$ (`AND`)

>[!fail] Non Funziona Sempre

L'*half-adder* a $1$ `BIT` funziona solo per i `BIT` ***meno significativi*** di una parola
- Non funziona per i `BIT` "*centrali*" per i quali ci può essere un ***riporto pendente*** in *input*

Per fare una somma con il riporto è necessario utilizzare un ***full-adder*** a $1$ `BIT`

#### Full-Adder
![[attachements/Full Adder.png]]

- La **somma** (*sum*) vale $1$ quando un ***numero dispari di input***, compreso il riporto in ingresso vale $1$
- Il **riporto in uscita** (*carry out*) vale $1$ se il ***numero di input*** a $1$, compreso il riporto in ingresso è maggiore o uguale a $2$

>[!tldr] Full-Adder a $n$ `BIT`
>La realizzazione di un ***full-adder*** a $n$ `BIT` consiste semplicemente nell'utilizzo di $n$ ***full-adder*** a $1$ `BIT` in *parallelo*
>I *segnali di riporto* devono essere opportunamente *collegati fra di loro*

##### Equazione Booleana
>*Il circuito può essere derivato dalla tabella di verità a seguito di alcune semplificazioni*

>[!abstract] *Sum*

$$
\begin{array}
\ \text{Sum}=\overline{A}\ \overline{B}C+\overline{A}B\overline{C}+A\overline{B}\ \overline{C} + ABC \\
\text{Sum} = \overline{C}(\overline{A}B+A\overline{B})+C(AB+\overline{A}\ \overline{B}) \\
\text{Sum}=\overline{C}(\overline{A}B+A\overline{B})+C\left( \overline{\overline{A}B+A\overline{B}} \right) \\
\text{Sum} =C\oplus (A\oplus B)
\end{array}
$$

>[!abstract] *Carry Out*

$$
\begin{array}
\ \text{Carry Out}=\overline{A}BC+A\overline{B}C+AB\overline{C}+ABC \\
\text{Carry Out}=C(\overline{A}B+A\overline{B})+AB(C+\overline{C}) \\
\text{Carry Out}=C(A\oplus B)+AB
\end{array}
$$


### Moltiplicazione Binaria
>[!info] Operazioni
>Per la moltiplicazione sono necessarie semplici operazioni di ***somma e shift***
>In teoria non occorre un circuito specifico e la moltiplicazione può essere implementata con un microprogramma usando semplice `ALU`
>Moltiplicatori ***hardware ottimizzati*** richiedono un minor numero di somme che possono essere parallelizzate