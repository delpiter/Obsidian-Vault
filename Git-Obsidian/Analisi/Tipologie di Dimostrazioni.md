[[Concetti Base#Teorema|Teoremi]]
## Dimostrazione per Assurdo
#### Es Teorema
- Ipotesi
	- Se $q^2 = 2$ $\Rightarrow$ $q\notin \mathbb{Q}$ 
	- Supponiamo per assurdo che:
$$\exists \; q \in \mathbb{Q} : q^2 = 2$$
- Sia $q$ della forma $\displaystyle{\frac{n}{m}}$ con
	- $n, \;m \in \mathbb{Z}$
	- $m \neq 0$
- Posso supporre che sia ridotta ai minimi termini
- Dall'ipotesi assurda so che:
$$\displaystyle{\frac{n^2}{m^2} = 2 \Leftrightarrow n^2 = 2m^2 }$$
- $n^2$ è pari
- $n$ è pari
- Se $n$ è pari è della forma:
$$n=2p,\; n\in \mathbb{Z}$$
- Quindi
$$n^2 = 2m^2 \Leftrightarrow 4p^2=2m^2$$
$$m^2 = 2p^2$$
- Quindi $m^2$ è pari $\Rightarrow$ m è pari
	- ###### CONTRADDIZIONE
		- $\displaystyle{\frac{n}{m}}$ era già ridotta ai minimi termini
		- Non possono avere fattori in comune
# ⨳

## Principio di induzione
- - -
>Tecnica dimostrativa 
>>La tesi è vera se vengono soddisfatte due condizioni
>>>"Passo 0"
>>>"Passo induttivo"
### Quando si usa?
- Quando si deve dimostrare una proprietà che è in funzione dei numeri naturali
#### Passo 0
- $P(n)$ è vera per $n=0$
	- Si sostituisce $n$ con $0$ e si verifica
#### Passo Induttivo
- Data la proprietà $P(n)$ vera (Ipotesi induttiva)
- Dobbiamo dimostrare che $P(n+1)$ sia vera
	- Bisogna fare in modo che $P(n+1)$ sia in funzione di $P(n)$
	$$f(P(n))$$
- Se riusciamo a dimostrare che $P(n+1)$ sia vera allora
$$P(n)\; vera\; \forall n\in \mathbb{N}$$
##### Es
- Dimostrare che
$$1+2+3+4+\dots+n =  \sum_{k=0}^{n} k = \frac{n(n+1)}{2}$$
###### Passo 0
- Dimostrare che $P(0)$ è vera
	- $0 = 0$
###### Passo induttivo
- Dimostrare che se
$$\sum_{k=0}^{n} k = \frac{n(n+1)}{2}$$
Allora
$$\sum_{k=0}^{n+1} k = \frac{(n+1)(n+2)}{2}$$
$$\sum_{k=0}^{n+1} k = \sum_{k=0}^{n} k + n+1 = \frac{n(n+1)}{2} +n+1$$
$$(n+1)\left( \frac{n+2}{2}\right)$$

##### Disuguaglianza di Bernoulli
>[!info] Ipotesi
>Sia $x \in\mathbb{R}:x>-1$ e $n\in\mathbb{N}$ si ha che:
>$$(1+x)^n \geq 1+nx, \forall n\in\mathbb{N}$$
###### Dimostrazione
1. $P(0)$ è vera, infatti: $1\geq1$
2. Verifichiamo che se $(1+x)^n\geq 1+nx$ allora $(1+x)^{n+1}\geq 1+(1+n)x$
$$
(1+x)^{n+1} = (1+x)^{n}(1+x) \underbrace{ \geq }_{ * } (1+nx)(1+x)
$$
- La direzione della disugualianza rimane uguale poichè $1+x$  è sempre maggiore di $0$
- Risolvo la disugualianza
$$
1+x+nx+nx^2\geq 1+x(n+1)$$
## Metodo di bisezione
---
>[!done] Definizione
>Il metodo di bisezione è un procedimento numerico iterativo consiste nel dividere l’intervallo assegnato in due sottointervalli mediante il punto medio $c$

Esempio

![[Limiti/Limiti#Teorema degli Zeri]]