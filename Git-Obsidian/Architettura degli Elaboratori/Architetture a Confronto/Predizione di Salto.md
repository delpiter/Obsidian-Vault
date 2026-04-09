>*Uno degli algoritmi più segreti dei produttori di `CPU`*

## Brench Prediction
---
>[!info] Introduzione
>Le architetture con [[Pipelining|pipeline]] funzionano molto bene se il codice viene eseguito ***sequenzialmente senza salti***
>- A seguito di un salto che *determina un cambiamento nella sequenza di istruzioni da eseguire*, una gran parte del lavoro ***già eseguito viene buttato***
>>[!abstract] In Breve
>>Le `CPU` moderne cercano di "*indovinare*" il risultato di un operatore di salto, tramite ***algoritmi euristici***

#### Esempio
```c
if(i==0)
	k=1;
else
	k=2;
```

```assembly
CMP i,0
BNE Else
Then: MOV k,1
BR Next
Else: MOV k,2
Next:
```

*In questo esempio sapere se $i$ sarà uguale a $0$ sarebbe di grande aiuto per eseguire il* ***prefetching corretto***

### Ottimizzazioni
>[!abstract] Predizioni di Salto
> Per ottimizzare le ***operazioni di pre-fetching***, le `CPU` possono utilizzare tecniche di predizione di salto, che a fronte di istruzioni di salto condizionale cercano di prevedere se il programma salterà oppure no
> Ci sono due tipi di predizione:
> - Predizione ***Statica***
> - Predizioni ***Dinamica***

#### Predizione statica
>[!info] Funzionamento
>Vengono utilizzati ***criteri di buon senso*** derivati dallo studio delle abitudini dei programmatori e del comportamento dei compilatori
>>[!example] Esempio
>>Assumiamo che tutti i salti condizionali all'indietro vengano eseguiti
>>- `While`, `For`

#### Predizione Dinamica
>[!info] Funzionamento
>Vengono mantenute ***statistiche*** (*tabelle interne*) circa la ***frequenza*** con cui i *recenti salti condizionali* sono stati eseguiti
>Sulla base di queste statistiche la `CPU` esegue la predizione.
>>[!example] Esempio
>>Se nelle ultime $n$ volte il salto corrispondente ad una data istruzione è stato eseguito almeno $n/2$ volte, allora è probabile che venga eseguito di nuovo

### Esecuzione Fuori Ordine
>[!info] *Out Of Order Execution*
>Nel tentativo di ***massimizzare le prestazioni***, alcune `CPU` consentono di saltare ***temporaneamente*** istruzioni che hanno *dipendenze*, lasciandole in attesa, e di passare ad eseguire ***istruzioni successive*** non dipendenti
>Questo tipo di tecnica prende il nome di ***Esecuzione Fuori Ordine***
>>[!caution] Garanzia
>>Questa tecnica deve comunque garantire di ottenere *esattamente gli stessi risultati* dell'***esecuzione ordinata***

### Esecuzione Speculativa
>[!info] Speculative Execution
>Tecnica correlata all'*esecuzione fuori ordine*
>Consiste nell'***anticipare*** il più possibile l'***esecuzione di alcune parti del codice*** (*gravose*) prima di sapere se queste serviranno
>>[!example] Esempi
>>L'anticipazione (***hoisting***) può essere relativa ad una ***operazione floating point*** o una ***lettura da memoria***
>
>>[!caution] Garanzia
>>Come l'*esecuzione fuori ordine*, nessuna delle istruzioni anticipate deve ***produrre effetti irrevocabili***

Molto spesso l'hardware della `CPU` non è in grado da solo di anticipare istruzioni, se non in casi banali o senza il ***supporto dei compilatori***
- In alcuni *processori recenti*, vengono previste particolari istruzioni che il compilatore può usare per ottimizzare il comportamento della `CPU`

>[!danger] Ricorda
>Tutte queste operazioni ***rimangono sempre nei registri*** della `CPU`, se qualcosa risulta essere sbagliato, la pipeline viene ***interamente pulita***, altrimenti si scrive nell'ordine previsto tutti i calcoli già fatti

## BUG Architetturali
---
>*A inizio 2018 sono stati resi pubblici da ricercatori, importanti bug di sicurezza, noti come **Meltdown** e **Spectre**, che coinvolgono la maggior parte delle `CPU` moderne*
>*Questi attacchi fanno uso di Cache e Esecuzione fuori ordine*

![[attachements/Meldtown-Spectre.png]]

Dopo la pubblicazione di queste vulnerabilità le `CPU` che uscirono successivamente furono più lente di circa $30$% rispetto a quelle precedenti 
### Meltdown
>[!info] Concetto
>L'attacco ***Meltdown*** permette di ***leggere*** il contenuto di ***tutta la memoria fisica***, *ignorando i vincoli* che non consentono ad un processo di vedere la memoria al di fuori della porzione a lui dedicata
>- La questione è particolarmente ***grave*** nel caso di *macchine virtuali e sistemi cloud*, dove i dati sono condivisi fra più aziende in una sola ***macchina fisica***

#### Funzionamento
>*Il funzionamento è relativamente semplice da intuire*

1. Si generano accessi a ***locazioni proibite*** (*aree di memoria che si vogliono spiare*)
2. L'***esecuzione fuori ordine*** permette la lettura di queste locazioni prima ancora della ***verifica dei permessi***
3. Una volta verificato che i *permessi non consentono l'accesso*, si ***genera un'eccezione*** e non si rende disponibile il contenuto della memoria
4. Nel frattempo la lettura ha provocato ***effetti collaterali*** all'interno della ***cache***, che ***non sono annullati***
5. ***Interrogando la cache*** in modo opportuno (se un dato è presente nella cache la *risposta è molto più veloce*), si può ***risalire al contenuto*** della cella di memoria

