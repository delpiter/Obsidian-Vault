## Problema Matematico
---
>[!definizione] Definizione
>Un ***problema matematico***, che indichiamo con $f$ è una *descrizione precisa* e **senza ambiguità** di un legame tra i dati del problema $x$ (*input*) e i risultati corrispondenti $y$ (*output*)
>>[!done] In altre parole
>>È una *funzione* che trasforma i **dati** in **risultati**.

Un problema si dice ***ben posto*** se la sua soluzione soddisfa tre condizioni:
1. ***Esiste***
2. ***È unica***
3. ***Dipende*** in modo continuo dai dati del problema

>[!hint] Osservazione
>Se un problema ammette ***una ed una sola soluzione***, la funzione *dato-risultato* è [[../../Analisi/Funzioni/Introduzione Funzioni#Funzione Biunivoca|biettiva]]

### Condizionamento di un Problema
>[!info]
>Quando un problema è ***ben posto*** si cerca di dare una misura quantitativa di come la *soluzione* venga **influenzata** da una **perturbazione** dei dati (se ne misura il ***condizionamento***).

Il condizionamento di un problema permette di misurare quanto la *soluzione cambia* in risposta a un *cambiamento nei dati*.

>[!help] Affidabilità dei Risultati
>Se un problema è ***mal condizionato***, i suoi risultati possono essere **inaffidabili** e **sensibili** a piccoli errori nei dati.

>[!tldr] Interpretazione dei Risultati
>Se un problema è ***mal condizionato***, può essere *difficile interpretare i risultati* e capire come dipendono dai dati.

> Supponiamo che i dati siano affetti da una **perturbazione**.
- Indichiamo con $\tilde{x}=x+\delta_{x}$ i dati affetti da una *perturbazione* $\delta_{x}$
>[!question] Come vengono propagati dal problema $f$ gli errori presenti nei dati?

> ***Ipotesi ideale***: non ci sono errori di calcolo.

Il "***condizionamento***" di un problema misura quanto i risultati $f(x)$ sono sensibili alle piccole perturbazioni nei dati $x$.

>[!done] Problema Ben Condizionato
>Se *piccole variazioni nei dati* $x$ portano a variazioni *relativamente piccole* nei risultati $f(x)$, il problema è ***Ben Condizionato***
>>[!note] Gli errori nei dati non vengono amplificati in modo significativo

>[!error] Problema Mal Condizionato
>Se *piccole variazioni nei dati* $x$ portano a variazioni *molto grandi* nei risultati $f(x)$, il problema è ***Mal Condizionato***
>>[!note] Gli errori nei dati possono essere enormemente aplificati.

Uno stesso problema può essere *mal condizionato* per certi dati ma **non** per altri.

#### Quantificare il Condizionamento
>[!cite] Indice di Condizionamento
>Sia $\displaystyle{\frac{\mid\mid f(x)-f(\tilde{x})\mid\mid}{\mid\mid f(x)\mid\mid}}$ la misura dell'[[../Numeri Finiti/Errore di Rappresentazione|errore relativo]] sui *risultati* e $\displaystyle{\frac{\mid\mid x -\tilde{x}\mid\mid}{\mid\mid x \mid\mid}}$ la misura dell'errore relativo sui *dati*.
>
>L'***indice di condizionamento*** $K$ mette in relazione i due errori:
>$$\displaystyle{\frac{\mid\mid f(x)-f(\tilde{x})\mid\mid}{\mid\mid f(x)\mid\mid}}\leq K\cdot\displaystyle{\frac{\mid\mid x -\tilde{x}\mid\mid}{\mid\mid x \mid\mid}}$$

$K$ quantifica l'entità con cui l'errore relativo sui dati si ***amplifica*** sull'errore relativo sui ***risultati del problema***.
- Se $K$ è "*grande*" il problema è *mal condizionato*

>[!nota]
>Il condizionamento è ***legato al problema numerico*** e **non** ha alcun legame con gli errori di arrotondamento delle operazioni macchina, ne con il particolare algoritmo utilizzato.

##### Esempio
>[!quote] Testo
> Consideriamo lo studio del condizionamento della valutazione di una funzione $f:\mathbb{R}\to\mathbb{R}$ (differenziabile) in un punto $x$.

Supponiamo di voler calcolare il valore di una funzione $f(x)$, ma il dato $x$ a nostra disposizione è effetto da un errore.

>[!warning] È importante stimare l'errore sulla funzione $f(x)$ in base all'errore sul dato.

>Indichiamo con $\tilde{x}=x+\delta_{x}$ il dato affetto da una perturbazione $\delta_{x}$, **piccola**.

Consideriamo uno sviluppo in serie del primo ordine di $f(x)$ in un intorno di $x$:
$$
f(x+\delta_{x})=f(x)+\delta_{x}f'(x)+\circ(\delta_{x})
$$

Essendo la perturbazione $\delta_{x}$ piccola:
$$
f(\tilde{x})-f(x)\approx (\tilde{x}-x)\cdot f'(x)
$$
$$
\displaystyle{\frac{f(\tilde{x})-f(x)}{f(x)}}\approx \displaystyle{\frac{(\tilde{x}-x)f'(x)}{f(x)}}
$$
$$
\left| \displaystyle{\frac{f(\tilde{x})-f(x)}{f(x)}} \right|\approx \left| \displaystyle{\frac{f'(x)x}{f(x)}} \right|\left| \displaystyle{\frac{\tilde{x}-x}{x}} \right|   
$$

- Poniamo $K=\left| \displaystyle{\frac{f'(x)x}{f(x)}} \right|$

$K$ è detto ***indice di condizionamento del problema*** della valutazione di una funzione $f:\mathbb{R}\to\mathbb{R}$ differenziabile in un punto $x$

##### Riformulare un Problema Mal Condizionato
>[!Help] Soluzione
>Nel caso in cui si abbia un ***problema mal condizionato***, si possono seguire le seguenti strade:
>1. Cambiare la *formulazione del problema*, per superare l'ostacolo.
>2. Usare la *precisione multipla* nei calcoli.
>3. Usare *tecniche di regolarizzazione* che sostituiscono al problema di partenza un problema leggermente modificato ma **ben condizionato**.