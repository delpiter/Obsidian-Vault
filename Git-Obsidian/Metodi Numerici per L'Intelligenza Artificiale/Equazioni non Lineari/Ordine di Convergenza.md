>[!definizione] Definizione
>Sia data una *successione di iterati* $\{ x_{k} \}$, generata da un [[Soluzione Numerica di Funzioni non Lineari|metodo numerico convergente]] ad un limite $\alpha$ e sia $e_{k}=x_{k}-\alpha$.
>Se esistono due numeri reali $p\geq1$ e $c>0$, tali che:
>$$\lim\limits_{k\to +\infty} \frac{|e_{k+1}|}{|e_{x}|^p}=c$$
>Si dice che la successione ha ***ordine di convergenza*** $p$ e fattore di convergenza $c$.

Ciò significa che esiste un indice $k_{0}$ tale che per $k>k_{0}$ risulta:
$$
|e_{k+1}|\approx c|e_{k}|^p
$$
## Ordini
---
>[!help] $p=1$
>Se $p=1$ occorre che $c<1$ affinché la successione sia [[../../Analisi/Successioni/Limiti di Successioni#Definizioni|convergente]].
>In tal caso si dice convergente ***linearmente***.

$$
|e_{k+1}|\approx c|e_{k}|\approx c^2|e_{k-1}|\approx\dots\approx c^{k+1}|e_{0}|
$$
Tanto pi è piccolo $c<1$ tanto migliore è la convergenza.

>[!abstract] $1<p<2$
>Se $1<p<2$ la convergenza si dice ***superlineare***.

>[!cite] $p=2$
>Se $p=2$ la convergenza si dice ***quadratica***.

### Significato di Ordine
> Sia $e_{k}=x_{k}-\alpha$, supponiamo che $|e_{k}|\leq \frac{1}{2}10^{-n}$, cioè la radice $x_{k}$, ha $n$ ***decimali corretti***.

Se il metodo iterativo ha ordine di convergenza $p$, allora

>[!tip]
>$$|e_{k+1}|\approx c|e_{k}|^p\leq c\left( \frac{1}{2}10^{-n} \right)^p=\frac{c}{2p}10^{-pn}$$
>>[!quote] A parole
>>La radice $x_{k}$ ha $p\cdot n$ ***decimali corretti***.
>>Il numero di decimali corretti tende ad essere moltiplicato per $p$ ad ogni passo solo per $k\to \infty$.

## Convergenza Locale e Globale
---
>[!help] Convergenza Globale
>Un metodo numerico convergente ha una ***convergenza globale*** se la convergenza è *garantita* qualunque sia l'ampiezza dell'intervallo iniziale $[a,b]$


>[!hint] Convergenza Locale
>Un metodo numerico convergente ha una ***convergenza locale*** se la convergenza **non*** è *garantita* qualunque sia l'ampiezza dell'intervallo iniziale $[a,b]$

### Teorema di Convergenza Locale
>[!definizione] Teorema
>Se $f:[a,b]\mapsto \mathbb{R}$ soddisfa le seguenti ipotesi
>1. $f(a)\cdot f(b)<0$
>2. $f,f',f''$ sono continue in $[a,b]$ ($f\in C^2[a,b]$)
>3. $f'(x)\neq 0 \forall x \in[a,b]$
>
><u>Allora</u>
>Esiste un intorno $I\subset[a,b]$ dell'unica radice $\alpha\in(a,b)$ tale che:
>- Se $x\in I$ allora la successione di Newton $\{ x_{i} \}_{i\geq1}$ converge ad $\alpha$

>[!cite] Teorema di Convergenza Globale del metodo di Newton
>Sia $f(x)\in C^2[[../../Analisi/Funzioni/Introduzione Funzioni#Intervallo|intervallo]] chiuso e limitato, ***sono verificate*** le seguenti condizioni:
>1. $f(a)f(b) < 0$
>2. $f'(x) \ne 0 \quad \forall x \in [a,b]$
>3. $f''(x) > 0 \quad \textit{oppure} \quad f''(x) < 0 \quad \forall x \in [a,b]$
>4. $\left| \frac{f(a)}{f'(a)} \right| < b - a \quad \quad\left| \frac{f(b)}{f'(b)} \right| < b - a$
>>[!quote] A parole
>>L'intersezione della retta che collega gli estremi cade internamente all'intervallo $[a,b]$
>
><u>Allora</u>
>Il [[Localizzare le Radici#Metodo di Newton|metodo di Newton]] converge all'unica soluzione $\alpha\in[a,b]$.

> ***Spiegazione***:

- La condizione 1. assicura che una radice **esista**.
- La condizione 2. assicura che non vi siano **tangenti orizzontali**.
- La condizione 3. assicura che la **convessità o concavità sia mantenuta** su tutto $[a,b]$.
- La condizione 4. assicura che le **tangenti agli estremi intersecano l'asse** $x$ internamente ad $[a,b]$.

