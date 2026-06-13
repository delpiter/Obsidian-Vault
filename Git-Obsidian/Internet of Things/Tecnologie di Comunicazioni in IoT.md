## Protocolli Machine-to-Machine
---
In ambito industriale, quando si parla di comunicazione tra dispositivi si fa riferimento ai cosiddetti **protocolli M2M**, ovvero protocolli pensati per la comunicazione automatica tra macchine, senza intervento umano diretto.

La comunicazione M2M può avvenire in due modi:
- **wireless** (senza fili)
- **wired** (con fili)

In entrambi i casi, è necessaria una connessione a Internet.

> [!info] Comunicazione MCU ↔ Moduli
> La comunicazione tra un microcontrollore (MCU) e i moduli di comunicazione avviene tipicamente attraverso una **porta seriale**.

### Connessione a Internet

I protocolli di riferimento per la connessione a Internet sono quelli della famiglia **IP**:
- **TCP/IP**
- **UDP/IP**

La connessione può essere stabilita in due modalità:

- **Diretta** — tramite tecnologie come 3G/4G/5G o WiFi
- **Indiretta** — per mezzo di un **Gateway**, che fa da intermediario tra il dispositivo e la rete
### Comunicazione Wireless: i Fondamentali

La comunicazione wireless è, nella sua essenza, una **comunicazione radio**. Può essere classificata in:

- **Terrestre** — infrastruttura che si trova sulla superficie terrestre
- **Satellitare** — infrastruttura in orbita intorno alla Terra

> [!tip] Da ricordare
> Tutte le tecnologie wireless si basano sulla propagazione di onde radio. La distinzione tra terrestre e satellitare riguarda *dove si trova* l'infrastruttura, non come funziona il segnale.

### Tecnologie Wireless

Le tecnologie wireless si distinguono in base alla portata:

| Categoria | Tecnologie |
|---|---|
| **Corto raggio** | Bluetooth, Visible Light Communication |
| **Medio raggio** | WPAN, WiFi |
| **Lungo raggio** | LPWA, 3G/4G/5G |

#### WiFi

Il WiFi segue lo standard **IEEE 802.11x** e, pur essendo ampiamente utilizzato anche in ambito embedded, non è stato progettato per quel contesto. Il suo principale limite è l'**alto consumo energetico**, che lo rende non ideale per dispositivi IoT a batteria.

#### 5G

> [!success] 5G e IoT
> Il 5G porta con sé molti vantaggi: alta affidabilità, velocità di trasferimento elevata e basse latenze. È stato progettato **anche per l'IoT**, rendendolo una delle tecnologie più promettenti per i sistemi M2M del futuro.

---

### Bluetooth

Il Bluetooth è una tecnologia a corto raggio che opera attraverso reti chiamate **scatternet**, organizzate secondo una logica master-slave:

- 1 **master**, che avvia e gestisce la comunicazione, connesso a un massimo di **7 slave**
- 1 slave può essere connesso a un massimo di **1 master**
- Più scatternet collegate tra loro formano una **piconet**

La comunicazione può avvenire in due modalità:

- **Connection-oriented** — è necessario stabilire una connessione prima di trasferire dati
- **Connectionless** — il trasferimento può iniziare senza una connessione esplicita, ma l'indirizzo di destinazione deve essere noto

## MQTT — Message Queue Telemetry Transport
---

MQTT è un **protocollo applicativo** basato sullo scambio di messaggi secondo il pattern **publish-subscribe**.

### Come funziona

- Un dispositivo può **sottoscriversi** (subscribe) a un determinato **topic**
- I topic sono organizzati in una struttura ad albero, simile a un filesystem, con `/` come separatore (es. `tank/waterLevel`)
- È possibile sottoscriversi a un topic specifico o all'intera ramificazione usando il carattere `#`
- Un dispositivo centrale, il **message broker**, fa da intermediario: riceve i messaggi e li distribuisce ai sottoscrittori interessati

> [!example] Esempio di topic
> `factory/line1/temperature` — identifica la temperatura della linea 1 di una fabbrica. Con `factory/#` ci si sottoscrive a tutti i dati di quella fabbrica.

### Livelli di QoS (Quality of Service)

Prima dell'inizio della comunicazione, è possibile configurare il livello di garanzia nella consegna dei messaggi:

| Livello | Garanzia |
|---|---|
| QoS 0 | Il messaggio viene recapitato **al più una volta** (best effort) |
| QoS 1 | Il messaggio viene recapitato **almeno una volta** |
| QoS 2 | Il messaggio viene recapitato **esattamente una volta** |

> [!warning] Attenzione alla scelta del QoS
> Un QoS più alto garantisce maggiore affidabilità, ma introduce overhead di rete. In contesti IoT con risorse limitate, la scelta del livello corretto è cruciale.