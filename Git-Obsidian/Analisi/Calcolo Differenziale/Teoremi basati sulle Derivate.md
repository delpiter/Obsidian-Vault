## Estremante Locale
---
>[!info] Definizione
>Sia $I$ intervallo di $\mathbb{R}$, $f:I \to\mathbb{R}$
>Sia $c\in I$
>
>>[!tldr] Minimo
>>Diciamo che $c$ è un punto di minimo locale per $f$ se:
>>$$\exists \delta>0:\forall x \in(c-\delta,c+\delta)\cap I$$
>>E si ha $f(c)\leq f(x)$
>
>>[!tldr] Massimo
>>Diciamo che $c$ è un punto di massimo locale per $f$ se:
>>$$\exists \delta>0:\forall x \in(c-\delta,c+\delta)\cap I$$
>>E si ha $f(c)\geq f(x)$

### Dimostrazione Grafica
![[Pasted Image 202304523.jpg]]

## Teorema di Fermat
---
>[!info] Teorema
>Sia $I$ intervallo di $\mathbb{R}$, $f:I \to\mathbb{R}$
>Sia $c$ [[Definizioni_Analisi#Punto interno in un Intervallo|punto interno]] di $I$
>Supponiamo che $f$ sia derivabile in $c$ e $c$ è [[#Estremante Locale]]
><u>Allora</u>
>$f'(c)=0$

### Dimostrazione
Sia $c$ punto di minimo locale
$$
\exists \delta>0:f(c)\leq f(x) \forall x \in(c-\delta,c+\delta)\cap I
$$
>[!done] Alternativa
>Scegliendo $\delta$ sufficientemente piccolo posso supporre che $(c-\delta,c+\delta)\subset I$ poichè $c$ è un punto interno di $I$

##### Considerando il [[Derivate#Rapporto Incrementale|rapporto incrementale]]:
$$
\displaystyle{\frac{f(x)-f(c)}{x-c}}
$$
###### Numeratore:
- $f(x)-f(c)\geq0$ poichè $c$ è un punto di minimo
###### Denominatore
Abbiamo due casi
- Caso $x \in(c,c+\delta)$
	- $x-c\geq 0$
	- Quindi il rapporto incrementale è sempre $\geq 0$
- Caso $x \in(c-\delta,c)$
	- $x-c\leq 0$
	- Quindi il rapporto incrementale è sempre $\leq0$

##### Passando al Limite

$\lim\limits_{x\to c^+} \displaystyle{\frac{f(x)-f(c)}{x-c}}\geq0$
e
$\lim\limits_{x\to c^-} \displaystyle{\frac{f(x)-f(c)}{x-c}}\leq0$

E poichè $f$ è derivabile $$f'(c) = \lim\limits_{x\to c} \displaystyle{\frac{f(x)-f(c)}{x-c}}=0$$
- Si può fare un ragionamento analogo anche per $c$ punto di massimo locale
### Esempio di $c$ interno ipotesi necessaria
Prendiamo $f(x)=x$ nell'intervallo $[0,1]$
- In questo caso $0$ è punto di minimo, tra l'altro anche assoluto, ma la sua derivata vale $1$
- Il punto $1$ è un punto di massimo, anche esso assoluto, ma la sua derivata vale $1$

## Teorema di Rolle
---

>[!info] Teorema
>Sia $f:[a,b]\to\mathbb{R}$, una funzione [[Git-Obsidian/Analisi/Funzioni/Introduzione Funzioni#Continuità|continua]] in $[a,b]$ e derivabile in $(a,b)$
>Supponiamo che $f(a)=f(b)$
><u>Allora</u>
>$$\exists c\in (a,b):f'(c)=0$$

### Dimostrazione
Dato che $f$ è derivabile su $[a,b]$, per il [[Git-Obsidian/Analisi/Funzioni/Introduzione Funzioni#Teorema di Weierstruss|teorema di Weierstruss]] esistono $max$ e $min$ di $f$
- Ho due possibilità:
#### $max$ e $min$ negli estremi
Se $max(f)$ e $min(f)$ sono entrambe assunti negli estremi
- Es $f(a)=max(f)$ e $f(b)=min(f)$ si può dedurre che $f$ è costante e dunque
$$
f'(x)=0\ \ \ \ \ \ \forall x\in[a,b]
$$
#### $max$ o $min$ assunti internamente
Se almeno uno, tra $max$ e $min$, è assunto all'interno di $(a,b)$ allora in tale punto $c$ posso applicare il [[#Teorema di Fermat]] e dedurre che:
$$
f'(c)=0
$$
### Visualizzazione Grafica
![[Pasted image 20231106151817.png]]

## Teorema di Lagrange
---
>[!info] Teorema
>Sia $f:[a,b]\to\mathbb{R}$, una funzione [[Git-Obsidian/Analisi/Funzioni/Introduzione Funzioni#Continuità|continua]] in $[a,b]$ e derivabile in $(a,b)$
><u>Allora</u>
>$$\exists c\in(a,b):f'(c)= \displaystyle{\frac{f(b)-f(a)}{b-a}}$$
>
>>[!done] In breve
>>Esiste un punto nella funzione per cui il coefficiente angolare della retta tangente passante per quel punto è uguale al coefficiente angolare della retta secante passante per i punti $(a,f(a))$ e $(b,f(b))$

### Dimostrazione

Considero la funzione:
$g(x)=f(x)-f(a)- \displaystyle{\frac{f(b)-f(a)}{b-a}}(x-a)$
>[!done] $g(x)$
>$g(x)$ è la differenza fra la funzione originale $f(x)$ e la funzione della retta secante passante per gli estremi. La formula viene da qui:
>$y−y1​=m⋅(x−x1​) \Leftrightarrow y =f(a) +\displaystyle{\frac{f(b)-f(a)}{b-a}}(x-a)$

- $g$ è derivabile in $(a,b)$ e [[Git-Obsidian/Analisi/Funzioni/Introduzione Funzioni#Continuità|continua]] in $[a,b]$ per somma e differenza di funzioni continue e derivabili
Inoltre
- $g(a)=\cancel{ f(a)-f(a) }- \cancel{ \displaystyle{\frac{f(b)-f(a)}{b-a}}(a-a) }=0$
- $g(b)=f(b)-f(a)- \displaystyle{\frac{f(b)-f(a)}{\cancel{ b-a }}}\cancel{ (b-a) }=0$

Adesso è possibile applicare il [[#Teorema di Rolle]] a $g$ e deduco che

La derivata di $g$ per la somma di funzioni derivabili sarà:
$$
g'(x) = f'(x)- \displaystyle{\frac{f(b)-f(a)}{b-a}}
$$
- Quindi
$$
\begin{array}
\ \exists c \in(a,b)t.c. \\
g'(c)=0 \implies g'(x)=f'(x)-0- \displaystyle{\frac{f(b)-f(a)}{b-a}}-0\\
\Leftrightarrow f'(c)=\displaystyle{\frac{f(b)-f(a)}{b-a}}
\end{array}
$$


### Visualizzazione Grafica
![[Pasted image 20231106151842.png]]

## Teorema test di Monotonia
---
>[!info] Teorema
>Sia $I$ intervallo di $\mathbb{R}$, $f:I\to\mathbb{R}$, derivabile
><u>Allora</u>
>$f \text{ è }\nearrow \text{ in }I\Leftrightarrow f'(x)\geq0 \ \ \forall x\in I$
>$f \text{ è }\searrow \text{ in }I\Leftrightarrow f'(x)\leq0 \ \ \forall x\in I$

### Dimostrazione
È necessario dimostrare l'implicazione reciproca
#### Supponiamo $f \nearrow$ in $I$
- Siano $x,c \in I, x\neq c$
	- Si ha che per definizione di funzione [[Git-Obsidian/Analisi/Funzioni/Introduzione Funzioni#Crescente|crescente]]

$$
\displaystyle{\frac{f(x)-f(c)}{x-c}}\geq 0
$$
Passando al limite per $x\to c$, deduco che, per il [[Limiti di Successioni#Teorema del Confronto|teorema del confronto]]:
$$
f'(c)=\lim\limits_{x\to c} \displaystyle{\frac{f(x)-f(c)}{x-c}}\geq 0
$$
- Quindi:
$$f'(c)\geq 0$$
#### Supponiamo $f'(x)\geq 0$, $\forall x \in I$
- Siano $x_{1},x_{2} \in I$ con $x_{1}\leq x_{2}$, allora si ha che:
$$
f_{\displaystyle|_{x_{1},x_{2}}}:[x_{1},x_{2}]\to\mathbb{R}
$$
- $f$ soddisfa le ipotesi del [[#Teorema di Lagrange|teorema di lagrange]] e dunque
$$
\exists c \in(x_{1},x_{2}): \displaystyle{\frac{f(x_{2})-f(x_{1})}{x_{2}-x_{1}}}=f'(c)
$$
- Per ipotesi quindi otteniamo: $f'(c)\geq 0$
Ciò implica $f(x_{1})\leq f(x_{2})$ cioè $f\nearrow$
### Osservazione
Considerando la monotonia strettamente crescente o decrescente
- Vale lo stesso la relazione di equivalenza?
$$
f\nearrow \text{ strettamente e }f'(x)>0, \forall x \in I
$$
- In generale non vale
	- Continua a valere la relazione solo da una parte
	- $f'(x)>0, \forall x \in I  \implies f \nearrow \text{strettamente}$
	- Invece non è vero
	- $f \nearrow \text{strettamente}   \implies f'(x)>0, \forall x \in I$
		- Poichè per il [[Limiti di Successioni#Teorema del Confronto|teorema del confronto]] 

$$
f'(c)=\lim\limits_{x\to c} \displaystyle{\frac{f(x)-f(c)}{x-c}}> 0
$$
- Diventa
$$f'(c)\geq 0$$
## Test di convessità 1
---
>[!info] Teorema
>Sia $f:I\to\mathbb{R}$ [[Git-Obsidian/Analisi/Funzioni/Introduzione Funzioni#Intervallo|intervallo]] di $\mathbb{R}$, con $f$ derivabile
><u>Allora</u>
>$f$ [[Studio di Funzioni#Concavità di Funzioni|convessa]] su $I\Leftrightarrow f' \nearrow$ su $I$
>$f$ [[Studio di Funzioni#Concavità di Funzioni|concava]] su $I\Leftrightarrow f' \searrow$ su $I$

### Dimostrazione

#### Assumo $f$ [[Studio di Funzioni#Concavità di Funzioni|convessa]] su $I$
$$
\forall x,y \in I \begin{cases}
f(x)\geq f(y)+f'(y)(x-y) \\
f(y)\geq f(x)+f'(x)(y-x)
\end{cases}
$$
- Sommando membro a membro si ha
$$
\cancel{ f(x) }+\cancel{ f(y) }\leq \cancel{ f(x) }+\cancel{ f(y) }+(x-y)(f'(y)-f'(x))
$$
$$
(f'(y)-f'(x))(y-x)\geq 0 \Leftrightarrow f' \nearrow
$$
#### Assumo $f'\nearrow$ in $I$
Siano $c,x \in I$, $c<x$
- $f$ soddisfa le ipotesi del [[#Teorema di Lagrange|teorema di Lagrange]] nell'intervallo $[c,x]$ e dunque
$$
\exists d\in (c,x):(x-c) f(x)-f(c)=f'(d)(x-c)
$$
- Poichè $f'$ è $\nearrow$
$$
f(x)-f(c)\geq f'(c)(x-c)
$$
## Test di Convessità 2
---
>[!info] Teorema
>Sia $f:I\to\mathbb{R}$, derivabile 2 volte su $I$
><u>Allora</u>
>$f$ convessa $\Leftrightarrow f''(x)\leq0, \forall x \in I$
>$f$ concava $\Leftrightarrow f''(x)\geq0, \forall x \in I$
- I punti dove cambia la convessità si chiamano punti di flesso