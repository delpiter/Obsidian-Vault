## Alcuni Fondamenti
---
>[!tldr] Principio di Privilegio minimo
> Il sistema [[Introduzione ad Android|android]] implementa il principio di privilegio minimo.
> - Ogni app, per *impostazione predefinita*, ha accesso ***solo ai componenti necessari per svolgere il proprio lavoro*** e non di più.

Può comunque richiedere l'autorizzazione per accedere ai dati del dispositivo.
- Posizione, videocamera, bluetooth, ...

### Components
>[!info] App Components
>I ***componenti*** sono i blocchi fondamentali di un'[[Architettura#System Apps|app]] *android*.

Ogni componente è un *entry point* attraverso il quale il sistema o un utente possono accedere all'app.

> Ci sono 4 diversi tipi di componenti:
- **Activities**.
- **Services**.
- **Broadcast Receivers**.
- **Content Providers**.

Un aspetto unico del design del sistema android è che *qualsiasi app* può **avviare** il componente di un'*altra app*.

>[!caution] Attenzione
>Le app ***android*** **non** hanno un *unico punto di ingresso*.
>- Non esiste una funzione `main()`.


#### Activities
>[!definizione]
>Un ***activity*** è un *entry point* per l'interazione con l'utente.
>>[!info] Rappresenta una ***singola schermata con un'interfaccia utente***

> Esempio: App di posta elettronica

Le attività possono essere:
- Mostra un elenco di nuove e-mail.
- Composizione di un'e-mail.
- Lettura di un'e-mail.

>[!done] Ognuna è indipendente dalle altre
- Una  qualsiasi app può avviare una di queste attività se l'app di posta elettronica lo consente.

Un'*activity* facilita le seguenti interazioni tra sistema e app:
- Tenere traccia di ciò che l'utente attualmente ha sullo schermo per garantire che il sistema continui a eseguire il processo che ospita l'attività.
- Sapere che i processi usati in precedenza contengono elementi a cui l'utente può tornare.
- Aiutare l'app a gestire il suo processo interrotto in modo che l'utente possa tornare alle attività con lo stato precedete.
- Fornire un modo per le app di implementare i flussi di utente tra loro e per il sistema di coordinare questi flussi.

>[!todo] Si implementa un'*activity* come sottoclasse della classe `Activity`

#### Services
>[!definizione]
>Un ***service*** è un *entry point* per mantenere un'app in esecuzione in **background**.

Viene eseguito in background per eseguire **operazioni di lunga durata** o eseguire lavori per **processi remoti**.

>[!danger] Un service **non** fornisce un'interfaccia utente

> Esempio:
- Riproduzione della musica in background.

Un altro componente, come un'[[#Activities|activity]], può avviare il service e lasciarlo in esecuzione o associarsi ad esso per interagire con esso.

> Esistono tre tipi di services
- Foreground
- Background
- Bound

>[!todo] Il componente è implementato come una sottoclasse di `Service`

>[!nota]
>Dalla versione $5$ in poi di ***android*** è meglio usare un `Job` di `JobScheduler` o un `worker` di `WorkManager`, per schedulare azioni.
>- Permette di ridurre il consumo di batteria.
##### Foreground Services
>[!info]
>Indicano al sistema di mantenerli in esecuzione ***fino al completamento del loro lavoro***, anche se l'utente non sta interagendo con l'app.

> Esempio:
- Riproduzione musicale, qualcosa di cui l'utente è ***direttamente a conoscenza***.

##### Background Services
>[!info]
>Sono ***services*** che eseguono in background *senza che l'utente ne sia direttamente a conoscenza*.

Può consentire che venga ucciso, se ha bisogno di `RAM` per cose che destano maggiore preoccupazione.

> Esempio:
- Il contapassi o altri **sensori** del telefono.

##### Bound Services
>[!info]
>Vengono eseguiti perché ***un'altra app ha affermato che desidera usufruire*** del servizio, chiamando `bindService()`.

Il sistema quindi sa che esiste una dipendenza tra questi processi, quindi se il processo $A$ è associato a un servizio nel processo $B$, sa che ***deve mantenere il processo*** $B$ in ***esecuzione*** per $A$.

#### Broadcast Receivers
>[!definizione]
>Un ***Broadcast Receiver*** è un componente che consente al sistema di inviare eventi all'app *al di fuori di un normale flusso utente*, consentendo all'app di rispondere agli annunci di trasmissione a livello di sistema.

Il sistema può definire broadcast anche alle app che ***non sono attualmente in esecuzione***.

>[!info] Molti broadcast provengono dal sistema
>Per esempio un broadcast annuncia che la ***batteria è scarica***.

Anche le app ***possono avviare broadcast***.
- Ad esempio per far sapere ad altre app che alcuni dati sono stati scaricati sul dispositivo e sono disponibili per l'uso.

>[!caution] Nota
>Anche se i broadcast receivers non visualizzano un'interfaccia, possono creare ***status bar notification*** per avvisare l'utente quando si verifica un evento.

>[!todo] Un broadcast receiver viene implementato come sottoclasse di `BroadcastReceiver` e ogni trasmissione viene erogata come oggetto `Intent`.

#### Content Providers
>[!definizione]
>Un ***content provider*** gestisce un set condiviso di dati dell'app che è possibile archiviare in un qualsiasi persistent storage location a cui l'app può accedere.

Tramite il content provider, altre app possono eseguire query o modificare i dati ***se il provider di contenuti lo consente***.

> Esempio
- Il sistema android fornisce un *content provider* che gestisce le informazioni di contatto dell'utente.
	- Una qualsiasi app con le **autorizzazioni appropriate** può richiedere al fornitori di contenuti di leggere e scrivere informazioni su una determinata persona.

>[!done] Per il sistema un content provider è un'entry point in un'app per la pubblicazione di dati

>[!todo] Un content provider è implementato come sottoclasse di `ContentProvider` e deve implementare un set standard di `API` che consenta ad altre app di eseguire transazioni

### Intent
> Per attivare *activities*, *services* e *broadcast receivers*, si usa un messaggio asincrono chiamato ***intent***.

>[!definizione]
>Un ***intent*** descrive un'azione da eseguire, inclusi i dati su cui agire, la categoria del componente che dovrebbe eseguire l'azione e altre istruzioni.

>[!todo] Un intent viene creato con un oggetto `Intent` , che definisce un messaggio per attivare un componente specifico (explicit intent) o un tipo specifico di componente (implicit intent)

> Per [[#Activities]] e [[#Services]], un *intent* definisce l'azione da eseguire.
- Può specificare l'[[Indirizzamento#In Internet|URI]] dei dati su cui agire.
- In alcuni casi, è possibile avviare un'**activity** per ricevere un risultato, nel qual caso l'attività restituisce anche il risultato in un **intent**.

> Per [[#Broadcast Receivers]] l'*intent* definisce semplicemente l'**annuncio da trasmettere**.
- Una trasmissione che indica che la batteria è scarica, include solo una stringa di azione nota.

#### Intent e Content Providers
> A differenza delle altre componenti i content provider non vengono attivati dagli intent.

Vengono attivati quando ***vengono scelti come target*** da una richiesta di un `ContentResolver`.