![[Le Periferiche#I Monitor LCD]]

Basso consumo di energia
- Molto buono per i [[Sistemi Embedded]].

>[!example] Esempio: `LCD` screen $16\times 2$

Caratterizzato da una singola linea di $16$ [[General Purpose Input Output|pin]].

Tutti i display `LCD` hanno lo stesso layout dei **pin** e possono essere connessi con ***arduino*** in *modi diversi*.
- `4` o `8` **pin**:
	- `8`: $6$ **pin** connessi ai **pin** digitali e $2$ per `VCC` e `GND`.
	- `6`: $4$ **pin** per inviare i dati e gli altri due per il *controllo*.
- Tramite [[Bus di Comunicazione#Protocollo Bus|I2C]]