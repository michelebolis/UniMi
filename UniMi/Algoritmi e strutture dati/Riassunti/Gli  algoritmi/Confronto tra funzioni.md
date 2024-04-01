Date due funzioni $f, g$ quale cresce di più?

Logaritmo < lineare < esponenziale
SE entrambe lineare, confronto grado 1 a n, se invece stesso grado guardo la costante

Date $f, g : N -> R^+$
- Limitazione superiore:
$f(n)$ è o-grande di $g(n)$, $f(n) = O(g(n))$ SE $\exists c > 0, \forall n_0 \in N$ t.c. $n>n_0$ : 
$f(n) \leq c * g(n)$

- Limitazione inferiore:
$f(n)$ è omega-grande di $g(n)$, $f(n)= \Omega(g(n))$ SE $\exists c > 0, \forall n_0 \in N$ t.c. $n>n_0$ : 
$f(n) \geq c * g(n)$

- Stesso ordine di grandezza
$f(n)$ è theta-grande di $g(n)$, $f(n)=\Theta(g(n))$ SE $\exists c, d > 0$, $n_0 \in N$ t.c. $\forall n>n_0$ : $c*g(n) \leq f(n) \leq d*g(n)$

Proprieta di $O, \Omega, \Theta$
$f(n)=(g(n))$ ALLORA $\forall k>0$, $k*f(n)=O(g(n))$
$f_1(n)=O(g_1(n))$ e f_2(n)=O(g_2(n)) ALLORA 
	$f_1(n)+f_2(n)=O(g_1(n)+g_2(n))$
	$f_1(n)*f_2(n)=O(g_1(n)*g_2(n))$

ATT non vale $f_1(n)-f_2(n)= …$

