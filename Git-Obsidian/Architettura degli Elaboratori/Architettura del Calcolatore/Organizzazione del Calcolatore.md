>*Un calcolatore digitale è un sistema composta da **processori** **memorie** e **dispositivi di input/output** collegati tra loro*

![[Von Neumann.png]]
- Questa *organizzazione*, con l'unica differenza del ***bus***, è uguale a quella della macchina di [[Storia dei Calcolatori#IAS - 1952|Von Neumann]] 
- Organizzazione detta: ***bus oriented***

>[!info] BUS
>Un **bus** è un insieme di *connessioni elettriche* ***parallele*** utilizzate per trasportare tutte le informazioni da un componente all'atro

## L'architettura di Von Neumann
---
![[VonNeumannArchitecture.png]]

>[!tldr] Idea
>La grande intuizione fu quella di utilizzare la **memoria** non solo per i dati ma ***anche per i programmi***
>- Potevano essere *caricati* in ***memoria*** con un lettore di schede evitando complesse e dispendiose *configurazioni*  con **interruttori e cavi**

***Programmi*** e ***Dati*** al tempo di esecuzione sono caricati in memoria

> *Componenti*:
- Un processore
	- Una `ALU`
	- Una serie di *registri generali* (contengono **input** e **output**)
	- *Registri Speciali* (`PC`, `IR`, etc...)
	- Una ***unità di controllo***
- Una memoria
- Un **Bus** che collega memoria e processore
