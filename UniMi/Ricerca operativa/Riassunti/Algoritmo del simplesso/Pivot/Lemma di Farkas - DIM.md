Parte 1: SE la prima è vera, la seconda è falsa
E' vera $\exists x \in R^n:Ax=b, x\geq 0$
ALLORA
$\exists \bar{x} \in R^n:A\bar{x}=b, \bar{x}\geq 0$
$A^Ty \geq 0 \implies \bar{x}^TA^Ty\geq 0$ (moltiplicando per la trasposta di $\bar{x}$ non dovrebbe cambiare segno)
$\bar{x}^TA^T=b^T \implies b^Ty \geq 0$ (MA sapendo che y è negativo, o è vera la riga sopra o questa)
QUINDI la seconda è falsa

Parte 2: SE la prima è falsa, la seconda è vera
Definiamo il cono l'insieme dei vettori $q$ in $m$ dimensioni t.c. SE li sostituissi a $b$, darebbero una soluzione
$C = \{q \in R^m: \exists x(q) \in R^n : x(q) \geq 0, Ax(q)=q\}$
C è convesso
Dato che la prima parte è falsa, $b \notin C$
Secondo il teorema dell'iperpiano separatore (esiste un iperpiano che separa il vettore e il cono)
$$\exists y  \in R^m \backslash \{0\} : q^Ty \geq 0, \forall q \in C, b^Ty < 0$$
Poiché $q=Ax(q)$,  $\forall q \in C$, per sostituzione (con $x(q)$ il vettore che quando $b=q$ risolve il sistema)
$$q^Ty \geq 0, \forall q \in C \implies x(q)^TA^Ty \geq 0, \forall q \in C$$
Poiché $x(q) \geq 0$, $\forall q \in C$
$x(q)^TA^Ty \geq 0, \forall q \in C \implies A^Ty \geq 0$
QUINDI la seconda parte è vera