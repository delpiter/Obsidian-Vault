## Cena dei Filosofi
---
>[!info] Concetti di Base
>Cinque ***filosofi*** passano la lora vita a *mangiare* e a *pensare*
>Per *mangiare* fanno uso di una tavola rotonda con:
>- $5$ sedie
>- $5$ piatti
>- $5$ posate fra i piatti
>
>Per *mangiare* un filosofo ha bisogno di ***2 posate*** (*destra* e *sinistra*)
>Per *pensare* un filosofo lascia le posate dove le ha prese

Questo problema mostra come *gestire situazioni* in cui i processi entrano in ***competizione*** per accedere ad insiemi di risorse a ***intersezione non nulla***

![[attachements/PhilosopherDinner.png]]

##### Problema
> Partiamo da una prima soluzione intuitiva

```c++
Semaphore chopsticks[5] = { new Semaphore(1), ..., new Semaphore(1) };

process Philo[i]{ /* i = 0, 1, 2, 3, 4 */
	while(true){
		//think
		chopstick[i].P();
		chopstick[(i + 1) % 5].P();
		eat();
		chopstick[i].V();
		chopstick[(i + 1) % 5].V();
	}
}
```


> [!danger] Attenzione
> Questa soluzione è la ***definizione di*** [[../Concorrenza nei sistemi#Deadlock|deadlock]].

Una situazione dove due o più azioni in competizione ***aspettano che le altre finiscano***, senza che nessuna finisca effettivamente.

Coffman definì $4$ [[../Concorrenza nei sistemi#Condizioni per deadlock|condizioni]] necessarie ma non sufficienti affinché avvenga un ***deadlock***.
- Un deadlock può avvenire in sistemi dove tutte le condizioni sono vere.
##### La vita di un Filosofo
```c++ title:Filosofo
void Philo[i]{
	while(true){
		//think
		aquireChopsticks();
		eat();
		releaseChopsticks();
	}
}
```

##### Definizioni
- $up_{i}$ Indica il numero di volte che la bacchetta $i$ viene *presa dal tavolo*
- $down_{i}$ Indica il numero di volte che la bacchetta $i$ viene *rilasciata sul tavolo*

>[!cite] Invariante
>$$down_{i}\leq up_{i} \leq down_{i}+1$$

In pratica:
> La bacchetta può essere vista come [[../Critical Section/Meccanismi per la Coordinazione#Semafori Binari|semaforo binario]].

##### Soluzione
```c++ title:"cena dei filosofi"
Semaphore chopsticks[5] = { new Semaphore(1), ..., new Semaphore(1) };

process Philo[i]{ /* i = 1, 2, 3, 4 */
	while(true){
		//think
		chopstick[i].P();
		chopstick[(i + 1) % 5].P();
		eat();
		chopstick[i].V();
		chopstick[(i + 1) % 5].V();
	}
}
```

>[!question] Perché il primo filosofo da la priorità alla bacchetta di sinistra?

Serve per inserire la *simmetria*
- Così facendo, si garantisce che ***c'è sempre qualcuno che riesce a mangiare in casi estremi***

> [!cite] In altre parole

Invece di dire che ogni filosofo richiede prima la bacchetta di destra introducendo una *assimmetria*:
- Le ***risorse*** (bacchette) vengono *numerate*, ogni ***processo*** (filosofo) deve prendere prima la bacchetta con **indice minore**
	- (il quarto filosofo prenderà la bacchetta 0 che sta a sinistra prima della 4 a destra).
- Si impone un ***ordine alle risorse***.
- Una ***simmetria*** che nella soluzione iniziale (*sbagliata*) non c'è.


> [!done] Regole generali per evitare deadlock
> Dati $n$ processi che condividono e acquisiscono multipli lock.
> 1. Assegna un ordine ai lock
> 2. Acquisisci i lock ***sempre nello stesso ordine***.
>
> > [!hint] Funzione perché rende impossibile l'attesa cicrolare


##### Soluzione Alternativa
> [!tldr] Idea
> Si aggiunge un ***sistema di ticket***, in cui a tavola ci possono essere in qualsiasi momento al massimo $N-1$ filosofi, con $N$ numero di filosofi totale.

```c++
Semaphore chopsticks[5] = { new Semaphore(1), ..., new Semaphore(1) };
Semaphore ticket = new Semaphore(4)

process Philo[i]{ /* i = 1, 2, 3, 4 */
	while(true){
		//think
		ticket.P();
		chopstick[i].P();
		chopstick[(i + 1) % 5].P();
		eat();
		chopstick[i].V();
		chopstick[(i + 1) % 5].V();
		ticket.V();
	}
}
```