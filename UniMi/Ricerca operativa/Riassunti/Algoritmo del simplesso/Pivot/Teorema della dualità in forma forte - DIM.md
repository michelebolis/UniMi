Sia $y^* \in R^m$ la soluzione ottima finita del duale $D$ e $w^* = b^Ty^*$ il suo valore
Vogliamo dimostrare che $\exists x^* \in R^n : x^* \leq b$, $x^* \geq 0$ e che il suo valore soddisfa la disequazione $c^Tx^* \geq b^Ty^*$

Procedendo per assurdo, supponiamo che tale soluzione $x^*$ del primale $P$ non esista e utilizzando il lemma di Farkas, dimostriamo che in tal caso sarebbe violata l'ipotesi di ottimalità di $y^*$
$\nexists x \in R^n : Ax \leq b, x \geq 0, c^Tx \geq w^*$
$\nexists x \in R^n : Ax \leq b, x \geq 0, -c^Tx \leq -w^*$
Definiamo
$A' = \begin{bmatrix} A \\ -c^T \end{bmatrix}, b' = \begin{bmatrix} b \\ -w^* \end{bmatrix}$
$A'$ di dimensione $(m+1)$ x $n$ e ($m+1$) x 1
$\nexists x \in R^n : A'x \leq b', x \geq 0$

Per il Lemma di Farkas, ciò implica che 
$\exists y' \in R^{m+1} : A'^Ty' \geq 0, b'^Ty' < 0, y' \geq 0$
Sia
$y' = \begin{bmatrix} y \\ \lambda \end{bmatrix}$
con $y \in R^m$ e $\lambda \in R$, allora il sistema equivale a 
$A^Ty-c\lambda \geq 0, b^Ty-w^*\lambda < 0, y  \geq 0, \lambda \geq  0$
Studiamo i casi $\lambda >0$  e $\lambda = 0$
1. $\lambda  > 0$
Dividiamo tutte le disequazione per $\lambda$ e poniamo $\hat{y} = \frac{y}{\lambda}$
$\begin{cases} A^T\hat{y} \geq c \\ b^T \hat{y}<w^* \\ \hat{y} \geq 0 \end{cases}$
Ciò implica che esista una soluzione ammissibile per il duale, il cui valore è minore del valore minimo il che genera una contraddizione
2. $\lambda = 0$
Otteniamo $A^Ty \geq 0, b^Ty^*  = w^*, y^* \geq 0$
Ponendo $\hat{y} = y^*+y$ e osservando che $y^*$ soddisfa le condizioni, si ottiene
$A^T\hat{y} \geq c, b^T\hat{y} < w^*, \hat{y} \geq 0$
Anche in questo caso si ha una contraddizione perche $\hat{y}$ è una soluzione ammissibile per il duale e il suo valore è minore del valore minimo

Questa dimostrazione per assurdo consente di affermare che
$\exists x \in R^n : Ax^* \leq b, x^* \geq 0, c^Tx^* \geq w^*$
Per il teorema della dualità in forma debole, non è possibile che $c^Tx^* >w^*$, quindi
$$z^*=c^Tx^*=b^Ty^*=w^*$$
