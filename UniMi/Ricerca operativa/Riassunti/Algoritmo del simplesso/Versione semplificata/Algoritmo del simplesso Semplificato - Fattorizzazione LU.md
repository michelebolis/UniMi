Per calcolare rapidamente l'inversa di B, si rappresenta $B=LU$ come prodotto tra due matrici triangolari
- una matrice $L$ unit lower triangular (gli elementi sulla diagonale hanno valore 1 e sopra la diagonale hanno valore 0)
- una matrice $U$ upper triangular (gli elementi sotto la diagonale hanno valore 0)

Il calcolo di $T_q=B^{-1}A_q$, cioè t.c. $BT_q=A_q$ si divide in due step
- Trovare $d:Ld=A_q$
- Trovare $T_q:UT_q=d$

Analogamente il calcolo di $y = (B^{-1})^Tc_B$, t.c. $B^Ty=c_B$ si divide in due step
- Trovare $d:U^Td=c_B$
- Trovare $y:L^Ty=d$

Tutti gli step sono calcolabili efficientemente per eliminazione Gaussiana

Aggiornamento di LU
Nel passaggio da B a B', quando x_q entra in base e x_p esce, bisogna aggiornare efficientemente L e U

$L^{-1}B = U$ è triangolare superiore
Sia $j$ l'indice della colonna di $U$ che corrisponde a $x_p$
$L^{-1}B'$ è ancora triangolare superiore tranne la colonna $j$

Con
- una permutazione ciclica delle colonne che sposta $j$ in fondo e tutte le colonne da $j+1$ a $n$ a sinistra di una posizione
- una permutazione ciclica delle righe che sposta la riga $j$ in fondo e tutte le righe da $j+1$ a $n$ in alto di una posizione

Si ottiene una nuova matrice triangolare superiore con in aggiunta alcuni elementi non zero sull'ultima riga
Essa si puo esprimere come prodotto tra una matrice $L'$ identica a $I$ tranne che nell'ultima riga ed una matrice $U'$ identica alla matrice permutata tranne che nell'ultimo elemento in basso a destra

Anche questi nuovi coefficienti si ricavano in modo efficiente per eliminazione Gaussiana

es
![[Pasted image 20240405091416.png|400]]
![[Pasted image 20240405091430.png|400]]
![[Pasted image 20240405091443.png|400]]