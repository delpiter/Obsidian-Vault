## Input Output
---
>[!abstract] PIN
> Ogni microcontroller, contiene un insieme di ***pin*** che possono essere usati per guidare l'input e l'output.

I `PIN` sono tipicamente ***general purpose***, possono essere programmati come **input** o **output**, in *base alle necessità*.

I pin possono essere [[../../Architettura degli Elaboratori/Rappresentazione dell'Informazione/Il Calcolatore e i Numeri Binari#I sistemi Digitali|analogici]] o [[../../Architettura degli Elaboratori/Rappresentazione dell'Informazione/Il Calcolatore e i Numeri Binari#I sistemi Digitali|digitali]].
- Un ***pin digitale*** può assumere solo due valori `HIGH` o `LOW` (`1` o `0`).
- Un ***pin analogico*** può assumere un qualsiasi valore nel range `0..5V` ([[../../Fisica/Elettromagnetismo/Potenziale Elettrico#Potenziale Elettrico|Volt]]).
	- Valori compresi tra `GND` e `VCC`.

>[!caution] Conversione
>La conversione è fatta dal `ADC` (analog to digital converter) che mappa un *voltaggio continuo* in un ***range di valori discreti***.

>[!help] Parametri di riferimento per i `PIN`

> ***Voltaggio***: [[../../Fisica/Elettromagnetismo/Potenziale Elettrico#Potenziale Elettrico|Volt]]
- Da applicare al pin (*input*) o prodotto dal pin (*output*).

> ***Corrente***: [[../../Fisica/Elettromagnetismo/Circuiti/Corrente Elettrica#Ampere|Ampere]]
- Corrente che si è in grado di ricevere (*input*) o prodotta (*output*)
- In questo caso si parla di *milliampere* ($40mA$, arduino o $12mA$, ESP32).

Oltre ad essere general purpose, alcuni `PINs` hanno delle ***funzioni aggiuntive*** che possono essere attivate:
- Dette `PIN` [[../../Reti/Introduzione/Multiplexing|multiplexed]] functions.

>[!example] Esempi
- **Interfacce seriali**.
- **Interrupt**.
- etc...
### Porte
>[!info]
>Il ***microcontroller*** interagisce con i `PIN` attraverso le ***porte***.
>- Come per i `PIN` le *porte* possono essere sia di *input* che di *output*.

Una porta è gestita da uno o più `SRF` (Special Purpose Registers).
- Ha il compito di mantenere lo ***stato*** (il valore corrente) e la configurazione (**input**/**output**).

Sul `ATMega328P` (arduino):
- Ogni porta è gestita da 3 registri
	- *DDRx*, *PORTx*, *PINDx*, dove *x* è il nome della porta.

> `DDRx` mantiene la direzione del pin (**input/output**).

> `PORTx` mantiene lo stato del pin.
- Per un pin input il `bit` a $1$ attiva la resistenza di Pull Up, a $0$ la disattiva.
	- Le resistenze usate nei circuiti per garantire che gli ingressi di un sistema logico stabilito siano a livelli logici previsti se i dispositivi esterni sono scollegati.
- Per pin output il `bit` a $1$ indica lo stato `HIGH`, $0$ lo stato `LOW`.

> `PINx`, per i pin input, mantiene il valore del segnale letto.
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
>`{c icon} delay()` è una procedura che esegue un [[../../Sistemi Operativi/Teoria/10 - Sezioni Critiche#Busy-Waiting|busy waiting]] per un numero specificato di millisecondi.

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
- Il valore medio del voltaggio è dato dalla seguente equazione:
$$
\text{VCC}_{\text{average}} = \text{duty cycle } \times \text{VCC}
$$

### Interrupt
>[!info]
>Gli [[../../Architettura degli Elaboratori/Architettura del Calcolatore/Interfacciamento di Periferiche#Interrupt|interrupt]] sono un meccanismo fondamentale usato dai microcontroller per reagire ad eventi innescati da **dispositivi esterni**.

Una `CPU` fornisce diversi `PIN`, chiamati `IRQ` (interrupt request), per ***ricevere dei segnali di interrupt***.

>[!warning] Interrupt disabilitati
>Quando gli interrupt sono disabilitati, tramite le funzioni `noInterrupts()` (*enable*) e `interrupts()` (*disable*), il sistema **non reagisce ad eventi esterni**.

Queste funzioni devono essere usate con ***cautela***.
- Si vuole avere una "***interrupt latency***" *bassa*. (tempo usato per reagire ad un interrupt).
- È meglio evitare utilizzare funzioni come `delay()`
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