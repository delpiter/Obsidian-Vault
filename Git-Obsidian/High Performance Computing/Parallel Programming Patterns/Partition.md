>[!tip] Pattern
>Il ***pattern partition*** consiste nel dividere il *dominio dei dati* in regioni solitamente 
>[[Insiemi Numerici#Insiemi Separati|disgiunte]] (potrebbe essere necessario avere insiemi **non disgiunti**) chiamate ***partizioni*** (*partition*).

Ogni *processore* opera su una singola partizione.

Questo pattern è particolarmente utile quanto l'applicazione esibisce la "***locality of reference***":
- Quando i processori necessitano di poca o nessuna comunicazione con gli altri e utilizzano solo i *dati locali*.
