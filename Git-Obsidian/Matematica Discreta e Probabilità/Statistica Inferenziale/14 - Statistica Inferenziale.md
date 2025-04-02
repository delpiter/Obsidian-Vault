## Intervalli di Confidenza
---
> Consideriamo una popolazione

Sia $X$ una [[3 - Variabili Aleatorie|Variabile Aleatoria]] definita sulla *popolazione*
- Supponiamo di conoscere [[1 - Indagine Statistica#Media|media]] e [[3 - Varianza|varianza]] di $X$ ($\mu_{X}$ e $\sigma^2_{X}$)

>[!caution] Consideriamo un campione casuale di $n$ elementi della popolazione su cui calcolare la variabile $X$

$X_{1},\dots,X_{n}$

$$
\overline{X_{n}}=\displaystyle{\frac{X_{1}+\dots+X_{n}}{n}}\sim N\left( \mu_{X}, \frac{\sigma^2_{X}}{n} \right)
$$
- Come visto [[13 -Teorema Centrale del Limite#Alternativa|qui]]

$$
\displaystyle{\frac{\overline{X_{n}}-\mu_{X}}{\sigma_{X}/n}}=\zeta_{0}\sim N(0,1)
$$
>[!note] Notazione
>Sia $0<c<1$ tale che:
>$$\mathcal{P}(-z_{c}<\zeta_{0}<z_{c})=c$$

> Per trovare $z_{c}$:

$$\mathcal{P}(-z_{c}<\zeta_{0}<z_{c})=\Phi(z_{c})-\Phi(-z_{c})=\Phi(z_{c})+\Phi(z_{c})-1=2\Phi(z_{c})-1$$
Deduciamo quindi che:
$$
\Phi(z_{c})= \displaystyle{\frac{1+c}{2}}
$$
![[NotazioneZ_c.png]]

###### Esempi
>$c=0.9$

$$
\Phi(z_{c})=\displaystyle{\frac{1+0.9}{2}}=0.95 \implies z_{c}=1.65
$$
>$c=0.8$

$$
\Phi(z_{c})= \displaystyle{\frac{1+0.8}{2}}=0.9 \implies z_{c}=1.28
$$

>[!warning] Problema
>Nella pratica ***non*** conosciamo $\sigma_{X}$ e $\mu_{X}$

>[!definizione] Definizione
>Il nostro scopo è quello di *stimare* $\sigma_{X}$ e $\mu_{X}$ e anche quello di dare una ***precisione*** o "***confidenza***" di questa *stima*
>$$\mathcal{P}\left( -z_{c}< \displaystyle{\frac{\overline{X_{n}}-\mu_{X}}{\sigma_{X} / \sqrt{ n }}} < z_{c}\right)=c$$

$$
\begin{array}
\ \mathcal{P}\left( \displaystyle{\frac{-z_{c}\cdot \sigma_{X}}{\sqrt{ n }}}< \overline{X_{n}}-\mu_{X}<  \displaystyle{\frac{z_{c}\cdot \sigma_{X}}{\sqrt{ n }}}\right)=c \implies\\
\mathcal{P}\left( \displaystyle{\frac{-z_{c}\cdot \sigma_{X}}{\sqrt{ n }}}-\overline{X_{n}}< -\mu_{X}<  \displaystyle{\frac{z_{c}\cdot \sigma_{X}}{\sqrt{ n }}}-\overline{X_{n}}\right)=c \implies  \\
\mathcal{P}\left( \overline{X_{n}} -\displaystyle{\frac{z_{c}\cdot \sigma_{X}}{\sqrt{ n }}}< \mu_{X}<  \overline{X_{n}}+\displaystyle{\frac{z_{c}\cdot \sigma_{X}}{\sqrt{ n }}}\right)=c
\end{array}
$$
>[!done] A parole
>"***Probabilità*** che la *media reale* sia compresa nell'intervallo sia uguale a $c$"

Sia $\overline{\sigma_{n}}$ la varianza del campione
- $\overline{\sigma_{n}}$ approssima $\sigma_{X}$

$$
Conf(\mathcal{P}\left( \overline{X_{n}} -\displaystyle{\frac{z_{c}\cdot \overline{\sigma_{n}}}{\sqrt{ n }}}< \mu_{X}<  \overline{X_{n}}+\displaystyle{\frac{z_{c}\cdot \overline{\sigma_{n}}}{\sqrt{ n }}}\right)=c
$$
#### Esempio
>Siamo in un frutteto, abbiamo $100$ albicocche di un frutteto

Misuriamo i *diametri*:
- ***Media*** = $5.1cm$
- ***Scarto Quadratico Medio*** $\sigma=1cm$

>[!question] Stimiamo con ***confidenza*** $95$% il diametro medio delle albicocche del frutteto

$X=$ diametro
$X_{1},\dots,X_{n}=$ diametri dei campioni

$\overline{X}_{100}= \displaystyle{\frac{X_{1}+\dots+X_{100}}{100}}=5.1$
$\overline{\sigma}_{100}=1$

$$
\Phi(z_{0.95})= \displaystyle{\frac{0.95+1}{2}} = 0.975 \implies z_{0.95}=1.96
$$
>[!done] Con ***confidenza*** al $95$% il diametro medio $\mu_{X}$ è compreso:
>$$\left[ 5.1- \displaystyle{\frac{1.96\cdot 1}{\sqrt{ 100 }}},5.1+ \displaystyle{\frac{1.96\cdot 1}{\sqrt{ 100 }}}\right]$$

>[!question] Determinare con quale confidenza $\mu_{X}$ sta nell'intervallo $[5,5.2]$

>Idealmente:

Dovrebbe essere una *confidenza* $<95$% poiché le condizioni sono ***più restrittive***

In questo caso dobbiamo imporre:
$$
\displaystyle{\frac{z_{c}\cdot \overline{\sigma}_{n}}{\sqrt{ n }}}=0.1
$$
Quindi:
- $z_{c}=\displaystyle{\frac{0.1 \cdot 10}{1}}=1$
>[!question] Chi è $c$ ?

$\mathcal{P}(-z_{c}<\zeta_{0}<z_{c})=c$
- $\mathcal{P}(-1<\zeta_{0}<1)=c$
- $2\Phi(1)=(2\cdot 0.8413)-1 = 0.683$

#### Caso Speciale Importante
>[!abstract] $X$ è una [[3 - Variabili Aleatorie#Variabili e Densità di Bernoulli|Variabile di Bernoulli]]
>$$\overline{\sigma}_{X}^2 =\overline{X}_{n}-\overline{X}_{n}^2$$

##### Esempio
>Abbiamo una moneta forse truccata

***Popolazione***: Tutti i lanci della moneta

- $\mu_{X}=\mathcal{P}($ La moneta dia *testa* $)$

>Lanciamo $80$ volte la moneta e otteniamo $43$ testa 

>[!question] Stimiamo con confidenza $90$% la probabilità che la moneta dia testa

$n=80$
$\overline{X}_{80}=\displaystyle\frac{43}{80}$
$\displaystyle\overline{\sigma}_{80}^2=\frac{43}{80}-\left( \frac{43}{80} \right)^2$

$z_{0.9}=1.65$

>[!done] Sostituiamo e otteniamo:
>$$[0.482,0.593]$$

