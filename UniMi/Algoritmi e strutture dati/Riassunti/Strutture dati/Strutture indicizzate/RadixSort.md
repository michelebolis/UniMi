Problema: ordinare un insieme di dati con chiavi intere
Lavoriamo sulle cifre, usando ogni volta 10 bucket
Inizio ad ordinare dalla cifra meno significativa fino ad arrivare a quella piu significativa
Stabilita mi garantisce di ottenere la soluzione corretta alla fine
Quando un numero non ha una cifra in realta c e scritto 0 (da pensare in binario)

```
ALGORITMO radixSort(array A[0…N-1])
t <- 0
WHILE ( esiste chiave k in A t.c. [k/bt]!=0) DO
	bucketSort(A, b, t)
	t <- t+1
```

SE devo ordinare n chiavi tra 0 e 999 999 999
Con $B=10^3$ bastano 3 passate di bucketSort
Usando B potenza di 2 le divisioni sono piu veloci (in generale divisione piu onerosa)

SE devo ordinare n chiavi su 32 bit cioè tra 0 e $2^{32} -1$
Con $B=2^8$ faccio 4 passate di bucketSort
Con $B=2^{16}$ faccio 2 passate

Tempo $\Theta(n)$

Come estrarre la cifra in posizione $t$ di $x$ in base $b$
$(\frac{x}{b^t})$ MOD $b$ //divisione intera
Dividere per potenze della base vuol dire fare uno shift

Non posso usarlo nei numeri con virgola mobile, problemi di approssimazione, di individuare mantissa, esponente…

![[Pasted image 20240329135638.png]]