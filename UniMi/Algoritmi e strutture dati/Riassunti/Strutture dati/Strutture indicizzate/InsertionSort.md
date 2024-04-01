Se ho una parte ordinata, ma poi una sequenza di numeri non ordinati rispetto a quelli precedenti
Cerchiamo il posto dove inserire il numero partendo da destra, dalla fine della sequenza ordinata

```
ALGORITMO insertionSort(array A[0…N-1])
FOR k <-1 TO N-1 DO
	x <- A[k] //elemento da sistemare
	j <- k-1
	WHILE j>=0 AND A[j]>x DO
		A[j+1] <- A[j] //sposto il precedente di x nella posizione di x
		j <-j-1
	A[j+1] <- x //nella posizione di j metto il valore di x
```

Numero Confronti: all'iterazione $k$, devo confrontare $x$ con $k$ valori alla peggio --> $\leq k$
Numero Totale Confronti:  
$$\sum_{k=1}^{n-1}{k} = \frac{n*(n-1)}{2}=O(n^2)$$
SE array ordinato: $n-1$ confronti: $Ο(n)$
Caso peggiore: array decrescente
Spazio: $Ο(1)$
L'algoritmo è stabile