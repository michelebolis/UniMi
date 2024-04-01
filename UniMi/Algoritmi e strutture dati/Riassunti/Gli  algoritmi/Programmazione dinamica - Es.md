Trovare dato un vettore $V$ in $Z$ un $Sottovettore=V[inizio:fine]$ di somma massima
Ricerca esaustiva: ispezioniamo tutti i possibili sottovettori
- $1<=inizio<=n$
- $inizio<=fine<=n$

Sono circa $\frac{n^2}{2}$ sottovettori
Facciamo $O(\frac{n^2}{2})$ iterazioni
Pero c è anche la somma di V che fa fine - inizio passi
Quindi tempo $O(n^3)$

```
ALGORITMO sottovettoreMax(Array V[1…n]) -> (intero, intero)
Max <- v[1], inizio <- 1, fine <- 1
FOR i <- 1 TO n DO
	Somma <- 0
	FOR f <- i TO n DO
		Somma <- somma + V[f]
		IF somma > max THEN
			Max <- somma
			Inizio <- i
			Fine <- f
RETURN (inizio, fine)
```

$Tempo = O(n^2)$

P(i): trovare il sottovettore di somma max che termina in posizione i
Soluzione di P: scelta le soluzioni di P(1), …, P(n)

```
ALGORITMO settovettoreMax(Array V[1…n]) -> (intero, intero)
Sia S[1..n] un vettore
S[1] <- V[1]
Max <- S[1], fine <- 1
FOR i <- 2 TO n DO
	IF S[i-1] >=0 THEN
		S[i] <- S[i-1] + V[i]
	ELSE
		S[i] <- V[i]
	IF S[i] >max THEN
		Max <- S[i]
		Fine <- i
Inizio <- fine
WHILE S[inizio]!=V[inizio]
	Inizio <- inizio -1
RETURN (inizio, fine)
```

$Tempo = O(n)$

