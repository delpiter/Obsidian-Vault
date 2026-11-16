![[../../Machine Learning/Reti Neurali/Training|Training]]
## Learning Rate
---
>[!question] Come scegliere il Learning Rate?

>[!definizione]
>Una funzione $f:\mathbb{R}^{n}\to \mathbb{R}$ è detta ***lipshitziana*** se esiste una costante $L>0$ tale che per ogni coppia di punti $x,y\in\mathbb{R}^{n}$ valga la seguente *disuguaglianza*:
>$$\| f(x)-f(y) \| \leq L\| x-y \| $$
>>[!quote] Significato
>> Una funzione Lipschitziana ha una ***crescita limitata***, la *variazione verticale* della funzione in due punti del dominio **non può** essere più grande della *variazione orizzontale* moltiplicata per $L$ (*costante di Lipschitz*).

> Esempio

La funzione $f(x)=\sin(x)$ è una funzione lipschitziana con costante $L=1$.
```functionplot
---
title: 
xLabel: 
yLabel: 
bounds: [-4,4,-4,4]
disableZoom: false
grid: true
---
f(x)=sin(x)
g(x)=x
h(x)=-x
```
>[!check] Teorema
> Ipotizziamo che $f:\mathbb{R}^{n}\to \mathbb{R}$ sia una funzione *convessa e differenziabile* con gradiente $\nabla f(x)$ *continuo* di **Lipschitz** con costante $L$, e che esista  $x^{*}$ tale che $\nabla f(x^{*})=0$ cioè esiste un ***punto stazionario***.
> <u>Allora</u>
> La *successione degli iterati* del metodo della discesa del gradiente:
> $$x^{k+1}=x^{k}-\eta \nabla f(x^{k})$$
> converge ad $x^{*}$ a patto che
> $$0<\eta< \frac{2}{L}$$ 

 Sfortunatamente *quasi tutti i problemi* di ottimizzazioni nell'allenamento di reti neurali sono ***non convessi***.

