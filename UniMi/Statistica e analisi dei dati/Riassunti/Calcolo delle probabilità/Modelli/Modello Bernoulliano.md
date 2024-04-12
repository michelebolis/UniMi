Il modello Bernoulliano di parametro $p$ è descritto da una variabile aleatoria $X$ che caratterizza l'esito di un esperimento, che quindi può essere positivo o negativo
$$X \sim B(p)$$
Ha un esito positivo, $X=1$, e un esito negativo, $X=0$
$\Omega = \{P, N\}$
$A = 2^\Omega$
Fissato $p\in[0,1]$
$$P(P) = p$$
$$P(N) = 1 - p$$
V.A. di Bernoulli $D_X = \{0,1\}$,
$$f_X(x) = \begin{cases} p \text{ SE } x = 1 \\ 1-p \text{ SE }x = 0 \end{cases}$$
$$F_X(x)=\begin{cases} 0 \text{ SE } x < 0 \\ 1 - p \text{ SE } 0 \leq x \leq 1 \\ 1 \text{ SE } x > 1 \end{cases}$$
$$E(X) = p$$
DIM
$E(X) = \sum_{x \in  D_X}x*f_X(x) = 1*f_X(1)=p$
$E(X) = \int_0^\infty 1-F_X(x) dx=p$ 
$$Var(X) = p*(1-p)$$
DIM
$Var(X) = E((X-p)^2) = \sum_{x \in D_X}(x-p)^2*f_X(x)$
$= (0 - p)^2 * (1 - p) + (1-p)^2 * p = p^2 * (1 - p) + p * (1 - p) = p * (1 - p) * (+p -p +1) = p * (1 - p)$
$Var(X) = E(X^2) - E(X)^2 = E(X) - E(X)^2 = E(X) * (1 - E(X)) = p * (1 - p)$

$f_X(x) = p^x * (1 - p)^{(1 - x)}$
Problema: indipendentemente da $X$, il dominio di $f$ e $F$ è $R$, ma in $f$ per come l ho scritto non ho i casi per $x\neq$ da 0 e 1, dovendo quindi $f_X(x)=0$ altrimenti
$$f_X(x)=p^x*(1-p)^{1-x}*I_{(0,1)}(x)$$
$$F_X(x)=(1-p)*I_{(0,1)}(x)+I_{[1,\infty)}(x)$$
