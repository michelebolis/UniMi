Uso delle variabili costante ma essendo ricorsivo dobbiamo considerare l'altezza dello stack che raggiunge
Considerando che lo spazio si ricicla, dipenderà da come viene suddiviso l'array

Caso: array gia ordinato
Array con 1 elemento (pivot) e una chiamata da 1 a $n-1$
Quindi avremo altezza $n$, proporzionale al numero di elementi

Caso: array quasi ordinato
Avremo ancora altezza n

OSS posso anche riordinare prima la parte di dx e poi quella di sx
```
PROCEDURA quickSort(array A, indice i, indice f)
IF f-i >1 THEN
	m <- partizione(A, i, f)
	quickSort(A, m+1, f)
	quickSort(A, i, m)
```

Ricorsione in coda/terminale è la seconda chiamata ricorsiva
Invece che fare la seconda chiamata faccio la chiamata come iterazione
```
PROCEDURA quickSort(array A, indice i, indice f)
WHILE f-i > 1 DO
	m <- partizione(A, i, f)
	quickSort(A, i, m)
	i <- m+1
```

//se voglio partire a ordinare la parte destra
```
PROCEDURA quickSort(array A, indice i, indice f)
WHILE f-i > 1 DO
	m <- partizione(A, i, f)
	quickSort(A, m+1, f)
	f <- m
```

Creo procedura che decide se fare prima la chiamata di dx o sx, in particolare sceglie quella con dimensione minore
```
PROCEDURA quickSort(array A, indice i, indice f)
WHILE f-i > 1 DO
	m <- partizione(A, i, f)
	IF m-i < f-m THEN
		quickSort(A, i, m)
		i <- m+1
	ELSE
		quickSort(A, m+1, f)
		f <- m
```

Supponendo di avere un record di n, la parte piu lunga e minima sarà n/2
Quindi altezza dello stack sarà lg n

- Versione migliorata: $\Theta(\log n)$
	- altezza pila = $\Theta(\log n)$ 
	- dimensione record di attivazione = $\Theta(1)$ 
- Versione base: $\Theta(n)$
	- altezza pila = $\Theta(n)$
	- dimensione record di attivazione = $\Theta(1)$ 

OSS caso peggiore per i confronti è anche il peggiore per lo spazio