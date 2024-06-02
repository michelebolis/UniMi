Dato un sistema di disequazioni lineari $Ax \leq b$, $x \geq 0$ con $A$ di dimensione $m$ x $n$ e $b$ di dimensione $m$, una e una sola di queste alternative è vera 
$$\exists x \in R^n : Ax \leq b, x \geq 0$$
$$\exists y \in R^m : A^Ty \geq 0, b^Ty <0, y \geq 0$$
OSS $y\geq 0$ non c era prima

DIM 
Introduciamo variabili di slack non negative
La condizione 1 diventa
$\exists x \in R^n, s \in R^m : Ax+Is = b, x \geq 0, s \geq 0$
Definendo $A' = [A|I]$ di dimensioni ($m$ x ($n + m$)) e $x' = \begin{bmatrix} x \\ s \end{bmatrix}$ di dimensioni ($n+m$) x 1, la condizione 1 diventa
$\exists x' \in R^{n+m} : A'x' = b, x' \geq 0$
Per il teorema di Farkas, essa è alternativa alla condizione
$\exists y \in R^m : A'^Ty \geq 0, b^Ty < 0$
Il sistema di disequazioni $A'^T y \geq 0$ equivale a $A^Ty \geq 0, y \geq 0$
