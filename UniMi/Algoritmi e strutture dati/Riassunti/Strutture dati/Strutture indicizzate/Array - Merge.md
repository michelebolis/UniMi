Ho due array, $B$ e $C$, gia ordinati, voglio crearne uno nuovo $X$ con gli elementi di $B$ e $C$ ordinati
- Prima ipotesi: uso gli algoritmi di prima mettendo prima insieme i due array a caso
- Seconda ipotesi:
So che il primo elemento, il piu piccolo, sarà nella prima posizione nel primo o nel secondo array
Cosi faro $n$ confronti
In realtà uno dei due array finirà prima quindi

Numero Confronti: $\leq n$

```
ALGORITMI merge(array B[0…lB-1], array C[0…lC-1]) --> array
Sia X[0…lB+lC-1] un array
i1 <- 0 //indice su B
i2 <- 0 //indice su C
K <- 0
WHILE i1<lB AND i2<lC DO
	IF B[i1] <= C[i2] THEN
		X[k] <- B[i1]
		i1 <- i1+1
	ELSE
		X[k] <- C[i2]
		i2 <- i2+1
	K <- k+1

IF i1<lB THEN //in B è rimasto qualcosa
	FOR j <- i1 TO lB-1 DO
	X[k] <- B[j]
	K <- k+1
ELSE //in C è rimasto qualcosa
	FOR j <- i2 TO lC-1 DO
	X[k] <- C[j]
	K <- k+1
RETURN X
```

$n= l_B + l_C$

Numero Confronti: al massimo $n$ confronti poi finisce un array --> $\leq n-1$ // $-1$ perche 1 elemento sicuramente dall array che non è finito lo devo prendere

Tempo: $\Theta(n)$ SE costo uniforme seno $\Theta(n*t)$
Spazio:
