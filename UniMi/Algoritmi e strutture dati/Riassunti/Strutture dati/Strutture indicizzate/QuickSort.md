Caso semplice $<=1$ elemento: soluzione immediata
Altrimenti: divido l'array in 2 part, le ordino in modo ricorsivo, combina le due soluzioni

Scelgo un numero: perno o pivot
Divido l'array in 2 array: il primo con tutti gli elementi $\leq pivot$ e l'altro $>pivot$

```
ALGORITMO quickSort(array A)
IF lunghezza di A > 1 THEN
	Partizionamento:
		Scegli un elemento x di A
		B <- {y appartenente ad A | y <= x}
		C <- {y appartenente ad A | y > x}
	quickSort(B)
	quickSort(C)
	A <- concatenazione di B e di C
//else non fare nulla
```

Voglio un algoritmo in loco e che non impieghi troppo per il partizionamento

ALGORITMO partiziona(array A, indice i, indice f) -> indice
Partiziona $A[i…f-1]$ rispetto a un elemento di $A[i…f-1]$ scelto come perno spostando gli elementi in modo che alla fine abbia gli stessi elementi ma gli elementi $\leq$ al perno devono stare nella parte a sinistra del perno mentre nella parte a destra quelli $>$ del perno.
Restituisce la posizione finale del perno (pos)
- Scansione da dx fino a trovare il primo elemento $\leq$ del perno, a quel punto inizio scansione da sx finche non trovo un elemento > del perno.
- Scambio i due elementi
- Riparto
- Mi fermo quando gli indici sono uguali
- Scambio perno con elemento a indice dx

```
ALGORITMO partizione(Array A, indice i, indice f) -> indice
perno <- A[i]
sx <- i
dx <- f
WHILE sx < dx DO
	DO dx <- dx-1 WHILE A[dx]>perno
	DO sx <- sx+1 WHILE sx <dx AND A[sx]<=perno
	IF sx<dx THEN
		Scambia A[sx] con A[dx]
scambia A[i] con A[dx]
return dx
```
OSS $A[i] - A[sx-1] \leq perno$ e $A[dx+1] - A[f-1] > perno$

es
![[Pasted image 20240329111310.png]]

[[QuickSort - Analisi Temporale]]
[[QuickSort - Analisi Spaziale]]
Algoritmo non è stabile