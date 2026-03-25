> [[Introduzione ad Android|Android]] utilizza un file system simile a quelli basati su disco di altre piattaforme.

Il sistema offre diverse opzioni per salvare i dati dell'app.
- App-Specific Storage
- Shared Storage
- Preferences
- Database

La scelta del tipo di storage da utilizzare dipende in base agli ***specifici bisogni***.

>[!question] Quanto spazio richiedono i dati?

>[!question] Quanto deve essere affidabile l'accesso ai dati?

>[!question] Che tipo di dati devi archiviare?

>[!question] I dati devono essere privati alla tua app?


## Categorie di Storage Location
---
>[!abstract] Internal Storage
>Lo ***storage interno*** è sempre disponibile anche se spesso più piccola di dimensione rispetto a quella *esterna*.

>[!caution] External Storage
>Lo storage esterno è un volume rimuovibile come `SD` card.

Sono rappresentati in android usando il *path*: `/sdcard`.

---

Le app vengono archiviate nella ***memoria interna*** per impostazione *predefinita*.
- Se le dimensioni dell'`APK` sono molto grandi si può indicare una preferenza nel [[Manifest]] dell'app per installare l'app nella ***memoria esterna***.

```xml
<mainfest
    android:installLocation="preferExternal">
	...
</manifest>
```

Per ogni app, android, fornisce due directory interne accessibili solo dall'app stessa:
- Una per contenere file persistenti (`filesDir`).
- Una per contenere l'app [[Cache]] (`cacheDir`).

>[!done] Pro
- Altre app non possono accedere a queste directory.

>[!fail] Contro
- Lo spazio riservato è piccolo.

Per accedere e memorizzare file persistenti si può usare la `File` `API`.
```kt
// filesDir
val file = File(context.filesDir, fileName)

// cacheDir
File.createTempFile(fileName, null, context.cacheDir)
```

Se non c'è abbastanza spazio nella memoria interna, si può usare quella esterna, android fornisce altre due directory:
- Una per contenere file persistenti (`externalFilesDir`).
- Una per contenere l'app cache (`externalCacheDir`).

>[!warning] Attenzione
>I file in queste directory ***non sono garantiti*** come *accessibili*.
>La scheda esterna potrebbe essere estratta dal dispositivo.

>[!check] Nota sui contenuti multimediali
> È importante utilizzare *nomi di directory* forniti da `API` come `DIRECTORY_PICTURES`.
> Questi nomi assicurano che i file siano **trattati correttamente dal sistema**.


### Permessi di accesso
> Android definisce le seguenti autorizzazione per l'accesso in lettura e scrittura alla memoria esterna:

- `READ_EXTERNAL_STORAGE`
- `WRITE_EXTERNAL_STORAGE`
- `MANAGE_EXTERNAL_STORAGE`

Nelle versioni vecchie di android le app **dovevano dichiarare** l'autorizzazione `READ_EXTERNAL_STORAGE` per accedere a qualsiasi file al di fuori delle directory specifiche dell'app.
- Le versioni più recenti si basano sullo ***scope*** di un file.

Questo modello di archiviazione basato sullo scope migliora la privacy dell'utente.

#### Scoped Storage
> Per offrire agli utenti un maggiore controllo sui propri file, di default le app destinate ad android `10+` hanno ***scoped access*** alla memoria esterna.

Queste app hanno accesso solo alla [[#App Specific Storage]] su memoria esterna.

>[!help] Scope
> Divide i [[Permessi|permessi]] nei seguenti livelli di accesso:
> - Accesso ***read and write*** ai propri file senza necessità di permessi.
> - Accesso in ***lettura*** ai media delle altre app con il permesso `READ_EXTERNAL_STORAGE`'.
> - Accesso in ***scrittura*** ai media delle altre app, solo con il *diretto consenso dell'utente* (ad eccezione della galleria di sistema).
> - ***Nessun accesso*** alle directory di storage esterno di altre app.
## App Specific Storage
---
>[!hint] Info
>Archivia i ***file destinati esclusivamente all'uso dell'app***, in directory dedicate all'interno di un volume di archiviazione interno.

Solo l'app è in grado di accedere a questi dati, tutte le *altre applicazioni non hanno accesso a questo storage*.

>[!important] Attenzione
- Se l'app viene disinstallata, i dati salvati in questo archivio **verranno persi**.

>[!help] Sicurezza
>Per una maggiore sicurezza è possibile utilizzare la ***Security Library*** per criptare i file.

## Shared Storage
---
>[!hint] Info
>Archivia i file che l'app intende ***condividere*** con altre app.

> Es.
- File multimediali, documenti, etc...

Android fornisce `API` per l'archiviazione e l'accesso ai seguenti tipi di dati condivisibili:
- Contenuti Multimediali (`MediaStore`).
- Documenti e altri file (`StorageAccessFramework`).
- Dataset (`BlobStoraManager`).

### Media
>[!help] Media Store
>Il framework fornisce un indice ottimizzato nelle raccolte multimediali, chiamato ***Media Store***, che consente di recuperare e aggiornare più facilmente questi media.

Anche dopo la disinstallazione dell'app questi file ***rimangono sul dispositivo***.

Per interagire con *media store*, si può utilizzare un oggetto `ContentResolver`:

> Il sistema esegue automaticamente la scansione del volume di archiviazione esterno e **aggiunge** file multimediali alle seguenti *raccolte ben definite*:
- `Images`: Fotografie e screenshot archiviati nelle directory `DCIM/` e `Pictures/`, vengono aggiunti nella tabella `MediaStore.Images`
- `Videos`: Archiviati nelle directories `DCIM/`, `Movies/` e `Pictures/`, vengono aggiunti nella tabella `MediaStore.Video`.
- `Audio Files`: Memorizzati nelle directory `Alarms/`, `Audiobooks/`, `Music/`, `Notifications/`, `Podcasts/` e `Ringtones`, vengono aggiunti alla tabella `MediaStore.Audio`.
- `Downloaded Files`: File archiviati nella directory `Downloads/` disponibili (da android $10+$) nella tabella `MediaStore.Downloads`.

Il media store include anche una raccolta chiamata `MediaStore.Files`.
- Il contenuto dipende dal fatto che l'app utilizzi l'archiviazione [[#Scoped Storage|scoped]].
- Se l'archiviazione con scope è abilitata la raccolta mostra solo le foto, i video e i file ***creati dall'app***.


## Preferences
---
>[!hint] Info
>Archivia ***dati primitivi***, privati in coppie *chiave-valore*.

## Database
---
