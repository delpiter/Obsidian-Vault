## Limiti per funzioni ad una Variabile Reale
---
### Intorni
>[!info] Definizione
>Dato $c\in\mathbb{R}$, chiamiamo intorno del punto $c$ un qualsiasi [[Git-Obsidian/Analisi/Funzioni/Introduzione Funzioni#Intervallo|intervallo]] della forma
>$$(c-r,c+r)$$
>Chiamiamo invece intorno di $+\infty$ un qualsiasi intervallo della forma 
>$$(a,+\infty)$$
>Chiamiamo invece intorno di $-\infty$ un qualsiasi intervallo della forma
>$$(-\infty,a)$$

#### Osservazione
>$U$ è un intorno di $c$ se $$\exists r>0:U=(c-r,c+r)$$
- Cioè $x\in U \Leftrightarrow |x-c|<r$

>$U$ è un intorno di $+\infty$ se $$\exists a>0:U=(a,+\infty)$$
- Cioè $x\in U \Leftrightarrow x>a$

>$U$ è un intorno di $-\infty$ se $$\exists b>0:U=(-\infty,b)$$
- Cioè $x\in U \Leftrightarrow x<b$

### Definizione Limite
>[!info] Definizioni
>Elenchiamo di seguito 2 definizioni uguali di limite
>>[!example] Definizione con definizione di [[Limiti di Successioni#Definizioni|successione]]
>>Sia $I$ un [[Git-Obsidian/Analisi/Funzioni/Introduzione Funzioni#Intervallo|intervallo]] o un [[Git-Obsidian/Analisi/Funzioni/Introduzione Funzioni#Intervallo Forato|intervallo forato]]
>>Sia $f:I\to \mathbb{R},c\in[inf(I),sup(I)]$ ([[Insiemi Numerici#Insiemi Limitati|limitazioni]]),$l\in\overline{\mathbb{R}}$
>>Diciamo che $\exists\lim\limits_{x\to+c}f(x)=l$ se:
>>$$\forall(a_{n})_{n\in\mathbb{N}}\text{ successione in }I\setminus\{ c \}:\lim\limits_{n\to+\infty}a_{n}=c$$
>>Si ha
>>$$\lim\limits_{n\to +\infty}f(a_{n})=l$$
>>>[!done] In breve
>>>Comunque io scelga una successione di punti che tende a $c$, quando ad $a_{n}$ applico la funzione il valore deve tendere a $l$
>
>>[!example] Definizione 2
>>Sia $I$ un [[Git-Obsidian/Analisi/Funzioni/Introduzione Funzioni#Intervallo|intervallo]] o un [[Git-Obsidian/Analisi/Funzioni/Introduzione Funzioni#Intervallo Forato|intervallo forato]]
>>Sia $f:I\to \mathbb{R},c\in[inf(I),sup(I)]$ ([[Insiemi Numerici#Insiemi Limitati|limitazioni]]),$l\in\overline{\mathbb{R}}$
>>Diciamo che $\exists\lim\limits_{x\to+c}f(x)=l$ se:
>>$$\forall \mathrm{V} \text{ intorno di } l, \exists \mathrm{U}_{\mathrm{V}}\text{ intorno di }c: \forall x\in\mathrm{U}_{\mathrm{V}}\setminus\{c\}$$
>>Si ha: $f(x)\in\mathrm{V}$
>>a
>>>[!done] In Breve
>>>Qualsiasi intorno di $l$ che io prenda, esiste un intorno del punto $c$ tale che l'insieme di valori ottenuti da $f(x), x\in\mathrm{U}c$ è un sottoinsieme dell'intorno di $l$

#### Teorema del "ponte"
- Il teorema del ponte enuncia che le due definizioni precedenti sono equivalenti
##### Esempio
###### Caso $l,c\in\mathbb{R}$
$$
\forall\mathcal{E}>0,\exists \delta_{\mathcal{E}}>0:\text{ se }|x-c|<\delta_{\mathcal{E}} \text{ si ha }|f(x)-l|<\mathcal{E}, x\neq c
$$
###### Spiegazione grafica
![[definizioneLimite.png]]

>[!done] In Breve
>Fissato un $\mathcal{E} >0$, esiste un $\delta>0$
>Tale che $\forall x$ nell'intervallo $(c-\delta,c+\delta)$ si ha che $f(x)$ deve cadere nell'intervallo $(l-\mathcal{E},l+\mathcal{E})$
###### Caso $l = +\infty, c\in\mathbb{R}$
$$
\forall \mathcal{E}> 0,\exists\delta_{\mathcal{E}}>0 :\text{ se }|x-c|<\delta_{\mathcal{E}}, f(x)>\mathcal{E}
$$

## Proprietà dei limiti
---
- Le proprietà dei limiti di funzione sono analoghe a quelle per le successioni
### Unicità del limite
>[!info] Definizione
>Sia $I$ un [[Git-Obsidian/Analisi/Funzioni/Introduzione Funzioni#Intervallo|intervallo]] o un [[Git-Obsidian/Analisi/Funzioni/Introduzione Funzioni#Intervallo Forato|intervallo forato]]
>Sia $f:I\to \mathbb{R},c\in[inf(I),sup(I)]$ ,$m,l\in\overline{\mathbb{R}}$
>Se $$\lim\limits_{x\to c}f(x)=l \text{ e } \lim\limits_{x\to c}f(x)=m$$
><u>Allora</u>
>$l=m$

### Teorema della permanenza del segno
>[!info] Definizione
>Sia $I$ un [[Git-Obsidian/Analisi/Funzioni/Introduzione Funzioni#Intervallo|intervallo]] o un [[Git-Obsidian/Analisi/Funzioni/Introduzione Funzioni#Intervallo Forato|intervallo forato]]
>Sia $f:I\to \mathbb{R},c\in[inf(I),sup(I)]$ ,$l\in\overline{\mathbb{R}}$
>Supponiamo che $$\lim\limits_{x\to c}f(x)=l$$
><u>Allora</u>
>Se $l>0$
>$$\exists \text{ un intorno }\mathrm{U} \text{ di c }:f(x)>0\ \ \forall x\in\mathrm{U}\cap I \setminus\{ c \}$$
>Se $l<0$
>$$\exists \text{ un intorno }\mathrm{U} \text{ di c }:f(x)<0\ \ \forall x\in\mathrm{U}\cap I \setminus\{ c \}$$

### Teorema dei due Carabinieri
>[!info] Definizione
>Sia $I$ un [[Git-Obsidian/Analisi/Funzioni/Introduzione Funzioni#Intervallo|intervallo]] o un [[Git-Obsidian/Analisi/Funzioni/Introduzione Funzioni#Intervallo Forato|intervallo forato]]
>Sia $f,g,h:I\to \mathbb{R},c\in[inf(I),sup(I)]$ ,$l\in\mathbb{R}$
>Se $$\lim\limits_{x\to c}f(x)=l,\ \ \lim\limits_{x\to c}=h(x)=l$$
>E $$\exists \text{ un intorno } \mathrm{U}\text{ di c }:f(x)\leq g(x) \leq h(x), \forall x \in \mathrm{U}\cap\setminus\{ c \}$$
><u>Allora</u>
>$$\lim\limits_{x\to c}g(x)=l$$

### Limiti unilateri
>[!info] Definizione
>Sia $I$ un [[Git-Obsidian/Analisi/Funzioni/Introduzione Funzioni#Intervallo|intervallo]] o un [[Git-Obsidian/Analisi/Funzioni/Introduzione Funzioni#Intervallo Forato|intervallo forato]]
>Sia $f:I\to \mathbb{R},c\in[inf(I),sup(I)]\cap\mathbb{R}$ ,$l\in\overline{\mathbb{R}}$
>Diciamo che $f$ ha limite per $x\to c$ da sinistra (scriviamo $x\to c^-$)
>Se ([[Definizioni_Analisi#Notazione Restrizione del dominio|notazione]]) $$\lim\limits_{x\to c}f(x)_{\displaystyle{|_{I\cap(-\infty,c)}}}=l$$

>[!example] Osservazione
>$$\exists \lim\limits_{x\to c}f(x)\Leftrightarrow \begin{cases}\exists \lim\limits_{x\to c^-}f(x)\\ \lim\limits_{x\to c^+}f(x)\end{cases}$$
>Tali limiti coincidono

### Cambio di variabile dei Limiti
>[!info] Teorema
>Siano $I,J$ intervalli o intervalli forati, $f:I\to\mathbb{R}, g:J\to\mathbb{R},f(I)\subseteq J$
>Siano $x_{0}\in[inf(I),sup(I)], l\in[inf(J),sup(J)]$
>Se $$\lim\limits_{x\to x_{0}}f(x)=l\text{ e } \lim\limits_{y\to l}g(y)=k$$
>Supponiamo che $\exists$ un intorno $\mathrm{U} \text{ di } x_{0}:f(x)\neq l\in\mathrm{U}\setminus\{x_{0}\}$
><u>Allora</u>
>$$\lim\limits_{y\to x_{0}}g(\underbrace{f(x)}_{l})=k$$


## Teorema degli Zeri
>[!info] Teorema
>Sia $f:[a,b]\to \mathbb{R}$ [[Git-Obsidian/Analisi/Funzioni/Introduzione Funzioni#Continuità|continua]]
>e supponiamo: $f(a)\cdot f(b)<0$
><u>Allora</u>
>$$\exists c\in(a,b):f(c)=0$$
>>[!done] In breve
>>Se in una funzione continua e limitata gli estremi della stessa sono discordi allora esiste un valore della $x$ per cui la $y$ assume il valore $0$
### Dimostrazione
Assumiamo $f(a)<0<f(b)$
- Sia $c_{0} = \displaystyle{\frac{a+b}{2}}$ il punto medio di $(a,b)$ ($c_{0}$ è il "passo 0")
- Si procede con il concetto di **Bisezione** (in informatica ricerca binaria)
#### 3 Possibilità
1. $f(c_{0})=0\to$ Dimostrazione finita 
2. $f(c_{0})>0\to$ Osservo che $f(a)<0<f(c_{0})$
3. $f(c_{0})<0\to$ Osservo che $f(c_{0})<0<f(b)$ 

- Nei casi 2 e 3 continuo la ricerca
	- Nel caso 2 considero l'intervallo $(a,c_{0}), a_{1}=a,b_{1}=c_{0}$
	- Nel caso 3 considero l'intervallo $(c_{0},b), a_{1}=c_{0},b_{1}=b$
- Rinomino gli estremi e ripeto il procedimento
#### 2 conclusioni possibili
Iterando il ragionamento (Metodo di Bisezione) si hanno 2 possibilità
1. Trovo, dopo un numero finito di iterazioni, uno zero di una funzione
	- $f(c_{k}) = 0$ per qualche $k$
2. Il procedimento continua indefinitivamente
	- In questo caso ho costruito due successioni $a_{n}$ e $b_{n}$ con le seguenti proprietà:

>[!tldr] Proprietà delle successioni
>$1) \ \ a\leq a_{n} \leq b_{n} \leq b, \forall n\in\mathbb{N}$
>$2) \ \ a_{n+1} \geq a_{n} \forall n \in\mathbb{N} \text{ cioè } a_{n} \nearrow$
>$3) \ \ b_{n+1} \leq b_{n} \forall n \in\mathbb{N} \text{ cioè } b_{n} \searrow$
>$4) \ \ b_{n}-a_{n} = \displaystyle{\frac{b-a}{2^n}}$
>>[!done] In Breve
>>Dopo ogni "passaggio" la distanza fra i due punti si dimezza, quindi al passaggio $n$ la lunghezza è uguale alla distanza originale diviso $2^n$
>>La distanza fra i punti delle due successioni tende a $0$ per $n\to+\infty$
>
>$5) \ \ f(a_{n}) < 0 < f(b_{n}) \forall n\in\mathbb{N}$
>>[!done] In Breve
>>La funzione nei punti delle successioni è concorde (stesso segno) rispetto al punto nel suo estremo

- Date queste proprietà:
	- Dalle proprietà 2,3 segue che per il [[Successioni#Limiti di Successioni Monotone|teorema del limite di successioni monotone]] $\exists\lim\limits_{n\to +\infty} a_{n},b_{n}$ inoltre dalla proprietà numero 1 segue che tali limiti sono numeri reali
	- Dalla proprietà numero 4 ho che $\lim\limits_{n\to +\infty}b_{n}-a_{n} = 0$ quindi per forza i due limiti sono uguali
		- $\lim\limits_{n\to +\infty}a_{n} = \lim\limits_{n\to +\infty}b_{n} = c$
	- Infine dalla proprietà 5, usando il [[Limiti di Successioni#Teorema del Confronto|teorema del confronto]] ho che
		- $\lim\limits_{n\to +\infty}f(a_{n})\leq0$
		- E analogamente
		- $\lim\limits_{n\to +\infty}f(b_{n})\geq0$
- Poichè $f$ è [[Git-Obsidian/Analisi/Funzioni/Introduzione Funzioni#Continuità|continua]] si ha che:
	- $\lim\limits_{n\to +\infty}f(a_{n})=f(c)\leq0$
	- $\lim\limits_{n\to +\infty}f(b_{n})=f(c)\geq0$
- Ne deduciamo quindi che $f(c) = 0\ \ \ \ \ \ \ \ \  \#$

## Teorema dei valori Intermedi
---
>[!info] Teorema
>Sia $I$ intervallo di $\mathbb{R}$, sia $f:I\to\mathbb{R}$ [[Git-Obsidian/Analisi/Funzioni/Introduzione Funzioni#Continuità|continua]] 
><u>Allora</u>
>$f(I)$ è a sua volta un intervallo (o [[Definizioni_Analisi#Intervallo degenere|intervallo degenere]])
>
>>[!done] In Breve
>>Se una funzione è continua, la sua immagine assume tutti i valori fra il massimo e il minimo della funzione

### Dimostrazione
#### $f$ Costante
Se $f$ è costante $=k \implies f(I)=\{ k \}\implies$ Intervallo degenere
#### $f$ Non Costante
Se $f$ non è costante:
$$
\exists y_{1},y_{2}\in f(I) \text{ con } y_{1}\neq y_{2}
$$
- <u>Devo mostrare che</u>
$$
\forall y :y_{1}<y<y_{2}, \text{ si ha che } y\in f(I)
$$
##### Dimostrazione
Siano: $$x_{1},x_{2}\in I:\begin{cases}
f(x_{1}) = y_{1} \\
f(x_{2}) = y_{2}
\end{cases}$$
- Osserviamo che $x_{1}\neq x_{2}$ poichè $f$ è una funzione
- Supponiamo che $x_{1}<x_{2}$
- Introduco una funzione
$$
\begin{array}
\ g:[x_{1},x_{2}]\to\mathbb{R} \\
g(x) = f(x)-y, \ \ \ \ y_{1}<y<y_{2}
\end{array}
$$
- Verifichiamo che la funzione $g(x)$ soddisfi le ipotesi del teorema degli zeri
	- Infatti:

$$
\begin{array}
\ g(x_{1})=f(x_{1})-y = y_{1}-y < 0 \\
g(x_{2})=f(x_{2})-y = y_{2}-y > 0
\end{array}
$$
Quindi
- $g$ è continua in $[x_{1},x_{2}]$ perchè lo è $f$ su $I$
- Applico il teorema degli zeri a $g$ e deduco che
$$
\exists c \in(x_{1},x_{2}):g(c)=0 \Leftrightarrow f(c)-y = 0\Leftrightarrow f(c)=y
$$