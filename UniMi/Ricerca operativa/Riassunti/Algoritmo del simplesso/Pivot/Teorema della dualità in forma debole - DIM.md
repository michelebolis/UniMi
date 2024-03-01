Dati
- $P$: maximize $z = c^Tx$, s.t. $Ax \leq b$, $x \geq 0$
- $D$: minimize $w = b^Ty$, s.t. $A^Ty \geq c$, $y \geq 0$

$$\forall\bar{x} \in X, \bar{y} \in Y, c^T\bar{x}\leq b^T\bar{y}$$
$A^T\bar{y} \geq c, \bar{x} \geq 0$ (sostituendo le soluzioni nei vincoli)
$\bar{x}^TA^T\bar{y} \geq  \bar{x}^T c$ (se multiplico per $\bar{x}^T$ il segno rimane lo stesso)
$c^T\bar{x} \leq \bar{x}^TA^T\bar{y}$ (leggo la disequazione da destra a sinistra)
Analogamente
$A\bar{x} \leq b$, $\bar{y} \geq 0$ (sostituendo le soluzioni nei vincoli)
$\bar{y}^TA\bar{x} \leq \bar{y}^Tb$ (se multiplico per $\bar{y}^T$ il segno rimane lo stesso)
$b^T\bar{y} \geq \bar{y}^T A\bar{x}$
In entrambi i casi, il secondo membro è uno scalare (e sapendo che lo scalare è uguale al suo trasposto)
$\bar{x}^TA^T\bar{y} = (\bar{x}^TA^T\bar{y})^T = \bar{y}^T (A^T)^T (\bar{x}^T)^T =  \bar{y}^T A\bar{x}$
$c^T\bar{x} \leq \bar{x}^TA^T\bar{y} = \bar{y}^TA\bar{x} \leq b^T\bar{y}$
