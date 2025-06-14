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
##### Pseudo Codice
```pseudo
	\begin{algorithm}
	\caption{Metodo di Bisezione}
	\begin{algorithmic}
	\State $ \text{Poni } x_{k+1}=a_{k} +\displaystyle\frac{b_k-a_k}{2} $
	\If{$f(x_{k+1})\cdot f(a_{k})<0$}
	\State $a_{k+1}=a_k$
	\State $b_{k+1}=x_{k+1}$
	\EndIf
	\If{$ f(x_{k+1})\cdot f(b_{k})<0  $}
	  \State $ b_{k+1}=b_{k} $
	\State $ a_{k+1}=x_{k+1} $
	\If{$ f(x_{k+1}) =0 $}
   \State $ x_{k+1}=\alpha $
 \EndIf
 \EndIf
 \State $ k=k+1 $
	\end{algorithmic}
	\end{algorithm}
```

## Regula Falsi
---
> Miglioramento del metodo di bisezione.

>[!tldr] Idea
>Il concetto sarebbe quello di considerare anche i valori che la funzione *assume* negli ***estremi dell'intervallo***.

>Si considera come nuova approssimazione della soluzione la retta passante per $(a,f(a)), (b,f(b))$

$$
\begin{cases}
y-f(a)=\displaystyle{\frac{f(b)-f(a)}{b-a}}(x-a) \\
y=0
\end{cases}
$$
Da cui si ottiene:
- $x=a-f(a) \displaystyle{\frac{b-a}{f(b)-f(a)}}$

