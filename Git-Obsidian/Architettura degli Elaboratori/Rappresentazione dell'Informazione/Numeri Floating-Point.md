## Introduzione
---
> Molti problemi di calcolo richiedono una gamma di valori **molto vasta** difficilmente esprimibile con le convenzionali tecniche di numerazioni

- La massa del sole $2\times 10^{33}gr.$ richiede un numero a $34$ cifre decimali o $111$ cifre binarie
- La massa dell'elettrone $9\times 10^{-28}gr.$ richiede un numero con $28$ cifre decimali oppure $90$ cifre binarie

Manipolare questi valori per *esteso* è molto scomodo e spesso infattibile e inutile
- Es la massa del sole non è certa dopo le prime 5 cifre significative

## Floating-Point
---
>[!info] Virgola Mobile
>Si adotta quindi una notazioni in cui la **gamma** dei valori esprimibili è indipendente dal numero di **cifre significative**
>Questo sistema è detto ***floating-point***

$$
n=f\times 10^e
$$
- $f\to$ **frazione o mantissa**
- $e \to$ **esponente**

La precisione è determinata dalla mantissa $f$ mentre la gamma di valori è determinata dall'esponente $e$

>[!warning] La notazione floating point consente più rappresentazioni per uno stesso numero

$$
3.14 = 0.314 \times 10^1 = 3.14 \times 10^0
$$
Per questo motivo è stata definita una **codifica *standard*** o *normalizzata* in cui i valori della **mantissa** $f$ sono compresi tra $0.1$ e $1$, ($0.1\leq f < 1$)


I **floating-point** possono essere utilizzati per "simulare" i numeri reali
- I numero di valori rappresentabili sono comunque infinitamente inferiore al numero di numeri reali
![[attachements/floatingpoints.png]]

>[!warning] Non tutti i numeri reali appartenenti alle aree rappresentabili possono essere espressi correttamente tramite un numero **floating-point**

A differenza dei numeri **reali**, la densità dei *floating-point* non è infinita
- Quando il risultato non si può esprimere nella rappresentazione numerica usata, viene utilizzato il numero più vicino rappresentabile
- L'errore che si commette è detto **errore di arrotondamento**

$$
E=min(\left| v-v_{1} \right|;\left| v-v_{2} \right|  )
$$
#### Esempio
Con numeri floating point con tre cifre decimali con segno per la mantissa e due cifre decimali con segno per l'esponente non è possibile rappresentare:
$$
\frac{10}{3}= 3.\overline{3}
$$
- In questo caso l'errore di arrotondamento è
$$
3.\overline{3} -0.333 \times10^1=0.000\overline{3}
$$

## IEEE 754: Standard Floating-Point
---
>[!info] Standard
>Adottato da praticamente tutti i [[Il Calcolatore e i Numeri Binari|calcolatori]] moderni
>Lo standard prevede vari formati
>I più utilizzati sono:
>- Formato a **singola precisione**
>- Formato a **doppia precisione**


| Elemento                        | Singola Precisione               | Doppia Precisione                  |
| ------------------------------- | -------------------------------- | ---------------------------------- |
| `BIT` di segno                  | $1$                              | $1$                                |
| `BIT` per l'esponente           | $8$                              | $11$                               |
| `BIT` nella parte frazionaria   | $23$                             | $52$                               |
| Numero totale di `BIT`          | $32$                             | $64$                               |
| Rappresentazione dell'esponente | Eccesso $127$                    | Eccesso $1023$                     |
| Campo dell'esponente            | Da $-126$ a $127$                | Da $-1022$ a $1023$                |
| Numero più vicino allo $0$      | $2^{-126} \approx 10^{-38}$      | $2^{-1022}\approx 10^{-308}$       |
| Numero più grande               | $\approx 2^{128}\approx 10^{38}$ | $\approx 2^{1024}\approx 10^{308}$ |

> Lo standard prevede di rappresentare i numeri in forma normalizzata e non normalizzata

### Forma Normalizzata
>[!tip] Standard
>La mantissa binaria normalizzata deve presentare un $1$ a ***sinistra della virgola binaria*** 
>L'esponente deve essere aggiustato di conseguenza

- Essendo sempre presente, tale **cifra non è informativa**, come la virgola binaria
	- Vengono considerate ***implicitamente presenti e non vengono memorizzate***

 Per evitare confusione con una frazione tradizionale, la combinazione dell'*implicito* della virgola e delle $23$/$52$ cifre significative vengono chiamate ***significand***
 - Mentre le cifre binarie dopo la virgola, *le uniche memorizzate* sono chiamate ***fraction***

>[!Esercizio] Trasformazione del numero $4568.1875_{10}$ in formato *IEEE 704* in singola precisione

Effettuo il cambiamento di base
- $4568.1875_{10} = 1000111011000.0011_{2}$
Normalizzo la mantissa
- $\underbrace{ 1.\overbrace{0001110110000011}^{\text{Fraction}} }_{ \text{Significant} } \times 2^{12}$
Esprimo l'esponente in eccesso $127$
- $12+127 = 139 \implies 10001011$

Ottenendo cosi la seguente codifica binaria:
![[attachements/BinaryFloatingPoint.png]]
#### Rappresentazione dello zero
Per rappresentare lo zero, lo standard riserva la combinazione di `BIT`, quelli dell'*esponente* e quelli del *significant*, a zero
![[attachements/plus0.png]]

- Ovviamente sarà inevitabile la doppia rappresentazione dello zero
	- Uno negativo e uno positivo
#### $-\infty +\infty$
Per rappresentare $\pm\infty$, lo standard riserva la combinazione di `BIT`, quelli dell'*esponente* tutti a `1` e quelli del *significant* tutti a `0

![[attachements/infinityFP.png]]`

#### Forma Denormalizzata
>[!tip] Valori Ancora più Piccoli
>La **forma denormalizzata** consente di rappresentare valori inferiori a $2^{-126}$

Consente di rappresentare valori fino a $2^{-149}$
Composta nel seguente modo:
- Tutti i `BIT` dell'*esponente* sono posti a `0`
- Il `BIT` del *signigicand* a sinistra della virgola binaria è implicitamente posto a `0`
>[!warning] Questa rappresentazione comporta una progressiva perdita di cifre significative

Il numero più piccolo rappresentabile in questa configurazione è:
![[attachements/smallestFloatingPoint.png]]

#### NaN
Per rappresentare questi valori si utilizzano le configurazioni in cui tutti i `BIT` dell'*esponente* sono `1`
- A differenza di $\pm\infty$ il valore della parte frazionaria è diverso da `0`
Esistono più tipi di `NaN`
>[!info] SNaN

Il ***Signaling NaN*** genera un'eccezione non appena viene utilizzato come operando in qualsiasi operazione


>[!info] QNaN

Il ***Quiet NaN*** viene propagato nella maggior parte delle operazioni senza generare eccezioni

