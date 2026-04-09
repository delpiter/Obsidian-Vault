>[!definizione] Android
>"The ***Android Manifest*** is an [[../../Tecnologie Web/HTML/Markup Language#Metamarkup e XML|XML]] file which contains important metadata about the Android app.

Ogni app project [[Introduzione ad Android|android]] deve avere un file `AndroidManifest.xml` nella radice del progetto.

```xml
<manifest ... >
    <application ... >
        <activity android:name="com.example.myapp.MainActivity" ... >
        </activity>
    </application>
</manifest>
```

Il **manifest** descrive le informazioni essenziali sull'app per:
- Strumenti di compilazione di **android**.
- Sistema operativo android.
- Google Play.

> Il file manifest ***deve dichiarare***:
- I componenti dell'app ([[Activity]], services, broadcast receiver e content provider #addLink).
- Le ***autorizzazioni*** #addLink necessarie all'app per accedere a parti protette del sistema o altre app.
- Le funzionalità hardware e software *richieste dall'app*.
## Manifest e Activity
---
> Ogni ***activity*** è solo vagamente legata alle altre activity.

Le activity possono avviare activity appartenenti ad altre app.

>[!summary] Per usare le activity nell'app, si devono registrare le relative informazioni nel ***manifest dell'app***

```xml title:"Activity Declaration"
<manifest ... >
    <application ... >
        <activity android:name=".ExampleActivity"/>
    </application>
</manifest>
```

- Il nome è l'unico attributo richiesto, ma ce ne sono diversi.

### Intent Filter
>[!info]
>Gli [[Intent]] ***filter*** permettono di eseguire un'acivity sfruttando richieste sia `explicit` che `implicit`.

> Esempio:
- `explicit`: Richiesta al sistema di aprire l'attività ***send-email con gmail***.
- `implicit`: Richiesta al sistema di aprire l'attività ***send-email con una qualsiasi activity che può svolgere il lavoro***.

>[!danger] Se non si dichiarano intent filter per un'activity, l'activity può essere avviata **solo** con *explicit intent*.

Questi *filter* si dichiarano nel manifest, all'***interno dell'elemento activity***.
Un componente dell'app deve dichiarare filtri separati per *ogni processo univoco che può svolgere*.
- Es: Un'attività di un'app della galleria può avere due filtri:
	- Visualizzazione dell'immagine
	- Modifica dell'immagine

```xml
<activity android:name=".ExampleActivity" android:icon="@drawable/app_icon">
	<intent-filter>
		<action android:name="android.intent.action.SEND" />
		<category android:name="android.intent.category.DEFAULT" />
		<data android:mimeType="text/plain" />
	</intent-filter>
</activity>
```

Per chiamare l'activity in [[Kotlin/Linguaggio Kotlin]] occorre fare:
```kt
val sendIntent = Intent().apply{
	action = Intent.ACTION_SEND
	type = "tect/plain"
	putExtra(Intent.EXTRA_TEXT, textMessage)
}
startActivity(sendIntent)
```

Nell'esempio, dichiariamo che l'app può ricevere richieste di ***invio di dati di tipo testuale***.
- Si usano i tag `{xml icon} <activity>` del *manifest* per controllare quali app **possono avviare una determinata activity**.

>[!important] Un'activity non può avviare un'altra activity a meno che entrambe le attività non dispongano delle ***stesse autorizzazioni***.

#### Package Visibility
>[!important] Importante
> Con android `11` sono state introdotte ***nuove restrizioni relative alla visibilità***.

Non è più possibile interagire direttamente con la maggior parte di package esterni.

> Soluzione
- Utilizzare un element `{xml icon} query` nel `manifest.xml`

```xml
<queries> 
	<intent> 
		<action android:name="android.intent.action.VIEW" /> 
		<category android:name="android.intent.category.BROWSABLE"/> 
		<data android:scheme="https" />
	</intent>
</queries>
```

L'elemento queries permette di filtrare i risultati dei metodi del `PackageManager` che restituiscono risultati relativi ad altre app.
#### Test
>[!todo] Test di Action

> Un intent filter può dichiarare ***zero o più elementi azione***.

Per **superare il filtro**, l'azione specificata nell'oggetto *intent* deve fare match con almeno una azione.

>[!summary] Test di Category

> Un intent filter può dichiarare ***zero o più elementi category***.

Per superare il filtro, ogni categoria nell'oggetto, deve corrispondere a una categoria nel filtro.

>[!Test di Data]

> Un intent filter può dichiarare ***zero o più elementi data***.

Ogni elemento può specificare una struttura `URI` e un [[../../Reti/Application Layer/Posta Elettronica#MIME|MIME Type]].
Ogni parte dell'`URI` è un attributo separato:
- `<scheme>://<host>:<port>/<path>`
- Es. `content://com.example.project:200/folder/subfolder/etc`

> ***Regole***
1. Un intent che non contiene né `URI` né un `MIME` *supera il test solo se* il filtro non specifica `URI` o `MIME`.
2. Un intent che contiene solo un `URI` *supera il test solo se* corrisponde al formato `URI` del filtro *e se* allo stesso modo il filtro **non** specifica un `MIME`.
3. Un intent che contiene solo un `MIME` *supera il test solo se* il filtro elenca lo stesso tipo `MIME` *e* **non** specifica un formato `URI`. 
4. Se un intent contiene sia un `URI` che un `MIME` (esplicito o inferibile dall'`URI`) passa la parte del tipo `MIME` solo se quel tipo corrisponde a un tipo elencato nel filtro, passa la parte `URI` se il suo `URI` corrisponde a un `URI` nel filtro.
>[!example] Esempi

```xml
<intent-filter>
  <data android:mimeType="image/*" />
  ...
</intent-filter>
```
- Dice ad android che il componente può ricevere image data da un content provider e visualizzarlo.

```xml
<intent-filter>
  <data android:scheme="http" android:mimeType="video/*" />
  ...
</intent-filter>
```
- Dice ad android che il componente può recuperare i dati video dalla rete per eseguire l'azione.

### Permission
> Il manifest deve contenere le autorizzazioni necessarie all'esecuzione di un'activity.

>[!example] Esempio
>La mia app vuole usare un'app chiamata **SocialApp** per condividere un post.

"**SocialApp**" deve esporre il seguente *manifest*.
```xml 
<manifest>
	<activity android:name="..." android:permission="com.google.socialapp.permission.SHARE_POST"\>
<manifest\>
```

La mia app deve contenere il seguente:
```xml
<manifest>
	<uses-permission android:name="com.google.socialapp.permission.SHARE_POST"\>
<manifest\>
```
