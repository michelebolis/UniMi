```
ALGORITMI merge(array A, indice i, indice m, indice f, array X)
i1 <- i
i2 <- m
K <- 0
WHILE i1<m AND i2<f DO
	IF A[i1] <= A[i2] THEN
		X[k] <- A[i1]
		i1 <- i1+1
	ELSE
		X[k] <- A[i2]
		i2 <- i2+1
	K <- k+1
IF i1<m THEN
	FOR j <- i1 TO m-1 DO
		X[k] <- A[j]
		K <- k+1
ELSE 
	FOR j <- i2 TO f-1 DO
		X[k] <- A[j]
		K <- k+1
FOR k <-0 TO f-i-1 DO
	A[i+k] <- X[k]
```

Si può evitare $X$ per il merge? Non banale
Non lo creo dentro il merge, ma prima in modo che sia unico evitando di usare ogni volta memoria ulteriore