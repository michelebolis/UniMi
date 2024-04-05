Consideriamo un problema di PL in forma standard
minimize $z = c^Tx$
subject to $Ax = b$
$x \geq 0$

con $n+m$ variabili non negative e $m$ vincoli di uguaglianza
Il suo duale è 
maximize $w = b^Ty$
subject to $A^Ty \geq c$

con $m$ variabili libere e $n+m$ vincoli di disuguaglianza

- Base primale

Scelta una base di $m$ colonne, il primale si puo riscrivere
minimize $z =  c^T_Bx_B+c^T_Nx_N$
subject to $Bx_B+Nx_N = b$
$x_B, x_N \geq 0$
con
$A = [B|N]$
$x^T  = [x_B|x_N]$
$c^T=[c_B|c_N]$

- Base duale

Il duale si puo mettere a sua volta in forma standard inserendo variabili non negative di slack
maximize $w=b^Ty$
subject to $A^Ty+s=c$
con $m$ variabili $y$ libere, $n+m$ variabili $s \geq 0$ e $n+m$ equazioni

Dato che $A^T = \begin{bmatrix} B^T \\ N^T \end{bmatrix}$ il duale si puo riscrivere
maximize $w = b^Ty$
subject to $B^Ty+s_B=c_B$
subject to $N^Ty+s_N=c_N$


Per il teorema degli scarti complementari, per ogni coppia di basi primale/duale che si corrispondono si ha che $x_is_i=0$ (una delle due deve essere fuori base), QUINDI $s_B = 0$
Da $B^Ty = c^B$ si ottiene
$$y = (B^T)^{-1}c_B$$
Da $N^Ty+s_N=c_N$ si ottiene
$$s_N = c_N- N^T(B^T)^{-1}c_B = $$
$$c_N- N^T(B^{-1})^{T}c_B =$$
$$c_N- (B^{-1}N)^{T}c_B$$
Nel primale invece si ha
$$x_B=B^{-1}b, x_N=0$$
Cosi le soluzioni primale e duale si possono calcolare a partire da $B$ e $N$ e i dati iniziali
