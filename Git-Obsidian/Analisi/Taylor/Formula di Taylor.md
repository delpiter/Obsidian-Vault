
## Formula di Taylor con Resto di Peano
---
>[!info] Teorema
>Sia $I$ [[../Funzioni/Introduzione Funzioni#Intervallo|intervallo]] di $\mathbb{R}$, $f:I\to\mathbb{R},c\in I,n \in\mathbb{N}$
>Se $f$ è derivabile $n$ volte,
><u>Allora</u>
>$$f(x)=\underbrace{ \sum^n_{k=0} \displaystyle{\frac{f^{(k)(c)}}{k!}}(x-c)^k }_{\displaystyle T_{c,n}(x) } + \circ(x-c)^n \text{ per }x\to c$$
>
>>[!done] In breve
>>Posso approssimare la funzione con un polinomio più una parte trascurabile di grado $n$

### Dimostrazione
#### Caso $c=0,n=2$
Voglio dimostrare che, se $f$ è derivabile 2 volte, allora:
$$f(x)=f(0)+f'(0)\cdot(x-0)+ \displaystyle{\frac{f''(0)}{2}}(x+0)^2+\circ(x+0)^2$$
Consideriamo la funzione Resto:
>[!tldr] $R(x)$
>$$R(x):= f(x)-f(0)-f'(0)x- \displaystyle{\frac{f''(0)}{2}}x^2$$
- Scopo: $R(x)=\circ(x^2) \text{ per }x\to0$
##### Calcolo $R'(x)$
$$
R'(x)=f'(x)-f'(0)-f''(0)x
$$
- Poichè $f$ è derivabile 2 volte possiamo affermare che $f'$ è derivabile una volta e dunque posso applicare il [[../Calcolo Differenziale/Derivate#Teorema di Caratterizzazione delle Funzioni Derivabili|teorema di caratterizzazione delle funzioni derivabili]]
- $f'(x)=f'(0)+f''(0)x+\circ(x)$
Sostituisco in $R'(x)$ e ottengo:
$$
R'(x) = \cancel{ f'(0) }+\cancel{ f''(0)x }+\circ(x)-\cancel{ f'(0) }-\cancel{ f''(0)x }
$$
- Quindi $R'(x) = \circ(x)\text{ per }x\to0$
##### Applico il teorema di Lagrange
Ora applico il [[../Calcolo Differenziale/Teoremi basati sulle Derivate#Teorema di Lagrange|teorema di Lagrange]] alla funzione Resto nell'intervallo $[0,x]$ (o $[x,0]$, dipende se $x>0$ o $x<0$)
- Quindi:
$$
\exists d_{x}\in(0,x)\text{ t.c. } \displaystyle{\frac{R(x)-R(0)}{x}=R'(d_{x})}
$$
- Divido tutto per $x$
$$
\displaystyle{\frac{R(x)-\overbrace{R(0)}^0}{x^2}=\displaystyle{\frac{R'(d_{x})}{x}}}
$$
- Ora basta dimostrare che $d_{x} = x$
##### Applico il valore assoluto
$$
\begin{array}
\ 0\leq\left|\displaystyle{\frac{R(x)-R(0)}{x^2}}\right|=\left| \displaystyle\frac{R'(d_{x})}{x} \right|\leq \underbrace{ \left| \displaystyle\frac{R'(d_{x})}{d_{x}} \right| }_{ \text{ tende a 0 per }x\to0 }  \\
\end{array}
$$
- Dato che $d_{x}$ è compreso tra $x$ e $-x$ se $x\to 0$ anche $d_{x}\to0$
Per il [[../Successioni/Limiti di Successioni#Teorema dei due Carabinieri|teorema dei due carabinieri]] deduco che:
$$
\displaystyle{\frac{R(x)}{x^2}} \to 0 \text{ per } x\to0
$$
- Quindi $R(x) = \circ (x^2) \text{ per } x\to0$
### Osservazione
Il polinomio di Taylor $T_{c,n}(x)$, di punto iniziale $c$ e di ordine $n$ è l'unico polinomio con la seguente proprietà:
$$
T^{(k)}_{c,n}(c) = f^{(k)}(c), \forall k=\{ 0,1,2,\dots,n \}
$$