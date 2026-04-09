## Fenomeni Aleatori
---
>[!Definizione]
>Un ***fenomeno aleatorio*** è un *qualcosa* che accade che porta ad un ***risultato*** (che ***non*** possiamo *prevedere* con certezza), appartenente ad un insieme ($\Omega$)

>[!abstract] Risultato
>Il risultato è un elemento dell'insieme $\Omega$
#### Esempio
###### 1)

>Fenomeno: *Lancio di un dado*

- $\Omega:\{ 1,2,3,4,5,6 \}$

###### 2)

>Fenomeno: *Partita di Calcio*

***Risultato*** (o esito): risultato della partita
- $\Omega:\mathbb{N}^2$

###### 3)

>Fenomeno: *Crescita di un bambino in un anno*

***Risultato***: Altezza
- $\Omega:[0,300]$

### Evento
>[!abstract] Definizione
>Un ***evento*** è un sottoinsieme di $\Omega$ di cui vorremo calcolare la *probabilità*

#### Esempio
[[#1|#1)]])
Esce $5$ o $6$
- $E=\{ 5,6 \}$

[[#2|#2)]])
"Pareggio"
- $E=\{ (n,n),n \in \mathbb{N} \}$

[[#3|#3)]])
Il bambino è alto almeno un metro
- $E=[100,300]$

### Valutazione di Probabilità
>[!info] Definizione
>Una ***valutazione di probabilità*** è una funzione che associa ad un evento $E$ un numero:
>$$\mathcal{P}(E): 0\leq\mathcal{P}(E)\leq 1$$
>>[!done] Quantifica la probabilità che l'evento accada

## Spazio di Probabilità
---
>[!abstract] Definizione
>Uno ***spazio di probabilità*** è una terna:
>$$(\Omega,\mathcal{A},\mathcal{P})$$
>Dove:
>1. $\Omega$ è un *insieme*
>2. $\mathcal{A}$ è un insieme di sottoinsiemi di $\Omega$ detti ***eventi***, tali che:
>	- $\varnothing,\Omega \in\mathcal{A}$
>	- $\mathcal{A}$ è chiuso rispetto a *complementare*, *unione* e *intersezione*, Comprende anche ***insiemi numerabili***
>3. $\mathcal{P}:\mathcal{A}\to[0,1]$ *tale che*
>	- $\mathcal{P}(\Omega)=1$
>	- Se $E_{1},E_{2},\dots$ sono ***eventi disgiunti***, allora la probabilità della loro unione sarà: $\mathcal{P}(E_{1}\cup E_{2}\cup\dots)=\mathcal{P}(E_{1})+\mathcal{P}(E_{2})+\dots$

#### Esempio
>$\Omega=\mathbb{Z}$

- $\mathcal{A}_{1}=\{ \varnothing,\mathbb{Z} \}$
- $\mathcal{A}_{2}=\{ \varnothing,\mathbb{Z},2\mathbb{Z},2\mathbb{Z}+1 \}$
- $\mathcal{A}_{3}=\{ \varnothing,\mathbb{Z},\mathbb{Z}_{\geq 0},\mathbb{Z}_{\leq 0},\mathbb{Z}_{\geq 1},\mathbb{Z}_{\leq 1},\{ 0 \},\mathbb{Z}_{\neq 0} \}$


#### Esempio
>Supponiamo di avere 3 urne
>- Urna $1$: Palline con $1$ o $2$ (***quantità incognita***)
>- Urna $2$: Palline con $1$ o $2$ 
>- Urna $3$: Palline con $3$ o $4$ 


*Fenomeno*: Estrazione di una pallina a caso

$\Omega=\{ 1,2,3,4 \}$
- $\mathcal{A}=\{ \varnothing,\Omega, \{ 1,2 \},\{ 3,4 \} \}$

$\mathcal{P}(\varnothing)=0 \quad \mathcal{P}(\Omega)=1$
$\mathcal{P}(\{ 1,2 \})=\frac{2}{3}\quad \mathcal{P}(\{ 3,4 \})=\frac{1}{3}$

## Spazi di Probabilità Uniformi
---
>[!quote] Definizione
>Gli ***spazi di probabilità uniformi*** sono *spazi di probabilità* in cui:
>- $\Omega$ è finito ($|\Omega|=n$)
>- Tutti i *risultati* sono ***eventi*** e hanno la ***stessa probabilità***
>- Se $\Omega=\{ a_{1},a_{2},\dots,a_{n} \}$, $\Omega=\{ a_{1} \}\cup \{ a_{2} \}\cup\dots\cup\{ a_{n} \}$
>>[!done] Conclusione
>>$$1=\mathcal{P}(\Omega)=\mathcal{P}(a_{1})+\mathcal{P}(a_{2})+\dots+\mathcal{P}(a_{n})=n\mathcal{P}(a_{1})\implies \mathcal{P}(a_{1})=\frac{1}{n}$$

Se $E\subseteq \Omega$ è un ***evento qualunque***:
$$\mathcal{P}(E)=\displaystyle{\frac{|E|}{|\Omega|}}$$
>[!caution] A parole
>$|E|\to$ Numero di casi ***Favorevoli***
>$|\Omega|\to$ Numero di casi ***Possibili***

#### Esempio
>***Lotto***: Estrazione di $5$ numeri diversi da $1$ a $90$

>[!question] Qual è la probabilità di fare terno al lotto?

I risultati sono disposizioni di lunghezza $5$ in $\{ 1,\dots,90 \}$

- Conviene considerare i numeri ***non ordinati***

$\Omega=\{$ Sottoinsiemi di $\{ 1,\dots,90 \}$ di $5$ *elementi* $\}$

$|\Omega|=\displaystyle\binom{90}{5}$

>[!question] Quanti sono i risultati favorevoli??

$\displaystyle\binom{87}{2}$
- $5$ numeri tra $1$ e $90$ che contengono $1,2,3$
>[!done] Dobbiamo scegliere 2 numeri tra $4$ e $90$
>$$\mathcal{P}(E)=\displaystyle{\frac{|E|}{|\Omega|}}=\displaystyle\frac{\binom{87}{2}}{\binom{90}{5}}=\displaystyle{\frac{\displaystyle{\frac{87\cdot 86}{2}}}{\displaystyle{\frac{90\cdot 89 \cdot 88\cdot 87\cdot 86}{5\cdot 4\cdot 3\cdot 2}}}}=\frac{1}{66 \cdot 2 \cdot 89}=\frac{1}{11748}$$


>[!question] Qual è la probabilità di indovinare un solo numero estratto?

$\mathcal{P}($*"Esce 1"*$)$=$\mathcal{P}($*"Esce 1 al primo estratto"*$)+\mathcal{P}(2^\circ$ *"estratto"*$=1)+\mathcal{P}($"$3^\circ=1$"$)+\mathcal{P}($"$4^\circ=1$"$)+\mathcal{P}($"$5^\circ=1$"$)$
- $\displaystyle\frac{1}{90}+\frac{1}{90}+\frac{1}{90}+\frac{1}{90}+\frac{1}{90}=\frac{5}{90}$

#### Osservazione
>[!quote] Osservazione
>Se $E$ è ***evento***, $E^c$ è anche ***evento***
>- $E\cup E^c=\Omega$


$$\begin{array}
\ \mathcal{P}(E)+\mathcal{P}(E^c)=\mathcal{P(\Omega)}=1 \\
\mathcal{P}(E)=1-\mathcal{P}(E^c)
\end{array}$$