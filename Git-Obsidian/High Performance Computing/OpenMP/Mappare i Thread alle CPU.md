## CPU Eterogenee
---
>L'esecuzione di un programma in una [[../../Architettura degli Elaboratori/Architettura del Calcolatore/La CPU|CPU]] [[../../Architettura degli Elaboratori/Architetture a Confronto/Architetture Parallele#Parallelismo nel Chip|eterogenea]] potrebbe essere altamente alterata in base a dove viene eseguita.

>[!info] Processori Omogenei
>Per ***processori omogenei*** l'opzione di default va bene.

Anche se è presente l'[[../Architetture Parallele#Hardware Multithreading|hyperthreading]]:
- I threads sono spalmati prima sui core fisici e poi sui *core virtuali*.

>[!warning] Processori Eterogenei

Per *processori eterogenei* è necessario specificare quali `CPU` il programma deve utilizzare.

> Variabili d'ambiente di [[OpenMP]]:

>[!abstract] `{sh icon} OMP_PLACES`
> Specifica ***quali processori*** verranno utilizzati dal programma.

> ***Esempio***: processore con $12$ core `[0,11]`
- `{sh icon} OMP_PLACES="0,1,2,3"`
	- Assegna il primo thread alla `CPU 0`, il secondo alla `CPU 1`, ...
	- Se ci sono più di 4 thread il quinto viene assegnato alla `CPU 0`.
- Espressione ***equivalente***: `{sh icon} OMP_PLACES="0:4"`
	- *Prendo 4 core partendo da 0*.
- `{sh icon} OMP_PLACES="0:4:2"`
	- L'ultimo parametro indica il "***passo***"
	- Equivalente a: `{sh icon} OMP_PLACES="0,2,4,6"`


`{sh icon} OMP_PROC_BIND`
- Previene che lo [[../../Sistemi Operativi/Teoria/7 - Scheduler|scheduler]] del *sistema operativo* **migri** i threads a una `CPU` diversa.

`{sh icon} OMP_DISPLAY_ENV=true`
- Stampa tutti i valori delle variabili d'ambiente di ***OpenMP***.

