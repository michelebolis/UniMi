Richiede il calcolo della derivata
Dato un intervallo iniziale $r=[a,b]$ per $s_k$
1. calcolare $\bigtriangledown f(x^{(k)+\frac{a+b}{2}d^{(k)}})$
	1. SE positiva, porre $r=[a, \frac{a+b}{2}]$
	2. SE negativa, porre $r=[\frac{a+b}{2},b]$
2. ripetere finche $r$ è abbastanza piccolo 