## Input Output
---
>[!abstract] PIN
> Ogni microcontroller, contiene un insieme di ***pin*** che possono essere usati per guidare l'input e l'output.

I `PIN` sono tipicamente ***general purpose***, possono essere programmati come **input** o **output**, in *base alle necessità*.

I pin possono essere [[Il Calcolatore e i Numeri Binari#I sistemi Digitali|analogici]] o [[Il Calcolatore e i Numeri Binari#I sistemi Digitali|digitali]].
- Un ***pin digitale*** può assumere solo due valori `HIGH` o `LOW` (`1` o `0`).
- Un ***pin analogico*** può assumere un qualsiasi valore nel range `0..5V` ([[Potenziale Elettrico#Potenziale Elettrico|Volt]]).
	- Valori compresi tra `GND` e `VCC`.

>[!caution] Conversione
>La conversione è fatta dal `ADC` (analog to digital converter) che mappa un *voltaggio continuo* in un ***range di valori discreti***.

>[!help] Parametri di riferimento per i `PIN`

> ***Voltaggio***: [[Potenziale Elettrico#Potenziale Elettrico|Volt]]

> ***Corrente***: [[Corrente Elettrica#Ampere|Ampere]]


Oltre ad essere general purpose, alcuni `PINs` hanno delle ***funzioni aggiuntive*** che possono essere attivate:
- Dette `PIN` [[Multiplexing|multiplexed]] functions 
>[!example] Esempi
- **Interfacce seriali**.
- **Interrupt**.
- etc...
### Porte
>[!info]
>Il ***microcontroller*** interagisce con i `PIN` attraverso le ***porte***.
>- Come per i `PIN` le *porte* possono essere sia di *input* che di *output*.

Una porta è gestita da uno o più `SRF` (***S***pecial ***P***urpose ***R***egisters).
- Ha il compito di mantenere lo ***stato*** (il valore corrente) e la configurazione (**input**/**output**).

### Impostare, Scrivere e Leggere un PIN
>Ci sono delle `API` per il funzionamento dei `PIN`.

`{c icon} pinMode()`
- Serve per impostare la *direzione* del `PIN` (**input**/**output**).

`{c icon} digitalWrite()`
- Per impostare il valore di un `PIN` **output**.

`{c icon} digitalRead()`
- Per leggere il valore di un `PIN` **input**.

`{c icon} int analogRead(int PIN)`
- Per leggere un valore analogico in un `PIN` specifico.

>[!hint] Dettaglio: I delay
>`{c icon} delay()` è una procedura che esegue un [[10 - Sezioni Critiche#Busy-Waiting|busy waiting]] per un numero specificato di millisecondi.

```c title:delay()
void delay(unsigned long ms)
{
	unsigned long start = millis();
	while(millis() - start <= ms);
}
```

### Pulsewidth Modulation
>[!definizione]
>Il `PWM` è un metodo per ***simulare*** un segnale analogico in output sui `PIN` **digitali**.

L'output è definito dal ***duty cycle***.
- Il ***duty cycle*** è un valore percentuale che rappresenta il periodo in cui il segnale è `HIGH`.
- Il valore medio del voltaggio è dato dalla seguente equazione: $\text{duty-cycle}\cdot VCC$.

### Interrupt
>[!info]
>Gli [[Interfacciamento di Periferiche#Interrupt|interrupt]] sono un meccanismo fondamentale usato dai microcontroller per reagire ad eventi innescati da **dispositivi esterni**.

Una `CPU` fornisce diversi `PIN`, chiamati `IRQ` (interrupt request), per ***ricevere dei segnali di interrupt***.

>[!warning] Interrupt disabilitati
>Quando gli interrupt sono disabilitati, tramite le funzioni `noInterrupts()` (*enable*) e `interrupts()` (*disable*), il sistema **non reagisce ad eventi esterni**.

Queste funzioni devono essere usate con ***cautela***.
- Si vuole avere una "***interrupt latency***" *bassa*. (tempo usato per reagire ad un interrupt).
#### Handling interrupts in Wiring
> `API`:
- `attachInterrupt(intNum, ISR, mode)`, where
    - `intNum`: interrupt number
    - `ISR`: pointer to handler `void (*func)(void)`
    - `mode`:
        - `CHANGE/RISING/FALLING` $\rightarrow$ at change `HIGH` $\leftrightarrow$ `LOW`
        - `LOW/HIGH` $\rightarrow$ when the state is `LOW` or `HIGH`
- `digitalPinToInterrupt(numPin)` helps finding `intNum` for the previous function

```c
#define BTN_PIN 2
volatile int count = 0;
int prev = 0;

void setup() {
	Serial.begin(9600);
	attachInterrupt(digitalPinToInterrupt(BTN_PIN), inc, CHANGE);
}

void loop() {
	noInterrupts();
	int current = count;
	interrupts();
	if (current != prev) {
		Serial.println(current);
		prev = current;
	}
}

void inc() {
	count++;
}
```