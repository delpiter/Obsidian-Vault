## Operazioni
- - -
>[!info] Definizione
>Siano $(a_{n}),(b_{n})_{n\in\mathbb{N}},\ l,m\in\mathbb{R}$
><u>Allora</u>
> $$
\begin{array}{}
\lim\limits_{n\to+\infty}a_{n}\pm b_{n}=l\pm m \\ \\
\lim\limits_{n\to+\infty} a_{n}\cdot b_{n}=l\cdot m \\
\lim\limits_{n\to+\infty} \displaystyle{\frac{a_{n}}{b_{n}}}=\frac{l}{m}, b_{n}\neq 0, m\neq0 \\
\lim\limits_{n\to+\infty} \displaystyle{\frac{a_{n}}{b_{n}}}=0,\text{ se } m=\pm\infty,l\in\mathbb{R}
\end{array}
>$$

### Casi $\pm\infty$ con la somma
$$
\begin{cases}
+\infty+\infty = +\infty \\
-\infty-\infty=-\infty \\
l\in\mathbb{R}\begin{cases}
l+\infty=+\infty \\
l-\infty=-\infty
\end{cases} \\
\end{cases}
$$
### Casi $\pm\infty$ con il prodotto
$$
\begin{cases}
+\infty\cdot(+\infty)=+\infty \\
+\infty\cdot(-\infty)=-\infty \\
-\infty\cdot(-\infty)=+\infty
\end{cases}
$$
### Forme indeterminate
$$
\begin{cases}
+\infty-\infty \\
0\cdot(\pm\infty) \\
\displaystyle{\frac{0}{0}} \\
\displaystyle{\frac{\pm\infty}{\pm\infty}}
\end{cases}
$$
##### Osservazione
$$
\begin{array}{}
\lim\limits_{n\to+\infty}a_{n}=l,\ \ \ \lim\limits_{n\to+\infty}b_{n}=0 \\
\displaystyle{\frac{a_{n}}{b_{n}}} \text{ in generale non diverge}
\end{array}
$$
### Esempi
$$
\begin{array}\
\lim\limits_{n\to+\infty} \displaystyle{\frac{n^3+2n-7}{n-3n^2+1}}= \\
=\lim\limits_{n\to+\infty} \displaystyle{\frac{n^3\left( 1+ \displaystyle{\frac{2}{n^2}}- \displaystyle{\frac{7}{n^3}} \right)}{n^2\left( -3 \displaystyle{\frac{1}{n}+ \displaystyle{\frac{1}{n^2}}} \right)}}= \\
\text{Le parentesi tendono ad un numero reale} \\
=\lim\limits_{n\to+\infty} \displaystyle{\frac{n^3}{-3n^2}}=\lim\limits_{n\to+\infty} \displaystyle{\frac{n}{-3}}=-\infty
\end{array}
$$