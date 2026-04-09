## ALU
---
>[!info] Definizione
>Un'***unità aritmetico logica*** è un circuito capace di eseguire operazioni ***aritmetiche*** e ***logiche*** elementari su due parole di input $A$ e $B$
>La maggior parte delle `ALU` esegue:
>- $A$`AND`$B$, `AND` logico `BIT` a `BIT`
>- $A$`OR`$B$, `OR` logico `BIT` a `BIT`
>- $\overline{A}$, complemento o negazione `BIT` a `BIT`
>- $A+B$, *Somma aritmetica*

### ALU a $1$ `BIT`
>*La figura a seguito mostra una `ALU` a $1$ `BIT`. Nel circuito sono evidenziati i diversi blocchi strutturali*

![[attachements/1Bit ALU.png]]
- *Gli input `ENA` e `ENB` possono essere utilizzati per forzare a $0$ gli input $A$ e $B$*
- *È possibile avere come input $\overline{A}$ al posto di $A$ semplicemente impostando a $1$ l'input `INVA`*

>[!abstract] Decoder
>Nell'angolo inferiore a sinistra, troviamo un [[Circuiti Combinatori#Decoder|decoder]] a $2$ `BIT`, le cui 4 linee di *output* vengono utilizzate per l'*attivazione* delle 4 diverse ***operazioni***
>- Questo avviene tramite un `AND` fra le linee di output del decoder e l'output dell'operazione

>[!tldr] Unità Logica
>In alto troviamo l'***unità logica***, in grado di calcolare le 3 ***operazioni logiche***.
>3 porte `AND` sono necessarie per dirigere ***1 solo output*** verso l'uscita in base alla *funzione selezionata*

>[!tip] Full-Adder a $1$ `BIT`
>In basso a destra troviamo un [[Circuiti Combinatori#Full-Adder|full-adder]] a $1$ `BIT`.
>Tutte le porte `AND` in aggiunta hanno il compito di ***abilitare*** o *meno* le **uscite** nel caso in cui la funzione "$+$" sia quella selezionata

### ALU a $n$ `BIT`
>*Il seguente circuito consente di eseguire le operazioni aritmetiche e logiche di base su due parole $A$ e $B$ di lunghezza $8$ `BIT` e di produrre il risultato nella parola $O$, anche essa da $8$ `BIT`*

![[attachements/8Bit ALU.png]]

>[!done] Il circuito è realizzato concatenando $8$ `ALU` a $1$ `BIT`

- Gli input di selezione $F_{0}$ e $F_{1}$ sono collegati ai *corrispondenti input di tutte* le $1$ `BIT` `ALU`
- Il riporto intermedio viene propagato da una $1$ `BIT` `ALU` alla ***successiva nella catena***
>[!warning] Attenzione, La propagazione non è *istantanea*

- L'ulteriore ingresso `INC` collegato alla $1$ `BIT` `ALU` relativa al `BIT` meno significativo, consente di ***incrementare il risultato di una unità*** nel *caso di addizione*
	- Tale input non richiede alcuna circuiteria aggiuntiva, in quanto coincide con l'input ***carry in***

