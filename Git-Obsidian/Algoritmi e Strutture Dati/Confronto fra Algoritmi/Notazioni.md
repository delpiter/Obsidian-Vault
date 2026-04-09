## Ordini di Grandezza
---
```functionplot
---
title: Crescita Funzioni
xLabel: 
yLabel: 
bounds: [0,10,0,50]
disableZoom: true
grid: true
---
f(x)=2^x
g(x)=x^3
q(x)=x^2
t(x)=x*log(x)
y(x)=x
j(x)=log(x)
b(x) = 1
```

1. $O(1)$
2. $O(log(n))$
3. $O(n)$
4. $O(n\cdot log(n))$
5. $O(n^k)$
6. $O(C^n)$
7. $O(n^n),O(n!)$
>[!info] Siano
>$\forall M>0$ Costante ***arbitrariamente grande***
>$\forall \epsilon>0$ Costante ***arbitrariamente piccolo***
>$\forall a>0$ Costante:
>$$log(n)^M<n^{\epsilon}<n^M<a{\epsilon n}<a{Mn}<\epsilon n!<Mn!<n^{\epsilon n}$$

>[!done] Trattabile 
Un [[../Problemi e Algoritmi#Problemi|problema]] con una soluzione algoritmica di complessità polinomiale si dice ***trattabile***

>[!warning] Intrattabile
>Un [[../Problemi e Algoritmi#Problemi|problema]] con una soluzione algoritmica  maggiore di una polinomiale si dice ***intrattabile***

>[!danger] Insolubile
> Un [[../Problemi e Algoritmi#Problemi|problema]] di cui non si conosce algoritmo che lo risolva si dice ***insolubile***


## $O$-Notation
---
Concetto simile a quello di [[../../Analisi/Taylor/Resto di Peano|o piccolo]] in matematica
La dimensione del [[Complessità di Algoritmi#Tempo di Esecuzione|problema]] per $\text{Example 1}$ è il numero di interi in input
- Una istanza con $100000$ interi è più grande di una con $1000$
- E' ovvio che il tempo di esecuzione cresce con la dimensione dell'istanza

>[!question] Quanto?

Non interessa il numero esatto di istruzioni, si considera solo il **termine dominante**
- Così si ottiene una approssimazione di $T(n)$

Interessa l'andamento della funzione andando verso ***valori sempre più grandi***
- Come per i limiti di funzione, per la complessità di un algoritmo si **seleziona il termine dominante**
- Anche i *coefficienti* diventano non significativi per $n$ molto grandi

L'**ordine di grandezza** di $T(n)$ dipende solo dal termine che cresce di più al crescere di $n$
- Ordine di grandezza si scrive ***O grande***
$f(x) = x^3+6x^2+9x+10$
$$O(f(x)) = O(x^3)$$
Un algoritmo $O(n^3)$ non può essere usato per istanze molto grandi, mentre un algoritmo $O(n)$ è utilizzabile per istanze di dati molto grandi
#### Crescita delle Funzioni
>[!info] Definizione Testuale
>La notazione $O-Grande$ caratterizza un *limite superiore* nel comportamento asintotico di una funzione
>>[!done] In altre parole
>>Questa notazione dice che una funzione cresce non più di un certo ritmo, basato sul termine di grado massimo.

>[!info] $O$ Grande
>La crescita delle funzioni può essere descritta con la notazione ***O Grande***
>>[!tip] Definizione Rigorosa
>>Siano $f$ e $g$ due funzioni da $\mathbb{R}$ a $\mathbb{R}$
>>Diciamo che $f(x)$ è $O(g(x))$ se esistono due costanti $C$ e $K$ tali per cui 
>>$$f(x)\leq C\cdot g(x)$$ quando $x>k$
>
>Se $f(n)$ sta "*sotto*" a $g(n)$ da un certo $n_{0}$ in poi (***definitivamente***)
>$$f(n)=O(g(n))\implies f(n)\leq cg(n)$$
>Con $n>0, c>0, \forall n\geq n_{0}$
>Quando si analizza la crescita di **funzioni di complessità**, $f(x), g(x)$ si assumono sempre positive
>Quando si vuole dimostrare che $f(x)$ è $O(g(x))$, è sufficiente trovare una coppia $(C,K)$ per cui vale la relazione.
>- Notare che ce ne possono essere infinite


##### Esempio
>Dimostrare che $f(x)=x^2+2x+1$ è $O(x^2)$

Per $x>1$ abbiamo:
$$
x^2+2x+1 \leq 2x^2+ x^2 \implies x^2 +2x+1 \leq4x^2
$$
- Quindi per $C=4$ e $K=1:f(x)\leq Cx^2$ quando $x>k$
- $f(x)$ è $O(x^2)$

## $\Omega$-Notation
---
>[!info] Definizione Testuale
>La notazione $\Omega$ grande caratterizza un *limite inferiore* nel comportamento asintotico di una funzione
>>[!done] In altre parole
>>Questa notazione dice che una funzione cresce al massimo veloce come un certo ritmo, basato come la notazione-$O$ sul termine di grado massimo

>[!info] $\Omega$ Grande
>L'opposto della notazione $O$ Grande
>>[!tip] Definizione
>>Siano $f$ e $g$ due funzioni da $\mathbb{R}$ a $\mathbb{R}$
>>Diciamo che $f(x)$ è $\Omega(g(x))$ se esistono due costanti $c_{1}$ e $n_{0}$ tali per cui 
>>$$f(x)\geq c_{1}\cdot g(x)$$ quando $x>n_{0}$

## $\Theta$-Notation
---

>[!info] Definizione Testuale
>La notazione $\Theta$ grande caratterizza un *limite superiore e inferiore* nel comportamento asintotico di una funzione.
>>[!done] In altre parole
>>Questa notazione dice che una funzione cresce *precisamente* ad un certo ritmo, basato, nuovamente sul termine di grado maggiore
>
>>[!done] Per dirlo in un altro modo
>>La notazione caratterizza la crescita di una funzione fra un fattore costante *superiormente* e un fattore costante *inferiormente* 
>>Questi due fattori ***devono essere diversi***

>[!info] $\Theta$ grande
>Approssimazione stretta sia $O$ grande che $\Omega$ grande
>>[!tip] Definizione
>>Siano $f$ e $g$ due funzioni da $\mathbb{R}$ a $\mathbb{R}$
>>Diciamo che $f(x)$ è $\Theta(g(x))$ se esistono tre costanti $c_{1},c_{2},n_{0}$ tali per cui 
>>$$c_{1}g(n)\leq f(n)\leq c_{2}g(n)$$ quando $n \geq n_{0}$

## $\circ/\omega$-Notation
---
>[!info] Analogamente
>Esistono notazioni per l'analisi asintotica per confrontare due funzioni solo strettamente $>$ o $<$ 
>>[!tip] $\circ$-Piccolo
>>$$f(n)=\circ(g(n))\Leftrightarrow f(n)=O(g(n)) \text{ AND } f(n)\neq \Theta(g(n))$$
>
>>[!tip] $\omega$-Piccolo
>>$$f(n)=\omega(g(n))\Leftrightarrow f(n)=\Omega(g(n)) \text{ AND } f(n)\neq \Theta(g(n))$$

## Ricapitolando
---
>Queste notazioni sono equivalenti al $\geq, \leq, =, <,>$ usato per i numeri applicato alle *funzioni*

Questa modalità di confronto è una ***relazione d'ordine parziale***
>[!info] Totale
>È possibile *confrontare* qualsiasi coppia di valori
>- Per esempio l'insieme dei numeri

>[!info] Parziale
>Non tutti gli elementi sono *confrontabili*
>- Per esempio $f(n) = n$ e $g(n)=n^{sin(n)+1}$

```functionplot
---
title: Relazione di Ordine Parziale
xLabel: 
yLabel: 
bounds: [0,25,0,25]
disableZoom: true
grid: true
---
f(x) = x
g(x) = x^2
c(x) = x^(1+sin(x))
```

## Limiti e Ordini di Grandezza
---
$$
\begin{array}
\ \text{Se } \lim\limits_{n\to +\infty} \displaystyle{\frac{f(n)}{g(n)}} = c \neq 0\implies f(n)=\Theta(g(n)) \\
\text{Se } \lim\limits_{n\to +\infty} \displaystyle{\frac{f(n)}{g(n)}} =0\implies f(n)=\circ (g(n)) \\
\text{Se } \lim\limits_{n\to +\infty} \displaystyle{\frac{f(n)}{g(n)}} = +\infty \implies f(n)=\omega(g(n))
\end{array}
$$
