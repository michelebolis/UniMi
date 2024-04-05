Il problema ora è ottenere $B$ e $N$ 
Per eseguire un passo di pivot, si sceglie una variabile primale fuori base con costo ridotto negativo, una colonna $q \in N$ t.c. $s_q <0$ (vincolo violato)
Indichiamo con $T=B^{-1}A$ il tableau corrente (che non vogliamo calcolare esplicitamente)
Sia $T_q$ la sua colonna corrispondente alla variabile $x_q$ (che calcoliamo esplicitamente)
$$T_q = B^{-1}A_q$$
dove $A_q$ indica la colonna $q$ della matrice $A$

Indichiamo con $p \in B$ l'indice della variabile primale uscente
$$p=argmin_{i:T_{iq}>0}{\{\frac{(x_B)_i}{T_{iq}}\}}$$
dove $(x_B)_i$ indica il valore della variabile in base alla riga $i$

Il nuovo valore di $x_q$, entrando in base, è $x'_q = \frac{(x_B)_p}{T_{pq}}$
Sapendo che x e x' sono soluzioni ammissibili
$$Ax = b, Ax'=b$$
$$x_N=0, x_i'=0, \forall i \in N \backslash \{q\}$$
Poiché
$$b=Ax=Bx_B$$
$$b=Ax'=Bx'_B+A_qx'_q$$
uguagliando si ha
$$x_B'=x_B-B^{-1}A_qx_q'$$
Nel duale
$$y^T = c_B^TB^{-1}$$
$$A_q^Ty+s_q = c_q, s_q=c_q-y^TA_q$$
