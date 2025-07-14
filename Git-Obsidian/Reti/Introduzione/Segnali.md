>[!question] Come è fatta l'Informazione
## Segnale Analogico
---
>[!info] Segnale analogico
>Un segnale è ***Analogico*** quando i valori utili che lo rappresentano sono continui (*infiniti*) in un intervallo e non numerabili

Un segnale molto semplice è la sinusoide:
$$A\sin(2\pi ft + \Phi)$$
- $A$: Ampiezza del segnale
- $f$: Frequenza del segnale (*oscillazioni al secondo* - $Hz$)
- $\Phi$: Fase del segnale

<font color="CornflowerBlue">$$f(t)=3\sin(3t+3)$$ </font>
<font color="red">$$g(t) = 2\sin(2t+2)$$ </font>
<font color="green">$$z(t)= 5\sin(t+5)$$</font>

```functionplot
---
title: 
xLabel: 
yLabel: 
bounds: [-10,10,-8,8]
disableZoom: true
grid: true
---
f(x)=3*sin(3*x+3)
f(x)=2*sin(2*x+2)
f(x)=5*sin(x+5)
```
### Descrivere il Segnale
>La singola sinusoide ha un *andamento temporale noto*

Le tre grandezze fondamentali sono ***sufficienti per caratterizzarla***

>[!attention] Problema
>L'andamento di un segnale nel tempo potrebbe diventare ***troppo difficile*** da *descrivere*

Se ci focalizziamo su *ampiezza*, *fase* e *frequenza*, descrivere il segnale è molto più semplice.

La funzione: $1.2\sin(2\pi3t)+0.7\sin(2\pi4t +1.4)$
- ***Diventa***:
![[Spectrum.png]]

- Questo grafico è chiamato lo ***spettro del segnale***

>[!info] Larghezza di Banda
>Noto lo spettro, sono note anche la frequenza minima $f_{m}$ e la frequenza massima $f_{M}$ del segnale.
>La ***larghezza di banda*** o ***banda del segnale*** è:
>$$B=f_{m}-f_{M}$$

In termini generali la larghezza di banda da indicazioni sul grado di ***complessità del segnale***

#### Trasmissione dei Segnali
>Scelto un certo **mezzo trasmissivo** ed una certa **tecnologia** per utilizzarlo, otteniamo la ***banda passante del canale***

Nella ***telefonia analogica*** *tradizionale* il segnale sonoro prodotto dall’utente viene *filtrato* e *limitato* nella «**banda fonica**» che va da $300$ a $3400 Hz$

## Segnali Digitali
---
>[!caution] Segnale Digtale
>Un segnale è ***digitale*** quando i valori utili che lo rappresentano sono **discreti** e **finiti**
>I calcolatori moderni utilizzano *due stati logici* (binari)

#### Conversione Analogico-Digitale
>La conversione analogico-digitale è caratterizzata da due fasi distinte:

![[Rappresentazione dei Suoni#Campionamento]]

>[!note] Teorema Shannon-Nyquist
>Il ***teorema Shannon-Nyquist*** permette di determinare il *minimo intervallo di campionamento* che permette di **ricostruire** il segnale analogico in modo integrale

$$
\begin{array}
\ f_{s} \geq 2 f_{M} \\
T_{s}=\displaystyle\frac{1}{f_{s}} < \frac{1}{2f_{M}}
\end{array}
$$

![[Rappresentazione dei Suoni#Quantizzazione]]
