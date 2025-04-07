>Un [[Soluzione Numerica di Funzioni non Lineari|metodo numerico convergente]] genera una successione $\{ x_{k} \}$  di *iterati* che soddisfa: $\displaystyle\lim\limits_{k\to +\infty}x_{k}=\alpha$.

>[!warning]
>In un contesto di calcolo computazionale, non è possibile eseguire un ***numero infinito di passi***.
>>[!done] Conclusione
>>È necessario stabilire criteri per ***arrestare il procedimento iterativo***.

## Tipi di Condizioni
---
> Il processo viene arrestato all'iterato $k$ per il quale si verifica una delle condizioni.

>[!caution] Condizione Basata sul Valore
>Il processo viene ***arrestato*** se all'iterato $k$ vale:
>$$|f(x_{k})|<\varepsilon$$

>[!abstract] Condizione Basata sull'Incremento
>Il processo viene ***arrestato*** se all'iterato $k$ vale:
>$$|x_{k}-x_{k-1}|<\varepsilon$$

Utilizzando il controllo del valore della funzione nel punto $x_{k}$ come criterio di arresto si possono presentare due situazioni problematiche.

![[RestrictiveCase.png|500]]
- L'iterato $x_{k}$ è **vicino** a $x*$ anche se $|f(x_{k})|$ è *grande*.

![[OptimisticCase.png|500]]
- Il valore di $x_{k}$ è lontano da $x*$ ma $|f(x_{k})|$ è *piccolo*.

>[!done] Soluzione
>Un criterio d’arresto basato *sia* sul **controllo del valore** della funzione *sia* sul **controllo dell’incremento** risulta molto più affidabile.
>>[!quote] Criterio di Arresto Relativo
>>$$\displaystyle{\frac{|x_{k}-x_{k-1}|}{|x_{k}|}}$$