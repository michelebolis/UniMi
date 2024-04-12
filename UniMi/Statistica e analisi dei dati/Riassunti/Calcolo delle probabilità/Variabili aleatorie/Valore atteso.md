Il valore atteso di una variabile aleatoria $X$ con supporto $D=\{x_1, x_2, …\}$ (essendo discreto posso scriverlo intensivamente) da un idea di centralità della distribuzione  
- SE X discreta
$$E(X)=\mu=\sum_{x_i\in D}x_i*P(X=x_i)$$
- SE X continua
$$E(X) = \int_{-\infty}^{+\infty}x*f(x) dx$$

Sommatoria potenzialmente infinita, a volte converge ma a volte diverge
ATT Il valore atteso di $X$ è definito SOLO SE la serie converge in valore assoluto
$$\sum_{x_i \in D}|x_i|*P(X=x_i) <\infty$$

In realtà è una media pesata delle specificazione considerando come pesi le probabilità

Proprieta del valore atteso
- Trasformazione lineare alla variabile aleatoria

Funzione $g: R --> R$

- SE X discreta  
$$E(g(X))=\sum_{x_i \in D}g(x_i)*P(X=x_i)$$
- SE X continua
$$E(g(X))=\int_{-\infty}^{\infty} g(x)*f(x) dx$$

$g(X) = a*X + b | a, b \in R$
$E(a*X+b) = a*E(X)+b$
DIM
$E(a*X + b)= \sum_{x_i \in D} (a*x_i+b)*P(X=x_i) = (\sum_{x_i \in D} a*x_i) + (\sum_{x_i \in D} b*P(X=x_i) )$
$= a*\sum_{x_i \in D} x_i*P(X=x_i) + b*\sum_{x_i \in D} P(X = x_i) = a*E(X) + b*1$

SE $a = 0, E(b) = b$ otterremmo una variabile aleatoria con supporto contenente una solo specificazione $b$
SE $b = 0, E(a*X) = a*E(X)$

Il valore atteso è un operatore lineare

- SE $X, Y$ indipendenti

$E(XY) = E(X) * E(Y)$
`DIM`
$E(XY) = \sum_{x \in D_X}\sum_{y \in D_Y} xy * f_{XY}(x, y)$
$=\sum_{x \in D_X}\sum_{y \in D_Y} xy * f_X(x) * f_Y(y)$
$=\sum_{x \in D_X}x*f_X(x)\sum_{y \in D_Y} y* f_Y(y) = E(X)*E(Y)$

- SE $n=1, 2, …$  la quantita $E(X^n)$ è detta momento n-esimo della variabile aleatoria $X$
	- SE $X$ è discreta, $\sum_{x \in D}x^n*p(x)$
	- SE $X$ è continua, $\int_{-\infty}^\infty x^n*f(x)dx$

