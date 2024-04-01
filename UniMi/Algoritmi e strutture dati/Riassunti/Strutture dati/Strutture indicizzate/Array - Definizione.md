Un array è una collezione di elementi dello stesso tipo ciascuno dei quali è accessibile in base alla posizione
Caratteristiche tipiche:
- Memorizzato in una porzione contigua di memoria
- Accesso tramite indice $[0:N-1]$
- Tempo di accesso è indipendente dalla posizione del dato

Limitazione: è una struttura statica, senza la possibilità di aggiungere nuove posizioni

Le variabili array sono riferimenti, puntatori, all'array
$B <- A$ in realtà sto passando il puntatore
$B[1] <- 0$
$Stampa(A[1])$ //stamperà 0

```
PROCEDURA azzera(array x [0…N-1])
	FOR i <- 0 TO N-1 DO
		x[i] <- 0
```

![[Pasted image 20240329100222.png]]

[[Ricerca in un Array]]
[[Array - Sort]]
