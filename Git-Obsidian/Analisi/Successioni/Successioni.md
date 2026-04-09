>[!info] Definizione
>Sia $A\neq 0,A\subseteq\mathbb{R}$ chiamiamo successione in $A$ una qualsiasi funzione
> $$
f: \mathbb{N}\to A
>$$
## Notazione
$$
\underbrace{a_{n}}_{\text{termine n-esimo}} := a(n)
$$
- $n$ anche detto l'indice della successione
##### Es
- $a_{n}=k, \ k\in\mathbb{R}$
![[attatchements/successione costante.png]]

- $a_{n}=(-1)^n$
![[attatchements/succesioneOscillante.png]]

## Successioni infinitesime
- - -
>[!info] Definizione
>Sia $(a_{n})_{n\in\mathbb{N}}$ una successione in $\mathbb{R}$ diciamo che la mia successione è infinitesima (che tende a $0$) per $n \to +\infty$ se
>$$
\forall \mathcal{E} \in \mathbb{R}^+\setminus\{0\}, \exists m_{\mathcal{E}}\in \mathbb{N} : \forall n \geq m_{\mathcal{E}} \text{ si ha } |a_{n}|\leq\mathcal{E}
>$$
>>[!done] In Breve
>>Fissato un numero $\mathcal{E}\in\mathbb{R}$ esiste una soglia $m_{\mathcal{E}}\in\mathbb{N}$ tale che, qualsiasi $n$ io prenda che sia più grande di $m_{\mathcal{E}}$, $a_{n}$ è più piccola di $\mathcal{E}$

![[attatchements/successioneInfinitesima.png]]
### Es
- $a_{n}=\displaystyle{\frac{1}{n}}$
- Verifichiamo che $\lim\limits_{n\to+\infty} \displaystyle{\frac{1}{n}} =0$
###### Infatti
$\forall \mathcal{E} \in \mathbb{R}^+\setminus\{0\}, \exists m_{\mathcal{E}}\in\mathbb{N} : \forall n\geq m_{\mathcal{E}} \text{ si ha } |\displaystyle{\frac{1}{n}}|\leq\mathcal{E}$
$$
\ |\displaystyle{\frac{1}{n}}|\leq\mathcal{E} \Leftrightarrow \displaystyle{\frac{1}{n}}\leq\mathcal{E}\Leftrightarrow n\geq \displaystyle{\frac{1}{\mathcal{E}}}
$$
- Posso scegliere come $m_{\mathcal{E}}=\lfloor \displaystyle{\frac{1}{\mathcal{E}}}\rfloor+1$

- È possibile generalizzare la definizione come successione infinitesima, che tende a qualsiasi numero reale
## Successione Monotona
- - -
>[!info] Definizione
>Sia $(a_{n})_{n\in\mathbb{N}}$ una successione in $\mathbb{R}$ diciamo che $(a_{n})$ è [[../Funzioni/Introduzione Funzioni#Crescente|crescente]] se
> $$
a_{n}\leq a_{n+1}, \,\,\,\ \forall n\in\mathbb{N}
>$$
>Sia $(a_{n})_{n\in\mathbb{N}}$ una successione in $\mathbb{R}$ diciamo che $(a_{n})$ è [[../Funzioni/Introduzione Funzioni#Decrescente|decrescente]] se
> $$
a_{n} \geq a_{n+1}, \,\,\,\ \forall n\in\mathbb{N}
>$$
>Analogamente strettamente crescente e strettamente decrescente

#### Esempi
- $a_{n}=n \nearrow$
- $a_{n}=\frac{1}{n} \searrow$
- $a_{n}=2^n \nearrow$
- $a_{n}=(\frac{1}{2})^n \searrow$
### Osservazione
> Se $a_{n}$ è una successione crescente allora $a_{n}$ è inferiormente limitata e $inf(a_{n})=a_{0}$
> Se $a_{n}$ è una successione decrescente allora $a_{n}$ è superiormente limitata e $sup(a_{n})=a_{0}$

## Limiti di Successioni Monotone
- - -
>[!info] Teorema
>Sia $(a_{n})_{n\in\mathbb{N}}$ successione in $\mathbb{R}$ monotona
><u>Allora</u> 
>$a_{n}$ è regolare
>Più precisamente
>$$
\begin{array}
\ \text{se }a_{n}\nearrow \implies\lim\limits_{n\to+\infty}a_{n}=sup(a_{n}) \\
\text{se }a_{n}\searrow \implies\lim\limits_{n\to+\infty}a_{n}=inf(a_{n})
\end{array}
>$$