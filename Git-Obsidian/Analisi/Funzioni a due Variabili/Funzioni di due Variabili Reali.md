## Funzione
---
>[!info] Definizione
>Sia $A \subseteq \mathbb{R}^2$, considerando
>$$
>\begin{array}
\ f:A\to\mathbb{R} \\
(x,y)\mapsto f(x,y)
\end{array}
>$$

### Grafico di una Funzione in $\mathbb{R}^3$
>[!tip] Definizione
>$$
G_{f}=\{ (x,y,z)\in\mathbb{R}^2 :z=f(x,y)\}
>$$

### Curva di Livello
>[!tip] Definizione
>Sia $f:\mathbb{R}^2\to\mathbb{R}$
>$(x,y)\mapsto f(x,y)$
>Chiamiamo ***linea o curva di livello*** di $f$ l'insieme:
>$$\{ (x,y)\in\mathbb{R}^2 : f(x,y)=c\}$$

![[attachements/funzioneGransasso.png]]

### Dominio
>[!tip] Rappresentazione
>Il dominio di una funzione $f$ in $\mathbb{R}^3$ è rappresentabile come un grafico in $\mathbb{R}^2$

#### Es
##### Determinare e Disegnare il dominio
$$f(x,y)=\sqrt{ 1-x^2-y^2 }$$
- Il dominio in forma "insieme":
$$
D:\{ (x,y)\in\mathbb{R}^2 :\underbrace{ 1-x^2-y^2\geq 0 }_{\displaystyle x^2+y^2\leq 1 }\}
$$
- Rappresentazione Grafica:
![[attachements/Pasted image 20231204153447.png|400]]
##### Es
$$
f(x,y)=\sqrt{ x^2 y^2 -4 }
$$
- Il dominio in forma "insieme":
$$
D:\{ (x,y)\in\mathbb{R}^2 :\underbrace{ x^2+y^2 -4\geq 0 }_{\displaystyle x^2+y^2\geq 2 }\}
$$
- Rappresentazione Grafica:
![[attachements/Pasted image 20231213145237.png|400]]

## Estremanti Locali
---
>[!info] Definizione
>Sia $A\subseteq\mathbb{R}^2$, sia $f:A\to\mathbb{R}$
>Sia $(x_{0},y_{0})\in A$
>
>>[!tldr] Minimo
>>Diciamo che $(x_{0},y_{0})$ è un punto di minimo locale per $f$ se:
>>$\exists$ un intorno $\mathrm{U}_{(x_{0},y_{0})}:$
>>$$f(x_{0},y_{0})\leq f(x,y),\forall(x,y)\in\mathrm{U}\cap A$$
>
>>[!tldr] Massimo
>>Diciamo che $(x_{0},y_{0})$ è un punto di massimo locale per $f$ se:
>>$\exists$ un intorno $\mathrm{U}_{(x_{0},y_{0})}:$
>>$$f(x_{0},y_{0})\geq f(x,y),\forall(x,y)\in\mathrm{U}\cap A$$

### Fermat per funzioni a due Variabili
>[!info] Teorema
>Sia $A\subseteq\mathbb{R}^2,f:A\to\mathbb{R}$, $A$ [[Elementi di Algebra Lineare e Geometria Analitica#Insiemi Aperti e Chiusi|aperto]]
>Sia $(x_{0},y_{0})\in A$ e supponiamo che $f$ sia [[Calcolo Differenziale#Derivabilità|derivabile]] in $(x_{0},y_{0})$
>Se $(x_{0},y_{0})$ è estremante locale:
><u>Allora</u>
>$$\nabla f(x_{0},y_{0})=(0,0)$$
>
>>[!done] A parole
>>Se il punto è un estremante locale allora il [[Calcolo Differenziale#Gradiente|gradiente]] è pari a $(0,0)$

#### Dimostrazione
Sia $g(x)=f(x,y_{0})$
- Se $(x_{0},y_{0})$ è un estremante locale per $f$, allora $x_{0}$ è un estremante locale per $g$
Inoltre $g$ è derivabile in $x_{0}$ 
- Poichè $f$ è derivabile in $(x_{0},y_{0})$ e $x_{0}$ è punto interno ($A$ insieme aperto)

Quindi applicando il [[../Calcolo Differenziale/Teoremi basati sulle Derivate#Teorema di Fermat|teorema di Fermat]] a $g$ deduco:
$$
g'(x_{0})=\displaystyle\frac{ \partial f }{ \partial x } (x_{0},y_{0})=0
$$
- Analogamente in $y$