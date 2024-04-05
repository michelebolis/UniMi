Una funzione di merito combina insieme i due effetti tramite un opportuno penalty parameter, $\mu$
Una funzione di merito $\phi(x, \mu)$ è esatta quando esiste un valore scalare positivo $\mu^*$ t.c. per ogni $\mu > \mu^*$ ogni minimo locale del problema vincolato è un minimo locale di $\phi(x, \mu)$

- L1 penalty function

$$\phi_1(x, \mu) = f(x) + \mu \sum_{i \in E} |c_i(x)| + \mu\sum_{i \in I}[c_i(x)]^-$$
con $[k]^-$ indica $max\{0, -k\}$ quindi $[c_i(x)]^-$ indica quanto la violazione, di quanto è negativo
La funzione $\phi_1(x, \mu)$ NON è differenziabile ovunque, ma è esatta
Il valore soglia è dato da 
$$\mu^*=\max_{i \in E \cup I}\{|\lambda^*_i|\}$$
Con $\lambda^*_i$ il vettore dei moltiplicatori duali corrispondenti ad una soluzione ottima $x^*$
Dato che $\lambda^*_i$ non è noto a priori, occorre iterativamente ricalibrare il valore di $\mu$

- L2 penalty function

Nei casi dei vincoli di uguaglianza
$$\phi_2(x, \mu)=f(x)+\mu||c_i(x)||^2$$
Non è differenziabile perché la derivata non è definita dove $c(x)=0$

- Fletcher's augmented lagrangian

E' sia differenziabile che esatta MA pesante a causa di $\lambda(x)$
$$\phi_F(x, \mu) = f(x) - \lambda(x)^Tc(x)+\frac{1}{2}\mu\sum_{i\in E}c_i(x)^2$$
con
$$\lambda(x)=[A(x)A(x)^T]^{-1}A(x)\bigtriangledown f(x)$$
e $A(x)$ indica lo Jacobiano di $c(x)$

- Lagrangiana aumentata

$$L_A(x, \lambda, \mu) = f(x) - \lambda^Tc(x) + \frac{1}{2}\mu||c(x)||_2^2$$
Si accetta un punto prossimo $(x^{k+1}, \lambda^{k+1})$ SE la $L_A$ diminuisce rispetto al punto corrente $(x, \lambda)$
Gli algoritmi che usano questa funzione di merito includono criteri per modificare opportunamente i valori di $\lambda$ e $\mu$

