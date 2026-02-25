>[!definizione] Android
>"The ***Android Manifest*** is an [[Markup Language#Metamarkup e XML|XML]] file which contains important metadata about the Android app.

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
>Gli intent filter permettono di eseguire un'acivity sfruttando richieste sia `explicit` che `implicit`.

> Esempio:
- `explicit`: Richiesta al sistema di aprire l'attività ***send-email con gmail***.
- `implicit`: Richiesta al sistema di aprire l'attività ***send-email con una qualsiasi activity che può svolgere il lavoro***.

Questi *filter* si dichiarano nel manifest, all'***interno dell'elemento activity***.

```xml
<activity android:name=".ExampleActivity" android:icon="@drawable/app_icon">
	<intent-filter>
		<action android:name="android.intent.action.SEND" />
		<category android:name="android.intent.category.DEFAULT" />
		<data android:mimeType="text/plain" />
	</intent-filter>
</activity>
```

Per chiamare l'activity in [[Linguaggio Kotlin]] occorre fare:
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
