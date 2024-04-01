```
ALGORITMO bubbleSort(Array A[0…N-1]) //versione 1
DO
	Scambiato <- false
	FOR j <-1 TO n-1 DO
		IF A[j]<A[j-1] THEN
			Scambia(A[j],A[j-1])
			Scambiato <- true
WHILE scambiato

ALGORITMO bubbleSort(Array A[0…N-1]) //versione 2
i <- 1
DO
	Scambiato <- false	
	FOR j <-1 TO n-1 DO
		IF A[j]<A[j-1] THEN
			Scambia(A[j],A[j-1])
			Scambiato <- true
	i <- i+1
WHILE scambiato AND i<n
```

Numero Confronti: all'iterazione $i$, $n-i$ confronti
Numero Totale confronti: 
$$\sum_{i=1}^{n-1}{n-i} = \sum_{k=1}^{n-1}{k} = \frac{n*(n-1)}{2}=O(n^2)$$
Caso migliore: $n-1$

L'algoritmo è stabile