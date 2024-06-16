`Nel primo ordine non siamo in grado di distinguere i massimi dai minimi`
Assumiamo che $f(x)$ e $c_i(x)$ siano tutte continue e differenziabili fino al secondo ordine
Siano
- $F(x^*)$ l'`insieme delle direzioni ammissibili` in $x^*$
- $\lambda^*$ un `vettore di moltiplicatori Lagrangiani` che soddisfano le KKT in $x^*$

DEF `Cono critico` in un punto $(x^*, \lambda^*)$ è l'`insieme delle direzioni ammissibili` t.c. il prodotto scalare tra le direzione e la normale è 0 per tutti i vincoli di disuguaglianza attivi nel punto con il $\lambda$ positivo
$$C(x^*, \lambda^*) = \{w \in F(x^*):\bigtriangledown c_i(x^*)^Tw=0, \forall i \in A(x^*) \cap I : \lambda_i^* >0  \}$$
QUINDI
$$w \in C(x^*, \lambda^*)\Leftrightarrow \begin{cases}
\bigtriangledown c_i(x^*)^Tw=0, \forall i \in E \\
\bigtriangledown c_i(x^*)^Tw=0, \forall i \in A(x^*) \cap I:\lambda_i^* >0 \\
\bigtriangledown c_i(x^*)^Tw \geq 0, \forall i \in A(x^*) \cap I:\lambda_i^* =0 
\end{cases}$$
Dato che $\lambda_i^*=0, \forall i \notin A(x^*)$,
$$w \in C(x^*, \lambda^*) \implies \lambda_i^*\bigtriangledown c_i(x^*)^Tw=0, \forall i \in E \cup I$$
Dalla definizione di $L(x, \lambda)$ e dalle KKT
$$w \in C(x^*, \lambda^*) \implies w^T\bigtriangledown f(x^*) = \sum_{i \in E \cup I} \lambda_i^*w^T\bigtriangledown c_i(x^*)=0$$
QUINDI `il cono contiene le direzioni ammissibili per le quale le derivate prime non danno sufficienti informazioni`

es
![[Pasted image 20240403103243.png|300]]
