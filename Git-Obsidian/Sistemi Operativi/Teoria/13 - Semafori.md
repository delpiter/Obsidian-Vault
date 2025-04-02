>Il nome indica chiaramente che si tratta di un ***paradigma*** per la ***sincronizzazione***

## Principio di Base
---
>Due o più processi possono cooperare attraverso semplici segnali

>[!definizione] Definizione
>Il ***semaforo*** è un tipo di dato astratto per il quale sono definite due operazioni
>>[!note] `V`
>>Invocata per *inviare* un segnale, come il verificarsi di un *evento* o il rilascio di una *risorsa*
>
>>[!cite] `P`
>> Invocata per *attendere* il segnale, come un *evento* o il rilascio della *risorsa*

###### Definizione informale
> Un semaforo può essere visto come una variabile intera

- L'operazione `P` ***attende*** che il valore del semaforo sia *positivo*
	- E *decrementa* il valore del semaforo
- L'operazione `V`  *incrementa* il valore del semaforo

>[!note] Le azioni `V` e `P` sono ***atomiche***

### Semaforo Invariante
>Siano $n_{p}$ il numero di operazioni `P` completate, $n_{v}$ il numero di operazioni `V` completate e $init$ il *valore iniziale* del semaforo

>[!abstract] Allora vale la seguente affermazione
>$$n_{p}\leq n_{v}+init$$

#### Politiche di Gestione dei Processi Bloccati
> Per ciascun semaforo:

- Il *sistema operativo* deve mantenere una struttura dati contenente l'***insieme dei processi sospesi***
- Quando un processo deve essere "*svegliato*" è necessario selezionare uno dei processi ***sospesi***

>[!info] Semafori `FIFO`
>La politica più semplice è quella `FIFO`, il processo che è stato in ***sospeso più a lungo*** viene "*svegliato*" per primo
>- Garantisce assenza di [[9 - Condivisione di Risorse#Starvation|starvation]] 
>- Struttura dati usata: ***Coda***

```c title:"Implementazione Semafori"
void P(){
	//[enter CS]
	value--;
	if(value < 0){
		pid = <id of invoker>;
		queue.add(pid);
		suspend(pid);
	}
	//[exit CS]
}

void V(){
	//[enter CS]
	value++;
	if(value <= 0){
		pid = queue.remove();
		wakeup(pid);
	}
	//[exit CS]
}
```

 Con questa soluzione vengono *ridotti notevolmente* i tempi di ***busy-waiting***
>[!warning] Non vengono completamente eliminati

Infatti, vengono semplicemente "*spostati*":
- Prima, il potenziale ***busy-waiting*** era esteso lungo *tutta* la sezione critica del processo
- Ora compare solamente durante la *modifica del semaforo*

## Semafori Binari
---
>[!definizione] Definizione
>I ***semafori binari*** sono una variante dei semafori il cui valore può assumere solo i valori `0` e `1`
>>[!question] A cosa servono?
>>Servono a garantire [[9 - Condivisione di Risorse#Mutua Esclusione|mutua esclusione]]
>>

#### Semaforo creato tramite Semafori Binari
>È possibile utilizzare i *semafori binari* per implementare un semaforo *generale*

>[!abstract] Componenti necessari
>- Un semaforo `mutex` per garantire la ***mutua esclusione***
>- Un semaforo ***privato*** `delay` per ciascun processo che partecipa
>- Una coda per garantire ***fairness***
>- Un `value` che indica quanti processi possono esserci

> Inizializzazione

- Viene inizializzato il semaforo `mutex` a $1$ 
- Inizializzati tutti i semafori `dealy` a $0$
- Inizializzo la *coda*

>Funzionamento `P()`

- Blocco il semaforo `mutex`
- Controllo il valore di `value`
	- Se è minore di $0$ blocco il semaforo privato `delay[pid]`
- Sblocco il semaforo `mutex`

>Funzionamento `V()`

- Blocco `mutex`
- Controlli il valore di `value` 
	- Se è minore o uguale a $0$ sblocco il semaforo privato del *primo processo in coda*
- Sblocco il semaforo `mutex`

>[!done] È possibile anche costruire un semaforo binario con un semaforo generale

>Concetto base:

Il semaforo viene implementato tramite due semafori binari
- Uno che *blocca* i processi che vogliono *diminuire* il valore a $-1$
- Uno che *blocca* i processi che vogliono *aumentare* il valore a $2$