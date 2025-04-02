## Introduzione
---
>[!question] In che contesto vivono i processi avviati dall'utente?

>[!info] Terminale di Controllo
>Quando accediamo ad una macchina *linux* lo si fa per tramite del ***terminale di controllo***
>>[!note] Bash Interattiva
>>A questo terminale viene legata la ***bash interattiva***,
>>- Il processo principale legato al *terminale di controllo* da cui nascono tutti gli altri ***processi figli***
>
>>[!warning] Attenzione
>>Se il *terminale di controllo* viene terminato il sistema operativo ***termina*** tutti i sottoprocessi di quel terminale

È possibile "*staccare*" un qualsiasi processo dal proprio ***terminale di controllo***

>[!tldr] Job Control
>Permette di portare i processi da *background* a *foreground* e viceversa

Il comando `{sh} jobs` stampa a video tutti i ***jobs in esecuzione*** 
### Processi in Foreground
>[!definizione] Definizione
>Sono i processi che "***controllano***" il terminale dal quale sono stati lanciati
>- Ad ogni istante *un solo processo* è in ***foreground***

#### Combinazione di Tasti
>[!abstract] `^Z`
>Con la combinazione di tasti `CTRL + Z` viene ***sospeso*** il processo in *foreground*

>[!caution] `^C`
>Con la combinazione di tasti `CTRL + C` viene ***terminato*** il processo in *foreground*


### Processi in Background
>[!definizione] Definizione
>Vengono ***eseguiti in parallelo*** rispetto all'esecuzione della bash
>- *Consentono* alla bash che li ha lanciati di leggere ed eseguire altri comandi e programmi
>
>>[!note] Condivisione
>>I processi in *background* usano una copia dei [[File Descriptor]] della bash che li ha lanciati
>>- In particolare condividono `stdin`, `stdout`, `stderr`

>[!abstract] Jobs
>Vengono definiti ***Jobs*** i processi in *background* o *sospesi* ***solo figli*** di quella shell
>- I "nipoti" non sono ***Jobs***

Con il carattere `&` è possibile lanciare un processo direttamente in *background*
- All'inizio dell'esecuzione del Job in *background*, la prima cosa stampata dal processo ***figlio*** è il ***job identifier*** seguito dal ***process identifier***
- Alla fine dell'esecuzione verrà stampato "***Done***"
	- `[JobIdentifier]<+/- > Done`
		- `+` Se il processo era il più recente messo in esecuzione
		- `-` Se era il penultimo

```sh title:Esempio
echo "ciao" &
# [1] 1111
# ciao
# [1]+ Done
```

##### Disown
>[!note] Comando disown
>Il comando `disown` lanciato dalla shell interattiva, *sgancia* dalla shell l'ultimo job messo in ***background***
>- `-r` sgancia tutti i job in esecuzione
>- `-a` sgancia tutti i job in esecuzione e sospesi
>- `%jobid` sgancia il job specificato

