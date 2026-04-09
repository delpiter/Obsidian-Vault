## Successioni Trascurabili
---
>[!info] Definizione
>Siano $(a_{n}),(b_{n})_{n\in\mathbb{N}}$ successioni reali, diciamo che $a_{n}$ è **trascurabile** rispetto a $b_{n}$ se:
> $$
\lim\limits_{n\to+\infty} \displaystyle{\frac{a_{n}}{b_{n}}}=0
>$$
>In tal caso scriviamo:
>$a_{n}=\circ (b_{n})$
>>[!done] In breve
>>La successioni $a_{n}$ è trascurabile rispetto a $b_{n}$ quando il limite del rapporto $\displaystyle{\frac{a_{n}}{b_{n}}}$ è uguale a $0$

### Calcoli con $\circ (\dots)$
- se $a_{n}=\circ(b_{n}),c_{n}=\circ(b_{n}) \implies a_{n}+c_{n}=\circ(b_{n})$
- se $a_{n}=\circ (b_{n}),c_{n}=\circ (d_{n})\implies a_{n}\cdot c_{n}=\circ (b_{n}\cdot d_{n})$
- se $a_{n}=\circ (b_{n}),a_{n}\cdot c_{n}=\circ (b_{n}\cdot c_{n})$

### Funzioni Trascurabili
---
- Analoghe alle successioni
>[!info] o Piccoli
>Siano $f,g:I\to\mathbb{R}$ [[../Funzioni/Introduzione Funzioni#Intervallo|intervalli]] o un [[../Funzioni/Introduzione Funzioni#Intervallo Forato|intervalli forati]], $c\in[inf(I),sup(I)]$
>Diciamo che $f$ è trascurabile rispetto a $g$ e scriviamo $f(x)=\circ(g(x))$ per $x\to c$
>Se
>$$\lim\limits_{x\to c} \displaystyle{\frac{f(x)}{g(x)}}=0$$

## Regole Aritmetiche
---
### Prodotto
#### Con costante
>[!done] In breve
>$$c\cdot\circ(f(x)) = \circ(f(x))\text{ per }x\to0$$
##### Osservazione
- $+\circ(f(x)) = -\circ(f(x))$
#### Fra Funzioni
>[!done] In breve
>$$\circ(f(x))\cdot\circ(g(x))=\circ(f(x)\cdot g(x))$$
### Somma
#### Stesso ordine
>[!done] In breve
>$$\circ(f(x))+\circ(f(x)) = \circ(f(x))$$
#### Funzioni Diverse
>[!done] In breve
>Se $g(x)=\circ(f(x))$
>$$\circ(f(x))+\circ(g(x)) = \circ(f(x))$$

##### Osservazione
- $\text{ per }x\to0:\ \ \circ(x^\alpha)+\circ(x^\beta)=\circ(x^\alpha),\ \ \ \ \ \alpha,\beta\in \mathbb{R},\alpha<\beta$
### Composte
>[!done] In breve
>$$\circ(\circ(f(x)))=\circ(f(x))$$
## Approssimazioni di funzioni note
---
$$
\begin{cases}
e^x=1+x+\circ(x) \text{ per }x\to 0 \\
log(1+x) = x+\circ(x) \text{ per }x \to 0 \\
sen(x)=x+\circ(x) \text{ per }x\to 0 \\
cos(x)=1- \displaystyle{\frac{x^2}{2}}+\circ(x) \text{ per }x\to 0 \\
tan(x)=x+\circ(x) \text{ per }x\to 0
\end{cases}
$$
