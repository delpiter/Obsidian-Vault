>Siano $A_{1},A_{2},\dots,A_{n}$ degli eventi

>[!question] Qual è la probabilità: $\mathcal{P}(A_{1}\cup A_{2}\cup\dots\cup A_{n})$?

## Complementare
---
>[!attention] Ricordando che
>$(A_{1}\cup A_{2}\cup\dots\cup A_{n})^c=A_{1}^c\cap A_{2}^c\cap\dots\cap A_{n}^c$

$$
\mathcal{P}(A_{1}\cup A_{2}\cup\dots\cup A_{n})=1-\mathcal{P}(A_{1}^c\cap A_{2}^c\cap\dots\cap A_{n}^c)
$$

#### Esempio
>[!question] Qual è la probabilità di ottenere un sei lanciando due dadi?

- $E_{1}=$"Il primo dado da $6$" $\implies(6,1),(6,2),(6,3),\dots$
- $E_{2}=$"Il secondo dado da $6$" $\implies(1,6),(2,6),(3,6),\dots$

$$
\mathcal{P}(E_{1}\cup E_{2})=1-\mathcal{P}(E_{1}^c\cap E_{2}^c)=1-\frac{25}{36}=\frac{11}{36}
$$
Dove:
- $E_{1}^c$ e $E_{2}^c$ sono gli *eventi* in cui non esce 6 ne nel primo dado ne nel secondo dado
	- Posso scegliere il primo numero in $5$ modi e il secondo dado il $5$ modi:
	- I casi possibili sono $6\cdot6$


## Principio di Inclusione Esclusione
---
> In alternativa è possibile utilizzare il principio di inclusione-esclusione


>[[../Combinatoria/2 - Principio di inclusione-esclusione|!note]]
>$$\mathcal{P}(E_{1}\cup E_{2})=\mathcal{P}(E_{1})+\mathcal{P}(E_{2})-\mathcal{P}(E_{1}\cap E_{2})$$


- $\displaystyle= \frac{1}{6}+\frac{1}{6}-\frac{1}{36}=\frac{11}{36}$

## Probabilità Condizionata
---
>[!info] Definizione
>Fissato $A$, un *evento che accade*
>>[!question] Qual è la probabilità che accada anche $B$?
>
>$$\frac{\mathcal{P}(B\cap A)}{\mathcal{P}(A)}=\mathcal{P}(B|A)$$
>>[!done] A parole
>>Probabilità di $B$ *condizionato da / dato* $A$

#### Esempio
>Estraiamo 2 palline senza rimpiazzo fra 3 rosse e 4 blu

- $B_{1}=$"Primo estratto blu"
- $B_{2}=$"Secondo estratto blu"
- $R_{1}=$"Primo estratto rosso"
- $R_{2}=$"Secondo estratto rosso"

$$
\mathcal{P}(B_{2})=\frac{4}{7}
$$
$$
\mathcal{P}(B_{2}|R_{1})=\frac{4}{6}
$$

#### Esempio
>2 Urne, Urna 1 $\implies$ $3$ palline rosse e $4$ blu, Urna 2 $\implies$ $2$ palline rosse e $5$ blu

Estraiamo una pallina a caso

>[!question] Qual è la probabilità che questa sia rossa?

$$
\begin{array}
\ \mathcal{P}(R)=\mathcal{P}(R\cap U_{1})+\mathcal{P}(R\cap U_{2})
 \\=\mathcal{P}(R|U_{1})\cdot\mathcal{P}(U_{1})+\mathcal{P}(R|U_{2})\cdot\mathcal{P}(U_{2}) \\
=\displaystyle\frac{3}{7}\cdot \frac{1}{2}+\frac{2}{8}\cdot \frac{1}{2}= \frac{19}{56}
\end{array}
$$


## Formula delle Probabilità-Totali
---
>Siano $\{ A_{1},A_{2},\dots \}$ delle [[../Combinatoria/3 - Partizioni|partizioni]] di $\Omega$ e sia $B\subseteq \Omega$

