## Algoritmi Greedy
---
>[!info] Definizione
>Un ***algoritmo greedy*** fa sempre la scelta che sul momento sembra la migliore
>L'algoritmo fa una serie di ***scelte locali ottime*** nella speranza che esse *conducano* ad una ***soluzione ottimale globale***

>[!warning] Un algoritmo *Greedy* non sempre conduce ad una soluzione ottimale

Cerchiamo la soluzione di un [[../../Definizioni/Definizioni_Algoritmi#Problema di Ottimizzazione|problema di ottimizzazione]]
- La ***ricerca esaustiva è impraticabile***

Si cerca di costruire una soluzione o di migliorare una esistente facendo una ***serie di aggiustamenti successivi***
- Ogni aggiustamento (***mossa***) è determinata solo sulla base di ***criteri locali***

>[!caution] Greedy
>Si affronta il problema completo *costruendo* la soluzione ***un pezzo alla volta***
>- Non si hanno ***soluzioni di sottoproblemi*** ma ***sottosoluzioni di un problema***

>[!done] Se si è fortunati
>Una sequenza di scelte localmente ottime può portare all'ottimo globale
>In questo caso il problema ha la ***Greedy Choice Property***

>[!fail] A volte gli algoritmi greedy non trovano la soluzione ottima
>La ***struttura del problema*** è tale per cui *nessun algoritmo greedy* può **garantire** di trovare sempre la ***soluzione ottima***

D'altro canto, algoritmi *non greedy* che garantiscono di trovarla hanno un ***costo computazionale proibitivo***
- In questi casi è necessario utilizzare [[../../Definizioni/Definizioni_Algoritmi#Algoritmi Euristici|Algoritmi Euristici]]

Esempio: [[../../Definizioni/Definizioni_Algoritmi#Traveling Salesman Problem|TSP]]

### Scelte Greedy
>[!Proprietà della Scelta Greedy]
>È possibile assemblare una ***soluzione globale ottimale*** facendo delle ***scelte locali ottimali***

In un algoritmo ***greedy***:
- La prossima scelta *potrebbe* ***dipendere*** dalle *scelte precedenti*
- La prossima scelta *non può* ***dipendere*** da *scelte future*

>[!done] Un algoritmo greedy fa la prima scelta prima di risolvere qualsiasi sottoproblema

È necessario dimostrare che una *scelta greedy* ad ogni step ***produca una soluzione ottimale***

#### Dimostrazione Tipica
La *dimostrazione tipica* esamina una ***soluzione ottimale globale*** di un sotto problema
- Successivamente mostra come ***modificare la soluzione*** sostituendo la *scelta greedy* con un'altra scelta ottenendo un *sotto problema simile ma più piccolo*

