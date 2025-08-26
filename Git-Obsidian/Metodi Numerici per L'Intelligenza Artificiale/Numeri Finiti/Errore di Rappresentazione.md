T> Gli errori esistono a causa della [[Floating Point#Numeri Finiti Floating Point|tecnica rappresentazione dei floating point]]

Poiché in un calcolatore il numero reale $\alpha\neq 0$ è sostituito con $fl(\alpha)$, è fondamentale stabilire una ***stima della differenza*** tra $\alpha$ e $fl(\alpha)$.

>[!danger] Errore Assoluto
>Si definisce ***errore assoluto*** di approssimazione la quantità:
>$$E_{\alpha}=\mid \alpha -fl(\alpha)\mid$$
>>[!note] Nota
>>L’errore assoluto è influenzato dall’*ordine di grandezza* di $\alpha$

>[!important] Errore Relativo
>Si definisce ***errore relativo*** di arrotondamento di $\alpha\neq0$ la quantità:
>$$E_{rel}=\displaystyle{\frac{\mid \alpha -fl(\alpha)\mid}{\mid\alpha\mid}}$$
>>[!note] Nota
>>L’errore relativo non dipende dall’**esponente** di $\alpha$, ma dalla sua **mantissa**, e dà indicazioni sull’*approssimazione* operata sulla mantissa.

>[!cite] Teorema
>Sia $\alpha\neq 0$ un numero reale rappresentato in base $\beta$ come:
>$$\alpha = \pm 0.a_{1}a_{2}\dots \ \cdot\beta^p, \quad a_{1}\neq 0, \quad p\in[L,U]$$
><u> Allora </u>
>Se non si verifica overflow, si ha:
>$$\mid\alpha-fl(\alpha)\mid\leq K\cdot\beta^{p-t}$$
>$$\displaystyle{\frac{\mid \alpha -fl(\alpha)\mid}{\mid\alpha\mid}}\leq K \cdot\beta^{1-t}$$
>
>Con:
>- $K=1$ nel caso di [[Floating Point#Troncamento e Arrotondamento|troncamento]]
>- $K=\frac{1}{2}$ nel caso di [[Floating Point#Troncamento e Arrotondamento|arrotondamento]]

> In generale, per la stima dell'errore si preferisce considerare l'errore relativo invece di quello assoluto.

