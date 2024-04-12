$E(| X - \mu |)$ MA il valore assoluto non è facile da gestire
Varianza della variabile aleatoria $X$
$$Var(X)=E((X-\mu)^2)= \sum_{x_i \in D}(x_i-\mu)^2*P(X=x_i)$$
Ma non semplice sempre da calcolare

$Var(X)= E((X - \mu)^2) = E(X^2 -2X\mu + μ^2) = E(X^2) + E(-2X\mu) + E(μ^2)$
// grazie alla linearità del valore atteso
$= E(X^2) -2μ * E(X) + μ^2 = E(X^2) -2μ*μ +μ^2 = E(X^2) -μ^2 = E(X^2) - (E(X) )^2$

$E(X^2)$ è il momento secondo della variabile aleatoria $X$

Deviazione standard
$$\sigma_X=\sqrt{Var(X)}$$

Proprietà varianza:
- Trasformazione lineare
Sapendo che
$$\sum_{i=1}^n i^2= \frac{n*(n+1)*(2n+1)}{6}$$

Data una variabile aleatoria $X$ e $Y = a*X +b$
$$Var(a*X)=a^2*Var(X)$$
DIM
$Var(X)= E( (Y - E(Y))^2 ) = E( (a*X-b -a*E(X) -b)^2) =$ 
$E ( (a * (X - E(X))^2 ) = a^2 * E( (X - E(X))^2 ) = a^2 * Var(X)$

SE $a=0$, $Var(b)=0$

- SE $X, Y$ indipendenti
$Var(X + Y) = Var(X) + Var(Y)$
- SE $X$ e $Y$ generici
$Var(X + Y) = Var(X) - Var(Y) - 2 * Cov(X, Y)$
DIM
$Var(X + Y) = E((X + Y)^2) - E(X + Y)^2 = E(X^2 + 2XY + Y^2) - (E(X) + E(Y))^2$
$= E(X^2) + 2*E(XY) + E(Y^2) - E(X)^2 - 2E(X)E(Y) - E(Y)^2 =$
$= E(X^2) - E(X)^2 + E(Y^2) - E(Y)^2 + 2*(E(XY) - E(X)*E(Y))$
$= Var(X) - Var(Y) - 2 * Cov(X, Y)$
