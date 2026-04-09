## Teorema dell'Estensione Lineare
---
>[!Teorema]
>Sia $V$ uno [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Spazio Vettoriale|spazio vettoriale]] su $\mathbb{K}$
>Sia $v_{1},\dots,v_{n}$ una sua [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Base|base]]
>Sia $U$ uno *spazio vettoriale* su $\mathbb{K}$ 
>Sia $u_{1},\dots,u_{n}$ un insieme di vettori di $U$
><u>Allora</u>
>Esiste ***una e una sola*** [[1 - Applicazioni Lineari#Applicazione Lineare|applicazione lineare]]:
>$$f:V\to U:f(v_{1})=u_{1},\dots,f(v_{n})=u_{n}$$

### Dimostrazione
>Sia $v\in V$

Allora, per il ***teorema delle coordinate***:
$$
\exists! a_{1},\dots,a_{n}\in \mathbb{K}:v=a_{1}v_{1}+\dots+a_{n}v_{n}
$$
- Quindi dato che $f$ è ***lineare***
$$
f(v) = a_{1}f(v_{1})+\dots+a_{n}f(v_{n})=a_{1}u_{1}+\dots+a_{n}u_{n}
$$
>[!done] Conclusione

Quindi esiste ed è ***unicamente determinata***

#### Esempio
>*Sia* $V=\mathbb{R}^2=U$ *dire se esiste e se è unica $f:V\to U$ lineare tale che* $f(e_{1})=(2,1), f(e_{2})=(-1,3)$

Poiché $e_{1},e_{2}$ sono una *base*, esiste ed è unica una tale $f$
- In effetti ogni $v=(x,y)\in V$ si scrive $v=xe_{1}+ye_{2}$ e quindi $f(v)=xf(e_{1})+yf(e_{2})=xu_{1}+yu_{2} =(2x-y,x+3y)$
Ad esempio:
$$
f(5,-3)=f(5e_{1},-3e_{2})=5f(e_{1})-3f(e_{2})=5(2,1)-3f(e_{2})=(13,-4)
$$

#### Esempio
>$f:\mathbb{R}^2\to\mathbb{R}^2$, $v_{1}=(2,-1), v_{2}=(4,-2)$

>[!question] Esiste un'unica applicazione lineare tale che $f(v_{1})=(1,0),f(v_{2})=(3,-1)$?

Osserviamo subito che $v_{2} = 2v_{1}$, quindi se $f$ è *lineare* $f(v_{2})=2f(v_{1})$
- Ma $(3,-1)\neq2(1,0)$

>[!fail] E quindi non esiste una tale $f$

>[!question] Esiste $f$ tale che $f(v_{1})=(1,1),f(v_{2})=(2,2)$? Se si, è l'unica?

Osserviamo che $v_{2}=2v_{1}$ e $f(v_{2})=2f(v_{1})$ quindi la condizione richiesta è *compatibile* con la ***linearità***

Completiamo $v_{1}$ a una [[../Basi dell'algebra/2 - Campi e Spazi Vettoriali#Base|base]] di $\mathbb{R}^2$, ad esempio $\underbrace{ v_{1} }_{ (2,-1) },\underbrace{ e_{1} }_{ (1,0) }$
Per ogni scelta di $u_{2}\in\mathbb{R}^2$ per il teorema precedente
- Esiste una $f$ lineare tale che $f(v_{1})=(1,1),f(e_{1})=u_{2}$

>[!fail] No, ne esistono infinite

### Proprietà del Teorema
>[!info] Proprietà
>Siano $V,U$ spazi vettoriali su $\mathbb{K}$
>Siano $v_{1},\dots,v_{n}$ base di $V$
>Siano $u_{1},\dots,u_{m}$ base di $U$
>Dato $f(v_{1})\in U$, 
>$$\exists! a_{11},\dots,a_{m1} :f(v_{1})=a_{11}u_{1}+\dots+a_{m_{1}}u_{m}:f(v_{n})=a_{1n}u_{1}+\dots+a_{mn}u_{m}$$
>>[!done] Conclusione
>>Ho ottenuto una "matrice $m\times n$" cioè una tabella di numeri con $m$ righe e $n$ colonne

Per il teorema precedente, questa matrice:
$$
A=\begin{pmatrix}
a_{11}\dots a_{1n} \\
\dots\dots \\
a_{m1}\dots a_{mn}
\end{pmatrix}
$$
Determina $f$ perché mi dice cosa fa $f$ ai vettori $v_{1},\dots,v_{n}$, e quindi a ***tutti gli altri vettori***

#### Esempio
>$V=\mathbb{R}^3$,  *Base:*  $v_{1}=(1,1,0),v_{1}=(1,0,-1),v_{3}=(0,1,2)$
>$U=\mathbb{R}^2$ , *Base:* $u_{1}=(0,2),u_{2}=(-1,0)$

$f:V\to U, f(x,y,z)=(x-z,2y-z)$

- $f(v_{1})=(1,2)=1u_{1}-1u_{2}$
- $f(v_{2})=(2,1)=\frac{1}{2}u_{1}-2u_{2}$
- $f(v_{3})=(-2,0)=0u_{1}+2u_{2}$

Otteniamo quindi la ***matrice***:
$$
\begin{pmatrix}
1 & \frac{1}{2} & 0 \\
-1  & -2  & 2
\end{pmatrix}
$$
##### Osservazione
>La matrice ottenuta ***dipende dalla scelta delle basi***

Scegliendo ***basi diverse*** per $V,U$ la stessa $f$ avrebbe prodotto una ***matrice diversa***