>[!info]
>Metodo a [[Ordine di Convergenza#Convergenza Locale e Globale|convergenza globale]], se l'intervallo è scelto in base al *segno della funzione*.
>È più veloce rispetto al metodo di bisezione. (convergenza [[Ordine di Convergenza#Ordini|superlineare]]).

>[!warning] Criterio di Arresto
>Il [[Criteri di Arresto|criterio di arresto]] basato sull'*ampiezza* dell'intervallo ***non è applicabile***.

#### Esempio
>[!example] Determinare lo zero di
>$$f(x)=x^3+4x^2-10$$
>Nell'intervallo $[a,b]=[-1,2]$.

```functionplot
---
title: 
xLabel: 
yLabel: 
bounds: [-1,2,-10,15]
disableZoom: true
grid: true
---
f(x)=x^3+4x^2-10
g(x)=7x
h(x)=12x-10
j(x)=17.694x - 21.389
```

### Pseudocodice
>Finché non risulta verificato il ***criterio di arresto***:
```pseudo
	\begin{algorithm}
	\caption{Regula Falsi}
	\begin{algorithmic}
\State $ \text{Poni}x_{k+1}=
a_{k}-f(a_{k})\cdot \displaystyle{\frac{b_{k}-a_{k}}{f(b_{k})-f(a_{k})}}$
\If{$f(x_{k+1})\cdot f(a_{k})<0$}
	\State $a_{k+1}=a_k$
	\State $b_{k+1}=x_{k+1}$
	\EndIf
	\If{$ f(x_{k+1})\cdot f(b_{k})<0  $}
	  \State $ b_{k+1}=b_{k} $
	\State $ a_{k+1}=x_{k+1} $
	\If{$ f(x_{k+1}) =0 $}
   \State $ x_{k+1}=\alpha $
 \EndIf
 \EndIf
 \State $ k=k+1 $
	\end{algorithmic}
	\end{algorithm}
```

## Metodi di Linearizzazione
---
>[!info]
>Data $f(x),x_{0},f(x_{0})$: si ***approssima*** la funzione con una retta per $(x_{0},f(x_{0}))$.
>$$y=f(x_{0})+m(x-x_{0})$$
>Si ottiene una versione *linearizzata* del problema $f(x)=0$.

$$\begin{cases}y=f(x_{0})+m(x-x_{0}) \\ y=0\end{cases}$$
- Da cui possiamo ottenere
$$
x_{1}=x_{0}-\frac{f(x_{0})}{m}
$$
>[!abstract] In Generale

$$x_{k+1}=x_{k}-\frac{f(x_{k})}{m_{k}}$$

>[!hint] Algoritmi
>A seconda della scelta di $m_{k}$ si ottengono:
>- ***Metodo delle Corde***.
>- ***Metodo delle Secanti e di Newton***.

### Metodo delle Corde
> Scegliamo un valore costante $m\neq 0$

>[!cite] Algoritmo
>Il metodo assume la forma
>$$x_{k+1}=x_{k}-\frac{f(x_{k})}{m}$$

Una scelta classica è quella di utilizzare il coefficiente angolare della retta che passa per i punti $(a,f(a)),(b,f(b))$.

$$
m=\frac{f(b)-f(a)}{b-a}
$$

Da cui otteniamo la formula:
$$
x_{k+1}=x_{k}-\displaystyle{\frac{b-a}{f(b)-f(a)}}f(x_{k})
$$

>[!example] Esempio

$$f(x)=x^3+4x^2-10$$
```functionplot
---
title: 
xLabel: 
yLabel: 
bounds: [-1,2,-10,15]
disableZoom: false
grid: true
---
f(x)=x^3+4x^2-10
g(x)=7x
h(x)=7x-10
j(x)=7x-8.563
```

### Metodo delle Secanti
>[!info]
>Il seguente metodo richiede ***due iterati iniziali*** (*input* del problema).
>L'**approssimazione** della funzione $f$ nell'intervallo $[x_{k-1},x_{k}]$ è la retta che passa per i punti: $(x_{k-1}),f(x_{k-1}),(x_{k},f(x_{k}))$ con *coefficiente angolare*:
>$$m_{k}=\frac{f(x_{k})-f(x_{k-1})}{x_{k}-x_{k-1}}$$

La retta calcolata interseca l'asse $x$ nel punto:
$$
x_{k+1}=x_{k}-f(x_{k}) \displaystyle{\frac{x_{k}-f(x_{k-1})}{f(x_{k})-f(x_{k-1})}}
$$

La convergenza del metodo è garantita se le approssimazioni $x_{0}$ e $x_{1}$ si scelgono abbastanza vicine alla soluzione.

>[!hint] Metodo a [[Ordine di Convergenza#Convergenza Locale e Globale|convergenza locale]]

- In tal caso la convergenza è ***superlineare*** ($p=\frac{1+\sqrt{ 5 }}{2}\approx1.618$)

### Metodo di Newton
>[!tldr] Idea
> Nel ***metodo di Newton*** ad ogni passo $k$ si considera la retta passante per il punto $(x_{k},f(x_{k}))$ e *tangente alla curva* $f(x)$, si determina il nuovo iterato come il punto di incontro tra la **retta** e l'*asse* delle $x$

Si pone $m_{k}=f'(x_{k})$, ottenendo:
$$
x_{k+1}=x_{k}-\frac{f(x_{k})}{f'(x_{k})}
$$
#### Ordine del Metodo di Newton
>[!abstract] ?
>Sia $\alpha$ una radice semplice di $f(x)$, cioè $f(\alpha)=0$ e $f'(\alpha)\neq 0$

> Consideriamo lo sviluppo del primo ordine di $f(x)$ in un intorno di $x_{k}$

$$
f(x)=f(x_{k})+(x-x_{k})f'(x_{k})+\frac{1}{2}(x-x_{k})^2f''(\zeta)
$$
Per un opportuno $\zeta$ compreso tra $x$ e $x_{k}$.

> Valutiamo in $\alpha$

$$
f(\alpha)=0=f(x_{k})+(\alpha-x_{k})f'(x_{k})+\frac{1}{2}(\alpha-x_{k})^2f''(x_{k})
$$

Dividendo per $f'(x_{k})$
$$
\frac{f(x_k)}{f'(x_k)} + (\alpha - x_k) + \frac{1}{2} (\alpha - x_k)^2 \frac{f''(\zeta)}{f'(x_k)} = (\alpha - x_{k+1}) + \frac{1}{2} (\alpha - x_k)^2 \frac{f''(\zeta)}{f'(x_k)} = 0
$$

Ricordiamo che $e_{k+1=}x_{k+1}-\alpha$
$$
-e_{k+1} + \frac{1}{2} e_k^2 \frac{f''(\zeta)}{f'(x_k)} = 0 \quad \implies \quad e_{k+1} = e_k^2 \frac{1}{2} \frac{f''(\zeta)}{f'(x_k)}
$$
> Da cui ricordiamo che $\lim\limits_{k\to \infty}x_{k}=\alpha$ e segue che:

$$
\frac{e_{k+1}}{e_k^2} \to \frac{1}{2} \frac{f''(\alpha)}{f'(\alpha)}
\
$$
>[!done] Ordine $p=2$
>Con fattore di convergenza:
>$$\frac{1}{2} \frac{f''(\alpha)}{f'(\alpha)}$$

>[!hint] Osservazione
>Se $\alpha$ è uno zero di [[Soluzione Numerica di Funzioni non Lineari#Molteplicità|molteplicità]] $m$, allora il metodo di Newton non ha più ***convergenza quadratica***.
>Diventa a *convergenza lineare*.
>$$|x_{k+1}-\alpha|\approx c|x_{k}-\alpha|$$
>Con $c=\frac{m-1}{m}$

##### Metodo di Newton Modificato
>[!definizione]
>***Metodo di Newton Modificato*** per radici di molteplicità $m>1$
>$$x_{k+1}=x_{k}-m \displaystyle{\frac{f(x_{k})}{f'(x_{k})}}$$

> Si dimostra che ha convergenza $p=2$

## Metodi Ibridi
>[!tldr] Idea
>Un metodo pratico è quello di far precedere metodi a *convergenza locale* da metodi a *convergenza globale*.
>Dopo alcuni passi del metodo globale si innesca il ***metodo di ordine superiore***.