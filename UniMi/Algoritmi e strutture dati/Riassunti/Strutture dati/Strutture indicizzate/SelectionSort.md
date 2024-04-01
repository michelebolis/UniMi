Scegliamo l'elemento più piccolo della sequenza ancora da esaminare e lo sposto in prima posizione
Array $A[0…N-1]$

Al passo $k$ con $k=0…N-2$:
Ho una parte ordinata $A[0] \leq A[1] \leq … \leq A[k-1]$
Ho una parte non ordinata $A[k]-A[j]$

```
ALGORITMO selectionSort (array A[0…N-1])
FOR k <- 0 TO N-2 DO
	//ricerca la posizione del minimo in A[k…N-1]
	m <- k
	FOR j <- k+1 TO N-1 DO
		IF A[j] < A[m] THEN
			m=j
	Scambia A[m] con A[k]
```

Numero Confronti: ciclo più interno ripete l'IF ($n-k-1$) --> $k$ varia
Numero Totale Confronti: 
$$\sum_{k=0}^{n-2}{n-k-1} = \sum_{i=1}^{n-1} {i} = \frac{n*(n-1)}{2} = \Theta(n^2)$$

Spazio: 3 variabili ($k,m,j$) quindi è costante --> $Ο(1)$
L'algoritmo non è stabile

OSS L'algoritmo è incrementale
OSS la parte gia ordinata, sarà definitiva non piu modificata in futuro