## Applicazione Lineare
---
>[!info] Definizione
>Sia $\mathbb{K}$ un [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Campo|campo]] e siano $V,U$ [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Spazio Vettoriale|spazi vettoriali]] su $\mathbb{K}$
>Un'[[../Basi dell'algebra/1 - Introduzione#Definizione|applicazione]] $f:V\to U$ si dice ***lineare*** se è compatibile con le operazioni di $U$ e $V$
>$$f(v_{1}+v_{2})=f(v_{1})+f(v_{2}), \quad\forall v_{1},v_{2} \in V$$
>>[!done] A parole
>>A sinistra dell'uguaglianza *applico* $f$ ad una *somma di elementi* di $V$, ottenendo un elemento di $U$
>>A destra dell'uguaglianza *applico* $f$ ai due elementi di $V$ e poi *sommo i due elementi* di $U$, ottenendo lo stesso elemento di prima
>
>$$f(av) = af(v), \quad\forall a \in\mathbb{K}, \forall v \in V$$
>>[!done] A parole
>>A sinistra dell'uguaglianza *applico* $f$ al *prodotto* di $V$ per uno *scalare*, ottenendo un elemento di $U$
>>A destra dell'uguaglianza *applico* $f$ all'elemento di $V$ e *moltiplico* per uno *scalare*, ottenendo lo stesso elemento $U$ di prima

### Esempi
#### Es 1
>$f:\mathbb{R}^3\to \mathbb{R}^2$ con $f(x,y,z)\mapsto(2z,x+y)$

>[!question] È'un applicazione lineare?

>Prendo due vettori generali $v_{1}=(x_{1},y_{1},z_{1}), v_{2}=(x_{2},y_{2},z_{2})$

$$
v_{1}+v_{2} = (x_{1}+x_{2},y_{1}+y_{2},z_{1}+z_{2})
$$

Applico l'applicazione $f$ alla *somma*
$$
\begin{array}
\ f(v_{1}+v_{2}) =(2(z_{1}+z_{2}),(x_{1}+x_{2})+(y_{1}+y_{2})) \\
f(v_{1})+f(v_{2}) = (2z_{1},x_{1}+y_{1})+(2z_{2},x_{2}+y_{2})
\end{array}
$$
- Possiamo notare che la somma è ***equivalente***

Controlliamo il *prodotto*
$$
\begin{array}
\ f(av)=(2az,ax+ay) \\
af(v)=a(2z,x+y)
\end{array}
$$
- Anche in questo caso è possibile notare l'***uguaglianza***

>[!done] Si, $f$ è un'applicazione lineare

#### Es 2
>$f:\mathbb{R}^2\to\mathbb{R}^2$ con $f(x,y) \mapsto (2x,y^2)$

>[!question] È un'applicazione lineare?

>Prendiamo due vettori di $V$, $v_{1}=(x_{1},y_{1}), v_{2}=(x_{2},y_{2})$

Applico l'applicazione $f$ alla *somma*
$$
\begin{array}
\ f(v_{1}+v_{2}) = f(x_{1}+x_{2},y_{1}+y_{2}) =(2(x_{1}+x_{2}),(y_{1}+y_{2})^2) \\
f(v_{1})+f(v_{2})=(2x_{1},y_{1}^2)+(2x_{2},y_{2}^2) = (2(x_{1}+x_{2}),y_{1}^2+y_{2}^2)
\end{array}
$$

- Possiamo subito notare la ***differenza*** fra i risultati

>[!fail] No, $f$ non è un'applicazione lineare

#### Es 3
>$f:\mathbb{R}^2\to\mathbb{R}^3$ con $f(x,y)\mapsto (0,x+y,1)$

>[!question] È un'applicazione lineare?

