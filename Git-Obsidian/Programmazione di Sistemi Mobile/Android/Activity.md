![[Fondamenti#Activities]]

Un'activity fornisce la finestra in cui l'app ***disegna la sua interfaccia utente***.
- Questa finestra in genere riempe lo schermo, ma può essere più piccola e fluttuare sopra ad altre finestre.

> In generale un'activity in un'app viene specificata come ***main activity***.
- Ovvero è la prima che viene *visualizzata all'avvio*.

![[Manifest#Manifest e Activity]]

## Il ciclo di vita di un'Activity
---
>Nel corso di vita, un'activity passa attraverso una serie di stati.

Si utilizzano delle **callback** per gestire le ***transizioni tra gli stati***.

>[!info]
>La classe `{kotlin icon} Activity` fornisce una serie di **callback** che consentono all'attività id sapere che il suo ***stato è cambiato***.

Il flusso è gestito interamente dal sistema operativo, il programmatore, semplicemente si "***aggancia***" alle callback per gestire i cambiamenti di stati.

![[attachements/ActivityLifeCycle.png]]

Le callback permettono di gestire i casi in cui avviene un evento che interrompe il normale flusso di utilizzo.

>[!important] Nota Bene
>Indipendentemente dall'evento di creazione, in cui scegli di eseguire un'operazione di *inizializzazione*, assicurati di usare l'***evento del ciclo di vita corrispondente per rilasciare la risorsa***.
### Creazione
> La creazione dell'activity è composta da 3 *callbacks* ordinate.

>[!abstract] `{kt icon} onCreate()`
- Viene creata l'activity, il programmatore deve assegnare le **configurazioni di base** e definire quale sarà il *layout*.
- Si esegue la logica di avvio dell'applicazione di base, che deve avvenire ***una sola volta***.

>[!tip] `{kt icon} onStart()`
- Segue l'`{kt icon} onCreate()`
- È il momento in cui l'*activity diventa visibile*.
- Si attivano le funzionalità e i servizi che offrono informazioni all'utente.

>[!failure] `{kt icon} onResume()`
- Segue l'`{kt icon} onStart()`.
- L'activity diventa la destinataria di ***tutti gli input dell'utente***.
- Le funzionalità principali di un'app legate al ciclo di vita sono implementate nel metodo `{kt icon} onResume()`.
- L'app rimane in questo stato finché non succede qualcosa che distoglie l'attenzione dall'app (es. Ricezione di una telefonata).
### Shut Down
> Lo stato di running comprende 3 ulteriori *callback*.

>[!help] `{kt icon} onPause()`
- Chiamata quando un'altra activity diventa di "*foreground*" (es. Ricezione di una telefonata), ***perdendo lo stato attivo***.
- Tecnicamente l'activity è ancora parzialmente visibile.
- Operazione opposta all'`{kt icon} onResume()`.
- Una volta terminata l'esecuzione, il callback successivo è `{kt icon} onStop()` o `{kt icon} onResume()`.
- L'esecuzione `{kt icon} onPause()` è molto breve, per questo ***NON*** la si dovrebbe usare per operazioni di salvataggio.

>[!missing] `{kt icon} onStop()`
- Chiamata quando l'activity non è più visibile all'utente (Attività distrutta, inizia una nuova attività, etc...).
- Operazione opposta all'`{kt icon} onStart()`.
- Il callback successivo è `{kt icon} onRestart()` se l'attività sta riavendo il focus, o `{kt icon} onDestroy()` se sta terminando.

>[!fail] `{kt icon} onDestroy()`
- Chiamata dal sistema *prima* che un'activity ***venga distrutta***.
- Operazione opposta all'`{kt icon} onCreate()`.
- Implementanto, generalmente per garantire che ***tutte le risorse di un'attività vengano rilasciate***.
- Chiamata quando: l'*attività sta finendo* o il sistema sta temporaneamente distruggendo l'attività a causa di una *modifica di configurazione*.

## Main Activity
---
>[!help] Info
>La ***main activity*** è l'entry point principale, l'activity che si apre quando l'utente esegue l'app attraverso l'icona.

```xml title:manifest
<activity android:name="MainActivity" android:exported="true">
	<intent-filter>
		<action android:name="android.intent.action.MAIN" />
		<category android:name="android.intent.category.LAUNCHER" />
	</intent-filter>
</activity>
```

L'`action_main` è l'azione che indica che è l'entry point principale e che ***non si aspetta intent data***.

`Category_Launcher` è la categoria è la categoria che indica che activity icon dovrebbe essere posizionata nel ***system app launcher***.
- Se l'elemento `{xml icon} <activity>` non specifica un'icona `icon`, il sistema usa l'icona dall'elemento `{xml icon} <application>`.
