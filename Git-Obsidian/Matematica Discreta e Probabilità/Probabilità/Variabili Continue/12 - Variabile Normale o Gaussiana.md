## Introduzione
---
>Proviamo a calcolare il seguente ***integrale***

$$
\int e^{ -s^2/2 } \, ds 
$$
>[!fail] Impossibile
>La *funzione di ripartizione* ***NON*** si può scrivere con una formula, tramite funzioni che ***conosciamo***

***È però possibile calolarne***:

$$
\int _{-\infty}^\infty e^{ -s^2/2 }\, ds 
$$
>[!done] Tramite calcoli fatti da ***Gauss***
>$$\sqrt{ 2\pi }$$

![[NormalDistribution.png]]

>[!info] Densità Normale Standard
>$$f(s)=\frac{1}{\sqrt{ 2\pi }}\cdot e^{ -s^2/2 }$$

### Variabile Normale Standard
>[!abstract] Definizione
>Una [[3 - Variabili Aleatorie|Variabile Aleatoria]] con questa densità 
>$$\zeta_{0}\sim N(0,1)$$

##### Valore Atteso e Varianza
>[!summary] Valore Atteso
>$$E[\zeta_{0}]=0$$
>Per la ***simmetria della densità***

>[!tldr] Varianza
>$$Var(\zeta_{0})=E[\zeta^2]-\underbrace{ E[\zeta_{0}]^2 }_{ 0 }$$

$$
E[\zeta_{0}^2] = \int _{-\infty}^\infty s\cdot s\cdot \displaystyle{\frac{1}{\sqrt{ 2\pi }}}\cdot e^{ -s^2/2 }\, ds 
$$
>Utilizziamo l'[[Calcolo Integrale#Integrazione per Parti|Integrazione per Parti]]

- $s=f\qquad s\cdot \displaystyle{\frac{1}{\sqrt{ 2\pi }}}\cdot e^{ -s^2/2 }=g'$
	- $g=\displaystyle\frac{e^{ -s^2/2 }}{\sqrt{ 2\pi }}$

$$
= \left[ \displaystyle\frac{e^{ -s^2/2 }}{\sqrt{ 2\pi }} \right] _{-\infty}^\infty+\int _{-\infty}^\infty \displaystyle\frac{e^{ -s^2/2 }}{\sqrt{ 2\pi }} \, ds = 1 
$$

>[!done] Quindi

$$
Var(\zeta_{0})=E[\zeta_{0}^2]=1
$$

#### Tabella dei Valori
>[!info]
>I valori della funzione di ripartizione $\zeta_{0}$ fra $0$ e $4$ sono riportati in ***una tabella***

>[!hint] Osservazione
>La funzione da $4$ in poi tende già a ***valori trascurabili***, quindi possiamo dire:
>$$\int _{4}^\infty f(s)\, ds = 0$$

[tavole normale standard.pdf](https://virtuale.unibo.it/pluginfile.php/2204077/mod_resource/content/0/tavole%20normale%20standard.pdf)

#### Proprietà
>[!caution] Valori Negativi
>Sia $-4<a<0$
><u>Allora</u> per ***simmetria***
>$$\mathcal{P}(\zeta_{0}<a)=1-\mathcal{P}(\zeta_{0}< -a)$$

##### Esempio
>$\mathcal{P}(\zeta_{0}< -0.68)$

$$
1-\mathcal{P}(\zeta_{0} < 0.68)=1-0.7517 \simeq 0.25
$$
## Variabile Normale
---
>[!definizione] Definizione
>Una variabile $\zeta=\sigma\zeta_{0}+\mu$ dove:
>- $\zeta_{0}\sim N(0,1)$
>- $\sigma,\mu \in\mathbb{R},\quad \sigma>0$
>
>Si dice ***Normale*** e scriviamo
>$$\zeta\sim N(\mu,\sigma^2)$$

#### Valore Atteso e Varianza
>[!summary] Valore Atteso
>$$E[\zeta]=E[\sigma\zeta_{0}+\mu]=\underbrace{ E[\sigma\zeta_{0}] }_{ 0 }+E[\mu]=\mu$$

>[!tldr] Varianza
>$$Var(\zeta)=Var(\sigma\zeta_{0}+\mu)=Var(\sigma\zeta_{0})=\sigma^2Var(\zeta_{0})=\sigma^2$$

## Esempi di Applicazione
---
>[!example] Misurazioni

>[!summary] Altezza di una Persona

>[!abstract] Peso dei Frutti di un Albero

>[!note] Etc...


#### Esempio
>$\zeta_{0}=$ Altezza di un Uomo
>- $\zeta\sim N(173,81)$

$$
\zeta=9\zeta_{0}+173
$$
Ci sono 5 taglie di divise *disponibili*
- XS -> $<162cm$
- S -> $162-170$
- M -> $170-180$
- L -> $180-190$
- XL -> $>190$

Ci sono $500$ ***reclute*** da vestire

>[!question] Quante divise devo ordinare per ogni taglia?

>XS

$\mathcal{P}(XS)=\mathcal{P}(\zeta<162)=\mathcal{P}(9\zeta_{0}+173<162)=\mathcal{P}\left( \zeta_{0}< -1.22 \right)=1-\Phi(1.22)=0.111293$

>S

$\mathcal{P}(S)=\mathcal{P}(162<\zeta< 170)=\mathcal{P}\left( \displaystyle{\frac{162-173}{9}}<\zeta_{0}<\displaystyle{\frac{170-173}{9}} \right)=\mathcal{P}(-1.22<\zeta_{0}< -0.33)=$
$=1-\Phi(-0.33)-\Phi(1.22)=1-\Phi(0.33)-(1-\Phi(1.22))=0.25947$

- $\dots$

#### Esempio
> $X=$ Lunghezza di una foglia di *lauro*

- $\mu=151mm$
- $\sigma=15mm$

>[!question] Determinare la probabilità che la foglia abbia:
>1. Lunghezza tra $120$ e $155mm$
>2. Lunghezza $>185mm$
 
$X=\zeta\sim N(151,225)$

$$
\mathcal{P}(120<\zeta<155)
$$
>[!caution] Standardizzazione

$$
\zeta=\sigma\zeta_{0}+\mu
$$
$\mathcal{P}(120<\sigma\zeta_{0}+\mu<155)=$
- $\mathcal{P}(120-\mu<\sigma\zeta_{0}<155-\mu)$
- $\mathcal{P}\left( \displaystyle{\frac{120-\mu}{\sigma}}<\zeta_{0}< \displaystyle{\frac{155-\mu}{\sigma}} \right)$

>[!hint]
>$\displaystyle{\frac{120-\mu}{\sigma}}$ e $\displaystyle{\frac{155-\mu}{\sigma}}$ si dicono ***standardizzazioni*** di $120$ e $155$


$\mathcal{P}\left( \displaystyle{\frac{120-151}{15}}<\zeta_{0}< \displaystyle{\frac{155-151}{15}} \right)=\mathcal{P}(-2.07<\zeta_{0}<0.27)=$
$=\Phi(0.27)-1+\Phi(2.07)=0.6064+09808-1=0.587$

2. 

$\mathcal{P}(\zeta>185)=\mathcal{P}\left( \zeta_{0}> \displaystyle{\frac{185-151}{15}} \right)=1-\Phi(2,27)=0.0116$