## Lettori e Scrittori
---
>[!info] Concetti Base
>Un ***database*** è condiviso tra un certo numero di *processi*
>Esistono *due tipologie* di processi
>>[!hint] Lettori
>>I ***lettori*** accedono al database per leggere il contenuto
>
>>[!cite] Scrittori
>>Gli ***scrittori*** accedono al database per aggiornare il contenuto

#### Proprietà
>Se uno scrittore accede al ***database***:
- Esso lavora in mutua esclusione
- Nessun altro lettore o scrittore può accedere al *database*

>Se ***nessuno*** scrittore sta accedendo al ***database***
- Un numero arbitrario di lettori può accedere al *database*

Le soluzioni devono soddisfare la seguente invariante:
>[!abstract] Invariante
>$$(nr > 0 \text{ AND }nw == 0) \mid \mid (nr== 0 \text{  AND } nw \leq 1)$$

### Soluzioni
#### Prima soluzione sovra vincolata
> Si usa un semaforo singolo che funziona come lock

```c++
Semaphore rw = new Semaphore(1);
DataBase db;

void Reader(){
	while(true) {
		rw.P();
		Item el = db.read();
		rw.V();
	}
}

void Writer(){
	while(true) {
		rw.P();
		Item el = create_record();
		db.write(el);
		rw.V();
	}
}
```

> [!warning] Inefficiente
> Ogni lettore e scrittore hanno ***accesso esclusivo al database***.
> In questo modo serializziamo l'accesso anche ai lettori.

#### Soluzione con multipli lettori concorrenti
> Usiamo in questa soluzione diversi semafori per gli scrittori.

```c++
Semaphore rw = new Semaphore(1);
DataBase db;
int nr = 0;
Semaphore mutexR = new Semaphore(1);

void Reader(){
	while(true) {
		mutexR.P();
		if(nr==0){
			rw.P();
		}
		nr++;
		mutexR.V();
		Item el = db.read();
		mutexR.P();
		nr--;
		if(nr==0){
			rw.V();
		}
		mutexR.V();
	}
}

void Writer(){
	while(true) {
		rw.P();
		Item el = create_record();
		db.write(el);
		rw.V();
	}
}
```

> [!done] In breve
> In questa soluzione permettiamo ad un lettore di entrare in lettura se la ***risorsa è libera*** o ***occupata da altri lettori***.
#### Priorità
>[!info] Priorità ai Lettori
>Se un *lettore* vuole accedere al database, lo potrà fare a patto che uno scrittore ***non*** l'abbia occupato
>>[[../Concorrenza nei sistemi#Starvation|Starvation]]

>[!list] Priorità ai Lettori
>Uno *scrittore* attenderà il ***tempo minimo possibile*** prima di accedere al database