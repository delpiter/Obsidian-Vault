> Ci sono grandezze per le quali un numero non basta. Ad esempio, lo [[Moto Rettilineo|spostamento]].

Per lo spostamento nello spazio tridimensionale occorrono tre grandezze:
- **Modulo**
- **Direzione**
- **Verso**

>[!tldr] Un oggetto definito da queste tre grandezze è detto ***vettore***.

## Versori
---
>[!abstract] Concetto
> Fissata una direzione orientata $r$, esistono infiniti vettori con quella direzione che differiscono per **modulo** e **verso**.
> - Tra questi, esiste un vettore $\vec{u}$ che ha la *stessa direzione* e *verso* di $r$ e *modulo unitario* ($\mid\vec{u}\mid=1$).
> 
> Tutti i vettori di cui sopra possono essere scritti come:
> $$\vec{a}=a\cdot\vec{u}$$
>>[!hint] $\vec{u}$ specifica la direzione e $a$ specifica modulo e verso

Dato un generico vettore $\vec{a}$, il "***suo***" versore può essere espresso come il vettore *diviso per il suo modulo*, ottenendo il versore di $\vec{a}$
$$
\vec{u}_{a}=\frac{\vec{a}}{a}=\frac{\vec{a}}{\mid\vec{a}\mid}
$$
[[Elementi di Algebra Lineare e Geometria Analitica#Vettori nel Piano e nello Spazio|Somma, Differenza e prodotto per uno scalare]].

## Scomposizione di un Vettore
---
>[!help] Idea
>Dato un vettore $\vec{v}$ e due direzioni orientate $r$ e $s$, voglio scrivere:
>$$\vec{v}=\vec{v}_{r}+\vec{v}_{s}=v_{r}\hat{r}+v_{s}\hat{s}$$
> Dove $\hat{r}$ e $\hat{s}$ sono i versori che definiscono le direzioni $r$ e $s$.

Per comodità, solitamente si utilizzano i [[3 - Teoremi su Spazi Vettoriali#Base Canonica|versori allineati con gli assi]].

> Nello spazio servono almeno tre direzioni orientate, la scelta più ovvia è la ***terna cartesiana***.

$$
\vec{v}=v_{x}\hat{i}+v_{y}\hat{j}+v_{z}\hat{k}
$$
- Dove è comune chiamare $(\hat{i},\hat{j},\hat{k})$ i versori degli assi $(x,y,z)$

>[!hint] Somma
>La somma di vettori espressi per mezzo delle componenti è molto semplice, dati:
>$$\begin{array}\ \vec{a}=a_{x}\hat{i}+a_{y}\hat{j}+a_{z}\hat{k} \\\vec{b}=b_{x}\hat{i}+b_{y}\hat{j}+b_{z}\hat{k}\end{array}$$
>Si ha:
>$$\vec{a}+\vec{b}=(a_{x}+b_{x})\hat{i}+(a_{y}+b_{y})\hat{j}+(a_{z}+b_{z})\hat{k}$$