>[!note] Formula
>$$\mathcal{P}(B\cap A_{1})+\mathcal{P}(B\cap A_{2})+\dots=$$
>$$=\mathcal{P}(B|A_{1})\cdot \mathcal{P}(A_{1})+\mathcal{P}(B|A_{2})\cdot \mathcal{P}(A_{2})+\dots$$

#### Esempio
>Sia una urna piena di $r$ palline ***rosse*** e $b$ palline ***blu***

>[!question] Qual è la probabilità che esca una pallina rossa alla seconda estrazione?

$\mathcal{P}(R_{2})=\mathcal{P}(R_{2}\cap R_{1})+\mathcal{P}(R_{2}\cap B_{1})$
- $=\mathcal{P}(R_{2}|R_{1})\cdot \mathcal{P}(R_{1})+\mathcal{P}(R_{2}|B_{1})\cdot \mathcal{P}(B_{1})=$
- $=\displaystyle{\frac{r-1}{b+r-1}}\cdot \displaystyle{\frac{r}{b+r}}+\displaystyle{\frac{r}{b+r-1}}\cdot \displaystyle{\frac{b}{b+r}}=\frac{r}{b+r}$


### Formula di Bayes
>[!quote] Concetto
>Permette di esprimere $\mathcal{P}(B|A)$ in funzione di $\mathcal{P}(A|B)$
>>[!note] Formula
>>$$\mathcal{P}(B|A)=\displaystyle{\frac{\mathcal{P}(A|B)\cdot\mathcal{P}(B)}{\mathcal{P}(A)}}$$

##### Dimostrazione
>$\mathcal{P}(A\cap B)=\mathcal{P}(B|A)\cdot\mathcal{P}(A)=\mathcal{P}(A|B)\cdot\mathcal{P}(B)$

#### Esercizio
>Popolazione: Popolazione della Turchia
>- $40$% sono fumatori
>- $25$% dei fumatori e il $4$% dei non fumatori soffrono di una malattia

>[!question] 1\) Qual è la probabilità che una persona a caso sia malata?

>[!question] 2\) Qual è la probabilità che una persona malata sia un fumatore

***Fenomeno***: Estrazione di una persona

$F=$ "Fumatori" $\quad N=$ "Non Fumatori"

- $\mathcal{P}(F)=0,4\quad\mathcal{P}(N)=0,6$
- $\mathcal{P}(M|F)=0,25\quad \mathcal{P}(M|N)=0,04$

1. 
$$\mathcal{P}(M)=\mathcal{P}(M|F)\cdot\mathcal{P}(F)+\mathcal{P}(M|N)\cdot\mathcal{P}(N)=$$
$$
=0,25\cdot0,4+0,04\cdot 0,6=0,124
$$

2. 
$$
\mathcal{P}(F|M)=\displaystyle{\frac{\mathcal{P}(M|F)\cdot \mathcal{P}(F)}{\mathcal{P}(M)}}=\displaystyle{\frac{0,25 \cdot 0,4}{0,142}}=0,806
$$


### Eventi Indipendenti
>[!info] Definizione
>$A,B$ eventi si dicono ***indipendenti*** se, il fatto che accada uno, ***non cambia*** la probabilità che accada l'altro
>- $\mathcal{P}(A|B)=\mathcal{P}(A)$
>- $\mathcal{P}(B|A)=\mathcal{B}(A)$
>
>>[!note] Conclusione
>>$$\displaystyle{\frac{\mathcal{P}(A\cap B)}{\mathcal{P}(B)}}\implies\mathcal{P}(A\cap B)=\mathcal{P}(A)\cdot\mathcal{P}(B)$$

#### Esempio
>Urna con 3 palline rosse e 2 blu

***Fenomeno***: Estrazione di due palline con rimpiazzo

- $B_{1}$ e $R_{2}$ sono *eventi indipendenti*

$$
\mathcal{P}(B_{1}\cap R_{2})= \mathcal{P}(B_{1})\cdot \mathcal{P}(R_{2})
$$