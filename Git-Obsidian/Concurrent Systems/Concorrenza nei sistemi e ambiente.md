## Tassonomia
---
> Esistono due tipologie di sistemi concorrenti che interagiscono con l'ambiente:


> [!failure] Reactive Systems
> Un ***reactive system*** è un sistema che esegue reagendo agli stimoli dall'ambiente.

Le interazioni sono *asincrone* e la non terminazione del programma potrebbe essere una feature voluta.

> [!abstract] Transformational Systems
> Un ***transformational system*** è un sistema puramente funzionale e sincrono.

Formalizzabile come una *macchina di Turing*.

### L'hyper-cubo della programmazione concorrente
> La tassonomia della *programmazione concorrente* può essere modellata attraverso uno spazio multidimensionale dove vengono allocati i vari approcci.

#addLink

> [!caution] Control Flow Model
> Sincrono vs Asincrono

> [!help] Shared Memory e Message Passing
> - Asynchronous Message Passing: Actor Programming
> - Synchronous/Channel based message passing


> [!info] Distribuito e Non Distribuito
> 


> [!tl;dr] Control oriented e data oriented
> Reactive Programming (*Data oriented*)

> Esempio di reactive programming

$$
\begin{aligned}
x \leftarrow 1 \\
y\leftarrow x + 1 \\
x \leftarrow 2
\end{aligned}
$$
- In un sistema *control oriented* il valore di $y$ alla fine dell'esecuzione sarà $2$.
- Nel *reactive programming* $y$ avrà il valore $3$.
