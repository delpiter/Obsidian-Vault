>[!info]  `~` Expansion
>La *tilde expansion* è una [[Terminale Unix#Espansioni|espansione]] che riguarda una stringa che è iniziata dal carattere: `~`
>È una espansione che riguarda diverse ***tipologie*** di stringhe

#### Senza alcun Username
>[!abstract] Utilizzo
>Se usato senza alcun *username* la `~` viene espansa con la directory home dell'**utente corrente**

1. Carattere `~` isolato
	- Sostituisce la tilde con `/home/username`
2. Carattere `~` seguito da *slash* seguito da *altri caratteri*
	- Se i caratteri *corrispondono ad una directory*, permette di espandere il comando con il ***percorso assoluto*** della directory

#### Con un Username
>[!abstract] Utilizzo
>Se usato con uno *username* la `~` viene espansa con la directory home dell'**utente specificato**

In questo caso `~` + `username` viene sostituito dal **percorso assoluto** della home directory dell'*utente specificato*


>[!warning] Se l'utente non esiste, la bash non esegue alcuna modifica sul comando scritto