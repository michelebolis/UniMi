Fasi
- Uso array $Y$ di dimensione $b$. Ogni cella di $Y$ conterrà un puntatore ad una coda ognuna delle quali conterrà tutti gli elementi di $A$ con chiave $i$
- Scandisco $Y$ e per ogni $i$ dovrò scandire la coda associata e riportare gli elementi in $A$
Osservo che l algoritmo è stabile

```
ALGORITMO bucketSort(Array A[0…b-1], intero b)
Sia Y[0…b-1] un array
FOR i <- 0 TO b-1 DO //predispongo bucket
	Y[i] <- coda vuota
FOR i <- 0 TO n-1 DO //riempimento bucket
	X <- A[i].chiave
	Y[x].equeue(A[i])
J <- 0
FOR i <- 0 TO b-1 DO //modifico A
	WHILE !Y[i].isEmpty() DO
		A[j] <- Y[i].dequeue()
		J <- j+1
```

Numero passi: $\Theta(b) + \Theta(n) + \Theta(b*O(n))$
In realtà non è $O(n)$ perché se ho la coda di $n$ elementi le altre code saranno vuote --> elementi si distribuiscono sulle code
In totale ho $n$ elementi, quindi in totale faccio $n$ passi nel while --> in realtà faccio $\Theta(n+b)$
Numero passi = $\Theta(b) + \Theta(n) + \Theta(n+b) = \Theta(n+b)$
SE $b=O(n)$ -> tempo $\Theta(n)$
SE $b=\Theta(n^2)$ --> tempo $\Theta(n^2)$ --> mi conviene usare heap sort

Algoritmo NON è in loco
Algoritmo è stabile
Vale per riordinare anche le liste manipolando direttamente le liste

Problema: ordina elenco rispetto al compleanno
Prima ordino il giorno e poi il mese con il bucket sort
Nel primo ordinamento uso 31 bucket
Poi uso 12 bucket
Avendo stabilita una volta che ho ordinato per il giorno, quando ordino per il mese mi rimane l ordine dei giorni

es
![[Pasted image 20240329135018.png]]