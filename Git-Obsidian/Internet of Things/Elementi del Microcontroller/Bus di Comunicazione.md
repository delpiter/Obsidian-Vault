## Bus e Protocolli
---
> I protocolli per scambiare i dati possono essere molto complessi, in base al dispositivo esterno.

Per questo motivo sono state introdotte delle interfacce di comunicazione specifiche, bus e protocolli.

>[!note] Tipologie
>Due tipi principali **seriale** e **parallelo**.

> ***Seriale***:
- Invio di uno stream di `bit` in modo sequenziale in un singolo canale.

> ***Parallelo***:
- Permette il trasferimento di più `bit` allo stesso momento tramite più canali.

![[BUS dei Calcolatori#BUS Sincroni e Asincroni]]

>[!abstract] BAUD Rate
>La velocità di trasmissione in `bit`$/\sec$ 

A livello hardware, un `BUS` seriale è composto da due *linee*:
- Una per trasmettere i `bit`.
- Una per ricevere i `bit`.

Uno dei componenti principali di un sistema seriale è `UART` (***U***niversal ***A***synchronous ***R***eceiver ***T***ransmitter).
	- Ha il compito di [[BUS dei Calcolatori#Arbitraggio del BUS|arbitrare]] i dati che arrivano e che partono dalle interfacce seriali.
#### Data Frame
> Ogni blocco di dato è trasmesso in un pacchetto chiamato ***frame***.

I frame sono creati ***aggiungendo delle sincronizzazioni***.

```mermaid
---
title: "Data Frame"
---
	packet-beta
	0-1: "Start"
	2-9: "Data"
	10-11: "Parity"
	12-13: "Stop"
```
>[!warning] Attenzione
>Prestare attenzione all'"[[Definizioni_Architettura#Ordinamento dei `BYTE`|endianess]]".

#### Libreria Seriale
> `Serial`class is an extension of `Stream` and includes methods such as:
- `{c}begin()`, `{c}end()`
- `{c}read()`, `{c}readBytes()`, `{c}readBytesUntil()`, `{c}peek()`, `{c}available()`
- `{c}parseFloat()`, `{c}parseInt()`
- `{c}write()`, `{c}flush()`
- `{c}print()`, `{c}println()`
- `{c}setTimout()`
- `{c}serialEvent()`

```c
char data;

void setup()
{
	Serial.begin(9600);
}

void loop()
{
	if(Serial.available())
	{
		data = Serial.read();
		Serial.print(data);
	}
}
```

#### Protocollo Bus
>[!todo] $I^{2}C$
>Il protocollo "***eye to see***" è un protocollo standard per i `BUS`.

Buone velocità, minimizzando il numero di `PIN` richiesti.
- Anche detto `TW` (Two Wire) poiché usa solo $2$ linee per la comunicazione (**data** e **clock**).

Ha una architettura di tipo [[BUS dei Calcolatori#Master e Slave|master e slave]].
- La comunicazione è sempre iniziata dal **master**.
- Il messaggio è ricevuto da tutti gli **slave**, solo il *target slave* reagisce al messaggio.

##### SPI
>[!abstract] SPI
>Il `BUS` ***SPI*** implementa un protocollo seriale ***full-duplex*** che permette una comunicazione bidirezionale tra il *master* e gli *slaves*.

**Non** è uno *standard ufficiale*.
