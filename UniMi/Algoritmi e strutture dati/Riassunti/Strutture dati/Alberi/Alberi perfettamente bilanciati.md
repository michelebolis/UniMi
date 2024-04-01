DEF un albero binario è detto perfettamente bilanciato quando per ogni nodo la differenza in valore assoluto tra i numeri di nodi presenti nei suoi sottoalberi sinistro e destro è al massimo 1

$n \geq 2^h$
DIM per induzione
Per $h=0$, $n=1=2^0$ VERO
Per $h>0$, supponiamo albero perfettamente bilanciato di altezza $h$

Almeno uno dei due alberi $T'$ o $T''$ ha altezza $h-1$. 
Quindi usando ipotesi induttiva allora quell albero ha almeno $2^{h-1}$ nodi. Cio implica che l'altro sottoalbero ha almeno $2^{h-1} -1$ nodi
Numero TOT nodi $\geq 1 + 2^{h-1} + 2^{h-1} -1 = 2^h$ VERO

Al massimo ho l albero completo, quindi $2^{h+1} -1$ quindi $h=\lfloor\log n\rfloor -1$ //parte intera inferiore
QUINDI altezza sempre logaritmica nel numero dei nodi

L'inserimento costa $\Theta(n)$
Quindi struttura va bene solo per ricerca in quanto gli aggiornamenti sono meno costosi

es
![[Pasted image 20240329144117.png|300]]
![[Pasted image 20240329144120.png|300]]