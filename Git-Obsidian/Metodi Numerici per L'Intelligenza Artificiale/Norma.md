> I dati di un problema in generale non sono solo scalari appartenenti ad $\mathbb{R}$.

Possono essere:
- **Vettori** di $\mathbb{R}^n$
- **Matrici** di $\mathbb{R}^{m\times n}$

Diventa necessario introdurre uno strumento matematico che estenda l'[[Errore di Rappresentazione|errore relativo]] (definito per scalari in $\mathbb{R}$), al caso più generale di *vettori* e *matrici*
## Norma Vettoriale
---
>La ***norma di un vettore*** è una funzione che *associa* ad ogni *vettore* una lunghezza non negativa.

>[!done] In altre Parole
>È un modo di quantificare la "*grandezza*" di un **vettore**.

>[!def] Definizione
>Ogni applicazione $\mid\mid \cdot \mid\mid:\mathbb{R}^n a, \mathbb{R}_{+}\cup\{ 0 \}$ si chiama ***norma*** su $\mathbb{R}^n$ se gode delle seguenti proprietà:
>1. $\mid\mid x \mid\mid >0 \quad \forall x \in\mathbb{R}^n$ e $\mid\mid x \mid\mid=0$ se e solo se $x=0$
>>[!hint] La norma di un vettore è sempre non negativa e nulla solo se il vettore è nullo.
>
>2. $\mid\mid\lambda x\mid\mid = \mid\lambda\mid \cdot \mid\mid x\mid\mid\quad \forall \lambda\in\mathbb{R}, y\in\mathbb{R}^n$
>>[!hint] La norma di un vettore scalato è uguale al valore assoluto dello scalare per la norma del vettore.
>
>3. $\mid\mid x+ y\mid\mid \leq \mid\mid x\mid\mid + \mid\mid y\mid\mid\quad \forall x,y\in\mathbb{R}^n$
>>[!hint] La norma di un vettore somma è minore o uguale alla somma delle norme dei due vettori.

### Esempi di Norme
>[!help] Norma Infinito
>$$\mid\mid x \mid\mid_{\infty}=\max\limits_{ i }\mid x_{i}\mid$$

![[InfinityNorm.png|400]]

- $S_{\infty}=\{ x\in\mathbb{R}^2 :\mid\mid x \mid\mid_{\infty}=max\{ \mid x_{1}\mid ,\mid x_{2}\mid\}=1\}$

>[!quote] Norma $1$
>$$\mid\mid x \mid\mid_{1} = \sum_{i=1}^n \mid x_{i}\mid$$

![[Norm_One.png|400]]

- $S_{1}=\{ x\in\mathbb{R}^2:\mid\mid x \mid\mid_{1}\mid x_{1}\mid + \mid x_{2} \mid = 1\}$

>[!summary] Norma $2$
>$$\mid\mid x \mid\mid_{1} = \left[ \sum_{i=1}^n x_{i}^2\right]^{1/2}$$

![[Norm_Two.png|400]]

- $S_{2}=\{ x\in\mathbb{R}^2:\mid\mid x \mid\mid_{2}=\sqrt{ x_{1}^2+x_{2}^2 }=1 \}$

### Teorema
> Le norme appena definite, hanno la proprietà di produrre risultati "***confrontabili***".

>[!cite] Teorema
>Per ogni ***coppia di norme di vettori***, ad esempio $\mid\mid x\mid\mid$ e $\mid\mid x \mid\mid_{*}$, esistono costanti positive $m$ e $M$, $0<m<M\in\mathbb{R}$, tali che $\forall x\in\mathbb{R}^n$
>$$m\cdot\mid\mid x\mid\mid_{*}\leq\mid\mid x \mid\mid \leq M\cdot\mid\mid x\mid\mid_{*}$$
>Si dice che le norme $\mid\mid x\mid\mid$ e $\mid\mid x \mid\mid_{*}$ sono ***equivalenti***.
>>[!done] Quindi tutte le norme su $\mathbb{R}^n$ sono equivalenti.

Si può far vedere che valgono le seguenti disugualianze:

$$
\begin{array}
\ \|x\|_{\infty} \leq \|x\|_2 \leq \sqrt{n} \|x\|_{\infty} \\
\|x\|_{\infty} \leq \|x\|_1 \leq n \|x\|_{\infty} \\
\|x\|_2 \leq \|x\|_1 \leq \sqrt{n} \|x\|_2 \\
\|x\|_{\infty} \leq \|x\|_2 \leq \|x\|_1 \\
\end{array}
$$

L'equivalenza delle norme è importante perché ***garantisce*** che i risultati ottenuti con una *norma* sono validi anche per le altre *norme equivalenti*.
#### Esempio
>Calcolare la norma $\infty,1,2$ del seguente vettore e verificare che vale la relazione.

$$
x=\begin{bmatrix}
1 \\
-4 \\
2
\end{bmatrix}
$$
$$\|x\|_{\infty}\leq\|x\|_{2}\leq\|x\|_{1}$$

- $\|x\|_{\infty}=\max(1,\mid-4\mid,2)=\max(1,4,2)=4$
- $\|x\|_{1}=1+\mid-4\mid+2 =4$
- $\|x\|_{2}=\sqrt{ 1+(-4)^2+2^2 } =\sqrt{ 21 }\cong 4.58257$

