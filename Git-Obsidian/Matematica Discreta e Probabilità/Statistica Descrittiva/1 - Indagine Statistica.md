## Definizioni di Base
---
### Popolazione
>[!Definizione]
>La ***popolazione*** è un insieme finito o infinito
>- Possono essere persone, oggetti, azioni, etc...

### Campione
>[!abstract] Definizione
>Un ***campione*** è un sottoinsieme della *popolazione*

### Carattere
>[!Definizione]
>Il ***carattere*** è una qualunque ***funzione*** che ha come dominio la *popolazione*
>Si divide in due categorie
>>[!info] Quantitativo
>> Un *carattere* è ***quantitativo*** se si esprime con numeri che rappresentano una *quantità*
>
>>[!caution] Qualitativo
>>Un *carattere* è ***qualitativo*** quando non è *quantitativo*
>
>Un *carattere* si dice ***Discreto*** se i valori che può assumere sono finiti o [[../0 - Introduzione#Insiemi Numerabili|numerabili]]

#### Esempio
>*Popolazione:* Lanci di una moneta (tutti i modi possibili di lanciare la moneta)

Caratteri possibili:
- Risultato$\implies$ ***Carattere qualitativo***
- Altezza massima del lancio$\implies$ ***Carattere quantitativo***
- Tempo di arresto$\implies$ ***Carattere quantitativo***

>*Popolazione:* Sequenze di 10 lanci di una moneta

Carattere:
- Numero di volte che è uscito testa$\implies$ ***Carattere quantitativo***


### Modalità
>[!info] Definizione
>I valori che può assumere un *carattere* si dicono ***modalità***
>
>>[!abstract] Frequenza
>>La ***frequenza*** di una *modalità* è il numero di volte in cui la modalità si presenta nel campione considerato

#### Esempio
>*Campione*: $50$ studenti

*Carattere*: Colore degli occhi $\implies$ ***Carattere qualitativo***
*Modalità*: Verde, Azzurro, Nero, Marrone, ...

Fra $50$ Studenti:
- $10$ hanno gli occhi verdi $\implies 10$  è la ***frequenza*** della *modalità* verde
- $45$ hanno gli occhi marroni $\implies 45$  è la ***frequenza*** della *modalità* marrone
- $5$ hanno gli occhi azzurri $\implies 5$  è la ***frequenza*** della *modalità* azzurro
- $0$ hanno gli occhi neri $\implies 0$  è la ***frequenza*** della *modalità* nero

| Modalità | Frequenza Assoluta | Frequenza Relativa  |
| -------- | ------------------ | ------------------- |
| Verde    | $10$               | $\frac{10}{50}=0.2$ |
| Marrone  | $45$               | $\frac{45}{50}=0,7$ |
| Azzurro  | $5$                | $\frac{5}{50}=0.1$  |

#### Classi
>[!Definizione]
>Se le *modalità* sono "*tante*" o "*infinite*", vengono raggruppate in ***classi***

##### Esempio
>*Campione*: $50$ studenti

*Carattere*: Voto di *maturità*

Classi: $60-70$, $71-80$, $81-90$, $91-95$, $96-100$

### Indici di Posizione
>[!abstract] Definizione
>Gli ***indici di posizione o cardinalità*** sono singoli valori che *sintetizzano* un aspetto della *distribuzione* del *carattere*

#### Moda
>[!Definizione]
>La ***moda*** è il *carattere* con *frequenza* più alta

#### Media
>[!abstract] Definizione
>Se abbiamo un *carattere quantitativo*, definiamo la ***media campionaria***:
>$$\overline{x}=\frac{1}{x}(x_{1}+\dots+x_{n})=\frac{1}{n}\cdot \sum_{i=1}^nx_{i}$$
>>[!done] Alternativa
>>Se abbiamo le *modalità* $m_{1},\dots, m_{n}$ con le corrispettive *frequenze* $f_{1},\dots,f_{n}$
>>$$\overline{x} =\displaystyle{\frac{f_{1}m_{1}+f_{2}m_{2}+\dots+f_{k}m_{k}}{f_{1}+f_{2}+\dots+f_{k}}}$$

##### Esempio
>I valori assunti sugli elementi del campione sono:

- $1,2,1,1,4,1,2,1,1,2,2$

$$
\overline{x}=\displaystyle{\frac{1+3+1+1+4+1+2+1+1+2+2}{11}}=\frac{19}{11}
$$
Oppure

| Modalità | Frequenza |
| -------- | --------- |
| 1        | 6         |
| 2        | 3         |
| 3        | 1         |
| 4        | 1         |

$$
\overline{x}=\displaystyle{\frac{6\cdot 1+3\cdot 2 +1\cdot3+1\cdot 4}{6+3+1+1}}=\frac{19}{11}
$$

##### Cambio di variabile di primo grado
>[!info] Proprietà
>Sia $y=ax+b$
>$$\overline{y}=a\overline{x}+b$$
>>[!warning] Attenzione
>>La proprietà funziona unicamente con ***funzioni di primo grado***

###### Dimostrazione
>Sfruttando le [[../Utility#Proprietà delle Sommatorie|proprietà delle sommatorie]]
$$
\overline{y}=\frac{1}{n}\sum_{i=1}^ny=\frac{1}{n}\sum_{i=1}^n(ax_{i}+b)=\frac{1}{n}\left( \sum_{i=1}^nax_{i}+\sum_{i=1}^nb \right)=a\underbrace{ \frac{1}{n}\sum_{i=1}^nx_{i} }_{ \overline{x} }+\frac{1}{\cancel{ n }}b\cancel{ n }=
$$

>[!done] Conclusione
>$$\overline{y}=a\overline{x}+b$$


###### Esempio
>Siano $50,55,53,44,43,48,50$ le temperature registrate in $^{\circ}F$ in una città

>[!question] Qual è la temperatura media in $^\circ C$?

- $x=$ temperatura in $^\circ F$
- $y=$ temperatura in $^\circ C$

$$
y=(x-32) \frac{100}{180}\implies y=\frac{5}{9}x- \frac{160}{9}
$$

$$
\overline{x}=\displaystyle{\frac{50+55+53+44+43+48+50}{7}}=49
$$
>Ora applichiamo la proprietà

- $\overline{y}=\frac{5}{9}\overline{x}- \frac{160}{9}\implies\overline{y}=\frac{5}{9}\cdot49- \frac{160}{9}=9.44 ^\circ C$

###### Esempio
>$180,190,150,210,160,140,140,210,220$

>[!question] Qual è la media di questi numeri?

Poniamo:
- $y=\displaystyle{\frac{x-200}{10}}$

$y$ assume i valori: $-2,-1,-5,1,5,-4,-6,-6,1,2$

- $\overline{y}= \displaystyle{\frac{-2-1-5+1+5-4-6-6+1+2}{10}}=-1.5$

$$
-1.5 = \displaystyle{\frac{\overline{x}-200}{10}}\implies\overline{x}=10\overline{y}+200\implies\overline{x}=-15+200=185
$$

#### Mediana
>[!info] Definizione
>La ***mediana*** di $x$ è un valore che ***divide il campione in 2 parti uguali***
>>[!example] $n=2k+1$
>>Se il campione ha un numero dispari di valori, e i valori sono ordinati in modo crescente
>>$x_{1} \leq x_{2} \leq x_{3} \leq\dots \leq x_{n}$, la *mediana* è $x_{k+1}$
>
>>[!example] $n=2k$
>>Se il campione ha un numero pari di valori, e i valori sono ordinati in modo crescente
>>la *mediana* è $\displaystyle{\frac{x_{k}+x_{k+1}}{2}}$

##### Esempio
> Valori di $x$: $2,1,4,1,0,2,10,-1,257$

*Mediana*:
- $-1,0,1,1,\underbrace{ 2 }_{ mediana },2,4,10,257$
