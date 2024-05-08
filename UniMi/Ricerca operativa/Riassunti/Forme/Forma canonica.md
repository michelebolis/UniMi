Data la [[Forma standard|forma standard]] di un problema di PL
minimize $z = c^T x$
subject to $Ax = b$
$x\geq 0$

1. Scegliendo una `base` e `permutando le colonne` di conseguenza si ha
minimize $z = c^{T}_B x_B + c^T_N x_N$
subject to $Bx_B + Nx_N = b$
$x_B, x_N \geq 0$

2. Moltiplicando a sinistra per $B^{-1}$
minimize $z = c^{T}_B x_B + c^T_N x_N$
subject to $I_{X_B} + (B^{-1} N) x_N = B^{-1} b$
$x_B, x_N >\geq 0$
con $I$ `matrice di identità`

La soluzione di base $x_B = B^{-1} b - (B^{-1} N) x_N$

- Sostituendo $x_B = B^{-1} b - (B^{-1} N) x_N$ in $z$
minimize $z = c^T_B B^{-1} b + (c^T_N - c^T_B B^{-1} N) x_N$
subject to $I_{X_B} + (B^{-1} N) x_N = B^{-1} b$
$x_B, x_N >=0$

- Riscrivendo $z$
minimize $z = z_B + \overline{c}^T_N x_N$
subject to $I_{x_B} + \overline{N}x_N = \overline{b}$

con $z_B$ costante che dipende da B, come abbiamo scelta la base
con $\overline{c}$ perche sono diversi dai $c$ coefficienti iniziali

- Quando si pone $x_N = 0$ si ha $x_B = B^{-1} b = \overline{b}$
SE $\overline{b}$ >= 0 ALLORA la soluzione di base è ammissibile 

`Esistono un numero combinatorio di forme canoniche, tante quante le possibili scelte della base`

Un problema di PL è in forma canonica SE e SOLO SE
- i coefficienti delle variabili di base, $x_B$, formano una matrice identità $m * m$
- le variabili di base $x_B$ NON compaiono nella funzione obiettivo

La forma canonica è `forte` SE e SOLO SE i termini noti dei vincoli sono non negativi, $\overline{b} \geq 0$
`Una forma canonica debole implica una soluzione di base non ammissibile `

[[Es forma canonica]]