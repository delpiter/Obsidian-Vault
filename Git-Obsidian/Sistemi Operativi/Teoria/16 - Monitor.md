## Introduzione
---
>[!definizione] Definizione
>I ***monitor*** sono un paradigma di *programmazione concorrente* che fornisce un approccio più ***strutturato*** alla programmazione concorrente
>>[!info] Composizione
>>Un ***monitor*** è un modulo *software* che consiste di:
>>- Dati *Locali*
>>- Una *sequenza di inizializzazione*
>>- Una o più *procedure*

I dati locali sono ***accessibili*** solo alle procedure del *modulo stesso*

Un processo entra in un ***monitor*** invocando una delle sue *procedure*

Solo **un processo alla volta** può essere all'interno del ***monitor***:
- Gli altri processi che invocano un monitor sono *sospesi*
- Il ***monitor*** fornisce un semplice meccanismo di [[9 - Condivisione di Risorse#Mutua Esclusione|mutua esclusione]]

### Implementazione
```pascal title:monitor
monitor name { 
	variable declarations... //monitor private variables 
	
	procedure entry type procedurename1(args...) { // public procedure
	 ... 
	} 
	type procedurename2(args...) { //private procedure
	... 
	}
	 name(args...) { ... } // initialization
}
```

>[!hint] Osservazione
>Assomiglia ad un *oggetto* nella programmazione a *oggetti*
>- Inizializzazione -> ***Costruttore***
>- Procedure entry -> ***Metodi pubblici***
>- Procedure -> ***Metodi privati***
>- Variabili locali -> ***Variabili pubbliche*** #wtf

## Meccanismi di Sincronizzazione
---
>`{cpp} Condition c;`

- Anche detta ***conditional variable*** (*CV*)

I meccanismi di sincronizzazione sono ***operazioni definite*** sulle *CV*

>[!caution] `{cpp} c.wait()`
>Attende il ***verificarsi*** della condizione
>- Viene rilasciata la [[9 - Condivisione di Risorse#Mutua Esclusione|mutua esclusione]]
>
>Il processo che chiama `{cpp} c.wait()` viene *sospeso* in una ***coda*** di attesa della condizione `{cpp}c`

>[!asd] `{cpp} c.signal()`
>***Segnala*** che la condizione è *vera*
>- Causa la ***riattivazione immediata*** di un processo (politica `FIFO`)
>- Il chiamante viene posto in *attesa*
>	- Verrà riattivato quando il *processo risvegliato* avrà rilasciato la ***mutua esclusione***
>
>Se nessun processo sta attendendo `{cpp} c`, la chiamata non avrà ***nessun effetto***


#### Politiche di Signaling
>[!abstract] `SU` *Signal Urgent*
>Politica "*classica*" di signaling

>[!summary] `SW` *Signal Wait*
>Il *signaling* process viene messo nella ***entry queue***

>[!example] `SR` *Signal and Return*
>Dopo la `{cpp}c.signal()` si ***esce subito*** dal monitor

>[!note] `SC` Signal and Continue
>La `{cpp}c.signal()` segnala solamente che un processo *può continuare*, il chiamante ***prosegue l'esecuzione***
>- Quando lascia il monito viene riattivato il *processo segnalato*

#### Implementazione Tramite Semafori
>[!info] Componenti Necessari
>1. Una struttura dati per la ***gestione dello stack***
>2. Un [[13 - Semafori|semaforo]] di [[9 - Condivisione di Risorse#Mutua Esclusione|mutua esclusione]] `{cpp} mutex`
>3. Per ogni variabile di condizione $cond_{i}$, una coppia $(c_{i},nc_{i})$
>	- $c_{i}$ è un *semaforo* correlato alla *condizione*, inizializzato a $0$
>	- $nc_{i}$ è il *numero di processi* che sono in attesa del verificarsi della condizione
>4. Un "***allocatore***" di semafori

```cpp title:Inizialization
Semaphore e = new Semaphore(1);
Stack stack = new Stack();
```

```cpp title="Monitor Entrance/Exit"
// Entrance
e.P();

// Exit
if(!stack.empty()){
	Semaphore s = stack.pop();
	s.V();
} else{
	e.V();
}
```

```cpp title="Wait & Signal"
// wait condition i
nci++;
if(!stack.empty()){
	Semaphore s = stack.pop();
	s.V();
} else{
	e.V();
}
ci.P();

// signal condition i
if (nci > 0) { 
	nci--; 
	ci .V(); 
	Semaphore s = new Semaphore(0); 
	stack.push(s); 
	s.P(); 
}
```

