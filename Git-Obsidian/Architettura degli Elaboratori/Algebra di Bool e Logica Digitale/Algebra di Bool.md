>[!question] Perché studiare l'algebra di Bool?

Si studia l'algebra booleana poiché le funzioni dell'algebra booleana sono ***isomorfe*** ai circuiti digitali.
- Un *circuito digitale* può essere espresso tramite un'*espressione booleana* e ***viceversa***

## Funzione Booleana
---
>[!info] Definizione
>Una ***funzione booleana*** ha una o più variabili in input e fornisce risultati che dipendono solo da queste variabili
>>[!abstract] Tabella di Verità
>>Poiché le variabili possono assumere solo i valori $0$ o $1$, una funzione booleana con $n$ variabili di input, ha solo $2^n$ *combinazioni possibili* e può essere descritta dando una tabella, detta ***tabella di vertià***

$$
V=f(X,Y,Z)
$$
![[attachements/Bool Function Truth Table.png]]

### Operazioni di Base
>*L'algebra di **Boole** si basa su tre operatori di base, `AND`, `OR`, `NOT`*

Tutte le ***funzioni booleane*** possono essere espresse come combinazione di queste tre operazioni


#### NOT
>[!info] Nega il segnale di ingresso


![[attachements/NOT-Gate.png]]
#### OR
>[!info] Output `1` se *almeno* uno dei due input è `1`

![[attachements/OR-Gate.png]]
#### AND
>[!info] Output `1` $\iff$ entrambi gli input sono `1`

![[attachements/AND-Gate.png]]

### Rappresentazioni Alternative
>*Le dimensioni delle tabelle di verità crescono al crescere delle variabili in input, sono quindi necessarie delle rappresentazioni alternative*

#### Ordinamento delle Righe
>[!info] ‎ 
>Ordinando le righe dell'input come i ***numeri binari*** è possibile codificare le tabelle di verità memorizzando solo la colonna dell'***output***

![[attachements/Simplified Truth Table.png]]

#### Output `1`
>[!info] ‎ 
>Si può specificare l'output di ogni ***funzione booleana*** esprimendo, tramite una ***espressione booleana***, quali combinazioni delle variabili di input determinano l'output `1`

Questa rappresentazione è importante perché può essere ***direttamente tradotta*** in un circuito di ***porte digitali***

Nell'esempio precedente, la rappresentazione sarebbe:
- `011`
- `101`
- `110`
- `111`

### Convenzioni Notazionali

>[!info] `1`
>Una variabile con valore `1` è indicata con il suo nome
>$$X,Y,Z,\dots$$

>[!abstract] `NOT`
>Il `NOT`  rappresenta una variabile con valore `0` e si indica con il nome della variabile con una *barra sopra*
>$$\overline{X},\overline{Y},\overline{Z}$$

>[!abstract] `AND`
>L'operatore `AND` *booleano* è indicato da un $\cdot$ moltiplicativo
>Oppure viene considerato ***implicitamente presente***
>$$X\cdot Y\cdot Z$$

>[!abstract] `OR`
>L'operatore `OR` *booleano* è indicato da un $+$
>$$X + Y +Z$$


### Da Tabella di Verità a Espressione Booleana
>*Passaggi da fare per passare da Tabella di verità alla notazione tramite espressione booleana*

1. ***Identificare*** tutte le righe della tabella che danno `1` in *output*
2. Per ogni riga trovata scrivere la ***configurazione*** delle variabili che la ***definiscono***
	1. Tutte le variabili della combinazione saranno in `AND` fra loro
3. ***Collegare*** tramite `OR` tutte le *configurazioni ottenute*

La tabella di prima espressa con queste notazioni è:
$$
\overline{X}YZ+X\overline{Y}Z+XY\overline{Z}+XYZ
$$

## Semplificazione di Funzioni Booleane
---
>*Le funzione booleane possono essere descritte da più espressioni equivalenti*

>[!info] Definizione
>Due *funzioni booleane* si dicono ***equivalenti*** se presentano lo stesso output per *qualsiasi configurazione dell'input*

>[!question] Cosa si intende per più semplice?

Una espressione $f'$ è più *semplice* di una espressione $f$, $f\equiv f'$ secondo il 
***criterio del minor numero di operatori***
- Se il suo calcolo richiede meno operazioni di `AND` e `OR` rispetto al calcolo di $f$

>[!done] ‎ 
>Determinare la ***più semplice espressione booleana*** equivalente alla funzione data
>permette di ***semplificare i circuiti*** corrispondenti

$$
XY\overline{Z}+X\overline{Y}Z+XYZ \equiv X(Y+Z)
$$
![[attachements/Simplified Boolean Function.png]]

### Proprietà
>*Le funzioni booleane possono essere semplificate applicando ripetutamente le seguenti proprietà*

![[attachements/Boolean Propreties.png]]