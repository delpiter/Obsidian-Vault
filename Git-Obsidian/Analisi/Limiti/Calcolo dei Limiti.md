## Polinomi
---
### Limite per $x\to\pm\infty$
- Calcolo analogo a quello delle [[../Successioni/Operazioni con i Limiti#Operazioni|successioni]]
	- Bisogna solo stare attenti al caso $-\infty$, vale la regola dei segni
	- Es $\lim\limits_{x\to-\infty }x^3=-\infty$
	- Es $\lim\limits_{x\to-\infty }x^2=+\infty$
### Limite per $x\to c$
- È sufficiente sostituire la $x$ con la $c$
	- Es $\lim\limits_{x\to c}3x^2-7x+1=3(c)^2-7(c)+1$
## Funzioni Razionali con $\displaystyle{\frac{p(x)}{q(x)}}$ con $p,q$ polinomi
---
### Limite per $x\to \pm\infty$
- Calcolo analogo a quello delle [[../Successioni/Operazioni con i Limiti#Operazioni|successioni]]
	- Bisogna solo stare attenti al caso $-\infty$, vale la regola dei segni
### Limite per $x\to c$
#### Con $c\in \text{Dominio}$ ($q(c)\neq0$)
È sufficiente fare la sostituzione di $x$ con $c$

#### Con $q(c)=0$
- $\lim\limits_{x\to 2} \displaystyle{\frac{1}{(x-2)^3}}\to \text{ non esiste limite}$
	- Ma:
		- $\lim\limits_{x\to 2^+} = +\infty$
		- $\lim\limits_{x\to 2^-}-\infty$
- Vale la solita regola dei segni
##### In Generale
$$
\begin{array}
\ \lim\limits_{x\to c} \displaystyle{\frac{1}{(x-c)^A}}=+\infty \text{ con A pari}
\\ \lim\limits_{x\to c} \displaystyle{\frac{1}{(x-c)^B}}\to \text{non esiste con B dispari} \\
\text{ma} \\
\begin{cases}
\lim\limits_{x\to c^+}\displaystyle{\frac{1}{(x-c)^B}} = +\infty \\
\lim\limits_{x\to c^-}\displaystyle{\frac{1}{(x-c)^B}} = -\infty
\end{cases}
\end{array}
$$
## Funzioni Esponenziali
---
### $a>1$
- $a^x$
	- $x\to +\infty=+\infty$
	- $x\to -\infty=0$
	- $x\to c=a^c$
### $0<a<1$
- $a^x$
	- $x\to +\infty=0$
	- $x\to -\infty=+\infty$
	- $x\to c=a^c$

## Funzioni Logaritmiche
---
### $a>1$
- $log_{a}x$
	- $x\to +\infty=+\infty$
	- $x\to i \ \ (i\leq 0) \implies \not\exists$
	- $x\to 0^+=-\infty$
	- $x\to c=log_{a}c, \text{con }c >0$
### $0<a<1$
- $log_{a}x$
	- $x\to +\infty=-\infty$
	- $x\to i \ \ (i\leq 0) \implies \not\exists$
	- $x\to 0^+=+\infty$
	- $x\to c=log_{a}c, \text{con }c >0$

## Funzioni Trigonometriche
---
### Seno e Coseno
- $\lim\limits_{x\to \mp\infty}\sin(x),\cos(x) \implies \text{ Non esiste}$
- $\lim\limits_{x\to c}\sin(x),\cos(x) =\sin(c),\cos(c)$

### Tangente
- $\lim\limits_{x\to \displaystyle{\frac{\pi}{2}}^-}\tan(x)=+\infty$
- $\lim\limits_{x\to \displaystyle{\frac{\pi}{2}}^+}\tan(x)=-\infty$
### Arcotangente
- $\lim\limits_{x\to +\infty}\arctan(x)=\displaystyle{\frac{\pi}{2}}$
- $\lim\limits_{x\to -\infty}\arctan(x)=-\displaystyle{\frac{\pi}{2}}$

## Operazioni e Forme indeterminate
---
### $a>1,p>0$
- $\lim\limits_{x\to +\infty} \displaystyle{\frac{x^p}{a^x}}=0$
- $\lim\limits_{x\to -\infty}|x|^p\cdot a^x=0$
### $0<a<1,p>0$
- $\lim\limits_{x\to +\infty} a^x\cdot x^p=0$
- $\lim\limits_{x\to -\infty} \displaystyle{\frac{a^x}{|x|^p}}=+\infty$
## Limiti Notevoli
---
### Logaritmi e Esponenziali
>[!tldr] Ricordo
>$$\lim\limits_{n\to +\infty}\left( 1+\displaystyle{\frac{1}{n}} \right)^n=e$$
>Si può mostrare che:
>$$\lim\limits_{x\to \pm\infty}\left( 1+\displaystyle{\frac{1}{n}} \right)^n=e, (x\in\mathbb{R}\setminus\{0\})$$

- Ponendo $y=\displaystyle{\frac{1}{x}}$
	- Si ottiene $\lim\limits_{x\to 0}(1+x)^{\frac{1}{x}}=e$
- Applicando il $log_{a}$ si ha che:
	- $\lim\limits_{x\to 0}\log_{a}[(1+x)^{\frac{1}{x}}]=\log_{a}e$

>[!info] Se $a=e$
>$$\lim\limits_{x\to 0}\ln\left[ (1+x)^{\frac{1}{x}} \right]=\lim\limits_{x\to 0} \displaystyle{\frac{ln(1+x)}{x}}=1$$

- Partendo dalla definizione precedente e ponendo:
>[!info] $y=ln(1+x)$
>Dato che $\lim\limits_{x\to 0}y=\lim\limits_{x\to 0}ln(x+1)=0$
>E $1+x=e^y \implies x=e^y-1$
>$$\lim\limits_{y\to 0} \displaystyle{\frac{e^y-1}{y}}=1$$

![[../Taylor/Resto di Peano#Funzioni Trascurabili]]
### Riscriviamo i Limiti
$$
\begin{array}
\
\lim\limits_{x\to 0} \displaystyle{\frac{ln(1+x)}{x}}=1 \Leftrightarrow \lim\limits_{x\to 0} \displaystyle{\frac{ln(1+x)-x}{x}}=0 \\
\text{Quindi} \\
ln(1+x)-x = \circ(x) \text{ per } x\to 0 \\
ln(1+x) =x+  \circ(x) \text{ per } x\to 0
\end{array}
$$
>[!done] In Breve
>$ln(1+x)$ è uguale ad $x$ più qualcosa di trascurabile per $x\to 0$
>Le funzioni per $x\to 0$ hanno l'andamento simile

$$
\begin{array}
\
\lim\limits_{x\to 0} \displaystyle{\frac{e^x-1}{x}}=1\Leftrightarrow \lim\limits_{x\to 0} \displaystyle{\frac{e^x-1-x}{x}}=o \\
\text{Quindi} \\
e^x-1-x = \circ(x) \text{ per } x\to 0 \\
e^x = 1+x+\circ(x) \text{ per } x\to 0
\end{array}
$$
>[!done] In Breve
>$e^x$ è uguale ad $x+1$ più qualcosa di trascurabile per $x\to 0$
>Le funzioni per $x\to 0$ hanno l'andamento simile

#### Es
- $\lim\limits_{x\to 0} \displaystyle{\frac{e^{2x}-1}{ln(1+3x)}}$
$$
\begin{array}
\ e^{2x}=1+2x+\circ(x) \text{ per } x\to 0 \\
ln(1+3x) = 3x+\circ(x) \text{ per } x\to 0
\end{array}
$$
- $\lim\limits_{x\to 0} \displaystyle{\frac{e^{2x}-1}{ln(1+3x)}}\Leftrightarrow \lim\limits_{x\to 0} \displaystyle{\frac{\not1+2x-\not1+\circ(x)}{3x+\circ(x)}}= \displaystyle{\frac{2}{3}}$

### Funzioni trigonometriche
>[!info] Seno
>Dimostriamo che
>$$\lim\limits_{x\to 0} \displaystyle{\frac{\sin(x)}{x}}=1$$

![[attatchements/limiteNotevoleSeno.png]]
- Osservo nell'immagine sovrastante che appaiono 3 figure
	1. Triangolo $\overset{\triangle}{OAP}$
	2. Settore Circolare $OAP$
	3. Triangolo $\overset{\triangle}{OAT}$
- In particolare per un fatto di inclusione:
$$
\begin{array}
\ 
\text{Area }\overset{\triangle}{OAP}\leq \text{ Area settore circolare }OAP\leq\text{ Area }\overset{\triangle}{OAT} \\
= \displaystyle{\frac{\sin(x)}{2}\leq \displaystyle{\frac{x}{2}}}\leq \displaystyle{\frac{\tan(x)}{2}}, x\in\left[ 0, \displaystyle{\frac{\pi}{2}} \right]
\end{array}
$$
- Poichè tutte le funzioni sono [[../Funzioni/Introduzione Funzioni#Funzioni Pari e Dispari|dispari]]
$$
|\sin(x)| \leq |x| \leq |\tan(x)|
$$
- Divido tutto per $sen(x)$
$$
1\leq |\displaystyle{\frac{x}{\sin(x)}}|\leq \displaystyle{\frac{1}{|\cos(x)|}}, x\in\left( - \displaystyle{\frac{\pi}{2}}, \displaystyle{\frac{\pi}{2}} \right)\setminus\{0\}
$$
- Per il [[Limiti#Teorema dei due Carabinieri|teorema dei due carabinieri]]
$$
\begin{array}
\ \lim\limits_{x\to 0}1 = 1 \\
\lim\limits_{x\to 0} \displaystyle{\frac{1}{|\cos(x)|}}=1 \\
\text{Quindi} \\
\lim\limits_{x\to 0} \displaystyle{\frac{|x|}{|\sin(x)|}}=1
\end{array}
$$
- In fine, facciamo l'inverso, quindi:
$$
\lim\limits_{x\to 0} \displaystyle{\frac{sen(x)}{x}}=1
$$
>[!info] Coseno
>$\lim\limits_{x\to 0} \displaystyle{\frac{1-\cos(x)}{x^2}}= \displaystyle{\frac{1}{2}}$

- Dimostraimolo tramite il limite precedente
$$
\lim\limits_{x\to 0} \displaystyle{\frac{1-\cos(x)}{x^2}}\cdot \displaystyle{\frac{1+\cos(x)}{1+\cos(x)}}=\lim\limits_{x\to 0} \displaystyle{\frac{1+\cos(x)}{x^2}}\cdot \displaystyle{\frac{1}{1+\cos(x)}}= \displaystyle{\frac{1}{2}}
$$
## Riassumendo
---
$$
\begin{cases}
e^x=1+x+\circ(x) \text{ per }x\to 0 \\
\log(1+x) = x+\circ(x) \text{ per }x \to 0 \\
\sin(x)=x+\circ(x) \text{ per }x\to 0 \\
\cos(x)=1- \displaystyle{\frac{x^2}{2}}+\circ(x) \text{ per }x\to 0 \\
\tan(x)=x+\circ(x) \text{ per }x\to 0
\end{cases}
$$
