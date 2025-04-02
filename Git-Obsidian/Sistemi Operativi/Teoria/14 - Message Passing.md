## Introduzione
---
>[!definizione] Definizione
>Il ***message passing*** è un paradigma di *comunicazione* tra processi
>La *sincronizzazione* avviene tramite lo ***scambio di messaggi***, e non più semplici segnali

#### Messaggio
>[!info] Definizione
>Un ***messaggio*** è un insieme di informazioni formattate da un processo *mittente* e interpretate da un processo destinatari
>>[!summary] Meccanismo di Scambio
>>Vengono *copiate* le ***informazioni*** di un messaggio da uno [[19 - Gestione della Memoria#Indirizzi Logici e Fisici|spazio di indirizzamento]] di un processo allo spazio di indirizzamento di un altro

Il passaggio dai *due spazi di indirizzamento* è mediato dal ***sistema operativo***
- Per garantire la ***protezione della memoria***
#### Operazioni
>[!example] Send
>Funzione usata dal *processo mittente* per "***spedire***" un messaggio ad un processo *destinatario*
>Il destinatario deve essere ***specificato***

>[!abstract] Recieve
>Funzione usata dal *processo destinatario* per "***ricevere***" un messaggio da un processo *mittente*
>Il processo mittente può essere specificato

### Tassonomia
##### Sincrono
>[!example] Send
>Sintassi:
>- `{cpp}p.ssend(m, q)`
>
>Il *mittente* `p` spedisce il messaggio `m` al processo `q`, ***restando bloccato*** fino a quando `q` non esegue l'operazione `{cpp}m = q.srecieve(p)`

>[!abstract] Recieve
>Sintassi:
>- `{cpp}m = q.srecieve(p)`
>
> Il *destinatario* `q` riceve il messaggio `m` dal processo `p`
> Se il *mittente* non ha ancora spedito alcun messaggio, il *destinatario* si ***blocca*** in attesa di ricevere un messaggio
> >[!note] È possibile lasciare il mittente non specificato

##### Asincrono
>[!example] Send
>Sintassi:
>- `{cpp}p.asend(m, q)`
>
>Il *mittente* `p` spedisce il messaggio `m` al processo `q`, ***senza bloccarsi*** in attesa che il destinatario esegua l'operazione `{cpp}m = q.arecieve(p)`

>[!abstract] Recieve
>Sintassi:
>- `{cpp}m = q.arecieve(p)`
>
> Il *destinatario* `q` riceve il messaggio `m` dal processo `p`
> Se il *mittente* non ha ancora spedito alcun messaggio, il *destinatario* si ***blocca*** in attesa di ricevere un messaggio
> >[!note] È possibile lasciare il mittente non specificato

##### Totalmente Asincrono
>[!example] Send
>Sintassi:
>- `{cpp}p.asend(m, q)`
>
>Il *mittente* `p` spedisce il messaggio `m` al processo `q`, ***senza bloccarsi*** in attesa che il destinatario esegua l'operazione `{cpp}m = q.nb-recieve(p)`

>[!abstract] Recieve
>Sintassi:
>- `{cpp}m = nb-recieve(p)`
>
> Il *destinatario* `q` riceve il messaggio `m` dal processo `p`
> Se il *mittente* non ha ancora spedito alcun messaggio, il la funzione ***termina*** ritornando un *messaggio nullo*
> >[!note] È possibile lasciare il mittente non specificato

###### Modello Sincrono, dato quello Asincrono
```cpp title:"Message Passing Sincrono dato l'Asincrono"
void ssend(Object msg, Process q) { 
	asend(msg, q); 
	ack = areceive(q);
} 

Object sreceive(p) { 
	Object msg = areceive(p); 
	asend(ack, p); 
	return msg; 
}
```

###### Modello Asincrono, dato quello Sincrono
```cpp title:"Message Passing Asincrono dato il Sincrono"
/* p identifies the calling process */ 
void asend(Object m, Process q) { 
	ssend(“SND(m,p,q)”, server); 
} 

void areceive(Process q) { 
	ssend(“RCV(p,q)”, server); 
	Object m = sreceive(server); 
	return m; 
} 

process server { 
/* One element x process pair */ 
	int[][] waiting; 
	Queue[][] queue; 
	while (true) { 
		handleMessage(); 
	} 
} 

void handleMessage() { 
	msg = sreceive(*); 
	if (msg == ) { 
		if (waiting[p,q]>0) { 
			ssend(m, q); 
			waiting[p,q]--; 
		} else { 
			queue[p,q].add(m); 
		}
	} else if (msg == ) { 
		if (queue[p,q].isEmpty()) { 
			waiting[p,q]++; 
		} else { 
			m = queue[p,q].remove(); 
			ssend(m, dest); 
		} 
	}
}
```