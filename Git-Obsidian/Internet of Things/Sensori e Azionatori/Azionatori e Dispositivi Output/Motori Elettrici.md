## Motori
---
>[!info]
> I *motori elettrici* sono macchine elettriche che convertono ***energia elettrica*** in ***energia meccanica***.

Ogni motore ha due parti principali:
- *Stator*: Parte fissa/statica.
- *Rotore*: Parte mobile.

>[!caution] Funzionamento

I due componenti generano un [[Magnetismo#Campo Magnetico e Quantità di Moto|campo magnetico]] che causa il ***movimento del rotore***.

> Tipologie di Motori Elettrici
- ***Direct Current Motors***.
	- Usati in progetti dove il motore deve avere:
		- Rotazione continua
		- Movimento di $360^{\circ}$
		- Alta velocità
		- Controllo di velocità angolare
	- [[Campo Magnetico e Correnti Elettriche#Spira percorsa da Corrente|Funzionamento]].
- ***Stepper Motors***.
	- Motore "*senza spazzole*" dove la rotazione è divisa in un **grande numero di step**. 
- ***Servo Motors***.
	- Come lo stepper ma con un *controllo più fine* dell'asse, differenze:
		- La posizione è assoluta, non relativa a quella corrente.
		- Il range di movimento è $180^{\circ}$.
	- Più facile da programmare.

>[!question] Come controllare il servo motor?

Il controllo è fatto inviando un ***flusso di impulsi digitali*** ad una frequenza specifica.
- La durata del pulso determina l'***angolo di rotazione***.
	- Tipicamente vanno da $1ms$ ($-90^{\circ}$) a $2ms$ ($90^{\circ}$).
	- Più è largo l'impulso più è largo l'angolo di movimento
	- In [[Sensori e Azionatori#Caratteristiche Statiche|scala lineare]].