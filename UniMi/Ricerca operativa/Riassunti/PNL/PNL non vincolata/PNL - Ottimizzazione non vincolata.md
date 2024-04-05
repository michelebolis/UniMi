Assumiamo che la funzione obiettivo $f(x)$ da minimizzare sia continua e differenziabile
Il gradiente di una funzione $f(x_1, ..., x_n)$ è il vettore delle su derivate parziali di primo ordine
$$\bigtriangledown f(x) = [\frac{\partial f}{\partial x_1}...\frac{\partial f}{\partial x_n}]^T$$
L'Hessiano di una funzione $f(x_1, ..., x_n)$ è la matrice delle sue derivate parziali di secondo ordine (matrice simmetrica perchè è indifferente derivare prima per x e poi per y)
![[Pasted image 20240328170725.png]]

Caratterizzazione dei minimi locali
Condizioni necessarie del primo ordine $\bigtriangledown f(\overline{x}) = 0$
Condizioni necessario del secondo ordine $\bigtriangledown ^2 f(\overline{x}) \geq 0$ (semi definita positiva)
Condizioni sufficienti del secondo ordine $\bigtriangledown ^2 f(\overline{x}) > 0$ (definita positiva)

[[PNL non vincolata - Algoritmi]]