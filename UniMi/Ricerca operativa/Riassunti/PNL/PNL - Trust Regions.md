Richiedono di
- approssimare la funzione $f()$ con un metodo $m_k()$ che viene aggiornato ad ogni iterazione $k$
- cercare un minimo di $m_k()$ in un  intorno di raggio $p_k$ della soluzione corrente $x_k$

SE la diminuzione del valore dell'obiettivo non è grande abbastanza, il raggio viene diminuito e l'ottimizzazione viene ripetuta
In questo metodo prima scegliamo il passo e poi la direzione
Solitamente il modello $m$ è quadratico e usa il gradiente $\bigtriangledown f_k$ e l'Hessiano o una sua approssimazione $B_k$
$$m_k(x_k+p) = f_k+p^T \bigtriangledown f_k + \frac{1}{2}p^TB_kp$$
