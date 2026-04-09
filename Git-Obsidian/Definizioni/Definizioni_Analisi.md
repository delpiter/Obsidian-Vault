## Corrispondenza biunivoca
---
In matematica una corrispondenza biunivoca tra due insiemi $X$ e $Y$, è una relazione binaria tra 
$Y$, tale che ad ogni elemento di $X$ corrisponda uno ed un solo elemento di $Y$, e viceversa
>In particolare, la corrispondenza biunivoca è una relazione di equivalenza.

## Seno e Coseno
---
![[attachements/Seno e Coseno.png]]
## Tangente
![[attachements/Tangente.png]]
## Valori Notevoli
---
|     | 0   |    $\displaystyle{\frac{\pi}{6}}$     |    $\displaystyle{\frac{\pi}{4}}$     |    $\displaystyle{\frac{\pi}{3}}$     | $\displaystyle{\frac{\pi}{2}}$ |
| --- | --- |:-------------------------------------:|:-------------------------------------:|:-------------------------------------:|:------------------------------:|
| sen | $0$ |     $\displaystyle{\frac{1}{2}}$      | $\displaystyle{\frac{\sqrt{ 2 }}{2}}$ | $\displaystyle{\frac{\sqrt{ 3 }}{2}}$ |              $1$               |
| cos | $1$ | $\displaystyle{\frac{\sqrt{ 3 }}{2}}$ | $\displaystyle{\frac{\sqrt{ 2 }}{2}}$ |     $\displaystyle{\frac{1}{2}}$      |              $0$               |

## Notazione numeri complessi in forma goniometrica
---
>[!info] Definizione
>$$
\rho(cos(\theta)+isin(\theta)):=\rho e^{i\theta} \\
>$$
#### Osservazione
$e^{i\pi}=-1\Leftrightarrow e^{i\pi}+1 = 0$

## Notazione Restrizione del dominio
---
>[!example] Notazione
>In una funzione $$f:A\to \mathbb{R}$$
>La notazione $$f_{\displaystyle{|_{A\cap B}}}$$
>Significa guardare $f$ solo in $A\cap B$

## Intervallo degenere
---
>[!info] Definizione
>Si dicono intervalli degeneri gli insiemi del tipo $I=\{ a \}$ ove $a\in\mathbb{R}$

## Coefficiente Binomiale
---
>[!info] Notazione
>$$\binom{n}{k} = \displaystyle{\frac{n!}{k!(n-k)!}}$$

>Si legge $n$ su $k$
## Formula del Binomio di Newton
---
>[!info] Formula
>$$(a+b)^n=\sum^n_{k=0}\binom{n}{k} \underbrace{ a^{n-k}b^k }_{ \text{*} }$$ 
>>[!done] \*
>>Tutte le coppie di esponenti la cui somma è $n$

- Dimostrabile per induzione

## Punto interno in un Intervallo
---
>[!info] Definizione
>Un punto interno ad un [[../Analisi/Funzioni/Introduzione Funzioni#Intervallo|intervallo]] $I$ qualsiasi è un punto che sta dentro all'intervallo $I$ tranne gli estremi dell'intervallo
>$$c\in I\setminus \{ inf(f),sup(f) \}$$

## Rette Sghembe
---
>[!info] Definizione
>Due rette sono sghembe se non hanno punti in comune e se non esiste alcun piano che le contiene entrambe

## Numeri Congrui a Modulo $n$
---
>[!info] Definizione
>Sia $n\in\mathbb{Z}, n\geq 2$, siano $a,b \in \mathbb{Z}$
>Definisco $a\equiv b(n)$
>>[!done] A parole
>>"$a$ congruo a $b$ modulo $n$"
>Se $a-b$ è multiplo di $n$, cioè
>$$\exists h\in\mathbb{Z}:a-b=hn$$

### Esempi
> $n=5$

- $23\equiv8 \ (5)$
- $23 \cancel{ \equiv } 20(5)$

## If You Know You Know
---
>[!abstract] ‎ 
>I want to
>$$\int_{10}^{13}2x dx $$
>With you


## Matrice Trasposta
---
>[!info] Definizione
>Data una matrice $M$, la ***matrice trasposta*** di $M$ è la matrice $M^T$ che ha per colonne le righe di $M$

>[!example] Esempio

$$
M=\begin{pmatrix}
3 & 1 & 7 \\
-1 & 0 & 4
\end{pmatrix}, M^T=\begin{pmatrix}
3 & -1 \\
1 & 0 \\
7 & 4
\end{pmatrix}
$$
### Osservazione
>*Per come è definito il [[../Analisi/Funzioni a due Variabili/Elementi di Algebra Lineare e Geometria Analitica#Prodotto tra Matrici (Riga $ times$ Colonna]]|prodotto%20riga%20per%20colonna)*
>
$$
(A\times B)^T = A^T \times B^T
$$

## Regola di Sarrus
---
>[!abstract] Regola
>Scorciatoia per calcolare il ***determinante*** di una *matrice* $3\times 3$

![[attachements/Sarrus Rule.png]]

## Prodotto Vettoriale
---
>[!info] Definizione
>Il [[../Algebra e Geometria/Applicazioni/7 - Determinante di una Matrice#Determinante|determinante]] permette di formulare la regola per calcolare il ***prodotto vettoriale***
>- Una *operazione* che associa ad una ***coppia di vettori*** un ***vettore***
>$$\mathbb{R}^3\times \mathbb{R}^3\to\mathbb{R}^3$$
>$$(v,u)\mapsto v\wedge u$$

Se $v=(a_{1},a_{2},a_{3}),u=(b_{1},b_{2},b_{3})$ allora definiamo
$$
v\wedge u = \det\begin{pmatrix}
a_{1} & a_{2} & a_{3} \\
b_{1} & b_{2} & b_{3} \\
e_{1} & e_{2} & e_{3}
\end{pmatrix}=e_{1}(a_{2}b_{3}-a_{3}b_{2})-e_{2}(a_{1}b_{3}-a_{3}b_{1})+e_{3}(a_{1}b_{2}-a_{2}b_{1})
$$

>[!abstract] In particolare

Il prodotto vettoriale eredita le *proprietà* del ***determinante***
- È alternante, cioè $v\wedge u =- u\wedge v$
- È multilineare, cioè $(a_{1}v_{1}+a_{2}av_{2})\wedge u=a_{1}(v_{1}\wedge u)+a_{2}(v_{2}\wedge u)$
	- $v\wedge(a_{1}u_{1}+a_{2}u_{2})=a_{1}(v\wedge u_{1})+a_{2}(v\wedge u_{2})$

