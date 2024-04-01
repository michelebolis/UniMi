Input: array $A$, elemento $x$
Output: indice $i$ t.c. $A[i]=x$ oppure $-1$ se $A$ non contiene $x$
//non ho specificato se il numero appare più volte

- Ricerca sequenziale
```pseudocode
ALGORITMO ricercaSequenziale(array A[0…N-1], elemento x) -> indice
I <- 0
WHILE  i<N AND A[i]!=x DO
	I <- i+1
IF i=N THEN
	RETURN -1
ELSE RETURN i
```

Lazy evaluation: SE il primo è falso in un AND non valuto il secondo
Al massimo fa $Ο(n)$ interazioni 
$T = \Theta(n)$ SE confronti $A[i]\neq x$ è di tempo costante (come gli interi)
Il parametro importante sono il numero di interazioni, per il resto semplifichiamo con tempo costante
Lo spazio oltre ai dati è solo la variabile i quindi $Ο(1)$
Facendolo da $i=N-1..0$ tolgo l'IF finale facendo solo return $i$

- Ricerca binaria/dicotomica (versione 1 ricorsiva)
Supponiamo che il nostro array sia ordinato
Confronto $x$ con $A[m]$ con $m$ indice centrale riuscendo a scartare ad ogni iterazione metà degli elementi
```pseudocode
FUNZIONE ricercaRic(array A, indice sx, indice dx, elemento x) -> indice
IF dx <=sx THEN RETURN -1
ELSE
	m <- (sx+dx)/2 //divisione intera
	IF x==A[m] THEN RETURN m
	ELSE IF x < A[m] THEN
			RETURN ricercaRic(A, sx, m, x)
		ELSE
			RETURN ricercaRic(A, m+1, dx, x)
	
ALGORITMO ricercaBinaria(Array A[0…N-1], elemento x) -> indice	
RETURN ricercaRic(A, 0, N, x)
```

OSS indice $dx$ è escluso dal controllo infatti nell'algoritmo passo $N$
Prima chiamata: dimensione $n$
Seconda chiamata: dimensione $\frac{n}{2}$
$i$-esima chiamata: dimensione $\frac{n}{2^{i-1}}$
$\frac{n}{2^{i-1}}=?1$
$i=1+lg_2 n$
Con un ulteriore chiamata ho 0 elementi quindi al più $2+lg_2 n$ chiamate

Ipotesi costo confronti $Ο(1)$
Le istruzioni esclusi i confronti hanno costo $Ο(1)$ perché non abbiamo cicli
$Tempo = \Theta(\log{n)}$ //dovrei fare $numero chiamate*costochiamate = \log_2 n * costante$
Spazio: al massimo potrò avere $\log n$ record di attivazione sullo stack --> $\Theta(\log n)$
Come prima spazio di un record è $Ο(1)$

Ricorsione terminale o ricorsione in coda: l'ultima ricorsione che poi farà terminare a cascata il programma
Per migliorare le prestazioni posso trasformare la ricorsione in un modo iterato

- Ricerca binaria (versione 2 iterata)
```
ALGORITMO ricercaBinaria(Array A[0…N-1], elemento x) -> indice
Sx <-0
Dx <- N
Pos <- -1
WHILE sx < dx AND pos==-1 DO
	m <- (sx+dx)/2 //divisione intera
	IF x==A[m] THEN pos <- m
	ELSE IF x < A[m] THEN
			Dx <- m
		ELSE
			Sx <- m+1
RETURN pos
```

Lo spazio è $Ο(1)$
Il tempo è $\Theta(\log n)$