Controllo la *somma*
$$
\begin{array}
\ f(v_{1}+v_{2}) = f(x_{1}+x_{2},y_{1},y_{2}) = (0,x_{1}+x_{2}+y_{1}+y_{2},1) \\
f(v_{1})+f(v_{2})=(0,x_{1}+y_{1},1)+(0,x_{2}+y_{2},1) = (0,x_{1}+x_{2}+y_{1}+y_{2},2)
\end{array}
$$
- Anche in questo caso i risultati sono ***differenti***

>[!fail] No, $f$ non è un'applicazione lineare

## Proprietà di Applicazioni Lineari
---
### Immagine
>[!info] Definizione
>Siano $V,U$ [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Spazio Vettoriale|spazi vettoriali]] su $\mathbb{K}$
>Sia $f:V\to U$ un'applicazione lineare
>Ricordiamo che $\mathrm{Im}f =\{ u\in U,\exists v\in V:f(v)=u \}$, e che $f$ è [[../../Analisi/Funzioni/Introduzione Funzioni#Funzione Surriettiva|suriettiva]] $\Leftrightarrow \mathrm{Im}f=U$
>>[!tip] Proprietà
>>$\mathrm{Im}f$ è un sottospazio vettoriale di $U$

#### Dimostrazione
>$\mathrm{Im}f$ non è un insieme vuoto, poiché $\underline{0}\in\mathrm{Im}f$
>$f(\underline{0})=\underline{0}\implies \underline{0}=v-v\implies f(\underline{0})=f(v)-f(v)=\underline{0}$

>[!dim] Vediamo che, se $u_{1},u_{2}\in\mathrm{Im}f$ allora $u_{1}+u_{2}\in\mathrm{Im}f$

In effetti $u_{1}\in\mathrm{Im}f$ significa che $\exists v_{1}\in V:f(v_{1})=u_{1}$
- Analogamente $u_{2}\in\mathrm{Im}f$ significa che $\exists v_{2}\in V:f(v_{2})=u_{2}$

Ma allora $\exists v_{1}+v_{2} \in V:f(v_{1}+v_{2})=f(v_{1})+f(v_{2})=u_{1}+u_{2}\in \mathrm{Im}f$

Inoltre se $u\in \mathrm{Im}f$, cioè $u=f(v), v\in V$ e $a\in\mathbb{K}$,
- Allora $f(av)=af(v)=au$, cioè $au\in\mathrm{Im}f$

### Nucleo
>[!info] Definizione
>Sia $f:V\to U$ un'***applicazione lineare***
>Definisco ***nucleo*** di $f$ come:
>$$\mathrm{ker}f=\{ v\in V:f(v)=\underline{0} \}$$
>>[!tip] Proprietà
>>$\mathrm{ker}f$ è un [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Sottospazio Vettoriale|sottospazio vettoriale]] di $V$

- $\mathrm{ker}$ significa nucleo in inglese (***kernel***)

#### Dimostrazione
>Come mostrato prima $\underline{0}\in\mathrm{ker}f$ poiché $f(\underline{0})=\underline{0}$

Se $v_{1},v_{2}\in\mathrm{ker}f$ allora:
- $f(v_{1})=\underline{0}, f(v_{2})=\underline{0}$
	- *Definizione di nucleo*
- $f(v_{1}+v_{2})=f(v_{1})+f(v_{2})=\underline{0}+\underline{0} = \underline{0} \implies v_{1}+v_{2}\in\mathrm{ker}f$
	- *Definizione Linearità*

Analogamente per la **moltiplicazione**:
- Se $a\in\mathbb{K}$ e $v\in\mathrm{ker}f$ cioè $f(v)=\underline{0}$
- Allora $f(av)=af(v)=a\cdot \underline{0}=\underline{0}$
E quindi $av\in\mathrm{ker}f$

### Iniettività e Nucleo
>[!info] Proprietà
>Sia $f:V\to U$ un'*applicazione lineare* 
>$f$ è [[../../Analisi/Funzioni/Introduzione Funzioni#Funzione Iniettiva|iniettiva]] $\Leftrightarrow \mathrm{ker} f=\{ \underline{0} \}$

#### Dimostrazione
>$\implies$
>Sia $f$ iniettiva

Già sappiamo che $f(\underline{0})=\underline{0}$
- Se $v\in\mathrm{ker}f$, allora $f(v)=\underline{0} = f(\underline{0})$
- Quindi per iniettività $v=\underline{0}\implies\mathrm{ker}f=\{ \underline{0} \}$

>$\impliedby$
>Sia $f:V\to U:\mathrm{ker}f=\{ \underline{0} \}$

Voglio mostrare che $f$ è iniettiva

Siano $v_{1},v_{2}\in V:f(v_{1})=f(v_{2})\implies f(v_{1})-f(v_{2})=\underline{0}$
- Per la proprietà di *linearità*:
	- $\underbrace{ f(v_{1}-v_{2}) }_{ \in\mathrm{ker}f } = \underline{0}$
	- Da qui posso notare che **per ipotesi** $v_{1}-v_{2} = \underline{0}\implies v_{1}=v_{2}$

#### Es 1 - Nucleo
>$f:\mathbb{R}^2\to\mathbb{R}^2, f(x,y)\mapsto(x+y,2x+2y)$

$$
\begin{array}
\ \mathrm{ker}f=\{ (x,y)\in\mathbb{R}^2:f(x,y)=0 \}=\{ (x,y)\in\mathbb{R}^2: \begin{cases}
x+y=0 \\
2x+2y=0
\end{cases}
\}= \\
\{ (x,y)\in\mathbb{R}^2:y=-x \}=\{ (t,-t),t\in \mathbb{R} \}
\end{array}
$$

Conclusione: $\mathrm{ker}f\neq\{ (0,0) \}$, quindi $f$ non è iniettiva

$\mathrm{Im}f=\{ (x+y,2x+2y),x,y\in\mathbb{R} \}=\{ (s,2s),s\in\mathbb{R} \}\neq \mathbb{R}^2 \implies f$ non è suriettiva

#### Es 2 - Nucleo
>$f:\mathbb{R}^2\to \mathbb{R}^2, f(x,y)\mapsto(x+y,x-y)$

>[!question] $f$ è iniettiva?
$$\mathrm{ker}f=\{ (x,y)\in\mathbb{R}^2: \begin{cases}
x+y=0 \\
x-y=0
\end{cases}\}$$
$$
\begin{cases}
x=0 \\
y=0
\end{cases}\implies \mathrm{ker}f=\{ \underline{0} \}
$$
>[!done] $f$ è iniettiva

>[!question] è vero che ogni $u=(z,w)\in\mathbb{R}^2$ si scrive come $(x+y,x-y)$

$\mathrm{Im}f=\{ (x+y,x-y),x,y\in \mathbb{R} \}$ 
$$
\begin{cases}
x+y = z \\
x-y=w
\end{cases}
\Leftrightarrow
\begin{cases}
x+y=z \\
-2y=w-z
\end{cases}
\Leftrightarrow
\begin{cases}
x =\displaystyle{\frac{w+z}{2}} \\
y = -\displaystyle{\frac{w-z}{2}}
\end{cases}
$$
Quindi $\forall(w,z)\in U, \exists(x,y)\in V:f(x,y)=(w,z)$
>[!done] $\mathrm{Im}f=\mathbb{R}^2\implies f$ è suriettiva

Abbiamo mostrato che $f$ è ***iniettiva*** e ***suriettiva***, cioè $f$ è ***biunivoca***
- $\forall u=(z,w)\in U$ esiste ed è unico $V=(x,y)\in V:f(v)=u$
- L'applicazione è dunque ***invertibile***, cioè esiste $f^{-1}$
$$
f^{-1}(z,w)=(\displaystyle{\frac{w+z}{2}}, -\displaystyle{\frac{w-z}{2}})
$$
