>[!tldr] Idea
>Determinare il ***numero delle soluzioni*** e *separare* ogni soluzione, cioè individuare per ogni soluzione, un *intervallo* che non ne contenga altre.

## Teorema degli Zeri
---
![[Limiti#Teorema degli Zeri]]

>[!hint] Ordine di Convergenza
>La relazione $b_{n}-a_{n} = \displaystyle{\frac{b_{0}-a_{0}}{2^n}}$ può essere usata per dimostrare che il metodo [[Ordine di Convergenza|converge con ordine di convergenza]] $p=1$ e $x=\frac{1}{2}$ 

***Infatti***:
$$
|e_{k}|=|x_{k}-\alpha|\leq \frac{1}{2}|b_{k}-a_{k}|=\frac{1}{2^{k+1}}|b_{0}-a_{0}|
$$
$$
|e_{k+1}|=|x_{k+1}-\alpha|\leq \frac{1}{2}|b_{k+1}-a_{k+1}|=\frac{1}{2^{k+2}}|b_{0}-a_{0}|
$$
Da cui risulta che:
$$
\frac{|e_{k+1}|}{|e_{k}|}\approx \frac{1}{2}
$$

### Precisione
>Supponiamo che ci vogliano $j$ iterazioni per ottenere una cifra significativa esatta nella soluzione.

$$
|e_{k+j}|\approx \frac{1}{10}|e_{k}|
$$
>[!question] Vogliamo stimare il numero di iterazioni $j$

$$
|e_{k+j}|\leq \frac{1}{2^{k+j+1}}|b_{0}-a_{0}|\approx \frac{1}{10}\cdot \frac{1}{2^{k+1}}|b_{0}-a_{0}|\implies \frac{1}{2^j}\approx \frac{1}{10}\implies j\approx \log_{2}(10)\approx 3.32
$$

### Criterio di Arresto
> Si basa sull'errore al passo $k$.

$$
\left| \displaystyle{\frac{b-a}{2^{k+1}}} \right|\leq \varepsilon
$$
>[!todo] Possiamo stimare quante iterazioni sono necessarie per raggiungere la precisione prefissata.

$$
2^{k+1}\geq \displaystyle{\frac{b-a}{\varepsilon}}\implies k\geq\log_{2}\left(\frac{b-a}{\varepsilon} \right)-1 \implies k= \left\lceil  \log_{2}\left( \frac{b-a}{\varepsilon} \right) -1\right\rceil
$$

>[!done] Conclusione
>Il metodo di bisezione è un metodo di ***sicura ma lenta convergenza***.
