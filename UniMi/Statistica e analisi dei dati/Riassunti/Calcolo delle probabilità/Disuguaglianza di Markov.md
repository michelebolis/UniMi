Consideriamo $X \geq 0$ e in tal caso $\forall a > 0$, 
$$P(X\geq a)\leq \frac{E(X)}{a}$$
SE aumento $a$, la $P$ diventa meno probabile e infatti a è al denominatore e quindi la frazione diminuisce
Ci permette di avere una stima della $P$ ma è utile SE consideriamo $\frac{E(X)}{a} < 1$

DIM
$E(X) = \sum_{x \in D_X} x*f_X(x)=\sum_{x<a}x*f(x)+\sum_{x\geq a}x*f_X(x)$
= somma di fattori mai negativi, quindi anche i prodotti non negativi + …
$$= \geq 0+...+\geq\sum_{x\geq a}x*f_X(x) \geq \sum_{x\geq a}a*f_X(x)$$
// perché sapendo che $x\geq a$ allora sicuro la somma sarà maggiore della somma in cui invece di $x$ ho $a$
$= a*\sum_{x\geq a} f_X(x)=a*P(X\geq a)$
$E(X) \geq a*P(X\geq a)$
$\frac{E(X)}{a}  \geq P(X \geq a)$
//sapendo che $a>0$ non cambia verso
$P(X < a) = a-P(X \geq a) \geq 1-\frac{E(X)}{a}$
