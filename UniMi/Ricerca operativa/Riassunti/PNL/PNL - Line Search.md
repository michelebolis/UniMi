Negli algoritmi line search, le scelte piu comuni per definire la direzione $d^{(k)}$ sono
- [[Line Search - Metodo del gradiente]]: scelgo la direzione opposta a quella del gradiente, $-\bigtriangledown f(x^{(k)})$
- [[Line Search - Metodo di Newton]]: scelgo una direzione $-B^-1\bigtriangledown f(x^{(k)})$, con B una matrice semi definita positiva
- metodo del gradiente coniugato: una direzione $-\bigtriangledown f(x^{(k)}) + \beta _kd^{(k-1)}$ che considera anche la direzione del passo precedente

Scelta del passo
Una volta scelta la direzione $d^{(k)}$ nei metodi line search rimane un problema di minimizzazione ad una sola variabile, lo scalare $s_k\geq 0$ (monodimensionale)
$$minimize f(x^{(k+1)}=f(x^{(k)}+s_kd^{(k)})$$
L'ottimizzazione esatta di $s_k$ non è indispensabile infatti una buona approssimazione è sufficiente per avviare l'iterazione successiva dopo aver migliorato $f(x)$

Gli algoritmi per determinare il passo possono essere classificati in
- algoritmi che richiedono il calcolo della derivata
	- [[Line Search - Metodo di bisezione]]
- algoritmi derivative free
	- [[Line Search - Metodo dei numeri di Fibonacci]]
