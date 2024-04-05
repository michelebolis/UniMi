Il valore dell'obiettivo z dopo il pivot è 
$$z = c^Tx'=c_B^Tx'_B+c_qx'_q = $$
$$c_B^T-c_B^T B^{-1}A_qx_q'+c_qx'_q = $$
$$c_B^T-y^TA_qx_q'+c_qx'_q =$$
$$c_B^T-(c_q-s_q)x'_q+c_qx'_q =$$
$$c_B^T+s_qx'_q= z+s_qx'_q$$
SE l'iterazione non è degenere, $s_q <0$ e $x'_q > 0$ implicano $z'<z$
QUINDI tutto ciò che serve per procedere con le iterazioni dell'algoritmo del simplesso $(x,y,s,z)$ puo essere calcolato a partire dai dati iniziali seguendo solo prodotti tra vettore e matrice e non tra matrice, conoscendo PERO $B^-1$
