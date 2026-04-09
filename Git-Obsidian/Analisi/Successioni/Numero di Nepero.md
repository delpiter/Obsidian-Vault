## Dimostrazione
### $f_{n}$ crescente
Sia
$$
\large (f_{n})_{n\in \mathbb{N}} = \left( 1+ \frac{1}{n} \right)^{n}
$$
Dimostriamo che $f_{n} \nearrow$
$$
\large  \frac{f_{n+1}}{f_{n}}\geq 1 \qquad \forall n \in \mathbb{N} \setminus \{ 0 \}
$$
#### Procedimento
$$
\begin{align}
& \frac{f_{n+1}}{f_{n}} = \frac{\left( 1+\frac{1}{n+1} \right)^{n+1}}{\left( 1+\frac{1}{n} \right)^{n}}= \frac{\left( \frac{n+2}{n+1} \right)^{n+1}}{\left( \frac{n+1}{n} \right)^{n}}= \left( \frac{n+2}{n+1} \right)^{n+1} \cdot \left( \frac{n}{n+1} \right)^{n} = 
\end{align}
$$
Trasformiamo l'esponente di $\left( \frac{n}{n+1} \right)^{n}$ per poter sfruttare la [[Funzioni di una variabile Reale#Funzione Esponenziale#Funzione Esponenziale#Funzione Esponenziale#Funzione Esponenziale#Proprietà|proprietà delle funzioni esponenziali]]
$$
\displaylines{
\begin{align}
& \left( \frac{n+2}{n+1} \right)^{n+1} \cdot \left( \frac{n}{n+1} \right)^{n+1}\cdot \frac{n+1}{n}= \\
& =\left( \frac{n^{2}+2n+1-1}{(n+1)^{2}} \right)^{n+1}\left( \frac{n+1}{n} \right) = \left( \frac{(n+1)^{2}-1}{(n+1)^{2}} \right)\left( \frac{n+1}{n} \right)
\end{align} \\ \\
= \left( 1-\frac{1}{(n+1)^{2}} \right)^{n+1}\left( \frac{n+1}{n} \right)
}
$$
Sfruttiamo poi la [[../Tipologie di Dimostrazioni#Disuguaglianza di Bernoulli|disugualianza di Bernoulli]] ponendo
- $x = \frac{1}{(n+1)^{2}}$
- $n = n+1$
$$
\left( 1-\frac{1}{(n+1)^{2}} \right)^{n+1}\left( \frac{n+1}{n} \right) \geq \left( 1-\frac{n+1}{(n+1)^{2}} \right)\left( \frac{n+1}{n} \right)
$$

Scomponiamo il secondo membro
$$
\begin{align}
& \left( 1-\frac{n+1}{(n+1)^{2}} \right)\left( \frac{n+1}{n} \right) = \\
&= \left( 1-\frac{1}{n+1} \right)\left( \frac{n+1}{n} \right) \\ \\
&\large = \left( \frac{n\cancel{ +1-1 }}{n+1} \right)\left( \frac{n+1}{n} \right) = 1
\end{align}
$$
### $h_{n}$ decrescente
Sia
$$
\large (h_{n})_{n\in \mathbb{N}} = \left( 1+ \frac{1}{n} \right)^{n+1}
$$
Possiamo dimostrare [[#$f_{n}$ crescente|analogamente]] che 
$$
\large h_{n} \searrow
$$
#### Osservazione
$$
\displaylines{
h_{n} = \left( 1+ \frac{1}{n} \right)^{n+1} = \left( 1+\frac{1}{n} \right)^{n}\left( 1+\frac{1}{n} \right)=f_{n}\left( 1+\frac{1}{n} \right)
}
$$
Sapendo che $\left( 1+\frac{1}{n} \right) \rightarrow 1$
$$
\large h_{n}\geq f_{n}
$$
Di conseguenza, crescenze e decrescenze di $f_{n}$ e $h_{n}$
$$
\large 2 = f_{1}\leq f_{n}\leq h_{n}\leq h_{1} = 4 \qquad \forall n \in \mathbb{N} \setminus \{ 0 \}
$$
$h_{n}$ e $f_{n}$ sono [[Limiti di Successioni#Terminologia|regolari]] e [[../Funzioni/Introduzione Funzioni#Limitazioni|limitate]], quindi sono [[Limiti di Successioni#Terminologia|convergenti]].

Inoltre, poichè $h_{n}=f_{n}\left( 1+\frac{1}{n} \right)$ con $\left( 1+\frac{1}{n} \right) \rightarrow 1$
$$
\large \lim_{ n \to \infty } h_{n}  = \lim_{ n \to \infty } f_{n}
$$
E quindi per il teorema del confronto il valore è $2<x<4$ e lo definiamo
$$
\large e: \lim_{ n \to +\infty } \left( 1+\frac{1}{n} \right)^{n}
$$