Siano $m, a, b', b^n, c \in R^+$ con $a>1$
L'equazione $F(n) = \begin{cases} b' \text{ SE } n=1 \\ m*F(\frac{n}{a}) + b^n * n^c \text{ SE } n>1 \end{cases}$

Soddisfa le seguenti relazioni
$$F(n) = \begin{cases} \Theta(n^c) \text{ SE } m < a^c \\
\Theta(n^c * \log n) \text{ SE } m=a^c \\
\Theta(n^{(\log{a}) m}) \text{ SE } m > a^c \end{cases}$$

Es 
$H(n) = \begin{cases} 1+H(\frac{n}{2})\\ 1 \end{cases}$
$b'=b^0 = 1$
$m=1$
$c=0$
$a=2$
$a^c = 1 = m$
$H(n)= \Theta(\log n)$

