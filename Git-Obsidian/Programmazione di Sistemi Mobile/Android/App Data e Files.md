> [[Introduzione ad Android|Android]] utilizza un file system simile a quelli basati su disco di altre piattaforme.

Il sistema offre diverse opzioni per salvare i dati dell'app.
- App-Specific Storage
- Shared Storage
- Preferences
- Database

## App Specific Storage
---
>[!hint] Info
>Archivia i ***file destinati esclusivamente all'uso dell'app***, in directory dedicate all'interno di un volume di archiviazione interno.

Solo l'app è in grado di accedere a questi dati, tutte le *altre applicazioni non hanno accesso a questo storage*.

>[!important] Attenzione
- Se l'app viene disinstallata, i dati salvati in questo archivio **verranno persi**.

## Shared Storage
---
>[!hint] Info
>Archivia i file che l'app intende ***condividere*** con altre app.

> Es.
- File multimediali, documenti, etc...

## Preferences
---
>[!hint] Info
>Archivia ***dati primitivi***, privati in coppie *chiave-valore*.

## Database
---
