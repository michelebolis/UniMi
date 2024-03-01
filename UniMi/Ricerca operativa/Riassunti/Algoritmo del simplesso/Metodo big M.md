Anziché eliminare dalla formulazione del problema artificiale le variabili $x$, è possibile mantenerle e penalizzare nell'obiettivo le variabili $u$ con coefficienti molto grandi
$$z^a = min\{c^Tx+w^Tu:Ax+Iu  = b, x,u \in R^n_+\}$$
con $w^T=[M, ..., M]$ vettore di coefficienti abbastanza grandi, t.c. ogni soluzione con una variabile $u_i > 0$, abbia costo maggiore del valore ottimo $z^*$ del problema 

Vantaggio: non serve una fase di inizializzazione
Svantaggio:
- il valore $M$ potrebbe provocare instabilità numerica
- non è detto che sia facile determinare il valore appropriato per $M$