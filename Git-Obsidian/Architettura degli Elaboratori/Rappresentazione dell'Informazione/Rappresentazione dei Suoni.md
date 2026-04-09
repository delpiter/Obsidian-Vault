> Fisicamente un suono è rappresentato come un'onda che descrive la variazione della pressione dell'aria nel tempo.
> Si tratta di un segnale **analogico**

## Codifica Digitale del Suono
---
>[!info] Campionamento e Quantizzazione
>Per "*trasformare*" un segnale audio da analogico a digitale sono necessari due passaggi
>1. ***Campionamento*** del suono
>2. ***Quantizzazione***

Campionamento ad elevata frequenza e la quantizzazione con un numero elevato di `BIT` per campione garantiscono una ***rappresentazione accurata***


```functionplot
---
title: Sampling and Quantization
xLabel: Time
yLabel: Amplitude
bounds: [-5,5,-5,5]
disableZoom: false
grid: true
---
f(x)=4sin(x)
g(x) = floor(4sin(x))
```


![[attachements/SamplingQuantification.png]]
### Campionamento
>[!tip] Definizione
>Il ***campionamento*** (*sampling*) è il processo che consente una riduzione di un ***segnale continuo*** nel tempo per ottenere un ***segnale discreto*** 

- Il concetto è quello di "*campionare*" un valore del segnale analogico ad un intervallo regolare
	- Il campione è un valore di un segnale in un ***punto del tempo e spazio***

Per digitalizzare un segnale il più simile a quello originale si cerca di campionare il suono a $44,1\ KHz$ ($44.100$ campioni al secondo)
- Circa il doppio dei $22\ KHz$ che rappresentano la banda udibile dall'uomo
### Quantizzazione
>[!tip] Definizione
>La ***quantizzazione*** in matematica e nel *digital sound processing* è il processo di *costrizione di un input* da un insieme di valori **continuo** o molto grande (come i [[../../Analisi/Insiemi/Insiemi Numerici#Numeri Reali|numeri reali]]) a un insieme **discreto** di valori.

Per digitalizzare un segnale il più fedele possibile a quello originale ci vuole un minimo di:
- `16 BIT` per canale (Stereo $=$ 2 Canali)
	- Ogni secondo di audio stereo $\to 44100 \times\left( \frac{16}{8} \right) \times2 \approx 172 KB/sec$
