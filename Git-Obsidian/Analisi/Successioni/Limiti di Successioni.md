## Definizioni
---
>[!info] Definizione Limite
>>[!tldr] Convergente
>>Sia $(a_{n})_{n\in\mathbb{N}}$ una [[Successioni|successione]] reale, sia $l\in \mathbb{R}$ diciamo che $\lim\limits_{n\to+\infty}a_{n}=l$ se :
>>$$
\forall\mathcal{E}>0, \exists m_{\mathcal{E}}\in\mathbb{N} : |a_{n}-l|\leq\mathcal{E} \ \forall n\geq m_{\mathcal{E}}
>>$$
>
>>[!example] Divergente
>>Sia $(a_{n})_{n\in\mathbb{N}}$ una successione reale, diciamo che $\lim\limits_{n\to+\infty}a_{n}=+\infty$ se :
>>$$
\forall k>0, \exists m_k\in\mathbb{N} : a_{n}\geq k \ \forall n\geq m_{k}
>>$$
>>Sia $(a_{n})_{n\in\mathbb{N}}$ una successione reale, diciamo che $\lim\limits_{n\to+\infty}a_{n}=-\infty$ se :
>>$$
\forall k>0, \exists m_k\in\mathbb{N} : a_{n}\leq k \ \forall n\geq m_{k}
>>$$
## Terminologia
- Se
	- $\lim\limits_{n\to+\infty}a_{n}=l \to$ la successione è convergente
- Se
	- $\lim\limits_{n\to+\infty}a_{n}=\pm\infty \to$ la successione è divergente

- $a_{n}$ si dice regolare se ha limite o convergente o divergente
	- Denoto $\overline{\mathbb{R}}=\{\text{insieme di tutti i possibili limiti}\}=\mathbb{R}\cup\{+\infty,-\infty\}$
