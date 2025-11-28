## Timers
---
> I ***Timers*** sono usati per implementare *funzionalità di alto livello*.

>[!done] Soluzione Più semplice
>Nel caso più semplice un timer è implementato tramite un counter, ***incrementato a livello hardware***.

```c title:"millis() using timers"
unsigned long millis()
{
	unsigned long m;
	uint8_t oldSERG = SERG;
	
	cli();
	m = timer0_millis; // variable that contains the value of the timer0 counter
	SERG = oldSERG;
	
	return m;
}
```

>[!danger] Watch Dog Timer
>Il ***Watch Dog Timer*** è un timer che conta fino ad un valore specificato, dopodiché un segnale è prodotto per **riavviare il sistema**.

In un normale funzionamento, il *watch dog timer*, riceve periodicamente un segnale prima di raggiungere il **threshold**, resettando il counter.
- Se non riceve un segnale, significa che il **microprocessore** ha incontrato un problema ([[9 - Condivisione di Risorse#Deadlock|deadlock]]) e deve essere resettato.

### Timers e Pulsewidth Modulation
>[!warning] Attenzione
>Dobbiamo prestare particolare attenzione alle interferenze quando si usano i timer e i `PWM`.

Se usiamo `{c} Timer1` direttamente, non possiamo utilizzare i `PIN` `9` e `10` per `PWM`.
- Potrebbero andare in conflitto (es. librerie per i servo motori).
### Timer e Interrupts
>[!example] `ATMega328`

I counter sono aggiornati a $16MHz$
- Ogni tick accade ogni $1/16.000.000$ di secondo ($\sim 63ns$).
- `{c icon} Timer0` e `{c} Timer2` sono a `8 bit`, ci mettono $256\cdot63 =16128ns$ per mandare in **overflow** il counter (riparte da $0$).
- `{c icon} Timer1` è a `16 bit`, $\sim 4.1ms$.

La frequenza di aggiornamento si può modulare specificando un valore `prescaler`, che divide la frequenza originale.
- `{c icon}int TimerSpeed = 16,000,000/prescaler;`

> Specificando un **prescaler** di $1$ il counter è incrementato a $16MHz$.

> Specificando un **prescaler** di $8$ il counter è incrementato a $2MHz$.

Il prescaler può essere: $[1,8,64,1024]$

>[!abstract] Generazione degli [[Interfacciamento di Periferiche#Interrupt|interrupt]].
>Dato un prescaler la ***frequenza di generazione di un interrupt*** è:
>- `{c icon} int interruptFrequency = 16,000,000/(prescaler * matchRegister + 1)`

