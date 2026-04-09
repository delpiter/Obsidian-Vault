---

---
![[../Calcolo Differenziale/Derivate#Derivata n-Esima]]
## Polinomio di Taylor
---
>[!info] Definizione
> Sia $I$ [[../Funzioni/Introduzione Funzioni#Intervallo|intervallo]] di $\mathbb{R}$, $f:I\to\mathbb{R}$, $c\in I$,$n\in\mathbb{N}$
> Supponiamo che $f$ sia derivabile $n$ volte
> Sotto queste ipotesi chiamiamo il polinomio di Taylor di $f$ di punto iniziale $c$ e ordine $n$ il polinomio:
> $$T_{c,n}=\sum^n_{k=0} \displaystyle{\frac{f^{(k)}(c)}{k!}}(x-c)^k$$


> Esempio:

- $f(x)=e^x$
- $\displaystyle P_{3}(x)=1+x+\frac{1}{2}x^2+\frac{1}{6}x^3$
```functionplot
---
title: 
xLabel: 
yLabel: 
bounds: [-5,5,-5,5]
disableZoom: false
grid: true
---
f(x)=1+x+(1/2)*x^2+(1/6)*x^3
g(x)=exp(x)
```
