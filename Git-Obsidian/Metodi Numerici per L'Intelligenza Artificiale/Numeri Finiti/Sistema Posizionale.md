## Numeri in un Sistema Posizionale
---
>Sistema numerico in cui il valore di una cifra *dipende dalla sua posizione*

>[!hint] Numeri reali in base $\beta$
>Un ***numero reale*** in *base* $\beta$ può essere rappresentato come:
>$$\pm(a_{n}a_{n-1}\dots a_{0}.b_{1}b_{2}\dots)_{\beta}=\pm\left(  \sum_{k=0}^n a_{k}\beta^k +\sum_{k=1}^\infty b_{k}\beta^-k \right)$$
>
>Dove:
>$a_{n}a_{n-1}\dots a_{0}$ sono le cifre della **parte intera**
>$b_{1}b_{2}\dots$ sono le cifre della **parte frazionaria**
>$\beta$ è la ***base del sistema numerico***

## Virgola Mobile e Virgola Fissa
---
>[!info] Concetti
>I sistemi di numerazione posizionale a ***virgola fissa*** e a ***virgola mobile*** sono due modalità di rappresentare i numeri reali utilizzando un *sistema numerico posizionale*, che **differiscono** nel modo in cui la ***virgola è trattata***.

### Sistema a Virgola fissa
>[!summary] Concetto
>Nel sistema a ***virgola fissa***, la *posizione* della virgola è **predefinita**, cioè la *parte frazionaria* del numero ha una **lunghezza costante** di `BIT`

>[!done] Velocità di Calcolo

Le operazioni sono ***generalmente più rapide***
- Non è necessario spostare la virgola durante le operazioni

>[!fail] Intervallo Limitato

La gamma di numeri che può essere rappresentata è ***limitata dalla posizione della virgola***

### Sistema a Virgola Mobile
>[[../../Architettura degli Elaboratori/Rappresentazione dell'Informazione/Numeri Floating-Point]]

>[!summary] Concetto
>Nei sistemi a ***virgola mobile*** (***floating point***) il numero di cifre dedicate alla parte intera e frazionaria *non è fisso*, ma dipende dall’**esponente**.
>- Permette di rappresentare numeri molto grandi o molto piccoli con la **stessa quantità di memoria**. 

Il numero è rappresentato come un prodotto di:
- Un ***numero significativo*** (**mantissa**)
- Un ***esponente*** che determina la *posizione della virgola*.