$$
4\leq 4.58257\leq 7
$$
## Norma di Matrici
---
>[!def] Definizione
>Sia $\mathbb{R}^{m\times n}$ lo [[2 - Campi e Spazi Vettoriali#Spazio Vettoriale|spazio vettoriale]] delle ***matrici*** $m\times n$ su $\mathbb{R}$, si dice che l'applicazione $\|A\|$ da $\mathbb{R}^{m\times n}$ a $\mathbb{R}_{+}\cup \{ 0 \}$ è norma della matrice $A$ se gode delle *seguenti proprietà*:
>1. $\mid\mid A \mid\mid >0 \quad \forall A\neq 0$ e $\mid\mid A \mid\mid=0\iff A=0$
>>[!hint] La norma di una matrice è sempre non negativa e nulla solo se il vettore è nullo.
>
>2. $\mid\mid\alpha A\mid\mid = \mid\alpha\mid \cdot \mid\mid A\mid\mid\quad \forall A\in M(m\times n), \ \forall \alpha \in\mathbb{R}$
>>[!hint] La norma di una matrice scalata è uguale al valore assoluto dello scalare per la norma della matrice.
>
>3. $\mid\mid A+ B\mid\mid \leq \mid\mid A\mid\mid + \mid\mid B\mid\mid\quad \forall A\in M(m\times p), B\in M(q\times n)$
>>[!hint] La norma di una matrice somma è minore o uguale alla somma delle norme di due matrici.
>
>4. $\|A\cdot B\| \leq \|A\|\cdot \|B\| \ \forall A\in M(m\times p), B\in M(q\times n)$
>>[!hint] La norma del prodotto di due matrici è minore o uguale al prodotto delle norme delle due matrici.

### Norme Compatibili
>Una norma di una matrice $\| \ \|_{M}$ è ***compatibile*** con una data norma vettoriale $\| \ \|_{v}$ se:

$$
\forall A\in\mathbb{R}^{m\times n}, \ \forall x \in\mathbb{R}^n
$$
- Vale la seguente *disuguaglianza*:
$$
\|A_{x}\|_{v}\leq \|A\|_{M} \cdot\|x\|_{v}
$$

Poiché si conoscono le norme di vettori, è interessante definire ***norme di matrici indotte*** dalle corrispondenti norme di vettori.

>[!def] Norme di Matrici Indotte
>Sia $A\in\mathbb{R}^{m\times n}$ e $x\in\mathbb{R}^n, x\neq 0$.
>Si definisce ***norma indotta*** (o *norma naturale*) $\| A\|_{N}$, la più piccola costante $C$ per cui vale la maggiorazione:
>$$\|A_{x}\|_{v}\leq C\cdot\|x\|_{v}$$
>- da cui
>
>$$\|A_{x}\|_{v}\leq \|A\|_{N}\cdot\|x\|_{v}\implies\displaystyle{\frac{\|A_{x}\|_{v}}{\|x\|_{v}}}\leq\|A\|_{N}$$

### Norme Indotte dalle Norme più Comuni
> Consideriamo le norme più comuni su $\mathbb{R}^n$

>[!quote] $p=1$

$$
\|x\|_{1} = \displaystyle\sum^n_{i=1}\mid x_{i}\mid
$$
- $\|A\|_{1}=\displaystyle\max\limits_{i=1,\dots,n}\sum^m_{j=1}\mid a_{ij}\mid$
Si considera la norma di $1$ di tutte le colonne e si prende il valore massimo.

>[!help] $p=\infty$

$$
\|x\|_{1}=\max\limits_{j}\mid x_{j}\mid
$$
- $\|A\|_{\infty}=\displaystyle\max\limits_{i=1,\dots,m}\sum^n_{j=1}\mid a_{ij}\mid$
Si considera la norma di $1$ di tutte le righe e si prende il valore massimo.

>[!summary] $p=2$

$$
\|A\|_{2} =\sqrt{ \rho(A^TA) }
$$
Dove $\rho$ è il ***raggio spettrale***, cioè l'autovettore di modulo massimo della matrice $A^TA$.

#### Richiami
- [[1 - Forme Bilineari#Matrici Simmetriche e Antisimmetriche|Matrici Simmetriche]]
- [[9 - Matrici Diagonali#Autovettore e Autovalore|Autovalore e Autovettore]]
- [[3 - Forme Quadratiche#Tipi di Forme Quadratiche|Tipi di Forme Quadratiche]]

### Teorema
> Anche per le matrici vale il concetto di norme equivalenti

>[!cite] Teorema
>Per ogni ***coppia di norme di matrici***, ad esempio $\mid\mid A\mid\mid$ e $\mid\mid A \mid\mid_{*}$, esistono costanti positive $m$ e $M$, $0<m<M\in\mathbb{R}$, tali che $\forall A\in\mathbb{R}^{n\times n}$ si ha:
>$$m\cdot\mid\mid A\mid\mid_{*}\leq\mid\mid A \mid\mid \leq M\cdot\mid\mid A\mid\mid_{*}$$
>Si dice che le norme $\mid\mid A\mid\mid$ e $\mid\mid A \mid\mid_{*}$ sono ***equivalenti***.

$$
\begin{array}
\ \displaystyle \frac{1}{\sqrt{ n }}\|A\|_{\infty}\leq \|A\|_{2}\leq\sqrt{ n } \|A\|_{\infty} \\
\displaystyle \frac{1}{\sqrt{ n }}\|A\|_{1}\leq \|A\|_{2}\leq\sqrt{ n } \|A\|_{1}
\end{array}
$$
