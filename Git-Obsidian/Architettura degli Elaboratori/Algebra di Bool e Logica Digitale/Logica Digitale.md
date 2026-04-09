>*I calcolatori odierni sono costituiti da* ***circuiti digitali***

Un sistema digitale opera con segnali "***discretizzati***" 
- Nel caso dei *circuiti elettrici digitali* un segnale può assumere ***2 stati***

![[attachements/LogicStates.png]]

>[!info] Porte Logiche
>I *mattoncini* di base dei circuiti sono le ***porte logiche***
>- Semplici circuiti in grado di calcolare le principali operazioni dell'[[Algebra di Bool]]
## Transistor
---
>[!abstract] Elemento di Base
>Le porte logiche sono realizzate con elementi attivi chiamati ***transistor*** che operano come *interruttori automatici*
>>[!done] Funzionamento
>>Un segnale sulla ***base*** ha l'effetto di mettere in comunicazione diretta ***emettitore*** e ***collettore***

![[attachements/Transistor.png]]
*I circuiti sovrastanti rappresentano rispettivamente le porte logiche `NOT`, `NAND` e `NOR`*

## Porte Logiche di Base
---
![[Algebra di Bool#NOT]]

![[Algebra di Bool#AND]]

![[Algebra di Bool#OR]]

#### NAND
>[!info] Equivale alla porta `AND` la cui uscita è *negata*

![[attachements/NAND-Gate.png]]
>*Sebbene sembri più complicata rispetto all'`AND`, la realizzazione in termini di transistor è più semplice*
#### NOR
>[!info] Equivale alla porta `OR` la cui uscita è *negata*

![[attachements/NOR-Gate.png]]
>*Sebbene sembri più complicata rispetto all'`OR`, la realizzazione in termini di transistor è più semplice*

#### XOR
>[!info] Output `1` $\iff$ gli input sono *diversi*


![[attachements/XOR-Gate.png]]

$$
A\oplus B = \overline{A}B + A\overline{B}
$$