#### Es
$a_{n}=\displaystyle{\frac{2n+1}{n+2}}$
- Verifica che $\lim\limits_{n\to+\infty}a_{n}=2$
- Dato $\mathcal{E}>0$
$$
\begin{array}
\ |a_{n}-l|=|\displaystyle{\frac{2n+1}{n+2}}-2|\leq \mathcal{E} \\
| \displaystyle{\frac{2n+1-2n-4}{n+2}}|\leq\mathcal{E} \\
\displaystyle{\frac{3}{n+2}}\leq\mathcal{E} \Leftrightarrow n+2\geq \displaystyle{\frac{3}{\mathcal{E}}} \\
n\geq \displaystyle{\frac{3}{\mathcal{E}}}-2
\end{array}
$$
#### Osservazione
>Non tutte le successioni hanno un limite
##### Es
- $a_{n}=(-1)^n$
![[attatchements/succesioneOscillante.png]]
- Oscilla fra $1$ e $-1$
## Successioni Limitate/Illimitate
- - -
>[!tldr] Definizione
>Sia $(a_{n})_{n\in\mathbb{N}}$ in $\mathbb{R}$ diciamo che $(a_{n})$ è illimitata/[[../Insiemi/Insiemi Numerici#Superiore|limitata superiormente]]/[[../Insiemi/Insiemi Numerici#Inferiore|limitata inferiormente]] se lo è l'insieme dei suoi termini
#### Termini
- $sup(a_{n})_{n\in\mathbb{N}}:=sup(a_{n}|n\in\mathbb{N})$
- $inf(a_{n})_{n\in\mathbb{N}}:=inf(a_{n}|n\in\mathbb{N})$
#### Esempi
- $(a_{n})$ è convergente $\implies (a_{n})$ è limitata
- $(a_{n}) \to +\infty$ $\implies (a_{n})$ è illimitata superiormente e limitata inferiormente
- $(a_{n}) \to -\infty$ $\implies (a_{n})$ è illimitata inferiormente e limitata superiormente
##### Osservazione
- $(a_{n})$ Limitata $\neq(a_{n})$ convergente
	- Es $(a_{n})=(-1)^n$
- $(a_{n})$è Illimitata superiormente $\neq(a_{n})$ divergente
	- Es 
$$(a_{n})\begin{cases}
n\text{ se n è pari} \\
0\text{ se n è dispari}
\end{cases}$$
## Unicità del Limite
- - -
>[!info] Teorema
>Sia $(a_{n})_{n\in\mathbb{N}}$ in $\mathbb{R}$, siano $l,m \in \mathbb{R}$ supponiamo
>$$
\begin{array}
\ \lim\limits_{n\to+\infty}a_{n}=l \\
\lim\limits_{n\to+\infty}a_{n}=m
\end{array}
>$$
>Allora $l=m$

### Dimostrazione
- Per ipotesi ho che
$$
\begin{array}
\ \forall \mathcal{E}>0,p_{\mathcal{E}}\in\mathbb{R}:|a_{n}-l|\leq\mathcal{E} \forall n\geq p_{\mathcal{E}} \\
\forall \mathcal{E}>0,q_{\mathcal{E}}\in\mathbb{R}:|a_{n}-m|\leq\mathcal{E} \forall n\geq q_{\mathcal{E}}
\end{array}
$$
- Sia $n\geq max\{p_{\mathcal{E}},q_{\mathcal{E}}\}$
$$
\begin{array}
\ | l-m | =   | l-a_{n}+a_{n}-m | \leq \underbrace{| l-a_{n} |}_{\leq\mathcal{E}} +   \underbrace{| a_{n}-m |}_{\leq\mathcal{E}} \\
|l-m|\leq 2\mathcal{E}
\end{array}
$$
- Da ciò si deduce che deve essere necessariamente $l=m$
- Infatti
	- Se fosse $|l-m|>0$, potrei trovare $\mathcal{E}>0$ (per esempio $\displaystyle{\frac{|l-m|}{2}}$) : $|l-m|>\mathcal{E}$

## Valore assoluto del Limite
- - -
>[!info] Teorema
>Sia $(a_{n})n\in\mathbb{R}:\lim\limits_{n\to+\infty}a_{n}=l$
>Allora
>$\lim\limits_{n\to+\infty}|a_{n}|=|l|$
### Dimostrazione
- Per ipotesi ho che
$$
\forall\mathcal{E}>0,\exists m_{\mathcal{E}}\in\mathbb{N}:|a_{n}-l|\leq\mathcal{E} \ \forall n\geq m_{\mathcal{E}}
$$
- Allora
$$
\forall\mathcal{E}>0,\exists m_{\mathcal{E}}\in\mathbb{N}:||a_{n}|-|l||\leq\mathcal{E} \ \forall n\geq m_{\mathcal{E}}
$$
- E ciò è sempre vero poichè per la disugualianza triangolare
$$
||a_{n}|-|l||\leq|a_{n}-l|
$$
#### Osservazione
- Non è sempre vero l'opposto

## Teorema del Confronto
- - -
>[!info] Definizione
>Siano $(a_{n})_{n\in\mathbb{N}},(b_{n})_{n\in\mathbb{N}}$ successioni regolari
>Siano $l,m\in \overline{\mathbb{R}}$ tali che:
> $$
\begin{array}
\ \lim\limits_{n\to+\infty}a_{n}=l \\
\lim\limits_{n\to+\infty}b_{n}=m
\end{array}
>$$
>>[!tldr] Supponiamo
>>$a_{n}\geq b_{n}$
>>Allora
>>$l\geq m$
### Dimostrazione
- Consideriamo solo il caso $l,m\in\mathbb{R}$ poichè tutti gli altri casi si deducono usando [[.md#Successioni Limitate/Illimitate|la terminologia]] precedentemente descritta
#### Dimostrazione per assurdo
- Voglio dimostrare che $l\geq m$, assumo per assurdo
$$
l<m
$$
- Scelgo $\mathcal{E}>0$ tale che
	- $l<l+\mathcal{E}< \displaystyle{\frac{l+m}{2}}<m-\mathcal{E}<m$
- Ma per ipotesi
$$
\begin{array}\
\exists p_{\mathcal{E}} \in \mathbb{N}:l-\mathcal{E}\leq a_{n}\leq l+\mathcal{E} \\
\exists q_{\mathcal{E}} \in \mathbb{N}:m-\mathcal{E}\leq b_{n}\leq m+\mathcal{E}
\end{array}
$$
- Quindi
$$
\begin{array}\
\forall n \geq max\{p_{\mathcal{E}},q_{\mathcal{E}}\}\text{ si ha: } \\
a_{n}\leq l+\mathcal{E}< \displaystyle{\frac{l+m}{2}}<m-\mathcal{E}\leq b_{n}
\end{array}
$$
- Ciò implica che $a_{n}<b_{n} \to$ contraddizione perchè per ipotesi $a_{n}\geq b_{n}$
#### Osservazione
Se avessi come ipotesi $a_{n}>b_{n}$ non potrei dedurre $l>m$ ma solo $m\geq l$
##### Esempio
$$
\begin{array}
\ a_{n}=\frac{1}{n}\ \ \ \ \ \ \ \ \ b_{n}=0 \\
a_{n}>b_{n} \\
l=0\geq m=0
\end{array}
$$
## Teorema dei due Carabinieri
- - -
>[!info] Definizione
>Siano $(a_{n}),(b_{n}),(c_{n})_{n\in\mathbb{N}}$ successioni reali supponiamo che
> $$
a_{n}\leq b_{n}\leq c_{n} \text{ e } l \in\mathbb{R} \ \ \ \forall n\in\mathbb{N}
>$$
>supponiamo anche che:
>$\lim\limits_{n\to+\infty}a_{n}=l,  \lim\limits_{n\to+\infty}c_{n}=l$
>Allora: $\lim\limits_{n\to+\infty}b_{n}=l$
- Dimostrato tramite il teorema del confronto

## Teorema della permanenza dei segni
- - -
>[!info] Definizione
>Sia $(a_{n})_{n\in\mathbb{N}}$ una successione regolare in $\mathbb{R}$, $l\in\overline{\mathbb{R}}: \lim\limits_{n\to+\infty}a_{n}=l$
>Se $l>0 \implies\exists \overline{n}\in\mathbb{N}:a_{n}>0 \ \ \forall n \geq \overline{n}$
>Se $l<0 \implies\exists \overline{n}\in\mathbb{N}:a_{n}<0 \ \ \forall n\geq \overline{n}$
>>[!done] In breve
>>Se il limite di una funzione è diverso da $0$, allora la funzione è localmente concorde con il llimite
