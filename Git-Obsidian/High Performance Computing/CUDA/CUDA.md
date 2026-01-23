## Compute Unified Device Architecture
---
>[!info]
>`CUDA` è una tecnologia proprietaria per la programmazione di [[Schede Grafiche|GPU]].
>- Espone un modello per la programmazione [[Il Design di Programmi Paralleli#Task Parallelism e Data Parallelism|data-parallel]].

> `OpenCL`
- `OpenCL` è una alternativa *open source* e portabile per la programmazione di `GPU` e `CPU`.
- È possibile "tradurre" il linguaggio `CUDA` in `OpenCL` attraverso dei ***transpiler***.
	- Le implementazioni sono però fino a $30\%$ più lente rispetto a `CUDA`.

>[!tldr] Idea
>`CUDA` separa il programma in due:
>- Un programma `CPU` (*host* program) che include le operazioni di `I/O`.
>- Un programma `GPU` (*device* program) che contiene le computazioni che devono essere eseguite dalla `GPU`.

Il caso più semplice di interazione tra *host program* e *device program* è la seguente:
1. L'***host program*** copia i dati di input nella memoria globale della `GPU`.
2. L'***host program*** chiama le funzioni del *device* per inizializzare i processi sulla `GPU`.
3. Copia dei risultati dalla memoria della `GPU` alla memoria della `CPU`.
### Terminologia
>[!abstract] Host
>L'***host*** è la `CPU` e la sua memoria (*host memory*).

>[!help] Device 
> Il ***device*** è la `GPU` e la propria memoria interna (*device memory*).

### Anatomia di una GPU
![[GPUAnatomy.png]]

>[!tip] Composizione
>La `GPU` è composta di numerosi "***streaming multiprocessor***" (`SM`), ciascuno di essi è composto da ulteriori "***streaming processor***" (`SP`).

>[!bug] Punto di vista del Programmatore

Dal punto di vista del programmatore la `GPU` è composta da:

> [[6 - Processi, Schedule e Thread|Thread]]
- I ***thread*** sono l'unità più piccola di lavoro.
- Eseguono tutti la stessa funzione [[3 - Livelli del Sistema Operativo#Kernel|kernel]].
- I ***thread*** sono raggruppati in `WARP` di $32$ per lo [[7 - Scheduler|scheduling]].

> ***Block***
- Un `Block` è una ***unità logica*** formata da un array `3D` di thread.
- Una sottoparte del lavoro che può essere eseguita in un qualsiasi ordine da un `SM`.
- Creata per *affrontare delle limitazioni* della `GPU` legate alla gestione della memoria.

>[!hint]
>I *thread* di un *blocco* possono fare cose che i thread di blocchi diversi non possono fare, come per esempio, ***condivisione di memoria***.

> ***Grid***
- Una `Grid` è un pezzo del lavoro che viene eseguita dalla `GPU`.
- È formata da un array `3D` di **Blocks**.
- Contiene un insieme di **Blocks** indipendenti che possono essere eseguiti in *qualsiasi ordine*.

Il programmatore ha accesso alla singola unità tramite:
- Id del blocco: `{c icon} BlockIdx.{x,y,z};`.
- Id del thread: `{c icon} ThreadIdx.{x,y,z};`

>[!done] Non è necessaria la gestione della potenza di calcolo

L'hardware è in grado di *schedulare* più thread rispetto ai core fisici con ***overhead praticamente nullo***.
