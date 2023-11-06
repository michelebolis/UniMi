Possiamo rappresentare lo stesso modello in maniera piu compatta come
maximize $w = c^T x$
subject to $A_x <= b$
$x >= 0$

es 


| Item        | $x_3$      | $x_4$  | $x_5$  | Vincolo |
| ----------- | ------- | --- | --- | ------- |
| maximize  z | $+x_3$  | $+3x_4$    | $-3x_5$    |    |
| Subject to  | $-3x_3$ | $+2x_4$    | $-2x_5$    | <=  9   |
|             | $-4x_3$ | $-3x_4$    | $+3x_5$    | <= 8   |
|             | $x_3$ ,   | $x_4$ ,   | $x_5$    | >= 0    |


$$c^T = \begin{bmatrix}1 && 3  && -3\end{bmatrix}$$
$$A = \begin{bmatrix}-3 && 2  && -2 \\ -4 && -3 && 3\end{bmatrix}$$
$$x = \begin{bmatrix} x_3 \\ x_4 \\ x_5 \end{bmatrix}$$
$$b = \begin{bmatrix} 9 \\ 8 \end{bmatrix}$$
