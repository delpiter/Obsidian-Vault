>Strategia risolutiva di problemi di grandi dimensioni

>[!info] Concetto Base
>Divido il problema in istanze sempre più piccole fino a che non ottengo *istanze* *banali*
>Risolvi tutti i problemi di *complessità banale*
>Combina tutte le **soluzioni ottenute**

### Divide Et Impera
>[!info] Dividi

Constato che la ***dimensione del problema*** è troppo grande per essere *risolta*, quindi:
- Divido l'istanza del problema in ***due o più istanze più semplici***

>[!tip] Risolvi

Passo [[../Programmazione/Funzioni/Recursive Functions|ricorsivo]]
- Utilizza la tecnica appena descritta per risolvere le *singole istanze di complessità banale*
- Chiamate anche ***sottoproblemi***

>[!done] Combina

Combina tutte le soluzioni trovate per i sottoproblemi in una singola soluzione per il ***problema originario***